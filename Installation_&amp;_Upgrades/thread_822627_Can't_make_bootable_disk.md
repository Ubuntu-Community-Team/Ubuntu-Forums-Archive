---
title: "Can't make bootable disk"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by ronti69 on 2008-06-08
Hello,
I am trying to install Xubuntu in an old PC (it's a pentium III with 256 Mb RAM). The problem in the computer doesn't have any drives... no CD, no floppy, nothing. It doesn't have any operating systems so I can't boot. I have an external USB CD drive, also have Puppy linux on a flashdrive, but the MOBO won't boot from USB.
So I tried to pop the hard drive in another computer and installed Puppy in it, in the hopes that I would be able to boot, recognize the USB CD drive and then install Xubuntu. But of course when I put the hard drive back Puppy won't boot. well actually maybe it does (I don't know) but I get this error message saying "can't find pup400.sfs" and "going into ramconsole mode" and I get a command prompt ... where I have no idea what to type
Can somebody please help?
Thanks!

---

### Post by logos34 on 2008-06-08
If it doesn't support usb boot, then you won't be able to boot from usb cdrom.

The only way left is to take the drive out again and install xubuntu on it. But you may have the same problem as you did with puppy.

Or maybe this is a desktop, in which case there is one other way: get you hands on an internal cdrom (connect it up at least temporarily to do the install)

---

### Post by ronti69 on 2008-06-09
Thanks, but I already tired that and it didn't work. The computer is in fact a kind of laptop - it is actually one of those terminals they use in the self checkouts in some stores. It has no CD, no floppy, only one IDE. Does anyone know how to install ANY operating system?
Thanks for reading

---

### Post by HunterThomson on 2008-06-09
What about installing over a network?

---

### Post by stchman on 2008-06-09
> **ronti69 said:**
> Hello,
I am trying to install Xubuntu in an old PC (it's a pentium III with 256 Mb RAM). The problem in the computer doesn't have any drives... no CD, no floppy, nothing. It doesn't have any operating systems so I can't boot. I have an external USB CD drive, also have Puppy linux on a flashdrive, but the MOBO won't boot from USB.
So I tried to pop the hard drive in another computer and installed Puppy in it, in the hopes that I would be able to boot, recognize the USB CD drive and then install Xubuntu. But of course when I put the hard drive back Puppy won't boot. well actually maybe it does (I don't know) but I get this error message saying "can't find pup400.sfs" and "going into ramconsole mode" and I get a command prompt ... where I have no idea what to type
Can somebody please help?
Thanks!

I have a tutorial to make a bootable CD using K3b.

[http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html)

---

### Post by zvacet on 2008-06-09
Try [unetbootin.]("http://unetbootin.sourceforge.net/")

---

### Post by logos34 on 2008-06-09
> **zvacet said:**
> Try [unetbootin.]("http://unetbootin.sourceforge.net/")

he's got no OS on the machine

---

### Post by Habbit on 2008-06-09
Most probably, your only option is taking the drive out and installing Xubuntu on another computer. You need to ensure that the bootloader (usually GRUB) is installed on the HD you're installing the OS to (it's usually installed on the first HD).

Then move the HD back to the target computer and, on first boot, enter the GRUB menu and correct the drive number if necessary - it should state (hd0). As (-kxf)Ubuntu uses UUIDs to identify its partitions, you shouldn't need to change anything else in order to get the system to boot.

Once you have it working, edit /boot/grub/menu.lst (or /boot/grub/grub.cfg if you're using GRUB 1.9x instead of 0.9x) and correct the drive number again, then run "sudo update-grub".

---

### Post by zvacet on 2008-06-09
@ **logos34**

> he's got no OS on the machine

Sorry,I overlooked that.My mistake.

---

