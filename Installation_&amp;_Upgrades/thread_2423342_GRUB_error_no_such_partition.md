---
title: "GRUB error: no such partition"
date: 2019-07-21
forum: Installation &amp; Upgrades
---

### Post by gicanzo on 2019-07-21
As in the title, when I boot my laptop, I get the above message. I previously had my computer set to dual boot Windows 10 and Parrot OS. I then decided to replace Parrot with Ubuntu. However, after installing Ubuntu, I would still get the previous grub screen at startup, which gave as options still Parrot OS and Windows Boot Manager. Therefore, I decided to delete one partition labeled as boot, and got this error thereafter. I can still boot into Windows or Ubuntu by pressing F12 when turning on my laptop . Then I get the option to choose which device (SSD, USB, etc..) and which OS to boot (also for some reason, the parrot option still shows up in that menu, together with two ubuntu entries). If I choose ubuntu, I am finally redirected to the grub screen, where again I have to choose between Ubuntu and Windows.

My ```
fdisk -l
``` results are:

```

Dispositivo     Start      Fine   Settori  Size Tipo
/dev/sda1        2048   1026047   1024000  500M EFI System
/dev/sda2     1026048 349168670 348142623  166G Microsoft basic data
/dev/sda3   535537664 537229311   1691648  826M Windows recovery environment
/dev/sda4   504287232 535537663  31250432 14,9G Linux swap
/dev/sda6   349169664 504286851 155117188   74G Linux filesystem

```

Moreover it returns also a list of 16 /dev/loop devices which I have never seen before.

As I said, there was previously also an sda5 partition labeled as boot, which I deleted. I already tried purging and reinstalling grub as explained in this post:
[https://ubuntuforums.org/showthread.php?t=1581099](https://ubuntuforums.org/showthread.php?t=1581099)

but nothing changed. Still no boot partition is found at startup. Any suggestions?

---

### Post by jeremy31 on 2019-07-21
What result for ```
efibootmgr -v
```

---

### Post by gicanzo on 2019-07-21
> **jeremy31 said:**
> What result for ```
efibootmgr -v
```

This is the result:

```
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0007,0000,0003,0004,2003,2001,2002
Boot0000* ubuntu    HD(1,GPT,465515c1-e971-11e8-8a4f-f64acfe05c03,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* EFI Network 0 for IPv6 (70-54-D2-54-71-F3)     PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(7054d25471f3,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* EFI Network 0 for IPv4 (70-54-D2-54-71-F3)     PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(7054d25471f3,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* Windows Boot Manager    HD(1,GPT,465515c1-e971-11e8-8a4f-f64acfe05c03,0x800,0xfa000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Ubuntu    HD(1,GPT,465515c1-e971-11e8-8a4f-f64acfe05c03,0x800,0xfa000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0006* TOSHIBA MK5075GSX                   BBS(HD,&#65533;,0x500)................-...........A......"...................................
Boot0007* parrot    HD(1,GPT,465515c1-e971-11e8-8a4f-f64acfe05c03,0x800,0xfa000)/File(\EFI\parrot\grubx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


```

---

### Post by jeremy31 on 2019-07-21
```
sudo efibootmgr -o 0004,0003
```
Reboot

---

### Post by gicanzo on 2019-07-21
it worked! Thank you very much :)

---

### Post by gicanzo on 2019-07-21
I guess not really related, but may I ask you also what are all these /dev/loop entries I see? I've never seen anything like that before when running fdisk -l. Here's the whole output:

```
Disk /dev/loop0: 42,8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 8,4 MiB, 8839168 bytes, 17264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 3,7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 14,8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 14,5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 256,2 GiB, 275064201216 bytes, 537234768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 465515C4-E971-11E8-8A4F-F64ACFE05C03

Dispositivo     Start      Fine   Settori  Size Tipo
/dev/sda1        2048   1026047   1024000  500M EFI System
/dev/sda2     1026048 349168670 348142623  166G Microsoft basic data
/dev/sda3   535537664 537229311   1691648  826M Windows recovery environment
/dev/sda4   504287232 535537663  31250432 14,9G Linux swap
/dev/sda6   349169664 504286851 155117188   74G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x51658ff1

Dispositivo Avvio Start      Fine   Settori   Size Id Tipo
/dev/sdb1          2048 976771071 976769024 465,8G  7 HPFS/NTFS/exFAT


Disk /dev/loop8: 149,9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 54,4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 3,7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 2,3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 88,5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 34,6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 140,7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 140,7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


```

---

### Post by jeremy31 on 2019-07-21
See [https://askubuntu.com/questions/906581/what-is-dev-loopx](https://askubuntu.com/questions/906581/what-is-dev-loopx)
From there it looks like this command may show more info
```
df -kh
```

---

### Post by oldfred on 2019-07-21
If you do not have parrot anymore you may want to delete the UEFI entry. 
If not changed:
sudo efibootmgr -b 0007 -B

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 
    
Many of us do not use nor want the snaps.
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

