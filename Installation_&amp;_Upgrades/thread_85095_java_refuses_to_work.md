---
title: "java refuses to work"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by allroz on 2005-11-01
I've been fiddling with getting java to work in firefox for about three weeks now. It just doesn't work for me. I've tried seroiulsy everything, and tried all installation guides. Can someone give me a method that will work? I need to be able to see java scripting for my work login. Thanks.

---

### Post by tseliot on 2005-11-01
[QUOTE=allroz]I've been fiddling with getting java to work in firefox for about three weeks now. It just doesn't work for me. I've tried seroiulsy everything, and tried all installation guides. Can someone give me a method that will work? I need to be able to see java scripting for my work login. Thanks.[/QUOTE]
Try Automatix, it will set the java plugin for you:

[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by allroz on 2005-11-01
This is the error that i get

```
tar: automatix-breezy_v2.15.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Ideas?

---

### Post by MakubeX on 2005-11-01
[QUOTE=allroz]I've been fiddling with getting java to work in firefox for about three weeks now. It just doesn't work for me. I've tried seroiulsy everything, and tried all installation guides. Can someone give me a method that will work? I need to be able to see java scripting for my work login. Thanks.[/QUOTE]

Javascript or java applets? If you need to make Java work, you only need to link the libjavaplugin (that is contained in the JDK) in the firefox/mozilla plugin folder.

---

### Post by tseliot on 2005-11-01
[QUOTE=allroz]This is the error that i get

```
tar: automatix-breezy_v2.15.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Ideas?[/QUOTE]
Yep, the current version (which yuo have downloaded) is automatix-breezy_v2.1[COLOR="Red"]6[/COLOR].tar.gz

Type the (correct) command again

---

### Post by allroz on 2005-11-01
Same thing. ```
tar: automatix-breezy_v2.16.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```


Am i just unable to perform normal operations or what? Seems everything i try to install fails.

---

### Post by bfonseca on 2005-11-20
[QUOTE=allroz]I've been fiddling with getting java to work in firefox for about three weeks now. It just doesn't work for me. I've tried seroiulsy everything, and tried all installation guides. Can someone give me a method that will work? I need to be able to see java scripting for my work login. Thanks.[/QUOTE]
I am having the same problem with the applets, 

however i have manage to install the plugin (I think it is correct). Before firefox kept asking me to install the plugin and now it doesnt do that. But i can not see the applets on the website.  I have used automatix and it fixed alot of my problems but it did not fix the applet problem. To get the plugin to work I followed these steps:

first i downloaded the jre from the java.sun.com and used the ark to unzip 
when ark finished it left me with a folder: jre1.5.0_05 

then i took the folder created by ark and mv that to /usr/local/

from here i did a search for all plugins and went to all of them and typed

ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so

and i did this for every plugin (because i am new to ubuntu) I didnt know which one to put it in. 

However after this i restarted firefox and i was no longer being prompt to install the plugin. but the applet still does not work.

any help to fix that problem would be greatly appreciated.
thanks 
brian

---

### Post by bfonseca on 2005-11-20
[QUOTE=allroz]I've been fiddling with getting java to work in firefox for about three weeks now. It just doesn't work for me. I've tried seroiulsy everything, and tried all installation guides. Can someone give me a method that will work? I need to be able to see java scripting for my work login. Thanks.[/QUOTE]
i fixed the problem with my computer. use the steps on my previous post but instead of using:

dont use:
ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so

instead use:
ln -s /usr/bin/jdk/jdk1.5.0_05/jre/plugin/i386/ns7/libjavaplugin_oji.so

restart the borwser and try it again, it should work it works for me. I did this to all the browsers plugins and now the applets work.

I hope this fixes your problem too.
brian

---

### Post by irosenbl on 2006-01-11
These postings and others on the forums have been very helpful... except I still cannot get applets to show graphics on Firefox.
Do these instructions (a nd those in the Sun download site apply to Ubuntu 5.04 (one before Breezy)?

If so, I can get logged in as root (using the Root Terminal at Applications>Systems Tools) and unpack the jre file from Sun but when it is done it creates a direcotry jrel.5.0_06 tha tI cannot cd to, or do anything with.  The few commands I know to use tell me tehre is no such file or directory.

Stubbornly I tried to do the ln -s command recommended in the Sun instructions and also the version of the ln command that Brian posted here.  All of them return me to the command prompt without indicating any problems.   When I restart Firefox and go to Edit>Preferences>Advanced I do not have an "Enable Java" to select.

Can anyone tell where I am going wrong?

Thanks,
Isabel

---

### Post by bfonseca on 2006-01-17
Have you tried Automatix...I'm not sure if it works with 5.04 but if it does that may fix the problem.
Brian

---

