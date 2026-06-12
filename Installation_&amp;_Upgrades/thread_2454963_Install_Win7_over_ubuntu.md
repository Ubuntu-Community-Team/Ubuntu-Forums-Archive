---
title: "Install Win7 over ubuntu"
date: 2020-12-09
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2020-12-09
My laptop is a Dell is a two year old Inspirion.  Currently I have 100% ubuntu installed.  Can anyone advise how to install Win7 100%, then after that I know have to re install dual boot back to ubuntu.  I bought a legit Win 7 Professional pack.  It could be as simple as insert disc and select SetUp but not sure how it will all play on a 100% ubuntu system. Thanks!

---

### Post by yancek on 2020-12-09
I've never installed windows 7 so I don't know if it has the "Custom" install option available on windows 10.  With the Custom install option, you can select a drive formatted to ntfs on which to install windows.  It will of course, overwrite the MBR if you have a Legacy install.  What you need to do is first determine if Ubuntu is installed UEFI or Legacy.  If it is UEFI, you need to install windows 7 UEFI which I understand can be done but it might not be straightforward so you may have to do research on it.  Googling install windows 7 UEFI produces a lot of results.

I would use GParted from a CD/DVD or flash drive or use the Ubuntu install medium which contains GParted and shrink the largest Ubuntu partition and then either leave unallocated space for windows 7 or create an ntfs partition on which to install it.  You might be better off with unallocated space.

If you have custom option in windows 7, it will not be necessary reinstall Ubuntu but simply reinstall Grub to the MBR on a Legacy install.  If it is UEFI, you will have separate entries for Ubuntu and windows and you need to set the Ubuntu entry to first boot priority in the BIOS and when booted into Ubuntu, run sudo update-grub.

---

