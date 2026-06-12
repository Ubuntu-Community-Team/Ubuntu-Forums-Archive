---
title: "CaBig Medical"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by anderskitson on 2008-05-08
I am attempting to install a program called caBig, for a biobank, anyways I am in the middle of installing some of the dependicies it needs, one being mysql, which is installed, one of the instructions it gives me in the installation pdf is this

> Enter grant all privileges on {schema_name}.* to
&#8216;{db_user}@&#8217;{web_server_name}&#8217; identified by &#8216;{db_password}&#8217;
with grant option;
Notes:
&#8226;   schema_name, db_user, web_server_name and
    db_password are defined in the deploy.properties file.
&#8226;   The semi-colon is an important part of the command--it prompts its execution.


I am lost as to what to replace the fields with, any help, or where I could get help would be great. I am assuming I am supposed to enter this into the mysql cli, It wants me to gather this information from a file called deploy.proterties, I know where it is, but the information i need to gather from it doesn't make sense, I think I need to point mysql to it, but how?
Heres the contents of that file

##################################################################################

#  PROJECT PROPERTIES

#

#  Value of the PROJECT_NAME property is used to create/name: 

#		1) Output project directory folder name

#		2) Beans JAR file name

#		3) ORM JAR file name

#  		4) Client JAR file name

#		5) WAR file name

#		6) Web Service Namespace

#		7) Documentation title in the generated API (Javadocs)

#

#  Value of the NAMESPACE_PREFIX is used to create:

#		1) XSD's (Schema's) 

#		2) XML Mapping and Unmapping files.

#

#  NOTE:  If XSDs are to be used for the caGRID, the value of the NAMESPACE_PREFIX 

#  should be the same as the GME namespace

#

#  Value of the CSM_PROJECT_NAME property is used as a prefix when creating:

#		1) The CSM security configuration file name

#

#  Value of the INSTANCE_LEVEL_SECURITY is used to enable/disable CSM instance

#  level security.  Only relevant if SECURITY_ENABLED property is set to 'true'.

#

#  Value of the ATTRIBUTE_LEVEL_SECURITY is used to enable/disable CSM attribute

#  level security.  Only relevant if SECURITY_ENABLED property is set to 'true'.

#

##################################################################################

PROJECT_NAME=example

NAMESPACE_PREFIX=gme://caCORE.caCORE/3.2/



SECURITY_ENABLED=false

CSM_PROJECT_NAME=sdk

INSTANCE_LEVEL_SECURITY=false

ATTRIBUTE_LEVEL_SECURITY=false



WEBSERVICE_NAME=${lab471}Service



################################################################################## 

#  APPLICATION SERVER PROPERTIES

#

#  SERVER_TYPE if set to jboss will exclude log4j.jar from the war file 

#              any other value will include the log4j.jar in the war file

##################################################################################

SERVER_TYPE=other

SERVER_URL=http://localhost:8080/${PROJECT_NAME}



################################################################################## 

#  MODEL PROPERTIES

#

#  XMI_FILE specifies the name of the file which contains the object/data model. 

#  The file is to be placed under models directory.

##################################################################################

#MODEL_FILE=sdk.uml

#MODEL_FILE_TYPE=ARGO

MODEL_FILE=sdk.xmi

MODEL_FILE_TYPE=EA



LOGICAL_MODEL=Logical View.Logical Model

DATA_MODEL=Logical View.Data Model

INCLUDE_PACKAGE=domain

EXCLUDE_PACKAGE=

EXCLUDE_NAME=



##################################################################################

#  DATABASE CONNECTION PROPERTIES

# 

#  If USE_JNDI_BASED_CONNECTION=yes then DB_JNDI_URL is used to obtain the 

#  connection and get data. 

#  If USE_JNDI_BASED_CONNECTION=no then DB_DRIVER, DB_CONNECTION_URL, DB_USERNAME

#  and DB_PASSWORD is used to initialize the collection and get data.

#

