---
title: "Need to reinstall windows"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by nanbudh on 2006-12-30
Hi,
I have installed ubuntu along with windows on my sata hard disk. A while ago windows got corrupted<some internet download was responsible i think> and neither the browser works nor any kinda sound is played. Anyway i want to reinstall windows but i donot want to reinstall ubuntu which is working perfectly and i have no complaints.If i simply load win XP CD would it not overwrite Grub loader?Then would i need to reinstall Grub again? how do i go about it? Please help me with clear cut instructions.I am a hobbyist and not a pro.Thanks in advance

---

### Post by riven0 on 2006-12-30
It could be tricky. You can use gparted to set aside an ntfs partition for windows, and then install XP there... But I do believe Windows will overwrite GRUB with it's own bootloader. Can't remember now; it's been so long since I've used Windows.

[Look here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), either way, just in case something goes wrong.

---

### Post by Stemp on 2006-12-30
Well just run a live-cd and install/update grub

---

### Post by nacho32 on 2006-12-31
make sure the pc boot off the cd first in bios
1 cd/dvd
2 hd
you should have no trouble

---

