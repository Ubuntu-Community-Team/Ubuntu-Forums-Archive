---
title: "Installing Jgrasp"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Hado on 2010-02-27
I'm completely new to the Linux OS.  
It is very foreign to me, i'm very used to the way windows does everything, including how windows does installation.
I know that Linux doesn't understand .exe files like windows does... which is part of the problem...
I have a linux zip file of a program (Jgrasp) that I want to install.  

I unzipped it into my home file and then wanted to run the program, but I have no idea what to do next.
How the heck do I run the program if i can't access the .exe's what files launch a program in linux?  Also how do i get it to recognize the JDK files?
Can anyone help?

---

### Post by elbing1 on 2010-05-04
bump - I'm having the same issue.

---

### Post by limaulime on 2010-05-09
It happened to me too. 
First of all, you have to ensure that you Java is installed properly. Follow this link and verify your java installation. 
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

If it's not instaslled, you have to install Java (jdk and jre). It took me several times and ways to get it properly  installed. sudo and ubuntu software center, everything.

After java properly installed, go to jgrasp folder/bin and click on shell script NOT the .exe file. If you are not sure which one, right-click and choose property. 

Now I can use jgrasp. Hope it helps.

---

