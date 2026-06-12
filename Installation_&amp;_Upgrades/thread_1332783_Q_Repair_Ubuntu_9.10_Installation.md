---
title: "Q: Repair Ubuntu 9.10 Installation"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by noloader on 2009-11-20
Hi All,

I use Clonezilla (LiveCD) to keep copies of various OS's on a separate (local) drive since I don't have hardware for a decent VM. Os's include XP, Vista, Debian, Mandriva, and Fedora. Ubuntu is the one OS that continually gives me problems. For whatever reason, Clonezilla can't always restore Ubuntu.

The setup described above is fairly straight forward: the first drive is 40 GB, and the installed OS (Ubuntu, XP, Debian, etc) gets to do what it wants with the drive. For all Linux installs, the drive is logically laid out as follows (in the exact order listed):
* /boot - 256 MB
* / - 16 GB
* swap - 2GB
* /home - remaining

For Ubuntu only (and only after a restore), I sometimes find myself at a GRUB prompt with a message similar to "Error 8: can't find the kernel". I've tried 'find /boot/grub/stage1' and various other methods from [1, 2]. I usually get an "Error 15: file not found". This has turned into an exercise in futility due to my lack of Linux/System/Lilo/Grub skills.

In the past, I've reinstalled Ubuntu when I needed to look at the specific OS behavior because of this issue. I'm now faced with my 4th re-installation, and would like to find another way to go about this. It's kind of absurd to perform a 4 hour reinstall (with patching) for a 10 minute question.

How do I initiate a 'Repair Installation' from the LiveCd? I am confident the file system described above is present. I've cycled through the options (F4, F6, etc) and damn if I can find it.

Thanks,
Jeffrey Walton

[1] [http://ubuntuforums.org/showthread.php?t=596](http://ubuntuforums.org/showthread.php?t=596)
[2] [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by darkod on 2009-11-20
If you are using 9.10 then you are using grub2 and not grub1. stage1/stage2 don't exist any more.
Plus, grub2 started using UUID identifiers for the disk partitions which change with each format of the drive. I am only guessing but I think that's the main problem.

Grub2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by noloader on 2009-11-20
Hi darkod,

After following a few links, I landed at [1] which stated the following: "This error is the result of a GRUB 2 installation to /boot but a Master Boot Record  MBR) which still contains Grub legacy. This can happen if you don't select your drive when running **sudo update-from-grub-legacy**." For the record, I did not run that command.

$ sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        1525    12000555   83  Linux
/dev/sda3            1526        2023     4000185   82  Linux swap / Solaris
/dev/sda4            2024        4865    22828365   83  Linux

OK. Everything is there as expected. Next, I used Palimpsest (Disk Utility) to add a label (boot) to the boot partition. Palimpsest shows that /dev/sda1 is mounted at /media/boot. I then click on 'boot' from the Places menu to force a mount. A quick check:

$ sudo ls /media
boot

Per the webpage [1], run the following with XXXX replaced with the mount point:
sudo grub-setup -d /media/XXXX/boot/grub /dev/sda

OK:
$ sudo grub-setup -d /media/boot/boot/grub /dev/sda
grub-setup: error: Cannot open `/boot/grub/device.map'

Hmm...
$ ls /media/boot/grub/device*
/media/boot/grub/device.map

OK. Per the webpage [1], run the following due to the 'device.map' error:
$ sudo grub-setup -d /media/boot/boot/grub -m /media/boot/boot/grub/device.map /dev/sda
grub-setup: error: Cannot open `/media/boot/boot/grub/device.map'

Just for ***** and grins:
$ sudo grub-setup -d /media/boot/grub -m /media/boot/grub/device.map /dev/sda
ubuntu@ubuntu:~$ 

Whoops. It seems to have worked (I won't know until reboot), but its not in the instructions.

 In the one hour since I posted, I've been down 4 dead ends while 5 others have posted boot problem questions. Perhaps the maintainers should add the ability to perform a directed repair or mbr/grub reinstallation. This is a royal pain in the ***, I did not issue the update-from-grub-legacy, and others are having the problem.

Jeff

[1] [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by noloader on 2009-11-20
> Whoops. It seems to have worked (I won't know until reboot),
It worked.

Jeff

---

