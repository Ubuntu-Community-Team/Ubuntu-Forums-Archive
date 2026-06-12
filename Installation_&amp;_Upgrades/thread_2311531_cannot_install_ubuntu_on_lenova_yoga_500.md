---
title: "cannot install ubuntu on lenova yoga 500"
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by reevo on 2016-01-28
Have tried version 14.0, 15.0 from DVD and USB . same message
\ubuntu\winboot\wubildr.mbr.   status 0xc000007b.   Cannot load because a required file is missing or contains errors.    Where to next

---

### Post by lisati on 2016-01-28
I'm not sure which versions of Ubuntu you are referring to. There's 14.04, 14.10, 15.04 or 15.10, but no 14.0 and 15.0. :confused:

By the way, wubi isn't currently supported.

---

### Post by reevo on 2016-01-28
Sorry 14.04 and 15.10

---

### Post by lisati on 2016-01-28
All is good. You might want to have a read of [this]("http://ubuntuforums.org/showthread.php?t=2229766") thread.

---

### Post by reevo on 2016-01-28
Confused about wubi . this is a new computer with windows 10. Isn' t wubi for vista and windows 7

Further info. Purchased computer today. Downloaded Ubuntu from website today and tried both versions 14.04 and 15.10. Why am I dealing with an unsupported command on a new computer with the latest ubuntu ?

---

### Post by lisati on 2016-01-28
Did you boot from the CD/DVD or did you start it with the Windows "autoplay" facility?

---

### Post by reevo on 2016-01-28
Booted from DVD. Then tried from USB. Same error each time

---

### Post by Bucky Ball on 2016-01-28
As stated, Wubi is no longer supported by Canonical or here, even though it is still included on some ISOs. Don't use it.

You created a DVD. How? You create a USB. How? What software did you use? Did you drag and drop the ISO onto the media? If so, that won't work. For DVD you need to burn a disk image. Use whatever software you use to do that in Windows. For USB, try either of the below. Rufus apparently works but never used it (never needed to). 

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

If you get that far, is Windows installed in UEFI mode or legacy/BIOS? This is important. Check out in BIOS because whatever mode that's installed in, that's what you need to install Ubuntu in. Once you know, boot the install media in that mode and when at the options 'Try Ubuntu'. 

That will take you to a desktop where you can take a 'test drive' before installing. This 'live' session from install media WILL NOT change anything on your hard drive (unless you manually do so intentionally). Everything working as expected?

If you don't get this far, let us know where you hit the brickwall and we'll see if we can get over it.

---

### Post by reevo on 2016-01-28
You may realise I am new to this with limited computer knowledge. I tried ubuntu by burning a disc from the ubuntu download site and loaded it onto an old dell computer and it has been working fine. Purchased a new lenovo because I was told they work well with Linux. Loaded this disc into new DVD burner (lg in) and followed same procedure and got same message .  Overwrote DVD with version 15.10 still the same.
  Will see how I go with your instructions.

Again my ignorance prevails. I can see that my computers boot mode is UEFI. When I get the error message trying to load ubuntu I can access this configuration. Am I suppose to change something here or am I downloading the wrong version of ubuntu for my computer. Is there a different option at the download stage ?

---

### Post by lisati on 2016-01-28
WUBI is a tool that, in theory, lets you install Ubuntu "within" Windows, and normally only starts when Windows is running. It doesn't always play nice with newer systems.

I'm mildly surprised that a mention of "wubidir" is made in an error message if you're actually booting from the disk instead of Windows.

---

### Post by Bucky Ball on 2016-01-28
It doesn't play at all with UEFI.

---

### Post by reevo on 2016-01-28
Will try again tomorrow. Had to reset the computer because internet explorer stopped working. Thanks for help will be back for more help tomorrow. It has broken me tonight

---

