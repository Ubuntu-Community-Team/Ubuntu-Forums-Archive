---
title: "Problem with Windows 7 bootloader and Grub2"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Dlizzz on 2010-03-25
Hi There,

I've Windows 7 x64 installed on a raid 0 (hd0, /dev/sda & /dev/sdb for Ubuntu) from where I boot using Windows bootloader.
I've just installed Karmic amd64 on a new disk (hd1, /dev/sdc for Ubuntu) with Grub2 on /dev/sdc.
When I change the boot disk in the Bios, Karmic is booting fine with Grub2. The problem is when I try to boot Karmic from the Windows bootloader.
I've dumped Grub2 bootsector (dd if=/dev/sdc of=/media/Windows bs=512 count=1) and stored it on hd0 root.
I've created the correct entry in BCD (using BCDedit) pointing to the bootsector dump.
When I boot from hd0, the Windows bootloader starts, showing the Ubuntu line and when I select it, Grub2 starts (so I'm pointing to the right dump) but freeze (I have a black screen with GRUB written at the top and the cursor blinking). It seems that the bootsector is corrupted.
I have tried sevral times, with Karmic disk formated with ext3 or ext4, always the same result !
I don't want to use Grub2 as bootloader for Ubuntu & Windows 7 because W7 is on a raid0. So, I still stick to have Windows bootloader working...

Any idea?

Thanks !

---

### Post by Mark Phelps on 2010-03-25
Sounds like you're having problems with getting EasyBCD to do what you want.

You would do better posting your questions to the EasyBCD forums, located at NeoSmart Technologies.

They have tutorials, are better equipped to answer BCD-related questions, and you won't get hit with a spate of responses about how you SHOULD be doing all of this with GRUB.

---

### Post by Dlizzz on 2010-03-25
I'm not using EasyBCD. I'm using BCDEdit to modify Windows 7 bootloader.
And as far as I can see, the Windows Bootloader does its job fine. It correctly calls the Grub2 bootsector because I can see Grub2 starting... The problem is after when Grub2 starts and then freezes.

---

### Post by oldfred on 2010-03-25
Booting from a drive and from the raid may change the drive numbering.
Typical grub entry has set root=(hd0,1) for drive and partition, but if you change to boot from raid does the hd? number change?

---

### Post by norseman-has-a-laptop on 2010-03-25
wait windows 7 has problems ....no way ok sorry to troll i just needed to get that out  of my system

---

### Post by Dlizzz on 2010-03-25
> **oldfred said:**
> Booting from a drive and from the raid may change the drive numbering.
Typical grub entry has set root=(hd0,1) for drive and partition, but if you change to boot from raid does the hd? number change?

You're definitively right. If we change the primary disk in BIOS, normally hd numbering will change too. But I've done the install with my raid0 as primary drive (using LiveCD). So the configuration is the same when I try to boot from Windows bootloader.

I haven't currently my hands on my home PC (the incriminated one) but as soon as I'm back home, I will run "boot_info_script.sh" ([]("http://bootinfoscript.sourceforge.net/")) and post the results.

---

### Post by Mark Phelps on 2010-03-25
> **Dlizzz said:**
> I'm not using EasyBCD. I'm using BCDEdit to modify Windows 7 bootloader.
And as far as I can see, the Windows Bootloader does its job fine. It correctly calls the Grub2 bootsector because I can see Grub2 starting... The problem is after when Grub2 starts and then freezes.

Sorry, misread your post...

Then you might want to look into using EasYBCD.  It has some diagnostics routines that can repair and reset BCD information.  They may be able to automatically fix the problem you have.

---

### Post by oldfred on 2010-03-25
In my non-raid system drive order does not change but seems to be based on the order plugged into the SATA ports. Grub then installs to the boot drive set in BIOS.

Not related rant:
Or that is what I believed until I installed the beta of lucid. Drive order has not changed but I boot from sdc. The install of Lucid put grub on sda and refers to partition 7 on same drive per boot-info script. Drive a has only 3 partitions, but it boots into sdc7 correctly. Usually the script has grub referring to a UUID when it is a different drive. I assume this is a script issue since I can boot Lucid, if I use BIOS to select the drive. But if I try to chainboot to sda it does not work. My grub in sdc still boots me into Karmic ok.

---

### Post by Dlizzz on 2010-03-25
> **oldfred said:**
> In my non-raid system drive order does not change but seems to be based on the order plugged into the SATA ports. Grub then installs to the boot drive set in BIOS.


Ok, I will check that when I'm back home. I will have learned something :D

---

### Post by Dlizzz on 2010-03-25
> **Mark Phelps said:**
> Sorry, misread your post...

Then you might want to look into using EasYBCD.  It has some diagnostics routines that can repair and reset BCD information.  They may be able to automatically fix the problem you have.

Once again, BCD isn't the prob... because it runs Grub2 fine !

---

