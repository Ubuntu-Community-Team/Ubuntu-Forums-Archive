---
title: "Grub Rescue Problem"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by nmoyefelix on 2011-06-27
I newly install Lucid 10.04, had problems after updating so I thought re-installing will solve it. I went to my windows environment and deleted the partition using Easeus, and was to reboot. Upon reboot,I had a blanck screen with the following message

Error: no such partition
Grub rescue>

Please how do I resolve this problem. I am a Newbie.
Felix

---

### Post by nzjethro on 2011-06-27
> I went to my windows environment and deleted the partition using Easeus, and was to reboot. Upon reboot,I had a blanck screen with the following message

After removing your Ubuntu partition, did you reinstall Ubuntu? You say you removed it, but did you reinstall it into the empty partition you created?

---

### Post by YesWeCan on 2011-06-27
Hi there. The problem is that Grub boot code cannot find files it needs in the Ubuntu partition, because the partition no longer exists. To fix this you need to reinstate the standard MBR code.
You can either boot your Windows CD and run a utility to fix the MBR or you can boot a Ubuntu live CD/USB and use Lilo to do this:
[COLOR=DarkGreen]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr [/COLOR] (assuming your Windows disk is named sda - check in System/Admin/Disk Utility).

---

### Post by Quackers on 2011-06-27
You removed Ubuntu but left grub in the mbr of the hard drive. Grub can't find its files now.
If you re-install Ubuntu the matter will resolve itself. After installation run sudo update-grub and your Windows boot option should re-appear.
Make sure you don't over-write a Windows partition when re-installing! That would be bad!

---

### Post by nmoyefelix on 2011-06-27
Thanks guys, I really appreciate you all. I will do as told.

---

