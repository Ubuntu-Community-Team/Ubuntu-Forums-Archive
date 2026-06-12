---
title: "Installing Ubuntu without previous operating system"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Elljl on 2010-01-26
I am building a computer using the following parts:

GB Patriot Gamer Series DDR2/800 RAM
AMD Athlon II X4 620 processor
500 GB hard drive
Gigabyte GA-MA74GM-S2 revision 1.x motherboard
Sapphire Vapor-X ATI Radeon HD 5750 video card

Will Ubuntu work on this? And can I use the ISO image, ubuntu-9.10-desktop-i386.iso? Or do I have to download another, not labeled i386, but something different?Any other spec needed can be provided.

---

### Post by earthpigg on 2010-01-26
this website is the first-stop-shop to find out if something is compatible:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

your video card isn't listed, unfortunately, so i did a bit of googling.

[this]("http://www.phoronix.com/scan.php?page=article&item=amd_juniper&num=4") google result says it's possible.


video cards and wireless are generally the most problematic. i checked your video card for you. think you can handle the rest? :D

usually, its a good idea to consult the hardware compatibility list ***before*** purchasing hardware. i personally do not purchase anything not listed there.

you can use the i386 iso, but the 64-bit version would probably perform a bit better. not a big deal, though. however, if you intend to have more than ~3.5gb of ram, then you should absolutely go for the 64bit.

---

### Post by Elljl on 2010-01-26
Thanks for the fast reply and searching.
I guess one good thing is I'm probably going to install any wireless cards. I'm probably going to use a broadband over power line ethernet connection, which I suspect should work with Ubuntu. It shouldn't need any drivers or anything since it's just an ethernet connection, right?:-s So since I'm going to use 4GB ram, I should use the 64-bit version? Where would I find that?

---

### Post by earthpigg on 2010-01-26
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) for 64 bit... click on 'alternative download options' below the big button.

> It shouldn't need any drivers or anything since it's just an ethernet connection, right?

***everything*** needs drivers. the primary difference between linux and windows is that linux attempts to include them in the kernel, which is why such a rediculous amount of hardware will work out-of-the-box without having to put an install cd in or hunt for them on the internet.

but yes, there is a 99.999999% chance that connecting to the net via ethernet will work out of the box.

> I guess one good thing is I'm probably going to install any wireless cards. 

if you ever decide to, do what i do: check the hardware compatibility list, and only purchase one that works out of the box with ubuntu.

---

### Post by mr clark25 on 2010-01-26
might go for some faster RAM, to. what you have should work, but at a low speed. i would recommend a lot more than 800mhz. i would go for something like 1066mhz.

EDIT: looks like i should have done the research before i posted. gigabyte's site said that it can only handle 800mhz.
you will still get plenty of speed with 800mhz.


do you plan to overclock at all?

---

### Post by earthpigg on 2010-01-26
i agree with the poster above me. if you haven't made the purchase yet, consider maybe getting only 2gb of RAM, but getting *faster* RAM (and a motherboard that can support it)?

a chain is only as strong as it's weakest link and whatnot.

2gb is a healthy amount for desktop linux and linux gaming use.

---

### Post by Elljl on 2010-01-27
I'm not going to be doing any overclocking simply because I don't know how to. And thanks, earthpig, for the compatibility site. I'm completely reviewing my order now. The link for the 32-bit version, it isn't bit torrent, is it? Because I have no bit torrent software. And my RAM, it should run good enough with 2GB?

---

### Post by efflandt on 2010-01-27
The **Alternative download options...** link opens up radio buttons to select 32 or 64 bit to download directly once you select a location from that list.

2 GB should be plenty for now.  Note that I am currently using less than 600 MB, the rest is buffered/cached data:

```
             total       used       free     shared    buffers     cached
Mem:       2058060    1876920     181140          0     135120    1151624
-/+ buffers/cache:     590176    1467884
Swap:      2290640          0    2290640
```

---

### Post by 73ckn797 on 2010-01-27
If you have over 3 gig of RAM and install 32 bit the install will likely use a PAE enabled kernel. That is what I discovered on one install with 6 gig. If not you can install it after the initial installation by finding it in the Synaptic Package Manager. My wifes computer has 4 gig RAM and was only showing 2.9 but jumped to 3.9 after installing the PAE kernel.

I use a Trendnet wireless network card on 2 computers. The card worked but was showing a very weak signal even 8 feet from the router. I installed the Windows XP driver using "ndisgtk", again, found in Synaptic.

64 bit will be able to read large RAM amounts normally. My computer is a 64 bit board but I use 32 bit Ubuntu and between 32 & 64 I find very little difference. There are a few programs not available in 64 bit for my needs. Others may/will have different results.

---

