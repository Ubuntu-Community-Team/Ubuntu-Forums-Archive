---
title: "Screen goes black and dies when x is about to start."
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by stiankarlsen on 2007-02-21
Im on an HP Pavilion dv6000, trying to install ubuntu 6.10

When i insert and boot off of the livecd, the screen goes black just as X is about to start. (No virtal terminals are working/responding either? (alt+ctrl+Fx)).

I then booted the livecd again, but this time pressed F4-VGA, and set the screen res. to 1024x768. 32bit. And this time X started without issues, it even set itself to 1280x800 screen resolution, which is optimal for my screen (not 1024 that i configured it to during boot).

I managed to install the OS to disk, however when i try booting the OS off the disk, i get the same problem i had to begin with - the screen goes black and dies completely.

I've also compared xorg.conf from the hd with the one on the live cd, they are both identical.

Anybody have any suggestions on what might be wrong?

hardware: amd turion 64 mobile 2ghz, 1gb ddr2 ram, geforce 7200(if im not completely mistaken)


Sincerely, Stian.

---

### Post by teaker1s on 2007-02-21
I'm having on going bugs with my dv6000 and nvidia 6150go
I imagine xserver is using the "nv" driver,there is a beta nvidia driver.
Also I don't know if your card will like it but my grapics will also run on "vesa" driver. to reconfigure xserver
boot recovery and ```
sudo dpkg-reconfigure xserver-xorg
```

I also started a dv6000 page in wiki here which has grown in tips
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by stiankarlsen on 2007-02-21
problem is i dont have terminal to reconfigure x in :(

edit: oh, boot recovery.. i can try that, thanks :)


edit2: no go. It just hangs during the boot in recovery mode

---

### Post by teaker1s on 2007-02-21
I've had fun with a dv6116eu.
I had nightmares with dapper and edgy
-feisty and latest bios sorts out 99% of the problems for me- only one I'm having an issue with is shutdown crashes xserver/kernel which I'm hoping latest xorg in pipeline will cure.

I wonder whether you try adding any of the following to the boot perams would alter it

```
NOAPIC NOAPCI NOSMP
```

---

### Post by stiankarlsen on 2007-02-21
I'll give those boot perams a shot, and get back to you. Thanks

---

### Post by teaker1s on 2007-03-03
failing that debian etch , NOAPIC and beta nvidia drivers cured mine

---

