---
title: "Mounting other linux partitions"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by igeldard on 2007-01-02
Hi,

I have a triple-boot XP, Ubuntu, Fedora Core 6 system. All boot nicely through GRUB.

But I'm unsure how to mount the FC6 installation (on hda4) so I can read files from the FC6 partition in Ubuntu (on hda3). I expect I need to edit /etc/fstab - but how exactly? 

Ian

---

### Post by coffeecat on 2007-01-02
This should do it. In a terminal:

```
sudo mkdir /media/hda4
gksudo gedit /etc/fstab
```Add this line to fstab:

```
/dev/hda4    /media/hda4    ext3        defaults    0 2
```But you're going to run into permission problems because Ubuntu and Fedora set up the first account with different UID and GID. Ubuntu does what most distros do and makes the UID of the first account 1000, whereas Fedora allocates 500, with a same name group with a GID of 500.

What you could do in Fedora is to set up another account and stipulate the UID of 1000, and also make the main group for this account 'users' which, as far as I remember, has the same GID as Ubuntu 'users' - 100.

If you want to mount the Ubuntu partition in Fedora add a similar line in fstab, but referring to hda3, having made a directory /media/hda3.

**Edit:** - I'm assuming here that your Ubuntu and Fedora partitions are both formatted ext3.

**Edit 2**: Of course, the permission problems won't apply if you are working as root in Fedora or sudo-ing in Ubuntu. But having the same UID is handy if you just want to copy/move something out of your home folder in the other distro using a Nautilus window as the ordinary user.

---

