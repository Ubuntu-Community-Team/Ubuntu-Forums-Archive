---
title: "installing Java on Ubuntu 6.10"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by Kemfisee on 2006-12-11
I am having a problem installing or figuring out how to install java on Ubuntu 6.10. i have 6.06 installed on another computer and found it in the Synaptic package manager and it works fine,, but can't find it in 6.10,,, the  
repository setup is different in 6.10 then 6.06,, so please can anyone help here!!!!!!

thanks

---

### Post by msumurph on 2006-12-11
> **Kemfisee said:**
> I am having a problem installing or figuring out how to install java on Ubuntu 6.10. i have 6.06 installed on another computer and found it in the Synaptic package manager and it works fine,, but can't find it in 6.10,,, the  
repository setup is different in 6.10 then 6.06,, so please can anyone help here!!!!!!

thanks

I did it using Synaptic.  First I enabled Universe and Multiverse under SETTINGS-REPOSITORIES.  Then, I hit the Reload button.  Finally, I scrolled down the list of apps until I found sun-java5-jre.  You may want to install sun-java5-plugin and/or sun-java5-jdk depending on your needs.

Good luck!

---

### Post by Dave54 on 2006-12-11
I found that [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") explains everything you need to know about repositories and java.

As for how I found it, [https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/") links to almost everything you need in ubuntu.

---

### Post by Zizo on 2007-09-27
Hi all,

I want to install Java 6 on ubuntu 6.06. I know java 5 is in the repository for this version of ubuntu, but I wanted to try with  Java 6. 

Anyway, I downloaded the **bin** file (java_ee_sdk-5_03-linux.bin) from Sun 's website. Doing **sudo ./java_ee_sdk-5_03-linux.bin** gives the following:

[B]Checking available disk space...
Checking Java(TM) 2 Runtime Environment...
Extracting Java(TM) 2 Runtime Environment files...
*** glibc detected *** double free or corruption (!prev): 0x080871b0 ***
Deleting temporary files...

  What is the solution to this?

Thank you in advance ...
[/B]

---

### Post by Zizo on 2007-09-27
Hi again,

I forgot to mention that I was trying to install the : 
**JDK 6 Update 2 with Java EE 5 SDK Update 3**

from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
This is where I got problems.

but for **JDK 6 Update 2 **everything worked fine.

---

