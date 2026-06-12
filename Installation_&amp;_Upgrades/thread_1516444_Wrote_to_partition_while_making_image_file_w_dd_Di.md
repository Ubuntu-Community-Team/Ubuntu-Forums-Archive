---
title: "Wrote to partition while making image file w/ dd: Did I mess it up?"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by vincebs on 2010-06-23
Hi everyone,

I recently bought a 500 GB hard disk to replace my 120 GB one. I have an external hard drive so I did:

sudo dd if=/dev/sda of=/media/LaCie/harddisk.img

in order to make an image of the entire hard disk on my external LaCie hard drive. But being bored (and stupid), I decided to go around and edit a couple of files on the drive during the 12 hours it took to create the image file.

Now I took out the old hard disk and put in the new hard disk and booted using a Dapper Drake LiveCD and issued the command:

sudo dd if=/media/LaCie/harddisk.img of=/dev/sda

When I come back tomorrow, will my computer boot up? Or did my editing screw up my files?

(The "editing" is because I was using Karmic Koala Ubuntu on the hard disk I was trying to copy, so I probably moved things in and out of swap and temporary internet files, as well as accessing (but not editing, except for the time-stamps) of the other partitions on the hard disk.)

---

