---
title: "Removing windows 7, install Ubuntu 10.10 only"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by tok78 on 2011-02-01
Hi all, 

this is my first post so please go easy on me. 

I am total newbie when it comes to Linux with little to no understanding of the command lines and what they mean. 

Issue: 

I currently have a dual boot Windows 7 PC (Toshiba Satellite A100-756 with 250GB HDD and 3GB RAM, 32-bit). 

What I want to do is format the HDD (removing both partitions) and make a clean install of Ubuntu only. 

I tried for several hours last night to achieve this using Ubuntu 10.10 and Pendrive, but with no success. System would not boot from USB stick. 

How do I: 
1. Format the HDD and remove the partitions using only Ubuntu on a USB stick? 

2. Install Ubuntu and partition the HDD ready to copy over my backed up files? 

I apologise if there is an existing thread on this. 

>Thanks in advance!

---

### Post by kukker32 on 2011-02-01
i would prefer installing from live cd. but if it's a notebook then go the usb way.

make sure the bios is set to boot from usb..

and during installation you will be prompted for making the partitions.
if you select "format partitions and use whole disk" or something similar, it should clean the whole disk and making a fresh install ;) 

when done it's ready to transfer files you've backed up..

hope this was helpfull.

---

### Post by runeh76 on 2011-02-01
Hi

Install from CD.
Just wanna give a tip..
When u have installed Ubuntu, make a backup and second account (user), then u can "play" around. And if something goes wrong, u have backup and ur installation (root) account in safe.

Keep fun and Enjoy  ;)

---

### Post by tok78 on 2011-02-01
Hey, the issue I have is that the laptop is not booting from the USB. 

It reads the USB and then boots from the HDD. 

How do I fix this issue?

---

### Post by kukker32 on 2011-02-01
somewhere in the bios set it to 'boot' from usb..

---

### Post by tok78 on 2011-02-01
> **kukker32 said:**
> somewhere in the bios set it to 'boot' from usb..

I have done that - the issue is that the USB stick is being ignored.

---

### Post by grahammechanical on 2011-02-01
What more can anyone add to solve this problem? Except the things that insult your intelligence but are the things we all slip up on from time to time. Such as when you exited the BIOS set up program did you chose "Exit and Save changes," or "Exit without saving changes?" Did you put boot from USB before boot from hard disc?

Regards.

---

### Post by Swagman on 2011-02-01
You may need to press F11 or F12 when machine posts

It's F8 on mine to get the boot selection. <--- That over-rides BIOS option believe it or not !!

Oops.. That might be F2 for your machine

---

### Post by Mark Phelps on 2011-02-01
If it reads the USB and then skips to the HDD, that means that the USB is not "bootable".  You can't just copy files to it to make it bootable; you have to follow specific steps.

See the link below on how to use Unetbootin to make a bootable USB stick with Linux distro on it:

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

