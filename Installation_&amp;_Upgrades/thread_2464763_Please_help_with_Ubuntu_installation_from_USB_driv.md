---
title: "Please help with Ubuntu installation from USB drive to hard drive"
date: 2021-07-11
forum: Installation &amp; Upgrades
---

### Post by bodya081 on 2021-07-11
Hello all, 

I'm brand new to Ubuntu and Linux and would really appreciate any help I can get installing Ubuntu on my old HP laptop. Here's where I'm at: This HP laptop is ~12 years old, has Windows 10 on it. I downloaded Ubuntu 20.04.2.0 LTS to the hard drive. Then I installed Rufus on 32Gb USB flash drive and used it to make ISO copy of Ubuntu to use for install. I then went to Boot settings and switched it to have the laptop boot up from USB flash drive. I restarted my laptop and it booted from usb stick like it was supposed to. Took me to the screen asking if I want to try it or to install it. I selected install alongside of Windows 10 and chose partition size. Went through install, it said installed successfully and computer needs to restart. From there it took me to the boot up screen that told me that I need to remove usb stick and press Enter to continue. That's where the problems started. Once I removed the usb stick and pressed enter it booted Windows instead of Ubuntu. So I restarted again, took me back to Ubuntu and I had to go through exact same process as before with the same result. This time I tried removing the stick after install and before restarting. That just crashed everything and screen went black. I saw something pop up on the top for a second saying Loop failed or Boot failed. Bottom line is I can get Ubuntu come up booting from the usb stick but I can't get it to install and stay on the actual laptop hard drive. Any advise/help would be greatly appreciated. Thank you!

TL;DR: I followed the instructions to install Ubuntu on my Windows laptop using USB bootable stick and everything worked well until I got to the last part asking me to take out the USB stick so it would boot from the laptop hard drive but instead it booted Windows 10.

---

### Post by yancek on 2021-07-11
The link below is the official Ubuntu documentation on dual booting Ubuntu with windows.  Given the age of your computer, it may no be EFI capable so make that determination first.  If you have windows installed in Legacy/CSM mode you need to boot and install Ubuntu in the same mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you are unable to resolve your problem with the information on the above site, use the Ubuntu install USB and download and run boot repair as explained at the site below.  Make sure to use the 2nd option using the ppa and select to run Create BootInfo Summary and do not try to make any repairs.  Post the link you get when it finishes here to get help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by GhX6GZMB on 2021-07-11
Not to the point, but: how on earth did you get Win10 onto that machine? And do you take a nap after starting it and when you wake up is it running?

Jokes aside: I run several HP laptops of that age with Lubuntu 20.04 and they run beautifully and fast.

I think you need to rethink your Win10 idea generally, those machines were born with Vista, and that's about it. Win7: no. Win 8: no. Win 10: no.

Just my experience..

---

### Post by QIII on 2021-07-11
I've had Win10 running on machines circa 2005.  To be fair, those were top of the line machines for their era, but they were 10 years old by the time Win10 came out.

If it'll run Win10, there is absolutely nothing wrong with that.  IMO Win10 is the best they've come out with if you discount all the privacy invasion stuff.

Disclaimer:  I make good money producing software for clients that use the Win10/Win Server platforms, so I might be biased.

---

### Post by oldfred on 2021-07-12
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

If you have BIOS/MBR configuration you will always need both a flash drive with Windows repair/recovery console and Ubuntu live installer. 
With BIOS you only have one MBR for booting. Grub will only boot working Windows, so when Windows does not boot you may have to temporarily install a Windows boot loader to MBR to boot into Windows & make repairs, and then using Ubuntu live installer restore grub to MBR.

Windows 10 works much better in UEFI/gpt boot mode as you can directly boot Windows & Ubuntu from UEFI.
Microsoft required vendors to install Windows 8 in UEFI/gpt mode, starting in 2012 when 8 was released. Windows 7 could be UEFI, but almost all 7 systems were installed in BIOS/MBR.

---

### Post by Impavidus on 2021-07-12
Most likely Ubuntu was installed, but your computer refuses to load it. 12 year old HP laptops with Windows 10 can be a bit tricky.

Is it in UEFI mode or in legacy mode? A 12 year old laptop may support UEFI, but I expect a preinstalled Windows Vista or 7 to be in legacy mode. But after moving to Windows 10, I can't say. Boot-repair will tell.

Windows 10 (or 8) and Ubuntu dual booting in legacy mode is tricky. Older HP laptops with Ubuntu in UEFI mode are tricky too.

---

