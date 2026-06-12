---
title: "Replacing and or deleting an (K)ubuntu install, without removing GRUB"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by Flazer on 2011-12-24
First, I apologize in advance.  I've searched and searched and couldn't find what I was looking for.  So if this is a repeat post of something that has been covered, can someone post a link?  Thanks.

So I figured I'd ask it here. I bought a small netbook (ASUS eeepc 1005hab) to use at school, because carrying my full size laptop was getting too much on transit etc.

My question is, I was trying different linux distros out, like Kubuntu, Ubunutu, etc., but decided I don't really like Kubuntu, takes up too much RAM . I did a full install rather than trying live cd like an idiot, and now I want to replace it with plain Ubuntu.

Anyone have an easy way to delete the Kubuntu partition, swap it out with one of the others, or something similar without reformating the whole drive and blowing my XP partition out of the water. The only reason I'm worried about that is the netbook doesn't have a CD drive, and the only stuff that came with the netbook were recovery CD's...explain that one to me.

Anyway, hope to get some help from you guys.

For reference.  I have an XP partition, and a Kubuntu one at this time.  I'd like to remove/replace Kubuntu with Ubuntu.

I have the same problem on my old Dell laptop set up as well :lolflag:

---

### Post by darkod on 2011-12-24
If I understood correctly you want to install Ubuntu over the Kubuntu?

It's very easy. First of all, boot Kubuntu and in terminal execute:

sudo fdisk -l (small L)

to see the partitions. If you do know which is your root partition and which swap, you don't need this step. Post the results here if you don't know what is what.

Once you know your root and swap partitions, boot the ubuntu usb and start the install. In the partitioning step select Something Else (manual install). It will open a list with your partitions.
Select the root partition (usually the larger one), and hit the button Change under the list. In the windows that opens, leave the size as same, change the Use As to ext4, tick the Format box and change the Mount Point to /. Close that window.
Then select the swap partition (the smaller one), and again Change. Leave the size as same, change the Use As to swap area. Swap has no mount point so no need to select anything.

That's it. Continue with the install and it will install ubuntu where you told it to, on the same partitions. Of course, this will destroy all data in Kubuntu, so copy anything you need first.

---

