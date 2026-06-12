---
title: "can't boot in ubuntu after install"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by paul555 on 2007-08-20
Hi all i just installed ubuntu 7.04 in my computer with the cd i received from shipit.After i reboot it and select ubuntu to start it just get stuck in loading up and freeze.I reinstall it ok again but the same happens  :(.My computer has an athlon xp 2200 cpu 512 MB RAM geforce FX 5200 and a maxtor 80GB hd.Does anyone have an idea what can i do?

---

### Post by heimo on 2007-08-20
> **paul555 said:**
> Hi all i just installed ubuntu 7.04 in my computer with the cd i received from shipit.After i reboot it and select ubuntu to start it just get stuck in loading up and freeze.I reinstall it ok again but the same happens  :(.My computer has an athlon xp 2200 cpu 512 MB RAM geforce FX 5200 and a maxtor 80GB hd.Does anyone have an idea what can i do?

First thing I'd try is adding acpi=off and noapic to boot options, like this:
[http://ubuntuforums.org/showpost.php?p=151797&postcount=2](http://ubuntuforums.org/showpost.php?p=151797&postcount=2)

---

### Post by paul555 on 2007-08-20
I added acpi=off and noapic in kernel options but the result is the same :( .I noticed that when i did the install it did also an update and now i have 2.6.20-15-generic kernel installed while with 2.6.18-15-generic which i think is the default installed by the livecd it was booting fine.Any ideas?

---

### Post by heimo on 2007-08-20
> **paul555 said:**
> I added acpi=off and noapic in kernel options but the result is the same :( .I noticed that when i did the install it did also an update and now i have 2.6.20-15-generic kernel installed while with 2.6.18-15-generic which i think is the default installed by the livecd it was booting fine.Any ideas?

So you have only one kernel in Grub menu? If not, try others if you haven't already. I  think there's some key to show actual boot messages, esc, F1 or like that, so that you could see if there's any error or warning at the point where it freezes. That could help.

---

### Post by paul555 on 2007-08-20
I have only one kernel 2.6.20-15-generic in normal and recovery mode.Both modes are not booting and when i press F2 it shows nothing just the text starting up

---

### Post by paul555 on 2007-08-20
I booted again with the livecd and when i try to open my disk with cfdisk 
```
sudo cfdisk /dev/hda
``` i get this error regarding my root partition
```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
```
Any suggestions how to fix this?

---

### Post by heimo on 2007-08-20
> **paul555 said:**
> I booted again with the livecd and when i try to open my disk with cfdisk 
```
sudo cfdisk /dev/hda
``` i get this error regarding my root partition
```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
```Any suggestions how to fix this?

Doesn't sound promising. Try running 
```
fdisk -l
```
and give us output, if possible.

---

### Post by paul555 on 2007-08-20
I started again the installation deleted the root and swap partition and now cfdisk /dev/hda works.Here is the output
```
# fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6343    50950116    7  HPFS/NTFS
/dev/hda2            6344        9784    27639832+  83  Linux
/dev/hda3            9785        9964     1445850    5  Extended
/dev/hda5            9785        9964     1445818+  82  Linux swap / Solaris

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           2        2550    20474842+   f  W95 Ext'd (LBA)
/dev/hdc2            2551       38913   292085797+   7  HPFS/NTFS
/dev/hdc5               2        2550    20474811   83  Linux
```
and 
```
                                  cfdisk 2.12r

                              Disk Drive: /dev/hda
                        Size: 81964302336 bytes, 81.9 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9964

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1        Boot        Primary   NTFS             []              52172.96 
    hda2                    Primary   Linux ext3                       28303.19
    hda5                    Logical   Linux swap / Solaris              1480.56




     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

```
But the installation frozen at 74% when it was copying the files.Now i will try again

---

### Post by heimo on 2007-08-20
> **paul555 said:**
> I started again the installation deleted the root and swap partition and now cfdisk /dev/hda works.

I'm not sure if I understand. Did you reinstall? Is the same problem - freezing at the beginning of boot - still there?

---

### Post by paul555 on 2007-08-20
Finally i did it i install ubuntu :) .I just  deleted the /dev/hda6 (my previous root partition) and created a new one as /dev/hda2 and i did the install ok.Now i have problem with gnome.When i first login i got a message that there is a panel already running and when i click ok the current died and i had and empty desktop.Since then the same happens every time i log on to gnome so i ```
apt-get install xfce4
``` and now i am using xfce and do the updates

---

