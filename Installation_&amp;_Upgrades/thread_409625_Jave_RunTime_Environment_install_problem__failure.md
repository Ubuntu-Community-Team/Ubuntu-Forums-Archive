---
title: "Jave RunTime Environment install problem / failure?"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by borisdaniel on 2007-04-14
Hey.. I dont know why but am getting a error message when i try to install the java run time, 

I get a authentication failure once i enter root pw.

Here's the instruction from the [website]("http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80")

>  To install the Linux RPM (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java

      Note about root access: To install the JRE in a system-wide location such as/usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0-linux-i586-rpm.bin
   5. Start the installation process. Type:
      ./jre-1_5_0-linux-i586-rpm.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.

Thanks :)

Boris

---

### Post by zvacet on 2007-04-14
You downloaded rpm file instead of deb,and that is the reason you can not install.If you have all repositories open,you can install java from synaptic.Search for** sun**.

---

### Post by borisdaniel on 2007-04-14
> You downloaded rpm file instead of deb
am sorry i dont understand. on the website the download available is rpm i dont know what deb is.

I downloaded the first jre-6u1-linux-i586-rpm.bin

any suggestion??

thanks...
boris

---

### Post by zvacet on 2007-04-15
You should download **Linux (self-extracting file)**.And,yes my  suggestion is still the same.Install Java from synaptic.If you don´t have all erpositories open here is how to do it
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
After that reload and you will have Java in synaptic.Search **sun** and pick any version of Java you like or need.

---

