---
title: "Bootloader help for dual boot"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by todbanner on 2016-05-04
I have looked around the forums for a fix for my situation and have come up with nothing.

I've got a Pansonic CF-30 Toughbook running windows 10 32 pro from the internal hard drive.

I've got the system all set up for my work and can't be without windows 10 for some of the applications I need.

It is not a work owned machine, I'm the owner of the machine and am free to make any changes I want.

The system has an SD card reader, however it has an older BIOS which is incapable of booting directly from the SD card.

I downloaded and installed the lastest iso, wrote to a usb, then installed to the SD card.

From what I've read, what I'd like to do is install Grub2 to the MBR of the hard drive, so the bios can boot the primary HD.  Then under Grub 2 it would give me either the option to boot into windows 10 on the drive or Ubuntu off the SD card.

I thought I should seek help before I wrecked the boot loader and lost my windows 10 install, which I can't do without.

So I assume the instructions will go something like, boot off the usb drive again.  Set up Grub, edit grub.cfg, update grub and go from there.

I just need some help with that config so I don't blow anything up.


Thanks!!!

   TodBanner.

---

### Post by yancek on 2016-05-04
If you have windows 10 and it was pre-installed on the machine, it is extremely likely that you are using UEFI/GPT which means you need to install Ubuntu UEFI also.  The link below is the official Ubuntu documentation on dual-booting using UEFI.  If you are using UEFI (the site below gives you a command to check if you don't know), you definitely do NOT want to install Grub to the MBR.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2016-05-04
> I downloaded and installed the lastest iso, wrote to a usb, then installed to the SD card.

Where was the boot loader installed to? The default location is to sda which should have been the hard drive. With a UEFI boot system there is a efi boot partition where the efi boot files will go. It is in the efi boot partition that Windows 10 keeps its efi boot files. And if Ubuntu was installed in EFI mode and not legacy mode then it is possible that the Ubuntu efi boot files are also in the efi boot partition.

My advice is to run the Ubuntu live session and install Boot Repair to it and then get Boot Repair to create a Boot Info Summary report. A URL will be provided which will be where the summary report has been stored online. Post the URL in this thread and then we can see what the situation is. The summary report will also recommend a repair option. You find it at the end of the report.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The solution might not be to reinstall Grub but to enter the UEFI settings utility and select to boot from Ubuntu.

Regards
[URL="https://help.ubuntu.com/community/Boot-Repair"]

[/URL]

---

### Post by LostFarmer on 2016-05-04
a fast web search says your comp was made in the XP-Vista time frame, is that correct ?  If yes then likely not EFI capable.  Noticed you are running 32 bit win 10.   If it is Legacy (MBR) booting it is harder to do but can be done.  You would need a small partition on the internal hdd for a dedicated grub install unless the  SD card will remain in the comp at all times.  The running and posting the data from Boot-Repair will tell us.

---

### Post by oldfred on 2016-05-04
I would also make a Windows repair CD or flash drive. Or if you have install media know how to get into repair console.
With Linux tools you can only make minor repairs to Windows and often need Windows tools.

And with Windows 10, you must have fast start up off, for grub to be able to find it and add it to grub menu. Grub only boots working Windows or one that is not hibernated nor needs chkdsk. Windows 10 fast start is hibernation and a Windows crash usually means chkdsk which cannot be done from Linux.

       Windows 10 repair disk
[URL="http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html"]http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html
[/URL]
 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

[URL="http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html"]
[/URL]

---

### Post by todbanner on 2016-05-17
Thanks for all the helpful responses.  

I haven't moved much on this project since I posted this question.

When I have to come back to it I will update with my progress so that other can benefit from it.

Cheers.

---

