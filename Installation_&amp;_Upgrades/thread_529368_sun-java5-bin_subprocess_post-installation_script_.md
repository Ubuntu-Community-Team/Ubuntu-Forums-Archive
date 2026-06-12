---
title: "sun-java5-bin: subprocess post-installation script returned error exit status 139"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by curation on 2007-08-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/133423](https://bugs.launchpad.net/ubuntu/+bug/133423) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				My problem is that the installation of Sun Java Runtime 5.0 did not install correctly. This has disabled the functionality for installing other programs as well as disabling components of other programs such as Firefox. I believe with java element involved.

Unfortunately, I didn't realize there was a more recent version of Sun Java Runtime available before I used the Add/Remove Applications tool to install Java.

Any ideas?

---

### Post by curation on 2007-08-19
btw, I am using Fiesty - UbuntuStudio

---

### Post by curation on 2007-08-22
Ok, maybe a solution. I found a workaround posted at: [http://ubuntuforums.org/showthread.php?t=332674](http://ubuntuforums.org/showthread.php?t=332674)

Basically, I installed a newer version which I made as my default & have left the broken java install as is on my system which seems to have worked. I also replaced Java6u1 with the currently available newer version: Java6u2 .

Install Java's JDK and Eclipse for performance and ease
INSTALLING JAVA (JDK/JRE)
Here is the updated version used to install Java's JDK 6u1 on Edgy. The method doesn't use packages, opting to use Sun's .bin file instead. Visit java.sun.com to download their .bin file. You probably want: jdk-6u1-linux-i586.bin.

STEP: Download it to your desktop. Once it's fully downloaded, open a command prompt and execute it like so:
Code:

cd ~/Desktop
sudo chmod +x *.bin
sudo sh ./jdk*.bin

STEP: Executing the .bin file creates a folder on your desktop named jdk1.6.0_01. Rename that folder to Java6u1. Now move that folder to /usr/lib

Code:

sudo mv Java6u1 /usr/lib

STEP: Now add Java to update-alternatives and make it the default like so:

Code:

sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
sudo update-alternatives --config java

STEP: Don't forget your Java plugin

Code:

sudo ln -s /usr/lib/Java6u1/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

---

### Post by Hildsvfar on 2007-08-22
Have you had any luck removing the other versions of Java?  I have 5 and 6 that are broken, and won't fix with apt-get or anything, and I guess I have one working version... and that's it.  I can't install anything because it says I have broken dependencies and can't remove java 5 and 6 even when I try.

---

### Post by Hildsvfar on 2007-08-22
it goes a little something like this:

```
sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java5-bin sun-java6-bin
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 145MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128260 files and directories currently installed.)
Removing sun-java5-bin ...

(update-desktop-database:6503): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing sun-java5-bin (--remove):
 subprocess post-removal script returned error exit status 139
Removing sun-java6-bin ...

(update-desktop-database:6510): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing sun-java6-bin (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 sun-java5-bin
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by curation on 2007-08-22
I am a newbie- so take what I say with that into consideration. Thus far, I haven't found a single thread which directly troubleshoots this problem. 

Perhaps it would be a good idea to have a Warning! about the potential for broken packages with Java on Ubuntu during install? 

Anyways, what I found is that I can now Add/Remove Programs with Java 6u2 despite the broken Java 5 install still being on the system. I think the key was installing Java 6u2 from .bin and making  the Java 6u2 path the 'default' within the conf.  Being a newbie, I have chosen not to mess with the system and leave the broken Java 5 alone. 

If I have a problem in the future with this set-up, I will certainly post about it.

---

### Post by curation on 2007-08-23
I spoke too soon... my current problem is thus:

E: gnomebaker: subprocess post-installation script returned error exit status 139
E: sun-java5-bin: subprocess post-installation script returned error exit status 139
E: sun-java6-bin: subprocess post-installation script returned error exit status 139

Any ideas?

---

### Post by Hildsvfar on 2007-08-26
Are we honestly the only two people having this problem?  This sucks.

---

### Post by Hildsvfar on 2007-08-28
Where are the files for java at?  I'm about ready to manually delete them and try and get apt-get to fix it.  Not being able to install new packages is really getting on my nerves.

---

### Post by Hildsvfar on 2007-08-29
...that didn't help either...

I really don't want to reinstall everything again....

---

### Post by Hildsvfar on 2007-09-07
Is this problem seriously unsolvable?  Because I'm gonna have to reinstall Ubuntu soon if it really is, and I really don't want to.

---

### Post by curation on 2007-09-08
I do believe this problem can be resolved. I have just run out of solutions and time. As there have not been any responses to this problem here or elsewhere, I have decided I will install the Gutsy release when it is formally available.

---

### Post by curation on 2007-09-17
i don't know if you are still having this problem but I thought it is worth a try as I was able to fix a broken package with gnome-subtitles on another install of Fiesty with this:

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=404876&goto=newpost](http://ubuntuforums.org/showthread.php?t=404876&goto=newpost)

Here is the message that has just been posted:
***************
Given 'package name' is the problem......

Open a console and type in the following:

Code:

sudo gedit /var/lib/dpkg/status

Search through the file for any reference to 'package name' and CAREFULLY delete all of that entry.

Save the file

Code:

sudo apt-get update

***************
I can't test this myself but it worked perfectly!

---

### Post by Hildsvfar on 2007-09-18
my god, thank you!  haha and I thought all hope was lost!

---

### Post by icon_mefisto on 2008-06-11
YES! Editing /var/lib/dpkg/status and removing the sections for the problem packages, fixed apt-get for me. No more "error exit status 139" messages, and everything installs/uninstalls correctly now.

---

