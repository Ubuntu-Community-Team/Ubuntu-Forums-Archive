---
title: "USB Installation - Long delays and runs very slow"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by AlwaysRemind on 2014-03-03
Hello everyone! I'm a Windows 8 user and from everything I gather it's near impossible to dual boot with Windows 8 and Ubuntu (Unless I'm wrong) and both work correctly. I used the Universal USB  Installer on one thumb drive, then disabled Secure Boot + Fast Boot,  switched to Legacy and was able to get into the Live version of Ubuntu  12.04.4! After that I went ahead and installed the boot and Ubuntu onto  the other thumb drive (my 32gig one) and it worked perfectly. As long as  I stay in Legacy I'm able to boot into it fine with no errors. It does,  however, run very very slow. The response time when clicking menu items  is about a 10 second delay. Is this normal with thumb drives?

**COMPUTER** GT70 0NC
**CPU** Intel Core i-7 3630QM, CPU 2.40GHz
**OS** Windows 8
**Chipset** Intel HM77 Chipset
**Memory** 12gb DDR3 1600MHz
**GPU** NVIDIA GeForce GTX 670MX 

If it's possible to install Ubuntu on my main hard drive that would be wonderful as long as it wouldn't conflict with Windows 8. I'm getting ready to deploy soon and I'd really like to make sure everything's stable (which is why I'm relying on Windows 8 so much for Skype and such).

Thanks guys!

---

### Post by oldfred on 2014-03-04
Many have installed to dual boot with Windows 8, but various vendors have made it difficult as some have modified UEFI to only boot Windows. The work around for those is a file rename so system thinks it boots Windows file, but that file is really grub/shim to boot Ubuntu. But then you only can boot Windows from grub.

My 6 year old systems both boot and run from flash drive. USB2 ports with USB2 flash drive is a bit slow, particularly on writes. You do have to change some settings to reduce writes similar to what you do for an SSD. My newer USB3 flash drive is about 10% faster on my old USB2 ports.
I also change from full Ubuntu to fallback with 12.04 or now called flashback. 

With 12GB of RAM, once apps are loaded in RAM, your system from flash drive should be just as fast as a hard drive install. Only writes where you save data may be slow. 

If in an area with less support and capability I would have several repair flash drives. At the minimum a Windows current version, Ubuntu current version installer and a full install of Ubuntu or maybe another flavor.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

    
Lots of info on UEFI install with dual booting Windows in my signature. Not sure about your brand/model.

---

### Post by AlwaysRemind on 2014-03-04
Thank you very much for replying!

After spending a few hours of trial and error I finally figured out how to just dual boot Windows 8 and Ubuntu. I actually had to **enable** Secure Boot and **disable **Fast Boot. Somehow this ended up actually working and I could move right past GRUB. The installation didn't recognize my OS but that was fine so I just did 'Something Else'. My other thread's right here: [http://ubuntuforums.org/showthread.php?t=2209117](http://ubuntuforums.org/showthread.php?t=2209117)

Thank you again for all of your help!

---

### Post by C.S.Cameron on 2014-03-04
I have installed 12.04 to a 16GB Sandisk Cruzer Fit USB2 Flash Drive.
I use it and a laptop as my entertainment center.

First partition is 2GB NTFS, second partition is / and there is 8GB swap.
The swap is to insure full hibernation.

It seems to me like Ubuntu is running in RAM.
Five seconds to open Libre Office Calc the first time, half a second to open it after that.

---

