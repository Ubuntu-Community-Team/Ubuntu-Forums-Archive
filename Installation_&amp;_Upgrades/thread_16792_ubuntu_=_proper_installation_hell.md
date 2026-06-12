---
title: "ubuntu = proper installation hell"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by A_deeper_blue on 2005-02-23
this is my scenario...

I have no internet connection
because my router is messed up 50% of the time (isn't my router.. no access privileges)
or the zyxel router has trouble with dhcp under linux

I also have a wireless connection but it's based on a by the kernel unsuported atmel chipset (AT76C502a)

so I have to patch the kernel... but first I have to add a custom kernel... now here comes the problem...  for this

I have to do, correct me if I'm wrong

```

#apt-get install build-essential bin86 libncurses-dev

# apt-get install linux-tree-2.6.8.1
# cd /usr/src
# tar jxf linux-source-2.6.8.1.tar.bz2
# ln -s linux-source-2.6.8.1 linux
# cd /usr/src/linux
# cp /boot/config-2.6.8.1-3-686 .config
# make oldconfig

etc etc...

```

but for this I need internet access (right??)

okay, I can download all packages...

but then it's a huge list of dependencies
which is basicly hell if you have to switch to windows every time to find a new one

my wireless adapter works in windows xp

I guess I have to switch back to gentoo.. at least that way you can get a proper kernel from the cd... 

because I do not wish to take my pc home with me to get ubuntu with internet installed

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=A_deeper_blue]

because I do not wish to take my pc home with me to get ubuntu with internet installed[/QUOTE]

I think the Kernel source is on the cd. So is stuff you need to compile.

---

### Post by A_deeper_blue on 2005-02-23
hehehehe.... ofcourse

silly me

---

### Post by bored2k on 2005-02-23
[QUOTE=A_deeper_blue]hehehehe.... ofcourse

silly me[/QUOTE]


i have a zyxel rout.er

no probs here

---

