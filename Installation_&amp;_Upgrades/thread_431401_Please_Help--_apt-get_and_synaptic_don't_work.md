---
title: "Please Help-- apt-get and synaptic don't work"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by advojess on 2007-05-03
Hi,  I'm having trouble with my apt-get and synaptic, I can't update anything anymore. :confused:  Furthermore, I have no idea what messed it up or where to turn.  I've tried 3 different sources.list files.  Apt-get usually hangs part-way thru trying to update.  I have full web access otherwise, IM works, etc...  I rebooted my firewall (IPcop) and my computer more than once.

I'm using Feisty 7.04 i386 on an AMD Turion 64 mobile.   I hope this is an easy fix because I've been searching and trying things for like a week now.  But at least, if someone could give me a clue where to look...

Here's my current minimalist sources.list...
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```Here's what I get from apt-get update...
```
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Err http://us.archive.ubuntu.com feisty Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Err http://security.ubuntu.com feisty-security Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Err http://us.archive.ubuntu.com feisty/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Err http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Err http://security.ubuntu.com feisty-security/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Err http://security.ubuntu.com feisty-security/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Err http://us.archive.ubuntu.com feisty-updates Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Err http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Err http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Packages
Get:4 http://us.archive.ubuntu.com feisty/restricted Packages [7628B]
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Get:5 http://us.archive.ubuntu.com feisty-updates/main Packages [6509B]
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Get:6 http://us.archive.ubuntu.com feisty-updates/restricted Packages [14B]
Ign http://us.archive.ubuntu.com feisty-updates/restricted Packages
Get:7 http://us.archive.ubuntu.com feisty-updates/universe Packages [14B]
Ign http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Get:8 http://us.archive.ubuntu.com feisty/main Packages [1307kB]
Err http://us.archive.ubuntu.com feisty/main Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:9 http://us.archive.ubuntu.com feisty/restricted Packages [7866B]
Err http://us.archive.ubuntu.com feisty/restricted Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:10 http://us.archive.ubuntu.com feisty/universe Packages [4912kB]
Err http://us.archive.ubuntu.com feisty/universe Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:11 http://us.archive.ubuntu.com feisty/multiverse Packages [193kB]
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:12 http://us.archive.ubuntu.com feisty-updates/main Packages [6468B]
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:13 http://us.archive.ubuntu.com feisty-updates/restricted Packages [20B]
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:14 http://us.archive.ubuntu.com feisty-updates/universe Packages [20B]
Fetched 20B in 3s (6B/s)
Reading package lists...
```I'm suspecting my problems are something not directly related to apt-get or synaptic but I could be wrong.  Hopefully someone here can give me a clue.  Thanks!

-~-Jesse

---

### Post by akudewan on 2007-05-03
There is a bug reported with a similar problem: [https://bugs.launchpad.net/ubuntu/+source/gmediaserver/+bug/107739](https://bugs.launchpad.net/ubuntu/+source/gmediaserver/+bug/107739)

---

### Post by zvacet on 2007-05-03
Disable your firewall and try again.Or maybe you will like to try this list( I don´t think list is a problem,but anyway)

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by advojess on 2007-05-03
> **akudewan said:**
> There is a bug reported with a similar problem: [https://bugs.launchpad.net/ubuntu/+source/gmediaserver/+bug/107739](https://bugs.launchpad.net/ubuntu/+source/gmediaserver/+bug/107739)

Thanks, but although it may be somehow related those error messages look a lot different than what I am seeing.  My problem is not yet related to Update Manager or individual packages.

---

### Post by advojess on 2007-05-03
> **zvacet said:**
> Disable your firewall and try again.Or maybe you will like to try this list( I don´t think list is a problem,but anyway)

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Well, I used to have a firewall, but I'm pretty sure I don't any more.  I completely removed it from my system (software firewall that is).  And my hardware firewall has not been changed since everything was working fine.

I also tried changing all the references to http:// to ftp:// in the sources.list but that didn't work either.  Why can I browse but not update or upgrade or anything like that?

---

### Post by akudewan on 2007-05-03
You could try removing the *us.* from your sources.list. Mine looks like this: ```
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
```

But you say you've already tried 3 different sources.list, so I really don't know...

---

### Post by advojess on 2007-05-03
> **zvacet said:**
> Disable your firewall and try again.Or maybe you will like to try this list( I don´t think list is a problem,but anyway)

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Actually, that is one of the lists I tried...

---

### Post by advojess on 2007-05-03
> **akudewan said:**
> You could try removing the *us.* from your sources.list. Mine looks like this: ```
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
```

But you say you've already tried 3 different sources.list, so I really don't know...

Yes, I've had mine like that already too.  Thanks anyway...

BUMP...

---

### Post by advojess on 2007-05-04
Anybody have a clue?

BUMP........

---

### Post by advojess on 2007-05-07
Please anyone?..... BUMP

---

### Post by Nythain on 2007-05-07
is it consistent or inconsistent... the servers tend to get hit hard at peak times, especially soon after a new release when people have to grab 150+ updates at a time

i used to get that error randomly, i would wait a minute or two, and it would work again

---

### Post by myrandomstuff on 2007-05-08
I am getting the same from that apt. I just installed ies4Linux and had to add the line for their repsoitories and it worked but I am trying to install HPLIP and cannot access  us.archive.ubuntu.com (91.189.89.8). So I don't think it is a firewall issue because I could get to another repository. Not much help, but at least you know it isn't just you and other repositories do work

---

### Post by advojess on 2007-05-11
> **Nythain said:**
> is it consistent or inconsistent... the servers tend to get hit hard at peak times, especially soon after a new release when people have to grab 150+ updates at a time
 
i used to get that error randomly, i would wait a minute or two, and it would work again
 
it's consistent, any time day or night, for several weeks now.  i'm just too stubborn to re-install when i think i should be able to figure it out.  plus i don't feel like setting everything up again, after getting pretty much all the hardware on my laptop working...

---

### Post by advojess on 2007-05-12
Well, well, I have got this issue resolved, at least partly...

I tried something I had tried before unsuccessfully, which is to edit the sources.list and change all the **http:// **to **ftp:// **for the repositories.

One thing that seems kind of strange is that after updating it doesn't say I need to upgrade anything, strange since I couldn't update for several weeks... But maybe nothing was updated.

I don't really like the fact that I didn't really fix it, but I think it must be a bug...
Also all the translation-en-US files are being ignored, I guess that doesn't matter?

I tried installing a couple things and it works fine... so :) :) :) :KS

---

