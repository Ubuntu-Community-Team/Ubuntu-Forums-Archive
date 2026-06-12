---
title: "Live CD problems!"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Philio on 2008-01-23
I want to install Ubuntu 7.10 on my PC, had it working fine on my laptop for a few weeks.
I boot the live CD to install however my keyboard and mouse do not work... I have a Logitech bluetooth keyboard/mouse, it is supposed to work even without bluetooth support as the machine should detect them as USB devices however on the live CD nothing works at all!
Can anyone help me to get this working?

---

### Post by jeffus_il on 2008-01-23
Here is a thread dealing with your problem.
[http://ubuntuforums.org/showthread.php?t=594624](http://ubuntuforums.org/showthread.php?t=594624)

---

### Post by Philio on 2008-01-23
Thanks, that would work, but... It requires a working keyboard to open up terminal and run these commands!!! I don't have another keyboard I can plug in... Why don't the mouse and keyboard work in the USB mode like they do in DOS/Windows if you don't have drivers installed?!

---

### Post by jeffus_il on 2008-01-23
The keyboard has a lot of problems in Windows as well see:
[http://reviews.pricegrabber.com/keyboards/m/11209327/](http://reviews.pricegrabber.com/keyboards/m/11209327/)

I will have a look around to see if there is some work around for Linux.
You can consider installing from within Windows, and reboot the machine. log in thru ssh and make the needed changes.

---

### Post by Philio on 2008-01-23
I've got the diNovo one, not really had any problems with it in Windows, it has lost connection a few times but then reconnects after a couple of seconds. However I know someone with the same kit that has a lot of connectivity problems, we run almost identical hardware as well so it's kinda strange!

I tried the Windows installer and got an error about bcdedit.

It's a bit odd really the keyboard works in USB mode so enable me to select an option from the install menu but no response from either the keyboard or mouse once the live CD has booted.

---

### Post by jeffus_il on 2008-01-23
Have you looked at the bios usb keyboard settings?

---

### Post by Philio on 2008-01-23
> **jeffus_il said:**
> Have you looked at the bios usb keyboard settings?

The only settings under USB in the BIOS are enabled for both keyboard and mouse.

---

### Post by Philio on 2008-01-23
I downloaded a Fedora 8 Live CD purely to see if it was a hardware specific issue and it works fine, doesn't look like it starts Bluetooth by default, prehaps there is a way I can disable bluetooth on the Ubuntu Live CD before boot? I don't particularly want to install Fedora it's a bit rough around the edges from past experiences with it.

---

### Post by jeffus_il on 2008-01-23
I'm not sure, some distros give you F2 and F3 options at boot they list them and you choose them, I don't remember the Ubuntu livecd boot, I will check it out.

---

### Post by jeffus_il on 2008-01-23
Is this a solution for you?
[https://answers.launchpad.net/ubuntu/+question/22843](https://answers.launchpad.net/ubuntu/+question/22843)

---

### Post by Philio on 2008-01-23
That does the trick, thanks very much! :)

---

