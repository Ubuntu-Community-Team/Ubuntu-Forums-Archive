---
title: "RAMDISK: EOF while reading compressed data ...Kernel panic - Unable to mount root"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by Skyxn3t on 2010-07-31
I was following this tutorial on How install the rpmfusion nvidia drivers in Fedora 13: 
[http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752) 

Here's the tutorial:
> **leigh123linux said:**
> **[SIZE=4]F13 Howto for the rpmfusion nvidia drivers[/SIZE] **
[SIZE=4][B][COLOR=Red]

This is a Three-Step Process.  If  you  don't follow all three steps, your install will fail![/COLOR][/B][/SIZE]



**1.  Install the nvidia driver.**  ( if you have 4Gb of RAM or more   you will probably have a PAE kernel [32bit only] so follow the PAE part  )

**_[SIZE=3]For GeForce 6, 7, 8, 9, 200 & 300 series  cards [/SIZE]_**

```
su
rpm -Uvh   http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm     http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm
yum install kmod-nvidia  xorg-x11-drv-nvidia-libs.i686

```If you use a PAE kernel 

```

su
rpm -Uvh   http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm     http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm
yum install  kmod-nvidia-PAE

```Or (akmod builds the required kmod on bootup ) 

```
su
rpm -Uvh   http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm     http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm
yum install akmod-nvidia  xorg-x11-drv-nvidia-libs.i686

```[B][U][SIZE=3]

[/SIZE][/U][/B][SIZE=2][COLOR=Black]**2. Edit grub.conf (  if you omit this  step the driver will fail to work )  **[/COLOR][/SIZE]   


  this command adds **rdblacklist=nouveau** option to   /boot/grub/grub.conf 

```

su -
sed -i '/root=/s|$| rdblacklist=nouveau|' /boot/grub/grub.conf
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname   -r)-nouveau.img
dracut /boot/initramfs-$(uname -r).img $(uname -r)
```**3. Reboot**

And this is what I did:

First I executed the following commands:

```
su
rpm -Uvh   http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm     http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm
yum install kmod-nvidia  xorg-x11-drv-nvidia-libs.i686

```

Then In step 2 I executed the following commands:

First:
```
sed -i '/root=/s|$| rdblacklist=nouveau|' /boot/grub/grub.conf
```

Then this one:
```
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname   -r)-nouveau.img
```

And when I got to this one:
```
dracut /boot/initramfs-$(uname -r).img $(uname -r)
```

I got this message: [COLOR="Red"]Will not override existing initramfs (/boot/initramfs-2.6.33.3-85.fc13.x86_64.img) without --force [/COLOR]
So I kinda ignored that command and restarted my computer and that's when I received this message:  

> **RAMDISK: EOF while reading compressed data uncompression error Kernel panic - not syncing Unable to mount root fs on unknown block (0,0)**[COLOR="Silver"]

============= I used a FedoraDVD/Rescue Option to access my system:

Here's my grub.conf file (boot/grub/grub.conf):

> 

**#**boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.33.6-147.fc13.x86_64 ro root=/dev/mapper/vg_wmxwrkst-lv_root rd_LVM_LV=vg_wmxwrkst/lv_root rd_LVM_LV=vg_wmxwrkst/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrgeb-sun16 KEYTABLE=us rhgb quiet  nouveau.modest=0 rdblacklist=nouveau
initrd /initramfs-2.6.33.6-147.fc13.x86_64.img
title Fedora (2.6.33.3-85.fc13.x86_64 ro root=/dev/mapper/vg_wmxwrkst-lv_root rd_LVM_LV=vg_wmxwrkst/lv_root rd_LVM_LV=vg_wmxwrkst/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrgeb-sun16 KEYTABLE=us rhgb quiet  rdblacklist=nouveau
initrd /initramfs-2.6.33.3-85.fc13.x86_64.img



When I execute the command: **uname -a** I get the following: 
**Linux localhost.localdomain 2.6.33.3-85.fc13.x86_64 ...**

---

