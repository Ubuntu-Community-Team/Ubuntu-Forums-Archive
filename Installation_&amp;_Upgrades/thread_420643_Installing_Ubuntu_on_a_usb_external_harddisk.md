---
title: "Installing Ubuntu on a usb external harddisk"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by chadbst on 2007-04-23
I have a USB enclosure with a Maxtor 40G harddrive enclosed.  After installing Ubuntu on that disk, I get GRUB error 21.

Can someone please help me out.  I want to have Windows XP(for my schoolwork - long story) on my internal harddrive and Ubuntu on my external harddrive.

---

### Post by bwhite82 on 2007-04-23
In order for this to work, you need to install grub onto the MBR of the external drive, and restore your Windows MBR for your internal drive. Then, when you want to boot into linux, you have to enable USB as the first boot device in your BIOS so that it immediately goes to grub. This way, when you want to boot to windows, you just make sure that your external drive isn't connected.

---

### Post by chadbst on 2007-04-23
Thank you soldierboy for the reply.  However, what you are telling me to do is what I don't know how to do!  I figured GRUB was installed on my internal drive.  I have since restored the MBR for the internal drive.  However, when I install Ubuntu to the hard disk, it installs to the external hard disk, but GRUB gets installed on the internal drive.  

Do you, or anyone for that matter, know how I can force GRUB to be installed on the external drive?

---

### Post by bwhite82 on 2007-04-24
I haven't installed Ubuntu in quite a while, but I thought there was an option during installation that asked you where you want the boot record to go?

---

### Post by mpvano on 2007-04-24
What version of Ubuntu?

If you are installing 7.04 - Feisty (and possibly some other versions), you only get  the option to decide where to install Grub if you use the ALTERNATE INSTALL CD.

The "Desktop" Cd  that boots into a live system doesn't give you any choice - it just silently installs grub into your MBR. I think this is a dangerous thing and should be fixed to at least give you a warning!

Because the bulk of the GRUB goot code still lives on the installation target disk, installing to the MBR of the first disk can break other OS installations under some circumstances (e.g. when installing to an external drive that's not always going to be plugged in!)

Mario

---

