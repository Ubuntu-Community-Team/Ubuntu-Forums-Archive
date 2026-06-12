---
title: "can't install Ubuntu 8.04"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by yipeskop on 2008-06-04
I for whatever reason cannot install 8.04. when I put in the Ubuntu 8.04 live cd to install, it starts loading the cd and brings me to that screen with the little orange bar that goes back and forth. After that it just brings me to a black screen that says
```
BusyBox V1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built in commands.

(initramfs)_

```

I then tested the live cd on two other computers and it worked perfectly fine. I tried my old 7.10 live cd on my computer and it worked perfectly fine.

Since that didn't work, I thought I'd try the alternate text based installer cd. It got to the point where it needed to mount the cd and I then got an error saying it couldn't mount the cd. I tried it on another computer and again it worked perfectly fine. 

Does Ubuntu 8.04 not support the TSScorp CDDVDW SHS202N CD/DVD drive or something? or is something else causing this?

---

### Post by wpshooter on 2008-06-04
Is the firmware on your CD drive up-to-date ?

---

### Post by UltraDangerLord on 2008-06-04
I'm having a similar problem.

I own get the..

> BusyBox V1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built in commands.

(initramfs)_

when i change the BIOS's sata controller mode from SATA to AHCI.

If I have the sata controller mode set to SATA the cd will boot up fine until it gets to the partition manager....

Once at the partition manager it lists no disks to change...

So.... I'm like hmmmm

---

### Post by Quannah on 2008-06-04
Finally! I have the same problem...

I have 2 SATA hard drives.
Hard Drive 1 has Windows XP Pro installed;
on Hard Drive 2 I want to install Ubuntu.

When I boot from the 8.04 Live CD everything starts fine, but then it ends with the BusyBox. I read that it has some purpose, but this isn't how the install should be, right?

Now I even managed to boot the Live CD from a USB pendrive, and this brings me to the Ubuntu 'desktop' with the install button. But when I start configuring the installationi, I can only choose the USB drive as partition. Both SATA hard disks are invisible in Ubuntu.

I have tried everything, with different boot settings in the BIOS, with both Live CD (cd-rom) and USB drive, with my second second drive formatted or unformatted (I read a full Linux install does't like Windows drives), but nothing works :(

Please help!

Edit: see [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195) for a discussion of this problem, and some solutions that have worked for some people (I'm not there yet).

---

### Post by Quannah on 2008-06-07
I finally got it right! After reading the golden tip in the other thread I mentioned above: "pci=nomsi".

My BIOS default settings for the two SATA HardDisks were 'Native IDE', which is IDE emulation, not the real SATA mode.

Using Native IDE I got the BusyBox and couldn't install Ubuntu 8.04. Windows XP no problem.
Using Legacy IDE I could install Ubuntu, as well as Win XP, but I kept getting startup errors, boot procedure would hang looking for my second HDD and give a '4th Master Hard Disk Error' - even though both hard disks  were recognized in the BIOS.
Using AHCI I couldn't install Windows (Hard disks not recognized) or Ubuntu (get the BusyBox instead). But this got me reading and I found out AHCI is actually the real SATA mode, which is of course preferable if you have SATA drives, even though the advantages are not that noticeable for most users.

So the solution was to use a RAID driver for the Windows installation (RAID uses AHCI as well). I got mine from my mainboard vendor (MSI) and slipstreamed it into a Windows XP installation disc (great! it actually worked) which was easy using nliteos. [www.nliteos.com](www.nliteos.com).
And for Ubuntu the solution was to install from the cd using the F6 option and simply add 'pci=nomsi' after the boot command line (that worked with Native IDE as well).

Off-topic: I'm not a hardened Linux user, but I know my way around with computers and used Linux before, and for me to need several days to finally figure everything out just because I have SATA drives, I think means there is still a lot to be won regarding Ubuntu ease of use.

On-topic: glad to finally have my dual boot system the way I want it, and even learned some interesting stuff along the way. Also, I really really like the way that Ubuntu desktop appears on my screen ;)

---

### Post by avtolle on 2008-06-07
FWIW, for anyone reading this, I recall seeing a discussion of this in other threads, and it appears to be a known bug, Search around, and you'll likely find a link to Launchpad about this.

---

