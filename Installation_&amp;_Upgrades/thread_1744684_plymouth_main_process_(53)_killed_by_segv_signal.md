---
title: "plymouth main process (53) killed by segv signal?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by ibootindos on 2011-04-30
plymouth main process (53) killed by segv signal. 

and below that it reads

plymouth-splash main process (175) terminated with status 2. 

what the fudge batman?

---

### Post by dino99 on 2011-04-30
i've removed the "splash" from boot line due to such issue

otherwise: sudo dpkg-reconfigure plymouth

---

### Post by ibootindos on 2011-04-30
> **dino99 said:**
> i've removed the "splash" from boot line due to such issue

otherwise: sudo dpkg-reconfigure plymouth

yes, but how do I get to a spot where I can do that? ubuntu is not loading at all in any mode.

---

### Post by dino99 on 2011-04-30
try recovery mode then select "repair packages"

---

### Post by ibootindos on 2011-04-30
> **dino99 said:**
> try recovery mode then select "repair packages"

I get the same error message when I try to boot into recovery mode as well.

---

### Post by ibootindos on 2011-04-30
anybody? lol

---

### Post by _sge on 2011-05-08
I've had the same problem for about a week after updating from 10.10 to 11.04. Many people have had similar problems but searching hasn't really helped. Such a frustrating problem for someone new to linux :(

The problem came about (for me at least) when the 11.04 upgrade froze when trying to update grub. I did a hard reset. After that, on ever reboot I got:
```
init: plymouth main process (57) killed by SEGV signal
```

(Now, **plymouth** is apparently the splash screen that appears when Ubuntu starts up. It also apparently controls [many things.](http://jonmccune.wordpress.com/2010/07/27/plymouth-main-process-341-killed-by-segv-signal/))

I think the bug has been fixed with the latest releases since after updating all the packages, everything started working for me. You'll need a LiveCD or another linux environment to fix this problem.

I ended up fixing it by booting an old Ubuntu drive and doing the following: (Now since I 'm reciting what I did from memory, there are probably many commands you don't strictly need to do, like binding /sys, that I needed when I playing around with update-grub earlier. So if someone can chime in, it would be appreciated)
```
cd /mnt
sudo mkdir hdd
sudo mount /dev/sdX /mnt/hdd
sudo mount --bind /dev /mnt/hdd
sudo mount --bind /sys /mnt/hdd
sudo mount --bind /proc /mnt/hdd

mount --bind /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt/hdd
```

(replace /dev/sdX the device node of your Ubuntu partition.)

Now you are chroot'd in your Ubuntu partition with internet hopefully working. Then I did:

```
apt-get update
apt-get upgrade
```

(Note you may need to do a dpkg command before being able to use apt-get)

After that, I restarted and I booted from my regular HDD into the shiny new Unity desktop environment :D

Hope this helps!

---

### Post by bobsk on 2011-05-14
Thanks a lot, _sge, this worked for me!

Just some adjustments I had to make in the commands you provided:


```

cd /mnt 
sudo mkdir hdd 
sudo mount /dev/sdX /mnt/hdd 
sudo mount --bind /dev /mnt/hdd/dev 
sudo mount --bind /sys /mnt/hdd/sys 
sudo mount --bind /proc /mnt/hdd/proc  
sudo mount --bind /etc/resolv.conf /mnt/etc/resolv.conf 
sudo chroot /mnt/hdd

```[FONT=monospace]

Note: if you're "rescuing" a 64-bit system, make sure to use a 64-bit LiveCD / external environment. Otherwise chroot will be confused. And so was I when I made the mistake.
[/FONT]

---

### Post by piks on 2011-05-20
Hi friends
 I am also facing this problem when upgrading from 10.10 to 11.04 ending with erro 
plymouth main process (59) killed by SEGV signal.
So I have tried all the steps as told by _sge and bobsk , but it is also giving me problems. 

cd /mnt
sudo mkdir hdd
sudo mount /dev/sdX /mnt/hdd
sudo mount --bind /dev /mnt/hdd
sudo mount --bind /sys /mnt/hdd
sudo mount --bind /proc /mnt/hdd

upto this step it is ok working fine, but in the next step 
mount --bind /etc/resolv.conf /mnt/etc/resolv.conf 
it is giving error of 
**mount: mount point /mnt/etc/resolv.conf does not exist**

what is the problem and how can I rectify ?

regards

---

### Post by oreoferret on 2011-05-22
> **_sge said:**
> I've had the same problem for about a week after updating from 10.10 to 11.04. Many people have had similar problems but searching hasn't really helped. Such a frustrating problem for someone new to linux :(

The problem came about (for me at least) when the 11.04 upgrade froze when trying to update grub. I did a hard reset. After that, on ever reboot I got:
```
init: plymouth main process (57) killed by SEGV signal
```(Now, **plymouth** is apparently the splash screen that appears when Ubuntu starts up. It also apparently controls [many things.]("http://jonmccune.wordpress.com/2010/07/27/plymouth-main-process-341-killed-by-segv-signal/"))

I think the bug has been fixed with the latest releases since after updating all the packages, everything started working for me. You'll need a LiveCD or another linux environment to fix this problem.

I ended up fixing it by booting an old Ubuntu drive and doing the following: (Now since I 'm reciting what I did from memory, there are probably many commands you don't strictly need to do, like binding /sys, that I needed when I playing around with update-grub earlier. So if someone can chime in, it would be appreciated)
```
cd /mnt
sudo mkdir hdd
sudo mount /dev/sdX /mnt/hdd
sudo mount --bind /dev /mnt/hdd
sudo mount --bind /sys /mnt/hdd
sudo mount --bind /proc /mnt/hdd

mount --bind /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt/hdd
```(replace /dev/sdX the device node of your Ubuntu partition.)

Now you are chroot'd in your Ubuntu partition with internet hopefully working. Then I did:

```
apt-get update
apt-get upgrade
```(Note you may need to do a dpkg command before being able to use apt-get)

After that, I restarted and I booted from my regular HDD into the shiny new Unity desktop environment :D

Hope this helps!

if i'm booting off a USB do I:

1) say "try ubuntu without installing"

and what then is the mount? it isn't /dev/sdX  (which is the cdrom)

any help would be appreciated.. been down a few days.. might just wipe my entire system and install 11.04 from scratch.. which would be a huge huge loss of time

---

