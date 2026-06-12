---
title: "Installing ubuntu on raid"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2007-03-17
Hi

I'm still trying to follow various tutorials for dual booting xp, vista and ubuntu on a nvraid drive set... getting closer now :)

I decided to use Feisty because of the things I had been reading about it being more compatible with my nv680i mobo and nv 8800gtx gfx card, but all the guides are for edgy and below, so I am not sure if something has changed for feisty or there are problems with the guides...

I have xp and vista successfully dual booting with xosl, and i am no trying to install ubuntu.

A number of the guides go through the steps of creating the partitions manually setting up the filesystems, installing and running debootstrap, making a target mount for the new os install, chroot to the target folder, then install the base system.

This is where I am stuck, with 2 things:

1) The guides say to execute 'apt-cdrom add' which I do, but this always fails saying it can't find the cd (I did assume that this won't matter as I have got the network working so I can just get the files from the online repository rather than the disc)
2) Then they say 'apt-get install ubuntu-base', when I do this it can't find the package, and after much searching i can't find anything that references this package.

Can someone help me, how do I add the cd repository (or at least confirm if I need to or not) and where can I find the ubuntu-base package, or what packages do I need to install to get ubuntu up and running?

Many Thanks

Matt

---

### Post by DJMatty on 2007-03-17
Just discovered that ubuntu-base has disappeared in edgy and above, and I should use ubuntu-minimal or ubuntu-standard instead...

Onto installing ubuntu-desktop now :)

Matt

---

### Post by tomazb on 2007-03-18
I followed the advice from [http://htglimited.com/2007/02/24/ubuntu-on-sun-fire-x2200](http://htglimited.com/2007/02/24/ubuntu-on-sun-fire-x2200) + adding pwconv in order to be able to get rid of chage errorrs. Anyway, things became tricky after installing ubuntu-desktop... After logging in GNOME Settings Daemon had major problem which made logins slow and desktop barely usable. Any ideas?

Thanks.

---

### Post by DJMatty on 2007-03-18
Well I completed the install a number of times, I now have GRUB allowing me to boot the o/s, but every time it tries to load it comes up with:

ALERT! /dev/mapper/nvidia_dsdhgsdhg does not exist! Dropping to a shell!

If i then run "ls /dev/mapper" i only get control, not the raid mappings

If i run "dmraid -ay" then the raid partitions appear in /dev/mapper

What I don't know is how to get that to work automatically.

Being a noob at this I am not sure what to do next... I guess it's not loading dmraid properly in the initrd image... but i really don't know how to fix it, and my searching of the net hasn't turned anything up yet.

Matt

---

### Post by tomazb on 2007-03-18
Sounds like you did not update initramfs:

update-initramfs -c -k `ls /lib/modules`

---

### Post by DJMatty on 2007-03-18
I did try that, but it didn't work...

It seems like the dmraid is in the initrd, just not activated. And I don't know how to get it to activate.

I have decided to give up and just install ubuntu on a regular SATA drive :(

Matt

---

