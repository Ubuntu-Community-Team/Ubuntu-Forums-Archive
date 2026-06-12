---
title: "How to Install ubuntu in an old laptop"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by disablek on 2008-05-20
Ok here's the problem. I've got an old laptop that can only boot from it's windows partition. No working CDROM, no bootable floppy, or even from usb. The other cruncher is that there's only one partition on the harddrive.

Is there anyway that i can install ubuntu on this?

---

### Post by iaculallad on 2008-05-20
If there is a built-in network adapter and you could direct you BIOS to boot from it then you could try [netboot]("https://help.ubuntu.com/community/Installation/Netboot").

---

### Post by Slim Odds on 2008-05-20
> **iaculallad said:**
> If there is a built-in network adapter and you could direct you BIOS to boot from it then you could try [netboot]("https://help.ubuntu.com/community/Installation/Netboot").

If the laptop is that old (although he didn't really say), it probably doesn't have the "boot from network" option.

Some specs would  be nice OP

---

### Post by overdrank on 2008-05-20
> **disablek said:**
> Ok here's the problem. I've got an old laptop that can only boot from it's windows partition. No working CDROM, no bootable floppy, or even from usb. The other cruncher is that there's only one partition on the harddrive.

Is there anyway that i can install ubuntu on this?

Hi and welcome, you could have a look at Wubi
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by kerry_s on 2008-05-20
> **disablek said:**
> Ok here's the problem. I've got an old laptop that can only boot from it's windows partition. No working CDROM, no bootable floppy, or even from usb. The other cruncher is that there's only one partition on the harddrive.

Is there anyway that i can install ubuntu on this?

the specs are important, linux is not just going to run on anything, there are requirements.

---

### Post by iaculallad on 2008-05-20
An out-of-the-blue solution would be to pullout the laptop HDD, install in on a laptop with CD/DVDROM. Intall you're Ubuntu LiveCD using that laptop. When done, pull it out again and re-place it on your old laptop. Usually, after booting it with the old laptop, an xorg error would display. Press Ctrl+Alt+F2, then enter your username and password. Issue the command **sudo dpkg-reconfigure xserver-xorg**. Try answering all the questions that are being displayed on the screen. Save the changes then restart your laptop using the command **sudo shutdown -R now**.

---

### Post by disablek on 2008-05-20
Sorry for the lack of info, but it's an old dell.

128M ram, some integrated video. The usual method of installing using the graphical interface is a nogo. The alternate install requires a bootable device. Same with the server version.

Netbooting yeah is out as well.

Wubi is interesting, but i want to replace windows on this. Can i install ubu with this, have wubi install a bootloader and hose the entire partition?

I like the HDD replace and install technique, but the only other laptop i've got is sata :(

---

