---
title: "xubuntu, unetbootin, and 4gb USB"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by phillyj on 2013-04-26
I wanted to make my pc load xubuntu from only a flash drive. I used unetbootin and had it make me a xubuntu 12.04 boot drive on a 4gb drive. I booted up my PC and got to the first options page where it says "Install", "Try without install", etc. I tried to install but I can't move forward because it says I need a minimum of 4.3 gb( I think it's 4.3 but can't remember now). 

I used the 12.04 Desktop 32bit version for unetbootin. I wasn't too sure about the "Alternate" version. Could this be why I can't use a 4gb stick?

I might have to use another light-weight linux, if I need more than 4gb.

Thanks

---

### Post by phillyj on 2013-04-26
> **phillyj said:**
> I wanted to make my pc load xubuntu from only a flash drive. I used unetbootin and had it make me a xubuntu 12.04 boot drive on a 4gb drive. I booted up my PC and got to the first options page where it says "Install", "Try without install", etc. I tried to install but I can't move forward because it says I need a minimum of 4.3 gb( I think it's 4.3 but can't remember now). 

I used the 12.04 Desktop 32bit version for unetbootin. I wasn't too sure about the "Alternate" version. Could this be why I can't use a 4gb stick?

I might have to use another light-weight linux, if I need more than 4gb.

Thanks

Well, I guess I missed the requirements at the bottom of the download page. Alternate only needs 2gb space to install.

---

### Post by sudodus on 2013-04-26
You can run a live session from your unetbootin made pendrive. If you add a casper rw file or partition on the pendrive, the live session will be persistent. This means that personal files, installed packages, settings etc will be saved at reboot or poweroff, and you will have it the next time you run xubuntu.

An alternative is to install xubuntu to another pendrive. This installation is the same kind of installation as if it were done to an internal drive. It is possible to install Lubuntu into a 4 GB pendrive, but I think Xubuntu needs more, in practical life it means an 8 GB pendrive.

A regular live drive is OK with a basic USB pendrive, but a persistent live or regular installation will be very slow unless you have a fast USB pendrive. The flash hardware is often slower than the USB2 interface, but if you get a USB3 pendrive, the flash is much faster. Of course it works at its full speed in a USB3 port, but it is also much faster than a basic USB pendrive in a USB2 port. Yesterday Sandisk Extreme was a good choice, but check speed versus cost, the market is changing rapidly.

What is it you want? Please tell us some more details, and you will get more detailed tips :-)

---

### Post by phillyj on 2013-04-26
> **sudodus said:**
> 

What is it you want? Please tell us some more details, and you will get more detailed tips :-)

I am planning a headless cryptocurrency mining rig. It's very basic, using a P4 and mATX mobo, and probably a AMD 7950. I need to finish modding the case with some more fans and test out the USB drive linux to see it will work for me. More of a learning experience for me.

I would say I'm a medium level linux user, adept with the cmd line and able to install non-native drivers.

---

### Post by sudodus on 2013-04-26
So you really don't need a system that is responding quickly to your commands. Once it is started, it will be number-crunching for long periods of time. Then you can install any *ubuntu, xubuntu is fine, into a basic 8 GB pendrive or a very old internal HDD (if you have one). You might also install Ubuntu Server without any graphic desktop environment. And as you have already noticed, the alternate installer is better with old or small systems, but xubuntu wants more space than lubuntu, so if you need to use the 4 GB pendrive, lubuntu is better. After installation Lubuntu 13.04 'Raring' occupies about 2 GB of the drive, but more is needed for temporary files during the installation.

*Edit*: You also need some space for a swap partition, maybe only 512 MB, to avoid crashes at temporary high memory usage. What cpu and how much RAM is there in the computer?

---

### Post by phillyj on 2013-04-26
Hmm, good points there. I just went with xubuntu because there is a guide to set it up for pendrive and mining. 

I only have a 4gb USB drive at the moment. Can't I just install xubuntu and remove the unnecessary programs. I only have 1Mbit DSL so downloading these distros take a while. 

I have the drive setup with Xubuntu 12.04 Alt version, so I will try it out later today. I'll have to look into that swap partition you mentioned.

System Specs:
Intel Pentium 4 515, 1Gb RAM. I took out the HDD to reduce unnecessary psu usage. The mobo has one PCIe slot so right now it's good enough for me.

---

### Post by sudodus on 2013-04-27
I think it is hard to install to the same drive as you are installing from. So if you want to install 'a regular installed system' to a USB pendrive, you should install from another pendrive or from an optical drive, CD or DVD, or even from a HDD (internal or external).

If you have a read/write optical drive, that would be straightforward: Make an install CD and install to the USB drive. Otherwise, you can clone the Xubuntu iso file to the HDD, and install from it to the pendrive. After that you can remove the HDD.

