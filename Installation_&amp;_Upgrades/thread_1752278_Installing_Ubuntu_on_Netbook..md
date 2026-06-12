---
title: "Installing Ubuntu on Netbook."
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by JamesBwoii on 2011-05-07
I'm trying to install Ubuntu 11.04 on my Acer Aspire One. This has no DVD drive so I'm using a USB.

When I boot the Acer using the USB it just stays on the same screen saying:
"SYSLINUX 4.03 2010-10-22 EDD Copyright © 1004-2010 H. Peter Anvin et al"

I then tried to install Ubuntu 10.10 Netbook version, but got the same error.

What's going wrong?

---

### Post by Dutch70 on 2011-05-07
Hi and welcome to UF

You may want to try downloading & using the "alternate cd install".

---

### Post by JamesBwoii on 2011-05-07
> **Dutch70 said:**
> Hi and welcome to UF

You may want to try downloading & using the "alternate cd install".

Do you mind telling me where I can find this? And do I need a specific netbook version?

---

### Post by Dutch70 on 2011-05-07
Remember, google is your friend. :)

[[COLOR="Red"]http://releases.ubuntu.com/11.04/[/COLOR]]("http://releases.ubuntu.com/11.04/")

I think 11.04 is the same for the netbook & desktop.

---

### Post by JamesBwoii on 2011-05-07
> **Dutch70 said:**
> Remember, google is your friend. :)

[[COLOR="Red"]http://releases.ubuntu.com/11.04/[/COLOR]]("http://releases.ubuntu.com/11.04/")

I think 11.04 is the same for the netbook & desktop.

I've tried that using Unetbootin and pendrivelinux and have received the error message with both of them. I'm now trying it with linuxliveusb.

---

### Post by frncz on 2011-05-07
I have installed natty 11.04 amd64 on the acer aspire one netbook yesterday.
I have not had any major problem with the installation from USB, having used the 'startup disk creator' application to create the USB from the downloaded .iso file.
It all runs fine.
A few comments:
with 1 gb memory, the system is quite slow. Installing 2 gb memory makes a big difference
I installed / in a btrs partition, and /home in a ext4 partition. I did overwrite the pre-loaded windows 7 and android.
On boot, I get an error message:
'error: sparse file not allowed, please hit key to continue..' or something like that. Hitting the return key gives a proper boot and it all runs smoothly.

I installed ccsm to reduce the launcher icon size to 32
Annoyingly some of the evolution set-up windows are too big for the screen. I need to switch workspace to reach the bottom of the windows to click on 'continue' etc.
Virtualbox works fine, as well as XP installed in it.

I hope this helps

Mike

---

### Post by Dutch70 on 2011-05-07
> **JamesBwoii said:**
> I've tried that using Unetbootin and pendrivelinux and have received the error message with both of them. I'm now trying it with linuxliveusb.

Have you checked the md5sum of the .iso you downloaded? 
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Also, check the cd/usb for defects by selecting "check cd for defects" instead of "try ubuntu" or "install".

You also may want to try a different usb stick if you have one. Some have U3 software that prevents booting Ubuntu & some just seem to have a bug. I don't want to lead you down the wrong path, just some things to consider.
[[COLOR="Red"]http://psychocats.net/ubuntu/usb[/COLOR]]("http://psychocats.net/ubuntu/usb")

---

