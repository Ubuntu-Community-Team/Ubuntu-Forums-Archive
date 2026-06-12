---
title: "Trouble installing Java"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by BRKsays on 2012-05-07
I am running Ubuntu 12.04 LTS. I wanted to install Java and so I downloaded the 32-bit self extracting .bin file from java.com and tried to install it according to their instruction.

"Follow these instructions: 
[LIST=1]
[*]**Change the permission of the file you downloaded to be executable.** Type:
  chmod a+x jre-7u<version>-linux-i586.bin
where <version> is to be replaced by the version downloaded. 
**Example**: For jre-7u3, the command is 
chmod a+x jre-7u3-linux-i586.bin
[*]Verify that you have permission to execute the file. Type:
ls -l
[/LIST]
                                                                                                                                  [CENTER][IMG]http://java.com/im/download/linux_image2.gif[/IMG][/CENTER]
                                                                                

[LIST=1]
[*]**Change to the directory in which you want to install.** Type:
    cd <directory path name>
    For example, to install the software in the /usr/java/ directory, Type:
    cd /usr/java/

    ***Note about root access:**     To install Java in a system-wide location such as /usr/local, you must  login as the root user to gain the necessary permissions. If you do not  have root access, install the Java in your home directory or a  subdirectory for which you have write permissions.*
[/LIST]
                                                                                                                   
[LIST=1]
[*]**Run the self-extracting binary** Type:
  ./jre-7u<version>-linux-i586.bin

  The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter **yes** to proceed with the installation.
[*]Java is installed into its own directory. In this example, it is installed in the /usr/java/jre1.7.0_<version> directory. When the installation has completed, you will see the word **Done**.
[/LIST]
                                                                                                                                  [CENTER][IMG]http://java.com/im/download/linux_image4.gif[/IMG][/CENTER]
                                                                                

[LIST=1]
[*]  Verify that the jre1.7.0_<version> sub-directory is listed under the current directory.  Type:
ls
[/LIST]
                                                                                                                                  [CENTER][IMG]http://java.com/im/download/linux_image5.gif[/IMG][/CENTER]
                                                                                
The installation is now complete. Skip to the [**Enable and Configure**]("http://java.com/en/download/help/linux_install.xml#enable") section."
                                                                                                  

The .bin file is in my "downloads" folder in /home. I tried to follow the instruction. While doing step 3, I received a "no such file or directory". So I created a /usr/java/ using mkdir in terminal. Now I'm stuck at step 4. I again receive "no such file or directory" message. What to do?:confused: Please enlighten me. Do I have to copy the .bin file to /usr/java/? The Java version I'm trying to install is Java 6 Update 32. And also it's a 32-bit version which I'm trying to install on a 64-bit Precise. Please help.:(

---

### Post by darkod on 2012-05-07
I think they made an error. If you want to install to /usr/java and to run the installer from there, the .bin installer has to be in that folder too. That's why you get the no such file error. Or simply run it from where ever it's downloaded, and it will install in a default location.

---

### Post by spcwingo on 2012-05-07
There's also a PPA that makes this much easier.  ;-)

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

---

### Post by Pilot6 on 2012-05-07
And here is a good manual.
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

