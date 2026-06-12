---
title: "Can't boot from usb after 10.04"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by EarthCrash on 2013-09-07
At first, this is not about boot priority, or non-bootable USB.

My PC can't boot from USB. But old linux distribution can do that.

For example, Win7 USB work well. But ubuntu can boot only 10.04 or older version.

Actually, my first try was clonezilla-live-2.1.2-43-amd64(Lastest version of that) because i've plan for HDD cloning & migration to linux. But when i try that, progress was freezed with this screen.
[ATTACH=CONFIG]246086[/ATTACH]

Problem is that occur not only clonezilla but also debian-based & redhat-based linux distribution. I was try everything i know during several(over 10) hours and i was founded that the first version of clonezilla(1.0.2-5 in '97) is bootable from USB!

So, i was focused release date of distribution and syslinux version(and release date). below screen is occur when boot from ubuntu 10.10(first non-bootable ubuntu in my PC) USB.
[ATTACH=CONFIG]246085[/ATTACH]

Did you see? syslinux's version is 3.86(2010-04-01). That's the same version with clonezilla-live-2.1.2-43.

But...i failed boot both fedora10(09.12.18) and fedora11(10.06.25). but they not failed by bootloader.
Fedora10: failed to find root filesystem and temporary shell.
Fedora11: hang at kernel load.(At second line output)



Used USB writer program list is this:
UltraISO (Almost alway best result.)
Universal USB Installer 1.9.4.1
unetbootin-windows-585
LinuxLive USB Creator 2.8.24
YUMI-0.1.0.6


And used 3 USBs for test. All of them can use for Windows boot USB.

There is no difference between 32-bit and 64-bit image file in test.



In my opinion, It looks like mainboard(MSI P56A-GD53) problem.
I do update BIOS firmware up to lastest. But still can't boot from recent linux USB.

And now, i'm tired about this. Can anyone solve this?(I'll test in my company PC after few hours)

---

### Post by EarthCrash on 2013-09-07
Problem solved.
There was two wrong action.

First, i should be choose 'UEFI: USB_NAME' rather than 'USB KEY: USB_NAME'.
I didn't mentioned about 'UEFI: USB' option maybe because when i select that with WIN7 boot USB, there was nothing happened.

Second, mainboard's boot priorities has bug or some sort of that. If i place CD/DVD in front of 'UEFI: USB', BIOS skip the UEFI entry so it will be not booted. Even if i place 'UEFI: USB' at first priority, i'll fall into 'UEFI built-in shell' at booting time if plugged USB has removed before booting. Therefore, i should select boot device manually by press F11.(in MSI board)

That's just all.

---

