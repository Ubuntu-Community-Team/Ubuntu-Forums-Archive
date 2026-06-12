---
title: "How to order SDA partitions"
date: 2019-03-15
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2019-03-15
After some "work" on my HDD and my Windows 10 enterprise I'm experiencing some booting issues with Ubuntu 18.04.2lts and I'm trying to identify the cause. Now I'd like to solve order SDA partition matter because I get "Partition table entries are not in disk order" advise when I run:
```

~$ sudo fdisk -l
[...]

Dispositivo     Start       Fine    Settori   Size Tipo
/dev/sda1     1024000    1228799     204800   100M EFI System
/dev/sda2     1228800    1261567      32768    16M Microsoft reserved
/dev/sda3   103561216  266242047  162680832  77,6G Microsoft basic data
/dev/sda4   286722048 1953523711 1666801664 794,8G Microsoft basic data
/dev/sda5     1261568  103561215  102299648  48,8G Linux filesystem
/dev/sda6   266242048  286722047   20480000   9,8G Linux filesystem

Partition table entries are not in disk order.
[...]

```
The "real" sda order is [1,2,5,3,6,4] and you can see it on attached gparted screenshot image.

Moreover as you can see there's 500MB unallocated space at the beginning of my HDD and I'd like to merge it to my last ntfs partition, I mean sda4 STORAGE. I think I can just run gparted within ubuntu live session and "shift/swap" all the other partitions until sda6 to cover the 500MB free space and then just resize sda4. Will be it so easy?

[This]("http://paste.ubuntu.com/p/pHV44tvxXj/") is my boot-repair report generated within ubuntu live session, I hope it'll help.

Thanks in advance.

---

### Post by oldfred on 2019-03-15
You show Windows hibernated, so will not be able to do anything. And the little key icons show mounted partitions, you cannot move mounted partitions, so have to use live installer.

But I would think twice before moving all your partitions. Each partition move will take a long time and any interruption will totally corrupt data. Or full back up drive required.
If you do move partitions, only use Windows to move NTFS partitions and immediately reboot into Windows to run chkdsk. Windows requires chkdsk after any resize.

That space probably was a Windows or vendor recovery partition, which if you have good backups is no loss. Better to just mount as another partition. Perhaps as a shared NTFS data partition do pass data from Windows to Ubuntu. But fast start must be off, or hibernation flag is set on all NTFS partitions.
       
Microsoft wants partitions in certain order and does not recommend moving.
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by gipsyshadow on 2019-03-15
Of course I'll use gparted in an ubuntu live session as I said (*"I can just run gparted within ubuntu live session"*), consider I posted gparted screenshot only to show the real sda partitions order :)
You can believe it or not but my win10 enterprise fast boot option is (and was) disabled. To show you this just look at the attached screenshot: though language isn't english you can see the 1^ entry box "Attiva avvio rapido" = "enable fast boot" is unchecked.

Ok, I won't move/shift partitions if it's so risky, just reorder sda in correct 1-6 sequence. And yes, I deleted windows recovery partition that was sda1.

So can you help me reordering partitions?

---

### Post by oldfred on 2019-03-15
Again order is not important on drive.
       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 
    
From this part of the site, you are not converting, but the comments on order should be heeded:
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
> The GPT partition numbers on a converted disk should match the partition numbers under Linux on the original MBR disk. For instance, if a disk had two primary partitions (1 and 3) and two logical partitions (5 and 6), you'll have the same partition numbers on the converted disk. This is perfectly legal for a GPT disk; however, some GPT disk utilities will sort these partition numbers and remove the gaps. You may then need to adjust your /etc/fstab and boot loader configurations. If you'd rather not suffer unexpected surprises, you can sort your partitions in gdisk with the s menu option from the start. You may still need to make /etc/fstab and boot loader changes, but at least you'll know to do this right away and not be taken by surprise by a utility that sorts the partition table but doesn't warn you about the need to make such changes.
  

---

### Post by gipsyshadow on 2019-03-16
I see. Just a last question: what about the fastboot/hibernation windows matter? I think it's strange to read the message
```

Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.

```
within that boot-repair report I linked above becasue I disabled fast boot. I guess hibernation and fast boot are 2 different things and I wonder if hibernation can bring issues to ubuntu booting but I couldn't find any about how to disable it. Am I on the wrong way this time too?

---

### Post by westie457 on 2019-03-16
To disable hibernation Windows open an 'Administrator Command Prompt'

Type in and run  ```
powercfg /h off
```
Exit the terminal

Not 100% sure sleep is disabled at the same time because I never use that function.

All of my sytems are either running or shutdown only.

---

### Post by oldfred on 2019-03-16
Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

