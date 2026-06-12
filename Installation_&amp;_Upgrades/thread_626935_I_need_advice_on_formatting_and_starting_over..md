---
title: "I need advice on formatting and starting over."
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by squirage on 2007-11-29
Hi All,

  I've made my Vista partition unbootable some how and I have upgraded from edgy to Feisty to Gutsy for various reasons but I have a lot of bugs and have lost recognition of my sound card.

  I can't recover with the factory recovery disks and was wondering if using Gparted to reformat and repartition would be the way to go?

  I am also toying with the idea of making a /home partition in addition to making partitions for trying out some other distros.

  I have seen some tips on psychocats, lifehacker, etc. does any body have a procedure they prefer?

  Just to recap:

  1. Suggestions on best practices for reformatting drives

   2. Suggestions for best practices for multiboot setup

I'm curious how you all are looking at it.

---

### Post by jpittack on 2007-11-29
I still need to get around to writing my how to, but here is how I set up.

vista partition
two recovery partitions installed by manufacturer- dell
(if these are deleted, vista does not boot)
extend partition
/ partition
/home partition
swap
swap partition fat32, meaning both OSes read it
some extra space at the moment for the next linux distro i use

---

### Post by squirage on 2007-11-29
Hi jpittack,

  Thanks, I have a partition that calls itself Toshiba system Volume that may have something to do with the recovery. When I look at those NTFS partitions I get the ! symbol and it shows their size, but not that anything is used.

  I know that the data is still there because I recovered it.

Thanks again for the feed back.

---

