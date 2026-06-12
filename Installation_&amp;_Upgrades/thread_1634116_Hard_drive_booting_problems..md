---
title: "Hard drive booting problems."
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by svw on 2010-11-30
I have some serious issues with my hard drive. Yesterday my computer (MSi Wind U-100 with Ubuntu 10.10 Netbook version) froze when I was working with TrueCrypt and Gimp. I used the power button to turn of the computer. When I restarted I had to choose from the Grub menu but neither the normal nor the recovery mode worked. I got this message:

> mount: mounting /dev/disk/by-uuid/dca5b708-43c7-4f96-a569-b25046ec3687 on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
no init found. try passing init = bootargI tried to get access to my hard rive using thumb drive Linux but I couldn't get access to my hard drive again. 
I get the following message: 

> Error mounting: mount: wrong fs type, bad option, bad superblock on  /dev/sda1, missing codepage or helper program, or other error. In some  cases useful info is found in syslog -try dmesg|tail or so#dmesg|tail gives the following output:

> ubuntu@ubuntu:~$ dmesg | tail
[  451.089213] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  451.089227] Descriptor sense data with sense descriptors (in hex):
[  451.089235]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  451.089266]         00 00 08 29 
[  451.089279] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  451.089294] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 00 08 28 00 00 08 00
[  451.089323] end_request: I/O error, dev sda, sector 2089
[  451.089362] EXT4-fs (sda1): 
[  451.089371] ata1: EH complete
[  451.089378] can't read group descriptor 4
ubuntu@ubuntu:~$ 
Does anyone have a clue how to solve this? At least I want to be able to save the data from my hard disk. Because I am not able to access it I wondered if a new installment would solve the problem. Your help is very welcome.

---

### Post by oldfred on 2010-11-30
I would try to run fsck to see if that fixes things:

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by svw on 2010-12-01
I get this output:

> "Attempt to read block from filesystem resulted in short read while  trying to open /dev/sda1 Could this be a zero-length partition?"

EDIT- I recoverde my harddisk using this method:  [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

I saved my files so I now do a new clean install

---

