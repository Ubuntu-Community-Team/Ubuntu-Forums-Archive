---
title: "How do I install windows again with Ubuntu?"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by hermespag on 2007-03-27
I recently switched motherboards because the last one stopped working and the windows I had installed alongside Ubuntu is no longer usable. Whenever I choose windows, it loads but stops before completion. I have tried to re-install Windows (The originial cd that came with the computer) and Ubuntu (A 6.10 live cd) and they both won't. Whenever I try to restart the computer to install either operating systems, it just goes straight to the window that lets you choose windows or Ubuntu. If you're thinking that the system doesn't detect my drives, you're wrong. The computer detects and I have used it as a matter of fact.

My question is: How do I install Windows again? My preference is to re-install windows completely and then install Ubuntu on another partition after.

---

### Post by tommcd on 2007-03-27
Sorry for the dumb question, but are you sure the BIOS is set to boot from the cdrom drive? If the windows disk and ubuntu disk are good (perhaps try to boot them on a different PC) then they should just boot to the install CD after you restart with the CD in the drive.

---

### Post by louis_nichols on 2007-03-27
You have to make sure your BIOS is set to boot from CD first. From what you're saying, it sounds like it's not currently set that way. Please rfer to the user manual of your mobo on how to do this.

After that is sorted, it will be just a siple matter of installing the 2 OSs. Windows first, then Ubuntu.

---

### Post by ssican on 2007-03-27
Did you try choose windows or Ubuntu ? Press the arrow to choose and after press ENTER.
Perhaps this page help: [http://www.windowsreinstall.com/](http://www.windowsreinstall.com/)

---

### Post by hermespag on 2007-03-27
I do have the CD-Rom set to boot.

---

### Post by bulldog on 2007-03-27
Boot ubuntu in recovery mode and log in console.
```
sudo dpkg -reconfigure -phigh xserver-xorg
```choose the right settings if necessary and reboot.
In most cases ubuntu will boot properly.

To reinstall windows or any OS,you must boot from cd-rom.
In your case you boot from hard disk,so find the right setting in your BIOS and make sure you're having a boot able cd in the player.

---

