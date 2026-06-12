---
title: "GRUB issues"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by Sisophon2001 on 2010-09-06
I have Ubuntu 10.04 as my main install, and I decided to temporally install kubuntu 10.04 on the same hard disk to check it out. Now I find my grub boot menu is controlled by the Kubuntu install, and I want to reset it to Ununtu so I can eventually remove or replace Kubuntu.

I tried following the instructions here [http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708") for 9.10 or greater, but I ended up with a grub prompt and the only way I could get my computer working again was to re-install Kubuntu. I did this twice before deciding it was time to ask for help.

sudo fdisk -l
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000849c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34336   275796028+  83  Linux
/dev/sda2           34336       38914    36772865    5  Extended
/dev/sda5           38182       38914     5881856   82  Linux swap / Solaris
/dev/sda6           34336       38017    29571072   83  Linux
/dev/sda7           38017       38182     1318912   82  Linux swap / Solaris

Partition table entries are not in disk order

```

/dev/sda1 is my main partition for Ubuntu with 282 GB formatted as ext4
/dev/sda5 is my swap file for Ubuntu 6GB
/dev/sda6 is my main partition for Kubuntu with 30 GB formatted as ext4
/dev/sda7 is my swap file for Kubuntu 1.4GB

/dev/sda2 is an extended partition containing sda5, sda6 & sda7

How do I move the grub loader from Kubuntu to ubuntu?

Thanks for any help,

Garvan

---

### Post by Rubi1200 on 2010-09-06
Hi,
boot into Kubuntu and remove grub-pc and grub-common:

```
sudo apt-get purge grub-pc
``````
sudo apt-get purge grub-common
```
This will leave the computer unable to boot but don't freak out.

Now, boot the computer with the Ubuntu CD in live mode and run the following commands:

```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Reboot the computer and in Ubuntu run ```
sudo update-grub
```Finished.

---

### Post by Sisophon2001 on 2010-09-06
Thanks Rubi1200, it worked perfectly, just as you described.

Garvan

---

### Post by Rubi1200 on 2010-09-06
You are more than welcome :)

If, when you decide to remove Kubuntu, something goes wrong (which should not happen), just follow the instructions to reinstall GRUB to sda1 and sda.

---

