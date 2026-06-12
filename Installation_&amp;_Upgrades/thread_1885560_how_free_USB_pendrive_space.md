---
title: "how free USB pendrive space?"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by uhuru53 on 2011-11-23
Using Ubuntu 11.10 on USB 8 Giga pendrive.
I get "shortage of disk memory" warning even if the pendrive isn't full at all.
Anyhow please tell me how could I free some memory space?
Thanks.

---

### Post by raja.genupula on 2011-11-23
actually in ubuntu even though you have deleted the data , it will be stored in .Trash folder in each and every drive . So we can eliminate that data comlpetely my erasing it in Trash also . 

check it out once.

---

### Post by uhuru53 on 2011-11-23
My trash is empty   :-(

---

### Post by jerrrys on 2011-11-23
your trash is empty.  what about the pendrive? mount the pendrive and look for a hidden folder, a **.trash** folder.

---

### Post by sudodus on 2011-11-23
hi uhuru53

Do you run ubuntu in a live session from the usb pendrive? If that is the case, is it a regular live session or a persistent session (so that you are saving data in a read/write file-system on the pendrive?

When your pendrive is mounted, please post the output of the terminal command
```
sudo fdisk -lu
``` and
```
df
```

I think that this information can help us solve your problem.

---

### Post by uhuru53 on 2011-11-26
> **sudodus said:**
> hi uhuru53

Do you run ubuntu in a live session from the usb pendrive? If that is the case, is it a regular live session or a persistent session (so that you are saving data in a read/write file-system on the pendrive?

When your pendrive is mounted, please post the output of the terminal command
```
sudo fdisk -lu
``` and
```
df
```

I think that this information can help us solve your problem.

I run ubuntu in a live persistent session from a 8GB pendrive, indeed I save my session whenever I shut down.

here the output of sudo fdisk -lu:

sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x283f283f

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204812684   102406311    7  HPFS/NTFS/exFAT
/dev/sda2       204828750   488392064   141781657+   7  HPFS/NTFS/exFAT

Disco /dev/sdb: 8495 MB, 8495562752 byte
64 testine, 32 settori/tracce, 8102 cilindri, totale 16592896 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x000a7743

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    16592895     8296432    c  W95 FAT32 (LBA)

and of df:

 df
File system         blocchi di 1K   Usati   Dispon. Uso% Montato su
/cow                   2035984   1919276     13284 100% /
udev                    504844         4    504840   1% /dev
tmpfs                   204896       812    204084   1% /run
/dev/sdb1              8280240   2779924   5500316  34% /cdrom
/dev/loop0              683136    683136         0 100% /rofs
tmpfs                   512232         8    512224   1% /tmp
none                      5120         0      5120   0% /run/lock
none                    512232       332    511900   1% /run/shm


If you may help me solving this without formatting the pendrive I'll be grateful! Many many thanks anyhow.

---

### Post by sudodus on 2011-11-26
> **uhuru53 said:**
> I run ubuntu in a live persistent session from a 8GB pendrive, indeed I save my session whenever I shut down.



 ```
df
File system         blocchi di 1K   Usati   Dispon. Uso% Montato su
[COLOR=Red]/cow                   2035984   1919276     13284 100% /[/COLOR]
udev                    504844         4    504840   1% /dev
tmpfs                   204896       812    204084   1% /run
/dev/sdb1              8280240   2779924   5500316  34% /cdrom
/dev/loop0              683136    683136         0 100% /rofs
tmpfs                   512232         8    512224   1% /tmp
none                      5120         0      5120   0% /run/lock
none                    512232       332    511900   1% /run/shm

```If you may help me solving this without formatting the pendrive I'll be grateful! Many many thanks anyhow.
The Italian text makes it a little hard to read but I try to understand. I think that the root file system [COLOR=Red]**/**[/COLOR] should not not be full and that may cause your problem. On the other hand there is plenty of space on /dev/sdb1 mounted on /cdrom. Is it writable (or readonly)? Maybe you can move some documents or other private files from **[COLOR=Red]/[/COLOR]** to /cdrom (which I think is a partition on your USB stick).

---

### Post by uhuru53 on 2011-11-26
Using Nautilus I see in / root folder only system files.
What could I move away to /cdrom?
btw /cdrom is the content I see in the pendrive when I open it using windows.

---

### Post by c.cobb on 2011-11-26
> **uhuru53 said:**
> I run ubuntu in a live persistent session from a 8GB pendrive, indeed I save my session whenever I shut down.

```
File system         blocchi di 1K   Usati   Dispon. Uso% Montato su
/cow                   2035984   1919276     13284 100% /
```

In a Live FS, the root dir is in RAM, vero? So increasing "lo spazio disponibile" means adding memory or some swap space.

---

### Post by sudodus on 2011-11-27
I agree with c.cobb. [COLOR=Red]***/***[/COLOR] is 'ram-drive'.

***Can you find /home and in /home can you find a directory (ubuntu? or some other name)? ***Are there files in there, documents etc, that can be moved to the free space on the usb drive? This would be the quick fix (help without formatting the pendrive).

If you are prepared to repartition and reformat your pendrive, one way would be to make a ***swap partition*** with gparted. The simplest (but not cheapest) method would be to ***buy more RAM if your motherboard can manage more*** (you seem to have 2 GB of 'ram-drive'. How much RAM is installed?

---

### Post by uhuru53 on 2011-11-27
> **sudodus said:**
> 
If you are prepared to repartition and reformat your pendrive, one way would be to make a ***swap partition*** with gparted. How much RAM is installed?

No, I am not prepared.
I have 1 Giga RAM.
Thanks anyway.

---

### Post by sudodus on 2011-11-27
> **uhuru53 said:**
> No, I am not prepared.
I have 1 Giga RAM.
Thanks anyway.
By the way, did you find any home directory and some files there to move?

---

### Post by sudodus on 2011-11-27
Obviously I was too quick to say that **[COLOR=Red]/[/COLOR]** (the file system) = RAM. It is RAM plus something else, maybe stored in a casper-rw file. Is there such a file on your USB pendrive?

/dev/sdb1 is mounted on [COLOR=Red]/cdrom[COLOR=Black] so look for such a file there!

One solution, that does not imply repartitioning would be to increase that [/COLOR][/COLOR]casper-rw file. But I'm afraid, that your customizing of the setup would get lost, unless we get **[COLOR=SeaGreen]help from someone with more experience[/COLOR] **than I have.

---

