---
title: "Dual Booting - Fedora and Ubuntu"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by craigpugsley on 2007-11-13
Hey all,

I'm a long-time Mac user, and had recently had the possibility of getting my hands on some new beefy hardware at work. This machine has Red Hat Fedora pre-installed. I'm currently using it mainly for development. 

But, I don't really like Fedora. Being a Mac user, I like the attention to detail, simplicity, and ease of use that Ubuntu offers (I've used a couple of version of Ubuntu in the past, but not had any hardware to install it onto full-time).

So, I'd really like to dual-boot this Fedora machine. I need to keep the existing Fedora installation, as it contains a pre-configured development environment that was set up by a guy who was a Linux guru, but has left the company.

To all intents and purposes, I'm a Linux noddy. I'm a developer, so I'm comfortable with the command line, *nix concepts and I'm not afraid to get my hands dirty.

I've popped in a Ubuntu 7.1 install CD, live distro has fired up, and I've gone to 'install' on the desktop. As I go through the install options, however, it looks like the only option I have is to completely erase the disk before installing.

Would someone mind pointing me in the right direction? I'm very keen to understand more about Linux generally, and Ubuntu specifically.

Thanks all!

---

### Post by bulldog on 2007-11-13
Well I have Fedora and ubuntu,windows and some other distro's running very well on my machine.
First thing to know is how your hdd is partitioned,if fedora uses the whole hdd,well it can be a little harder,you have to backup your data and reinstall and all that stuff.

```
sudo fdisk -l
``` will give you the information yuo need about the partitions on your hdd.

If you need help,post back.

---

### Post by craigpugsley on 2007-11-16
Thanks for your reply. 

I think your post has told me pretty much all I needed to know. The machine itself has two disks - I believe in a RAID array of some sort. I don't want to do anything to those disks that might potentially break the installation, as the set-up on there is quite unique and I have no idea how to reproduce it.

OK, another tack: if I were to put another HD in the machine and create one big partition on that, could I install on to that? Would Ubuntu automatically add itself to the bootloader that starts Fedora, or is there some magic I would need to know?

Thanks!

---

