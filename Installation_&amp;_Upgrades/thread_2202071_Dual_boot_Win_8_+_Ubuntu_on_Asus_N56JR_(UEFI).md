---
title: "Dual boot Win 8 + Ubuntu on Asus N56JR (UEFI)"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by Alessandro_Antonel on 2014-01-27
Hi everyone,
I'm having a lot of trouble installing Ubuntu 13.10 on my brand new Asus N56JR laptop. It is a 64 bit system, it comes with Windows 8 installed, and it has that damn UEFI. I need Ubuntu mostly for university exercises and for getting to know how a Unix system works but not as main environment, so I'd install it as a Windows 8-Ubuntu dual boot.

The problem is that, even if I adjusted BIOS settings as many tutorials and guides on the Internet suggested, the installation freezes.
These are the steps I followed:
1) I insert the Ubuntu DVD/USB drive in the laptop. 
2) Turn off the laptop.
3) Turn on the laptop pressing ESC key. A list of bootable devices is shown.
4) I select the aforementioned device. As the device name is shown twice on the list, I make sure to select the one which starts with [UEFI].
5) I press OK, the system reboots, and the Grub menu appears, as expected. Shortly before showing the Grub menu, for a second or two, this error is shown: [http://imagizer.imageshack.us/v2/800x600q90/13/tmch.jpg](http://imagizer.imageshack.us/v2/800x600q90/13/tmch.jpg) . Is this the cause of my problem?
6) Both selecting the first menu option (Install) or the second (Try without installing) it's always the same: Ubuntu starts loading from DVD/USB drive, and the Ubuntu logo is shown with the throbber demanding to wait. But, after a minute or two, the installation stops and everything freezes (I realize it from DVD drive noise stopping, or USB drive led that stops blinking) and even the throbber's animation stops. I tried waiting but nothing happens; the only thing is that, if I press the laptop's power button, the DVD is ejected. So I have to disconnect laptop from power and battery.

I tried what I said before both with a DVD and a USB drive (made with the Rufus utility). The USB drive is a 3.0 drive, and my laptop has only USB 3.0 ports, but that shouldn't be a problem. And the ISO image I downloaded can't be corrupted (I downloaded it via uTorrent, and anyway the MD5 hash matches with the one reported [here](http://wiki.ubuntu-it.org/Installazione/MD5Sum)).

Any ideas on how to solve this problem?

These are screenshot of my BIOS configuration settings. Can you check if they're fine or if anything must be changed?

Thanks in advance!

Main
[[img]http://s24.postimg.org/naqfsijkh/20140125_203059.jpg[/img]](http://postimg.org/image/naqfsijkh/)

Advanced
[[img]http://s30.postimg.org/ckm543e1p/20140125_203107.jpg[/img]](http://postimg.org/image/ckm543e1p/)

Advanced -> SATA configuration
[[img]http://s11.postimg.org/49npl8fin/20140125_203116.jpg[/img]](http://postimg.org/image/49npl8fin/)

Advanced -> Graphic configuration
[[img]http://s24.postimg.org/s45ljmqoh/20140125_203126.jpg[/img]](http://postimg.org/image/s45ljmqoh/)

Advanced -> Intel Anti-Theft Technology configuration
[[img]http://s27.postimg.org/4zxtgll1b/20140125_203133.jpg[/img]](http://postimg.org/image/4zxtgll1b/)

Advanced -> USB configuration
[[img]http://s27.postimg.org/mutkcwxq7/20140125_203140.jpg[/img]](http://postimg.org/image/mutkcwxq7/)

Advanced -> Network stack
[[img]http://s29.postimg.org/fzxq06dhv/20140125_203150_0.jpg[/img]](http://postimg.org/image/fzxq06dhv/)

Boot
[[img]http://s24.postimg.org/6mb1qk80h/20140125_203158.jpg[/img]](http://postimg.org/image/6mb1qk80h/)

(continues in the next message)

---

### Post by Alessandro_Antonel on 2014-01-27
(continued from previous message)

Security
[[img]http://s29.postimg.org/d6gmgowcz/20140125_203219.jpg[/img]](http://postimg.org/image/d6gmgowcz/)

Security -> I/O interface security
[[img]http://s11.postimg.org/8qoal3y4v/20140125_203227.jpg[/img]](http://postimg.org/image/8qoal3y4v/)

Security -> Secure Boot menu

This is the one I'm most concerned about. As you can see I disabled Secure Boot Control, but the "actual" Secure Boot option is shown in grey and it can't be selected/changed (though it shows Disabled)...
[[img]http://s27.postimg.org/i51sitayn/20140125_203238.jpg[/img]](http://postimg.org/image/i51sitayn/)

Save & Exit
[[img]http://s16.postimg.org/vgszic6wx/20140125_203250.jpg[/img]](http://postimg.org/image/vgszic6wx/)

---

### Post by ali12 on 2014-01-27
im having a similar same issue on my asus x550l but im booting with a cd and it installs fine everytime but
it brings me to a bash grub menu when i install it instead of a gui and doesnt boot.

---

### Post by oldfred on 2014-01-27
I know others have posted UEFI where when one setting is made it locks out others. Or if secure boot is on, you cannot enable legacy boot or when legacy boot is enabled you cannot turn on secure boot. So your settings may be ok. 
Better to have secure boot off. I did not see fast/quick boot setting in UEFI. Some have it in UEFI and in Windows or may be separate setting, but needs to be off.

Is error from UEFI boot of flash drive?
Have you tried any boot parameters on grub linux boot entry?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    

Some other Asus.
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
      
 HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

 Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

This was a Dell, but mentions an Intel issue that may apply.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Only 13.10 or later has support for Wireless with Haswell chips.
> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.


---

### Post by Alessandro_Antonel on 2014-01-27
> **oldfred said:**
> I did not see fast/quick boot setting in UEFI. Some have it in UEFI and in Windows or may be separate setting, but needs to be off.


Thank you for your kind reply.
Yes there is a quick boot setting in my UEFI/BIOS, but it was hidden when I enabled the Launch CSM setting, because it seems quick boot can't be enabled when Launch CSM option is enabled (so it should be OK). Is there an option for Quick boot in Windows 8? I didn't know that, where can I turn it off?

> Is error from UEFI boot of flash drive?

The loading screen of Ubuntu freezes after selecting an option from the Grub menu both using a DVD and a USB flash drive. No difference, only thing is that USB is faster and takes less time to get to the point where it freezes.
If you meant this one [http://imagizer.imageshack.us/v2/800x600q90/13/tmch.jpg](http://imagizer.imageshack.us/v2/800x600q90/13/tmch.jpg) again the error is shown both using DVD and USB drive.

Thanks for the links you posted, I'll read them later and I'll let you know if anything turns out.

---

### Post by oldfred on 2014-01-27
If download is correct, I think you probably need some boot parameters.
More info in link in my signature.
 Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by Alessandro_Antonel on 2014-02-07
Thank you so much, Oldfred! I solved using the "nomodeset" parameter in Grub2, looks like it was some kind of graphic card compatibility issue.
Thank you again, this thread can be closed! :)

---

