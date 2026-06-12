---
title: "Dual Boot 15.10 and Win 10 Bootloader"
date: 2016-01-25
forum: Installation &amp; Upgrades
---

### Post by nd456 on 2016-01-25
Hello,
I have a think pad T420 and upgraded windows 7 to windows 10 so windows is in Legacy mode. I just tried to install Ubuntu 15.10 alongside of windows and had no problem with the installer off of a live USB. The computer is in legacy boot mode only but when the installation finished and restarted the computer boots right into windows as if there is no boot loader. I tried changing the boot mode into UEFI and Both (UEFI/Legacy) and I am unable to boot into Ubuntu. The hard drive was resized during installation and I am clueless how to fix this.
Thank you in advance. -Andy

---

### Post by Nuno_Abreu on 2016-01-25
OK, do you still have the live USB there? If yes, great!

Now, boot from it. Mount the partition where Ubuntu is on and remember the path. After that, go to the Terminal and type this:
```
sudo grub-install --root-directory=/path/to/ubuntu /dev/sdX
```

Now, after this, type this command:
```
sudo chroot /path/to/ubuntu && sudo update-grub 
```

It should be done after you reboot.
Tell me if it worked!

---

### Post by nd456 on 2016-01-25
What partition is it?
[ATTACH=CONFIG]266940[/ATTACH]

---

### Post by Nuno_Abreu on 2016-01-25
It is the one highlighted on the screenshot you posted (partition 5 formatted in ext4), I assume. Mount that partition (which seems mounted already) and check the path where it was mounted. Then, do the steps I mentioned in the previous post.

---

### Post by nd456 on 2016-01-25
Thank you for the reply. I had trouble executing the command to reinstall grub. I ended up fixing it with the Boot-Repair tool.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Nuno_Abreu on 2016-01-26
That works too. Probably you did not specify the path correctly - the path is not the device identifier (ex. /dev/sdXY), but the directory itself - that could be the problem.
But I'm glad it's sorted out.

---

