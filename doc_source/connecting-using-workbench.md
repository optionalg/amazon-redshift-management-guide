# Connect to Your Cluster by Using SQL Workbench/J<a name="connecting-using-workbench"></a>

 Amazon Redshift does not provide or install any SQL client tools or libraries, so you must install any that you want to use with your clusters\. If you already have a business intelligence application or any other application that can connect to your clusters using a standard PostgreSQL JDBC or ODBC driver, then you can skip this section\. If you don't already have an application that can connect to your cluster, this section presents one option for doing so using SQL Workbench/J, a free, DBMS\-independent, cross\-platform SQL query tool\. 

## Install SQL Workbench/J<a name="set-up-sqlworkbench"></a>

 The *Amazon Redshift Getting Started* uses SQL Workbench/J\. In this section, we explain in detail how to connect to your cluster by using SQL Workbench/J\. 

**To install SQL Workbench/J**

1. Review the [SQL Workbench/J software license](http://www.sql-workbench.net/manual/license.html#license-restrictions)\.

1. Go to the [SQL Workbench/J](http://www.sql-workbench.net/) website and download the appropriate package for your operating system on your client computer or Amazon EC2 instance\.

1. Go to the [Installing and starting SQL Workbench/J](http://www.sql-workbench.net/manual/install.html) page\. Follow the instructions for installing SQL Workbench/J on your system\.
**Note**  
SQL Workbench/J requires the Java Runtime Environment \(JRE\) be installed on your system\. Ensure you are using the correct version of the JRE required by the SQL Workbench/J client\. To determine which version of the Java Runtime Environment is running on your system, do one of the following:  
Mac: In the **System Preferences**, click the Java icon\.
Windows: In the **Control Panel**, click the Java icon\.
Any system: In a command shell, type `java -version`\. You can also visit [http://www\.java\.com](http://www.java.com), click the [Do I Have Java?](http://www.java.com/en/download/installed.jsp) link, and click on the **Verify Java** button\. 
For information about installing and configuring the Java Runtime Environment, go to [http://www\.java\.com](http://www.java.com)\.

## Connect to Your Cluster over a JDBC Connection in SQL Workbench/J<a name="connect-to-workbench-via-jdbc"></a>

**Important**  
Before you perform the steps in this procedure, make sure that your client computer or Amazon EC2 instance has the recommended Amazon Redshift JDBC driver\. For links to download the latest drivers, see [Download the Amazon Redshift JDBC Driver](configure-jdbc-connection.md#download-jdbc-driver)\.

**To use a JDBC connection in SQL Workbench/J**

1. Open SQL Workbench/J\.

1. Click **File**, and then click **Connect window**\.

1. Click **Create a new connection profile**\.

1. In the **New profile** box, type a name for the profile\. For example, examplecluster\_jdbc\.

1. Click **Manage Drivers**\. The **Manage Drivers** dialog opens\. In the **Name** box, type a name for the driver\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/mgmt/images/jdbc-manage-drivers.png)

   Click the folder icon next to the **Library** box, navigate to the location of the driver, click it, and then click **Open**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/mgmt/images/redshift_jdbc_file.png)

   If the **Please select one driver** dialog box displays, select **com\.amazon\.redshift\.jdbc4\.Driver** or **com\.amazon\.redshift\.jdbc41\.Driver** and click **OK**\. SQL Workbench/J automatically completes the **Classname** box\. Leave the **Sample URL** box blank, and then click **OK**\. 

1. In the **Driver** box, select the driver you just added\.

1. In **URL**, copy the JDBC URL from the Amazon Redshift console and paste it here\.

   For more information about finding the JDBC URL, see [Configure a JDBC Connection](configure-jdbc-connection.md)\.

1. In **Username**, type the name of the master user\.

   If you are following the *Amazon Redshift Getting Started*, type *masteruser*\.

1. In **Password**, type the password associated with the master user account\.

1. Select the **Autocommit** box\. 

1. Click the **Save profile list** icon, as shown below:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/mgmt/images/sql_workbench_save.png)

1. Click **OK**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/mgmt/images/redshift_driver_sql_workbench.png)

## Test the SQL Workbench/J Connection<a name="test-workbench-connection"></a>

 After you configure your JDBC or ODBC connection, you can test the connection by running an example query\. 

1. You can use the following query to test your connection\.

   ```
   select * from information_schema.tables;
   ```

   If your connection is successful, a listing of records appears in the **Results** tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/mgmt/images/connect-cluster-query-result-50.png)

1. Alternatively, if you loaded the sample tables and data from the [Amazon Redshift Getting Started](http://docs.aws.amazon.com/redshift/latest/gsg/), you can test your connection by typing the following query into the **Statement** window:

   ```
   select * from users order by userid limit 100;
   ```

   If your connection is successful, a listing of records appears in the **Results** tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/mgmt/images/connect-cluster-query-result-55.png)