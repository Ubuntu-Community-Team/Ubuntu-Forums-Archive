---
title: "Grub installed correctly but still doesn't work"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by privateRob on 2012-10-20
Hi everybody!

I've installed the new released Ubuntu 12.10 64bit without any problems. Now, if I try to boot my OS from the SSD, it immediately restarts after the bios screen.

If the booting order is something like:
1. HDD (Ubuntu 12.10)
2. USB HDD (Live USB stick)

Then it will boot "Live-Ubuntu" from the live usb stick.


I managed to install grub onto the usb-stick and then everything works as expected (grub starts and I can boot my OS from the SSD), but only with the usb stick inserted at the start-up. Meanwhile I have destroyed grub on the usb-stick and I can't get it to work again, because I have no idea, how I did it in the first place.

So, that's the current state.

###

I have tried and googled a lot of things. Too many to mention them all here.
I won't write them down, because perhaps I missed a small but very important step to get grub working.

```
sudo grub-install --boot-directory=$USB_DIR/boot /dev/sda
```

Doesn't report any problems but it still doesn't work on a reboot.

boot-repair doesn't report any erros either, but produces a very good output:
SSD Ubuntu: [http://paste.ubuntu.com/1291722/](http://paste.ubuntu.com/1291722/)
USB Live Ubuntu: [http://paste.ubuntu.com/1292394/](http://paste.ubuntu.com/1292394/)

thx!

---

### Post by darkod on 2012-10-20
You need to recreate the ubuntu usb again and boot with it in live mode. You should be able to fix this from live mode.

Or alternatively make a bootable cd with boot-repair and use it to repair your boot process. You can also run boot-repair from ubuntu live mode.
Instructions here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by privateRob on 2012-10-20
> **darkod said:**
> You need to recreate the ubuntu usb again and boot with it in live mode. You should be able to fix this from live mode.

Or alternatively make a bootable cd with boot-repair and use it to repair your boot process. You can also run boot-repair from ubuntu live mode.
Instructions here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

First, thank you for your fast response! :)

I have no CD/DVD drive therefore I'm only using an Ubtuntu live usb (which I have recreated many many times).

I also ran boot-repair many many times. No problems are reported but it still doesn't work.


If I run:
```
sudo grub-install sda
```

then I get the Error:
Path '/boot/grub' is not readable by GRUB on boot. Installlation is impossible. Aborting.

But I think, ubuntu tries to install it on the USB stick for some weird reason, even if the USB stick is on /dev/sdb :confused:

If I run:
```
sudo grub-install --boot-directory=$USB_DIR/boot /dev/sda
```

No problems are reported but it still doesn't work.

---

### Post by darkod on 2012-10-20
First, it's grub-install, not grup-install. Those commands can't be run like that from live mode, it depends whether you are running them from with-in your ubuntu installation, or from a live session. For live session it works differently.

But nevermind that. I hoped boot-repair can help you to avoid running more commands. Grub2 isn't installed fully, the core.img is not on sda5, which might be why boot-repair is failing. Boot again into live session and start executing these commands in terminal:
To prepare for chroot:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Remove grub2 completely, reinstall it and recreate config files, then install it on the MBR of /dev/sda:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Reboot without the usb stick and see if it worked.

---

### Post by privateRob on 2012-10-20
yes, Yes, YES!

Thank you very much! You solved it! :smile:

---

### Post by darkod on 2012-10-20
No problem. Enjoy it.

---

### Post by YannBuntu on 2012-10-23
Hello

**@darkod:** good job :) FYI an equivalent but shorter procedure is: Boot-Repair --> Advanced options --> GRUB options --> tick "Purge and reinstall GRUB" --> apply.

---

