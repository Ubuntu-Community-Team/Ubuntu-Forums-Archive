---
title: "EMGD struggle"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by Gromke on 2015-09-20
Hi dear -buntu users.

I have an Asus 1015cx EeePC with an Intel Atom N2600 possessor, and I am struggling to get the display right.
First I had Linux Mint 13 installed. In that time everything went well, because the official driver (cedar view) was still supported. But now in newer kernels the gma500 display is no longer supported.
Recently, although already a few month ago, I  found out there is a new repository by Thopiekar that makes the display work with the EMGD driver. so I tried that in a new installation with Lubuntu 14.04 but so far I didn't manage to get it to work.
I think the main problem is that I cant get my xorg.conf file proper. I seems like it needs to be really specific.
Right now it boots without xorg.conf file in a stretched resolution. With xorg.conf file it only boots in console mode. I also tried to add different modelines, but then it would only boot with a black screen.
I'm not sure anymore if it is just the xorg.conf file or if I mis something else as well.

I followed some guide somewhere, I cant find it back right now, I followed everything precisely, but at the xorg.conf part its just like "you just make your own". Oké there are some examples but they are really complex and not like a standard xorg. With codes like xrandr -q you can find some information, but it seems like this file wants a lot more information.

edid: here is one of the guides I've followed from thopiekar himself: [https://github.com/EMGD-Community/intel-binaries-linux](https://github.com/EMGD-Community/intel-binaries-linux)

I'm just a bit lost a this point and hope there is someone with some successful experience and some good advise. Maybe again  a step by step explanation.

---

