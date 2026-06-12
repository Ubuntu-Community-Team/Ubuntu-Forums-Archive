---
title: "Problem running Java"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by iSandman on 2012-12-12
Hi there, For some reason every time I try and install Java, it opens a folder instead of running an executable file...The problem is, there is no executable file. I have no idea what to do and completely at a loss. Would be much appreciated if someone could help me install Java!

---

### Post by sammiev on 2012-12-12
I like to install without using PPA's and this is the method I use. Others will tell you to use a PPA. YOU can if you wish, this is just safer.

Latest [Java]("https://sites.google.com/site/easylinuxtipsproject/java").

---

### Post by iSandman on 2012-12-13
My whole problem is that I need to open a application but the application uses Java. For some reason there is no executable file for the program in Linux but in Windows there is. The program says on Windows that it can only be used in Linux but as I said there is no executable file for the program in Linux. Am I trying to open it wrong?

---

### Post by sammiev on 2012-12-13
If I'm reading your post correctly this should do the trick. You may wish for someone else to come around as well.

the program should be in binary format (or an exacutable)
type in terminal
sudo chmod +x ./(name of the program)
then type
./(name of the program)

---

### Post by iSandman on 2012-12-13
> **sammiev said:**
> If I'm reading your post correctly this should do the trick. You may wish for someone else to come around as well.

the program should be in binary format (or an exacutable)
type in terminal
sudo chmod +x ./(name of the program)
then type
./(name of the program)


I tried this, for some reason it won't work? It says permission denied.

---

### Post by QIII on 2012-12-13
Are you having a problem installing the Java runtime environment, or just getting a Java application running?

Would you post the results of ```
java -version
```

and also let us know if you are trying to execute a .jar file?

---

### Post by iSandman on 2012-12-13
Ok, essentially I'm trying to run a file. It's called UnBrickableResurrectorR40.jar. It opens up a folder which it's not suppose to do, it's suppose to open a program. I tried opening this program with the terminal and tells me that permission denied or along those lines. It was said that I needed Java to run this program, So I downloaded Java, But Java is acting the same way as this program I'm trying to run. It opens a folder instead of starting the application. So my main problems are: 1. Java install opens itself as a folder. 2. UnBrickableResurrectorR40.jar opens itself as a folder. 3. Terminal refuses to open these programs.

---

### Post by QIII on 2012-12-13
You can use sammiev's method to install Oracle Java (which he recommends and I don't any longer -- we both used to) or look at the wiki link in my signature, under "Oracle Java 7", "Command line methods" and click the link "Using webupd8.org's strikingly simple method."  The reason I now recommend the webupd8 method is that they are reputable and they keep up with the release of Oracle Java updates so that your Java version is updated automatically when you do your normal Ubuntu updates.  With the Easy Linux Tips method, you have to be aware of new updates and reinstall.

Easier still, most likely, would be to install OpenJDK from the repository.

That may already be installed, which is why I asked you to post the results of ```
java -version
```If OpenJDK is installed and the writer of the application is clever enough to understand that OpenJDK 7 is the open source reference implementation for Oracle Java 7 -- which means that even Oracle is committed to making sure Oracle Java complies with OpenJDK 7, not the other way around -- then it should work with OpenJDK 7.  If he is not aware of that relationship, the application may balk and Oracle Java 7 will have to be installed.

Try with OpenJDK 7 first.

To run your .jar from the command line, try

```
java -jar /path/to/filename.jar
```(assuming all of the resources are available and can be accessed with the classpath given in the manifest, which is usually the case when someone distributes the application) which is often convenient the first time you run something so you can watch the terminal for exceptions that might be thrown.

---

### Post by iSandman on 2012-12-13
> **QIII said:**
> You can use sammiev's method to install Oracle Java (which he recommends and I don't any longer -- we both used to) or look at the wiki link in my signature, under "Oracle Java 7", "Command line methods" and click the link "Using webupd8.org's strikingly simple method."  The reason I now recommend the webupd8 method is that they are reputable and they keep up with the release of Oracle Java updates so that your Java version is updated automatically when you do your normal Ubuntu updates.  With the Easy Linux Tips method, you have to be aware of new updates and reinstall.

Easier still, most likely, would be to install OpenJDK from the repository.

That may already be installed, which is why I asked you to post the results of ```
java -version
```If OpenJDK is installed and the writer of the application is clever enough to understand that OpenJDK 7 is the open source reference implementation for Oracle Java 7 -- which means that even Oracle is committed to making sure Oracle Java complies with OpenJDK 7, not the other way around -- then it should work with OpenJDK 7.  If he is not aware of that relationship, the application may balk and Oracle Java 7 will have to be installed.

Try with OpenJDK 7 first.

To run your .jar from the command line, try

```
java -jar /path/to/filename.jar
```(assuming all of the resources are available and can be accessed with the classpath given in the manifest, which is usually the case when someone distributes the application) which is often convenient the first time you run something so you can watch the terminal for exceptions that might be thrown.


Thank you so much, The application worked!

---

### Post by sammiev on 2012-12-13
Hey QIII and thanks for dropping by and adding to this thread. Glad we both answered it correctly. Yes we have a different ways to get the same job done. :) Now we need to get the OP to mark this thread as solved.

---

### Post by MontrealCorp on 2013-02-13
i like this thread , got links for noob like me for ubuntu.


one thing tho, i like QIII link but i like sammiev too.

is there any security reason why QIII do not use openjdk method ?

ty

pretty important cause it is to play poker so...

---

