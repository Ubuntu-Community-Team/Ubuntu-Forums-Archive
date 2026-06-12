---
title: "Partition Installation Questions !"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by A4orce84 on 2008-08-25
Hey Everyone,

I'm new to Ubuntu, been rocking Windows for a while..but wanted to play around with it.

Basically I have a single HD laptop with Windows installed, and created a 5 gig partition so I could use Ubuntu:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2353.jpg[/IMG]

It's the Fat32 partition in the picture. Anyways everytime I select it and try to go to the next step, I see this:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2357.jpg[/IMG]

I click on the edit partition setting, but am confused about what the file system and mount point are....and which one I should be using.

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2359.jpg[/IMG]

If anyone could offer any help, I would GREATLY appreciate it! Thanks guys! =)

--A4orce4

---

### Post by Partyboi2 on 2008-08-25
Ubuntu uses ext as there filesystem, so when making the partition make it a ext3 partition. The recommended minimum space for ubuntu is 8 gig, so you would need to increase the partition size , but if you are able to I would personnaly recommend alittle more eg 15 gig.
 You will also need to make a swap partition as well which is roughly 1.5 to x2 the amount of onboard ram you have.
eg.
/ 13 gig
swap 2 gig (1 gig ram)
When you are manually making the partitions make sure that you choose a mount point for the /root partition. So from the list choose / (root) When it comes to the swap partition choose "swap".

---

### Post by A4orce84 on 2008-08-25
Thanks!

I started installing ubuntu, and I almost made it to the end of the installation...then this happened:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2366.jpg[/IMG]

Any ideas?

---

### Post by Partyboi2 on 2008-08-26
What is your sda1  (fat 16) partition for? Looks like grub is trying to install to that partition.

---

### Post by A4orce84 on 2008-08-26
Dell's dumb diagnostic utilities, can't I put it all on SDA5?

---

