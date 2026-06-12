---
title: "[SOLVED] How do I use all unallocated space in gparted?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by bluenova on 2006-06-03
Hi guys and gals,

I am trying to follow this guide:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)
so that I can do a clean install of Dapper without losing my home folder. The problem I have is I already had 20Gb of unallocated space from an old win xp installation, and after resizing my Linux partion I now have 2 lots of unallocated space. How can I use all this space to make my new /home partition?

At the moment gparted looks like this:

Unallocated 20Gb
/dev/hda2/ ext3 48.83Gb
Unallocated 44.22Gb
/dev/hda3 extended 1.44Gb
******/dev/hda5/ Linux-swap 1.44Gb

So I can either use the 20Gb or the 44.22Gb to use for /home but not both.

I need a quick answer please as I'm booted via the live cd at the moment.

Thanks for your help.

---

### Post by curuxz on 2006-06-03
can you post the mount points for all of those partitions or even better a screenshot of the GTparted window

---

### Post by bluenova on 2006-06-03
Hi curuxz,

Well I decided to go ahead and use the 44.22 of unallocated for now as I need to get this done. (girlfriends complaining about lack of internet access on her machine :D). I'll look at getting that 20Gb back later.

---

### Post by bluenova on 2006-06-04
Well this is how gparted looks:
[IMG]http://www.mmwebsites.com/Screenshot-GParted.png[/IMG]


Any ideas how I can use the free space in hda1?

---

### Post by bluenova on 2006-06-05
Bumpedy bump

So I'm looking to use that unallocated space in hda1, but it won't let me use it, even when booted via live cd and all disks unmounted, it just won't let me make the partition any bigger :(

---

### Post by bluenova on 2006-06-06
Any one can help?

---

### Post by glotz on 2006-06-06
You'll need to unmount either of the surrouding blocks, hda1 or hda2. You'll need to boot using a liveCD to do that probably. You can use the 6.06 desktop cd for example or gparted offers a small live cd just for the purpose. Then you can resize either (or both, whatever you like) of those partitions.

---

### Post by bluenova on 2006-06-06
[QUOTE=glotz]You'll need to unmount either of the surrouding blocks, hda1 or hda2. You'll need to boot using a liveCD to do that probably. You can use the 6.06 desktop cd for example or gparted offers a small live cd just for the purpose. Then you can resize either (or both, whatever you like) of those partitions.[/QUOTE]
Yea, I know that, that's how I made the home partition, but it still won't let me use that unallocated space on hda1

---

### Post by glotz on 2006-06-06
So you unmount hda1, click on resize and drag&drop the start of the partition to the beginning of the unallocated space and then hit apply. Where's your problem?

---

### Post by bluenova on 2006-06-06
[QUOTE=glotz]So you unmount hda1, click on resize and drag&drop the start of the partition to the beginning of the unallocated space and then hit apply. Where's your problem?[/QUOTE]
It won't let me do it. I could make hda1 smaller, but it won't go any bigger. I guess because hda1 is after the unallocated space, but there must be some way I can use it. Perhaps gparted is too limited?

---

### Post by bluenova on 2006-06-11
Bump

---

### Post by glotz on 2006-06-11
I guess you could try making an ext3 of the unallocated space and copying hda1 to it, then making sure you've got a working copy (need to edit /etc/boot/menu.lst **on both partitions to point to the kernel on the new partition** and /etc/fstab **on both partitions to point / to the new partition**) and then removing the old hda1 and then trying to resize the new partition containing hda1. This potentially could get very ugly. Maybe wait for other suggestions if somebody would come up with something more rational...

---

### Post by RRS on 2006-06-11
[QUOTE=glotz]I guess you could try making an ext3 of the unallocated space and copying hda1 to it, then making sure you've got a working copy (need to edit /etc/boot/menu.lst **on the old hda1 to point to the kernel on the new disk** and /etc/fstab **on the new disk to point / to the new disk**) and then removing the old hda1 and then trying to resize the new partition containing hda1. This potentially could get very ugly. Maybe wait for other suggestions if somebody would come up with something more rational...[/QUOTE]

Basically, yes, that's the way to do it. An existing partition can only be expanded upwards (to the right as shown in the graphic.)

After removing hda1 and adding it's space to the new partition I believe you should be able to rename the new partition to hda1 and avoid having to mess with fstab, grub, etc.

---

### Post by glotz on 2006-06-11
Ahh, trixy! :)

---

### Post by bluenova on 2006-06-13
Thanks I'll give it a go.

---

