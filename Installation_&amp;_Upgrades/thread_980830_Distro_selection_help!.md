---
title: "Distro selection help!"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by dogscoff on 2008-11-13
I'm looking to install Linux on an older PC about 7 years old, probably. It's a pretty unremarkable PC-World type Desktop, probably on-board graphics card, with something like 280 meg of memory. Sadly I can't be more precise right now because it belongs to a friend[*], so I don't have access to it right now. 

The minimum specs for Ubuntu seem to be a little vague, but I get the feeling that this machine is pretty much on the borderline. It ran a Hardy live CD, albeit agonisingly slowly, so I don't think there are any other hardware deficiencies. I realise I'm not providing much in the way of specs here, but does anyone else run Ubuntu happily under this kind of spec? If I install to the HD, how much of a speedup can I hope for compared to the Live CD?

My first thought was to go for Xubuntu, since I understood it to be somewhat lighter in resource usage, and I ran it on my old laptop for a while. However I read in another thread that Xubuntu is almost as resource-hungry as normal Ubunutu. Is this true? If there's little or no difference in this regard then I might just as well go for gnome.

If Xubuntu really is as hungry as regular gnomebuntu, does anyone know of any other lightweight ubuntu derivative? I looked into Linux Mint and it's XFCE derivative, and they look very nice, but I couldn't really see what it offered over plain Ubuntu.

Or is Ubuntu too ambitious with this PC? Should I go for something lighter still, like Puppy? Trouble is, my friend [non-geek] wants a no-hassle PC that just works, and I [semi-geek] don't want to be going to her house every other week tinkering when it turns out I haven't configured something quite right. For this reason I'd rather use *buntu, since I am familiar with it and therefore less likely to make a mistake. 

Finally: Assuming I can decide up on and install an OS, will OOo, pidgin and firefox be OK on these specs? These are the things she will use the PC for most of the time. 



Help...?



[*] Before deciding to go the linux route, I made an effort to fix her Windows install. Without doubt the worst case of Windows Rot I've ever seen. I spent an entire evening getting rid of unwanted programs and data, running virus/ malware scans, cleaning the registry, defragging, all of that - and within a week it was as bad as ever. Ugh.

---

### Post by alwez_loner on 2008-11-13
Well as it says [here]("https://help.ubuntu.com/community/Installation/SystemRequirements#Low-spec%20computers%20(Xubuntu)")it seems that kubuntu might work for your low specs PC.

Check it out and see.

---

### Post by sandy8925 on 2008-11-13
Running from the livecd is always slower than running from an installed version on the ahrd disk. And you probably didn't have a swap partition which might have made it more slower. Anyway I don't think that those specs are a limitation 'cause I have a pretty old comp too and it has only 256 MB RAM and it runs hardy pretty well.Just use wubi to install it and if it doesn't work out you can always uninstall it.

By the way my comp. specs are :

Pentium 4 1.8 Ghz
256 MB DDR RAM
Nvidia Geforce 6600 GT (AGP)
Two 40 GB hard disks (PATA or IDE - I'm not sure)

---

### Post by sandy8925 on 2008-11-13
Oh and you could also try xubuntu which requires lower specs.You might also try dsl which is just 50 MB and is gonna be a lot faster since it can load into and run completely from RAM.

---

### Post by binbash on 2008-11-13
Try xubuntu, if it is slow you should try archlinux or gentoo if you manage to install.

---

### Post by mikjp on 2008-11-13
Forget both Ubuntu and Xubuntu. My suggestions are:

* Debian with IceWM or Openbox or some other lightweight window manager
* Zenwalk
* Vector Linux

I use Vector Linux on a P1000 with 256 Mb RAM. Runs fine even with KDE though I like both Fluxbox and WindowMaker. Xubuntu was almost unusable even after turning off all kinds of services. Vector 5.9.1 is usable out of the box, it even plays YouTube videos :-)

You could also read the blog posting mentioned in my signature.

Greetings,

mikko

---

### Post by dogscoff on 2008-11-14
Thanks for the replies everyone.

Sandy8925: Thanks, I like the wubi idea. I forget that you can dual-boot. Do you think your machine would still be usable if you had on-board graphics rather than a dedicated card with its own memory? I'm tempted to spend £5 on an old graphics card on ebay., just to reduce the load on the processor and memory. I just wish I had more information about this PC, so I knew what it has already, and what bus it needs.

I had already considered XUbuntu, but I had read that it is subject to "gnome-creep", and as a result it is now almost as resource intensive as full ubuntu. But maybe that's not true, I don't know.

I have an old DSL CD around somewhere, but it probably a bit too striped down for my purposes. After all, this machine can run XP, so you'd expect it to run an equivalent linux distro.

mikjp: Thanks for the links. I've looked at your them, zenwalk and vector look nice. It's pretty scary moving away from *buntu though. If it was my own PC then I'd say fine, I can play with new and unfamiliar distros and learn about them and if I can't get it working right then it doesn't matter. However this is someone else's PC. How much tinkering am I likely to need with Vector, for example? What repository does it use, is it comprehensive? Will I have to be installing and compiling stuff from the command line? Like I say, the very last thing I want is a phone call saying "this doesn't work for me" because I neglected to configure something correctly. Not so much because I mind going over there, but because it gives the user the wrong impression of Linux.

I'm not sure what to do. Maybe I should take the PC away and spend a few days with it, rather than trying to get it all done in an evening.

---

### Post by razy60 on 2008-11-14
I know its not Ubuntu, but i have an old 10years old at least(128 ram, 2 7gig hdd's, p2  processor) that i put pclinuxos on when i first tried a Linux distro, works very well and is very windozy so no major shocks when using it. A si said its not Ubuntu but it is Linux.

---

### Post by heyho on 2008-11-14
I've never found xubuntu to run any slicker than ubuntu whenever I've used it, so I tend not to bother now.  I have tried fluxbuntu (this may be dead now), and dsl, but the only small install I've been really impressed with was puppy - I put this on my parent's old desktop, and I've not looked back.

Well worth a try - it boots in about 45 seconds!

---

### Post by snowpine on 2008-11-14
Crunchbang is a really nice Ubuntu 8.04 derivative using Openbox as the windows manager. It includes all the audio and video codecs as well as a nice set of applications for surfing/youtube/multimedia/etc. I find it to be a bigger improvement over Ubuntu than a switch to Xubuntu, if that makes sense. 

One thing I've been playing around with lately, might be an option if you have a little extra time to set everything up, is Debian Lenny plus the LXDE desktop environment. Out of all the super-lightweight options I've come across, LXDE is closest to a "traditional" desktop environment, and therefore more familiar for someone like your friend.

---

### Post by mikjp on 2008-11-14
> **dogscoff said:**
>  How much tinkering am I likely to need with Vector, for example? What repository does it use, is it comprehensive? Will I have to be installing and compiling stuff from the command line? 

The default installation is pretty good in Vector. It uses its own package manager and the package selection is rather limited, but it should be fine for normal uses (browsing the web, word processing, email etc). I have not compiled anything from the command line except EDE desktop environment, but I suppose 99.9 % of Linux users are not interested in it anyway.

If you really want to have a big repository and a lightweight distro with easy package management, take Debian.

Greetings,

Mikko

---

### Post by RedSquirrel on 2008-11-15
If you want to stick with Ubuntu, you could try a minimal installation.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

For ease of use, you might try installing xfce4 on it.

```
sudo apt-get install xfce4
```

---

