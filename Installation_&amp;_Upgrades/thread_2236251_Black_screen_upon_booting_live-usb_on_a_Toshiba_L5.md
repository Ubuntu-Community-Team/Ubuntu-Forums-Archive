---
title: "Black screen upon booting live-usb on a Toshiba L50D -B"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by mm144 on 2014-07-25
Hi, I was wondering if anyone could guide in the installation of Ubuntu 14.04.  
I cannot get past the boot up and just shows a black screen.
The Toshiba L50D-B that I have has an AMD A10-7300 processor, and since it's an APU, it has an associated GPU, Of R6 type (don't know the Radeon number associated)
It has Windows 8, with UEFI with secure boot, which is disabled currently.  it has similar specs to [http://www.ubuntu.com/certification/hardware/201403-14902/](http://www.ubuntu.com/certification/hardware/201403-14902/), if not identical.

At first I thought it was the UEFI Secure boot, but it after many attempts, even after disabling secure boot, to boot Ubuntu, I tried Linux mint.  There, I got something, posted as an attachment.    Which leads me to believe, it's a Video card issue.

Dual booting is a requirement so, disabling UEFI is out of the question.  I just don't what to try next.

---

### Post by Bucky Ball on 2014-07-25
Yea, when you boot from the USB and get to the options screen (Try, Install, etc.) hit F6 and choose 'nomodeset' option. Continue. Any luck?

You don't need to disable UEFI (in fact, don't as Win8 is installed in UEFI if preinstalled on the system by default), Ubuntu should handle that fine. Just, as you have, disable secureboot and all that stuff Win8 related. Not even sure if that's required with 14.04. I don't advise choosing the option, 'install alongside Win' though. Probably best to 'Something Else' and partition manually. The other option can be a little buggy and wipe the drive!

---

### Post by mm144 on 2014-07-25
Thanks for the reply, but when I boot, the usb, I am not greeted with the standard Ubuntu Bios boot up screen which has nomodeset as a visible option.  Instead, I have three options, which basically boils down to, try, install, and check boot medium.  Nowhere do I see "nomodeset" as an option.

---

### Post by sudodus on 2014-07-25
How did you make the USB boot drive? From Ubuntu or Windows or MacOS?

If you made the USB drive with the ***Startup Disk Creator*** alias usb-creator-gtk or with ***mkusb***, you can try F6 according to this wiki page

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you made it with Unetbootin, you press the TAB key to edit the boot commands, and add the boot option at the end of the line with **quiet splash**.

See these links for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by mm144 on 2014-07-25
I tried both unetbootin (without quiet splash) and Universal-USB-Installer-1.9.5.4.  I could try the boot option quiet splash, once I get back from work in a couple of hours.

---

### Post by sudodus on 2014-07-25
I'd recommend ***Unetbootin*** of those two tools.

And ***no***, you need not try quiet splash, I only mentioned them to indicate where to add the boot option **nomodeset** (and maybe later on some other boot options).

---

### Post by Bucky Ball on 2014-07-25
Yes, when you get to the 'Try' 'Install' 'Check' screen, hit F6. See my first post. Then you should see a pop-up with a bunch of options. Choose 'nomodeset'. Proceed.

---

### Post by mm144 on 2014-07-25
As i said, there's no F6 option, but thanks to sudodus, i used the edit function of grub to manually add it to the grub settings.  Have now installed it and had to once again manually add nomodeset to grub for it to boot. (Now to figure out how to make it the default)  I am now typing this in ubuntu 14.04! Thanks to you both.

---

### Post by Bucky Ball on 2014-07-25
Good news. Please mark the thread as solved to help others by following the second link in my signature. Good luck.

---

