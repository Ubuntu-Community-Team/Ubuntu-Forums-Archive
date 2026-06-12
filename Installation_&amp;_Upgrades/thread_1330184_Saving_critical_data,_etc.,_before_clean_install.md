---
title: "Saving critical data, etc., before clean install"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2009-11-18
I have a working 9.10 created by upgrading from 9.04.
I want to do a clean install of 9.10.
What do I need to save (on an external hard disk) from my upgraded system and then restore when 9.10 is newly installed?

E.g. I had to make changes in various folders/files to get my scanner and printer working. I have installed additional software such Truecrypt, etc., and also VirtualBox where I have a minimal XP runnable as a guest.

I've already saved my home folder as that contains my personal files, etc.

My system is dual boot XP and 9.10 and I understand that GRUB will have been replaced by GRUB 2 after the new install of 9.10. 
What will I need to do re GRUB 2 to ensure that I can still dual boot XP and 9.10? (My aim is to eventually only boot 9.10, recover the disk space used by XP and only run XP as a Virtual Box guest)

---

### Post by dstew on 2009-11-18
Generally, it is hard to back up installed software because the software will use pieces that are scattered throughout the system. For example, there might be initialization scripts in /etc/init.d, configuration files in your home folder, and binary files in /usr or other places. If you had to change folder names, and permissions, it is even more difficult.

Usually, when you do a clean install, you need to re-install your programs. If you do a clean install, grub 2 (or, grub version 1.97 -- same thing) will be installed by default. It should detect your other operating system and you should be able to dual boot no problem.

---

### Post by raymondh on 2009-11-18
In jaunty and Hardy ....

..... I have used [aptonCD]("http://aptoncd.sourceforge.net/") to back-up and restore my apps and its' dependencies whenever I needed to fresh-install .... mostly in jaunty.  _Note that I have not tried aptonCD in Karmic_.

Dstew is right about initial and binary files and possible difficulties if permissions are changed.

If you have 9.10 working, why clean-install?  If your end-goal is to sole-boot, why not just work on that without the need for a fresh install.  Just a thought/question.

Regards,

---

### Post by welshmike on 2009-11-18
dstew

Thanks for the advice.

Arghh! that is a pain . I knew that MS Windows re-install (I've needed to do that about once a year to restore performance) requires re-install of all applications and has the additional mess of DLLs and foul up of the registry.

I was hoping that Ubuntu was not as honerous.

So I'll stick with my 9.10 upgrade rather than install new.

I've just got to change my system to overcome the following annoyance I created:
[http://ubuntuforums.org/showthread.php?t=1328122](http://ubuntuforums.org/showthread.php?t=1328122)

I must say that when I switch from using Ubuntu to using Windows XP I've now found the latter frustratingly slow compared with Ubuntu 9.10.

---

### Post by welshmike on 2009-11-18
> **raymondhenson said:**
> 

If you have 9.10 working, why clean-install?  If your end-goal is to sole-boot, why not just work on that without the need for a fresh install.  Just a thought/question.

Regards,

raymondhenson

You are right that sole-boot should be my first priority.

Thanks

---

### Post by audiomick on 2009-11-18
I think this thread:
[http://ubuntuforums.org/showthread.php?t=1300029](http://ubuntuforums.org/showthread.php?t=1300029)
Is dealing with the same topic

---

### Post by raymondh on 2009-11-18
> **welshmike said:**
> dstew

Thanks for the advice.

Arghh! that is a pain . I knew that MS Windows re-install (I've needed to do that about once a year to restore performance) requires re-install of all applications and has the additional mess of DLLs and foul up of the registry.

I was hoping that Ubuntu was not as honerous.



Just my thoughts.  The flexibility and power of linux allows us operators to tweak the system as we see fit. Sometimes, it is a necessity because of system incompatibilities. The downside is that most "re-installs" can happen because of operator-error.  So many times in jaunty have I had to re-install because I became to aggressive in tweaking a working install :)

That said, and once you have your karmic settled down, now's a good time to consider a back-up plan.  I use RSYNC in conjunction with GRSYN (the GUI) which are both in the repos.  I also clone my HD/Partitions using [PING]("http://ping.windowsdream.com/") and have it saved in the HD (like a built-in recovery partition) and elsewhere (just in case).

Happy ubuntu-ing :)

---

### Post by raymondh on 2009-11-18
> **audiomick said:**
> I think this thread:
[http://ubuntuforums.org/showthread.php?t=1300029](http://ubuntuforums.org/showthread.php?t=1300029)
Is dealing with the same topic

Herman's script works well.

---

### Post by welshmike on 2009-11-18
> **raymondhenson said:**
> 

That said, and once you have your karmic settled down, now's a good time to consider a back-up plan

I too have screwed up my system badly by trying various Linux distros.
Fortunately I had used Acronis True Image to backup my internal hard drive and was able to restore from that. In fact before I upgraded from Ubuntu 9.04 to 9.10 I took a true image backup just in case. I didn't need the backup because the upgrade to 9.10 went without any real problems, just
[http://ubuntuforums.org/showthread.php?p=8225815#post8225815](http://ubuntuforums.org/showthread.php?p=8225815#post8225815)

Because 9.04 froze at random times and I hadn't had a fix I was still dependant on Windows XP but with 9.10 and the various automatic updates I've had no such problems with 9.10 and it is now my "production" system.

Thank you Ubuntu development team.

---

