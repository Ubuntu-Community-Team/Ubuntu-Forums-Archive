---
title: "UUID issues when cloning?"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by mathog on 2010-05-19
I am going to clone a 10.4 LTS workstation to identical hardware.   All UUID references have been purged from /etc/fstab
(which now uses LABEL= references instead) and from /boot/grub/menu.lst (which uses groot=(hd0,1), and LABEL= where it had been UUID=).

My question is, are there buried UUID references in the initrd.img, or will these changes be sufficient?  I ask because recent experience with Mandriva  turned up exactly this issue.
In that instance the clone script did

```
partition new disk
make file systems on it
mount root partition
mount boot partion
copy boot and root from the template machine

```

Unfortunately the second step created new UUIDs which did not match those in the initrd.img copied over in the last step.  So the clone would not boot.  I would like to know if Ubuntu does the same thing before this issue bites me again.

If there are hidden UUIDs in the Ubuntu initrd.img (from the initial install), is there some way to make a new initrd which will use the same access methods as are current in /etc/fstab and /boot/grub/menu.lst?

Thanks.

---

### Post by mathog on 2010-05-19
Also possibly related, where the heck is the default run level being set?  /etc/init/rc_sysinit.conf is hardwired to start in run level 2, but the system boots to run level 5 (GDM starts, ssh will let anybody login), and there is nothing in the /boot/grub/menu.lst
file that looks to me like it is telling the initrd.img to go to graphical multiuser mode.

---

### Post by srs5694 on 2010-05-19
I'm not sure about UUID references in Ubuntu's default initrd, but I believe you're mistaken about the runlevel. Ubuntu follows the Debian model of runlevels, in which the launching of X is *not* tied to a particular runlevel. The "X in runlevel 5" model is used by Red Hat, Fedora, Mandriva, and related distributions, but not by Ubuntu. I just checked to be sure, and my Ubuntu-based MythTV system is currently in runlevel 2, and X does start. I'm quite sure I haven't messed with its configuration on this score.

---

### Post by mathog on 2010-05-20
> **srs5694 said:**
> Ubuntu follows the Debian model of runlevels, in which the launching of X is *not* tied to a particular runlevel. The "X in runlevel 5" model is used by Red Hat, Fedora, Mandriva, and related distributions, but not by Ubuntu. I just checked to be sure, and my Ubuntu-based MythTV system is currently in runlevel 2, and X does start. 

Hmm, so what is the approved way to boot an Ubuntu system without automatically turning on X11 and the GUI login?

EDIT:  found it, put "text" in as a kernel parameter in /boot/grub/menu.lst.  On the next boot it will come up without starting gdm.  Can use "startx" once logged in.

---

### Post by srs5694 on 2010-05-20
It's also possible to disable GDM in runlevel 2, just like you'd disable any other SysV service.

---

### Post by tgalati4 on 2010-05-20
With older Ubuntu distros (like Dapper) you could do a simple

sudo cp /dev/sda /dev/sdb

Put the second drive in new (similar) machine and boot.  

Besides UUID's in /etc/fstab and GRUB, there are probably references to UUID in the initrd.img and app armour profiles.  So I don't know what the simplest procedure is for cloning a system.

My guess is to make the clone then run dpkg-reconfigure kernel to recreate the initrd.img and any other UUID references required for proper operation.

Since Ubuntu is a human desktop distribution, the UUID allows for just about every conceivable disk configuration.  Since Ubuntu is not an enterprise distro, simple cloning tools don't exist.

SUSE linux has a Live Studio which is a web-based distro configurator that allows you to spin a SUSE distro just the way you want.  You then download the ISO and use that to clone your empire.

---

### Post by mathog on 2010-05-20
> **tgalati4 said:**
> references to UUID in the initrd.img and app armour profiles. 

I just gunzip'd and un cpio'd the intird from this OS, and it did not contain any UUID's, at least not any that "grep -i -r" could find.  The init script in the top directory has all sorts of code for handling UUID, LABEL, and so forth, but it is acting on whatever is passed in by grub.

Searching the apparmor area didn't turn up any UUIDs either.  There were some in /etc/blkid.tab, and of course udev typically stores MAC addresses and other machine specific bits, but the cloning scripts stomp those files after copying over the OS partitions.

So it looks like ubuntu isn't going to be too hard to clone, once it has been configured not to use UUIDs in fstab or grub.  If it turns out otherwise I will post details.

---

### Post by tgalati4 on 2010-05-20
There is also an ubuntu respin tool that I heard about on a recent [http://tllts.org](http://tllts.org) podcast but I haven't used it.

---

