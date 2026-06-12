---
title: "Ubuntu 12.10 - Can't Install or Boot Alongside Windows 8"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by Illithid00 on 2013-02-15
I have a Toshiba Satellite C855D laptop running Windows 8, which I'd like to remove and replace with Ubuntu 12.10. I disabled Secure Boot, which was preventing me from booting with either a Live USB or Live DVD. However, when I attempt to boot from the Live USB or Live DVD (hitting F12 at the Toshiba screen, then choosing the appropriate option when the boot option comes up), now all I get is a black screen. No boot screen, no purple Ubuntu screen, just black.

I've formatted and put Ubuntu on the USB I'm using three times, with the same results each time, and made two different Live DVDs. I've read about problems dual-booting Ubuntu with Windows 8, but I'm trying to remove Windows 8 rather than dual-booting. Any help would be appreciated.

---

### Post by oldfred on 2013-02-15
Is this an UltraBook? Which is Intel SRT with a small SSD?

What video system does it have? If nVidia you need nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    With UEFI, it is more like the after install screen.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

But some Toshibas have major issues and some work.
        [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

       The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)

            Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by Illithid00 on 2013-02-15
It's a regular laptop, not an ultrabook. It's the [Toshiba C855D with AMD E-450 APU and Radeon graphics]("http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=2000034277"). I don't know how to check for Intel SRT, but the drive is this model by [Seagate]("http://www.game-debate.com/harddrive/index.php?h_id=140&harddrive=ST320LT020-9YG142%20320GB"). I turned off Secure Boot and the quick boot feature.

As mentioned, I'd like to completely get rid of Windows and replace it with Ubuntu 12.10 64-bit. I have the Live DVD and a Live USB. When I boot up the computer, I press F12 when the Toshiba logo appears and that brings up a menu of sources to boot from, with the HDD at the top, followed by the USB drive and DVD drive. If I choose anything other than the HDD, I get a black screen, with no splash screen or anything like that.

I looked through your links, but haven't been able to find anything resembling the problem I've been having.

---

### Post by oldfred on 2013-02-15
When booting do you get a screen with the tiny keyboard & accessibility icon at the bottom for about 5 to 10sec?. If so press any key. Then f6 and add nomodeset.
That may be only with BIOS boot, not UEFI boot.

Some UEFI systems only want to install with BIOS mode, and then we have to use Boot-Repair to convert to UEFI mode.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
I would not plan on immediately deleting Windows. A few systems only work correctly with Windows still installed.

---

### Post by Illithid00 on 2013-02-15
> **oldfred said:**
> When booting do you get a screen with the tiny keyboard & accessibility icon at the bottom for about 5 to 10sec?. If so press any key. Then f6 and add nomodeset.
That may be only with BIOS boot, not UEFI boot.

Some UEFI systems only want to install with BIOS mode, and then we have to use Boot-Repair to convert to UEFI mode.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
I would not plan on immediately deleting Windows. A few systems only work correctly with Windows still installed.

No, I don't get the screen with the keyboard/accessibility icons, just a black screen. Occasionally, I've gotten a very brief flash of something that looks like a boot screen, like the one where you choose between regular Ubuntu, Safe Mode, and stuff like that, but it flashes up for less than a second and then back to black.

What systems wouldn't work without Windows? My previous computer was solely Ubuntu after my Windows 7 install crashed and never had any problems related to the software that I was aware of.

---

### Post by oldfred on 2013-02-15
Does alt-f2 or control alt T get you to a terminal?

Does holding shift key down from BIOS get you a grub menu? UEFI may be using grub to boot Flash drive.

If you get live install working, but before you install I would definitely back up efi partition and the entire Windows after you have shrunk it from inside Windows with its Disk tools.

---

### Post by Illithid00 on 2013-02-20
> **oldfred said:**
> Does alt-f2 or control alt T get you to a terminal?

Does holding shift key down from BIOS get you a grub menu? UEFI may be using grub to boot Flash drive.

If you get live install working, but before you install I would definitely back up efi partition and the entire Windows after you have shrunk it from inside Windows with its Disk tools.

None of that works. I got a GRUB menu asking to install Ubuntu or try without installing on a Live USB of Ubuntu Secure Remix, but that's it. I hit the "try without installing" option so I could see if it would actually boot or open anything, but it went right back to a black screen.

---

### Post by oldfred on 2013-02-20
Then you need the nomodeset.

With UEFI it is a bit different. I think it is more like booting the first time after install. But try any key and f6 which is normal BIOS boot or see if f6 works on its own. 

Normal screens to get to nomodeset but not UEFI boot screens are shown in links above.

---

