---
title: "Want to delete Chrome (hexxeh build) + partitions. Help!"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by sammya on 2011-09-29
So basically I want to remove Hexxeh's ChromiumOS build that is dual booted alongside my Ubuntu OS. These are the steps I was going to take but would like a little guidance and to correct anything I am doing wrong. 

1). Boot Ubuntu from USB
2).  Run GParted Partition editor.
3). Delete the 3 partitions ChromiumOS is running from:

i). C-State - sda3, ext3
ii). C-Root - sda4, ext3
iii). Boot - sda2, ext4. Flag: boot

So only my linux partition will be left (linux-swap, sda1)

Here is an image to correct anything I have missed:

[IMG]http://i52.tinypic.com/263ih74.png[/IMG]

Also with the GRUB bootloader at the start..what do I have to do to update it for the changes I have made?

Cheers

---

### Post by Quackers on 2011-09-29
To make sure that Ubuntu's grub is in control of things I would suggest that you boot into Ubuntu and run ```
sudo grub-install /dev/sdX
``` where /dev/sdX is your Ubuntu drive (often /dev/sda).
You can then delete any partitions you wish that aren't Ubuntu-related. It's possibly best to do this part when booted into the Ubuntu live cd environment.
When you next boot into your normal Ubuntu installation you can run ```
sudo update-grub
``` to update your grub menu.

---

### Post by sammya on 2011-09-29
tried the first command you recommended and i get this error:

```
error: cannot stat `/dev/sdx'.

```

any ideas?

---

### Post by Quackers on 2011-09-29
You need to change /dev/sdX to the hard drive you boot from (or install Ubuntu on) such as /dev/sda or /dev/sdb, whichever it is :-)

---

### Post by hg21 on 2012-11-12
> **sammya said:**
> So basically I want to remove Hexxeh's ChromiumOS build that is dual booted alongside my Ubuntu OS. These are the steps I was going to take but would like a little guidance and to correct anything I am doing wrong. 

1). Boot Ubuntu from USB
2).  Run GParted Partition editor.
3). Delete the 3 partitions ChromiumOS is running from:

i). C-State - sda3, ext3
ii). C-Root - sda4, ext3
iii). Boot - sda2, ext4. Flag: boot

So only my linux partition will be left (linux-swap, sda1)

Here is an image to correct anything I have missed:

[IMG]http://i52.tinypic.com/263ih74.png[/IMG]

Also with the GRUB bootloader at the start..what do I have to do to update it for the changes I have made?

Cheers

From this it looks as if your main Ubuntu is on sda2 and you wouldn't want to delete that.

Did you actually get ChromiumOS working from your HDD?

---

