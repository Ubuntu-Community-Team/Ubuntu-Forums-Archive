---
title: "manual GRUB install using ntldr for boot"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Captain Giraffe on 2008-03-26
I have a XP installation on hd0,0 with mbr booting the XP installation on hd0,0
on hd0,1 i installed ubuntu from a Live CD without installing grub at the same time as there were no option to install it only on hd0,1

Id like to use the nt bootloader to boot grub
My progress so far is that I get to the grub command prompt on hd0,1 I still haven't been able to boot the installed system. Im using the live CD to manipulate the hd0,1 ubuntu installation.

I have tried both (consulting the quite tersely written grub manual)
(sudo) grub-install --root-directory=/boot /dev/sda1
then copied the bootsector from sda1 (hd0,1) to the ntldr boot.ini entry.
and
sudo grub
with
root + install
as well as
root + setup  (whats the difference between setup and install?)

Im thinking that the chainloader FILE command can be useful?
I once got a message that vmlinuz.... was not a proper executable not sure if that is important.

Any ideas?

---

### Post by confused57 on 2008-03-26
Here is an older tutorial that I have bookmarked:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

You might want to burn a Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a great utility for booting problems...it's capable of booting Windows or Linux and can restore either's IPL(Initial Program Loader) to the mbr.

You can install grub to the root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
you'll need to read down a little in the tutorial to find how to install to the root partition

During an install of Ubuntu, you can install grub to the root partition by clicking on the "Advanced" button in the lower right and change the default (hd0) to /dev/sda2(or however your root partition is recognized by the installer).

---