#  DB_DIALECT is used by the Hibernate to prepare the database specific queries

#

#  CACHE_PATH is being used by the EHCache to store its cache files on disk

##################################################################################

USE_JNDI_BASED_CONNECTION=no

DB_JNDI_URL=java:/SDK



DB_CONNECTION_URL=

DB_USERNAME=lab471

DB_PASSWORD=471msb

DB_DRIVER=oracle.jdbc.driver.OracleDriver



DB_DIALECT=org.hibernate.dialect.OracleDialect



##################################################################################

#  SECURITY DATABASE CONNECTION PROPERTIES

#

#  If CSM_USE_JNDI_BASED_CONNECTION=yes then CSM_DB_JNDI_URL is used to obtain the 

#  connection and get data. 

#  If CSM_USE_JNDI_BASED_CONNECTION=no then CSM_DB_DRIVER, CSM_DB_CONNECTION_URL, 

#  CSM_DB_USERNAME and CSM_DB_PASSWORD is used to initialize the collection and 

#  get data.

#

#  CSM_DB_DIALECT is used by the Hibernate to prepare the database specific queries

#  If you are using instance level security then the CSM tables are required to be 

#  present in the same schema as the domain object resides

##################################################################################

CSM_USE_JNDI_BASED_CONNECTION=no

CSM_DB_JNDI_URL=java:/SDK



CSM_DB_CONNECTION_URL=

CSM_DB_USERNAME=

CSM_DB_PASSWORD=

CSM_DB_DRIVER=oracle.jdbc.driver.OracleDriver



CSM_DB_DIALECT=org.hibernate.dialect.OracleDialect



##################################################################################

##################################################################################

#  CODE GENERATION OPTIONS

##################################################################################

##################################################################################

#  The following properties are used to enable or disable code generation step(s). 

#  These properties accept values of either 'true' or 'false'. Setting the value 

#  to 'false' for a component disables the code generation of that component, while

#  setting the value to 'true' enables it

#

#  VALIDATE_LOGICAL_MODEL 	if enabled checks for the validity of the object model

#  VALIDATE_MODEL_MAPPING 	if enabled checks for the validity of the object to 

#                         	database mapping 

#  GENERATE_HIBERNATE_MAPPING if enabled generates Hibernate related artifacts

#  GENERATE_BEANS 			if enabled, generates Java beans from the object model

#  GENERATE_CASTOR_MAPPING 	if enabled, generates castor mapping files for the 

#                          	object model

#  GENERATE_XSD 			if enabled, generates the XSD

#  GENERATE_WSDD 			if enabled, generates the Web Services Deployment  

                 			Descriptor (WSDD) file

##################################################################################

VALIDATE_LOGICAL_MODEL=true

VALIDATE_MODEL_MAPPING=true

GENERATE_HIBERNATE_MAPPING=true

GENERATE_BEANS=true

GENERATE_CASTOR_MAPPING=true

GENERATE_XSD=true

GENERATE_WSDD=true



INCLUDE_SEARCH_EVENT_LISTENER=false

##################################################################################

#  ADVANCED PROPERTIES

#

#  CACHE_PATH is being used by the EHCache to store its cache files on disk

#  java.io.tmpdir will create the cache files in the temporary directory. 

#  User can choose to specify any absolute path for the cache files

##################################################################################

CACHE_PATH=java.io.tmpdir

---

### Post by tofuconfetti on 2008-05-08
What this means ...

```
Enter grant all privileges on {schema_name}.* to
&#8216;{db_user}@&#8217;{web_server_name}&#8217; identified by &#8216;{db_password}&#8217;
with grant option;
Notes:
&#8226; schema_name, db_user, web_server_name and
db_password are defined in the deploy.properties file.
&#8226; The semi-colon is an important part of the command--it prompts its execution.
```

... is the classic command line assignment of a user and privileges for a mysql user on a mysql database.  The ";" ends every command in commandline mysql.  So all it's telling you to do is to make a user and give him/her specific privileges for a specific database.  All you have to do is find out which actual database names and users you want to enter.

