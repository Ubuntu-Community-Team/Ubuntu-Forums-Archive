---
title: "Grub No Such Device"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by ]SK[ on 2014-04-03
Hi all, 

I did a fresh install of Windows 8.1 then an install of Ubuntu Gnome.  After install though rebooting gives me the error in the title.  Being new to the Linux I have no idea where to go now :(

SDA is my SSD where Windows resides
SDB is 3TB, 2.5TB allocated as an NTFS partition for my Windows data.  The remaining 500GB is where I installed Ubuntu.

```
ubuntu-gnome@ubuntu-gnome:~$ sudo parted /dev/sdb unit s print
Model: ATA TOSHIBA DT01ACA3 (scsi)
Disk /dev/sdb: 5860533168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system     Name                          Flags
 1      34s          262177s      262144s                      Microsoft reserved partition  msftres
 2      264192s      4883820885s  4883556694s  ntfs            Basic data partition          msftdata
 3      4883822592s  4883824639s  2048s                                                      bios_grub
 4      4883824640s  5843791871s  959967232s   ext4
 5      5843791872s  5860532223s  16740352s    linux-swap(v1)

```

```
ubuntu-gnome@ubuntu-gnome:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Apr  3  2014 1252642852641331 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr  3  2014 2E74-B2F0 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Apr  3  2014 3ADC775EDC7712FD -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr  3  2014 4b943951-769a-425a-bc7b-6128f1b84e3e -> ../../sdb4
lrwxrwxrwx 1 root root 10 Apr  3  2014 7e30c4e3-ad09-4684-8895-2e9c68775932 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Apr  3  2014 DE72DD5472DD324F -> ../../sdb2

```

```
ubuntu-gnome@ubuntu-gnome:~$ blkid
/dev/sda1: LABEL="System Reserved" UUID="1252642852641331" TYPE="ntfs" 
/dev/sda2: UUID="3ADC775EDC7712FD" TYPE="ntfs" 
/dev/sdb2: LABEL="Data" UUID="DE72DD5472DD324F" TYPE="ntfs" 
/dev/sdb4: UUID="4b943951-769a-425a-bc7b-6128f1b84e3e" TYPE="ext4" 

```

Doesn't seem to like sdb3?

---

### Post by oldfred on 2014-04-04
The bios_grub is normally not shown as it is unformatted. Same with Windows msftres. Both are just spaces reserved to write info. That space is not available in gpt partitioned where with MBR(msdos) you have the sectors after the MBR or first sector until the first sector of first partition which is now usually sector 2048. 

Do you have drives in AHCI mode not IDE nor RAID?

Post this from live installer.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Do not run auto fix with Boot-Repair. It just installs grub to all hard drives, and you actually want Windows boot loader in MBR of SSD and grub in MBR of hard drive.

---

### Post by ]SK[ on 2014-04-04
Ah thank you.  Well, I ran the tool and attempted to repair Grub but it still failed.   I saw the option to fix mbr so took my changes and indeed it's fixed booting back into Windows.  
Strangely this exercise has pointed out that I am using IDE and not AHCI.  Being that it would be wise to switch to make the most of my SSD I will need to reinstall both OS's tonight (if [this]("http://superuser.com/questions/471102/change-from-ide-to-ahci-after-installing-windows-8") registry value change doesn't work).  Maybe using AHCI will fix the issues I am seeing currently in the legacy IDE mode?

---

### Post by oldfred on 2014-04-04
I got my SSD a couple of years ago and for trim to work you have to have AHCI mode not IDE. But then my XP did not work as it does not have drivers. It would have been a total reinstall of XP and I had been wanting to stop using XP but had one app I kept using. It finally forced me to shutdown XP. :)

But newer Windows have the drivers and you should be able to install them easily before changing to AHCI in BIOS. Some Windows already have driver and change just works.

My Ubuntu install worked whether IDE or AHCI mode in BIOS. And I was able to go back and turn on IDE to boot into XP, but that became such a hassle it was time to kill XP.

---

