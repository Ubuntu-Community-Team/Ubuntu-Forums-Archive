---
title: "mce: [Hardware Error] screen pops up after clicking install and continue"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by cA6nXC8 on 2013-10-20
I currently have Windows 7 installed on my desktop (specs of computer included at the end of post), and i wanted to install ubuntu. I got Ubuntu 12.04.3 Amd 64 and burned it to a dvd ( installed fine on my laptop earlier). I inserted the disc and restarted the computer. The computer booted from the dvd and asked if i wanted to try or install ubuntu. I clicked install, it asked me if i wanted to download updates while installing and etc, well, i clicked continue and then this screen comes up:

[1.Link to image]("http://i.imgur.com/8Z4a6sh.jpg") ( if that didn't work, here's the link: [http://i.imgur.com/8Z4a6sh.jpg](http://i.imgur.com/8Z4a6sh.jpg) )

So i googled that, and found out that this could be caused by multiple different things involving hardware. I also have recently been getting blue screens of death on windows. Finding this out, i decided to remove some old RAM i threw into my pc i took from an older one. I figured that the old RAM was what could have been broken. However, once removing it. i seemed to have gotten an even longer error:

[2.Link to image]("http://i.imgur.com/pH7A6oS.jpg") ( [http://i.imgur.com/pH7A6oS.jpg](http://i.imgur.com/pH7A6oS.jpg) )

As of right now, i'm thinking that something in my pc is... broken. Thoughts on what i should do would be greatly appreciated. 

Rig Specifics: 

OS = Windows 7
MotherBoard = Gigabyte GA-Z68X-UD3-B3 LGA 1155 Intel Z68 SATA 6Gb/s USB 3.0 ATX
Cpu = Intel Core i5-2500k Sandy Bridge 3.3 ghz LGA 1155 95w BX80623152500k (OVERCLOCKED to about 4.4 ghz)
Cpu Fan = Cooler master hyper 212 plus
RAM = G.SKILL ripjaws x series 8 GB 240-pin DDR3 SDRAM 1600 F3-12800CL9D-8GBXL
GPU = Nvidia GTX 670
Sound card = Asus Xonar DG ( i think )
DVD drive = ( some dvd drive i got from an older asus pc i had 5-6 years back, still works decently )
Hard Drives = ( ^ one hard drive is a 1 TB drive taken from the same pc above, seems to work fine ) Another hard drive is a barracuda 1tb or something named like that.
PSU = Some $40-50 600 watt rosewill psu i had sitting around
Case = Antec 900 ( or it may be the twelve hundred, can't remember ) But it has a good amount of fans so heat Shouldn't be an issue.

---

### Post by heir4c on 2013-10-20
Seeing the errors, there is something wrong with the CPU. Here a link to a same error, maybe the first answer will help you further:
[http://askubuntu.com/questions/146469/kernel-panic-machine-check-processor-context-corrupt-after-install](http://askubuntu.com/questions/146469/kernel-panic-machine-check-processor-context-corrupt-after-install)

---

### Post by cA6nXC8 on 2013-10-20
Checked it out and investigated. The problem was indeed the CPU. I've had it overclocked for about 6 months now. The overclock seems to have 'worn' out the cpu a little. I found it out when doing a burn test, my desktop soon crashed after i started the test. I went in and lowered the clock ratio some. This relieved some stress on the CPU. It now seems to be doing fine. I've also successfully installed Ubuntu. Thank you for your help.

---

### Post by heir4c on 2013-10-21
No thanks, I have also learned something with searching for a answer to your problem.

---

