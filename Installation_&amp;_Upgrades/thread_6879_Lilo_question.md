---
title: "Lilo question"
date: 2004-12-02
forum: Installation &amp; Upgrades
---

### Post by rejean on 2004-12-02
Hi all!
I have installed Ubuntu on a 2nd hd (2.5 Gb) on a Penthium II, 500 Mhz, 256 Mb RAM but I chose to use Lilo instead of Grub. I have a hda swap file (534 Mb), a hda5 ReiserFS (probably a failed Slackware install), a hda3 Win95 Fat16 probably empty and a hda4 W95Fat32 which is probably my WinXP partition. 
I tried doing a: sudo su
                         #cfdisk 
to change the Flags to Boot without any luck. Now when I try to write the partitions I am told that more than one partition is marked bootable and that DOS MBR cannot boot this. How do I make hda1 and hda3 unbootable so that only hda4 is bootable?

Also, if I may, when I do lilo I get the following:

root@ubuntu:/home/rene # lilo
Warning: /etc/lilo.conf should be writable only for root
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/hda1'
Warning: The boot sector and map file are on different disks.
Added Linux *
Skipping /vmlinuz.old
Warning: CHANGE AUTOMATIC assumed after "other=/dev/hda3"
Added Windows
root@ubuntu:/home/rene #

I have tried reading as many topics on this forum and looked into the FAQs without luck. Where could I find a cfdisk man or could someone help me dual booting Ubuntu and WinXP Pro?
Thanks in advance,
Rejean

---

### Post by rejean on 2004-12-02
Hi all!
Never mind. Since I had so little running in Ubuntu, yet. I decided to reinstall with Grub and everything is under control now. 
Thanks for reading me. :wink: 
Rejean

---

