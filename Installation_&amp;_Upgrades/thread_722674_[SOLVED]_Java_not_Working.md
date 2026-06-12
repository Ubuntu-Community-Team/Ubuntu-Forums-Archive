---
title: "[SOLVED] Java not Working"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Jiffyman on 2008-03-12
Right now I am trying to get Java working so my friend can play Runescape He has  just recently switched from Winblows to Ubuntu Gusty and I am trying to do everything in my power to make him happy with it. So far everything is fine with the exception of Java. When He first tried to get on Runescape the new plugin window popped up, being a novice user he installed the first one in the list which was GCJ WEB Plug-in. Needless to say this didn't work when He loaded up runescape the Java plugin reported an error. I managed to remove all icedtea stuff and installed Sun Java via "sudo apt-get install sun-java6-bin" it seems to install fine, but the I run "sudo java -version it says I need to get packages. Can someone help me out? Any would be appreciated.

---

### Post by Pumalite on 2008-03-12
What's the output of:
sudo apt-get install -f

---

### Post by DaV|d on 2008-03-12
Could you post the exact output please?

Also, you will need the plugin package to run java in your browser.

> sudo apt-get install sun-java6-plugin

Hope your friend enjoys his gutsy experience :p

---

### Post by taurus on 2008-03-12
Double post, difference title, same question/problem.  :rolleyes:

[http://ubuntuforums.org/showthread.php?t=722673](http://ubuntuforums.org/showthread.php?t=722673)

---

### Post by Jiffyman on 2008-03-12
joseph@joseph-desktop:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * kaffe
 * cacao
 * java-gcj-compat
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
joseph@joseph-desktop:~$ 
 

joseph@joseph-desktop:~$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Edit: Sorry..... I don't even know how I double posted.

---

### Post by taurus on 2008-03-12
Try

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```
and make sure java 6 is the default one from the third command.  You can check by running this command again.

```
java -version
```

---

### Post by Jiffyman on 2008-03-13
I tried the following commands and they worked on my laptop which had the same kinda problem. I just phoned the house and I told him to run these commands every one worked. When he went to Firefox and put in runescape the browser told him to download the plugin. I think this is partly a screw up on my part because I installed Firefox3.0 and reinstalled Firefox2.0 thanks to another guide. I remember him telling me that the  browser specifically ask for Java Run Time Environment instead of GCJ, Iced, or the Java6 Web Plugin. From what He told me Java is apparently installed on his machine. What command can I run to prove that it's working? I probably also need to create a symbolic link to the plug-ins in Firefox plug-in folder, but I am not sure where these folders are located.

By the way how do I give a thanks.

---

### Post by Jiffyman on 2008-03-13
Bump.....

---

### Post by DaV|d on 2008-03-13
> **Jiffyman said:**
> From what He told me Java is apparently installed on his machine. What command can I run to prove that it's working?

To test your JRE execute
```
java -version
```

You should get an output similar to this:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

> **Jiffyman said:**
> I probably also need to create a symbolic link to the plug-ins in Firefox plug-in folder, but I am not sure where these folders are located.

the firefox plugin folder is /usr/lib/firefox/plugins

> **Jiffyman said:**
> By the way how do I give a thanks.
[All about the Thanks feature]("http://ubuntuforums.org/showthread.php?t=702596")

---

### Post by Jiffyman on 2008-03-13
Told him to run "java -ver" and it came up with pretty much the same info as the example.

Could someone tell me how to create the symbolic link?

---

### Post by DaV|d on 2008-03-13
first, make sure you have you have the package "sun-java6-plugin" installed:
```
sudo apt-get install  sun-java6-plugin
```

restart Firefox and check whether the plugin is installed correctly by visiting the [java test page]("http://www.java.com/en/download/help/testvm.xml").

If you're asked to download the java plugin again, or the plugin doesn't work as expected,
execute the following to set up the symbolic link:
```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

Restart Firefox again and re-visit the [java test page]("http://www.java.com/en/download/help/testvm.xml").

Good luck!

---

### Post by Jiffyman on 2008-03-13
I had him perform the symbolic link and now everything works. Thanks for all the input that helped put this problem to an end. One more question before I kill the thread. How do I mark it as solved.

---

### Post by DaV|d on 2008-03-13
Thread Tools > Mark this thread a solved.

Glad everything's ok! :)

---

### Post by Jiffyman on 2008-03-13
Thanks again.

---

### Post by siofwolves on 2008-03-16
Thanks people. I was having the exact same problem.

Sorted now. :)

---

### Post by hulio40 on 2008-03-25
i have did everything that was sayd here and i still get the grey box an after a few seconds the box turns black and then nothing i need to run this game:   [www.needformadness.com](www.needformadness.com)  pls someone help

---

### Post by DaV|d on 2008-03-25
Are you using firefox? and do you hava java 6 installed?
also, could you paste the output of ```
ls -l /usr/lib/firefox/plugins
```

---

### Post by hulio40 on 2008-03-26
> **DaV|d said:**
> Are you using firefox? and do you hava java 6 installed?
also, could you paste the output of ```
ls -l /usr/lib/firefox/plugins
```

yes i have java 6 and i use firefox 

heres what i get:

total 16
lrwxrwxrwx 1 root root   37 2008-02-08 12:00 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   34 2007-12-28 16:10 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root   64 2008-03-24 23:14 libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root   39 2008-03-24 14:54 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   36 2007-12-28 06:48 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2007-12-28 06:48 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2007-12-28 06:48 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2007-12-28 06:48 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2007-12-28 06:48 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2007-12-28 06:48 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2007-12-28 06:48 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2007-12-28 06:48 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 9104 2008-03-25 11:27 libunixprintplugin.so
lrwxrwxrwx 1 root root   46 2008-03-17 16:53 mplayerplug-in-dvx.so -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root   47 2008-03-17 16:53 mplayerplug-in-dvx.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
veaceslav@ubuntu:~$

