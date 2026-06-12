---
title: "Ubuntu couldn't install Grub"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by xx55tt on 2011-06-22
I installed Win7. I wanted to install Ubuntu to another drive. I chose the third option to do things manually, as I couldn't change the hard drive in the first option. (keeping Windows and installing Ubuntu) So I made a root and a swap partiton for Ubuntu. The installer asked me to set the location of the bootloader, I chose the one with "Windows loader" in it. The installer accepted it and proceeded to the installation. Before it finished, it threw an error saying that it couldn't install Grub to the place I've set. The dialog allowed me to choose another drives, but it still failed. So I choose not to install Grub, but the dialog stayed there and did nothing. (bug probably) I had to restart the PC.

So I'm here with a working Windows, and Ubuntu without Grub. Thanks for your help in advance.

---

### Post by YesWeCan on 2011-06-22
When you have Ubuntu on a separate disk, you should install Grub to the MBR of that disk so that your Windows disk is untouched. Often I recommend disconnecting the Windows disk during install to avoid any confusion with the installer.

No problem. You need to boot from your live CD/USB and install Grub. After booing,
1) Run Disk Utility in System/Admin and see what the drive name is of your Ubuntu disk. It is probably /dev/sdb and your Windows disk is /dev/sda. Also confirm the number of your Ubuntu root partition, probably sdb1.

2) Install Grub to your Ubuntu disk. In a terminal (assuming your disk is /dev/sdb and root partition is sdb1):
[COLOR="Blue"]sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb[/COLOR]

If there are no other errors you should be able to boot your Ubuntu disk by telling the bios to boot it first. Once booted, you need to run a command to update Grub's boot menu:
[COLOR="Blue"]sudo update-grub[/COLOR]

Try that.

---

### Post by YesWeCan on 2011-06-22
I'm not sure from your description whether the installation completed or not. The grub install will fail if not and you'll have to do the Ubuntu install from scratch.

If you do, check in the installer that the bootloader is put on /dev/sdb (or whatever your Ubuntu disk is named) and not on a partition which are named /dev/sdbn, like /dev/sdb1.

---

### Post by xx55tt on 2011-06-22
So I've booted from liveCD, I could mount /dev/sdb1, but grub-install didn't work.
```
rm: cannot remove `/mnt/boot/grub/915resolution.mod': Permission denied

```

I guess I'll reinstall Ubuntu, just to be sure. But first I just need to clarify that I need to keep the Win bootloader on its disk, and install Grub on the Ubuntu disk. And Grub will add Win to the bootlist.

---

### Post by YesWeCan on 2011-06-22
Did you precede it with 'sudo'?

---

### Post by xx55tt on 2011-06-22
Yes I used sudo.

But the main problem was my lack of knowledge. I wanted to install the bootloader to the Win disk, now I installed it to Ubuntu's disk and it's working fine. Thanks for your help. :)

---

### Post by YesWeCan on 2011-06-22
You are welcome.
Don't forget to mark this thread as "solved" in the [COLOR="Red"]Thread Tools[/COLOR] menu.

---

### Post by BLTicklemonster on 2011-06-22
Off Topic:
I just today learned that GRUB stands for GRand Unified Bootloader.

---

