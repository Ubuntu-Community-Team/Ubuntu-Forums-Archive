---
title: "Failed update to 11.10"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by paperchaser on 2011-09-26
I am a noob when it comes to Ubuntu, however; lured into a sense of my own power I decide I could use a beta version just like any one else.

Disaster occurred in the form power cut while the update was urrr updating.

I get the option to boot the following: None will boot correctly into a desktop
 
Linux 3.0.0-11-generic
Linux 3.0.0-11-recovery
Linux 2.6.38-11-generic
Linux 2.6.38-11-recovery

If I use the e function I can get in to a shell on the 2.6.38-11.
( I deleted the quite splash and set vt.handoff=7 to 6 - F10 to boot

Ubuntu oneiric (development branch) clive-desktop tty6

I don't know what it does but I can then enter may name and log in.

If I do a DIR - my files and directories show up on the directory desktop.

I have tried get the update files and installing them but to no avail. It does not change the boot up.

I have also download and installed the desktop again and that won't work either.

Can anyone suggest how I can either save my data (I know backups ...) or how I can boot up into graphics so I can salvage my data.

Thanks

---

### Post by MAFoElffen on 2011-09-26
> **paperchaser said:**
> I am a noob when it comes to Ubuntu, however; lured into a sense of my own power I decide I could use a beta version just like any one else.

Disaster occurred in the form power cut while the update was urrr updating.

If I use the e function I can get in to a shell on the 2.6.38-11.
( I deleted the quite splash and set vt.handoff=7 to 6 - F10 to boot

Ubuntu oneiric (development branch) clive-desktop tty6

I don't know what it does but I can then enter may name and log in.

I have tried get the update files and installing them but to no avail. It does not change the boot up.

Can anyone suggest how I can either save my data (I know backups ...) or how I can boot up into graphics so I can salvage my data.

I see that you "can" get to a TTY text console or terminal(?)

Have you tried:
```

sudo apt-get update
sudo apt-get check

```Will refresh the updates list and check for broken dependencies...
```

sudo apt-get -f
sudo apt-get dist-upgrade

```Will try to fix broken packages... with the second command will
> 
 ...in addition to performing the function of upgrade, also intelligently  handles changing dependencies with new versions of packages; **apt-get** has a "smart" conflict resolution system, and it will  attempt to upgrade the most important packages at the expense of less  important ones if necessary.
Let me know how it goes.

---

### Post by paperchaser on 2011-09-26
MAFoElffen, thanks for the suggestion.

However no improvement.

---

### Post by MAFoElffen on 2011-09-26
> **paperchaser said:**
> MAFoElffen, thanks for the suggestion.

However no improvement.
11.10 is beta.... Meaning they're working things out still in pieces.  On some of my test boxes I still have problems starting with lightdm as the desktop manager... and
```

sudo apt-get install gdm

```was able to correct things via installing GDM as the desktop manager...  Not sure that came up on an update(?) but worth a try.

If it doesn't help, you can go back to lightdm via
```

sudo dpkg-reconfigure lightdm

```

---

### Post by paperchaser on 2011-09-27
gdm is the up to date version

if I try lightdm I get the following errors


enviroment variable DPKG_MAINSCRIPT_NAME missing 
enviroment variable DPKG_MAINSCRIPT_PACKAGE missing

If I try and re-install DPKG it just returns saying already newest version

---

### Post by garvinrick4 on 2011-09-27
Put in a live cd (install cd using Try Ubuntu) and open a terminal and find your install by sda#
```
sudo fdisk -l
```Upper case L

Now I am going to use sda5 for this[COLOR=Red] you use your own.[/COLOR]
Open a terminal and [COLOR=Red]copy and paste these using your own sda#[/COLOR]
[COLOR=Red]Now get internet working on the Live cd[/COLOR] or will not update and upgrade will just say error for that command.
```
sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
dpkg --configure -a
``````
apt-get update; apt-get upgrade
``````
dpkg --configure -a
``````
grub-install /dev/sda
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot.
```Hope it worked out  the kinks, it is acording to how far along the upgrade was when power went out.
This above does abit of all including installing grub incase that is fouled.
## Going to go offline now will check this in the morning let me know how you did.

---

### Post by paperchaser on 2011-09-27
when I type in 

sudo mount /dev/sda2 /mnt

it returns

you must specify the file system type.

Do I need to add some thing else

---

### Post by garvinrick4 on 2011-09-27
Make sure it is where your file system is sda2, if it was and upgrade and not a clean install failing there
should still be a file system to mount in the partition. Post the results of.
```
sudo fdisk -l
```Lower case L

---

