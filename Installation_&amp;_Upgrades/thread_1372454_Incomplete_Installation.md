---
title: "Incomplete Installation"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by udratherbme on 2010-01-04
OK... I have a Toshiba L35-S2151, 1G Ram, ATI Radeon Exp Card.... I tried to install 9.10 w/ no success, I was able to use the Demo several times w/ no problems.  Once I decided to do an install, I had to do the help with boot CD option from the menu and I was able to do the complete install, once I completed the installation, rebooted and It gets hung up on the Grub Menu... what am I missing

---

### Post by kansasnoob on 2010-01-04
> **udratherbme said:**
> OK... I have a Toshiba L35-S2151, 1G Ram, ATI Radeon Exp Card.... I tried to install 9.10 w/ no success, I was able to use the Demo several times w/ no problems.  Once I decided to do an install, I had to do the help with boot CD option from the menu and I was able to do the complete install, once I completed the installation, rebooted and It gets hung up on the Grub Menu... what am I missing

Well, if this is an Xorg problem I'm fairly stumped, but I have run into some problems with grub2 not playing well with a few Toshiba laptops. Did you install via Live Cd or Live USB?

Regardless we have nothing to lose by taking a look at the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I'm thinking since the live CD (or USB) ran maybe we can revert to legacy grub just to see if you can boot.

---

### Post by udratherbme on 2010-01-04
I used live cd

EDIT: Removed Result.TXT  added Results.doc

---

### Post by kansasnoob on 2010-01-05
Sorry for the belated response, my power went out :(

I'm just now going to look this over.

---

### Post by kansasnoob on 2010-01-05
Well I see nothing actually wrong there. As I said if this is related to X I'm fairly stumped, but since you hang at the grub menu I think it's definitely worth trying to revert to legacy grub, it's also fully reversible.

Just so I don't have to do a lot of explaining look here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And especially regarding my mount & chroot procedure here (take note of the **if one part of the string fails it stops the whole process so if you encounter any failure message look at the list of individual commands below!**):

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Anyway since your root partition is on sda1, from a Live CD:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now we want to update the package list:

```
apt-get update
```

Note: if that fails for any reason we may run into trouble going forward!

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub-pc grub-common
```

```
apt-get install grub
```

```
update-grub
```

```
grub-install /dev/sda
```

Now we need to work in a grub shell:

```
grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

```
quit
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then just reboot and hopefully you'll be able to boot!

Regarding X, in both Karmic and Lucid I've had to use the Xorg crack repo but I have a totally different graphics card:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Take special note of this quote from their main page:

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

> Packages for those who think development versions, experimental and unstable are for old ladies. We want our crack straight from upstream git! Well, straight, we want it built and packaged so we don't need to know what we're doing, except that we will break our X and put our computers on fire.

Their PPA can be installed in a chroot if you still can't boot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Note: Nano can be a confusing text editor to use if you haven't used it before! I explained a bit about that here (it's about 2/3 of the way down on that post):

[http://ubuntuforums.org/showpost.php?p=8606412&postcount=35](http://ubuntuforums.org/showpost.php?p=8606412&postcount=35)

```
nano /etc/apt/sources.list
```

Then using the arrow keys navigate to the bottom of that file and add these two repos:

> deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 

Then exit nano as explained in that other post and still in the chroot environment:

```
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
```

Then just:

```
apt-get update
```

```
apt-get upgrade
```

Of course then exit the chroot and unmount.

---

