---
title: "problems with 8.04"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by tobhiyah79 on 2008-08-19
I was installing Ubuntu 8.04. With 6% installation left the computer shut down. After turning it on again and entering my user name and password, a completely blank screen opened, only showing the mouse. Its as if the computer is frozen.  Is there a way to turn on the computer and have it boot the previous version 7.10?

---

### Post by manishtech on 2008-08-20
If you have installed it over 7.10 in the same partition, am sorry to inform you that you are out of luck. Maybe experts may be able to help you out if any such solution occurs, though I don't think such.

I think that your installation was not completed properly, so you are facing the blank screen. Re-install 8.04 properly and try again. 

Incomplete installations are always prone to problems

---

### Post by Kevbert on 2008-08-20
Is the CD burnt by you or not ? If it is did you perform a [[COLOR="Red"]hash check[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") on the ISO file you downloaded ? Did you burn the CD at the slowest speed possible ? (recommended as errors less likely). Have you check the CD integrity via the first menu that's displayed ?
As manishtech says, it looks like you've installed over the top of 7.10.  You can run 7.10 and 8.04 on the same hard disk but in separate partitions.  By default Ubuntu will install on the whole hard disk if you use guided install.  It's better to perform a manual install and use, say, 10Gb for main ext3 partition, mount point as / and swap partition twice your ram size.  Then when you install another version of Linux/Ubuntu you can manually set up a new partition (format and mount the same) but use the same swap partition (no setting up required as it's already there).

---

### Post by yabbadabbadont on 2008-08-20
I don't know why your system shut down, maybe it overheated?

The install will *appear* to hang at 6% while it is copying the deb archives, of the packages to be installed, from the CD/DVD to the hard drive.  If you are using the text mode installer (is there any other?), you can hit Alt-F4 to see a running log of what is being done by the installer.  Hit Alt-F1 to switch back to the installer screen.

---

### Post by manishtech on 2008-08-20
> I don't know why your system shut down, maybe it overheated?
Maybe power problem :confused:

> The install will *appear* to hang at 6% while it is copying the deb archives, of the packages to be installed, from the CD/DVD to the hard drive. 

He said only 6% left,not 6% done......
Yes, some time is taken to copy all the packages in beginning and at last temporarily files and been deleted which also takes time.

> If you are using the text mode installer (is there any other?), you can hit Alt-F4 to see a running log of what is being done by the installer. Hit Alt-F1 to switch back to the installer screen.
Thanks a ton for this neat tip. :) I didnt knew this.

---

### Post by yabbadabbadont on 2008-08-20
> **manishtech said:**
> He said only 6% left,not 6% done......
Yes, some time is taken to copy all the packages in beginning and at last temporarily files and been deleted which also takes time.

Oops...  I missed that.  (obviously :lol:)  I noticed that it seemed to sit there for quite a while at the end too.  It didn't really show anything in the log session on tty4 either.  Makes sense that it might take a while to clean up all the temp stuff.

I'm glad that I was at least able to offer some useful information, even it if didn't address the OP's problem.  :)

---

### Post by manishtech on 2008-08-21
> **yabbadabbadont said:**
> Oops...  I missed that.  (obviously :lol:)  I noticed that it seemed to sit there for quite a while at the end too.  It didn't really show anything in the log session on tty4 either.  Makes sense that it might take a while to clean up all the temp stuff.

I'm glad that I was at least able to offer some useful information, even it if didn't address the OP's problem.  :)
I know about the tty's but never knew that tty4 shows the log of the installation. Thanks again :)

---

