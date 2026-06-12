---
title: "Ubuntu wubi installation 12.04"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by ExpDisease on 2011-11-21
Hello,

I was having an installation problem which is based on guid partitioning(or whatever). I came up with a solution which is installing ubuntu with wubi. I shrinked my partition and make a partition for ubuntu which is 150gb.I installed it but some things are missing.

- No grub just windows boot loader
- Only 30 gb of hdd
- Maybe some other things that i didin't notice

So what can I do about these things

Also i have a power management and screen brightness issue. Randomly gives brightness levels every startup. But the brightness indicator is always at full. I have nvidia gt520m.

---

### Post by efflandt on 2011-11-21
Wrong forum.  12.04 is under development, so until it is released the correct forum for it is [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

PS: You might want to avoid development versions (especially wubi versions) unless you are very familiar with Linux and are willing to troubleshoot bugs. Wubi is probably the last thing they sort out after everything else is working in normal Linux file systems.

---

### Post by bcbc on 2011-11-22
There isn't a 12.04 wubi.exe yet. Are you sure you have a 12.04 wubi install? Maybe you mean 10.04 - unless of course you upgraded from 11.10.

Anyway, I believe the nvidia card is an optimus card which doesn't work under linux. So you're probably having issues with your onboard intel gpu. You can review this and see whether it applies: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

Also, you can post the output of the following command so we know what release you are on:
```
cat /etc/lsb-release
```

PS Wubi doesn't install to partition - it uses a virtual disk with a built in max size of 30GB. It's possible to increase it, but probably better to figure out how to install it direct. Usually if Wubi works, then a normal install will work too. What problem did you get when you tried to install?

---

### Post by lisati on 2011-11-22
Are you sure you're doing a Wubi install? Wubi doesn't usually put Ubuntu into its own partition, but normally uses a file/folder on the Windows partition.

---

### Post by ExpDisease on 2011-11-22
I downloaded iso of 11.10 and opened it with power iso. I don't know why, it downloaded some things. Wubi didin't make a partition. I made it for ubuntu but it only used 30gb of it. When the installation finished it restarted and at the screen there was something like this. "Preparing 12.04 for the first use" I was suprised too. I don't know what is an optimus card but it uses nvidia accelarated driver or something like that. I didin't want to install ubuntu with wubi but I had no choice. Because of the guid partitioning ubuntu installer didint recognise my windows 7. I don't want to format everything right now so i did it like this.

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"

```

---

### Post by bcbc on 2011-11-22
Well that's a pretty major bug then... you should only be able to update to 12.04 at the current time by editing your /etc/apt/sources.list file

Please can you post your wubi log file(s) here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags (press on the **#** above the edit box). You can find them in the %temp% directory (from Windows). Enter %temp% in your explorer address bar. They should be named either wubi-11.10-rev245.log (that's the one I am most interested in). If you only have a wubi-11.10-rev241.log then post that too. Thanks


PS For the a discussion on Ubuntu and Optimus, refer to this: [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by bcbc on 2011-11-22
In terms of getting Ubuntu installed properly... please download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That will help identify the issue that is preventing a normal install (although as I said before a successful wubi install usually means that a normal install will work as well).

Once that is figured out you should get off the development release.

---

