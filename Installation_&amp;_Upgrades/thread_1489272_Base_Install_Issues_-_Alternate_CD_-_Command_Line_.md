---
title: "Base Install Issues - Alternate CD - Command Line System"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by kero4 on 2010-05-20
Hi,

I am trying to experiment with installing the base ubuntu system via an alternate CD and want to install the command line system only.

I am trying to create a minimal environment and know what to do once the install is done.

My problem is that 3 times in a row, about 75% through the base install, the installer keeps asking for media change and to put in an additional CD. According to installation instructions for Low Memory Systems (not the case for me but works for what i want to do) it says nothing about needing an additional CD?

Any help or comments would be appreciated.

I just want to install the command line base system so I can install the environment of my choice.

I have tried so many distro's already and would like to create my own if that makes sense :)

Thanks

Rod

---

### Post by vikjon0 on 2010-05-21
You need to use the minimal CD or the serverCD those will install a base system only.

Then you should take a look at remastersys, or other tools like that,

---

### Post by kero4 on 2010-05-21
But according to unbuntu's own directions, they suggest using the alternate CD?

If I use the server version, do I still have to use option "install command line only" or should I install normally?

I assume the server version if I install normally is pretty bare bones?

I just found the minimal CD, but again, I only want to install the base, command line system only, will it give me this option without downloading all the stuff that it doesn't have?

Sorry for being so new but what is remastersys?

I plan on after base is installed installing a light weight environment and login manager and only a few apps like a browser, cd program and video player, etc.

Eventhough my box is fairly new, I like bare bone OS's as I don't do alot other than surf the web, make a few cd's and watch some vides, that's it.

This is the command line I found on unbuntu's site, this is what I will use minus abiword - will this works?

sudo aptitude install gdm xorg xterm icewm menu mozilla-firefox abiword synaptic

or this

sudo aptitude install kdm xorg xfce4 firefox synaptic

And go from there......

---

### Post by vikjon0 on 2010-05-21
> But according to unbuntu's own directions, they suggest using the alternate CD?
Okey, never seen that. I have seen that it can be used for command line installation interface...not to install a command line system.

> If I use the server version, do I still have to use option "install command line only" or should I install normally?
I assume that this refere to the installation interface...not the end product...but I know nothing.

> I assume the server version if I install normally is pretty bare bones?
If you install server without manyally adding any server component you get a barebone system. As far as I can understand the end result is the same as if using the minimal CD. If you doubt use the minimal CD instead. (takes longer time to install since it is all downloaded from rep)

---

### Post by kero4 on 2010-05-21
Thanks,

I found this guide for ubuntu minimal desktop, what ya think, looks straight forward.

[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

I have downloaded both the mini cd and server edition, I'll give the server edition a shot first. QUESTION: 32 bit or 64 bit, I myself don't think 64 is required.

Sorry for all the questions by the way, but once I know this stuff, I can help friends of mine with older boxes install a lightweight OS without bloat. Plus it will spread the word on ubuntu, etc :)

"Okey, never seen that. I have seen that it can be used for command line  installation interface...not to install a command line system."

Maybe I am just mixing up the lingo and that's were my problems all started.

**One last question, last night I did a debian base install and installed icewm. Was fun but want to do the ubuntu version, the only problem I kept having was not being logged in as ROOT. Will I run into this problem with the ubuntu min install???**

I am excited to try all this, this weekend :)

---

