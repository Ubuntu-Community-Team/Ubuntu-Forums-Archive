---
title: "Dual boot system to work in case of an HD failure ?"
date: 2017-05-07
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2017-05-07
[FONT=&quot]I'm trying to set up a dual boot system that will protect against a hard disk failure.[/FONT]
[FONT=&quot] It's a desktop with 3 hard drives - I have installed Ubuntu 1604 in sda1,  and another Ubuntu 1604 in sdc5.   On  bootup, it gives me the expected menu choice of which install I want to boot from,  and I have used both for booting with no problems.[/FONT]
[FONT=&quot]I simulated  a failure of sda  by pulling the plug on it and booting up,  hoping that the system  would wind up  booting off of  sdc5. [/FONT]
[FONT=&quot] It didn't. I got an error message: ‘error: file/boot/grub/i386-PC/normal.mod not found’.  I figured that if I just plugged in sda again I would be able to boot the system normally, but to my surprise that didn't work - I got the same error message again.[/FONT]
[FONT=&quot]I fixed the situation by using a boot repair disk. [/FONT]
[FONT=&quot] So, how do I set the system up in such a way that  if sda fails, sdc5 will take over and boot up?[/FONT]
[FONT=&quot]Thanks [/FONT]

---

### Post by JKyleOKC on 2017-05-07
If the BIOS in your system has an option for setting the boot sequence, see if it allows you to set sda1 as the first-try boot source and sdc5 as the next (actually you should have the cd/dvd drive as the first try, followed by the hard drives, so that you can run diagnostics from a live CD). Some of the boxes here do have such an option, allowing several hard drives to be set up; older ones allow only one hard drive and that would be your sda1. The one I'm replying through does have the multiple option, and it's more than 10 years old, so it's likely that yours will have this option as well.

Note that you have to be sure that grub is installed on both drives. It's not always automatic, but you can force it via apt-get or synaptic.

---

### Post by ra7411 on 2017-05-07
> **JKyleOKC said:**
> If the BIOS in your system has an option for setting the boot sequence, see if it allows you to set sda1 as the first-try boot source and sdc5 as the next (actually you should have the cd/dvd drive as the first try, followed by the hard drives, so that you can run diagnostics from a live CD). Some of the boxes here do have such an option, allowing several hard drives to be set up; older ones allow only one hard drive and that would be your sda1. The one I'm replying through does have the multiple option, and it's more than 10 years old, so it's likely that yours will have this option as well.

Note that you have to be sure that grub is installed on both drives. It's not always automatic, but you can force it via apt-get or synaptic.

Good point re. the BIOS - every computer I've worked with in the past, the BIOS gives a choice of HDs to go to - this one only shows what is sda on my system, not sdb or sdc -  the rest was cd/dvd, various usb versions etc. When I was trying to get it to boot after the error failure, and had replugged sda, I spent some time trying to use that solution and I couldn't get the sdc or sdb drive to show up - weird.

As to installing grub on sdc, that sounds good, but I'm in the dark as to details.

---

### Post by yancek on 2017-05-07
> As to installing grub on sdc, that sounds good, but I'm in the dark as to details. 				

While booted to the Ubuntu installed on sdc5 just run:  sudo grub-install /dev/sdc
That should put Grub boot code in the MBR of sdc pointing to the boot files on sdc5 and then you can set sdc to first boot priority in the BIOS to boot that system if sda fails.
Make sure you have the correct device (sdc).  If you can't see sdc in the BIOS, that won't work but if it is an actual hard drive/usb drive, that would be very unusual.

---

### Post by JKyleOKC on 2017-05-07
> **ra7411 said:**
> Good point re. the BIOS - every computer I've worked with in the past, the BIOS gives a choice of HDs to go to - this one only shows what is sda on my system, not sdb or sdc -  the rest was cd/dvd, various usb versions etc. When I was trying to get it to boot after the error failure, and had replugged sda, I spent some time trying to use that solution and I couldn't get the sdc or sdb drive to show up - weird.

As to installing grub on sdc, that sounds good, but I'm in the dark as to details.Yancek has already replied about installing grub. As for the boot order, you might want to look at updating the BIOS -- but I've never had the nerve to try that, myself, because if anything goes wrong you have a very large paperweight instead of a computer!

You might consider creating a bootable USB drive that simply provides a copy of grub, that in turn boots to the sdc5 partition (and it's quite possible that if sda is no longer valid, the name for sdc5 may have changed. In fact, it's probable.). You should be able to use the grub-customizer program, not installed by default but available in the repositories, to configure the copy of grub on the flash drive. Your BIOS could then be set to use the flash drive as a fallback.

General observation: since the sda-sdb-etcetera names are assigned automatically in the order that the drives are detected by the BIOS, they are not reliable as designations for drives from which to boot. Unplugging sda probably changed the id of sdc to sdb. Much better to use "UUID" values, or even disk labels; these, once assigned by the system, remain associated with the same drive until deliberately changed (such as by reformatting the drive).

---

### Post by ra7411 on 2017-05-07
> **yancek said:**
> While booted to the Ubuntu installed on sdc5 just run:  sudo grub-install /dev/sdc
That should put Grub boot code in the MBR of sdc pointing to the boot files on sdc5 and then you can set sdc to first boot priority in the BIOS to boot that system if sda fails.
Make sure you have the correct device (sdc).  If you can't see sdc in the BIOS, that won't work but if it is an actual hard drive/usb drive, that would be very unusual.

I went back into BIOS. In the boot sequences I'm used to seeing, you can go to #1, hit enter, and see an array of choices including all your HDs. Not with this BIOS - you see the model number of 1 HD (I have 3 on this machine). Two of my HDs (sda and sdc, both w/ o/s installs) are the same model Hitachi, so you don't know which is which you're seeing. I guess you're supposed to know that you have go elsewhere in this particular BIOS and designate which of the same model #'s is to show up in the boot sequence choice.  

So when you're trying to do some kind of alteration, or you've had a failure, you get to go through a puzzle game to figure out what you're looking at, and which HD is the one in the  boot sequence, if you have 2 of the same model in the machine.

Anyway, I booted with sdc5 o/s, did the Grub  install,  and nothing blew up.  
I think I'll quit right here.... I'm not in the mood to be pulling any HD plugs and see  what happens.

---

### Post by efflandt on 2017-05-07
You might look into putting supergrub on a CD or small USB memory stick for emergencies. It searches for systems on the fly when it boots. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by oldfred on 2017-05-07
If a new UEFI system, grub only installs to the ESP on drive seen as sda.

You then can copy the boot files from sda's ESP to sdc's ESP. But UEFI may or may not auto recognize new drive.
Often when you disconnect a drive it removes the entries from the UEFI NVRAM. Some will auto find when drive reconnected. Many only find Windows entries and you have to use efibootmgr to add them again.

Post this: 
sudo parted -l

---

### Post by ra7411 on 2017-05-07
> **efflandt said:**
> You might look into putting supergrub on a CD or small USB memory stick for emergencies. It searches for systems on the fly when it boots. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I made a dvd disk - next debacle I'll give it a try.

Thanks

---

