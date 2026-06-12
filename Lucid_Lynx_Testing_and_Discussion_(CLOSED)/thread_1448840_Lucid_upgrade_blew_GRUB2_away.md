---
title: "Lucid upgrade blew GRUB2 away"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pikkio on 2010-04-07
Hi folks,
I'm on a **MacBookPro5,5** (13").
Recently I installed Karmic (in dual-boot through **rEFIt**) from the Desktop CD and all went fine.
Today I decided to upgrade to Lucid and unfortunately it failed on the **grub-pc** configuration.

A little resume of the situation.

* My disk is partitioned in the following way:

```
/dev/sda1 (type: FAT32)   --> EFI System (FAT)
/dev/sda2 (type: HFS+)    --> Mac OS X HFS+
**/dev/sda3 (type: Unknown, boot code: GRUB, size: ~1Mb) --> GRUB2 BIOS Boot**
/dev/sda4 (type: ext4)    --> Linux (mount: /)
/dev/sda5 (type: Unknown) --> Linux Swap
/dev/sda6 (type: ext4)    --> Linux (mount: /home)
```

Now, the /dev/sda3 should be a BIOS Boot Partition [1]; it was created by the Karmic Live CD Installation app, as I followed the tutorial [2] on the wiki.
In detail, I've used the "install to the largest continuous free space" option. Then, I've added later the sda6 partition for the /home mount, during a subsequent installation process, and I installed GRUB on **/dev/sda3** as suggested.

Everything went pretty fine, on Karmic.

* Then, I did 'update-manager -d' and at the end of the process I got:
```
Setting up grub-pc (1.98-1ubuntu3) ...
Installing new version of config file /etc/grub.d/05_debian_theme ...
/usr/sbin/grub-setup: error: unable to identify a filesystem in hd0,3; safety check can't be performed.
```

* Of course, now GRUB fails on start ("grub_puts_" not found, or similar) and I'm only able to reach an incomplete grub-recovery command line. It seems I'm not the first having this issue [3].

* When I try to recover GRUB from the Karmic Live CD (using the chroot environment, as suggested in [4]), I got the same error message as before:

```
# grub-update
[...]
# grub-install /dev/sda3
[...]
/usr/sbin/grub-setup: error: unable to identify a filesystem in hd0,3; safety check can't be performed.
```


I would appreciate any ideas from more experienced Mac users. I'm not familiar with the GPT system at all.

Thanks in advance.
___

[1] [http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[2] [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu)
[3] [http://ubuntuforums.org/showpost.php?p=9075220&postcount=5](http://ubuntuforums.org/showpost.php?p=9075220&postcount=5)
[4] [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by linuxopjemac on 2010-04-07
Sounds like this:
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

### Post by pikkio on 2010-04-07
Hi, thanks for the reply.
I do not think that is the issue I'm experiencing, 'cause after my Karmic installation (before the firs boot) I checked the disk with the rEFIt tool and the partitions were already perfectly synced.
In fact, Karmic has been booting nicely. My problems started with the upgrade to Lucid.
I think the problem is with GRUB and a poorly documented installation on a GPT disk.
(I don't want to install GRUB directly on /dev/sda, as I want to keep rEFIt as the main dual-boot chooser).

---

### Post by linuxopjemac on 2010-04-07
see also here:
[http://wiki.debian.org/MacBook#line-240](http://wiki.debian.org/MacBook#line-240)

---

### Post by linuxopjemac on 2010-04-07
I don't have that 1Mb parition of unknown type, as I started from 8.10 and installed 9.10 over it (I have 4 partitions /dev/sda1 is EFI, /dev/sda2 is HFS+, /dev/sda3 is Linux root, /dev/sda4 is swap). Maybe you can delete said /dev/sda3 and try to put GRUB2 on / (root, now /dev/sda4). After backup of course. Or you might want to consider to delete /dev/sda2-6 and make one empty partition and install Lucid from scratch.

Just an idea.

---

