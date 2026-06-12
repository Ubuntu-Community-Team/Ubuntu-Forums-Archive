---
title: "ran MBRfix by mistake and cannot login to Ubuntu now"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by capricon on 2010-05-23
Hi,
I have a Ubuntu(Ubuntu 8.04 LTS)/Vista dual boot setup ( Single HDD machine) and Ubuntu was the default OS. While playing with an external HDD i accidentally ran MBRFIX  on my desktop HDD and now it boots directly into windows not showing grub menu.

Ran Ubuntu live CD and ran sudo fdisk -l and got the following result:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14179   113892192+   7  HPFS/NTFS
/dev/sda2           14180       24321    81465615    5  Extended
/dev/sda5           14180       23902    78099966   83  Linux
/dev/sda6           23903       24321     3365586   82  Linux swap / Solaris

```
**What do i do get my old grub setup back. Please help.**

By the way, i tried the following per forum but have issues:

```

grub> root (hd0,2)

Error 21: Selected disk does not exist

grub> 

```

---

### Post by oldfred on 2010-05-23
Instructions vary depending on whether you have grub legacy or grub2. Do not use the wrong set as that can make it worse.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

B

---

### Post by darkod on 2010-05-23
If you had a 9.10 or 10.04 clean install (not upgrade from previous version), just use the cd again to boot into live mode and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you had earlier version of ubuntu, you have grub1 and the procedure is different, so don't do the above.

---

### Post by capricon on 2010-05-23
Sorry, forgot to mentions i am using Ubuntu 8.04 LTS

---

### Post by capricon on 2010-05-23
> **oldfred said:**
> Instructions vary depending on whether you have grub legacy or grub2. Do not use the wrong set as that can make it worse.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

B

Thanks.

Hi went with "How to restore the Ubuntu grub bootloader (9.04 and older)" and getting the following problem:

```
grub> find /boot/grub/stage1

Error 15: File not found

grub> 
```

but i know "/boot/grub/stage1" exists in /dev/sda5.

---

### Post by albinootje on 2010-05-23
> **capricon said:**
> 
By the way, i tried the following per forum but have issues:

```

grub> root (hd0,2)

Error 21: Selected disk does not exist

grub> 

```

From the top of my head, please correct me if i'm wrong.

Boot from the ubuntu 8.04 install/live cdrom, fire up a terminal,
and do :
```

sudo mount /dev/sda5 /mnt
sudo chroot /mnt
mount /proc
cd /dev
MAKEDEV sd
grub-install /dev/sda
umount /proc
exit
sudo reboot

```

---

### Post by capricon on 2010-05-23
> **capricon said:**
> Thanks.

Hi went with "How to restore the Ubuntu grub bootloader (9.04 and older)" and getting the following problem:

```
grub> find /boot/grub/stage1

Error 15: File not found

grub> 
```

but i know "/boot/grub/stage1" exists in /dev/sda5.

My fault again, did not do 'sudo' before grub. Trying now the ""How to restore the Ubuntu grub bootloader (9.04 and older)"

---

### Post by darkod on 2010-05-23
The message about not finding stage1 is worrying me.

Otherwise, since you use grub1 and your root partition is /dev/sda5, you tried to repair with wrong root command. The commands should be like:

sudo grub
root (hd0,4)
setup (hd0)
quit
sudo reboot

But I'm not sure about the stage1 missing message.

---

### Post by capricon on 2010-05-23
i did 
sudo grub
root (hd0,4) (after running find /boot/grub/stage1)
setup (hd0)
quit
sudo reboot
 and it worked.
I did just grub instead of sudo grub and that was causing the problem.

Now  I want to say Big Thank you all replies here. Amazing helps. Once again i am proud to be a Ubuntu user.

Thank you all and i am marking it as solved.

---

