<h3>Code Book</h3>
<div style="border: 5px dotted gray; padding: 10px 20px; background-color:#ededed; box-shadow: 0 1px 5px rgba(0, 0, 0, 0.25);">
<p>The <code>run_analysis.R</code> script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.</p>
<ol style="list-style-type: decimal">
<li><strong>Download the dataset</strong>
<ul>
<li>Dataset downloaded and extracted under the folder called <code>UCI HAR Dataset</code></li>
</ul>
<br /></li>
<li><strong>Assign each data to variables</strong>
<ul>
<li><code>features</code> &lt;- <code>features.txt</code> : 561 rows, 2 columns <br /> <em>The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.</em></li>
<li><code>activities</code> &lt;- <code>activity_labels.txt</code> : 6 rows, 2 columns <br /> <em>List of activities performed when the corresponding measurements were taken and its codes (labels)</em></li>
<li><code>subject_test</code> &lt;- <code>test/subject_test.txt</code> : 2947 rows, 1 column <br /> <em>contains test data of 9/30 volunteer test subjects being observed</em></li>
<li><code>x_test</code> &lt;- <code>test/X_test.txt</code> : 2947 rows, 561 columns <br /> <em>contains recorded features test data</em></li>
<li><code>y_test</code> &lt;- <code>test/y_test.txt</code> : 2947 rows, 1 columns <br /> <em>contains test data of activities’code labels</em></li>
<li><code>subject_train</code> &lt;- <code>test/subject_train.txt</code> : 7352 rows, 1 column <br /> <em>contains train data of 21/30 volunteer subjects being observed</em></li>
<li><code>x_train</code> &lt;- <code>test/X_train.txt</code> : 7352 rows, 561 columns <br /> <em>contains recorded features train data</em></li>
<li><code>y_train</code> &lt;- <code>test/y_train.txt</code> : 7352 rows, 1 columns <br /> <em>contains train data of activities’code labels</em></li>
</ul>
<br /></li>
<li><strong>Merges the training and the test sets to create one data set</strong>
<ul>
<li><code>X</code> (10299 rows, 561 columns) is created by merging <code>x_train</code> and <code>x_test</code> using <strong>rbind()</strong> function</li>
<li><code>Y</code> (10299 rows, 1 column) is created by merging <code>y_train</code> and <code>y_test</code> using <strong>rbind()</strong> function</li>
<li><code>Subject</code> (10299 rows, 1 column) is created by merging <code>subject_train</code> and <code>subject_test</code> using <strong>rbind()</strong> function</li>
<li><code>Merged_Data</code> (10299 rows, 563 column) is created by merging <code>Subject</code>, <code>Y</code> and <code>X</code> using <strong>cbind()</strong> function</li>
</ul>
<br /></li>
<li><strong>Extracts only the measurements on the mean and standard deviation for each measurement</strong>
<ul>
<li><code>TidyData</code> (10299 rows, 88 columns) is created by subsetting <code>Merged_Data</code>, selecting only columns: <code>subject</code>, <code>code</code> and the measurements on the <code>mean</code> and <em>standard deviation</em> (<code>std</code>) for each measurement</li>
</ul>
<br /></li>
<li><strong>Uses descriptive activity names to name the activities in the data set</strong>
<ul>
<li>Entire numbers in <code>code</code> column of the <code>TidyData</code> replaced with corresponding activity taken from second column of the <code>activities</code> variable</li>
</ul>
<br /></li>
<li><strong>Appropriately labels the data set with descriptive variable names</strong>
<ul>
<li><code>code</code> column in <code>TidyData</code> renamed into <code>activities</code></li>
<li>All <code>Acc</code> in column’s name replaced by <code>Accelerometer</code></li>
<li>All <code>Gyro</code> in column’s name replaced by <code>Gyroscope</code></li>
<li>All <code>BodyBody</code> in column’s name replaced by <code>Body</code></li>
<li>All <code>Mag</code> in column’s name replaced by <code>Magnitude</code></li>
<li>All start with character <code>f</code> in column’s name replaced by <code>Frequency</code></li>
<li>All start with character <code>t</code> in column’s name replaced by <code>Time</code></li>
</ul>
<br /></li>
<li><strong>From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject</strong>
<ul>
<li><code>FinalData</code> (180 rows, 88 columns) is created by sumarizing <code>TidyData</code> taking the means of each variable for each activity and each subject, after groupped by subject and activity.</li>
<li>Export <code>FinalData</code> into <code>FinalData.txt</code> file.</li>
</ul></li>
</ol>
</div>
