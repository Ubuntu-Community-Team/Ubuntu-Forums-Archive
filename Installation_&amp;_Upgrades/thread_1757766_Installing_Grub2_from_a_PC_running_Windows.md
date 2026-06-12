---
title: "Installing Grub2 from a PC running Windows"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by c.cobb on 2011-05-13
In short, what I'd like to find is a workaround to install Grub2 onto a USB stick, from a PC running Windows, without using a GUI. 


After searching, I don't find any way to install Grub2 from Windows.  I do have a nice little MS-DOS batch file that installs syslinux onto a USB stick. It's simple, fairly fool-proof, and I'd like to convert it to install Grub2.

Did find an example of [running grub-install without actually installing]("http://en.gentoo-wiki.com/wiki/Grub2#Chainloading_to_GRUB2") anything:

    grub-install --grub-setup=/bin/true /dev/sda

So, IFAIKT, this just creates the Grub2 'boot.img' file, and maybe also modifies the 'core.img' file? Is that right? If so, then a little DOS utility to write a USB's MBR using the boot.img should work, yes? 

However, I notice the boot.img file is 512 bytes. As I understand it, a drive's partition table is included in that space. 

I'd like to take that boot.img and use it to install Grub2 on any arbitrary USB stick, without altering the existing partition table.  If I snip off the last 72 bytes so the image is only 440 bytes, it seems like this should work (assuming that every USB stick will have Grub2 installed in the /boot/grub subdirectory).


If this sounds right, is there a DOS-based MBR update utility that you would recommend? I find several, such as MBRUtility, MBRWizard, and MBRFix, among others. 

Thoughts? Thanks!

---

### Post by dabl on 2011-05-13
Is there some reason you can't boot a Live CD for the 3 minutes it would take to install Grub to the USB stick?

---

### Post by 73ckn797 on 2011-05-13
> **dabl said:**
> Is there some reason you can't boot a Live CD for the 3 minutes it would take to install Grub to the USB stick?

Sounds like this would be the easy way to do it.

---

### Post by c.cobb on 2011-05-14
> **dabl said:**
> Is there some reason you can't boot a Live CD for the 3 minutes it would take to install Grub to the USB stick?
Yes, the reason being that I won't be doing the setup. I'm trying to create a nearly fool-proof, Windows-based, easy for the user to follow, never used Unix, and don't even understand much about Windows solution. 

I have that now for syslinux, but it won't allow booting directly from an ISO file, and unpacking an ISO onto USB is an unnecessary complexity any more. I was distributing a zip file with Puppy Linux, and that worked okay as it was fairly small. But even then, a verbose, multi-dialog-window process is necessary to connect to the network which, apparently, is too inconvenient/complex for most people. Using Ubuntu would eliminate this step, and it looks and feels much nicer, and more familiar. 

Is there any technical reason I can't make this drop-dead simple? In a world where anything more than copy this file, and then "double click it" is considered complex?
Thanks!

---

### Post by c.cobb on 2011-05-15
> **c.cobb said:**
> So, IFAIKT, this just creates the Grub2 'boot.img' file, and maybe also modifies the 'core.img' file? Is that right? If so, then a little DOS utility to write a USB's MBR using the boot.img should work, yes? 
Not quite right. I thought that the boot.img simply booted the core.img kernel located in the clusters section (e.g. /boot/grub subdir), but core.img gets installed into the reserved sectors area of the fs--after the MBR but before the file allocation tables.

As USB sticks can have geometry that prevents the core.img from being installed correctly, guess I'll stick with syslinux for now, and distribute my custom Ubuntu in .zip format instead. That works for sure. 
Thx,

---

