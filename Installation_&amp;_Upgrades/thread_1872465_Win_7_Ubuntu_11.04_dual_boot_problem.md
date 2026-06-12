---
title: "Win 7 Ubuntu 11.04 dual boot problem"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by tfbielawski on 2011-10-30
I have Ubuntu 11.04 and Windows 7 installed together. Ubuntu was first, Win 7 was second. 
 
After installing 7, I no longer had an option to boot into Ubuntu...no menu at all.
 
I followed advice on these threads and reinstalled Grub. That allowed me to boot into Ubuntu but there was no option for Win 7.
 
I repaired the Win 7 MBR and now have no option for Ubuntu. I'm going in circles. 
 
Clearly, I need to fix one or the other so that I have a complete boot menu but I don't know how.
 
Any help appreciated tremendously.
 
Thanks!!
 
Tom

---

### Post by garvinrick4 on 2011-10-30
After you get Ubuntu booting with its grub as you installed you have to:
```
sudo update-grub
```
in Ubuntu to put Windows in as a menu entry and in its config file.
Then both will boot.

---

### Post by tfbielawski on 2011-10-31
Thanks for the reply.
 
I've run sudo update-grub. 
 
Now what files do I need to edit, and how, in order to make it dual boot properly?
 
Thanks!
 
 
[www.tombielawski.com]("http://www.tombielawski.com")
[www.facebook.com/thechroniclesofllars]("http://www.facebook.com/thechroniclesofllars")

---

### Post by raja.genupula on 2011-10-31
Hi man ...look at my signature for Grub recovery and then after installing GRUB Customizor gonna give possibility to edit the GRUB your system.   

All the best.

---

### Post by tfbielawski on 2011-10-31
Raja,
 
I've recovered Grub. I will try your links and post back.
 
Thanks!
 
Tom
[www.tombielawski.com]("http://www.tombielawski.com")
[www.facebook.com/thechroniclesofllars]("http://www.facebook.com/thechroniclesofllars")

---

### Post by tfbielawski on 2011-11-01
Try and try again....I got it installed. But, I'm not sure what to make of it. It shows entries for Ubuntu, memtest, and for linux_xen. 
 
Thanks.
 
[www.tombielawski.com]("http://www.tombielawski.com")
[www.facebook.com/thechroniclesofllars]("http://www.facebook.com/thechroniclesofllars")

---

### Post by tfbielawski on 2011-11-01
Evem using the customizer, I cannot get Windows to load. 
 
[www.tombielawski.com]("http://www.tombielawski.com/") 
[www.facebook.com/thechroniclesofllars]("http://www.facebook.com/thechroniclesofllars")

---

### Post by lemming465 on 2011-11-01
Normally the grub installation process detects and configures windows partitions.  Could you describe your hardware a little, particular how many disks of what kinds?  Output from *sudo parted --list* would be helpful, for example.

We're assuming a fresh install of Ubuntu 11.04, which would be using grub2.

On the windows side, "EasyBCD" from Neosmart (free for personal use) might be able to find your Linux install when Windows owns the disk master boot record (MBR).

---

### Post by mvs1207 on 2011-11-01
Have you enabled GRUB_DISABLE_OS_PROBER?  Check your grub config file.
```
$ grep -i "GRUB_DISABLE_OS_PROBER" /etc/default/grub 
```

If the grep command outputs lines, make sure it **not** set to _true_

If GRUB_DISABLE_OS_PROBER is not enabled, then I guess grub is unable to find your Windows 7 partition or unable to find a bootable partition.  Can you check boot flags on your hard dist?  (assuming /dev/sda as your HD)
```
$ sudo fdisk -l /dev/sda
```

---

### Post by tfbielawski on 2011-11-15
> **lemming465 said:**
> Normally the grub installation process detects and configures windows partitions. Could you describe your hardware a little, particular how many disks of what kinds? Output from *sudo parted --list* would be helpful, for example.
 
We're assuming a fresh install of Ubuntu 11.04, which would be using grub2.
 
On the windows side, "EasyBCD" from Neosmart (free for personal use) might be able to find your Linux install when Windows owns the disk master boot record (MBR).
 
 
Easy BCD did the trick!!! Thank you!!! :D:D

---

