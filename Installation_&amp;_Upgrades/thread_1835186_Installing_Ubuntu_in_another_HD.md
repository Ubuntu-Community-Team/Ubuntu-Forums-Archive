---
title: "Installing Ubuntu in another HD"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by harikumar on 2011-08-28
I have two hard disks in my PC One HD is loaded with Windows XP. I want to install ubuntu 11.04 in the other HD  and to have dual boot. I am a novice to ubuntu. Please provide a link where I can find instructions to do this

---

### Post by Hakunka-Matata on 2011-08-28
If you haven't yet tried Ubuntu on that machine, I'd suggest you do that first.  Boot to an Ubuntu liveCD and choose "try Ubuntu without installing" and see how it works on your hardware.

---

### Post by YesWeCan on 2011-08-29
Hi and welcome to the Ubuntu forums.

I second Hakunka-Matata's advice.

If the drive you want to use for Ubuntu has nothing on it you want to keep then I would disconnect your XP drive and boot the Ubuntu CD/USB and select install. Choose "use entire disk". After the installation is finished, you can reconnect the XP drive and set you BIOS to boot the Ubuntu drive. Once Ubuntu has booted, open a terminal and run
[COLOR="Navy"]sudo update-grub[/COLOR]
to add XP to the Grub boot menu.

[Disconnecting the XP drive during the Ubuntu install is not necessary but it avoids a problem with the installer where it may install Grub on the XP drive and not warn you. You have to intervene to stop it doing this and it is not obvious how]

---

