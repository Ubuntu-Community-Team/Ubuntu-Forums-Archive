---
title: "Can't install 10.10 from USB"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by davidbr on 2010-10-13
I have created a USB stick for 10.10 Desktop Edition from Windows (following the instructions [here ]("http://www.ubuntu.com/desktop/get-ubuntu/download")(i.e. using Universal USB Installer).

After I boot my PC from the USB I only get a Syslinux line saying "SYSINUX 4.02 2010-07-21 ... Peter Anvin et al" and that's it.
Nothing happens.

I even tried editing syslinux.cfg and remove the 'ui' as explained [here]("http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/"), but that didn't help also.

---

### Post by C.S.Cameron on 2010-10-13
Have you checked the MD5SUM of the downloaded iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Using the Startup Disk Creator from the Live CD worked for me. I have heard that UNetbootin and Universal are not working with 10.10 yet but have not tried them myself.

---

### Post by 1danjack on 2010-10-13
Had exactly same problem trying to insatll 64bit version of 10.10 via Universal USB Installer. This was onto a newish laptop.

I md5sum'd the original iso and all was ok.

(Original USB stick may also have been ok as when I then tried it on my 32bit laptop and the installer got as far as telling me it couldn't install 64bit on 32bit.)

I've another machine with 10.04 installed so I started that created USB startup disk via "startup disk creator". This is using the same 10.10 64bit iso and same usb stick. The stick was created sucesfully and now 10.10 is all installed ok.

To the OP I recommend three alternatives (after you've md5sum'd your iso to be sure that's ok):
1. burning a CD of 10.10
2. downloading 10.04 running that from USB and then creating another 10.10 USB with startup disk creator
3. trying to find an older version of the windows installer, the previous one was: Universal-USB-Installer-1.7.9.7 and use that to make a 10.10 USB stick

---

### Post by davidbr on 2010-10-14
I finally burnt 10.10 onto a CD.

This USB issue is really a bad welcome for new ubuntu users.

---

### Post by libssd on 2010-10-14
> **davidbr said:**
> I finally burnt 10.10 onto a CD.

This USB issue is really a bad welcome for new ubuntu users.
My introduction to Ubuntu involved writing the installation ISO to a USB from Windows (netbook, no optical drive). The process worked exactly as documented. This was with Ubuntu 9.04 last year. Since then, I have prepared all subsequent installers using Startup Disk Creator. Several different brands of USB, all at least 2gb, no problems with any of them. I always do a secure erase (writing zeroes to the entire USB) before writing the ISO to it.

---

### Post by 1danjack on 2010-10-31
Hi libssd, how do you write zeros to your usb, also how long approx does it take?

---

### Post by libssd on 2010-10-31
> **1danjack said:**
> Hi libssd, how do you write zeros to your usb, also how long approx does it take?
It's one of the secure erase options of Apple's disk utility. I suspect you could achieve the same result using shred:

$ sudo shred /n1 /dev/sda

(substitute device name of your USB for /dev/sda )

---

