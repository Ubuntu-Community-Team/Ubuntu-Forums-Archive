---
title: "busybox dropping to a shell"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by newbie234 on 2011-12-22
I have  PowerBook G4 and I recently upgraded from 10.04 to 12.04

It installed and upgraded everything and when prompted I restart the computer. Now all I see when I boot the computer is:
```
WARNING bootdevice may be renamed. Try root=/dev/sda4
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/hda4 does not exist. Dropping to a shell!

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```

I tried typing "exit" after the (initramfs) and it didn't work

I booted in with the 10.04 live CD - I don't have any menu.1st or grub.conf files, any of the sort.

Anyone help? :(

---

### Post by JackPM on 2011-12-22
I am right where you are!

See below and try the commands.
I can get mine to Ubuntu...but it doesn't boot to Ubuntu.

Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/EXIFM-root does not exist.  Dropping to shell!

BusysBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of commands.

[COLOR="Blue"](initramfs) modprobe dm-mod
(initramfs) lvm
lvm> vgchange -a y
lvm> exit
(initramfs) exit[/COLOR]

Ubuntu 10.04 LTS EXIFM tty1

EXIFM login:

---

### Post by rsavage on 2011-12-23
newbie234 your hard drives have been renamed in 11.10 and 12.04.  What was hda is now sda.  So if you have any references to hda in your yaboot.conf you need to change them to sda.
 
At the second yaboot prompt type 
 
Linux root=/dev/sda4
 
It should then boot normally.  You will need to adjust your yaboot.conf to make this permanent so you don't have to keep typing it.
 
gksudo gedit /etc/yaboot.conf
sudo ybin -v
 
If you still end up in a busybox prompt then type
 
modprobe pata_macio
exit
 
I wrote a guide [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .

---

### Post by jack_spratt on 2012-08-12
> **JackPM said:**
> I am right where you are!

Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/EXIFM-root does not exist.  Dropping to shell!

BusysBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of commands.

[COLOR="Blue"](initramfs) modprobe dm-mod
(initramfs) lvm
lvm> vgchange -a y
lvm> exit
(initramfs) exit[/COLOR]

Ubuntu 10.04 LTS EXIFM tty1

EXIFM login:

I have the same problem with 12.04, after having installed Ubuntu (Dream Studio) into a LVM volume, after installing lvm2 on the liveCD. The error that I get is 

```
ALERT! /dev/mapper/vg-home--desktop-distro2 does not exist. Dropping to shell!
```

The commands suggested above look like they should work for me, but unfortunately 'lvm' and 'vgchange' are commands that aren't recognised. I tried using the LiveCD to chroot in and install lvm2, but during the installation errors occurred. I couldn't set up the chroot according to help.ubuntu.com as I couldn't install the recommended packages before attempting to chroot.

Does anyone know how I can install lvm2 in such a way that /dev/mapper/vg-home--desktop-distro2 will be mounted and accessible during boot? Thanks!

---

### Post by JackPM on 2012-08-12
Can you paste the whole message?
Can you type 'exit'?

Thanks,
Jack

---

### Post by jack_spratt on 2012-08-20
Thanks for your assistance!

> **JackPM said:**
> Can you paste the whole message?

I typed it as I can't think of a way to paste. Hopefully typos are few ;)

```
- Give up waiting for root device. Common problems:
  - Check rootdelays (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Mussing modules (cat /proc/modules/; ls /dev)
ALERT! /dev/mapper/vg_home--desktop-distro2 does not xist. Dropping to a shell!

BusyBox v1.10.5 ........
```


> Can you type 'exit'?

This produces exactly the same message as the one above - the error message is simply repeated.

I tried following the instructions here: [http://ubuntuforums.org/showthread.php?t=1943820#7](http://ubuntuforums.org/showthread.php?t=1943820#7) but I can't get Internet access (/etc/init.d/network doesn't exist, neither does ifconfig or ifup), so the wget commands don't work.

- Jack.

---

### Post by JackPM on 2012-08-21
What message do you get when you type help?

If a list comes up then try:

/bin/busybox ls
/bin/busybox lvm


Then try previous commands.

If /bin/busybox ls works then check your yaboot.conf

---

