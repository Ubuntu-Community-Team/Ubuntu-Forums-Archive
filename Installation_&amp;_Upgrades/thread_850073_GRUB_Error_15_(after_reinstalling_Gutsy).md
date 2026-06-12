---
title: "GRUB: Error 15 (after reinstalling Gutsy)"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by areskz on 2008-07-05
Yesterday I have reinstalled my Gutsy. During the installation I have chosen to format my sda5 partition (**fdisk -l **output is attached), and set (as it was before) sda7 as home patition. sda6 was left as a swap. 

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06902fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         896     7194624   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         896        3507    20971520+   7  HPFS/NTFS
/dev/sda3            3508        9409    47407815    5  Extended
/dev/sda4            9410       24322   119781376    7  HPFS/NTFS
/dev/sda5            3508        6546    24410736   83  Linux
/dev/sda6            6547        6919     2996091   82  Linux swap / Solaris
/dev/sda7            6920        9409    20000893+  83  Linux

```

Everything went okay until the finishing of installation: when it started installing GRUB. It just hung. I've killed the process, started installation again, and now ticked off "Install GRUB" in options. (I just though that I already have GRUB, and I don't even change "\" partition number).

Installation went okay, and when I rebooted my laptop GRUB said to me: "**Error 15**". And there is no even a possibility to press 'e' to correct menu.lst, or something. It just hungs and the only option is to reboot by CTRL+ALT+DEL.

By the way, I have not only one OS installed now, also (along with Kubuntu) I have my pre-installed Vista, and before reinstall it also was in GRUB. Now I can't access nor Vista either Kubuntu. 

How can I, maybe, reinstall GRUB, and let him detect what OS I have installed and create menu.lst items for them? Or maybe I can somehow correct extisting version?

The only way I can access my laptop is via LiveCD.

**[COLOR="Red"]UPD[/COLOR]** Have read somewhere about Super Grub CD, downloaded it, burn to a cd and tried. Tried different options, nothing helped to boot linux. **But managed to uninstall GRUB and to boot Vista**. Now, I think, I need to install GRUB. (But if I'm trying to use Super Grub CD to boot linux I still get **Error 15**).

---

### Post by bumanie on 2008-07-05
boot ubuntu live cd; in terminal > sudo grub > root (hd0,4) > setup (hd0) > quit and reboot. Grub should work again and give the choice of both OSes. If not post back any errors. I'm surprised super grub disc couldn't boot ubuntu - may be there is more wrong than meets the eye. We'll see.

---

### Post by LinuxRocks713 on 2008-07-05
From this: 
[http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)

It says that GRUB Error 15 is most often caused by a kernel image that doesn't exist.

You choice would be to reinstall the System. If it still doesn't work after reinstalling, boot from the Ubuntu LiveCD and type:

```

grub-install /dev/sda

```

Hope that helped.

---

### Post by bumanie on 2008-07-05
linuxrocks713 is correct, I was thinking of error 17. If super grub disc won't boot ubuntu, I think the only option is to reinstall to / If sgd works look [here]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by areskz on 2008-07-05
> **bumanie said:**
> boot ubuntu live cd; in terminal     and reboot. Grub should work again and give the choice of both OSes. If not post back any errors. I'm surprised super grub disc couldn't boot ubuntu - may be there is more wrong than meets the eye. We'll see.

Done. Here's it output:
```
[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]

grub> root (hd0,4)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done. 
```
Now, when it boots, it shows me a Grub command line (like '**grub> **').Seems like I have to input something. Trying 'boot', but it told me that kernel have to loaded first.


> **LinuxRocks713 said:**
> From this: 
[http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)

It says that GRUB Error 15 is most often caused by a kernel image that doesn't exist.

You choice would be to reinstall the System. If it still doesn't work after reinstalling, boot from the Ubuntu LiveCD and type:

```

grub-install /dev/sda

```

Hope that helped.

Have tried it just now. The result is:
```
Could not find device for /boot: Not found or not a block device.
```
When I attempted to mount /dev/sda somewhere (tried /mnt/), the result was:
```
mount: /dev/sda already mounted or /mnt/ busy
```
That's it =(

Hope that you guys can help me etering some info in GRUB command line so I could boot some OS.

---

### Post by LinuxRocks713 on 2008-07-05
> **areskz said:**
> 
<snip>
Have tried it just now. The result is:
```
Could not find device for /boot: Not found or not a block device.
```
<snip>

Reinstall Ubuntu; Your current installation is missing a /boot directory.

---

### Post by areskz on 2008-07-05
Thank you, guys. Seems like I have a "bad" distro DVD (not only the problems with installing told me about that, I even can't launch a live cd now), so now I will spend couple of days downloading fresh one (Hardy). I hope reinstalling will help me :)

---

### Post by areskz on 2008-07-07
Reinstalling solved the problem. Thank you guys.

---

