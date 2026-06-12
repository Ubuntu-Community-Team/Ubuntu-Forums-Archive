---
title: "Unable To Find A Medium Containing A Live File System"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by RogerMon on 2012-08-04
Hello,

I found similar issues in other threads, but no one has respondind, so I'll start a new thread:

I'm an experienced Windows developer, but a Linux neophyte.  I've tried to install Ubuntu desktop on my workstation from a dvd, which results in the above error.  My hardware is a Dell XPS-9100 high-end workstation. The OS is Win 7.  My option was to install alongside Windows.  I formatted part of the second hard drive for Ubuntu.  It seems that the kernel can't find the root file system on the second drive.  I've not been able to find a way to address this.

I'll appreciate all help.

Thanks,

Roger

---

### Post by oldfred on 2012-08-04
Is this booting DVD or after the install. It sound like the DVD may not be correct?

Some have issues with CD or DVD and burning quality. Some have a bad download. I prefer USB as it installs a bit faster. You can check download with md5sum.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If installing to a second physical drive, it is not install along side. But Windows confuses drives and partitions, calling both 'drives'. If you created partitions with Windows you may have converted to dynamic partitions which will not work with Linux and some Windows repair tools.

---

### Post by RogerMon on 2012-08-04
Hi,

Thanks for the quick reply!  this happens after the install at start up.

I DLd the code from the website. The Roxio software didn't report any problems.

I'll look at the links you listed.

Roger:)

---

### Post by oldfred on 2012-08-04
If it is after the install, it is often a video issue. Since they changed video to in the kernel I have had to use nomodeset on first boot until I install nVidia's driver. Works for others also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you do not get grub menu, you have to hold shift down from BIOS until menu appears.

---

### Post by RogerMon on 2012-08-04
Hi Again,

Okay, we are on the right track.  It is a video problem.  This is being typed from Chrome in Ubuntu!

I experimented with Grub, and initially, couldn't find the menu shown in the NoModeSet article.  After a couple more restarts (How do you restart?  It doesn't recognize shutdown) I did find the menu mentioned, added the nomodeset command to the file for a temporary boot, and that's where I am now,

I have dual monitors.  I'd be okay with one monitor, but it is on the wrong one.  I want it to be one the right-side monitor (I'm getting a stiff neck :))

So, now how can I tweak the video and monitors?  Is dual-monitors an option with Ubuntu?

Thanks for your help,

Roger

---

### Post by oldfred on 2012-08-04
I do not know about dual monitors. If you need help on that a new thread with that in the title may help get attention of those who know more. I have seen several threads in forum.

What video card?

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=dual+monitor&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=dual+monitor&sa=Search)

---

