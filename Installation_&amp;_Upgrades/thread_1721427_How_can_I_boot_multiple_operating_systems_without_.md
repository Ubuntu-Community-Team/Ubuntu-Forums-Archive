---
title: "How can I boot multiple operating systems without choosing the OS at the machine?"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by sofakng on 2011-04-04
Sorry for the hard to understand title but it's difficult to describe in one sentence.

What I'd like to do is install Windows and several different versions of Linux on the same system.  After everything is installed, I'd like to switch between operating systems *from inside the operation systems*.

Example:

I'm inside Windows but I want to reboot into Ubuntu 9.04.  I need to run a command to update the boot manager so it knows to boot into Ubuntu 9.04.

I do not want to walk to the physical box to make a menu selection.

EDIT:  I'd like to be able to switch between Windows 7 and Ubuntu (9.04, 10.04, and 10.10)

---

### Post by Megaptera on 2011-04-04
I don't think you can do that without re-booting. Unless on virtual system but I don't run those.

Also support for 9.04 is not going to around much longer - might even have ceased I'm not sure.

---

### Post by perspectoff on 2011-04-04
You want virtual machines.

Use either VirtualBox (recommended and easy to use) or VMWare (more complex but slightly more powerful in the long run).

---

### Post by ajgreeny on 2011-04-04
Yes Ubuntu 9.04 has now lost its support, and 9.10 is about to lose its support as well in a week or two.  Go for 10.04.

To answer your real question, however; I don't think you can do what you want either without running virtual installations in VirtualBox or another host.

---

### Post by Hedgehog1 on 2011-04-04
+1 on virtual machines. I use this with great success.

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

It also has the advantage of unlimited installs that use much less disk space than 'partitioned' installs. Easy backups, too!

Virtual Box is free, and available for Windows as the host OS or Linux as the host OS.

I use Ubuntu as the host OS at home, and Windows as the host OS at work.

***The Hedge***

:KS

p.s. If you use Linux as the Host OS, you can run an OS in a work space.  It is very handy and looks rather cool:

[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]

---

### Post by nikRbokR on 2011-04-04
Well, in terms of switching without having to get up, all you need to do is reboot and then select the appropriate OS when you boot up.

However, if you don't want to reboot at all, then virtual machines are the way to go. Virtualization may cause some problems if you have dated hardware, but as you can see from Hedgehog1's photos it's quite handy. If you use Windows most of the time, then you may want to virtualize the Ubuntu distros (stick with 10.04 and 10.10... especially now that 11.04 is due to be released soon).

I don't have much experience with virtualization, but I tried it once. Wasn't too difficult.

---

### Post by oldfred on 2011-04-05
I do not know exactly how to do what you want, but.

I boot grub2 in my USB flash drive that is FAT32. You could create a FAT32 partition with grub2 and boot that. Your grub.cfg can have a set default line that you adjust from a .bat script in windows and a bash file in Linux.

These are loop back entries since I am directly booting ISO files but you can easily use standard partition boot entries:

```
[COLOR=Red]set default=0 [/COLOR]
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600


menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/natty-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

```to boot a partition use this style grub2 entry. This will then boot the newest kernel even if updated:

Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. It uses the link file for the kernal in / (root) for Debian, not sure about other distributions.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Another way might be to dd different boot loaders grub windows into the MBR. I think my OS/@ did this back when.

---

