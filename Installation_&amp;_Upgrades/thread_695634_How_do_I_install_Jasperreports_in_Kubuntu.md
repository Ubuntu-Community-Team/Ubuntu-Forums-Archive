---
title: "How do I install Jasperreports in Kubuntu"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by tomduffy on 2008-02-13
Ok, I am relatively new to Linux environments but I am getting to like it. I am running Kubuntu and I want to install Jasperreports. I downloaded the ,tar.gz, I unzipped it to a floder on my desktop, I changed to the folder and run ./configure (as instructed in forums). I now know that this would only work if I had a configure file in the directory, which I have not. I have got Build essential installed. There is no install instructions that I can see or that make sense. Where do I go from here?

---

### Post by taurus on 2008-02-13
While you are in the directory of that unpacked file, post the output of this command from a terminal.

```
ls -la
```

---

### Post by tomduffy on 2008-02-13
Output is

total 132

drwx------ 8 debbiexxxxx debbiexxxxx  4096 2008-02-13 13:59 .

drwxr-xr-x 4 debbiexxxxx debbiexxxxx  4096 2008-02-13 14:09 ..

-rw-r--r-- 1 debbiexxxxx debbiexxxxx     0 2008-02-13 13:59 ?

drwx------ 4 debbiexxxxx debbiexxxxx  4096 2008-01-11 14:46 build

-rwx------ 1 debbiexxxxx debbiexxxxx 17347 2008-01-06 16:05 build.xml

-rwx------ 1 debbiexxxxx debbiexxxxx 29189 2008-01-11 14:09 changes.txt

-rwx------ 1 debbiexxxxx debbiexxxxx  1831 2007-08-22 14:48 .classpath

drwx------ 5 debbiexxxxx debbiexxxxx  4096 2008-01-11 14:45 demo

drwx------ 3 debbiexxxxx debbiexxxxx  4096 2008-01-11 14:49 dist

drwx------ 2 debbiexxxxx debbiexxxxx  4096 2008-01-11 14:45 docs

drwx------ 2 debbiexxxxx debbiexxxxx  4096 2008-01-11 14:45 lib

-rwx------ 1 debbiexxxxx debbiexxxxx 26930 2006-02-09 10:09 license.txt

-rwx------ 1 debbiexxxxx debbiexxxxx  6629 2008-01-06 16:06 pom.xml

-rwx------ 1 debbiexxxxx debbiexxxxx   389 2006-05-30 11:11 .project

-rwx------ 1 debbiexxxxx debbiexxxxx  2446 2005-11-17 22:02 readme.txt

drwx------ 4 debbiexxxxx debbiexxxxx  4096 2008-01-11 14:45 src

debbiexxxxx@tomxxxxx-laptop:~/Desktop/jasperreports-2.0.4$

---

### Post by taurus on 2008-02-13
Can you post that readme.txt?

```
cat readme.txt
```

---

### Post by tomduffy on 2008-02-13
I have downloaded apache-ant-1.7.0 but the same applies, I do not know how to install it.
I did run apt-get install ant or something similar that I read in a forum, is this sufficient?

JasperReports Library
=============================


1. ANT Build Tool
-----------------------------

In order to compile the project or to run the sample applications 
provided with this distribution, you need to have the ANT build tool 
installed on your system. 
You can get a copy of this tool and details about how to use it 
at this address: [http://ant.apache.org/](http://ant.apache.org/)

There are several ANT specific build.xml files in this project that 
help perform different tasks. Each task has a description explaining
what it does and the list of all available tasks inside a build.xml 
file can be obtained by going to the parent directory of that particular
build.xml file and launching "ant -p" from the command line.



2. Compile the source files
-----------------------------

In the project's root directory there is a build.xml file that 
exposes different targets and helps compiling the Java source files, 
the documentation or build the JAR files.
Make sure you have the ANT build tool correctly installed on your machine
and then launch "ant -p" from the command line in the JasperReports root directory 
to see what tasks are available for building up the library from the source files.



3. Run the samples
-----------------------------

The /demo directory contains some JasperReports sample applications 
and a HSQLDB demo database.


3.1 HSQLDB
Some of the supplied samples use the HSQL Database Engine Server 
found in the /demo/hsqldb directory. In order to run those samples 
you should start the HSQLDB server first. 
There is a build.xml file in the /demo/hsqldb directory which contains 
two ANT targets: "runServer" and "runManager".
The first is for starting up the HSQL database and the second is for
lanching the HSQL client application in case you need to view the
database structure or run some queries against it.

3.2 Build and run samples
Inside each sample directory there is a build.xml file that 
helps compiling the java source files and also run the application. 
More information about each ANT task available for each sample can be obtained
by running "ant -p" from the command prompt inside the sample directory.



4. Support and training
-----------------------------

JasperSoft Corporation now offers support, services and training 
for JasperReports and you can learn more about all these here:
[http://www.jaspersoft.com/support_options.php](http://www.jaspersoft.com/support_options.php)

---

### Post by tomduffy on 2008-02-13
Sorry I should of said this is the output from the readme.txt

---

