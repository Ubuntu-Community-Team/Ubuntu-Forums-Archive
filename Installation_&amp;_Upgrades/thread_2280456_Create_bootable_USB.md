---
title: "Create bootable USB"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by ellie3 on 2015-05-30
I want to install Ubuntu onto an old computer with no curernt OS. I followed the instructions on the Ubuntu webpage to create a bootable USB, but the computer won't reconise the USB. I have changed boot options to boot from USB. There is a wubi.exe which copied to the USB. Is that meant to be there? So new to this.

---

### Post by sammiev on 2015-05-30
Hi ellie3 and welcome.

Not sure what OS you are using so here is a few options to create the bootable USB.

You never posted the specs of the computer you wanted to install ubuntu to.

Which flavour and version is also a big help.

[here]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") and [here]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu")

---

### Post by ubfan1 on 2015-05-30
You don't have Windows, so forget about the wubi.exe.  What model computer are you trying to install to?  Some of the newer UEFI machines may have issues booting USB with secure boot enabled, but that should not be an issue on an older computer.  Try changing USB ports, try removing other USB devices (may be a power issue), try booting the USB on another computer.  Did you hashcheck the downloaded iso? 
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
Once you can boot the USB, check it and the computer's memory:

Select the media check before trying to install:
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Do a "memory check" (another live-media menu choice) on your PC.
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by sudodus on 2015-05-31
Welcome to the Ubuntu Forums :-)

You have already got very good advice in the previous posts. Maybe I can add some tips to it.

1. Make sure the downloaded iso file is good.

- That is suits your computer. If the computer is old, standard Ubuntu might be too demanding, and you should get a lighter flavour, Lubuntu, Xubuntu or Ubuntu Mate. If the computer is very old, you might need an ultra-light linux distro (outside the Ubuntu family), for example Wary Puppy, TahrPup or 
Tiny Core. See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

- Please specify your computer (the target computer, where you want to install Ubuntu)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- That the downloaded file was downloaded without transfer errors. Check the md5sum.

2. Make sure that the USB pendrive works

- What operating system is there in the computer, where you created (want to create) the USB boot drive?

- Please try the USB boot drive in more than one computer - to make sure it works.

- Try with other tools, if you have problems, for example according to this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

3. Please come back with more details (descriptions and questions)

---

