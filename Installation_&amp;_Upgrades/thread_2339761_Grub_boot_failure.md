---
title: "Grub boot failure"
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by gray-marsh on 2016-10-12
New to the forums and quite new to Ubuntu and got myself into a bit of a pickle!

Have a Compaq Mini (wireless only, no cd drive) that was configured to dual boot Windows XP and Ubuntu and was working okay.  Then for various reasons I decided the remove Ubuntu and stupidly deleted the Ubuntu partition from Windows and so as I'm sure you know the pc will now not boot and ends with a Grub-Rescue prompt.

After a lot of research I realised the only option would be to create a Live Ubuntu USB stick and boot from there.

Next issue is I am currently on holiday on a Scottish island with very slow broadband and the only other internet accessible device I have is the iPad I am currently writing this on.  I briefly managed to borrow a friends laptop but could not wait the 5hrs it was going to take to download a full Ubuntu 16.04 ISO file so had a search and managed to find a stripped out version which was only 295mb and so downloaded this and created the USB.

Back on the notebook it happily boots from the USB and brings up the Grub? menu asking me to install Ubuntu or try it without installation but whichever one I choose causes the installation to crash out with a missing firmware which I think is for the wireless device.

The problem is I have no way of downloading the firmware and writing it to the USB stick so is there any way I can force the install past this point and ignore the error? If I press enter when the error comes up then I get to an Ubuntu command prompt and if I type Help then I get a list of commands but I am unsure of Linux syntax so any tips on what I can do?

thanks

Graham

---

### Post by oldfred on 2016-10-12
While with high speed Internet using Ubuntu to fix system is good choice, there are other options.
If system is that old you probably should have had Lubuntu anyway and it is smaller than Ubuntu.
I believe the full Boot-Repair disk is based on Lubuntu.

But most lightweight repair tool for BIOS based systems is Super Grub.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

But best not to decide to reconfigure system when not at home.
Always have Windows repair disk and Ubuntu repair disk with you when you travel.
I create a Linux tools disk with many Linux installs or repair tools on one flash drive, just for emergencies.

---

### Post by gray-marsh on 2016-10-12
I'm not bothered about anything on the laptop as the only reason for bringing it was to be able to download pictures from the wife's camera so I'm currently in bad books as I've bust it!!

---

### Post by gray-marsh on 2016-10-13
Is there no way I can use the Ubuntu command prompt to edit the boot sequence on the USB to either bypass the firmware issue or boot into windows which is still on the first partition?

---

### Post by oldfred on 2016-10-13
This was a typical grub boot stanza You can leave off the menuentry & {} and see if manually typing it works.
Example with set root to sda2 hd0,2.  You need to know which partition Windows was in.
Grub only boots working Windows  so if any Windows issues, it will not work.
```

 menuentry "Windows Vista (loader) (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
chainloader +1
} 


```

---

### Post by gray-marsh on 2016-10-13
Thanks but how do I get that into the grub menu? Very new to Ubuntu!

---

### Post by yancek on 2016-10-13
> Thanks but how do I get that into the grub menu? Very new to Ubuntu! 		

When you boot Ubuntu from the flash drive, you should see this message on screen:   Press enter to boot the selected OS. 'e' to edit the commands before booting...
So with Ubuntu on the menu highlighted, hit the 'e' key on the keyboard and screen will change and you should see the menuentry which you can modify.  Delete the info for the entry and replace it with what oldfred suggested.  You would have to replace  "(hd0,2)" with the correct partition if if is not sda2.  This is a one time change so if you have to reboot for some reason, you would need to do the entry again.

---

### Post by oldfred on 2016-10-13
If typing into grub as boot stanza, you need the entire thing.
If you choose to go to grub command line, not the e for edit of grub menu entries, then you have to type each line.

---

### Post by gray-marsh on 2016-10-13
Never seeing the message. Goes straight to the menu and then when I try to install crashes out. Worked out how to use "cd" and "las" to explore the USB stick but can't find which file I need to edit!

---

### Post by oldfred on 2016-10-13
We were suggesting editing as you boot. If you get grub menu.
If you have older system, it may not be grub menu but a BIOS boot with purple screen. That uses syslinux not grub.

Which screen do you get.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you  try Super Grub? It is the easiest way to boot an existing install if it is bootable.

---

### Post by gray-marsh on 2016-10-13
I get the screen with the two icons at the bottom which is described as "[COLOR=#333333][FONT=Ubuntu]- If the BIOS is NOT set up to boot the CD in UEFI mode, or if the disk is not 64-bit, then you will see the screen below"

Its an old system so definitely not 64-bit and not UEFI.

I can't try the supergrub as I have no way of downloading anything to the laptop or USB stick until I can boot into windows or Ubuntu.[/FONT][/COLOR]

---

### Post by oldfred on 2016-10-13
I do not know of any way to boot Windows from BIOS installer.
There probably is a way to edit syslinux, but I do not know.

[http://www.syslinux.org/wiki/index.php?title=SYSLINUX](http://www.syslinux.org/wiki/index.php?title=SYSLINUX)

---

