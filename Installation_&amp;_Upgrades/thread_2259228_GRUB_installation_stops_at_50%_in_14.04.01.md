---
title: "GRUB installation stops at 50% in 14.04.01"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by RLerner on 2015-01-03
Hello All,

I have a rebadged Dell Poweredge R510 that I have been struggling to get Ubuntu Server 14.04.01 x64 onto. These servers come with a SATADOM token, or a small 8GB SSD used for preinstallation of software.

I have an image that I have used on many systems, and have checked using the menu for defects.

I** have not** been able to complete installation of Ubuntu on this box. Either the system restarts randomly, or when I get far enough, the GRUB2 installation hangs at exactly 50%, and then I get a "grub-install /dev/sda failed" error.

While the device has a backplane and some sort of software based RAID controller, I had similar results whether I used the front-loading bays, or attached SATA right to the board.

This noted, I added a SATA DVD-RW drive to the system so I could try even Ubuntu Desktop 14.04.01 live boot, which failed in both install and restart.

I then decided I would try to install Windows 7 to see how far it would get. It installed all the way and runs fine. This is unacceptable. I don't want Windows. Windows doesn't want me. I told Windows that a while ago but it keeps trying to talk to me.

Anyway, I'm curious if anybody has experienced this issue before, and could explain to me why Windows and Ubuntu would work differently in this way (writing the MBR perhaps?)

I'm also looking for a solution, and instead of waiting for all the files to copy each time I try the install, is there a way to make it jump right to the GRUB step just to see if that would pass?

I also tried LILO, though I've never used that so I had no idea what it would do. It just restarted the server.

I have a few 1 TB drives I'm using for this, but only one installed in the system at any given time.

Thanks for the help.

---

### Post by RLerner on 2015-01-04
[IMG]http://makeameme.org/media/created/I-got-a-0zubv6.jpg[/IMG]

---

### Post by yancek on 2015-01-04
> I'm also looking for a solution, and instead of waiting for all the  files to copy each time I try the install, is there a way to make it  jump right to the GRUB step just to see if that would pass?

Yes there is.  Take a look at the link below.  Scroll down to Fixing a Broken System and the option for "vie the Live CD Terminal".  The problem with that is it doesn't create a grub menu, the grub.cfg file so you won't be able to boot unless you manually create your own which you should be able to find by googling grub.cfg sample or template.  At least you would find out if Grub installs.  I'm not familiar with your hardware and don't use RAID so I doubt I'll be of any help if this doesn't work.

---

