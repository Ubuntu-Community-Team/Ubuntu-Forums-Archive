---
title: "I gave up"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Timelyne on 2009-12-22
I tried everything in the book to install ubuntu using wubi but just cannot get it to boot.

Stuck at this **sh: grub** 

I searched and tried every command,nothing works.

I installed it on a second hard disk from win XP.

---

### Post by USB_NL on 2009-12-22
you can try Ubuntu on a usbstick if you can make them bootable in either the bios or bootmenu of your PC

google pendrivelinux

---

### Post by phillw on 2009-12-22
> **Timelyne said:**
> I tried everything in the book to install ubuntu using wubi but just cannot get it to boot.

Stuck at this **sh: grub** 

I searched and tried every command,nothing works.

I installed it on a second hard disk from win XP.


Have you tried this ?

>                                   **Re: sh:grub > desperation**             
                                                                [SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

     Quote:
                                                 # Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B]                                 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
                                                                                               It's from drs305 and has had great success. Post back if you still have problems after doing as it says.

The long, in depth chat on the problem is over here --> [http://ubuntuforums.org/showthread.php?p=8384533](http://ubuntuforums.org/showthread.php?p=8384533)

Regards,

Phill.

---

### Post by Timelyne on 2009-12-22
by the time a type this**[COLOR=Navy] loopback loop0 /ubuntu/disks/root.disk[/COLOR]**  i get error file not found or no such disk.

---

