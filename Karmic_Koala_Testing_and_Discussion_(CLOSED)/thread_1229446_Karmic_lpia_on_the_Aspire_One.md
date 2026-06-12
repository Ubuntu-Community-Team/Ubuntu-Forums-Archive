---
title: "Karmic lpia on the Aspire One"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jbernardo on 2009-08-02
I thought I'd collect my experiences installing kubuntu-netbook lpia on my Aspire One, in case anyone is stumped on the same places I was.
The first problem was to get a lpia image. Finally, I found a iso on the [ports]("http://cdimage.ubuntulinux.org/ports/daily/current/") subtree. I used the 20090801, as it was the current one yesterday. 
To put it in a USB key, I already knew I had to use the same distribution, so I installed usb-creator on a i386 karmic partition. As I had kubuntu, it installed a bunch of other stuff, but no worries. I formatted the USB key with it (and then it crashed), then used it to copy the iso to the key.
Booting with the usb key seemed to work well, and install progressed until it tried to call tasksel. I don't know if it was because of bug #[376103]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376103") or not. After three tries, I choose to let it go on and finish the install.
On boot, everything went well and I had a command prompt. No X, as that part obviously wasn't installed. I logged in, connected a network cable, and as it didn't get automagically enabled, launched the dhcp client with "dhclient3 eth0".
After having the network set up, I then tried to update my packages, but /etc/apt/sources.list had only two entries pointing to a cdrom. But there was also a sources.list.apt-setup, which had the whole list of ports repository, so it was just a matter of copying it to sources.list and commenting out the cdrom entries.
After a "sudo aptitude update; sudo aptitude dist-upgrade", I was able to install kubuntu-netbook with a simple "sudo aptitude install kubuntu-netbook". After that I installed also nn-applet, since knetworkmanager and the network-manager applet are both [still broken]("https://bugs.launchpad.net/knetworkmanager/+bug/392593"). All I did was, once again, "sudo aptitude install -R network-manager-gnome"; the -R is to make sure it only installs what is needed, not the recommendations. I do the same for firefox-3.5 to make sure it doesn't install ubufox and all the related gnome stuff.
Time for a reboot... And to find out that the xserver-xorg-synaptics driver isn't available in the lpia repositories, so the touchpad didn't work! I connected a usb mouse, and went online. I found it at Alberto Milone's [ppa]("https://launchpad.net/%7Ealbertomilone/+archive/ppa"). I added that to the repositories, and while I was at it I also added the medibuntu [repositories]("https://help.ubuntu.com/community/Medibuntu"). After a "aptitude update" I installed xserver-xorg-input-synaptics directly from the ppa ([clicked on it]("https://launchpad.net/%7Ealbertomilone/+archive/ppa/+files/xserver-xorg-input-synaptics_0.99.3-2ubuntu4netbook1_lpia.deb") and let gdebi install it), as it still wouldn't show up in the available packages in aptitude. Restarted X, and here I was with the touchpad working! Wifi works with nm-applet, and everything else was working out of the box. I didn't test the right hand card reader before I installed my customized lpia kernel - basically a ubuntu kernel with the [sickboy's config]("http://www.aspireonekernel.com/"), just updated to 2.6.31, and with CDAC modems and ECRYPT_FS enabled. 
If there is any  request for it, I can attach my config file.
I built the kernel fetching it from git and following[ this blog]("http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/"), with the relevant changes for karmic. The jbernardo comments there are mine... I had to install a chroot on a i386 machine to be able to build for lpia, but appart from that it wasn't that complicated. The hardest thing is to have to use git... ;)

Well, here it is. It isn't for the faint of heart, with the lpia iso failing to install any graphic environment*, xserver-xorg-input-synaptics missing from the ports, and knetworkmanager broken*. But now I have a fast and efficent kde environment on my aspire one, and I am happy with the results. I didn't even have to mess around with intel drivers as I did with jaunty.
I'd love your comments...

**Update**: the synaptic driver is back in lpia, so no need to install it by hand. Knetworkmanager now works, so no need for nm-applet. 

**Update2:**
I also installed karmic lpia now on my eeepc 1101HA, and it was almost the same. I left the XP install in place, and used the second NTFS partition, which I divided into /, /home and swap partitions. From there on, the install was basically the same as described above for the AA1, until the [configuration of the X drivers for the GMA500]("http://ubuntuforums.org/showthread.php?t=1253406"), which allows me to have about half the graphics performance of the AA1 instead of one hundredth. But I am now using wicd on the 1101HA, as [there is a regression in the ath9k]("https://bugs.launchpad.net/linux/+bug/414560") drivers in the latest couple of kernels, and since NetworkManager and it's frontends like to keep roaming around, it meant one minute pauses every two minutes at work, where I have various APs with the same SSID - every new scan means a reset of the ath9k, and that means almost a minute without any answer.
I also can't use grub2 on the 1101HA due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425359"), I wonder if any other user of the 1101HA is affected by it. On the Aspire One it works well.

---

### Post by adaemox on 2009-09-18
Thanks for the post, I just stumbled upon lpia while researching the up and coming lubuntu. I'm going to give karmic lpia a try on virtual box and then maybe on my laptop (not sure if that's even possible, but worth a go).

Anyway, I couldn't find an ISO until I found your post so thanks for that.

If I remember I'll respond with my experience.

---

### Post by mindwarp on 2009-09-18
I was under the impression LPIA was depreciated and only supported by Ubuntu Partners (like dell).  Fyi all LPIA is is a few GCC flags.

---

### Post by adaemox on 2009-09-19
That's good to know, I've been trying to figure out exactly what this was all about.

---

### Post by jbernardo on 2009-09-20
lpia is supposed to be "Low Power Intel Atom", so in fact i386 compatible but optimized for the atom and similar CPUs. It reportedly gives lower power consumption and might improve speed in the future, as intel compiler (IGCC) atom optimizations are ported to gcc. From the comparisons I've seen, using intel's compiler instead of gcc gives between 10% and 20% more performance of the compiled code on the atom CPUs.

---

### Post by ozorba on 2009-10-06
I have installed Karmic UNR on AAO 110 and almost everything works. 

However, I have to use the touchpad buttons to select things. It does notrecognised the double finger tab or slide on the right hand side. 9.04 was fine.

---

