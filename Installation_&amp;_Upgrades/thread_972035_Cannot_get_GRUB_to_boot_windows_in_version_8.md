---
title: "Cannot get GRUB to boot windows in version 8"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Bondy_uk on 2008-11-05
Hi everyone,

I really don't understand whats going on here and whether I should report a bug or not.

Basically, I decided to wipe my Gutsy install and start fresh with Hardy. Only that when I did GRUB would not load Windows at all. The install didnt even find Windows when it asks about copying settings etc across.

Its been 2 days and ive done everything I could think of and find on the net... reinstalling GRUB via terminal [root (hd0,4) / setup (hd0) / etc], using the CD method (selecting manual install etc), editing the menu.lst to various different formats, tried using alternative bootloaders, LinuxRescueCD, etc etc.

The closest I got was it finally would say its loading, then just sit there and do nothing at all. I could only ever have a system that would boot into Windows or boot into Ubuntu, but never be working to boot both.


Anyway, I just got fed up with it, wiped Hardy off and installed Gutsy (7.10). The install found Windows straight away for copying settings and configured GRUB to boot both Ubuntu and Windows perfectly.

So this has me really confused... what has been changed in version 8 to cause so much trouble?

---

### Post by dstew on 2008-11-05
My guess is that the installer program is not configuring grub properly. The installer program is not grub itself. It looks for other operating systems, and attempts to create the proper grub menu, and install grub on the proper disk in the MBR in the proper way. The installer makes some assumptions about which disk will be first in BIOS, and sometimes it is in error. Or, it does not recognize your Windows system.

I can't say exactly why the installer failed, but you can get around it by installing grub manually, and editing your /boot/grub/menu.lst manually. 

To do it perfectly, you need a [grub boot floppy]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html"). The reason for this is that it allows you to install grub in its **native** state, without any operating system present. If you install grub from the Live CD, you are not running native grub but the grub *shell* program, which runs under Linux. If your Linux system guesses wrong about the BIOS disk order, and installs the grub booter wrong, then the grub boot loader will fail. This is the same reason the installer fails.

If you choose to install using native grub from a boot floppy, the technique is the same as from the grub shell, which you already tried. The one advantage is that you are installing grub in the same state as it will boot from, so whatever disk is (hd0) during the install will be (hd0) during the boot.

---

### Post by Bondy_uk on 2008-11-05
Thanks for the info.

Im so mad with Intel's assumption that you dont need a floppy drive anymore, its caused me no end of trouble (my Intel branded motherboard does not have a floppy connector! ffs).

Im getting so angry at this stupid install at the moment. The Gutsy install was a fluke, I was customizing my setup and screwed it up, so thought 'thats fine, I know it works so I will just wipe it and start again'... BIG mistake.

Must have tried to install 20 times by now, both Gutsy & Hardy, yet now cant boot into either Linux or stupid Winblows. That Super Grub didn't work either.

Even if its a fresh install, or ive done the same steps, ive come out with errors 12, 13, 15, a frozen screen saying 'starting' and a blank screen with 'No Operating System Installed'


I thought Ubuntu was supposed to be easy! :confused:

---

### Post by Bondy_uk on 2008-11-05
> **dstew said:**
> and editing your /boot/grub/menu.lst manually. 


Rereading your reply made me remember something else strange...

I checked which drive was which, edited menu.lst to reflect this (and got Ubuntu working). After I reset the PC the drive had switched around! (hd0/hd1). So I restarted again to make sure Grub was still working and yep, loaded perfectly... but they had switched back over AGAIN??!

I repeated this a few times and it kept doing it. But what I dont understand, is that if it thinks HD0 is HD1 one time, then back to HD0, how come it ALWAYS booted into linux with root as HD(0,1) ?

I just dont understand, there is something really strange going on. I have never had this much trouble with installing any distro before, even when I remember back and every distro I used would install lilo :confused:

*EDIT*
Wow, I just realised how long ago that was!
The days before Redhat broke off and released Fedora (thats when I stopped using it).
When in Susie it would load into a CDI and I had to type 'init x' to bring up the GUI.
Oh and when Mandrake was the big craze for Windows users to convert. I remember the little program they had pre-installed that would copy all your windows fonts etc across with one click, rather than using xterm... now that was a big hit! lol.

Come to think of it, I really should know a lot more about linux than I do 8-[

---

### Post by dstew on 2008-11-06
> Im so mad with Intel's assumption that you dont need a floppy drive anymore, its caused me no end of troubleYou can make a [native-grub bootable CD-ROM]("http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM") too. Consider it if you want to really get a grip on your problem.

With the switching of (hd0) and (hd1), that is weird, but I think it is possible. If you are running native grub (that is, just booting, and no Linux running yet) and the designations are changing, that is a BIOS issue. It is possible that some advanced "feature" of your BIOS is guessing that you want the other disk booted next time, etc, so the drive order is changing. Does it always boot though, no matter which drive it wants to use for the kernel in menu.lst? In other words, is the grub boot loader in the MBR of a disk that gets booted consistently? And then, the problem is booting the kernel from menu.lst? Is it that grub boots, you get the grub menu, but then the wrong disk is selected for the Linux kernel?

---

