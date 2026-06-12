---
title: "Installing Windows on Linux. Anything to watch out for?"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by TheTwitchy on 2008-01-16
I have Linux on my main machine, an I'm loving it. However, I only ever put Linux on it, and not Windows. However, I realize now that I need Windows on it to run a couple of applications.

I've heard that given the choice, you should install Windows first, and Linux second, so I'm wondering if I do it the other way around, if there's anything wrong with this or if I need to know anything specific.

---

### Post by Craigus on 2008-01-16
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Search in the page linked for the supergrub method - definitely the easiest solution.

---

### Post by LunatikOwl on 2008-01-16
I used this method to restore the grub boot menu a few times after installing windose:

1. Boot from Ubuntu live cd
2. Fire up a teminal and type
```
sudo -i
```
to go to root mode.
now type
```
fdisk -l
```
and find the root partition of your ubuntu installation, say /dev/sda1 in this example.
now type:
```

mkdir /mnt/root
mount /dev/sda1 /mnt/root
chroot /mnt/root /bin/bash
grub-install /dev/sda1

```
now you just restored the grub menu.
after you boot you should see it. if you can't see the windose option choose ubuntu and edit the file:
/boot/grub/menu.lst

and uncomment the windose chain-loader section.
note only that you might need to change the partition in that section to the partition youv'e installed windose to.
/sda1 or /hda1 changes to (hd0,0)
/hdb4 changes to (hd1,3) and so on.
hope this helped...

---

### Post by RockHaxor on 2008-01-16
If you run a dual-boot system with Linux and Windows, I am sure this has happened to you. You had to do your quarterly reinstall of Windows, and now you don’t see the Grub bootloader anymore, so you can’t boot into Ubuntu, this may happen if you install Windows after Ubuntu.

Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

```
sudo grub
root (hd0,0)
setup (hd0)
exit
```

Reboot (removing the livecd), and your boot menu should be back.

If you have grub after the install but Windows is not an option try this:

Open the terminal: **applications/accessories/terminal**
insert this code
```
sudo gedit /boot/grub/menu.lst
```
Copy this code and insert it at the bottom of this open document (In the title portion you can call windows whatever you like):)

```
title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1
```

Look at the top of this open document where it annotates that the grub loader is hidden by default. If you want the selection to be visible instead of having to hit (esc) when booting place a (#) sign in front of this line.

Save this document and reboot your system

Note: You should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3)

---

