---
title: "ubuntu 1804 upgrade messed up 3rd party boot manager"
date: 2019-07-18
forum: Installation &amp; Upgrades
---

### Post by bdubawoop on 2019-07-18
Thinkpad with win10 on sda2, ubuntu 18.04 on sda6, debian9 on sda8.

Yesterday I upgraded ubuntu from 16.04 to 18.04 & it looked ok.

today I find I can't boot debian9 with my long time boot manager (terabyte bootit baremetal). I just get a blinking cursor or the computer reboots!

Debian will boot from the ubuntu boot menu & both win10 & ubuntu boot from the terabyte boot manager.

I did send a query to terabyte since it boots from ubuntu but not the boot manager but thought I'd see if anyone on the forum has seen something similar.

---

### Post by oldfred on 2019-07-18
Not familiar with that boot loader.
Not even sure if Boot-Repair will see it. Just run report, obviously do not run any repairs with Boot-Repair as that will install grub.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by bdubawoop on 2019-07-18
Thanks for the response but had trouble understanding it as not familiar with boot-repair program.

In any case I got it back to normal by booting to debian (thru the ubuntu boot menu) & then reinstalling grub in the debian partition per terabytes instructions on how to reinstall grub.

Not good that the upgrade process from 16 to 18 trashed my debian boot info & yet it didn't touch terabytes boot program, maybe a bug?

I see boot-repair can be installed in ubuntu, I'll probably do that & see what it looks like.

I'm now leery of upgrading on my desktop as I've got 2 flavors of Debian + Mint on it.

---

### Post by oldfred on 2019-07-18
It sounds like your boot loader uses a Windows type boot loader to load more code in the PBR - partition boot sector.
I used to install the old grub legacy that way and use a grub partition to boot each install with its grub in the PBR of its partition.
But grub2 does not recommend installing it to a PBR as it is forced to use unreliable blocklists.

---

### Post by bdubawoop on 2019-07-20
I decided to risk it & upgrade to 18.04 on my backup desktop.

It went smoothly & all the other systems on it (more than the thinkpad) booted ok.

I guess it just didn't like the way the thinkpad was set up, tho it is similar to the desktop (same boot manager, etc).
.

---

### Post by scriber on 2019-07-21
> **bdubawoop said:**
> Not good that the upgrade process from 16 to 18 trashed my debian boot info & yet it didn't touch terabytes boot program, maybe a bug?

I would say that's good that it didn't touch Boot-It, as it shouldn't. ( I've used it for years)

When I upgraded from 16.04 to 18 I backed up all my important data and then did a clean install.

I've never had too much success upgrading on top of another version.

---

### Post by bdubawoop on 2019-07-21
I spoke a little too soon

it appears the ubuntu upgrade did affect the debians that are on the same drive. This time it was only a 2 minute delay about "a start job running...". A little googling shows it may be related to my 2 swap files (1 on ubuntu's drive, 1 on another hard drive). After the delay it boots normally though.

debian10-buster, which is on a separate drive boots normally.

---

### Post by oldfred on 2019-07-21
I have two swap partitions, but with Ubuntu now say not to use swap when installing, so I get swap file.

One of my test installs reformatted swap and then I had issues booting my main working install which happened to mount that swap. I had commented out the other drive's swap.

Check if UUID of swap matches UUID in fstab.
cat /etc/fstab
lsblk -f

---

### Post by bdubawoop on 2019-07-21
thanks oldfred, i'll try it.

sounds similar to what i found googling.

---

### Post by bdubawoop on 2019-07-22
it was the wrong swap uuid's in fstab.

found by comparing them with blkid output.

ubuntu evidently changed the swap uuid's for any debian partitions on the same drive. I have debian10 on another drive & that wasn't touched.

still don't know why it made debian unbootable on my thinkpad until I re-installed grub2, diff hardware tho--and only 1 hard drive.

reinstalling grub on the desktop had no effect.

---

