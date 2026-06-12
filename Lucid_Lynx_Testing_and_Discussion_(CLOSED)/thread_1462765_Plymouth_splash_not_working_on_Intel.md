---
title: "Plymouth splash not working on Intel"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by espenfjo on 2010-04-26
Hi,
I have a problem with plymouth and no splash showing at boot/shutdown.
My system is upgraded from 9.10 and it is updated with the newest packages.
Plymouth seems to be workings since it logs an awful amount of data when put in debug mode.
KMS is also enabled.

debug-log: [http://paste.ubuntu.com/422619/](http://paste.ubuntu.com/422619/)

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


---

### Post by dino99 on 2010-04-26
what you can try:

into synaptic, remove/purge plymouth then reinstall

and/or into console: sudo dpkg-reconfigure plymouth

---

### Post by espenfjo on 2010-04-26
plymouth wont remove/purge completely, since cryptsetup and mountall depends on it.
> 
sudo aptitude purge plymouth plymouth-label plymouth-theme-sabily plymouth-theme-solar plymouth-theme-spinfinity plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  cryptsetup mountall 
The following packages will be REMOVED:
  plymouth{p} plymouth-label{p} plymouth-theme-sabily{p} plymouth-theme-solar{p} plymouth-theme-spinfinity{p} plymouth-theme-ubuntu-logo{p} plymouth-theme-ubuntu-text{p} plymouth-x11{p} 
0 packages upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2*437kB will be freed.
The following packages have unmet dependencies:
  cryptsetup: Depends: plymouth but it is not installable
  mountall: Depends: plymouth but it is not installable
The following actions will resolve these dependencies:

Install the following packages:
plymouth-theme-text [0.8.2-2 (lucid)]

Keep the following packages at their current version:
plymouth [0.8.2-2 (lucid, now)]

Leave the following dependencies unresolved:
ubuntu-desktop recommends plymouth-theme-ubuntu-logo
ubuntu-desktop recommends plymouth-x11
ubuntu-standard recommends plymouth-theme-ubuntu-text
Score is -10545



So i removed all but plymouth and plymouth-theme-text.
> ran dpkg-reconfigure plymouth
aptitude install plymouth-theme-ubuntu-logo 
update-alternatives --config default.plymouth

dpkg -l | grep plym
> ii  libplymouth2                                                0.8.2-2                                         graphical boot animation and logger - shared
ii  plymouth                                                    0.8.2-2                                         graphical boot animation and logger - main p
ii  plymouth-label                                              0.8.2-2                                         graphical boot animation and logger - label 
ii  plymouth-theme-text                                         0.8.2-2                                         graphical boot animation and logger - text t
ii  plymouth-theme-ubuntu-logo                                  0.8.2-2                                         graphical boot animation and logger - ubuntu


Still no go.

---

### Post by rayraven on 2010-04-26
Try this, as root: [sudo su]

```

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

```

That should make plymouth appear. But, it might delay your boot a tad-bit.

---

### Post by KlavKalashj on 2010-04-26
> **rayraven said:**
> Try this, as root: [sudo su]

```

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

```That should make plymouth appear. But, it might delay your boot a tad-bit.

This is an amazing fix, it delays boot with maybe like 0,5 secs, but the entire boot is beautiful. Love it.

---

### Post by espenfjo on 2010-04-27
Still not working here :\
I have also FRAMEBUFFER=y in /etc/initramfs-tools/conf.d/plymouth

---

### Post by timosha on 2010-04-27
> **rayraven said:**
> Try this, as root: [sudo su]

```

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

```That should make plymouth appear. But, it might delay your boot a tad-bit.

Works for me. Thank you very much =D>

---

### Post by scottuss on 2010-04-27
I'm going to try this fix tonight because I'm having the same problem. Out of interest, has anyone reported this bug? I subscribed to an existing one, but nothing seems to be happening. If the work-around works OK then I'll be happy(ish) but I'd rather not have the boot delay ;-)

Also, updates might break this?

---

### Post by P4man on 2010-04-27
> **rayraven said:**
> Try this, as root: [sudo su]

```

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

```

That should make plymouth appear. But, it might delay your boot a tad-bit.

Thanks a lot. Also worked on my old radeon!

---

### Post by aidanr on 2010-04-27
> **rayraven said:**
> Try this, as root: [sudo su]

```

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

```

That should make plymouth appear. But, it might delay your boot a tad-bit.

Helped me out too (eee 901).

---

### Post by dino99 on 2010-04-27
just got plymouth packages updates

---

### Post by philinux on 2010-04-27
> **dino99 said:**
> just got plymouth packages updates

I've got this bookmarked just in case a real fix emerges,

Meanwhile the fix above is in place and working well here, nVidia 8600GT.

[https://launchpad.net/ubuntu/+source/plymouth/+changelog](https://launchpad.net/ubuntu/+source/plymouth/+changelog)

---

### Post by rifak on 2010-04-27
this worked for me also. im running a macbook3,1 with intel gm965. are there any downfalls in using this fix? also, what will need to be changed when an update occurs? will this be a persistent change, or will this need to be done every time plymouth is updated?

---

### Post by garvinrick4 on 2010-04-27
This is bug#540801 in launchpad.net.  Mr Remnant will explain why it works . When this fellow speaks you can
take it to the bank. 



[Scott James  Remnant]("https://launchpad.net/%7Escott")             wrote             on 2010-03-18:               [                 **Re: X server starts before Plymouth**               ]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2")                                              [  #2]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2")                                                        The problem here is the graphics  drivers; on your system they're taking longer to load than it takes to  check and mount the filesystem - so there's no reason to start the  splash screen, since we can already start X.
 On HDD-based systems this is worse because we do the ureadahead phase  before loading drivers; thus it can take a long time for a splash to  appear.
 One "solution" is to use the initramfs and start plymouth as a  critical step:
   echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
  update-initramfs -u
 But that introduces a significant delay into boot just to get the  splash screen up for the rest of it.

---

