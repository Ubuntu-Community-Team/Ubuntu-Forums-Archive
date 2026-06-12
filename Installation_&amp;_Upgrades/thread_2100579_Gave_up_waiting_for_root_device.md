---
title: "Gave up waiting for root device"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by 333ameeth on 2013-01-02
hi,
I'm using  ubuntu 12.04 lts,
previously everything was fine and few days before i got following 
error:
 
```
Gave up waiting for root device. Common problems:  - Boot args (cat /proc/cmdline)     - Check rootdelay= (did the system wait long enough?)     - Check root= (did the system wait for the right device?)  - Missing modules (cat /proc/modules; ls /dev) ALERT! /dev/disk/by-uuid/0c65a8c2-a7654613-aa98-16ff0119ceb9 does not exist. Dropping to a shell!
```and then comes (initramfs) prompt:
here i tried @ sudo update -initramfs -u
but it is not working.

 how to overcome this problem?  

thanks in advance, Ameet

---

### Post by dino99 on 2013-01-02
i suppose you have made some hasardous tweaks dont you ?

can you still boot on recovery mode ? (if you dont see the grub menu, then hold "shift" down at bios end process)

if your system is really borked (as it seems) then a clean reinstall is mostly the easiest and fastest way to get it back.

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by darkod on 2013-01-02
Looks like it's not finding the root partition. Try to boot the computer with your ubuntu cd in live mode (Try Ubuntu), and browse the hard disk. Do all folders open correctly? Can you see files and folders on it?

Open terminal and post the output of:
```
sudo blkid
sudo parted -l (small L)
```

---

### Post by cross37 on 2013-01-03
If you can boot up with a live CD and see all of your files, edit /etc/default/grub.conf, and add rootdelay=60 to GRUB_CMDLINE_LINUX.

for example:
GRUB_CMDLINE_LINUX="rootdelay=60"

This will allow the kernel to wait an extra 60 seconds for the root device to become available.  

Some raid controllers take a while to make the drives available to the OS. 

On a Dell T310 server that I had, it sometimes needed longer than 60 sec.  I had rootdelay=90.

---

### Post by Corin-EU on 2013-02-06
Please try this.

When the GRUB screen appears, press 'e' to edit the boot entry which is failing to find the root device.

Use the down arrow key to move down to the line which beings

linux /vmlinuz-...

and then the right arrow key to move along to just before " ro ".  Then use backspace to delete the preceeding UUID
string all the way back to and including UUID=, just leaving root=

Then type in the name of the root device eg /dev/sda1 or /dev/sda5 according to on which disk partitition you actually installed the root file system.

Then type CONTROL X  and watch to see if the system boots properly.

I am experiencing this problem on a 64 bit system but not on an i386 system, both with 12.10 (via Mint 14)

---

