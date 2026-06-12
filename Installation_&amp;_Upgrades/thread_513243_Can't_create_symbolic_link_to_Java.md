---
title: "Can't create symbolic link to Java"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by parthamage on 2007-07-30
I am following the instructions to install Java under 7.04.  I am using the instructions from Java.  I got the Java installed in a home folder, and then modified the link command to reflect the change in directories and version number, but every time I try to create the link, I get "Permission denied".  Example follows:

charles@charles-desktop:/usr/lib/firefox/plugins$ ln -s /home/charles/java/jre1.6.0_02/plugin/i386/ns7/libjavaplugin_oji.so .
ln: creating symbolic link `./libjavaplugin_oji.so' to `/home/charles/java/jre1.6.0_02/plugin/i386/ns7/libjavaplugin_oji.so': Permission denied
charles@charles-desktop:/usr/lib/firefox/plugins$ 

Can anyone help?

---

### Post by dreadlord_chris on 2007-07-30
yup.... since you are trying to create a link in a **system** folder (root owned) you need to **sudo** that link command:
```
 sudo ln -s /home/charles/java/jre1.6.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

```

---

### Post by crunchfighter on 2007-12-19
How can I see if my symbolic link is working properl?  I have installed/resinstalled java6 several times via Synaptic and terminal, created the symbolic link several times.  

In my terminal window:

craig@t41-laptop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
craig@t41-laptop:~$ 
_________________________________________

On java.com 'verify version' page:

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

________________________________________

Additional troubleshooting: I tried to install my java-driven stock broker's desktop platform, but fails the install because I do not have jvm vresion 1.5 or later.  This means that I have a java install problem with ubuntu rather than just a java problem with Firefox, true?

Any thoughts?  

Oh yeah, been using ubuntu for about a week.  Please be gentle.  It's my first time.

---

