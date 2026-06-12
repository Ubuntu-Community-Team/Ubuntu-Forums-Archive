---
title: "Unable to boot computer 10.04.4 Lucid USB Flash drive"
date: 2019-01-22
forum: Installation &amp; Upgrades
---

### Post by kman-devnull on 2019-01-22
For one of my projects I need to use Ubuntu 10.04.4 x86 installation.

I have created a boot-up USB using the 'start-up disk creator'(from ubuntu 16.04 LTS) from iso downloaded from [http://old-releases.ubuntu.com/releases/lucid/](http://old-releases.ubuntu.com/releases/lucid/)

When I plug in this USB into the computer I wish to install, then re-order the boot order with this USB Flash Drive as first, (irrespective of whether it's a new or old computer) it says insert valid boot media/ insert boot media etc.

I have tried on several different computers (32 bit/ 64 bit), and also with different iso's downloaded i.e. with both x86-64/x86, but the USB Flash drive doesn't get read at all, the BIOS just says, -- 'please insert boot media'.

The contents of the USB looks like this:
```
[Ubuntu 10.04.4 LTS i386]# ls

autorun.inf  dists    isolinux    pics  preseed             ubuntu
casper       install  md5sum.txt  pool  README.diskdefines  wubi.exe


```

Please SUGGEST -- what's wrong?? (very urgent)

thanks.

---

### Post by jamesbrown2 on 2019-01-22
You said that you tried it on several different computers, but you never said specifically what resulted.  You tried this specific boot USB?  Did it work?

I would recommend Etcher:  [https://www.balena.io/etcher/](https://www.balena.io/etcher/) for creating your USB boot media.  

If that does not work, after you test it using two DIFFERENT USB drives, please answer:  Which exact computer are you trying to boot, by the way?

---

### Post by Topsiho on 2019-01-23
I think you **are** aware that Ubuntu 10.04.4 is a very old version of Ubuntu, nearly 9 years old. But just to be sure I want to tell you that Ubuntu 10.04 (Lucid) is not supported anymore, so **using it connected to the internet is risky**: no security or other updates are available.
This does not explain, as far as I know, why you can't install it now on any of your computers, 32 or 64 bits.
Are you sure you can't use Ubuntu 16.04 LTS (support until 2021) or Ubuntu 18.04 LTS (support until 2023) ?
(don't use Ubuntu 18.10 or so, the not LTS-versions are only supported for 9 months)

Topsiho

---

### Post by mastablasta on 2019-01-24
1. check the md5sum that the download is OK.
2. check the USB drive to make sure it is OK.

if all is good here are possible workarrounds or solutions:
1. some old bios can not boot from USB, you can use PLOP to bypass that limitation and just boot from CD.
2. burn the OS image on CD and use a CD to boot the OS
3. use a virtualisation on a modern computer to load the old OS. for example virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
if you are low on RAM, you can use something with a lighter desktop such as Xubuntu or Lubuntu 10.04.

---

### Post by monkeybrain20122 on 2019-01-24
Maybe you can explain to us a little bit what is the nature of your project and why do you think you must have Ubuntu 10.04 so perhaps someone can give you better advice than to use an unsupported, almost 9 year old dead OS to do your project? If your project can only work on something that old maybe it is time to go back to the drawing board (how do you maintain it??)

---

