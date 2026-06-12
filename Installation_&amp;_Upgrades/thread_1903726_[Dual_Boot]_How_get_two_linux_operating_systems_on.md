---
title: "[Dual Boot] How get two linux operating systems on one laptop?"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by clueless1337 on 2012-01-03
So I have Ubuntu linux 10.4 on my laptop right now, but I would like to have another linux version aswell on this laptop, how can I do this?

I imagine I have to use a dual boot to do this, but since I have never done anything like this before I am asking for your help.


Sorry if this is in the wrong section, but I just have no idea where I should have posted this

---

### Post by Elfy on 2012-01-03
yep - dualboot or if you have sufficient specs try virtual machines.

If you do want to dualboot then - BACKUP :)

Not sure what you want to dualboot so not sure if it's got partition editor tools - I expect so.

Basically I would resize the current install partition to allow enough space for whatever you want to install, then install to that partition.

Generic advice - but as yet no real idea of what you have there to deal with :)

Give us the output of 

sudo fdisk -l

as a start.

What do you hope ot dualboot with - or are you expecting to try more than one OS.

---

### Post by clueless1337 on 2012-01-03
I put a screenshot of the output I'm getting when I do sudo fdisk -l  under this post.

Basically I would like to dual boot Backtrack Linux as second OS (or Linux Mint)

I don't really think this laptop has enough power to run it on a virtual machine, so I think dual boot would be a better option

---

### Post by Elfy on 2012-01-03
Boot with the livecd - go to the partition editor - right click sda1 - resize - apply.

Create new partition in the unallocated space. Make not of name - possibly sda3

Start the installer - when you reach the partition part - select your new partition - you'll need to edit/change it - you will wnt to set mountpoint to /

If possible also set grub to the new partition if you want your ubuntu to control grub.

Install.

Backup anything you'd not want to lose - just in case something goes awry in the resizing operation.

---

