---
title: "Partitioning question"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by golanhall on 2006-06-12
Bare with me I'm pretty new to Linux'ubuntu' -land.

I have a pretty good understanding how to partition, but it seems the Ubuntu installer is not clear to me.
I had 2 partitions(both ntfs) ready for installation, on the second one I installed windows so I had a fresh one (primairy) ready for conversion to ext3 and installation of Ubuntu.

When I pressed the install icon I got this wizard, I really dislike wizard when it comes to partitioning :). I was wondering what the automatic function does, my guess deleting my set-up partitions thus losing my windows install.

So I chose manual mode, played a bit with it (not yet delete/convert the prim partition). I was asked to fill in a few mount points on the next screen, also including a location for the swap file. When I entered the same hdd for the swap & root loc I got a bit 'no-can-do' screen.

Now is it my question if Linux needs a seperate partition for the swap?
I also saw that when I deleted / added a ext3 partition it removed the boot flag windows carefully placed on the prim partition. Will this boot information be gone if I delete/convert to ext3? Resulting not having the option to boot in windows mode anymore?

I really like to have everything on one disk, it is my obsessed way of organizing things :rolleyes:

---

### Post by Krusty Ruffle on 2006-06-14
[QUOTE=golanhall]Now is it my question if Linux needs a seperate partition for the swap?
I also saw that when I deleted / added a ext3 partition it removed the boot flag windows carefully placed on the prim partition. Will this boot information be gone if I delete/convert to ext3? Resulting not having the option to boot in windows mode anymore?

I really like to have everything on one disk, it is my obsessed way of organizing things :rolleyes:[/QUOTE]

Yep, swap needs to be a different partition, and it need to be formatted as swap.

I think, if I were you, I would consider deleting the non-windows partition, then making it into 3 partitions, the first one being about 150-250 MB either ext2, ext3, or reiserfs, wich will be used for /boot. Then a second one of around 250 MB formated & used for swap, then use the rest for /, formatted either ext3, or reiserfs.

After installing, grub should automagically locate & configure a boot option for Linux, & windows, though it has been a long time since I've bothered dual booting so don't quote me n that....

Hope this helps.

---

