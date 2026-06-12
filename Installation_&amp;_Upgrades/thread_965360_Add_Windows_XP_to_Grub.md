---
title: "Add Windows XP to Grub"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by a_washington on 2008-10-31
Hi all! I want to add Windows XP HE to the GRUB menu. I have no GRUB experience so please keep your explanations in simple terms.:)



Here is my Hardware configurations:


1 Maxtor 40GB HDD connected via IDE directly to motherboard. This one has Windows XP on it.



1 USB Maxtor 320GB external HDD connected to USB 2.0 port. This one has Ubuuntu on it.


Now both OS'S are bootable changing the order in the BIOS, but I would like it to be in the GRUB menu. 


Thank you in advance for helping me!!!:)

---

### Post by Elfy on 2008-10-31
Can you run these from a terminal please

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

Please use the # button to enclose them in code tags

---

### Post by Hutongs79 on 2008-10-31
I'm going to bump the tread up.cheap wow power leveling (World of warcraft Power Leveling):**buy [WoW Power Leveling](http://www.igsstar.com),  cheap [world of warcraft power leveling](http://www.igsstar.com/wow-powerleveling-us/) , 1-80 level [wow Power Leveling](http://www.wowgoldweb.com),[maple story mesos](http://www.buymsmesos.com),       [wedding invitations](http://www.vponsale.com/invitations/)**

---

### Post by logos34 on 2008-10-31
When you post your fdisk output we'll know what partition # windows is on, but assuming it's the typical layout (partition 1), then you'll want to add a windows entry to menu.lst exactly [as show here]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").  (If instead it's second after a recovery partition, then 'hd1,1')

---

### Post by a_washington on 2008-10-31
OK, I ran the command here was the results:





Disk /dev/sda: 40.9 GB, 40982151168 bytes
240 heads, 63 sectors/track, 5293 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x07eca173

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         677     5118088+   b  W95 FAT32
/dev/sda2   *         678        5292    34889400    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56b38f6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38539   309564486   83  Linux
/dev/sdb2           38540       38913     3004155    5  Extended
/dev/sdb5           38540       38913     3004123+  82  Linux swap / Solaris








And the internal HDD has 2 portions, a recovery portion and the one with windows on it.

---

### Post by caljohnsmith on 2008-10-31
Logos34 actually answered your question, but if you would like a little more specific help, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And look at the entries for Ubuntu that will look similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a37
3-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
If your Ubuntu entries use (hd0,0), then just add this to the end of your menu.lst to boot Windows:
```
title	   Windows XP
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
But if your Ubuntu entries instead use (hd1,0), then use the following for Windows:
```
title	   Windows XP
root       (hd0,1)
chainloader +1
```
Give that a shot and let us know how it goes. :)

---

### Post by a_washington on 2008-10-31
Thank you caljohnsmith!!!!!!!!!!!:) You totally rock!!!!!!! Kudos to you!!!! You are the type of person that makes me use forums!:) I would hit thanks a million time if it would let me!!!!!!!!!:)

---

### Post by caljohnsmith on 2008-11-01
That's great news you can boot Windows XP now, and I'm glad I could help out. Cheers and have fun. :)

---