Looking at the file you posted, it seems to me that what you have is a setup for an oracle database.  These variables are defined:

```
USE_JNDI_BASED_CONNECTION=no

DB_JNDI_URL=java:/SDK

DB_CONNECTION_URL=

DB_USERNAME=lab471

DB_PASSWORD=471msb

DB_DRIVER=oracle.jdbc.driver.OracleDriver

DB_DIALECT=org.hibernate.dialect.OracleDialect
```

So you probably have to find out how to put in as the DB_DRIVER="something.or.other.to.tell.you.to use.a.mysql.driver".  You'll have to probably dig into your documentation to find out what specifies that you are using a mysql database rather than an oracle database.

Now, once you have that specified, just define the variables like you wish in that file.  Literally add them yourself such as:

```
SCHEMA-NAME=labdatabase
DB_USER=yourname
DB_PASSWORD=yourpassword
WEB_SERVER_NAME=myserver.mydomainname.net
```

Once you have them defined, log into your mysql database with the root user name, which is set up at the time of install, from the commandline like this:

```
mysql -uroot -p
```

then give it your password.  You may have to first create the database you are assigning the privileges to:

```
create database labdatabase;
```

From the mysql prompt issue the recommended command substituting the ACTUAL values you put in the config file.

```
grant all privileges on labdatabase.* to yourname@myserver.mydomain.net identified by 'yourpassword' with grant option;
```

That creates all privileges on every table in the labdatabase to 'yourname' at the 'myserver.mydomain.net' host using the password 'yourpassword' and allows that user to grant privileges to other users.

---

### Post by anderskitson on 2008-05-09
>       Drivers for MySQL, Oracle 9i and DB2 are included with the SDK. If you are
      using a different version of Oracle or DB2, you must obtain the appropriate
      drivers. JDBC drivers can be downloaded from the Sun Developer Network
NOTE:
      at [http://developers.sun.com/product/jdbc/drivers/index.html](http://developers.sun.com/product/jdbc/drivers/index.html), or from the
      individual vendors&#8217; sites (for example, the Oracle 8i driver
      classes12.zip can be downloaded from [http://www.oracle.com/technol-](http://www.oracle.com/technol-)
      ogy/software/tech/java/sqlj_jdbc/index.html). These drivers should be placed
      in the {project_home}/lib directory and the appropriate directory in
      your J2SE container (e.g., Tomcat, JBoss) to enable connection to the
      appropriate database. In addition, some manual modification of the
      Hibernate configuration files may be necessary.

So I am going to use Tomcat, so i should install that before i do anything else then?

Allright I have a few more questions I am trying to test the system, and it came with some test files, Here are the instructions it gives me

>   In a Command Prompt window, enter cd {mysql_home} to go to your MySQL
  home directory.
  Note: mysql_home is defined in the deploy.properties file.
  Example: cd C:\mysql
2 Enter cd bin to go to the bin directory.
3 Enter mysql to execute the MySQL monitor.
4 Enter select * from {schema_name}.{table_name};.
  Notes:
  &#8226; schema_name is defined in the deploy.properties file.
      Example: cacore
  &#8226;   The semi-colon is an important part of the command--it prompts its execution.
5 For the initial example, enter select * from cacore.gene where gene_symbol
  like &#8216;IL%&#8217;;. There should be 9 rows displayed.

>   Enter the following URL in your browser to verify all your required system
  resources are available: http://{web_server_name}:8080/{project_name}/Happy.jsp.
  Note: project_name and web_server_name are defined in the
  deploy.properties file.
  Example: project_name = example; web_server_name = localhost
2 For the getting started example, enter: [http://localhost:8080/example/Happy.jsp](http://localhost:8080/example/Happy.jsp)

It is trying to access a local database just to see if it works, but I am not sure how to setup a local database

---

### Post by anderskitson on 2008-05-09
1

---

