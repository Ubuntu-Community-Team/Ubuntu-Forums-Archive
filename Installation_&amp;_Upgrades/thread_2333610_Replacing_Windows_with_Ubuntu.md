---
title: "Replacing Windows with Ubuntu"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-08-11
Hello everyone I wanted to know what the process was to remove Windows 10, completely from a multi dual booting machine

This particular machine has Windows 10 and three other Linux installation systems on it. I would like to just remove Windows altogether because I don't use it at all and would like to make good use of that disk space

My concern is if I do remove Windows how would this effect my booting sequence? I currently have the option to choose which os using the Grub menu

I would like to keep things in order as they currently are

I would not want to delete anything and then have trouble booting my multi SO's

Thankstill for any help with this

---

### Post by yancek on 2016-08-11
If you are using the older style MBR system to boot and have Grub in the MBR booting the different systems, you would just re-format the windows partitions to be used under Linux.

If you are using UEFI, I would expect re-formatting the windows partitions and removing the windows entry from the EFI partition to work.  Since the process varies from manufacturer to manufacturer, I would suggest you post info on whether you use UEFI or not and if you do, which manufactuer you purchased the system from as some do not comply with UEFI standards and removing the entry for windows could cause you problems.

---

### Post by RobGoss on 2016-08-11
Thanks so much for the help

Yes I'm am using UEFI and it's a Dell desktop, like I stated this machine has multi SO'S on it and I don't want to mess anything up it's also a fairly new machine

---

### Post by oldfred on 2016-08-11
I normally suggest full backup of the ESP - efi system partition and Windows. We often see users to jump into the deep end of the pool and then find they cannot run one game or application and want Windows back.

If sure, you can just reformat the NTFS partition and use it as a data partition. I do not suggest moving / partition as changing start can create issues, particularly if interrupted for any reason.

And you can remove the /EFI/Microsoft folder from the ESP and the Windows boot entry in UEFI using efibootmgr.

---

### Post by RobGoss on 2016-08-11
> [COLOR=#000000]I normally suggest full backup of the ESP - efi system partition and Windows. We often see users to jump into the deep end of the pool and then find they cannot run one game or application and want Windows back.[/COLOR]


Thanks Fred but there's no going back to Windows for me and I'm not a gamer at all. I haven't use Windows for about a year

I just wanted to make sure what ever I do I just don't mess up the boot loader and still be able to boot my other systems up

So you're saying to format NTFS partition and I can use that partition for another Linux OS

What about the boot loader do I need to install it again?

---

### Post by oldfred on 2016-08-11
Since UEFI, and if grub boots ok now, no change should be required.
Unless you did one of the work arounds that some systems require. 
Most Dells just work and do not have to have the work arounds many other brands require.

If you install another system, then boot may change. I find another Ubuntu install overwrites my main working install of 16.04. So I back up /EFI/ubuntu. But the only thing that really changes is the tiny grub.cfg in the ESP that is a configfile (like a chain load) to the full grub.cfg in the install.

---

### Post by RobGoss on 2016-08-11
Thanks Fred I'll take a closer look and my configurations much appreciated

---

### Post by ubfan1 on 2016-08-11
After removing Windows, run sudo update-grub to rewrite the grub.cfg file without the Windows choice.

---

### Post by RobGoss on 2016-08-11
> **ubfan1 said:**
> After removing Windows, run sudo update-grub to rewrite the grub.cfg file without the Windows choice.


Thanks for the tip Ubfan I'll keep this in mind as I proceed with this configuration

---

### Post by RobGoss on 2016-08-13
Thanks for the tips everyone

---

### Post by RobGoss on 2016-08-15
Just a quick update on how it went removing Windows from my multi boot system. After deleting the Windows partition and a few small Windows partitions everything was still booting as normal

I used that 168 GB Windows partition for Manjaro Linux and everything is running smooth

Thanks for all the great advice it is much appreciated

---

