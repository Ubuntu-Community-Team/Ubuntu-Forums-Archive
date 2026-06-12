---
title: "GRUB error 21"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by Cyberapoc on 2007-06-25
Dear everyone,

I installed Feisty Fawn on my notebook a while back and wanted to do the same for my desktop (one harddisk), since I really hate windows vista.

It didn't work as planned though. The Ubuntu install went very smootly, but I just couldn't get GRUB to recognize the hard disk and got an error 21 every boot.

I did a dual boot with vista for starters, and the migration manager recognised vista. Furthermore: I had to install this version of Ubuntu since previous kernels didn't recognise my quite new ECS motherboard with dual core support (RAID controller). Perhaps my current problem has something to do with this?

I tried to solve the problem by changing my HD settings in CMOS to manual and LBA and I reinstalled GRUB on my master boot record with chroot. Both did nothing to solve the problem.

I would really appreciate any help, since I am quite eager to make the step from windows to linux/ubuntu, because I just love the simplicity and efficiency of it.

Thanks in advance

Kevin

---

### Post by Pumalite on 2007-06-25
Ubuntu 7.04 has a problem with Raid arrays, as do all other distros. There is a way to get around this: look in Ubuntu.com/Documents/FakeRaid. In the meantime, read this:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

What Raid are you using? 0 or 1?

---

### Post by Cyberapoc on 2007-06-25
To be honest, I am not quite sure which RAID it is...

How do I find out?

Thanks for your answer, will read the link now.

---

### Post by Pumalite on 2007-06-25
If you don't know which Raid it is, you are better of without Raid. You'll have less problems with Linux: now and in the future. Raid 0; the improvement in performance is minimal. Raid 1; it's like using suspenders and a belt. You can disable it in BIOS, I think.

---

### Post by Cyberapoc on 2007-06-26
EDIT: Ok, when I enter RAID setup it says I don't even have a RAID HDD and RAID is disabled. The controller in BIOS was already set on IDE. Does anyone know how it is then possible that I get an error21?
Original message follows
----------------------------------------------------------------------------------------------------------------------------------

I think RAID was already disabled or I am not sure whether it will work if I install Ubuntu next time...

I tried the fake RAID guide and of course had some problems. dmraid failed, so I followed the guidelines on the fakeraiddebug. 

This is the result:

ubuntu@ubuntu:~$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdc
NOTICE: skipping removable device /dev/sdb
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
No RAID disks
WARN: unlocking /var/lock/dmraid/.lock
ubuntu@ubuntu:~$ sudo dmraid -b
/dev/sda:    488397168 total, "3QE0B27S"
ubuntu@ubuntu:~$ sudo dmraid -rD
No RAID disks
ubuntu@ubuntu:~$ sudo fdisk -u -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    61442047    30720000    7  HPFS/NTFS
/dev/sda2        61442048   471042047   204800000    7  HPFS/NTFS
/dev/sda3       471057930   488392064     8667067+  83  Linux
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=outputfile skip=488395168
2000+0 records in
2000+0 records out
1024000 bytes (1.0 MB) copied, 0.0374864 seconds, 27.3 MB/s
ubuntu@ubuntu:~$ 

See also the attached file. 

I hope someone is able to help, thanks in advance.

Kevin

---

### Post by Pumalite on 2007-06-26
I'm out of my depth here. Someone else will have to jump in.

---

### Post by Cyberapoc on 2007-06-26
Thanks for your help anyway, much appreciated!

---

### Post by Cyberapoc on 2007-06-26
I just found out that it might have something to do with my JMicron... 

Does anyone have any knowledge which will help me?

thanks in advance

---

### Post by Herman on 2007-06-26
Okay, I normally don't touch threads with the word 'RAID' in them, but since you are waiting without help, try this link and see if it helps you at all, [     Grub error 21]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21").
Regards, Herman :D

Pumalite, thanks for that info, I like it, I'm inclined to agree with that, 
> If you don't know which Raid it is, you are better of without Raid. You'll have less problems with Linux: now and in the future. Raid 0; the improvement in performance is minimal. Raid 1; it's like using suspenders and a belt. You can disable it in BIOS, I think. I don't know anything about RAID, but I do know that GRUB is supposed to support it, here's a link to the GRUB Wki about it, [http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID), if that's any help.
Regards, Herman :D

---

