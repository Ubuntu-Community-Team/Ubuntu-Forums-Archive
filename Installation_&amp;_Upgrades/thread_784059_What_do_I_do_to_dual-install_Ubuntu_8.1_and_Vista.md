---
title: "What do I do to dual-install Ubuntu 8.1 and Vista?"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Mulenmar on 2008-05-06
Well, I can't give up Vista, or at least XP SP2, without losing my ability to play Halo and Elder Scrolls 3. (No internet, hard to get all the packages for Wine )

But I've been using Ubuntu and Xubuntu on several of my older computers, and I want to give it a try on my newest computer -- which even Vista runs quickly on.  I know about roughly how to partition for Ubuntu.

Here's the question: How do I install Ubuntu 8.1 without destroying my ability to boot Windows Vista?

Windows Vista came pre-installed on my machine, and although I made the HP backup DVDs when I got the computer, I DO NOT have the ordinary Windows Vista installation CD. If this ruins Vista, I'm SOL.

Thx!

EDIT: I can't check to see if this works until this afternoon, but does this look like it would work?

[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by Mulenmar on 2008-05-06
Hello? Somebody please answer!:(

---

### Post by Mze on 2008-05-06
A [link]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") very well recommended

Did you run a search on the forums?
This question has been answered more than 500 times on this forum.

---

### Post by confused57 on 2008-05-06
You can use Vista's bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

You'll need to install grub to Ubuntu's root partition, by clicking on the "Advanced" button in the lower right and entering your root partition ,e.g. /dev/sda2(or however the installer/partitioner recognizes your root partition) in place of the default (hd0), which is the mbr.

Burn a copy of Super Grub Disk before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by fixitdude on 2008-05-06
Don't forget that you can run a lot of windoze programs with linux on something like wine. You only run the programs you can't find a duplicate for under linux, and that list is getting smaller every day.

Push a button and REBOOT, reboot, reboot windoze every hour (like normal) while still browsing on linux!!!!

Plus, I am sure you can install windoze new on something like VMWare and save the HD file image (since it's really only a binary file under linux) so you can easily go back to a new install (like you have to do every few months anyway).

Others:

Wine - FREE!!!!!! Already part of ubuntu
[http://www.winehq.org/](http://www.winehq.org/)

VMWare - has a free version and a pay for one.
[http://www.vmware.com/](http://www.vmware.com/)
[http://en.wikipedia.org/wiki/VMware](http://en.wikipedia.org/wiki/VMware)

Parallels - $50
[http://www.parallels.com/](http://www.parallels.com/)
[http://en.wikipedia.org/wiki/Parallels%2C_Inc](http://en.wikipedia.org/wiki/Parallels%2C_Inc).

Sun xVM VirtualBox is an X86 virtualization software package
sun.com

---

### Post by Rallg on 2008-05-06
I do dual-boot from a USB stick. The hard drive MBR is unaltered from its original Vista installations (meaning that without the USB inserted and selected at boot time, the computer boots directly to Vista without seeing GRUB).

If your computer can boot from USB (not all can), you need to create a bootable USB stick, use Grub4DOS, and modify its menu.lst to recognize your boot options. All these techniques are described on the Internet, so you can search for them. The one trick is that with Grub4DOS on the USB, it will think the USB is hd0 and that your hard drive is hd1.

---

### Post by Mulenmar on 2008-05-07
I didn't know Vista's loader could already run Ubuntu...so I just installed GRUB over it. There are two entries for Vista, but everything works fine. Now, I just have to install all the
mp3 plugins.

And I DID run a search, of the entire ubuntu forums. Nothing helpful turned up. But, I figured it out.

Like I said, it would be a major chore to download Wine and everything I need for it, as I don't have internet on that computer. Thanks for the links, though! I'll look them.:KS

---

