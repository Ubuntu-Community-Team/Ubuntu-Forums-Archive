---
title: "GRUB2 Bootcd"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by grondinmf on 2010-05-14
Hey guys, I just installed Ubuntu 10.04 and so far i love it. my only issue is that i wanted to keep my windows installation for now because my tv card wont work under linux(plan on getting a new oine at some point.) so i installed the grub bootloader to a USB flash drive my issue ATM is that my bios is stupid and it only scans one of the connected usb devices when i tell it to boot from usb. this is a pain cause every time i reboot i have to turn off my other usb drive so it will boot.

My question is how can i created a bootable CD or floppy with GRUB2. i have googled but most of the stuff i found returned errors or just did not work. 

thanx for any help.

---

### Post by darkod on 2010-05-14
Is there a specific reason you don't want to install grub2 to the MBR of the hdd? It is perfectly able to dual boot windows and ubuntu.

---

### Post by darkod on 2010-05-14
Otherwise, making a cd with grub2 is not that straighforward because cds are burned trough software usually.

But if you have a floppy drive, just find out the device name (I don't have one, so I can't check), and lets assume the device name is /floppy.

In that case just boot ubuntu, put a floppy in the drive and execute:

sudo grub-install /floppy

That will install grub2 on the floppy. At least I think it should work.

PS. I just remembered, was it called something like /dev/fd0 or similar?

---

### Post by grondinmf on 2010-05-14
i do not want to install the bootloader to the MBR of the hdd cause if i decide to remove linux then i have to repair the windows bootloader this avoids that. 

running sudo grub-install /dev/fd0 does not work it returns:

/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

if i run 

sudo grub-install /dev/fd0 --force

it will install but then when i try to boot it does not work(i will comeback and post the exact error i get in a min as i'm trying again.)

it flahses so fast i can't really see it...tired to pause but did not work...seems to say something like gnome error.

---

### Post by darkod on 2010-05-14
> **grondinmf said:**
> i do not want to install the bootloader to the MBR of the hdd cause if i decide to remove linux then i have to repair the windows bootloader this avoids that. 


Repairing the windows bootloader takes one single command and is done in a second. It's much more complicated what you are trying to do.

If the floppy can't work, I don't know. Writing to a cd like that is impossible too.

---

### Post by grondinmf on 2010-05-14
that is tru...i was just trying to be picky. and since the original grub could be installed to floppy i thought this should work 2 but grub2 is much different...anyways thanx for the help i will either stay like this or move grub to the hdd...

---

### Post by oldfred on 2010-05-14
Herman has instructions for floppy disk or CD or USB as boot.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

Also for grub legacy or grub 0.97 if you look thru his site.

---

