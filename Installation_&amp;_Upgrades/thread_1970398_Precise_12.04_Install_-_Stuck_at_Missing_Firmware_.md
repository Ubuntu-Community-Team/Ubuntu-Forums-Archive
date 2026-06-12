---
title: "Precise 12.04 Install - Stuck at Missing Firmware Files"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by CraigThomas on 2012-05-01
I have a dual booting Toshiba Satellite R630-13T (Windows 7/Ubuntu 11.10).  I want to replace 11.10 by doing a fresh 12.04 install leaving me with a dual booting (Windows 7/Ubuntu 12.04).

I am using the Ubuntu 12.04 64bit Alternate CD - because I want a command line system first and may add the GUI later.

I am currently part the way through the install and have encountered the following message:

Detect network hardware
-----------------------
Some of your hardware needs non-free firmware files to operate.  The firmware can be loaded from removable media, such as a USB stick or floppy.

The missing firmware files are: brcm/bcm43xx-0.fw
If you have such media available now, insert it, and continue.

Load missing firmware from removable media?
Yes / No

I understand the message and the reason for it but where can I get the firmware file from?

I tried searching on here and Google too, but I've mostly found instructions on how to get the Broadcom wireless card working once everything is installed (possibly using fwcutter).  But being picky and with a nice new set up, I'd like to just find and add this driver at this point in the install if possible.

My searches threw up the following, without being entirely obvious what I need to do:
[https://help.ubuntu.com/12.04/installation-guide/amd64/loading-firmware.html]("https://help.ubuntu.com/12.04/installation-guide/amd64/loading-firmware.html")
[http://cdimage.debian.org/cdimage/unofficial/non-free/firmware/]("http://cdimage.debian.org/cdimage/unofficial/non-free/firmware/")
[http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

The wireless is not crucial to the install as I have a wired connection but I would like to do a 'proper, clean' install.

Appreciate any help,

CraiG

---

### Post by CraigThomas on 2012-05-01
Plenty of views, but no replies, guess it's not an easy/quick fix.

I chose "No" for now, carried on with the install (going home soon) will see if I can get wireless working post-install.

If anyone does know what I should have done or where I can get the firmware please let me know, as I'll quite happily re-install again tomorrow just to "get it right".

Thanks,

---

### Post by oldfred on 2012-05-01
I see the package in Synaptic, so from command line cannot you not just download as shown in the help.ubuntu link you have in your previous post?

---

### Post by CraigThomas on 2012-05-02
> **oldfred said:**
> I see the package in Synaptic, so from command line cannot you not just download as shown in the help.ubuntu link you have in your previous post?

Thanks Fred, but I was still in the middle of the install so there's no command line at that point, just a 'yes' or 'no', which if you answer 'yes' I'm guessing it'll look for the file on a connected USB or CD.

This maybe more of an issue for someone installing Ubuntu with only wireless as an option.  (admittedly the set up I'm going for is not the usual one).

---

### Post by roton on 2012-05-27
I had this same message today when installing. I couldn't find the file either so ended up just saying no.
The strange thing is that the wireless worked after install :s

---

### Post by AndreaCanesi on 2012-06-01
You can take it from this package:
[http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/linux-firmware_1.79_all.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/linux-firmware_1.79_all.deb.html)

Download it from a repo, open it with an unzipper (like 7zip on windows), copy your file on a usb key and insert it when requested.

After the installation remember to install all the package (for maintenance).

---

