---
title: "Ubuntu 64 Bit on Pendrive - Error Boot"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by kingvv on 2013-11-01
Hello, I own an Asus Notebook with USB UEFI.
I tried to install the version of Ubuntu 10.13 64 Bit on a 16 GB Flash Drive (Fat 32) through UNetBootin.
The installation on the memory stick is successful but on booting from USB errors here:

I state that in the GNU GRAB menu choose the option "Try Ubuntu Without Installing" ...

Calling: Test-Built in
Error reading /Lib/Udev/Hwdb.bin no such file or directory
Load module index
Unload module index

Notebook in the block.

Do you have any solution ?

Thank you.

---

### Post by fantab on 2013-11-01
> **kingvv said:**
> Hello, I own an Asus Notebook with USB UEFI.
I tried to install the version of Ubuntu 10.13 64 Bit on a 16 GB Flash Drive (Fat 32) through UNetBootin.
The installation on the memory stick is successful but on booting from USB errors here:

I state that in the GNU GRAB menu choose the option "Try Ubuntu Without Installing" ...

Calling: Test-Built in
Error reading /Lib/Udev/Hwdb.bin no such file or directory
Load module index
Unload module index

Notebook in the block.

Do you have any solution ?

Thank you.

I hope you mean 13.10 Ubuntu. And When you say you installed Ubuntu to USB flash drive with Unetbooin you mean you've 'Burned' the ubuntu.iso to the USB flashdrive.

Sounds to me like a bad 'Burn'. Burn ubuntu.iso again to the USB drive. Before that do a **[MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM")** on your ubuntu.iso to see if your download is not corrupt.
Is there a Windows in the picture? If yes, then what version?
What Graphics do you have onboard? What model Asus?

---

### Post by kingvv on 2013-11-01
Yes, is Ubuntu 13.10 64 Bit. MD5Sum Check is OK.
I have a Notebook Asus N750JV with Nvidia GeForce GT 750M and Windows 8.1.

---

### Post by fantab on 2013-11-01
Windows 8.1.

Have you disabled "**[Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")**"?
Have you disabled "**[Fast Boot]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm")**"?
If you are welcomed to 'Black Screen' upon booting then usne '**[NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132")**'.

If your Windows is booting with UEFI then you HAVE to boot and install Ubuntu in UEFI mode.

Good Luck...

---

### Post by kingvv on 2013-11-02
Fast startup e Fast Boot are disabled.
We tried the version 12.4 the result does not change.

Ubuntu being installed in USB Pendrive with UNetBootin and does not allow you to press F6 because the screen is not existent.

:-k

---

### Post by fantab on 2013-11-02
Try again, it will be there.

---

### Post by kingvv on 2013-11-02
> **fantab said:**
> Try again, it will be there.


" If you are welcomed to 'Black Screen' ... " (This screen is not existent)

Instead of using the program UNetBootin with which could I install Ubuntu 13.10 64Bit to USB Pendrive ?

---

### Post by kingvv on 2013-11-09
No reply ? :(

---

### Post by fantab on 2013-11-09
When you boot USB what optiton are you selecting on BIOS/UEFI boot menu (not grub)?
You should choose USB EFI and not USB PMAP. Sometimes you have to choose USB-HDD.... Check those things.

Burn the .iso again to the USB. And I hope you have done the MD5Sum Check on the downloaded .iso as suggested earlier.

---

### Post by oldfred on 2013-11-09
Since it is a new Haswell or 4th gen Intel, best to use 13.10. A lot of kernel changes and Intel driver changes were made to support the newest chips. Until 12.04 comes out with next refresh I doubt if it will work with your system and then you will be close to 14.04 which may even be better.

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)


These were different brands but one of the few Haswell systems that did evenually work.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by gcbzzzz on 2014-02-12
I did all the things suggested here... though i am not sure i understand what i should be looking in the message wight before mine :/

downloaded 13.10. md5 checks out.

tried writting to iso with `dd bs=4M`... tried now wipping the USB device, creating a fat32 partition, and using netbootin.

tried several USB medias. already.

computer is a ASUS vivobook S200E.

All options in the bios that might impact anything here are off. fast boot. ccm. anti-theft. etc.

it boots up until this:
[IMG]https://lh5.googleusercontent.com/-WxCCm1fXb6U/UvvcacDYZrI/AAAAAAAABHc/QzAdOqfggYU/s640/IMG_20140212_123214.jpg[/IMG]


--- 
edit: maybe relevant... right before the boot options, i can see a UEFI not found message flash very fast... can't read it all.

but, this BIOS does not boot anything other than UEFI, what am i getting?

---

### Post by oldfred on 2014-02-12
@gbczzzz
Better to start your own thread.
Are you getting grub menu at start of install or boot to live mode? Or accessibility screen?
What cpu and video card, chip?
Post in new thread details.

---

### Post by gcbzzzz on 2014-02-12
@oldfred, why another thread? just because i'm a different person? than OP?

it is still the very same version of ubuntu, and all his info matches mine... yes, i was getting the grub menu, same as OP as you can't get to that error on stage1 or 2, i guess. but any option (test, install, test disc, etc) ended up on that same point.

but, anyway, after checking the md5sum a hundred times, and writting on a dozen usb drivers, sd cards, etc... i gave up and burned a DVD. and everything worked. slow, wasteful, but worked.

---

