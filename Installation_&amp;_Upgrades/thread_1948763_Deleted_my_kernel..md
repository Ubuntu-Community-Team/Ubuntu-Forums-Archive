---
title: "Deleted my kernel."
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by Pitmaster on 2012-03-28
I made a big mistake. Software-update program wanted a upgrade but a few programs where not secure. 
So i did apt-get upgrade
Big misstake, my kernels are gone.
It seems that al other software is still there but my kernels are gone.

I am running (was) latest 64 bit lubuntu.

How do I get my system up and running again?

Thx, Nico

---

### Post by LinuxFan999 on 2012-03-28
You will need to reinstall Ubuntu. Remember to back up your data.

---

### Post by azmyth on 2012-03-28
Can't it be repaired with a LiveCD, idk though?

---

### Post by wojox on 2012-03-28
> **azmyth said:**
> Can't it be repaired with a LiveCD, idk though?

LiveCD and chroot. :p

---

### Post by 1clue on 2012-03-28
> **wojox said:**
> LiveCD and chroot. :p

+1 on that.

You're about to learn a bunch more about how kernels work.

It's not really that big a deal.  If you start compiling your own kernels you'll inevitably wind up with no kernel at some point, or worse yet you'll wind up with 3 kernels none of which work completely.  I started by reinstalling everything, then when I got bored with that I figured out how to fix it.  :)


First you need a bootable Linux CD (LiveCD) and second you need a copy of the kernel you want to install.  Which can be gotten from apt-get, if you actually have enough there.

So you boot off the livecd, then mount your normal / partition and /boot, if you have a separate /boot partition.  I do, but my installation stops being standard right about the time it asks for user input so I don't really know.

Anyway, mount your normal / onto /mnt/ubuntu for example, then /boot onto /mnt/ubuntu/boot, then /mnt/ubuntu/usr etc for all your partitions.  You don't need to mount anything that isn't needed for critical Linux operations.  Also this:

mount -t proc none /mnt/ubuntu/proc
mount --rbind /dev /mnt/ubuntu/dev

That puts the special directories /proc and /dev into the proper place

Then

chroot /mnt/ubuntu /bin/bash

at which point you'll be running on your regular distro but with the LiveCD kernel.

Now, install your new kernel.

Good luck and have fun.

---

### Post by Pitmaster on 2012-03-29
Thx for the clue 1clue :p

I indeed have my computer back again. Partly that is.
I have done as you suggested. After that I did I have done apt-get install linux-generic and I had my computer back.
No network, no graphics and as I see now more things are missing.

I really made a big mistake.......

I have done: apt-get install lxdm but starting it didn't does the jop,
apt-get install xserver-xorg, no go, apt-get install nvidia* gave me hope again.....

Did I do anything wrong already again?

I miss my network icon in the corner and I miss wine.....

So, now I go and try to install both.

Thx so far, Nico

---

### Post by Pitmaster on 2012-03-29
I now have installed with synaptic "network-manager-gnome". Now I have my icon for network back next to the clock.
Something that also changed: Synaptic didn't work from menu. Menu command is synaptic-pkexec and putting this in terminal worked but from menu it didn't. After installing network-manager-gnome Synaptic worked again from menu.

Nico

---

### Post by 1clue on 2012-03-29
Here's where I start losing the ability to help.

It seems you're missing some drivers.  To me that means you're either running the wrong kernel or you didn't install a package that contains the drivers.

Frankly I've never been in this situation with Ubuntu.  Ubuntu is my "lazy" distro, where I just install it and leave the core stuff alone.  If I'm messing with this sort of thing, the past few years I've been using Gentoo.  In that case, you compile everything from source anyway, so what you're talking about doesn't seem so bad.

Each distro is a bit different on how they handle this.  The sort of drivers you're talking about are mostly built into the kernel source, which to me means they should be packaged with the kernel but for some reason they almost never are.  Commercial drivers MUST be packaged separately, but the open source ones there's no reason.

I also don't have access to my Linux box from here, so I can't log in and look around.  Won't have access for most of a day.

Here's what I would check:
[LIST=1]
[*]Is linux-generic the version of the kernel your flavor of Ubuntu uses by default?
[*]Is the 64/32 bit part correct?
[*]Is there some other kernel which has more drivers?
[*]Is there a drivers package for your kernel which is not installed?
[/LIST]

As a general rule in this scenario, you should ask yourself "What's missing?" and then try to install that thing.  Also make use of google and the forums, look for "ubuntu" and your specific hardware that doesn't work.

It may be complicated but it's probably not difficult, if that makes any sense.  It's going to be a series of simple tasks that gets you back to a working state, and doing this sort of thing a few times really tells you a lot about Linux.  If you have the time I strongly recommend that you go about fixing rather than wiping and reinstalling.

Good luck and have fun.

---

