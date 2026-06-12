---
title: "[SOLVED] Partitioning Scheme"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Arthur Archnix on 2008-02-22
I've come up with a new partitioning scheme based on a document I read about hardening a debian server  (although, my system is a laptop and I am the sole user). I'd really appreciate your feedback / comments. 

Also, I know that the fastest part of the disk is the outside, but what partitioners should go here, and is that the first partition or the last?

You'll note the large amount of temp space, this is because I use Gimp sometimes and sometimes rip/edit dvds. Testing is where other Linux distros go, and I figured if I liked testing a lot, it's a pretty simple matter to copy things over and make it my new system.

[img]http://i256.photobucket.com/albums/hh197/ArthurArchnix/partioning.jpg[/img]

---

### Post by whazooo on 2008-02-22
why ro in /testing? Just curious..

---

### Post by Arthur Archnix on 2008-02-22
Well, if I'm booting testing then the scheme would look a little different, with all the other partitions mounted ro. But when booting the system on a daily basis there's really no need to have write access to testing. Other than that, no real reason. Just trying to follow that principle that says only grant permissions that are needed, layers of security and all that.

---

### Post by Arthur Archnix on 2008-02-27
Here's what I finally went with, all of them are mounted with the 'noatime' option

***Primary Partitions***
/sda1 - 900 MB - swap
/sda2 - 125 MB - /boot    - ext2 -    {nodev,nosuid,ro}
/sda3 - 125 MB - /nix/arch/boot     - ext2 -    {nodev,nosuid,noexec,ro}

***/sda4 - Extended Partition***
/sda5 - 04 GB - /    - ext3 - 
/sda6 - 04 GB - /nix/arch/root    - ext3 -    {nodev,nosuid,noexec,ro}
/sda7 - 04 GB - /nix/testing    - ext3 -    {nodev,nosuid,noexec,ro}
/sda8 - 03 GB - /tmp    - ext2 -    {nosuid}
/sda9 - 60 GB - /data    - ext3 -    {nodev,nosuid}

---

