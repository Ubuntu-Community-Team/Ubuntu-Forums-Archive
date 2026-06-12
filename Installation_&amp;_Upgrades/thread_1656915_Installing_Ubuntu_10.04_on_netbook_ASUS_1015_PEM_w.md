---
title: "Installing Ubuntu 10.04 on netbook ASUS 1015 PEM without destorying Win 7 Starter"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by digimas on 2010-12-31
Hello everyone,

I just got an ASUS Eee PC 1015 PEM and wanted to install 10.04 on it without destroying the Win 7 Starter installation.

I booted up a live cd and went through the steps until I got to the partitioning menu. My 250 GB hard drive was already partitioned into 4 different sections:

1.) 100 GB for Win 7 Starter, C: drive
2.) 120 GB for Ubuntu installation, (previously D: drive)
3.) 29 GB for Win 7 Starter, (unknown purpose)
4.) Less than 1 GB, (unknown purpose)

I was going to install Ubuntu on the second partition but ran into trouble when trying to define a swap partition. 

Do I need to repartition the hard drive to give myself a swap partition? How could I do this without affecting Win 7 Starter?

How large of a swap partition should I have?

Also, I've seen something called "Unity" while searching around. Is this something I should have since I'm using a netbook? Will it make much of a difference in performance? Can I install it after installing 10.04?

If anyone has had any experience installing Ubuntu on this particular system and can offer some guidance your help would be greatly appreciated.

Thanks,
Digimas

---

### Post by lithopsian on 2010-12-31
I would suggest not bothering with the swap partition if you are at all concerned about partitioning your drive.  Using a swap file is just as effective on any recent Linux kernel and that can be done (and redone) at any time after installation.  Maybe it will even prompt you during installation?

Unity is a sort of desktop on top of a desktop, standard on Maverick Netbook edition.  It provides an interface which my nephew says is like iTunes, with rather larger buttons down the left of the screen and a thinner panel along the top.  I don't like it, especially on smaller screens, but some people do.  It is certainly slower than a more minimal desktop, you'll have to see how it is on your hardware.  Strange that such a heavy a space-consuming desktop is used for the devices with the weakest CPUs and the smallest screens, but the kids do seem to like it more than me.

You can always change to a different desktop if you don't like it, although it can sometimes be a little difficult to find your way out of Unity!  Underneath there somewhere should be Metacity, but I think Openbox is also in the default install.  Otherwise, they're all easily available in the default respositories.

---

