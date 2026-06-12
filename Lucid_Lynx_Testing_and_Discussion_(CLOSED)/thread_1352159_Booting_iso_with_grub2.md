---
title: "Booting iso with grub2"
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2009-12-11
I've installed grub2 to a flash drive formatted with fat32. I can boot 9.04 and 9.10 but not 10.04. This is what I have for 10.04:

```
menuentry "Ubuntu Alternate 10.04 64bit Alpha 1" {
 set root=(hd0,1)
 loopback loop /boot/iso/lucid-alternate-amd64.iso
 linux (loop)/install/vmlinuz iso-scan/filename=/boot/iso/lucid-alternate-amd64.iso noeject noprompt quiet splash cdrom-detect/try-usb=true
 initrd (loop)/install/initrd.gz
}
```

The kernel boots and the initrd loads but the installer can't mount the "CD". Is there a parameter that I missed?

*Edit* More descriptive title

---

### Post by VMC on 2009-12-11
> **Jordanwb said:**
> I've installed grub2 to a flash drive formatted with fat32. I can boot 9.04 and 9.10 but not 10.04. This is what I have for 10.04:

```
menuentry "Ubuntu Alternate 10.04 64bit Alpha 1" {
 set root=(hd0,1)
 loopback loop /boot/iso/lucid-alternate-amd64.iso
 linux (loop)/install/vmlinuz iso-scan/filename=/boot/iso/lucid-alternate-amd64.iso noeject noprompt quiet splash cdrom-detect/try-usb=true
 initrd (loop)/install/initrd.gz
}
```

The kernel boots and the initrd loads but the installer can't mount the "CD". Is there a parameter that I missed?

*Edit* More descriptive title
I'm not sure I use ISOLINUX to boot my usb flash drives. But you may check out your root=parameters . If you have an external HD, don't yo want hd1,1? Or is that ISO reside on the internal HD?

---

### Post by Jordanwb on 2009-12-11
I use grub2 to boot the iso. Both ISO and grub2 are on a 1 partition USB flash drive.

---

### Post by Gina on 2009-12-11
I have a feeling that doesn't work...  I use the **System>Administration>USB Startup Disk Creator** menu option which installs ISOLinux plus the all the rest.

---

### Post by ayates on 2009-12-11
Here is my entry on a sata hard drive and it works.

```
menuentry "Lucid Iso                                           " {
         loopback loop (hd0,2)/lucid-desktop-i386.iso
         linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso noeject
         initrd (loop)/casper/initrd.lz
}
```

---

### Post by Jordanwb on 2009-12-11
> **ayates said:**
> Here is my entry on a sata hard drive and it works.

Okay I'll try that.

I can get the Desktop amd64 booting fine via the ISO and grub2, the splash image during bootup is ugly as hell but I don't get a message about mounting a CD.

---

### Post by ranch hand on 2009-12-11
> **ayates said:**
> Here is my entry on a sata hard drive and it works.

```
menuentry "Lucid Iso                                           " {
         loopback loop (hd0,2)/lucid-desktop-i386.iso
         linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso noeject
         initrd (loop)/casper/initrd.lz
}
```
I am going to try that too.  I have tried to get these Ubuntu ISOs to boot before with no luck at all.  I may have problems because mine are all amd64.

If this doesn't work I may down load the i386 and see if that works.

---

### Post by Jordanwb on 2009-12-11
This is what I have that works for the Desktop variants:

```


menuentry "Ubuntu Desktop 10.04 32bit Alpha 1" {
 set root=(hd0,1)
 loopback loop /boot/iso/lucid-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/lucid-desktop-i386.iso noeject noprompt quiet splash cdrom-detect/try-usb=true
 initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu Desktop 10.04 64bit Alpha 1" {
 set root=(hd0,1)
 loopback loop /boot/iso/lucid-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/lucid-desktop-amd64.iso noeject noprompt quiet splash cdrom-detect/try-usb=true
 initrd (loop)/casper/initrd.lz
}
```