### Post by ajgreeny on 2016-01-28
Here is a very good and comprehensive article about installing Ubuntu 14.04 in many different situations, ie MBR BIOS, UEFI using GPT partitions etc etc, all of which may sound very strange to you.

However, have a good read through and then come back to ask us specific questions, telling us also exactly what hardware the Lenovo Yoga 500 uses.
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by reevo on 2016-01-29
Have done some reading but the challenge is still wether I am getting to the starting line with a broken leg. Today i have downloaded ubuntu 14.04.3 to my computer. I then copied it to a usb .When I open the usb I can see a wubi file in there. The feedback I have had has indicated that wubi is an old unsupported file. Why is it in the download for the current version considering the error message relates to the wubi file. I have been able to get into the firmware and change the booting sequence so the first boot was from the usb. This did nothing, just loaded straight into windows. The computer does boot from UEFI and I cannot see the option of changing that (if that is what I should be doing ) or do I get a download of ubuntu that is in UEFI , problem is I cannot see any option when I go to download that can change any of these parameters.
  So now as I have been doing this my new lenovo Yoga seems to have got a virus so I am currently doing a total reset (i hate windows) Writing this from old Dell which is running ubuntu beautifully.

---

### Post by Bucky Ball on 2016-01-30
Enter BIOS. You will see the option to boot the USB in UEFI mode. That is all you have to do. 

Please give a link to where you are downloading 14.04 from. You copied the ISO to a USB? You don't do that. You need to create a bootable USB using either of the below (or other methods). Simply putting the ISO on a USB won't do anything. 

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Bottom line: You don't need to be 'opening the file on USB'. What file? The ISO? Don't do that, use one of the USB creators above, ignore Wubi, boot the USB in UEFI from BIOS when you're done and report where you get to.

---

### Post by reevo on 2016-01-30
UNetbootin failed. Would not recognize the sudo prompt. Now going to go with dvd burner. In BIOS no option of changing USB boot to UEFI . It shows that the boot mode is UEFI and that the usb boot is enabled. Cannot change either of these. Can only change the boot sequence. Downloading from ubuntu.com/download/desktop version 14.04.3-desktop-amd64.iso from mirror.as24220.net. The only option from this download is to choose 32 or 64 bit, i have no access to UEFI as a download option. 
  I am expecting the download issue to be the same but I am hoping something went wrong when I first tried. Should i change the boot sequence so windows is not first and make the dvd boot first, could this bypass the wubi issue that started all my trouble.
 Lenovo Yoga 500-141SK Intel i5 6200U CPU 2.30GHZ System memory 4096MB.
 This process went off without a hitch when I did this all with the Dell laptop, here I am now feeling like a complete knob as I chase my tail around a process that I am clearly lacking in knowledge of.

Success of a kind, Burnt image to disc and changed booting procedure and I am going. Issue now is wifi. The network settings are only wired , no provision for wireless. Have no internet. Any ideas ? Thanks for the help so far, my knowledge is growing

---

### Post by wepbep on 2016-02-08
(Bios: One thing I found was when you want secureboot to disable you have to use a password, DONT forget to delete it ! And disable windows fastboot in windows rescue.)

Furthermore, to get your wifi working it is easier to use 15.10 and wait for 16.04lts.

15.10 worked out of the box for me yoga 500 15isk

---

### Post by Vidar30 on 2016-02-14
I'm able to install Ubuntu on my Lenovo Yoga 500 but its running so slow that its basically unusable. It hangs all the time. Can't see anything out of the ordinary in the log files but what do I know - anyone here got Ubuntu working on this laptop?

EDIT: It was due to faulty USB

---

### Post by virgosun on 2016-04-09
I quad boot Windows 10/Ubuntu 15.10/El Capitan 10.11.4/Android x86
I even run Ubuntu from PXE
I don't know your Y500 version
See [https://www.youtube.com/watch?v=lZjFVmu6spw](https://www.youtube.com/watch?v=lZjFVmu6spw)

---

