---
title: "cannot install ubuntu"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by wolfhowl on 2009-12-22
Hi I have a new computer that I am trying to install ubuntu onto.  I bought this computer after my xp dell crashed and I was able to recover all my data and have loaded ubuntu onto that computer successfully and I like it.  Now however when I try to load it onto my new computer it either hangs up or goes all the way through and then I get a big error message.  I have tried four different cds that have the image burned onto them and every one has a disk read error.  I have tried booting from a usb following the directions on the ubuntu web site for configuring the usb this is what I get 

it goes to a blank screen and then I press any key and get this:
done.
chroot: cannot execute apt-cdrom: Input/output error
Begin: Disabling AppArmor (does not work with stacked file systems)... ...
chroot: cannot execute update-rc.d: Input/output error
Done.
Begin: Possibly disabling update-initramfs (useless on a live CD)... ...
chroot: cannot execute dpkg-divert: Input/output error
Done.
Begin: Grant administrative PolicyKit pivilieges to default user... ...
mkdir: cannot create directory '/root/etc/' : Input/output error
/scripts/casper-bottom/44pk_allow_ubuntu: line 26: cant create /root/etc/policyKit/PolicyKit.conf: Input/output error
cp: cannot stat '/root/etc/' : Input/output error
Done.
Begin: Running /scripts/init-bottom... ...
mount: mounting /dev on /foot/dev failed: Input/output error
Done.
Target filesystem doesnt have /sbin/init.
No init found. Try passing init= bootrag.


BusyBoxv1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)

so that is where I am at.  I also checked the usb device and it came up with 23 errors on the drive so I went through the whole process of getting the program on the usb and still get the same amount of errors and the same error message

can anyone help me
:confused:



my system has this processor:
amd athlon II x2 240, 1920mb of memory and a M2N68-AM SE2 motherboard

---

### Post by Skidbladniir on 2009-12-22
Try a different CD burner, at a lower speed.  Also, any friends have Ubuntu, they can create a USB Boot from System -> Administration -> Something about USB - near end of list

---

### Post by wolfhowl on 2009-12-22
I burned one of the disks at the slowest speed possible at 4x and it still wouldnt read the disk

---

### Post by bumanie on 2009-12-22
As Skidbladniir says, try a different burner ie a friends - it has happened occasionally that trying a different burner works, also some people have also tried a different brand of cd and had success when they previously had no luck. Alternatively, you could download the .iso for the text-based installer - it often works when a live cd won't.

---

### Post by wolfhowl on 2009-12-22
Thanks I will give that a try new cds and the text based installer

---

