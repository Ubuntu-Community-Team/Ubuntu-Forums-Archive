---
title: "Network &quot;Upgrade&quot; How?"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by kosmos on 2006-03-30
One of my computers is an old laptop that has neither a CD nor BIOS netboot. It does have a pcmcia network card, and long ago in the past, I installed fedora core 1 via a procedure like this:

- copy the vmlinuz and initrd.img from the install CD to /boot/isolinux/ (I had all the install CD files on a separate server on my LAN).
- edit /boot/grub/grub.conf and add a stanza to use those files
- reboot, and the installation procedure allows me to select install from NFS/HTTP, whatever, and I'm off and running.

It seems like decent way to go, but I can't figure out how to do this with Breezy. Since my laptop has an old version of linux on it currently, I can easily install whatever I need over the network while booted up, the problem is, I'm stupid and can't figure out exactly what I need to put in /boot to get a network install option going.

I've googled around and seen a couple people say things like Breezy will give you an option to do a network install once it finds it can't access the CD, but this is not the case for me, or I'm doing something wrong.

Anyone know what I should do to get this working? Or offer a better solution? Thanks.

---

### Post by Iandefor on 2006-03-30
The wiki has a page for this. Check it out:

[https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot)

---

### Post by kosmos on 2006-03-30
About the wiki, it relies on a floppy, which I wanted to avoid.

Anyway, here is kind of a solution that seems to be working for me so far:

I got an iso with stuff in it that understands network install from here: [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso)

I unpacked it on one of my other machines, and copied the contents to my laptop in /boot/install.

I looked in the file isolinux.cfg to check out the boot params for a server install, and added a stanza in my /boot/grub/grub.conf that included the /boot/install/linux /boot/install/initrd.gz and the boot params I wanted.

Rebooted, and it starts the installer stuff, selected the network installation parameters I wanted, and so far, it looks like its installing.

If I get stuck, I'll go back and try the install floppy, I just didn't want to deal with that since I already had an old version of linux installed, I thought it would be easier to just install the boot junk and go from there.

---

