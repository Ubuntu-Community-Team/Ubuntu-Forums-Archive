---
title: "Installing a newwer version"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by awacs on 2010-05-25
To make a long story short, Karmic comes with HylaFax 6.0.3-2ubuntu1, and I really want 6.0.3-5.1ubuntu1, that comes with Lucid. I don't want to upgrade Karmic right now, but I want the newer Hylafax. How do I do this? 

I tried downloading hylafax-server_6.0.3-5.1ubuntu1_i386.deb, and running apt-get install on the .deb, but it told me 
"E: Couldn't find package hylafax-server_6.0.3-5.1ubuntu1_i386.deb"

So, how do I do this?

Thanks!

---

### Post by awacs on 2010-05-25
I tried adding 
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main universe
to my /etc/apt/sources.list, with the result that apt-get update && apt-get upgrade wanted to upgrade 572 packages. I *didn't* want to do this. 

So, I tried
# apt-get install hylafax-server

which was a little better (31 upgrades, 25 new), but it gave me a "This should NOT be done unless you know exactly what you are doing!" prompt about removing 
hostname upstart (due to hostname) util-linux

I *don't* know what I am doing. So I hit abort.

What *should* I be doing?

---

### Post by awacs on 2010-05-25
I tried dpkg -i /path/to/new/hylafax/, which barfed on:

hylafax-server depends on libc6 (>= 2.11~20100104-0ubuntu2); however: Version of libc6 on system is 2.10.1-0ubuntu16.

Should I download and upgrade libc6? To what version? How many things will *that* break? I'm confused.

---

