---
title: "Can't install Ubuntu Lucid netbook"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by drmiho on 2010-06-21
Hi guys, 
I tried to install Ubuntu netbook remix Lucid on a Lenovo IdeaPad netbook with an Intel Atom processor and a SSD HD 4 GB and a SATA HDD of 160 GB. The installation starts normally, but stops on step 3 of 7, where I choose my keyboard layer...it never passes on to step 4 of 7. I must mention that I had a corrupted installation of Windows XP running on it...I made an USB bootable disk, and everything goes fine untill step 3 of 7. Does anybody have any idea?
Thanks

---

### Post by ajgreeny on 2010-06-21
Is the iso file you used good?  Did it boot properly to the gnome or UNR desktop?  You should check the file against the listed md5sum figure shown in [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

If the .iso is OK you should write it again to the usb drive and try again.
How did you write to the usb drive; with unetbootin?

---

### Post by drmiho on 2010-06-21
I used the startup disk creator in Sytem/Administration. The iso must be ok since I tried it on my laptop and it works.

---

### Post by hobocaver on 2010-06-22
Hi    I also installed UNR, but on an Asus 1201 with AMD processor, would not boot. In these forums I found a suggestion that Unetbootin was not loading the MBR properly. I can only give a vague format for the command I used.  dd if/     of /dev/sdb        The if line moves a MBR to the USB, /dev/sdb on my machine. UNR then booted perfectly and works fantasticly.

---

