---
title: "BIOS/UEFI Trouble While Rejecting MS Windows 8 License &amp; Installing Ubuntu on New PC"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by pfau82 on 2012-11-29
Hi Ubuniverse,

I'm brand new to posting, so I hope you'll forgive my obvious ignorance (I've tried to abide by all of the policies and search for previous answers to my problem).

I've been running Ubuntu (and loving it) as a Win7 dualboot for about 2 years now. Recently I purchased a brand new Samsung Ativ SmartPC (500t) tablet (with keyboard dock) running a pre-installed (full, non-RT) version of Windows 8. I decided, however, that I was tired of paying the MS tax and that Ubuntu could meet all of my computing needs, so I rejected the initial Windows 8 License terms and tried to Live boot the system into Ubuntu (as I had many times before on various systems). After trying to reject the Windows 8 license, however, and messing with the Live USB for over a day, I fear I may have just bought myself an expensive brick.

The system now boots directly to the BIOS. There is no option to tell the system which device(s) to boot from first. However, under the "Exit" tab, there is a section labelled "Boot Override". Under this section it lists "UEFI: SanDisk" as the only option (so clearly it is recognizing my Live USB in some way). When I highlight this option and select it, the screen just quickly refreshes and produces the exact same screen without (apparently) running or doing anything.

I have tried disabling the "Secure Boot" function (which I know has been a Linux headache of dubious security merit) and also disabling the "TPM 2.0 Device" (not quite sure what that is). None of that seems to do anything.

When I restore all of the defaults and reboot, it actually does not go directly to BIOS, but takes me to a more troubling screen:

> Error occurred during Clearing RPMB   ResultCode = 0x10000012

  Unexpected Error during clearing RPMB
Press VOL_UP to proceed...

When I proceed as it suggests, I am rebooted directly back into the BIOS with the same problems.

I have messed around with the "Secure Boot Configuration" but it seems like I am completely locked out of making any changes to the configuration (probably because I haven't even accepted the Windows License or fully installed the OS yet). In the configuration, however, when I try to configure a custom "Secure Boot Mode", it does take me to a "Key Management" screen where it clearly recognizes that I have a Live USB plugged in. But all of the options are "locked" or "Fail" when I try to reconfigure them.

I really wanted to reject the Windows License and try to get my MS refund since Ubuntu does everything I need; I guess freedom (of software) has a dangerous price. Any suggestions would be most welcome (as well as any corrections pertaining to forum rules or conventions I may have flouted!).

Thanks for any advice!

---

### Post by oldfred on 2012-11-29
The 64 bit version of Ubuntu 12.10 has the new grub2 2.00 which has the Windows secure boot enabled. That should boot with either secure boot on or off in UEFI. 

But some UEFI configurations are buggy and do not work.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
       
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have a quick-boot setting in UEFI/BIOS turn that off also.

Is your model shown here?
[http://www.linlap.com/samsung](http://www.linlap.com/samsung)

There have been several others  posting here with Samsung or Windows 8, but I do not think anyone with your model & Windows 8.

[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by pfau82 on 2012-11-29
Thanks for your reply!

I have indeed been trying the 64bit after I read that it was best with UEFI. Frankly, I've tried both 32bit and 64bit installations out of desperation. I also just tried SystemRescueCD after burning a Live USB with UNetbootin. Again, the BIOS recognizes, but is unresponsive to, the USB stick.

It is clearly a major bug, which, given my novice skill level, seems to begin (at least) with the BIOS itself. I have been thinking of trying to see if I can get Smart Boot Manager or FreeDOS to help me fix/manage/work around the BIOS. I have a feeling that the BIOS update I've downloaded from Samsung.com might help, if there was some way I could get it to run.

And no, my make/model isn't listed on linlap.com.

Thanks again.

Still working on it...

---

### Post by oldfred on 2012-11-29
There has to be a UEFI setting to turn secure boot off. Some have installed with it on, but others have had to turn it off. 

The 32 bit does not have UEFI drivers, so it will never work. And not many of the other Repair Linux have updated to UEFI yet. Ubuntu is one of the first to have a way that works with secure boot.
You may also have legacy/BIOS/AHCI mode that may boot the older BIOS MBR type systems from CD or flash drive.

From Windows spec to vendors:
> Mandatory. On non-ARM systems, the platform MUST implement the ability for a physically
present user to select between two Secure Boot modes in firmware setup: "Custom" and
"Standard". Custom Mode allows for more flexibility as specified in the following:

    

---

### Post by Osamabingandhi on 2013-06-02
I am sitting here with the same issue....Is it possible in any way imaginable to install ubuntu on a Ativ smart pc 500t??? No usb-stick will boot into an ubuntu-live-usbstick.

---

