---
title: "Ubuntu 12.04.2 64Bit install issue"
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by circleinsideabox on 2013-04-15
I currently have a Samsung 14" QX411-W02UB. It was running Ubuntu 12.04 64bit flawlessly until I installed the Intel Graphics Installer and it ended it making my touch-pad no longer work. I decided to just do a fresh install to resolve my issue. The installation kept failing (ubuntu would produce a blank screen after rebooting.) So I checked the media for defects and this is what message came up.

Integrity test failed:
The ./pool.main/l/linux-signed-its-quantal/kernel-signed-image-3.5.0.-23-generic-di_3.5.0-23.3.5~precise1_amd64.udeb file failed the MD5 checksum verification.

This is my file:[FONT=Segoe UI][COLOR=#000000]ubuntu-12.04.2-desktop-amd64.iso[/COLOR][/FONT]
[FONT=Segoe UI][COLOR=#000000]I used both unetbootin and the Linux universal installer to transfer the file to the USB drive.

I've attached a picture of the message.

I've checked and I can install the 32bit version of Ubuntu without an issue.
I've also tried the alternate 64bit version as well.[/COLOR][/FONT]

---

### Post by ajgreeny on 2013-04-15
That error means that the .iso file you used to make the USB install medium, or the transfer of that to the USB has resulted in a bad USB.

Check the .iso file md5sum against the list at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") and if necessary download again, by torrent if you can, as that will always give you a good downloaded file, then transfer the .iso to USB again.  personally, I don't think it matters which of the two apps you have used is your choice, as they both do a fine job.

---

### Post by circleinsideabox on 2013-04-15
thanks for the suggestion. I went back and downloaded/installed **12.04.1 **64bit and I had no issues with installation. There is definitely something wrong with those .iso files.

---

### Post by circleinsideabox on 2013-04-15
to the MODS
this thread can be marked as SOLVED, thanks.

---

### Post by omidkosari on 2013-04-25
please open following url and report that the bug also affects you [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1161771](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1161771)

---

