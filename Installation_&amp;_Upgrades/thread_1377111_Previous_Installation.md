---
title: "Previous Installation"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Kayazikyo on 2010-01-09
Hi everyone. 
This is my first post and I sincerely hope it's in the right section... (When I fix this issue and learn more I plan to actually contribute to and help out on these forums.)

I have a Dell Inspiron something from 2005 running windows XP home edition version 2002, 512MB RAM, 160GB harddrive space and a 650GB external drive (not sure if any of this data is needed, but just in case it is, why not include it?)
I have the Ubuntu 9.04 Desktop Edition disk. 

A while ago, I had Ubuntu installed on my machine (alongside windows) and it was fine, and I'm not quite sure what happened, but I ended up having to uninstall Ubuntu and I'm most sure that I tried to uninstall it wrong.
Now, I'm trying to reinstall Ubuntu and every time I go to install it it says it needs to completely uninstall the old installation. So I let the uninstallation run, and it says that access was denied. Then it says "for more information, read..." and it gives me the location of a .log file on my computer. So I go to look for the .log file, and at first I tried looking for it myself, and apparently the folder it's supposed to be in just doesn't exist. Then, I tried to use windows search to find it, and every time I try, it says "an unexpected error occurred."

tl;dr I really want to install Ubuntu but there's a non-working previous installation and I can't uninstall that and my computer won't tell me why...Help?


Thanks!!

---

### Post by raymondh on 2010-01-09
Did you install Ubuntu using wubi?  Better yet, was windows XP running when you loaded the ubuntu disc to install?

If so, here's the [wubiguide]("https://wiki.ubuntu.com/WubiGuide").  Scroll down to the uninstall section.

If not, can you boot into the ubuntu liveCD, select "try ubuntu..." and when the desktop loads, access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

Small L.  Copy/paste the results in your next post.  It'll help visualize your HD.

Regards,

Raymond

---

### Post by Kayazikyo on 2010-01-10
I'm unable to boot from the LiveCD, but I installed using wubi anyways.
So thanks so much for the wubiguide link, I went and downloaded Uninstall-Ubuntu.exe and I restarted fine but then when I try to boot from Ubuntu, it just shows a blank screen....

---

### Post by raymondh on 2010-01-10
> **Kayazikyo said:**
> I'm unable to boot from the LiveCD, but I installed using wubi anyways.
So thanks so much for the wubiguide link, I went and downloaded Uninstall-Ubuntu.exe and I restarted fine but then when I try to boot from Ubuntu, it just shows a blank screen....

From your first post ...

***"I really want to install Ubuntu but there's a non-working previous installation and I can't uninstall that and my computer won't tell me why...Help?"***


Have you been able to uninstall ubuntu already? Did you follow the wubi-guide and if so, what procedure?  It is a 2 step process and you need to be in windows to do this because a wubi-ubuntu 'resides' inside windows.

-  access the add/remove function and remove ubuntu
-  access the boot.ini file and remove the wubi-related line. ONLY THE WUBI-RELATED LINE.

If Ubuntu is already uninstalled/removed,  (as well as the boot.ini file edited to remove the wubi-related line) ... see if you can finally install Ubuntu.


Raymond

---

### Post by Kayazikyo on 2010-01-10
> -  access the boot.ini file and remove the wubi-related line. ONLY THE WUBI-RELATED LINE.
Thank you so much! I'd tried that method before and I wasn't sure which line I was supposed to delete and was afraid I'd mess something up horribly if I deleted the wrong thing, so I tried other things.
I've done both of the things you've said, so I'll try to install again and see what happens.

---

### Post by Kayazikyo on 2010-01-10
> **raymondh said:**
> 
-  access the add/remove function and remove ubuntu
-  access the boot.ini file and remove the wubi-related line. ONLY THE WUBI-RELATED LINE.
So sorry for the trouble, but...
I did both of these things. Several times, with the same results.
After uninstalling and then using wubi to "help me boot from CD" and letting it install the bootloader, when I go to my boot menu Ubuntu shows up and when I go to it, it just shows a blank screen...

---

### Post by raymondh on 2010-01-10
In that "black screen" ... is there anything flashing in the upper right corner?  Any error messages?

*If you are trying to install via the wubi method again, defrag XP (2x if you have the time) and clean it from viruses/malware.

You mentioned that you used to run 9.04 before.  To me that means that your system had the capability/resources to handle 9.04 (graphics, etc, etc).  There must be something else going on different now.

Let's try something different.  Try to boot into the liveCD *(that means restarting / stopping the boot-up process tp get to either QUICK BIOS or BIOS / changing the boot order to boot the CD drive first or ahead of the HD / loading the liveCD / continuing the boot process)* and select TRY UBUNTU (which is known as live session).  Are you able to get to live session? Can you access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

small L.  Copy/paste the results in your next post.  Play around live session and then exit (or close down).

If you are able to boot into liveCD, do you want to consider installing Ubuntu in it's own partition ... and not through wubi which makes it a file "inside windows".

Here is the installation guide for your reference.

[https://help.ubuntu.com/9.04/installation-guide/i386/ch05s01.html#id2668141](https://help.ubuntu.com/9.04/installation-guide/i386/ch05s01.html#id2668141)
[https://help.ubuntu.com/9.04/installation-guide/i386/boot-installer.html](https://help.ubuntu.com/9.04/installation-guide/i386/boot-installer.html)
[https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Here is an [interview with Russo]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/"), the developer of WUBI. Note his response to the second question.

Regards,

Raymond

---

