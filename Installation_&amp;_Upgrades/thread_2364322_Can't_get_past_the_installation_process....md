---
title: "Can't get past the installation process..."
date: 2017-06-21
forum: Installation &amp; Upgrades
---

### Post by austinmesser on 2017-06-21
Hey all, I've been attempting (with very little success) to install Ubuntu 16.04.2 onto a Toshiba Satellite CL15t-B1204 from a Mac running OS X 10.6.8. I've finally made a drive with the iso file, but I've been unable to progress past the installation phase. Upon completing the process, the restart brings me back to the "Install Ubuntu," "Try Ubuntu Without Installing," etc screen. I tried accessing the BIOS, and after doing so I found that switching from the USB back to the internal disk upon start up produces the same initial installation menu. Is there anything additional that I have to do manually to ensure that the computer is reading the internal disk during a boot or reboot?

---

### Post by kyrithis on 2017-06-22
I have to ask, sorry. Have you removed the USB after install? Sometimes your BIOS likes to default straight to the last successful boot device (In this case, the USB) but will revert back to the boot order if said device is removed.

If you've done that, post back and we'll get to work on next steps.

---

### Post by yancek on 2017-06-22
The first sentence in your post seems to indicate you are trying to do a network install, installing to a Toshiba from a Mac.  Is that correct?  If not clarify, did you download the official iso file from the Ubuntu site and put it on a usb?  What software did you use to put it on the usb?  What installation type option did you choose?  It sounds like you might have done a 'frugal' install but more info is needed.

---

### Post by austinmesser on 2017-06-23
> **yancek said:**
> The first sentence in your post seems to indicate you are trying to do a network install, installing to a Toshiba from a Mac.  Is that correct?  If not clarify, did you download the official iso file from the Ubuntu site and put it on a usb?  What software did you use to put it on the usb?  What installation type option did you choose?  It sounds like you might have done a 'frugal' install but more info is needed.

Sorry for the late reply, I work weird hours and this has been somewhat of an "after hours" project of sorts. I'm sort of learning as I go when it comes to these sort of things, and as such I'm not sure I know what you mean by a "network install." Below is a list of the actions I've taken:

1) Download Ubuntu 16.04.2 iso image from Ubuntu onto a Mac (OS X 10.6.8)
2) Delete all files on an 8gb USB disk, utilize the Mac's "Disk Utility" application to erase and reformat? the USB
3) Open the "Terminal" application and, after using "diskutil list" and "diskutil info" to find out where I should write the iso file (diskx in the following command), write the iso file to the usb using "sudo dd if=/Path/isofile.iso of=/dev/diskx bs=1m"
4) Eject USB from the terminal
5) Change BIOS settings on Toshiba Satellite to boot from USB
6) Insert the USB and perform the installation of Ubuntu

Once it asks me to restart the computer after having completed the installation, leaving the USB in, taking it out, and going into BIOS to specifically request a change to booting from the internal disk all yield the same result, which takes me to a "GRUB" screen (black with white lettering) that asks whether I would like to install, try Ubuntu, or install an OEM thing.

---

### Post by austinmesser on 2017-06-23
> **kyrithis said:**
> I have to ask, sorry. Have you removed the USB after install? Sometimes your BIOS likes to default straight to the last successful boot device (In this case, the USB) but will revert back to the boot order if said device is removed.

If you've done that, post back and we'll get to work on next steps.

I believe I tried this the other night, but in the spirit of due diligence I just gave it another shot. I got a message that said "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key"

I went into BIOS on my second attempt and, sure enough, USB was at the top of the boot order. I went into settings and adjusted the internal disk to the top of the list, and hit "save and exit." Upon restart I got the exact same result.

---

### Post by ubfan1 on 2017-06-23
With 2G of memory, you might be better off trying lubuntu.  Did you ever select the "try" option when booting the USB?  Did it work?  Assuming a UEFI install, not dual booting, 64 bit, gpt partitioned disk, you will need an efi partition, a root partition, and swap -- Were those set up in the install?

---

### Post by mörgæs on 2017-06-24
I don't see 2 GB of memory mentioned. 

For a computer with touch screen I recommend that you stay with Ubuntu.

---

### Post by ubfan1 on 2017-06-24
The specs of a Toshiba Satellite CL15t-B1204 say 2G, not user upgradeable.

---

