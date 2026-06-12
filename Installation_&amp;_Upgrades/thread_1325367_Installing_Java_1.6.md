---
title: "Installing Java 1.6"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by back on 2009-11-13
Hi, I`m new in ubuntu and linux system, but I really want to use it. In my first steps I'm having some newbie trouble.

When I tried to install Java 1.6 with command "sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk" got this error message "-bash: $: command not found". 

What I need to do to fix this problem?

Thanks in advance and sorry for my poor english :)

---

### Post by Axos on 2009-11-13
If you used copy and paste to copy that command line into a terminal window, is there any chance you may have accidentally included the leading "$" prompt from wherever you copied the command line?

Personally, I just download the JDK directly from Sun's web site rather than getting it from the Ubuntu repository. But it requires more steps to install and configure. Let me know if you would like the detail and I'll post it.

---

### Post by back on 2009-11-13
Thanks for your reply! 

Maybe this was an issue, because now I get this message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-bin has no installation candidate


Details of installation in your way would be nice :)

---

### Post by Axos on 2009-11-13
First, I recommend creating a dedicated "java" user for installing Java-related software. This is completely optional but I like that it isolates Java from the rest of the system. If you want to take this approach, just click on System -> Administration -> Users and Groups and then click the Unlock button and enter your password. Next, click the Add User button and enter the following:

Username: java
Real name: java
Profile: Desktop user
User password: [I use my usual password]
Confirmation: [re-enter the same password]

Click the OK button to create the user.

Next, click on this link:

[http://java.sun.com/javase/downloads/widget/jdk6.jsp](http://java.sun.com/javase/downloads/widget/jdk6.jsp)

Select either the Linux or Linux x64 platform depending upon whether you are running the 32-bit or 64-bit version of Ubuntu. Leave the "Use Sun download manager" checkbox UNchecked and click Continue. This will pop up an annoying dialog asking you to log in. Click "Skip this step". Depending upon whether you chose the 32-bit or 64-bit version, download one of the following files by clicking the blue text link (don't click the checkbox nor the "Download selected with Sun Download Manager):

32-bit: jdk-6u17-linux-i586.bin
64-bit: jdk-6u17-linux-x64.bin

Make sure you don't download the RPM version! RPM is for a different Linux distribution (Red Hat, I believe).

Once you've downloaded the appropriate file, open a terminal and make it executable with chmod:

chmod +x jdk-6u17-linux-i586.bin
 or
chmod +x jdk-6u17-linux-x64.bin

If you created a "java" user, now is the time to log off your current account and log in as "java". Open a terminal.

In the terminal, change (cd) to the directory where you want to install the JDK. Since the installer will create a subdirectory in your current directory and install all the files within that subdirectory, it's easiest to just stay in your home directory.

Now you are finally ready to run the installer you downloaded. If you are logged in as "java", you'll need to refer back to where you downloaded it while you were logged in as your regular user. If you downloaded it to your desktop and your regular user name is "foo", the command would be either:

~foo/Desktop/jdk-6u17-linux-i586.bin
 or
~foo/Desktop/jdk-6u17-linux-x64.bin

The first thing the installer will do is barf out a license agreement. Use the space bar to page through this document, carefully reading every word about how Sun will own all your offspring, etc. The usual crap every company wants. Eventually you'll reach a prompt to enter "yes" or "no" (without the quotes) to agree to the agreement. Once you enter "yes" (without the quotes), it will begin unpacking the files. Finally, it will prompt you to press Enter to continue. If you press Enter, it will fire up your browser to ask you to register on their web page. Bah. Instead of pressing Enter, I just press Ctrl-C. The JDK is already installed and there is no need to let the installer fire up your browser.

If you logged in as "java", you can now log off and log back in as your regular user.

In your home directory, edit or create a file called .gnomerc and put this line in it (assuming you installed the JDK with the dedicated user "java"):

PATH=/home/java/jdk1.6.0_17/bin:$PATH

If you installed the JDK using your regular user name, change the line to point to where you actually installed it.

To make GNOME run the .gnomerc file you just created (or modified), log off and log back in.

You should now be able to open a terminal and run:

java -version

...and see something like this:

java version "1.6.0_17"
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)
Java HotSpot(TM) Server VM (build 14.3-b01, mixed mode)

I hope the above is clear and accurate. Let me know if you have any questions or problems.

Oh, if you want to enable the browser plug-in for Firefox, you need to take the following steps:

cd /usr/lib/mozilla/plugins
sudo ln -s /home/java/jdk1.6.0_17/jre/plugin/i386/ns7/libjavaplugin_oji.so

Again, that assumes you installed the JDK as "java". Modify the path if you installed it as your regular user.

Later, when you install a newer version of the JDK, don't forget to go back to the /usr/lib/mozilla/plugins directory, remove the old symlink, and create a new one to the new JDK's plugin.

---

### Post by wojox on 2009-11-13
```
sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin
```

 [Go here to test]("http://www.java.com/en/download/help/testvm.xml")

---

### Post by Axos on 2009-11-13
Good point. Despite those errors, it might have already installed. Worth testing first before going through all the steps to install it the manual way from Sun's distribution.

---

### Post by back on 2009-11-14
I tried Axos method to install java. All installation process was fluent and in final step I created file .gnomerc, in file wrote my destination where is installed java (PATH=/home/jdk1.6.0_17/bin:$PATH) and placed in /home directory. Rebooted whole system and in terminal put "java -version command", but output said:

root@back:~# java -version
-bash: java: command not found

Maybe I placed .gnomerc file in wrong direction?


Edited:

I founded some solutions. They said that I need to put some text in .bashrc file. For me it would be something like this:

PATH=$PATH:/home/jdk1.6.0_17/bin
export PATH
JAVA_HOME=/home/jdk1.6.0_17
export JAVA_HOME

Do I need to do this step?


EDITED 2:

Okey, now everything is working fine. So much thanks for all you guys, such a great community :)

EDITED 3:

hmm, it looks like I celebrated too early.. Now I'm trying to install glassfish application server and end up with this error:

root@back:~# java -Xmx256m -jar glassfish-installer-v2.1.1-b31g-linux.jar
Exception in thread "main" java.io.IOException: Cannot run program "java": java.io.IOException: error=12, Cannot allocate memory
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:459)
        at java.lang.Runtime.exec(Runtime.java:593)
        at java.lang.Runtime.exec(Runtime.java:466)
        at glassfish.main(glassfish.java:97)
Caused by: java.io.IOException: java.io.IOException: error=12, Cannot allocate memory
        at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
        at java.lang.ProcessImpl.start(ProcessImpl.java:65)
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:452)
        ... 3 more


I have 512 RAM, in my opinion it should be enough.

EDITED 4:

Now I'm struggling with this command "[B]lib/ant/bin/ant -f setup.xml"

[/B]BUILD FAILED
/root/glassfish/setup.xml:177: The following error occurred while executing this line:
/root/glassfish/setup.xml:607: exec returned: 1

---

### Post by Axos on 2009-11-14
Unfortunately, I have never tried to install glassfish so you've gone beyond my experience level. :D

Have you solved the problem you described in edit 3? So now you just need help with edit 4?

Based on the "exec returned: 1" message, I'm going to guess that means the exec system call and when it returns 1 that means EPERM: "Operation not permitted". I think that could be caused by trying to execute a file which has not been marked executable (chmod +x). Is there any more detail in the output to suggest which file it is trying to execute?

At this point I am just making guesses. You might find better help on a Java-specific forum like [http://www.coderanch.com/forums](http://www.coderanch.com/forums). Or Sun also has forums of their own: [http://forums.sun.com/index.jspa](http://forums.sun.com/index.jspa).

---

### Post by back on 2009-11-14
Yes I solved EDIT 3 problem. If anybody will need help how to fix this, just change "java **-Xmx256m** -jar glassfish-installer-v2.1.1-b31g-linux.jar" to -Xmx128m or -Xmx64m.

Of course it's not very good solution, because glassfish likes to have some more space, but it's better than nothing.

When I struggled with edit 4, I though it would be better to use something not so "huge", so I just downloaded and installed tomcat app server. Smaller and quite stable. Works well, no problems so far.


One more thanks Axos for your help ;)

---

### Post by Axos on 2009-11-14
The good thing about installing Java the way you did is that you can install more than one version if you need to test applications under Java 1.5, for example. All you have to do is repeat the installation procedure with Java 1.5's installer. It will install in its own subdirectory. Then you can change your PATH to point to the Java 1.5 bin directory. Boom, instant version switching. Some apps also have command line options which let you point them to the JDK directory to use. For example, the NetBeans IDE has the --jdkhome option:

netbeans --jdkhome /home/java/jdk1.6.0_17

---

