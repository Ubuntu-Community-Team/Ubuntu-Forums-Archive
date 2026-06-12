---
title: "Whoops - where is grub?"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by bigalxyz123 on 2011-06-11
Hello forum,

I have a Toshiba Satellite Pro laptop, about 2 years old.

For some time it has been running in a dual-boot configuration, Windows 7 and Ubuntu (currently 11.04).

My Windows partition started to have lots of problems - slow running, crashing, updates not installing, etc. so I decided to reinstall W7 from scratch.  At the moment it's running fine.  Unfortunately the grub bootup screen has disappeared - the laptop just boots up to Windows now, and that's that.  I can't run Ubuntu and I can't access the Ubuntu partition from Windows (in order to retrieve some important files).

HELP!  Is there a simple solution to this problem?

Many thanks,

Alan.

---

### Post by wojox on 2011-06-11
Easiest way I've found is to reinstall Grub2 from a [Live-CD]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files")

---

### Post by Quackers on 2011-06-11
Yes, you can boot from the live cd and select "try Ubuntu" then re-install grub to the mbr of the hard drive.
First you will need to identify which partition is your Ubuntu root partition. You can do that by opening gparted or by running in the terminal ```
sudo fdisk -l
``` That's a lower case L not a 1.
Once you have identified your Ubuntu root partition you can run the following commands in the terminal - substituting your partition instead of /dev/sdXY (for example /dev/sda5) and your drive by changing /dev/sdX in the second command (eg if your root partition is /dev/sda5 then your drive would be /dev/sda).
```
sudo mount /dev/sdXY /mnt  
sudo grub-install --root-directory=/mnt /dev/sdX
``` If no errors are reported you can reboot and Ubuntu should boot directly.
If so, open a terminal and run ```
sudo update-grub
``` when you should see the Windows Loader recognised as grub.cfg is run.

---

### Post by FreymanX on 2011-06-11
Heres what I would do. I would burn a CD with Ubuntu 10.04

Then I would restart my PC and press F12 to go boot up with CD

I would make your computer all Linux

Download an .ISO Image of Windows 7 and burn it to a CD a repeat step 2

Then finally start over and dual boot all over again.

---

### Post by wojox on 2011-06-11
> **FreymanX said:**
> Heres what I would do. I would burn a CD with Ubuntu 10.04

Then I would restart my PC and press F12 to go boot up with CD

I would make your computer all Linux

Download an .ISO Image of Windows 7 and burn it to a CD a repeat step 2

Then finally start over and dual boot all over again.

What???

---

### Post by MARP1961 on 2011-06-12
Download an iso. image of Windows 7? Have I missed something?

---

### Post by bigalxyz123 on 2011-06-12
@wojox/Quackers - many thanks - that worked nicely.  Root partition was /dev/sda6.  The only slightly unexpected thing is that I didn't need to do the final 'sudo upgrade-grub' command because upon the first reboot, the full grub screen reappeared, as if by magic, exactly as it was before.

Regards
Alan

---

### Post by Quackers on 2011-06-12
Yes, update-grub is run during the process. The guide says that it may not be necessary to run it :-)
Glad everything is working now :-)

---

