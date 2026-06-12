---
title: "Karmic fresh install, vuze won't open, gives java error"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by scott.todd on 2009-11-14
I recently upgraded from Jaunty to Karmic, had some hardware issues. Software all worked okay, in particular, vuze was better than before. In order to resolve some of the other issues, I decided to do a fresh install of Karmic, to see if ext4 and grub2 actually improved the performance of my computer. Actually it is even slower than before especially on booting, but that is not my issue...

I installed my usual extras: including ubuntu-restricted-extras and vuze, using "sudo aptitude install ...". While I was waiting for them to finish installing, I was configuring other things, such as the time being updated using an internet server, which of course installed ntp. My best guess is it interrupted the installation with some error: I thought nothing of it and reran the aptitude command.

Now when I open vuze it just aborts. I tried opening it using the terminal, and it gave an error about java. I am unable to figure out how to fix this. I have tried uninstalling the extras, and reinstalling, tried installing different versions of java. Nothing...

Before I go ahead and try to do a fresh install over again, is there ANYTHING else I should try first?

Here is the message that it gives:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0x0119c1c0, pid=4041, tid=3079375728
#
# JRE version: 6.0-b16
# Java VM: OpenJDK Client VM (14.0-b16 mixed mode, sharing linux-x86 )
# Distribution: Ubuntu 9.10, package 6b16-1.6.1-3ubuntu1
# Problematic frame:
# V  [libjvm.so+0x3001c0]
#
# An error report file with more information is saved as:
# /home/scott/hs_err_pid4041.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Aborted

---

### Post by manixdk on 2009-11-22
> **scott.todd said:**
> I recently upgraded from Jaunty to Karmic, had some hardware issues. Software all worked okay, in particular, vuze was better than before. In order to resolve some of the other issues, I decided to do a fresh install of Karmic, to see if ext4 and grub2 actually improved the performance of my computer. Actually it is even slower than before especially on booting, but that is not my issue...

I installed my usual extras: including ubuntu-restricted-extras and vuze, using "sudo aptitude install ...". While I was waiting for them to finish installing, I was configuring other things, such as the time being updated using an internet server, which of course installed ntp. My best guess is it interrupted the installation with some error: I thought nothing of it and reran the aptitude command.

Now when I open vuze it just aborts. I tried opening it using the terminal, and it gave an error about java. I am unable to figure out how to fix this. I have tried uninstalling the extras, and reinstalling, tried installing different versions of java. Nothing...

Before I go ahead and try to do a fresh install over again, is there ANYTHING else I should try first?

Here is the message that it gives:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0x0119c1c0, pid=4041, tid=3079375728
#
# JRE version: 6.0-b16
# Java VM: OpenJDK Client VM (14.0-b16 mixed mode, sharing linux-x86 )
# Distribution: Ubuntu 9.10, package 6b16-1.6.1-3ubuntu1
# Problematic frame:
# V  [libjvm.so+0x3001c0]
#
# An error report file with more information is saved as:
# /home/scott/hs_err_pid4041.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Aborted

I had the same problem. I had to change the JRE so my home banking would work. Now Vuze won't work. Given the choice (Home banking working or Vuze working) I chose home banking :-).

---

### Post by suicidejack on 2009-12-05
I've got the same problem.  It happens in eclipse whenever I try to use a swing object or when I launch netlogo.  Any help on fixing this problem is appreciated!

---

### Post by scott.todd on 2009-12-15
I was able to get it working doing the following:

```
sudo apt-get remove --purge vuze openjdk-6-jre
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install vuze
```

I figured this one out by doing research... but I did get some ideas (none of which worked in my case) from the question I asked here:
[HTML]https://answers.launchpad.net/ubuntu/+source/azureus/+question/90240[/HTML]

---

### Post by lysmihyp on 2009-12-15
Wow, very lovely picture. I will use this cards as my backgroung in my blog.

---

