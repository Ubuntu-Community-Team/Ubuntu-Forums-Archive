---
title: "Booting Windows XP (When it is the only partition)"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by BCollar on 2009-12-21
Hello all,

After using my computer's 'restore cd' and erasing all partitions I was unable to boot Windows XP.  

Also the Grub2 and Grub Rescue was damaged.

I was able to install a Grub v.1.97 boot loader from the 9.10 live cd.

Now I have an NTFS partition and the computer will boot to an SH prompt.  However when I command "Boot" it says "no kernel installed".

I am aware of the fixmbr feature of the Windows Setup CD.  However I have no Setup CD.  There is another program that you are supposed to be able to boot from a disk, called MbrFix from Sysint.no but I was unable to get it to work from my SD Card.

I am trying to restore Windows XP to it's purest state.  Is there a way to load a "Windows Kernel"?

What options do I have from this point?

---

### Post by darkod on 2009-12-21
I'm not sure if it will work, because I haven't tried it, but there should be a command in linux to install windows MBR.
Boot with ubuntu cd, Try Ubuntu option. In terminal do:

sudo apt-get install install-mbr
sudo install-mbr /dev/sda

Reboot without the cd and see if it helped.

---

### Post by BCollar on 2009-12-21
There doesn't seemed to be a package or a subsequent command for that advice.  

Wait- I found a package called Mbr in Synaptic..  I downloaded it, what next?

---

### Post by BCollar on 2009-12-21
WHHHOOOO!  It's WORKING!!  

After downloading the package "Mbr" using Synaptic from the 9.10 live cd  I was able to install it using **sudo install-mbr /dev/sda **

The previous posts said it was impossible to do without a Windows Setup CD..  

They were wrong!  And what I always knew shouldn't be as difficult as having to go to the store and buy a Windows Installation CD.. ending up being painless!  

Thanks DarkoD!  YOU  :guitar: !!

---

