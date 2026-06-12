---
title: "Dell Latitude 3550: Cannot boot from hard disk after booting from usb key!"
date: 2015-12-31
forum: Installation &amp; Upgrades
---

### Post by konstant@mail.ntua.gr on 2015-12-31
I had installed Ubuntu 14.04 on my Dell Latitude 3550. I worked with it with almost no problems for a week. Due to a [problem with the touchpad]("http://en.community.dell.com/support-forums/software-os/f/3525/t/19665328") , I tried ubuntu 15.10 by booting from a usb stick. After that, I could not boot from the hard disk anymore. The laptop enters into system checking mode and reports that no bootable medium is found. I tried to [repeat the steps from this page]("http://www.dell.com/support/article/no/no/nobsdt1/SLN297060/en")  in order to (re)create a boot option but this had no effect. All grub files (grubx64.efi,grub.cfg,MokManager.efi,shimx64.efi) were accessible from the BIOS in order to create the relevant boot option (of course I was choosing grubx64.efi according to the instructions) . 

I had to install the system from the beginning (now ubuntu 15.10 it is...) in order to be able to use the laptop. I need to find what the problem is, since I will always be afraid to boot the laptop from a USB medium. 
(e.g. is it only for ubuntu 14.04 or also for 15.10, if I can do something from the BIOS or correct something in /boot using ubuntu booted from usb etc)

Bear in mind that I cannot do any tests, since my laptop is up and running (takes more than half a day to bring it to this state with all my files and software!) and I cannot risk loosing everything again.

---

### Post by grahammechanical on 2015-12-31
First, Please do not use an email address as a user name. You will get spammed.

Second, only you know what you did when running that 15:10 live session. The problem was caused by something you did.

I have run many live sessions. Sometimes, it is to fix things. Sometimes it is to test a new release of Ubuntu. Sometimes it is to change the partition layout. I can tell you this: Running a live (Try) session and then exiting the session will not automatically remove any OS that is installed on the hard disk or remove the boot loader. And those are of the two possible causes of getting a "no boot able medium" message.

 But the live session, like the installed desktop session, does put power in our hands and with that power we, the user, can do things to mess up the OS. I speak from experience.

Regards

---

### Post by oldfred on 2015-12-31
Please post a user name change request here. Review "sticky" threads on requirements for a name change.
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

Best to see details, but do not run autofix unless someone has reviewed your configuration, Boot-Repair usually works, but autofix sometimes does make it worse where advanced mode would fix it:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by dcsoldschool53 on 2016-01-01
I had did the same thing once or twice myself. What happen was, you had install the operating system on the usb, instead of putting the livecd .iso file on it. When you had ran that operating system from the usb, it had created two different file from the two operating system on the laptop. The vmlinuz, initrd, and some other files too, were put on the laptop, in short, your laptop didn't know which files to use. This is why it didn't boot.

  If you had created a dedicated grub partition, and created a menu there it may have worked for you. I hope this helps

---

### Post by konstant@mail.ntua.gr on 2016-01-02
There is no problem with the OS, the data on disk, incl the /boot dir looks fine (as seen from the booted Ubuntu from the USB). dcsoldschool53 below gives an interesting hint, but I can't afford to try it since I need my system running. As for my username, I am not allowed to change it (<10 posts) - but I am not afraid of spam either! 

Thanks for the help anyway...

---

### Post by dcsoldschool53 on 2016-01-02
No I meant the OS on the laptop got corrupted. The USB OS will always be fine, and with out corruption.
Also, get yourself an external hard drive to back your DATA up, just encase some thing like this happens again.

---

### Post by oldfred on 2016-01-03
You cannot change your own user name even with lots of posts, only edit your data.
You have to request an Admin to change user name as it is tied to your login.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I do have high speed Internet, and after downloading ISO & partitioning in advance can install in 10 Minutes. And add in applications & copy configurations back relatively quickly, so in less than an hour can have a new install.

      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

