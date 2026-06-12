---
title: "how to install java 6 update 18"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by nani2ratna on 2010-01-21
Hi,

I want to install java 6 update 18.
Mine is 64 bit Ubuntu OS.
I have downloaded jdk-6u18-linux-x64.bin file from sun.java.com

But I don't how to install .bin file in ubuntu.
Before that can i use above file to install.

Thanks and Regards
Ratna

---

### Post by tors on 2010-01-21
Make the .bin-file executable:

 chmod 755 jdk-6u18-linux-x64.bin

And then execute the file:

 ./jdk-6u18-linux-x64.bin


This should start the installer.

I usually keep my java-installation in a directory and change my PATH to the version I wish to run:

 JAVA_HOME=/home/tors/java/java-1.4.2/
 PATH=$JAVA_HOME/bin:$PATH

or

 JAVA_HOME=/home/tors/java/java-1.6.0_18/
 PATH=$JAVA_HOME/bin:$PATH

To check which version is on the path
 
 java -version

---

### Post by nani2ratna on 2010-01-21
Hi,

Thank you very much.
I did the same and it got installed successfully.

I have already installed java-6-sun-1.6.0.15.
And there is a link between java-6-sun and java-6-sun-1.6.0.15
Now i have installed jdk1.6.0_18.
Do you know how to link java-6-sun to jdk1.6.0_18.

Thanks in advance
Ratna

---

### Post by mcdjork on 2010-01-22
This was very helpful, thanks!

---

### Post by mellice on 2010-01-24
Hi there, I followed the same steps but when I reach the last step which agree for the license, the following error happend

Unpacking...
./jdk-6u18-linux-x64.bin: 447: cannot create install.sfx.19262: Permission denied
Checksumming...
/usr/bin/sum: install.sfx.19262: No such file or directory
[: 474: -ne: unexpected operator
[: 474: -ne: unexpected operator
chmod: cannot access `install.sfx.19262': No such file or directory
Extracting...
./jdk-6u18-linux-x64.bin: 477: ./install.sfx.19262: not found
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

any help please?

---

### Post by Aruispax on 2010-01-25
I have a weird, but similar problem.  Java seems to be installed perfectly.  Java -version gives me:

java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)

I have followed instructions on this and other sites trying to get firefox to now recognize and use the Java, but it doesn't even show in the add-ons menu.  Any thoughts?  

:confused:

---

### Post by alsk on 2010-02-11
Not found a resolution yet? Well... 

Sun gives some hints:
Download (claro que si): [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com)

How to throw JDK in manually: [http://java.sun.com/javase/6/webnotes/install/jdk/install-linux-64-self-extracting.html](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux-64-self-extracting.html)

Manual install of Firefox plugin: [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html)

SO... 
This is for Jaunty (9.04) on x84_64 (AMD 64, mine Athlon 64 3000+)
- first download JDK (or JRE..)
- install the downloaded .bin to /usr/lib/jvm/ as /usr/lib/jvm/jdk1.6.0_18 
- make soft links to the jdk dir from java-6-sun (and java-default... is it needed? I did)
[FONT=Courier New]   # cd /usr/lib/jvm
   # rm java-6-sun (see that it's only a symlink)
   # rm java-default
   #[/FONT][FONT=Courier New] ln -s jdk1.6.0_18/ java-6-sun
   # ln -s jdk1.6.0_18/ java-default[/FONT]

- Create symbolic link to java 1.6.0-18 plugin 

[FONT=Courier New]# cd /usr/lib/firefox/plugins/
# mv libnpjp2.so libnpjp2.so.old
# ln -s /usr/lib/jvm/jdk1.6.0_18/jre/lib/amd64/libnpjp2.so libnpjp2.so
# ls -al libnp*[/FONT]
[FONT=Fixedsys]lrwxrwxrwx 1 root root   50 2010-02-12 00:55 libnpjp2.so -> /usr/lib/jvm/jdk1.6.0_18/jre/lib/amd64/libnpjp2.so
[/FONT] 
- restart Firefox (I restarted system too, so the libs would be reloaded for sure :rolleyes:)  
- Type url "about: plugins" and if you can see java 1.6.0-18, Great! Else see that the plug-in is enabled

- Fiddle with firefox so that IcedTea is not used for java 1.6.0 from plug-in management, instead show Sun Java 1.6.0-18 for that

Hope this helps and won't mess your system.

---

