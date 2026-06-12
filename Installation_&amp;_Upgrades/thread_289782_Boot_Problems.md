---
title: "Boot Problems"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2006-10-31
I posted earlier about the "missing operating system" message I was getting while trying to install Ubuntu.  My problem was / is related to the fact I'm trying to boot to either XP (located on a RAID drive) or Ubuntu by specifying the boot drive in my BIOS.  When I'd specify booting to the Ubuntu drive, Ubuntu would install but when I'd reboot I'd get the "missing operating system" message.  On top of that, Ubuntu would mess up the MBR of the XP drive.

If you're interested in the particulars, you can read the other post [here.]("http://www.ubuntuforums.org/showthread.php?t=288150").

I tried disconnecting all the other drives on my system to get Ubuntu installed.  It worked fine and I got to have a quick look at the system, which is nice.

However (and as you'd probably expect), when I reconnected my other drives, Ubuntu would no longer boot.  I briefly get the graphical boot screen, then the system is stopped and I get a message something like the following (sorry, I'm not where I can access the installation now and don't have access to my notes):

/dev/sh: Couldn't load tty; Using shell instead.

Sorry, that's the gist of the message.

Anyway, I read in a post related to dual booting with XP that you can edit a file called "linux.bin", which you can use to specify the location of various hard drives.  I thought I might be able to point Ubuntu to the correct location for it to boot.

Anyone have that info or other info that might help?

---

