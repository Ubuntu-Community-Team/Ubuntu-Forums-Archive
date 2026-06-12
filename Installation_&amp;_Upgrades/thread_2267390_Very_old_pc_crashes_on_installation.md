---
title: "Very old pc crashes on installation"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by Ag_Liz on 2015-03-01
I have  a very old celeron with 256MB (!! ) of RAM ! I tried to install ubuntu from usb! on the istallation process after boot i choose install Ubuntu from the installetion menu of ubuntu and then on the lang choose menu, it crushes! The pointer of the mouse is responding very slow! I 'm geussing this is caused by lack of RAM memory!

Any suggestion on which version to use! I have tried the Lubuntu,  but since  was not thrilled by the UI, i 'm looking on a version more similar to ubuntu but lighter ! 
is Something like thiss out there?

---

### Post by mörgæs on 2015-03-01
You could try Bodhi Linux. Not like Ubuntu but not like Lubuntu either. 

There are videos on Youtube showing which user interface to expect.

---

### Post by v3.xx on 2015-03-01
I had LXQt working nicely on a 256M box, but sacrifices must be made.  High ram apps will run dead slow when they go to swap.  FF and Chrome are useless on 256.  Another 256M stick makes a real big difference.  1G is best.

---

### Post by tgalati4 on 2015-03-01
You can install to 256 MB of RAM, but you need to create a swap partition on the disk drive first.  512 MB or 1 GB of swap should do.  The install will take forever and the resulting desktop will be slower than Henry's Wet Patch on a cold day.  Tiny Core Linux will run well. nas4free will also run in 256 MB if you want a headless disk server.  Put in a SATA PCI card and set up a bunch of disks.

---

### Post by Ag_Liz on 2015-03-02
I went on installing  Lubuntu seems working (almost) fine . Very slow but nevertheless  faster from ubuntu. Nice advices about the Bodhi Linux , LXQt intresting seems nice *Distribution's. Will download and try them out, see if will perform better.* I also looking ways to get my hands on a ram this old, here on the local shops ( no luck so far).

---

### Post by grahammechanical on 2015-03-02
> [COLOR=#000000] I 'm geussing this is caused by lack of RAM memory![/COLOR]

A video adapter that has little of its own memory and cannot do 3D rendering and so forcing the CPU to do all the work does not help either. If the video adapter cannot support Ubuntu's user interface called Unity then Ubuntu will install using an open source video driver called llvmpipe. It does a reasonable job of approximating Unity 3D on video adapters that do not support 3D rendering. But it does appear slow even on video adapters that can do 3D rendering.

This is why we recommend Lubuntu. You might want to keep an eye on the new kid on the block - Ubuntu Mate. The 15.04 version seems to have a user interface that can easily be modified with functions from other user interfaces. It can have the Unity style app-indicators amongst other stuff. See the video

[https://ubuntu-mate.org/blog/](https://ubuntu-mate.org/blog/)

It will need that extra stick of RAM but it is a very interesting member of the Ubuntu family.

[https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

Regards.

---

### Post by mastablasta on 2015-03-03
even lubuntu installer won't work on 256MB ram

---

### Post by Ag_Liz on 2015-03-03
> even lubuntu installer won't work on 256MB ram

lubuntu Worked for me ! on 256MB RAM. A little slow but it's working!

> Ubuntu Mate
looks nice  Thanks

---

### Post by tgalati4 on 2015-03-03
As long as you have a swap partition, the system "thinks" it has more RAM.  I believe most installers now require 384 MB of RAM to install without swap.  512 MB is recommended and 1 GB is desirable.

---

