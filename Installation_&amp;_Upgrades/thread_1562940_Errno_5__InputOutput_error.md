---
title: "Errno 5 : Input/Output error"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by Kyrie1337 on 2010-08-28
I am trying to install v 10.04.1 and it works up till 34% and then it gives me that error. So annoying and i don't have any other OS's.

I am posting this from a bootable 9.10 CD which doesnt even partition right.

Please help

PS : I have a 64 bit CPU but i downloaded 32 bit ubuntu. Is that a problem?

Thanks

---

### Post by Kyrie1337 on 2010-08-28
Its only on 10.04. 9.04 doesn't partition.

---

### Post by Kyrie1337 on 2010-08-28
now just tryingto get partition to work ;\

---

### Post by Kyrie1337 on 2010-08-28
Bump please.

---

### Post by Microsoft Hater on 2010-08-28
Hey, I'm having the same problem.

Try these out: [http://ubuntuforums.org/showthread.php?t=1545792](http://ubuntuforums.org/showthread.php?t=1545792)

They haven't worked for me, but they're the first things to try and seem to have helped some people through this error.

Cheers

---

### Post by Kyrie1337 on 2010-08-28
Uh, that isn't the right thread. there are no answers there.

---

### Post by Microsoft Hater on 2010-09-04
Check out [http://ubuntuforums.org/showthread.php?p=9807537#post9807537](http://ubuntuforums.org/showthread.php?p=9807537#post9807537) if you are still having errno 5 problems.

---

### Post by MartinLF on 2010-09-15
I was getting the error message [Errno 5] Input/output error when trying to install 8.10.  Twice I got this, once at 51% complete and once at over 60% complete.  Both times while copying files.

This is how I fixed it and got the install to work:

In the partitioner part of the installer, while doing a manual install, I checked the checkbox for reformat for the EXT3 partition which is the partition which I created for my Ubuntu installation.  I also edited the partition and made sure that EXT3 Journaling Filesystem was selected for the partition as well as the mount point was set to /.

I continued the installation process and this time it went to completion.  I now have a dual boot with XP on the machine.  I did not have to burn another CD at a slower speed, I did not have to swap my CD drive, or do any of the other things in the posts that people suggested.

I don't know if this will work for you, but it is a simple thing to do before trying other things.

---

### Post by jimbo99 on 2010-09-15
Most of the time you get those errors there's a problem with the HDD or the DVD/CDROM or even the CD/DVD reader drive.

As far as the CD/DVD drive goes try burning the CD at a slower speed.

Even though it occurs during the install and yet you are able to boot from it to post your question, it still doesn't rule out the CD/DVD drive nor the platter you burned.

There's a program called gsmartcontrol that you can install (even on the Live CD though you'll loose it when you reboot) that does a pretty spectacular job of testing the HDD for problems.  Try installing that (there are .deb files that you can download so you don't need a repository added).

Always test your hardware first and when you assume it isn't the hardware then you make an **** out of you and guess who.

If the HDD pans out and you have burned the iso at a slower speed onto the CD/DVD blank, then there could be something else wrong with the hardware in the system.  Check your RAM as an extra measure.

Test hardware first any time you have an issue even if only a couple weeks have passed since you were successful.  I know, as I repair computers for a living.  I use that gsmartcontrol to test the drives of units that come into my shop.  Windows, Mac, Linux, everything.

---

### Post by krishnandu.sarkar on 2010-09-15
I've faced this problem too. In my case it was faulty RAM. Check your RAM with memtest86+ bundled with Ubuntu Live CD or it also may be faulty media. Try burning in 8x

---

### Post by dmp2010 on 2010-09-17
I had similar problem when I was trying to install Ubuntu 10.04. I download the file 2/3 time and burnt the CD and same problem. A co-worker gave my a CD which worked fine. So, in my case, the CDs that I had made didn't work for some reason.

---

### Post by norcal on 2010-10-05
i just set up a dual boot windows 7 and 10.04. i had this frustrating problem until i used the alternate cd. it worked for me.

---

