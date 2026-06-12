---
title: "Installing over existing LUKS+LVM partitions"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by harry666t on 2010-09-02
I think I've got a somewhat unusual case here.

I've been a Debian user for a couple of years, but I've made a decision to switch to Ubuntu. I have Debian installed on LUKS+LVM, and I want to preserve my /home without moving the data to any external media (I don't have any). My partition layout is as follows:

sda1: /boot
sda2: encrypted volume (sda2_crypt)
sda2_crypt: LVM volume group, with /, swap and /home.

Having many previous (sad) experiences with completely borked experiments and data loss, I've decided to try the trick in VirtualBox first. I've installed Debian (testing, netinst, Dec 2009) with encrypted LVM, and touch'd a file in my $HOME so that I'd know if the contents were preserved. Then proceeded to install Ubuntu 10.04.1 from the alternative CD. After the installer started and loaded some of the basic components (but before it entered the partitioner) I've switched to a shell and read a scroll of identification:

```
$ cryptsetup luksOpen /dev/sda2 sda2_crypt
[entered the passphrase]
$ lvm vgscan
$ lvm lvscan
```

The partitioning program could properly see the volumes only after these magic incantations were cast. I proceeded with the installation, making sure to mark /home as "keep the data". After a few dozens of minutes the system rebooted and GRUB welcomed me (I chose legacy GRUB instead of GRUB2).

* The problem is, instead of asking for the passphrase outright, *the kernel is waiting a minute or two before dropping to a rescue shell, complaining about not being able to find root. From there, I can unlock & search for volumes manually, and only then resume booting. The rest of the boot process is OK.* Well, I usually reboot the system only once in a few weeks, so this isn't a BIG problem (typing in a few cryptic commands each time the system boots would also make me look like some pr0 h4x0r, lol), but oh well, this is going to be inconvenient on the long run.

* Another concern; after the installation, *I've noticed that the contents of my $HOME were overwritten by Ubuntu's default skeleton* (pictures, desktop, music, templates, and other crap). The control file I've touch'd after installing Debian wasn't there. I believe that this is because the installer was creating a user account with the same name as the one that was already on the disk, but I'm unsure about that. I don't want to lose my data while switching, that's the whole point of this dance.

---

### Post by harry666t on 2010-09-05
Okay, I've dealt with both issues by myself. As of asking for passphrase on boot, it seems that I should've added an appropriate entry in /etc/crypttab:

```
sda2_crypt /dev/sda2 none luks
```

And then re-generate the initrd:

```
update-initramfs -cvk all
```

The overwriting installer... I must've been incautious, because it seems that it actually doesn't overwrite anything in /home, and I've just somehow did not create my test file at all.

Hope this helps someone with a similar problem.

---

