---
title: "GParted doesn't recognize HDD - No OS installed - Can't do anything"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by y-u2untu-4 on 2015-05-09
I have following problem. I was about to install Linux on my laptop (Lenovo ThinkPad Edge E540), when I probably corrupted the whole machine.

**EDIT1**: Previous state: Win7 / elementaryOS - dual boot - perfectly working


My current state:

[LIST]
[*]No OS installed
[*]No Linux Live Distro recognizes a harddisk
[*]GParted Live doesn't recognize a harddisk either
[*]Lenovo Diagnostic tool is the only thing recognizing my harddisk
[/LIST]

I tried every way I ca imagine..

_[SIZE=3]When just trying to **boot** up, I get[/SIZE]_

```
error: no such partition.
Entering rescue mode...
grub rescue>
```

In there I tried

```
ls
```

which gives me

```
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
```

But in none of the 4, I can find a 

```
(hd0,XX)/boot
```[INDENT]_[SIZE=3]Trying **ubuntu 15.04**:[/SIZE]_

```
Error parsing PCC subspaces from PCCT
ACPI PCC probe failed
```

Then it boots up, but GParted doesn't recognize the HDD and the installation process fails, because I don't have enough space (because the harddrive isn't recognized)...

[SIZE=3]_Trying to install **Archlinux** gives me_[/SIZE]

```
No caching mode page found
Assuming drive cache: write through
```

Then starts up, but

```
fdisk -l
```

gives me only my USB stick, not the harddrive..

_[SIZE=3]Trying **CentOS** gives me[/SIZE]_

```
No caching mode page found
Assuming drive cache: write through
```

And then needs a lot time to give me 

```
Warning: Could not boot.
Warning: /dev/root does not exist

Starting Dracut Emergency Shell
```

_[SIZE=3]Trying to install **Damn Small Linux** gives me[/SIZE]_

```
VFS: Cannot open root device "" or 03:02
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on 03:02
```

[SIZE=3]_Trying **Manjaro** gives me_[/SIZE]

```
Loading /manjaro/boot/x86_64/manjaro.img failed: No such file or directory
```[/INDENT]


**EDIT2**: Lenovo Diagnostic Tool gives me

```
HGST
HTS725050A7E630
Firmware: GH2ZB550
[COLOR=#ff0000]Size: 0GB
[/COLOR]
```


Any other test I should run? Any ideas what's going on?

---

### Post by dino99 on 2015-05-09
some brands set hidden partition to customize the installation. As the Lenovo tool only can find the hdd, it might be the case here (sadly). The first thing is to go into the bios to see if the hdd is found and well identified.
[http://support.lenovo.com/us/en/documents/ht080188](http://support.lenovo.com/us/en/documents/ht080188) 
[http://support.lenovo.com/us/en/documents/migr-4yqlgr](http://support.lenovo.com/us/en/documents/migr-4yqlgr)
[http://www.laptop-repair.info/lenovo_hard_drive_problems.html](http://www.laptop-repair.info/lenovo_hard_drive_problems.html)

Last request on  [https://www.hgst.com/support](https://www.hgst.com/support)

---

### Post by y-u2untu-4 on 2015-05-09
I can see the HDD in the Boot order screen, but cannot click on it to see details.

[http://imgur.com/PeYeDhn](http://imgur.com/PeYeDhn)

---