Changing the file paths for the alternate variant doesn't work, can't mount the "CD".

---

### Post by ranch hand on 2009-12-11
WOW, thanks for that.

I have 4 installs now of Lounge Lizard with the A1 and my boot/root is not this one (Stoned Lizard) so I am chrooting into the buggers to update and then boot to them to see if they work (before updating this one) and to play abit.

So I can add this stuff and get the menu right and then try it later.

I stay on here as much as possible as I am running boinc here.

EDIT;
What is the;
> 
[FONT=monospace]cdrom-detect/try-usb=true

for?
[/FONT]

---

### Post by Jordanwb on 2009-12-11
I'm not exactly sure. It was in a tutorial I found and the iso's boot, so I leave it there.

---

### Post by ranch hand on 2009-12-11
Same result I always get - "file not found" and yes I did put in where it is correctly.

It is not on the partition that is boot/root.  Could that be a problem?  I can change where I boot from easy enough, wee are using grub2.

---

### Post by Jordanwb on 2009-12-11
> **ranch hand said:**
> It is not on the partition that is boot/root.  Could that be a problem?  I can change where I boot from easy enough, wee are using grub2.

As far as I know, the ISO's and grub2 have to be on the same partition.

---

### Post by ayates on 2009-12-11
That's the only way I got it to work. ISO & grub on same partition.

---

### Post by ranch hand on 2009-12-11
Well, tomorrow when I am back on the Stoned Lizard, I will copy the menu entry from Lounge Lizard and change my boot/root and see what happens.

This has been getting on my thungas.  Ubuntu puts out the first full grub2 OS and you can't get Ubuntu ISOs to boot as well as other ISOs.  That is just not right.

It is FUN.

---

### Post by Jordanwb on 2009-12-11
> **ranch hand said:**
> Stoned Lizard, Lounge Lizard, thungas

:confused:

Um okay.

---

### Post by ranch hand on 2009-12-11
Stoned Lizard=9.04>9.10>10.04 upgrade, Lounge Lizard=9.10>10.04 upgrade.

Some of us think Lucid Lynx is lame.

Thungas you either have or haven't got.

---

### Post by Gina on 2009-12-12
I guessed the Lizards were computers, as for "thungas" use your imagination :lolflag:

---

### Post by ranch hand on 2009-12-12
> **Gina said:**
> I guessed the Lizards were computers, as for "thungas" use your imagination :lolflag:
You have it almost right.  I only have the one box.  I have 8 OS', right now, on the test platform (dual SATA external enclosure with two 320Gb HDDs).  I also have "Daily Lizard" and the boring "ISO-testing" installs of 10.04-testing.

---

### Post by Jordanwb on 2009-12-12
I tried the 9.10 alternate ISO and for some reason it can't mount the "CD" either. :(

---

### Post by ranch hand on 2009-12-12
Nope, still "can't find file".  This is, however, just as well I have ever done to get one of these to boot.

---

### Post by Jordanwb on 2009-12-12
I can't get Desktop amd64 to fully load on my desktop machine. Xorg loads and that's it. Black screen, can't drop to a terminal. It works fine on my laptop, my desktop has a nvidia card, maybe that's the problem.

---

### Post by ranch hand on 2009-12-12
I am using an ATI card, that could be the problem.

---

### Post by Jordanwb on 2009-12-12
> **ranch hand said:**
> I am using an ATI card, that could be the problem.


Laptop (ATI chip): Great
Desktop (Nvidia): fail

---

### Post by ranch hand on 2009-12-12
I think this is strange.  I think it has to do, mainly, with the CD being barely compatible with booting.

---

### Post by Jordanwb on 2009-12-12
The desktop isos boot just fine. For some reason the alternate CDs do not. I made my xorg problem a different thread to keep them seperated.

---

### Post by ranch hand on 2009-12-12
Sorry, I meant "ISO" instead of "CD".  Been a long day and my brain is ready to shut down.

---

