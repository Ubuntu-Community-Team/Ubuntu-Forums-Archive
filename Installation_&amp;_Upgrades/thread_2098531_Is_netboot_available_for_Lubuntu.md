---
title: "Is netboot available for Lubuntu?"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by wagoner on 2012-12-26
I am trying to install lubuntu on one of my desktop pc's.  I was looking through the instructions to do a network install and it references netboot.  Is this available for lubuntu or any of the other ubuntu varieties?

I did a network install of another distro and it was pretty easy.  I obtained the linux and initrd files and copied them to the hard drive.  Then I rebooted and got into the grub command line and manually booted the installer.  After that it was pretty much off to the races.  

From what I can tell, netboot is only available for the main ubuntu distribution.  Does anyone know?

---

### Post by fdrake on 2012-12-26
> **wagoner said:**
> I am trying to install lubuntu on one of my desktop pc's.  I was looking through the instructions to do a network install and it references netboot.  Is this available for lubuntu or any of the other ubuntu varieties?

it's available on all linux (and windows too now)

---

### Post by Cheesemill on 2012-12-27
You can use the netboot mini.iso to boot the installer.

When you get to the tasksel screen you can select 'Lubuntu Desktop Environment' as one of the options.

[http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

---

### Post by mörgæs on 2012-12-27
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Using this script one can install LXDE (as in Lubuntu) or another desktop environment.

---

### Post by wagoner on 2012-12-28
Thanks Cheesemill.  netboot works for all of them, and I was able to choose the lubuntu desktop from the list.

---

