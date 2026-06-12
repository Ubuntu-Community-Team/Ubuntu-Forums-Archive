---
title: "Dimension 8400 unable to boot after install"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Face-One on 2007-02-09
Hi,

Iam a new user in the Linux World. With the help of a friend we tried to install Ubuntu 6.10 from a DVD. I made sure the MD5 sums where correct with hkSFV

But somekind of problem that I can't indentifi accured. And just after you reboot the system it completly looks up. I can not access a text or GUI terminal.

Here you can read about what kind of computer I have. 

Dell Dimension 8400
3.6 GHz Pentium 4 Processor 550 w/HT 800 FSB
2GB Dual Channel DDR2 SDRAM at 533MHz
256MB PCI Express x16 ATI Radeon X850
Intel 82801 FR SATA RAID CONTROLLER
2 x 160GB Serial ATA Hard Drive In Raid 0
12x DVD+RW/+R w/ double layer write capability Hitachi/LG
16x Allround DVD Player

---

### Post by Face-One on 2007-02-17
Could someone please help me with this? Give me a hint what is wrong? I have been reading about that my ATI card might be the fault. 

But being so new to this I have no idea how to make this work.

---

### Post by eapache on 2007-02-17
did you install using the 'alternate installer' or using the regular liveCD/liveDVD method? If you installed using the alternate installer, your graphics card is probably the problem. If not, I don't really know.

If you installed using the alternate installer, follow these instructions to boot from the liveCD (I got them from aberry555):

> This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

This will get you into the gui. Now go into the /etc/X11/xorg.conf file on your hard-drive (you may have to mount it first), and make the same changes. Good luck.

---

