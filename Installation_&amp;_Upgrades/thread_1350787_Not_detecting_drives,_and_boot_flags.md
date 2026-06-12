---
title: "Not detecting drives, and boot flags"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by kyleballing on 2009-12-09
First, I tried to run the Ubuntu 64 bit live CD and I got the following error:
*"Unable to find a medium containing a live filesystem*"
The md5sum of the disk image is ok and I burned the disk twice on different burners and get the same issue

Next, I loaded the image on a USB stick and ran the live system. In order to do this, I had to change the BIOS to recognize the USB as a hard drive, then set it to be the first priority hard drive to boot from. Ubuntu was able to load correctly except it does not detect any of my hard drives, therefore I cannot install it correctly.

I tried the LiveCD again, this time I messed around with the boot options. I got Ubuntu to load, but only when I checked all the flags (acpi=off, noapic, nolapic, edd=on, noraid), and ran in safe graphics mode. I was able to perform the installation successfully. When I booted from the hard drive with Ubuntu installed, there was an error in Grub saying it could not find the root directory or something to that effect.

I tried fedora 10 and that seemed to work great except the network drivers didn't seem to work.

I tried openSuse 11.2 gnome liveCD and got the same errors as with ubuntu. I can't run the liveCD without all the flags and in safe graphics mode, and when loaded off a USB stick, my hard drives are missing.

It's been a while since I dealt with Linux, but I feel pretty comfortable with it. Any ideas as to what is going wrong here? (I suspect it has something to do with my BIOS settings)


My machine has a Tseries TF710 motherboard, Dual core Athlon, two large sata drives, a sata CD drive. It was running windows XP 64 and Vista just fine.

---

### Post by phillw on 2009-12-09
hi,

The setting (or even re-installation) up of Grub2 is covered in this excellent area. --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Regards,

Phill.

---

### Post by darkod on 2009-12-09
> **kyleballing said:**
> Ubuntu was able to load correctly except it does not detect any of my hard drives, therefore I cannot install it correctly.

I tried the LiveCD again, this time I messed around with the boot options. I got Ubuntu to load, but only when I checked all the flags (acpi=off, noapic, nolapic, edd=on, noraid), and ran in safe graphics mode. I was able to perform the installation successfully.

I believe you had what I call raid setting remains. Usually this is the reason hdd not to be seen at all. Maybe that's why it worked with "noraid" you used. You should have troubleshooted more before installing, if the LiveCD was not working OK usually you can't expect the installation to work too.
Boot with the LiveCD (usb) again and in terminal execute:
sudo apt-get remove dmraid

Usually you should use that before the install. Since you already installed, don't know if it will be working now. But check. And if that was your problem you should be able to reinstall ubuntu any time now, if you need to.

---

