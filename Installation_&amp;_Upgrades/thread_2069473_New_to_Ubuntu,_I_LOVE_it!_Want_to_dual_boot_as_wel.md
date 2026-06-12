---
title: "New to Ubuntu, I LOVE it! Want to dual boot as well and install windows 7."
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by c4nati on 2012-10-10
Hello all! I absolutely love Ubuntu and can't wait to further my knowledge and learn as much as I can about Linux! I'm actually getting into computers as a whole and I just built my first pc two days ago and I had Ubuntu .iso on cd I burned last week and installed it.  The reason I'm asking for help (Because there's plenty of tutorials on how to dual boot and I've watched many so I don't waste time asking questions with answers) is because every tutorial I read or watched has you dual booting on windows first and installing Ubuntu, but Ubuntu is the only current OS on my computer.  I know I have to "partition" in order to do so but I have no idea how to do that as well, if someone would be as kind as to help guide me through this process I will be extremely grateful and I am trying to learn as much as possible! Thanks!

---

### Post by oldfred on 2012-10-10
Welcome to the forums.

If a very new computer, did you install Ubuntu in BIOS/MBR or UEFI/gpt mode? If not sure post this:

sudo parted /dev/sda unit s print

If MBR Windows has to have a primary NTFS partition with the boot flag. So depending on what partitions you used, you can just create a new primary and install to that partition. Windows will overwrite the MBR, so have liveCD/USB handy to reinstall grub2 and run sudo update-grub to add Windows to your boot menu.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

