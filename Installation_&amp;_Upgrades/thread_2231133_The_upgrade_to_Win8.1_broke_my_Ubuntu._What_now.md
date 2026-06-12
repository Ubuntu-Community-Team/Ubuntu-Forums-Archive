---
title: "The upgrade to Win8.1 broke my Ubuntu. What now?"
date: 2014-06-23
forum: Installation &amp; Upgrades
---

### Post by Sosippus on 2014-06-23
Hello Linux gurus. I am trying to get linux back running on my laptop that has Win8. 

It used to run before I upgraded to Win8.1 but now, whenever I choose Linux in the boot menu it just returns some messages saying that it failed to mount. The errors are the following:

[http://i.imgur.com/dK90sAa.jpg](http://i.imgur.com/dK90sAa.jpg)
(Sorry for the crappy pic)

I then tried to boot Ubuntu from a USB drive to recover it. However, Ubuntu never loads and either: freezes in a blank screen with a blinking _  or loads Win8 instead if I boot from a Ubuntu DVD. *(I took care to see the boot priorities in BIOS)* Running Boot-repair from a LiveUSB rendered **both** OS unusable. Neither of them loads. The logs of the repair, and of a repair done again (yes, I'm desperate) are in here:

[http://paste.ubuntu.com/7691026/](http://paste.ubuntu.com/7691026/)
[http://paste.ubuntu.com/7691350/](http://paste.ubuntu.com/7691350/)

This allowed me to see Grub:

> GNU GRUB version 2.00-13ubuntu3
> Minimal BASH-like line  editing is supported. For the first word, TAB lists possible command  completions. Anywhere else TAB lists possible device or file  completions.

though this is not exactly the linux environment, it is a step towards it right? :) 

Note that Boot-Repair is selecting /sdb in *Restore the MBR of: sdb (generic mbr)*. I have no other option to choose in here besides others for sdb, *although linux is installed in sda3, sda5 and sda6 as you can see from this screen*
[IMG]http://i.imgur.com/8vodw7N.jpg[/IMG]

Is there any way to recover it Ubuntu and Win8? I'm afraid that if I run the automatic recover of Win8 everything will be back as it was before. How can I solve these problems?

I appreciate all the help

---

### Post by Bucky Ball on 2014-06-23
Rub boot repair>Advanced Option>Replace MBR
Reboot. Can you boot Win? If so,
Run boot repair>Recommended Repair
Reboot. Do you get the grub menu? If so,
Are all entries present and correct and do they boot?

This combination worked for me last night when I was in the same situation as you are now. Hope it helps you, too.

---

### Post by fantab on 2014-06-23
Upgrade to Win8.1 from Win8 almost always breaks Grub. The simplest soultion is to re-install Grub (bootloader).
There are two ways to do it: 1. [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") utility and 2. [Reinstalling Grub from Live Ubuntu]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")

---

### Post by Sosippus on 2014-06-24
> **Bucky Ball said:**
> Rub boot repair>Advanced Option>Replace MBR
Reboot. Can you boot Win? If so,
Run boot repair>Recommended Repair
Reboot. Do you get the grub menu? If so,
Are all entries present and correct and do they boot?

This combination worked for me last night when I was in the same situation as you are now. Hope it helps you, too.
Well, I came to the conclusion that Boot Repair is selecting the boot partition wrongly. When I click advanced it shows that the boot partition is sdb2, but if you look at my gparted screenshot, both partitions in sdb are NTFS so linux can't be in one of them. I have no idea why sdb2 is even flagged as boot... Either way, it seems like boot repair isn't going to help me much.

> **fantab said:**
> Upgrade to Win8.1 from Win8 almost always breaks Grub. The simplest soultion is to re-install Grub (bootloader).
There are two ways to do it: 1. [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") utility and 2. [Reinstalling Grub from Live Ubuntu]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")
Please see my reply above. I was also looking into your option number 2.

Some more new information: yesterday I was following the first reply [in this thread]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported?rq=1"), and it turns out that when I do the first things under "Windows 8 + Ubuntu" I get the message pertaining to being able to regularly install ubuntu alongside win8 with no big problems. Now whether something will happen to Grub later, I don't know... So, overall, and given the problem in selecting the correct boot repair partition,, I think I'll just try to delete sda3, sda5 and sda6 using windows and have Win8.1 on sda, and then install Ubuntu on sdb. Does this sound good?

---

### Post by LastDino on 2014-06-24
Why do you want to get rid of the working Ubuntu install and do it again? I don't really get it tbh. When fixing grub is of 2 min job.

Boot into your Live Ubuntu DVD/USB
Mount the partitions and drive where Ubuntu is installed.
 ```
sudo mount /dev/sdXY /mnt
```
Then simply install the thing?
  ```
      sudo grub-install --root-directory=/mnt /dev/sdX

```

Then see if you can get into grub.

Where /dev/sdX is the disk where Ubuntu is installed, and /dev/sdXY is the partition on the disk where Ubuntu is installed. In other words, /dev/sdXY contains /boot and so on.

Use fdisk -l to verify the Ubuntu installation location.

If this is not what you want then pardon me.

---

### Post by Sosippus on 2014-06-24
> **LastDino said:**
> Why do you want to get rid of the working Ubuntu install and do it again? I don't really get it tbh. When fixing grub is of 2 min job.

Boot into your Live Ubuntu DVD/USB
Mount the partitions and drive where Ubuntu is installed.
 ```
sudo mount /dev/sdXY /mnt
```
Then simply install the thing?
  ```
      sudo grub-install --root-directory=/mnt /dev/sdX

```

I tried that using sda5. I was trying to install grub again, but it couldn't find the correct folders in the linux installed partition. I assumed that there was something that broke Ubuntu altogether. However...

> **LastDino said:**
> 
Use fdisk -l to verify the Ubuntu installation location.
If this is not what you want then pardon me.
...I have not tried this. Yes, it is what I wanted :) I will give it a try and post back the details later. Thanks

---

### Post by LastDino on 2014-06-24
You should see asterisk symbol where your install is under boot column in output of that command. I'm looking at your initial screen shot though and sd2 looks like has boot, so look if you find something other than that. 

Did you even install any Windows OS there?

---

### Post by Sosippus on 2014-06-24
I honestly have no idea why sdb2 is flagged boot. This is the second partition of an harddrive that has nothing there... just some windows images backups, done by the default windows utility and some other program. Other than that, I don't recall doing anything else there.

I only have one Windows installed, and this should be in sda2.

---

### Post by mastablasta on 2014-06-24
it could be that's it's a recovery patition. e.g. something goes wrong you direct the PC to boot from recovery instead of main partition.

---

### Post by Bucky Ball on 2014-06-24
Boot Repair>Advanced Options>Grub Location. Put grub where you want it ...

sda is normal. The reason it is showing sdb is because you have a USB plugged in that is being assigned sda, perhaps? If this is the case, follow the above and put the grub on sdb.

---

### Post by oldfred on 2014-06-24
Understand boot flag is a Windows (and Lilo) convention to know which partition is bootable. MBR scans partition table for boot flag to know which partition to find more Windows boot code. This is after you set in BIOS which drive to boot from and have a boot flag on the Windows partition with boot files. If just a data drive boot flag is not quired.


Grub does not use a boot flag and whatever partition you use to boot with grub does not need boot flag. BIOS/MBR can boot a partition on another drive when using grub.

There are a few BIOS (mostly Intel) that will not even let you start to boot without a boot flag on a primary partition, so we still suggest a boot flag on a primary partition.

---

