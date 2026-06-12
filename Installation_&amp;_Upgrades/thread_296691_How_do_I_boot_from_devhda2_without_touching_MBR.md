---
title: "How do I boot from /dev/hda2 without touching MBR?"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by dustin_wielenga32 on 2006-11-10
I recently bought a Toshiba laptop, and tried Ubuntu on it.  I was amazed to see that it set the resolution correctly (widescreen), and it also recognizes the wireless network card without any intervention by me!  I used Slax before, and with that I need to use Ndiswrapper and all, so this was an awesome surprise.

So, I would like to install the newest version (Edgy I think?) to my laptop.  I think I should be able to figure out how to install, I've installed other distros before on other comps, and this one's supposed to be beginner-friendly, so that shouldn't be a problem.

My question is, as the title states, how can I boot Ubuntu from the second partition on my laptop without messing with the MBR?  Can I boot from the CD, and then select an option on the CD to boot from hard drive?  Or could I put something on a USB thumbdrive, boot from that, and have that point to /dev/hda2?

Any suggestions would be much appreciated.

Thank you very much to those who have developed Ubuntu, I think this time my switch to Linux will be real!

---

### Post by confused57 on 2006-11-10
I assume you have Windows installed on the first partition of your hard drive and don't want to install grub to the mbr.
  Using the alternate install cd, you can select where to install grub...here is a thread selecting to install to floppy:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

  I don't know if you have the USB flash connected during install, that you can opt to install grub to the flash drive or not?  There may be someone who has actually done this that can help you.

  The desktop live cd automatically installs grub to the mbr.

It's possible you could install grub to the root partition of Ubuntu, then use the Super Grub Disk to boot Ubuntu:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

See the link toward the bottom of the page for SGD...

---

### Post by Herman on 2006-11-10
In some models of Toshiba laptops, there is an 'Express Media Player', which is thought to cause problems with Grub, so you may be correct to not want to install Grub to MBR in this case.

I agree with what confused57 advised in the above post.

 I would also like to add that you can easlily install '**[WinGrub]("http://grub4dos.sourceforge.net/")**', which I am testing at the moment and like very much.

WinGrub is an easy click-to-install program for Windows that is quite easy to use. I am still testing it, and it seems that it automatically loads the 'stage2' of the /boot/grub directory of the Linux partition. I have a multi-boot set-up and I tried deleting my entire /boot/grub directory in /dev/hda2 just to see what WinGrub would do, and it automatically went to my /dev/hda6 /boot/grub/stage2 and brought up the grub menu in that install. That means WinGrub is very reliable, even for people who do not really know what they are doing.

Wingrub is booted from Windows by adding a line in the Windows boot.ini file to 'Start Grub'. To see what I mean by the boot.ini file, [click here]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP"). Most people would want to edit it from Windows' side though, especially if your Windows is on NTFS. 
I added the following line to my boot.ini file,
```
C:\GRLDR="Start Grub"
```note: do not leave any blank lines in boot.ini, but place that line immediately underneath the existing text in your boot.ini file.
That means you will get a Windows boot menu, and you can select either Windows or 'Start Grub' when booting up. If you select 'Start Grub', you will get your Grub Menu from your next Linux partition.

The only problem I encountered was that WinGrub cannot handle our 'savedefault' command which we use in our menu.lst boot entries in Ubuntu. In the situation where you are booting with WinGrub, you can safely dispense with the 'savedefault' commands in menu.lst, and just hash them out, or delete them from the menu. They won't be useful for anything when we are booting from WinGrub anyway.

I think WinGrub is a great solution for anyone who wants to dual boot and for some reason can't use the regular Gnu/Linux Grub by itself.

Regards, Herman :D

---

### Post by dustin_wielenga32 on 2006-11-10
Thank you for your advice.  I did get it to work, in the end I used a guide that I found on LinuxDevCenter.com, so I installed Grub to second partition, and then edited the Windows boot.ini to give the option to boot from that.

If anybody else is interested, here is the link:
[http://www.linuxdevcenter.com/lpt/a/6554](http://www.linuxdevcenter.com/lpt/a/6554)

The only part of this guide I used was the section titled: "Installing GRUB and Making Ubuntu Bootable Using the Windows Bootloader."  Hope that helps someone out.

Thanks again for your advice folks, and thanks Hermen for warning me about the Express Media issue.

---