### Post by CelticWarrior on 2020-12-09
> [COLOR=#000000]I bought a legit Win 7 Professional pack.[/COLOR]

I really doubt it considering Windows 7 is out of support for quite some time now. Microsoft or any authorized seller don't sell it now and even if you acquired a legit package from some third-party seller you won't be able to activate it now.

---

### Post by crip720 on 2020-12-09
Win 10 would be a much better choice to install now.  There are a few legal ways of installing it for free, can google so you will not be out of money.  If your Win 7 has a legal license(?) might be able to use that also to upgrade/install.  Should be able to shrink your Ubuntu partition with gparted on a USB and make a NTFS/or free space partition for Windows.  Just have a Ubuntu installer USB handy to repair grub if needed.

---

### Post by oldfred on 2020-12-09
Did you Dell originally come with Windows 8 or 10?
Then the license is in the UEFI or 8 or 10, but not 7.
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

---

### Post by mawil10132 on 2020-12-09
> **oldfred said:**
> Did you Dell originally come with Windows 8 or 10?
Then the license is in the UEFI or 8 or 10, but not 7.
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

The laptop came with Win10, not sure what your getting at?

---

### Post by mawil10132 on 2020-12-09
> **yancek said:**
> I've never installed windows 7 so I don't know if it has the "Custom" install option available on windows 10.  With the Custom install option, you can select a drive formatted to ntfs on which to install windows.  It will of course, overwrite the MBR if you have a Legacy install.  What you need to do is first determine if Ubuntu is installed UEFI or Legacy.  If it is UEFI, you need to install windows 7 UEFI which I understand can be done but it might not be straightforward so you may have to do research on it.  Googling install windows 7 UEFI produces a lot of results.

I would use GParted from a CD/DVD or flash drive or use the Ubuntu install medium which contains GParted and shrink the largest Ubuntu partition and then either leave unallocated space for windows 7 or create an ntfs partition on which to install it.  You might be better off with unallocated space.

If you have custom option in windows 7, it will not be necessary reinstall Ubuntu but simply reinstall Grub to the MBR on a Legacy install.  If it is UEFI, you will have separate entries for Ubuntu and windows and you need to set the Ubuntu entry to first boot priority in the BIOS and when booted into Ubuntu, run sudo update-grub.

You lost me on the UEFI or Legacy, I installed ubuntu 20 right after it came out of beta.   (after I wrote this is began wondering if i should simply reinstall ubuntu first as it handles wipe and HD partitioning, then install 7 in the empty partition?

---

### Post by oldfred on 2020-12-09
You cannot install Windows 7 as it is End of Life.
But you already have a product key for Windows 10. So you just have to reinstall it in UEFI mode.
You cannot install Windows 10 in BIOS mode and have the product key work.

---

### Post by C.S.Cameron on 2020-12-09
Windows 10 ISO: [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)
Use mkusb to make an installer USB: [https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

---

### Post by rsteinmetz70112 on 2020-12-10
[QUOTE=CelticWarrior;14005955]I really doubt it considering Windows 7 is out of support for quite some time now. Microsoft or any authorized seller don't sell it now and even if you acquired a legit package from some third-party seller you won't be able to activate it now.[/QUOTE

I don't think that's correct. I reinstalled Win 7 from a DVD a couple of weeks ago. I even installed Win7 into a Ubuntu VM. You may have to use the phone system to activate it but it can still be done. You can still upgrade Win7 to Win10 free using the Microsoft Media Download tool. I've recently done that as well.

---

### Post by rsteinmetz70112 on 2020-12-10
I'd suggest installing Win7 into a Ubuntu VM and avoiding the whole dual boot hassle.

---

### Post by mawil10132 on 2020-12-10
> **yancek said:**
> I've never installed windows 7 so I don't know if it has the "Custom" install option available on windows 10.  With the Custom install option, you can select a drive formatted to ntfs on which to install windows.  It will of course, overwrite the MBR if you have a Legacy install.  What you need to do is first determine if Ubuntu is installed UEFI or Legacy.  If it is UEFI, you need to install windows 7 UEFI which I understand can be done but it might not be straightforward so you may have to do research on it.  Googling install windows 7 UEFI produces a lot of results.

I would use GParted from a CD/DVD or flash drive or use the Ubuntu install medium which contains GParted and shrink the largest Ubuntu partition and then either leave unallocated space for windows 7 or create an ntfs partition on which to install it.  You might be better off with unallocated space.

If you have custom option in windows 7, it will not be necessary reinstall Ubuntu but simply reinstall Grub to the MBR on a Legacy install.  If it is UEFI, you will have separate entries for Ubuntu and windows and you need to set the Ubuntu entry to first boot priority in the BIOS and when booted into Ubuntu, run sudo update-grub.

I think you have the best idea, I'm downloading gparted!   ubuntu is UEFI

---

### Post by mawil10132 on 2020-12-10
I have another question if you don't mind:  I downloaded gpart live then burned the iso to a dvd, rebooted then tap f12 to check dvd is first in line of start que and it is, but ubuntu still loads as normal. Got any ideas?

---

### Post by yancek on 2020-12-11
If the DVD is first in boot priority, then it should boot.  When you made the change was it a permanent change in the BIOS?  If so,  did you make sure to save it?  Or is the F12 option just the one time boot option? I've never used a Dell so I'm not familiar with it.  Another option you can try is to use the Ubuntu install USB which has GParted on it.

---

### Post by CelticWarrior on 2020-12-11
> **mawil10132 said:**
> I think you have the best idea, I'm downloading gparted!   ubuntu is UEFI
No, installing Windows 7 now is a **very bad idea**, for all the reasons already commented and also because Windows 7 could only - it still can but SHOULDN'T - be installed in UEFI mode with a USB stick; **Windows 7 cannot be installed in UEFI mode with a DVD**.
While it WAS supported, Windows 7 would be installed directly downloading it from Microsoft and burning an USB using the Media Creation tool online from a Windows session (if downloading from any non-Windows only the ISO file would be downloaded and then the users would burn it with alternative tools like MKUSB or WoeUSB in Ubuntu). **Of course, this isn't an option now that Windows 7 is obsolete, unsupported**.
It may still be possible to image the DVD (to .iso or .img) and then use the resulting file with the alternative tools but preferably done in Windows with Rufus (Rufus may even be able to make an USB installer directly from the DVD but I'm not sure).

And also any Windows strictly requires GPT for UEFI mode and MBR("msdos") for BIOS mode. Ubuntu isn't restricted in the same way. If your Ubuntu was installed in UEFI mode (as it should be) then very likely the drive is GPT (as it should be, but again, not a given) in which case **booting the Windows 7 installer from the DVD won't let you install it anyway**. If (UEFI) Ubuntu was installed in a MBR drive then it will allow installation of Windows 7 in Legacy/"BIOS" mode but then the **dual-boot won't work**.

If your computer came with a **factory installed Windows 10** - that later it was replaced by Ubuntu doesn't matter - you have **a valid Windows 10 OEM license already**. You can at reinstall it anytime. Just download it directly from Microsoft and burn it to a USB stick, same way / some options as above. **Once installed (UEFI mode only, as it should be) it'll activate online. ****No additional purchase necessary!**

Now, expanding on my previous post...
No matter how legit your purchased Windows 7 was (original Microsoft pressed DVD + serial number and all). **it is no longer valid**, it won't activate, it'll be for all intended purposes indistinguishable from any "pirated" version.
**** You were SCAMMED****

You can use the DVD to install Windows 7 in a virtual machine. It's relatively safe to use that way as long as it doesn't connect to the internet.

So, in conclusion, thinking that a "well, maybe..." answer is the "best idea" and ignoring the expert warnings and suggestions stems from ignorance, carelessness and confirmation bias. Just DON'T, for your own sake and everybody else's (a compromised OS isn't only dangerous for the user, it can be used to attack other networks). 


> **mawil10132 said:**
> I have another question if you don't mind:  I downloaded gpart live then burned the iso to a dvd, rebooted then tap f12 to check dvd is first in line of start que and it is, but ubuntu still loads as normal. Got any ideas?

Gparted is already included in any Ubuntu installation media, no need to download it separately (and depending on the GPaterd's standalone ISO capabilities it may not even boot in UEFI mode, as it seems to be the case.

Indeed, if you want to dual- or multi-boot and your current Ubuntu installation occupies the whole target drive, you need to boot a live session and shrink the main Ubuntu partition. GParted is a good tool for that.

It must be stressed this also is very indicative of basic knowledge lacking.

---

### Post by CelticWarrior on 2020-12-11
> **yancek said:**
> If the DVD is first in boot priority, then it should boot.  When you made the change was it a permanent change in the BIOS?  If so,  did you make sure to save it?  Or is the F12 option just the one time boot option? I've never used a Dell so I'm not familiar with it.  Another option you can try is to use the Ubuntu install USB which has GParted on it.

I don't know how the GParted ISO is made by I suspect it can boot in BIOS mode only or must be burned in a CD, not a DVD.
Or it was incorrectly burned. Given what the OP showed so far that wouldn't surprise me at all.
And Gparted has USB specific images that surely work in UEFI mode.

---

### Post by oldfred on 2020-12-11
I have gparted gparted-live-1.1.0-1-amd64.iso and in viewing it, it has /EFI/Boot/bootx64.efi for UEFI boot from an external device. Looks like it also has syslinux for BIOS boot.

I have only booted gparted in last few years with grub2's loopmount or from my UEFI installs to work on another drive. But always UEFI.

---

