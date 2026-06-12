---
title: "Low memory instyall (48 MB RAM)"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2010-07-31
Hey everyone,

I have a very old laptop, which I want to give a sort of 'new life', as a little server (just for experimenting). However, the laptop has very little RAM and I have difficulty with the installation.

I tried using a USB stick as swap device (formatted it as swap with another computer and the used swapon to activate it), but it seems that the installation doesn't use it (instead, the kernel starts killing tasks).

So, my question is, can I use a USB stick as swap drive during the installation and if so, how?

---

### Post by davidmohammed on 2010-07-31
It may be possible with gparted - but why would you want to?

USB sticks have limited writes (100,000) which would be quickly eaten up when used as a swap.

USB sticks are very very slow (60Mb/s) vs hundreds/thousand Mb/s for standard ram.

suggest - open your wallet and spend 10 dollars or so for some very cheap ebay ram!

---

### Post by infamous-online on 2010-07-31
I don't think your system can run Ubuntu as an installation with an interface requires I believe 128 megs of memory and for an installation without it requires i think 64. Like David said, you're going to have to upgrade your memory.

---

### Post by Bachstelze on 2010-07-31
> **infamous-online said:**
> I don't think your system can run Ubuntu as an installation with an interface requires I believe 128 megs of memory and for an installation without it requires i think 64.

I've run the installer on 32.  That was with Hardy, but I don't think the installer has changed much, and even if for some stupid reason it now insists on having 64, just don't use it and do a debootstrap.

---

### Post by theozzlives on 2010-07-31
[This]("https://help.ubuntu.com/community/Installation/LowMemorySystems") may help. It about installing on low memory systems. As low as 32 MB. It won't run good, but if you're using it as a server or router, it should do.

---

### Post by Bliepo32 on 2010-07-31
> **davidmohammed said:**
> It may be possible with gparted - but why would you want to?

USB sticks have limited writes (100,000) which would be quickly eaten up when used as a swap.

USB sticks are very very slow (60Mb/s) vs hundreds/thousand Mb/s for standard ram.

suggest - open your wallet and spend 10 dollars or so for some very cheap ebay ram!

I don't want to use it as permanent swap, just for the installation

> **theozzlives said:**
> [This]("https://help.ubuntu.com/community/Installation/LowMemorySystems") may help. It about installing on low memory systems. As low as 32 MB. It won't run good, but if you're using it as a server or router, it should do.

Thanks I will have a look and see if it helps.
EDIT: I tried installing the server edition of Ubuntu and this fails, so I cannot even set-up a command line system :(

---

### Post by infamous-online on 2010-07-31
> **Bliepo32 said:**
> I don't want to use it as permanent swap, just for the installation



Thanks I will have a look and see if it helps.
EDIT: I tried installing the server edition of Ubuntu and this fails, so I cannot even set-up a command line system :(

Yea, then it looks like you just need more ram.

---

### Post by Bliepo32 on 2010-07-31
Well, if someone has a method which could work, I would love to hear it. I could install more RAM on it, but I just wanted to see if I could do something usefull with it.

---

### Post by snowpine on 2010-07-31
Ubuntu server system requirements are [well documented]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu%20Server%20%28CLI%29%20Installation"):

> Ubuntu Server (CLI) Installation

    * 300 MHz x86 processor
    * 128 MiB of system memory (RAM)
    * 1 GB of disk space
    * Graphics card and monitor capable of 640x480
    * CD-ROM drive

You need more RAM.

---

### Post by Bliepo32 on 2010-07-31
Well, the page itself also says this:
> While you can often run Ubuntu on hardware of lower (and sometimes much lower) specification using a minimal install, performance will suffer. Most users (especially those new to Ubuntu) risk frustration if they ignore these suggestions. 
For now, I will just keep trying :P

---

### Post by oldos2er on 2010-07-31
Why not use a distro made specifically for low RAM systems, like Puppy?

---

### Post by lykwydchykyn on 2010-07-31
Yeah, you want puppy, tiny core or basiclinux for that thing.  Ubuntu was just not designed for specs like that.

---

### Post by jocko on 2010-07-31
> **Bliepo32 said:**
> Well, the page itself also says this:

For now, I will just keep trying :P
Which cd do you use?
If the server cd fails, try the "normal" alternate installer and install a cli-only system (at least I think it's still possible...). As far as I know, the server installer will install more services than a simple command-line install will (like all the server apps/services which does require some ram...).
Or try the minimal installer ([look here]("https://help.ubuntu.com/community/Installation/MinimalCD")). I haven't seen any official minimal requirements in my 3 minutes of googling, but in one of the pages I found someone said it will run on as low as 32 Mb of ram.
If you think adding swap will help, why not add a swap partition to the hard drive before you try the installer? You can probably do that from some minimalist distro like puppy. But I'm not sure the text based installer on the server, alternate or minimal cd's will ever use the swap partition...

---