Or the other way around might work better: Install Xubuntu to the HDD as usual and remove the application program packages that you don't need. Reduce the size of the root partition, make the swap small enough, and move it so that the whole system is small enough to squeeze into the USB pendrive. Use ```
gksudo gparted
``` to edit the partitions.

Then you are ready to clone the system. But I think you need to boot from a third drive (a CD, DVD, USB or HDD), because the source and target drives should not be mounted (not used at all) when you clone the system from the HDD to the USB drive.

I would clone it with dd, nicknamed 'disk destroyer', because it does what you tell it to do without any questions, even if it is not what you want to do. So a typing error makes the difference between miracle and catastrophe. Don't use dd in a computer with a lot of personal files, unless you have a fresh backup!!! In this case, there should not be too much work invested, that can be lost. Assuming the HDD is found at /dev/sda and the USB pendrive at /dev/sdx, use this command

```
sudo dd if=/dev/sda of=/dev/sdx bs=4096
```

Running from a USB flash drive, you should use the mount option **[FONT=courier new]noatime[/FONT]** in **[FONT=courier new]/etc/fstab [/FONT]**for the root partition. It reduces the wear of the flash hardware. If you tamper with the swap partition and the UUID is changed, you need to edit its entry in **[FONT=courier new]/etc/fstab[/FONT]**. Check with

```
sudo blkid
```

---

### Post by phillyj on 2013-04-27
Are you saying that it is better to use a boot disc. Then I boot and install to the empty USB drive? Then what is the purpose of unetbootin? I thought it would install on my boot USB drive and delete unnecessary files.

---

### Post by C.S.Cameron on 2013-04-27
Once the computer is booted a Persistent install is as fast as a Full install.
With a 4GB pendrive you will end up with about 3GB of persistence space.

A persistent install takes longer to boot, is not as secure and shouldn't be updated.

The Try/Install screen can be removed by overwriting syslinux.cfg with:

```
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

---

### Post by sudodus on 2013-04-27
Unetbootin makes a boot USB drive, that will act similar to a boot CD. So you can say that Unetbootin will do what the burning program would do, but to a USB drive instead of a CD or DVD.

The purpose of the boot USB drive is to perform the installation to an internal HDD in the standard case. If you want to install to a USB drive, you need to have the system to install from somewhere else.

An alternative is a persistent live USB drive, which can be made with Unetbootin. It boots in the same way as without persistence, and in addition, there is a casper rw file (or partition), where you can save personal files, installed programs and system settings. A persistent live system is 'between a boot CD and an installed system'. It is easier to make than a full installation, and it is easier to break (so that you have to start with a blank casper rw file or a backup copy of it).

The persistent live system might be the best choice for you, if the installation procedure to the USB pendrive is too complicated. When everything you need works, make a full backup, and you need not worry if it breaks.

---

### Post by phillyj on 2013-05-04
Slow as molasses. I went and burned Xubuntu Alt to a CD and installed the OS onto the USB drive. It took a few hours to install onto the USB. Everything worked well but it is very slow. 

At least I have an understanding of the install process and how long it takes. I will install Lubuntu next. How does Lubuntu compare with the other lite *nix versions?

---

### Post by sudodus on 2013-05-05
Lubuntu is the lightest and fastest of the Ubuntu flavours. There are other linux distros, that are lighter or that fit better for old hardware.

But you must remember that the USB 2 drive is slow for read/write operations. Once the code is in the RAM, it will be much faster. But if the RAM is too small, and the system starts swapping, it will be slow again: slow if the swap partition is on an internal hard disk drive, very slow if the swap partition is on a USB disk or USB flash pendrive. USB 3 drives are faster, but if connected via a USB 2 port, it will be much slower than an internal  hard disk drive.

The important thing is if the number-crunching will be fast (done within the RAM) or not. Don't worry so much if the manual commands will be slow. You can check if swap is used or not. From another command window, use either
```
  top
```
or
```
 swapon -s
```
while the numbercrunching is running.

---

### Post by phillyj on 2013-05-15
Well, I got a chance to try to install Lubuntu on my 4gb drive (actually <4gb). Anyway, it didn't work because I need a bigger drive. If xubuntu needs at least 3.7gb drive, then LiteUbuntu should have smaller drive requirements. Oh well, I'll try mint...ohwaitaminute...it needs 4gb too. Hmm, I think I will try DSL next then. What are they stuffing into distro nowadays?

---

### Post by sudodus on 2013-05-15
A regular install of Lubuntu 13.04 via the desktop iso needs 4.3 GB, but  the final installed system is only around 2 GB (there are a lot of  temporary files). I think it should work to ***install Lubuntu with the alternate iso***  into a drive with almost 4 GB. And I think that Lubuntu 12.04 is around  the same size, so it should work too from its alternate iso.

If  that does not work, you can make a ***persistent live system of any of the  Ubuntu family flavours*** (the casper rw file can be around 3 GB which  should be more than enough). So if you want Xubuntu, it should work in a  persistent live system.

Another alternative is to run ***Ubuntu Server***, if you need no graphical desktop environment, and this is a good alternative for a headless machine.

Finally you can start with the ***Ubuntu mini iso*** and add whatever packages you need.

***DSL*** is nice and ***very***  small, but I think it is more like a toy to run on very old hardware.  If you can find the necessary packages (or source code and compilers and  compile your cryptocurrency mining rig yourself, that would be great  :-)

There are also other very small distros, for example ***Puppy Linux***.

Another distro, that might be a good alternative is a "poor man's install' of ***Knoppix***.  This corresponds to a persistent live Ubuntu family system, but Knoppix  is designed to run like this as its standard or preferred way to run.

---

