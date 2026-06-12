---
title: "During Install - Install Grub To Root Partition Not MBR?"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by DasFox on 2011-05-07
During the Kubuntu installation, can you pick to install Grub to the root partition not the MBR?

I already have a bootloader I use with other systems on the box, that is already on the MBR that I want to keep there and not have overwritten, so it's important I can install to the root partition.

I remember in older versions of Ubuntu you could pick where to install Grub, now I'm not sure if I've overlooked it, but now it all seems like it's just been dumbed down and all you can do is install to MBR, which is done automatically, with no options... :(


THANKS

---

### Post by ottosykora on 2011-05-07
> **DasFox said:**
> During the Kubuntu installation, can you pick to install Grub to the root partition not the MBR?

I already have a bootloader I use with other systems on the box, that is already on the MBR that I want to keep there and not have overwritten, so it's important I can install to the root partition.

I remember in older versions of Ubuntu you could pick where to install Grub, now I'm not sure if I've overlooked it, but now it all seems like it's just been dumbed down and all you can do is install to MBR, which is done automatically, with no options... :(


THANKS

well yes this is possible, but kind of hidden, you have to get to some extra button during the install and mark explizit where it should be installed.

The big problem is, that when you do so, the grub2 may become unstable and also you will get warnings that this kind of installation is not supported yet or is unstable or what ever from grub itself.
I managed to screw up my system by that.

But once you mange to install it run it properly, in such config it is recomended to replace the grub2 by the grub legacy, then it will work stable, with any proper bootmanagers for ever.
Legacy grub is stable the grub2 makes too many problems if run just from root partition according to the authors of it.

try
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by kansasnoob on 2011-05-07
> **DasFox said:**
> During the Kubuntu installation, can you pick to install Grub to the root partition not the MBR?

I already have a bootloader I use with other systems on the box, that is already on the MBR that I want to keep there and not have overwritten, so it's important I can install to the root partition.

I remember in older versions of Ubuntu you could pick where to install Grub, now I'm not sure if I've overlooked it, but now it all seems like it's just been dumbed down and all you can do is install to MBR, which is done automatically, with no options... :(


THANKS

I think other than artwork Kubuntu is the same as Ubuntu :confused:

In Ubuntu the grub-install option is only available when using the manual partitioning option (now called Something Else), very similar to this:

[ATTACH]191445[/ATTACH]

---

### Post by Rubi1200 on 2011-05-07
As kansasnoob pointed out, you can only choose to install GRUB to a partition when using manual partitioning.

Unfortunately, the option to not install a bootloader was not put back in for 11.04.

---

### Post by DasFox on 2011-05-07
I picked 'Something Else' I did not see any options for Grub...

So legacy Grub is better for the root partition?

But if this is true and then as pointed out by Rubi1200 that you can't pick to not install it, then this is really stupid on the part of Canonical that everyone is just a newbie and wants to do everything your way and you give the end-user no choices...

Really sad... :(

---

### Post by wilee-nilee on 2011-05-07
> **DasFox said:**
> I picked 'Something Else' I did not see any options for Grub...

So legacy Grub is better for the root partition?

But if this is true and then as pointed out by Rubi1200 that you can't pick to not install it, then this is really stupid on the part of Canonical that everyone is just a newbie and wants to do everything your way and you give the end-user no choices...

Really sad... :(

You weren't looking close enough.;) choosing something else takes you to a gui for choosing a selected partition, in that gui screen below choices window is a button, drops up or down and lists the places for grub put it in the Kubuntu partition.

---

### Post by wilee-nilee on 2011-05-07
Modified screen shot from post #3 it seemed to have no resonance for you; see if it does now.lol.;)
[ATTACH]191507[/ATTACH]

---

### Post by DasFox on 2011-05-07
Ok my bad...

By the way is anyone running Grub2 on the root partition and having success or it's not good?

Another thing, I use to own a macbook pro and when Snow Leopard came out I bought the DVD and since have learned how to use it and install it on a PC, so I have Chamelon as the bootloader on the MBR I was thinking to keep, but I have read some people saying that Grub2 detects the OSX partitions and adds an entry into grub, so I'm wondering if I install it to the MBR if it might just boot OSX?


THANKS

---

### Post by wilee-nilee on 2011-05-07
> **DasFox said:**
> Ok my bad...

By the way is anyone running Grub2 on the root partition and having success or it's not good?

Another thing, I use to own a macbook pro and when Snow Leopard came out I bought the DVD and since have learned how to use it and install it on a PC, so I have Chamelon as the bootloader on the MBR I was thinking to keep, but I have read some people saying that Grub2 detects the OSX partitions and adds an entry into grub, so I'm wondering if I install it to the MBR if it might just boot OSX?


THANKS

There is a apple part of the forums, you might report yourself asking the mods for their opinion here. A header more relevant ie apple computer kubuntu blah blah, you know what I mean, might be helpful, or a shiny new thread.

To help in general we need all the facts up front so just remember this.

You wont get in trouble if you report yourself, the mods and members want you all set up, it is just a matter of utilising the tools of the forum, when you have a not so common set up. 

Two others in this thread and myself spend a lot of time helping on boot problems, personally I know nothing about apple, they may but I don't recall ever seeing them comment in this area.:)

Here is the apple part of the forum.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

I don't think that it is against the rules to start a new thread as long as you post a link to this one, use your own judgement here.

---

### Post by DasFox on 2011-05-07
Ok thanks...

Well I got nothing to loose, so I'll just install it to the MBR and see if ti detects it and if not, rip it out and install legacy to root and reinstall Chamelon, it's not a problem for me, just thought I'd ask before jumping....


THANKS

---

