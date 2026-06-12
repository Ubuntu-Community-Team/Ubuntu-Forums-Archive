---
title: "Difference between WUBI and normal install"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by hakelm on 2011-09-19
I had difficulties getting my Asus Eee PC 1215P to boot from the USB-stick so I made a WUBI-install of Ubuntu 11.04 under Windows 7.
Now my question is:
Is there any difference between a "normal install" and a "WUBI-install" other than that the two operating systems share the same file space?
Are there any disadvantages with the WUBI-install?
Thanks in advance for any advice
Håkan

---

### Post by ottosykora on 2011-09-19
well, in fact it should do the same job first.

But when it comes to major updates (distro upgrades) it often ends up in non booting situation.
Also sooner or later you might want need more space then allocated at the wubi install and then things can also get complicated.

As all is basically stored in one or two big files, the installation can be kind of fragile as damage to one such file makes the install complete damaged, while on a real partition installation one damaged file might not  be a big problem yet.

The wubi was meant for initial test, just to see how does it look like etc, but for long time use it is not very suitable I think.

My wubi installs seldom survived distribution upgrade.

---

### Post by hakelm on 2011-09-19
Thanks a lot.
This means that I should make a normal install but that doesn't work for me since I get a "(initramfs) Unable to find a medium containing a live file system" when trying to install, so I am really stuck.
Håkan

---

### Post by Frogs Hair on 2011-09-19
Disadvantages :

No hibernation
30 Gb partition limitation .
Dependent on Windows (Dead Windows = Dead Ubuntu)

It is possible to increase space or move a Wubi installation to a partition , but I would consider these as last resorts unless you have no other installation options . 

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

[http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Elfy on 2011-09-19
> This means that I should make a normal install but that doesn't work for me since I get a "(initramfs) Unable to find a medium containing a live file system" when trying to install, so I am really stuck.Check the download you created the boot disk from.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by varunendra on 2011-09-19
> **forestpiskie said:**
> Check the download you created the boot disk from.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Do this first ^.

Then, assuming (from the error message) that it is a live usb drive you are trying to install from, after verifying the integrity of the downloaded iso, try recreating the live usb using unetbootin this time.

Also, if possible, consider creating a live cd instead of a live usb if it is creating problems.

---

