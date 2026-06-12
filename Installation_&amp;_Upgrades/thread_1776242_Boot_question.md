---
title: "Boot question"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by JohnBonne on 2011-06-05
I have installed Windows and Ubuntu on my hard drive. Studied a bit and couldn't find an answer to this question. I have an external drive plugged in to a usb port. I have had an operating system on this hard drive before, so I know how to go about putting an operating system on it. It will house xfce.
   I wanted to know if I can install the efxe O/s and add it to my boot sequence; Or, if installing it will wipe out my Windows/Ubuntu install. If it will wipe out my booting into windows could I install the Live CD vanilla on the disk so I can boot directly from it. 

Also the boot partition, should I place the o/s on  /boot, /, or at the beginning?

Home from vacation,
John

---

### Post by JohnBonne on 2011-06-06
> **JohnBonne said:**
> I have installed Windows and Ubuntu on my hard drive. Studied a bit and couldn't find an answer to this question. I have an external drive plugged in to a usb port. I have had an operating system on this hard drive before, so I know how to go about putting an operating system on it. It will house xfce.
   I wanted to know if I can install the efxe O/s and add it to my boot sequence; Or, if installing it will wipe out my Windows/Ubuntu install. If it will wipe out my booting into windows could I install the Live CD vanilla on the disk so I can boot directly from it. 

Also the boot partition, should I place the o/s on  /boot, /, or at the beginning?

Home from vacation,
John

Anyone?

---

### Post by Toz on 2011-06-06
Not exactly sure what you mean when you say "xfce's O/S", but if you are referring to xubuntu, then read on.

If your system can boot from the external drive, then you should be good to go. The xubuntu installer will allow you to install to the external drive. 

Important things to keep in mind:
1. During the install process, make absolutely sure that you select the external drive to install to (not the internal one)
2. When asked where to install the boot loader (grub), make sure you select the external drive and not your internal drive.

When you want to run the install on the external drive, simply tell your bios to boot from the external drive and you should be good to go.

---

### Post by oldfred on 2011-06-06
This is Maverick with standard Ubuntu, but the install process is the same. To get a choice on where to install grub2's boot loader, you have to use manual install.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by JohnBonne on 2011-06-13
> **oldfred said:**
> This is Maverick with standard Ubuntu, but the install process is the same. To get a choice on where to install grub2's boot loader, you have to use manual install.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

I'll be giving that a try this weekend.

---

