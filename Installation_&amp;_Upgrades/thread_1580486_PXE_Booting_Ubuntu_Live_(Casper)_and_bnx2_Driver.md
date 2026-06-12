---
title: "PXE Booting Ubuntu Live (Casper) and bnx2 Driver"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by c0mm on 2010-09-23
Hello,

I don't know if this is the right place to post, please move if required.

I have a Dell R610 that has a Broadcom BCM5709. I have a PXE server setup to boot Ubuntu Live (Casper), this has been tested to work fine for other servers.

The problem I faced first was getting the bnx2 driver into the initrd.lz, which I figured out. The driver is now loaded but when the init scripts run they seem to get stuck trying on a ipconfig line.

I've attached a screenshot of the error.

Basically it gets to the point of mounting the root filesystem which is nfs. At which point it runs configure-networking and then two ipconfig lines, which seem to load the bnx2 driver, and try to configure it for dhcp. This however fails.

Here is my pxelinux.cfg

default live
label live
  menu label ^Try Ubuntu without installing
  kernel ubuntu/desktop-lucid/vmlinuz
  append  boot=casper netboot=nfs nfsroot=192.168.21.236:/mnt/media/ubuntu-10.04-desktop-i386 initrd=ubuntu/desktop-lucid/initrd.lz ip=dhcp --

It's taken me a while to get this far, and I'd like to at least get this boxed booted with some sort of linux using PXE.

---

### Post by c0mm on 2010-09-24
Alright, found the problem. It was DHCP, hence why it was pausing.

---

### Post by snakt on 2011-02-15
Thanks for the info.

---

### Post by deadtrout on 2011-03-05
How are those R610's doing?  I'm currently setting up a few R610's with Ubuntu as replacements for Solaris on Sun x2200's.  I'm looking forward to ditching Solaris completely someday.

Thanks for the info!

---

