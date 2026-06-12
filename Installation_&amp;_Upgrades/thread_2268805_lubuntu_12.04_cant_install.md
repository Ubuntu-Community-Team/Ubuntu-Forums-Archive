---
title: "lubuntu 12.04 cant install"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by shaolinchamp on 2015-03-11
I have a live usb of lubuntu, boots to the desktop fine, but when I try to install from the desktop it will load for a while and then display step one which is language selection. After I click continue, it will seem like it'll continue but then close the window.  

Really not sure what to make of it, it does have only 256 ram which I dont think would affect it.  Any input is appreciated

---

### Post by kerry_s on 2015-03-11
before you start the installer use gparted to create the partitions & swap, start the swap with "sudo swapon" that should give you the extra memory needed.
you might want to consider going even lighter than lubuntu.i hear puppy can handle memory that low.

---

### Post by shaolinchamp on 2015-03-11
Well ive seen that lubuntu can handle very old machines quite well, but ill look into puppy linux

And I would make an ext4 and swap partition right?

---

### Post by Elfy on 2015-03-11
You know that Lubuntu 12.04 is well out of support now?

---

### Post by sudodus on 2015-03-11
> **kerry_s said:**
> before you start the installer use gparted to create the partitions & swap, start the swap with "sudo swapon" that should give you the extra memory needed.
you might want to consider going even lighter than lubuntu.i hear puppy can handle memory that low.
+1, Lubuntu really needs at least the double RAM, 512 MB to be useful (with a reasonable speed and stability using standard programs for browsing the internet. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]
> **shaolinchamp said:**
> Well ive seen that lubuntu can handle very old machines quite well, but ill look into puppy linux

And I would make an ext4 and swap partition right?

Try Wary Puppy and TahrPup, two versions of Puppy Linux. You can also try also Tiny Core and ToriOS. But it would be worthwhile to look for [second hand] RAM to plug into the computer to get 512 MB RAM or more. Then Lubuntu 14.04.2 might be a good choice. It is supported until April 2017.

> **Elfy said:**
> You know that Lubuntu 12.04 is well out of support now?
+1

Light-weight alternatives, based on Ubuntu 12.04 LTS are Bento, Bodhi and LXLE, but they all want at least 512 MB RAM. Those re-spins are supported until April 2017.

---

### Post by shaolinchamp on 2015-03-11
This is more of a backup pc im using for time being, so is that why the install is failing because of the lack of ram? Im sure it will run fine on this box once its installed

I tried the swapon and it said the device was busy

---

### Post by sudodus on 2015-03-11
Lubuntu needs more RAM unless you try more or less advanced methods. See also this link.

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

Maybe the operating system has already started to use the swap partition. What does

```
swapon -s
```

say?

And please post the output of the following commands

```
sudo parted -l
df
```

---

### Post by shaolinchamp on 2015-03-11
Ok it actually already was using the swap partition as I see with the -s command, however the used amount is 0 and the priority is -1. Seems like it would rather use zram

---

### Post by sudodus on 2015-03-11
Yes, until zRAM is full. Then it would use the swap partition (and be very sloooooooooooooooooooooooooooow).

---

### Post by kerry_s on 2015-03-11
okay if swaps working that's good, it maybe slow but it will get there. with swap it is possible to install something like lubuntu, but like i said i wouldn't recommend.
i did do a install of elementary os luna(based on ubuntu 12.04lts) on 256mb, of course the pc had a fairly decent graphics card i think it was 64mb of memory, & we used a sdcard for the drive, so no moving parts. disabled the animations & shadows with elementary tweak, it was a pretty good runner.

might want to check out elementary os it's prettier than most.
[http://elementary.io/#](http://elementary.io/#)

---

