---
title: "Installed Ubuntu but it keeps booting Windows 7"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2013-02-21
I got Windows 7 on a work laptop and I need to do some testing in Ubuntu. So I plugged in a flash drive, rebooted, ran the install and resized my partitions to 350 and 150. Everything installed fine, it rebooted and it automatically boots Windows 7, doesn't give me any Grub. I redid the install 3 times and every time it reboots right into Windows 7 without giving me any Grub option at any point. I have Quick Boot disabled, I can see the machine POST, but it still doesn't let me choose.

Never seen this before, any advice?

---

### Post by oldfred on 2013-02-21
Best to see details of what is where.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Maheriano on 2013-03-04
Thanks, you were pretty close.
Figured out the problem, this computer has a UEFI boot so I had to run the LiveUSB and do a boot repair with all recommended options. That gave me the Grub options and then I could boot into either Ubuntu or Windows.

---

### Post by zer010 on 2013-03-04
It seems that I'm definitely not the only one with this issue.  I don't have any Boot-info and such currently after my nth install. Will install Lubuntu 12.10 again tomorrow and gather the appropriate info.

---

### Post by zer010 on 2013-03-05
OK, installed Lubuntu 12.10 again. 
Also installed boot-repair in a Live session. 
Before running the repair option, here's the info link.
[http://paste.ubuntu.com/5589343/](http://paste.ubuntu.com/5589343/)

I'll run the repair later and post another info link.

---

### Post by zer010 on 2013-03-05
Ok, ran the boot-repair and it says everything went fine, we'll see after a reboot. Here's the info link it gave at finish.
[http://paste.ubuntu.com/5589373/](http://paste.ubuntu.com/5589373/)

---

### Post by oldfred on 2013-03-06
Even if you UEFI/BIOS has UEFI, your Windows & Ubuntu are installed in BIOS mode. So you should not boot anything in UEFI mode.

---

