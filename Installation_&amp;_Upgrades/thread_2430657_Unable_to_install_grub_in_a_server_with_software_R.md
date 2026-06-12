---
title: "Unable to install grub in a server with software RAID1"
date: 2019-11-05
forum: Installation &amp; Upgrades
---

### Post by mateovilar2 on 2019-11-05
I am trying to install an Ubuntu server 18.04 with a software RAID1. Everything seems to go fine until the step in which it tries to install grub. At this moment, it is not able to continue and the only way is to finish without boot manager. After the first reboot, you may see "gnu grub version 2.02" and grub>
I have tried to do the installation several times but I get always the same result.
Thank you in advance for your help.

---

### Post by oldfred on 2019-11-05
Do not know server.

But is install UEFI or BIOS. 
Is drive gpt or old MBR(msdos)?

If UEFI, you must have ESP - efi system partition for grub to correctly install. Best to use gpt.
If drive is gpt, you must have either ESP for UEFI boot or a bios_grub partition for BIOS boot.

---

### Post by SeijiSensei on 2019-11-05
Creating a separate /boot partition with some 512 M is an effective solution to this.  Let the machine boot from the primary drive then start the RAID array.  I have a couple of machines with large RAID1 mdadm arrays for which this method works flawlessly.  (I generally don't put the OS on the RAID either.  I use RAID for other filesystems like /home or a custom /data or similar mount point like, in my case, /media/raid.)

---

### Post by rsteinmetz70112 on 2019-11-05
It is possible to put the OS on a RAID 1 device, although a separate /boot partition is a good idea.

---

### Post by SeijiSensei on 2019-11-06
I know. On machines where I'm running a RAID array, I also have another drive which I make the primary device.

---

