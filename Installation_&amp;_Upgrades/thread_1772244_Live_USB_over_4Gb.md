---
title: "Live USB over 4Gb"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by hackthis02 on 2011-05-31
I need to make a live disk on a USB but it needs to be around 20GB. I searched around and come up with nothing.This is so I can install a custom Linux 10.10LTS on computers of different hardware config.

---

### Post by jerrrys on 2011-05-31
a persistent install?  that can be done with 'usb-creator'

---

### Post by hackthis02 on 2011-05-31
I've looked into that, but it needs a ISO image to make a bootable drive and ISO can only be 4GB. I'm looking for a way to copy my HD (around 20GB) onto a flash drive and make it into a bootable live environment.

---

### Post by Skaperen on 2011-05-31
I never heard of 10.10 LTS.

But I have made flash drive images of 10.04.2 LTS, 10.10, and 11.04, only in desktop editions, if any of these would help.  What you would do is first run "dd" to copy the image to the drive at sector 0 (e.g. the whole drive, not a numbered partition, like maybe /dev/sdc or such, wherever your flash drive shows up).  Then run fdisk on that drive and add another partition at the end of the existing one.  Then format that new partition and populate it with your stuff.  After the regular install, you have to get your stuff yourself.

If you are integrating your stuff into the installer and making a new ISO, you may be out of luck.  But you can make much larger ISOs for BluRay media (up to 50GB).  But you'd need a BluRay drive on the machines to use the optical media, so I see why a flash drive is a big plus for this.  But I don't know if the other tools for making flash drive installers can handle that size.  Maybe usb-creator can?  I've never tried that or have any idea what means it uses, so I cannot say.

Let me know if you want to try one of the flash drive images I made (slightly larger than original ISOs).

---

### Post by oldfred on 2011-05-31
Several alternatives. If you just have a few configurations, you can copy each as an ISO to a flash drive and loop mount boot each ISO with grub2.

You could create a base line all updated ISO to install then run scripts to add the additional changes.

Custom Ubuntu Live USB - debian-live scripts post by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=1740975](http://ubuntuforums.org/showthread.php?t=1740975)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Document system backup or multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by psusi on 2011-05-31
10.10 is not an LTS release.

---

### Post by hackthis02 on 2011-06-01
Yeah sorry it's 10.04 LTS. I was using remastersys but when we got all the things int he system, it became to big for the ISO image. And I don't think something like Clonezilla would work simply because my boss wants one image to be able to go on a wide range of hardware configurations. If there was a way to set out Linux so that is reconfigured itself on the first boot up after the flash, that would be a viable option. Is that possible?

---

### Post by psusi on 2011-06-01
What needs reconfigured?  Generally one image will boot just fine on all kinds of hardware.

---

### Post by hackthis02 on 2011-06-01
So I could make one clone from Clonezilla and it would flash onto any computer?

---

### Post by psusi on 2011-06-01
> **hackthis02 said:**
> So I could make one clone from Clonezilla and it would flash onto any computer?

Yep.

---

### Post by hackthis02 on 2011-06-01
I just read about Live USB Persistent mode. Thinking that might be my answer.

---

### Post by Skaperen on 2011-06-02
> **hackthis02 said:**
> Yeah sorry it's 10.04 LTS. I was using remastersys but when we got all the things int he system, it became to big for the ISO image. And I don't think something like Clonezilla would work simply because my boss wants one image to be able to go on a wide range of hardware configurations. If there was a way to set out Linux so that is reconfigured itself on the first boot up after the flash, that would be a viable option. Is that possible?
So what you are trying to do is make an installer that would install an identical, but highly customized (lots of added packages, custom files, tweaks, etc) setup on each machine?  And the resulting ISO was more than the 4.70 GB that would fit on a DVD?  If you don't need to make many copies of this, maybe a dual layer DVD will work (8.54 GB).  Of course, every machine will then need a dual layer capable DVD drive (most are now days, but some older machine might not handle it).  A USB DVD drive would be a workaround (since you were thinking USB, I assume all your machines have that).

Another alternative, which is what I do, is just install using a regular ISO image, the normal base system.  Then I run rsync to drag in a collection of files into a directory within /tmp, and run all the numbered scripts within a specific subdirectory of that collection.  These scripts then do upgrades, tweaks and extra installs.  I find it easier to change than building a new ISO.

---