---

### Post by hulio40 on 2008-03-26
and when i run runescape it says eroor loading applet

---

### Post by DaV|d on 2008-03-26
I think that your browser is using the gcjwebplugin instead of the sun-java-plugin.
You can either:
1) uninstall the package 'gcjwebplugin'/'gcjwebplugin-4.1'/'gcjwebplugin-4.2' whichever is installed 
or
2) remove the symlink 'libgcjwebplugin.so' from the plugins folder by executing ```
sudo unlink /usr/lib/firefox/plugins/libgcjwebplugin.so
```

Afterwards, restart firefox.

I recommend method 1 unless you're using the gcjwebplugin package for something else, as it is both cleaner and saves space ;)

If you're still getting errors, after doing the above could you please post the output of
```
ls -l /etc/alternatives/firefox-flashplugin
ls -l /etc/alternatives/firefox-javaplugin.so
```

---

### Post by hulio40 on 2008-03-26
> **DaV|d said:**
> I think that your browser is using the gcjwebplugin instead of the sun-java-plugin.
You can either:
1) uninstall the package 'gcjwebplugin'/'gcjwebplugin-4.1'/'gcjwebplugin-4.2' whichever is installed 
or
2) remove the symlink 'libgcjwebplugin.so' from the plugins folder by executing ```
sudo unlink /usr/lib/firefox/plugins/libgcjwebplugin.so
```

Afterwards, restart firefox.

I recommend method 1 unless you're using the gcjwebplugin package for something else, as it is both cleaner and saves space ;)

If you're still getting errors, after doing the above could you please post the output of
```
ls -l /etc/alternatives/firefox-flashplugin
ls -l /etc/alternatives/firefox-javaplugin.so
```

i did the first method and now firefox says i am missing a plugin and to go manually instal java 

tried it in epiphany and on the java test page i see that java orange box loading and it works but when i run rs or needformadness it crashes and closes my windows...  

would i need to tell firefox what plugin to use? and how would i do that 

here r the outputs of both commands:

lrwxrwxrwx 1 root root 46 2008-02-08 12:00 /etc/alternatives/firefox-flashplugin -> /usr/lib/flashplugin-nonfree/libflashplayer.so

lrwxrwxrwx 1 root root 64 2008-03-24 14:54 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by hulio40 on 2008-03-26
everything works fine in epiphany web browser but on firefox nothing :confused:

---

### Post by DaV|d on 2008-03-26
Well you have 2 symlinks to the same plugin, not sure whether that might be the problem.
Remove one link with this:
```
sudo unlink /usr/lib/firefox/plugins/libjavaplugin_oji.so
```
That should leave you with only one link pointing to a java plugin.

To check if everything's ok, could you please post the output of the following:
```
ls -l /usr/lib/firefox/plugins
```

Also, what version of firefox are you using?

---

### Post by hulio40 on 2008-03-26
nope changed nothing still tells me im missing a plug in but if im bothering u its alright i mostly use epiphany i find it fast and simple anyways heres the output:


total 12
lrwxrwxrwx 1 root root   37 2008-02-08 12:00 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   39 2008-03-24 14:54 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   36 2007-12-28 06:48 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2007-12-28 06:48 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2007-12-28 06:48 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2007-12-28 06:48 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2007-12-28 06:48 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2007-12-28 06:48 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2007-12-28 06:48 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2007-12-28 06:48 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 9104 2008-03-25 11:27 libunixprintplugin.so
lrwxrwxrwx 1 root root   46 2008-03-17 16:53 mplayerplug-in-dvx.so -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root   47 2008-03-17 16:53 mplayerplug-in-dvx.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt

---

### Post by DaV|d on 2008-03-27
Last thing I can think of, besides a re-installation of sun-java6-bin is:
```
sudo update-alternatives --config firefox-javaplugin.so
```

---

### Post by jasong on 2008-03-27
Not sure if this is proper etiquette, but...

Could a mod please place a comment in post #6 of this thread that running those first two commands might make Ubuntu(Gutsy Gibbon 7.10 in my case) "notice" that it's set up wrong.  That particular plugin package doesn't seem to exist in Gutsy Gibbon, but another package was referring to it.  Running those first two lines caused Gutsy Gibbon to ask for an update(unless it was a fortuitous coincidence) and that seems to have solved the problem.  I'll post again if I'm wrong about the solution sticking around.

Btw, the problem I keep referring to is that java would work the first 1-3 times I would access a page, and then it wouldn't run the java stuff at all.  I would just get blank space where the java stuff is supposed to be.

Sorry if this has already been mentioned, I haven't read the whole thread.  Even if this post is deleted, please consider my mod comment request.

---

### Post by Menky on 2008-04-03
ls -l /etc/alternatives/firefox-javaplugin.so

That did the trick for me. Apparently the java-gcj package was not helping because before I had:

mentor@mentoris-desktop:~$ ls -l /etc/alternatives/firefox-javaplugin.so

lrwxrwxrwx 1 root root 48 2008-04-03 00:48 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-gcj/jre/lib/libgcjwebplugin.so


ander after i removed:


sudo aptitude remove java-gcj-compat

then I got:

mentor@mentoris-desktop:~$ ls -l /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root 64 2008-04-03 12:57 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Now Java.com recognizes my latest version + facebook photo uploading works with Java + everything.

Thanks again so much  :)

---

