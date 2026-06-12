---
title: "Grub 1 configuration"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by doetoe on 2012-06-29
I had a perfectly working multi boot system (two Ubuntu's and windows XP) on a laptop. When I changed one of the Ubuntu's to Arch linux, and reinstalled a bootloader in the process, overwriting the original one, I didn't manage to boot anymore. 
My ubuntu resides on /dev/sda7. To be able to boot it, I added the following lines to my menu.lst:

title Ubuntu
root (hd0,6)
kernel /boot/vmlinuz-2.6.35-32-generic root=/dev/sda7 ro
initrd /boot/initrd.img-2.6.35-32-generic

These files do exist. 
This starts the boot process seemingly correctly, but it just stays forever in the Ubuntu splash screen (the little balls below "ubuntu" do move). I suspect it is not relevant, but the installation is of Ubuntu 10.4, and the machine is a more or less 8 year old laptop, Compaq Presario V4000.
In my boot partition there are a few more files with the same version number: System.map-2.6.35-32-generic, abi-2.6.35-32-generic, vmcoreinfo-2.6.35-32-generic. Should these also be mentioned in menu.lst?

If anyone sees anything that is clearly wrong, could you please let me know?

Thanks

---

### Post by jmfal on 2012-06-29
Try restarting and select recovery kernal at the grub screen and update grub from the menu.
If you are brought back to the menu select normal boot and follow the prompts.
If not, at the command prompt enter:
```
  startx     
```

enter username and password at the prompts and at the login screen  restart..

---

### Post by coffeecat on 2012-06-30
> **doetoe said:**
>  When I changed one of the Ubuntu's to Arch linux, and reinstalled a bootloader in the process, overwriting the original one, I didn't manage to boot anymore. 
My ubuntu resides on /dev/sda7. To be able to boot it, I added the following lines to my menu.lst:

I may be misreading this, but it sounds as though the Arch version of grub may have been installed to the mbr, in which case editing your Ubuntu's grub1 menu.lst won't help. And it may be that the Arch grub is misconfigured for your Ubuntu installation. In case this is so, it would be helpful to get an overview of your system with the boot info script.

Boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page (but see below) - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Two comments. There is an error in the boot info script instructions on that page. The boot info script file is now called bootinfoscript, so the command to run it, if you have moved it to the desktop, should be:

```
sudo bash ~/Desktop/bootinfoscript
```

Also - it should work in Arch. If you can boot into Arch, you could try running it there instead of using the Ubuntu live CD.

---

### Post by doetoe on 2012-06-30
Thanks jmfal and coffeecat. 
Indeed I had installed the new bootloader in the mbr, and was editing the menu.lst of the new installation (in particular I couldn't select a recovery kernel either unless I would add it myself first). The bootinfoscript looks very useful. I'm sure I will be using it at some other moment.
The problem (or at least the solution) turned out to be unrelated to grub: in /etc/fstab I was trying to mount the ext4 partition containing the arch installation, as type reiserfs. I don't know why that stopped the whole boot process, but fixing it solved the problem.

---

