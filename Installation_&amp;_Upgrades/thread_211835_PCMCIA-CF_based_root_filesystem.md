---
title: "PCMCIA-CF based root filesystem"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by tinmith on 2006-07-08
Hi,

I am trying to mount a root filesystem an Ubuntu Dapper system using a CF card placed in a PCMCIA slot, the problem is that PCMCIA requires all kinds of modules and tools to be running which are not typically available before the real root FS is mounted.

Previously I tried to get this working with older Ubuntu releases but I was hoping that now with the new kernel in Dapper which has PCMCIA rewritten for hotplug it would be easier to do.

Could anyone give me some pointers on how to do this? Like what modules I would need to build into my initrd filesystem or anything that needs to be done?

I was hoping to use a PCMCIA interface rather than USB because I was thinking it might have better performance during operation.

thanks,
Wayne

---

### Post by K.Mandla on 2006-07-09
I don't have an answer for you, but I thought I would suggest checking Damn Small Linux, if you haven't already. I know those folks have CF installations as an option, although I haven't ever tried one. 

I also know there is the issue of limited writes to a CF card, or something to that effect. I think the idea is to boot off the CF as if it were a CD, thereby avoiding writing to the card. And putting swap on the CF is a huge no-no.

Anyways, just some ideas.

---

### Post by tinmith on 2006-08-22
I worked out a solution to the problem!

The first thing you need to do is to make sure you have mkinitramfs installed, and then copy the /etc/mkinitramfs directory to a new one, we will call it /etc/mkinitramfs-pcmcia

Now, make a script called buildme and add the following:

[FONT="Courier New"]#!/bin/bash

VERSION=`uname --kernel-release`
NAME=pcmcia

set -xv
mkinitramfs -d /etc/mkinitramfs-$NAME -o /boot/initrd.img-$VERSION-$NAME[/FONT]


Now, edit the initramfs.conf file and make sure it says "MODULES=most" in there somewhere.


Now, create a file called modules and put the following in there:

[FONT="Courier New"]# This is to allow beeping early during boot
pcspkr

# This is to allow booting from PCMCIA-CF cards
pcmcia
pcmcia_core
ide_cs
yenta_socket
rsrc_nonstatic[/FONT]


Once you have done this, make sure you are in the directory and run ./buildme

It will generate for you an initramfs file in /boot and you can then use it. Configure your boot loader to run it, and then your PCMCIA-CF card should show up as /dev/hda on my system, or possibly another device. But it does work. The nice part about the Dapper release is that PCMCIA is now integrated nicely with hotplug, so there is no need for all the card manager stuff from before, which makes this much easier than it was before.

So now you can use a PCMCIA CF card as your root filesystem, and if your BIOS allows it, you could also boot off the CF card as well. In my case I have a Toshiba Tecra laptop and will use the SD card or USB port to actually boot the system.

regards,
Wayne

---

### Post by bernstein on 2007-01-22
Thanks a lot Wayne for figuring this out !! I've spent uncountable hours searching for this solution ! and as always : if one knows how, it's dead easy :-)

Ajusted the guide to work on edgy (one of the modules has changed)

Created an appropriate wiki entry : [BootFromPCMCIA]("https://wiki.ubuntu.com/BootFromPCMCIA")

---

