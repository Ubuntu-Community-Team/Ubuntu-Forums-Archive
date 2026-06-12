---
title: "I’m trying to install Ubuntu on an old vista machine and it isn’t working"
date: 2022-01-28
forum: Installation &amp; Upgrades
---

### Post by rpiguy on 2022-01-28
I can go through the menus just fine but when I try to boot it, with any options it just crashes and displays “end kernel panic-not syncing 
attempted to kill init”

---

### Post by oldfred on 2022-01-28
How much RAM? You may need a lighter weight flavor.

My old laptop from 2006 bought a couple days before Vista (intentionally) used Ubuntu for years. 
But it would not install 20.04. I did install server and then added a lightweight gui.
And I was able to install Kubuntu which is more of a middle weight system.

Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by rpiguy on 2022-01-28
I’ll try this but I have 4gb of ram and also it displays the same thing on arch and that only needs 1gb

---

### Post by GhX6GZMB on 2022-01-29
I have a couple of older laptops that were born with Vista.
The BIOS has some "Vista optimizations" that you need to disable.
I also suggest that you look at Lubuntu or Xunbuntu. Ubuntu tends to be heavy on older HW, even with 4 GB.

---

### Post by rpiguy on 2022-01-31
I tried booting xbuntu I will attach a pic of the error screen

Imgur link: https://imgur.com/a/mjVk0kB

---

### Post by rpiguy on 2022-01-31
now when i tryed to boot xbuntu i enabled all of the advanced settings just for fun and it booted perfectly

---

### Post by MAFoElffen on 2022-01-31
What is the computer make/model, and what is the CPU?

---

### Post by rpiguy on 2022-01-31
It’s a old hp desktop with 4gb of ram and a core 2 duo

---

### Post by MAFoElffen on 2022-01-31
Core 2 Duo (itself) should run fine with Ubuntu 20.04.3 64bit. I have an Old (2007) MacBook that has that CPU and running that///

I would recheck the MS5sum of the ISO file.

---

### Post by GhX6GZMB on 2022-01-31
> **rpiguy said:**
> It’s a old hp desktop with 4gb of ram and a core 2 duo
Heh!
I'm running four HP 6910p laptops (2...4 GB RAM, Core 2 Duo @ 2GHz) with Lubuntu 20.04. Damn fast! Ubuntu was too heavy, they got slow.
Super stable too.

---

### Post by rpiguy on 2022-01-31
I had to enable 
acpi
noapic
nolapic
And now it works but it’s slow so I think I’m going to load xubuntu or lubuntu

---

### Post by rpiguy on 2022-01-31
I think I’m going to Use xubuntu

---

### Post by donald187 on 2022-01-31
> **rpiguy said:**
> It’s a old hp desktop with 4gb of ram and a core 2 duo

I run an Inspiron 530s with 4 GB of ram and a core 2 duo (e8600).  Ubuntu 20.04.3 runs fine.  No problems at all.

---

### Post by GhX6GZMB on 2022-01-31
> **rpiguy said:**
> I had to enable 
acpi
noapic
nolapic
And now it works but it’s slow so I think I’m going to load xubuntu or lubuntu
Great that it works! Enjoy! :)

---

