---
title: "Quantal Install on PPC iMac Gone Wrong"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by moore.bryan on 2012-09-02
I've recently needed to reimage my aged iMac G4 FlowerPot due to Debian Squeeze's PPC support not being really "up-to-date" enough for some of things I need to do. Needless to say, I was incredibly excited to see Quantal supports my architecture. My to my chagrin, I discovered my CDROM no longer functions on the machine, but thought to myself, "no big deal, I'll just USB boot." Well, any of you who have tried such a thing on a PPC iMac knows that's the dumbest thing I could have ever said or thought, as Odysseus had an easier time getting home than we have in usb-booting on PPC.

Regardless, following Shawn Corey's excellent guide [here]("https://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux#creating_a_bootable_usb_drive_from_a_x86_machine_in_linux") and making a few of my own adjustments, I was able to do what I needed to and even could boot the install. Install itself goes swimmingly until setting-up the package installer (aka apt). No errors are thrown, but apt is not installed. I know this because when running a rescue and dropping into a root shell, there is no apt. I can continue running the installer and even reboot the machine, but I run into the display error related to not having xserver-xorg-video-nouveau installed.

And now you see my issue... I need to apt-get the nouveau and can't because apt isn't installed.

I'm stuck. Help?

UPDATE
I've been able to get around my previous problem with apt-install, a program I knew nothing about, but which--apparently--acts as apt inside of the installer. From there, I was able to install the things I thought I needed and rebooted; however, I'm without a graphical startup. I tried the fixes mentioned in [this]("http://ubuntuforums.org/showthread.php?t=1769801") thread to no avail. I'm sure it's because Quantal handles xorg differently, but I'm not sure how. I seem to remember reading an article about why xorg.conf was being removed, but can't remember where I saw it. New help?

---

