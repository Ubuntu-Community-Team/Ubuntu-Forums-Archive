---
title: "[SOLVED] Ideapad Y530 + Ubuntu"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2008-11-21
I have a few questions about this combination, Lenovo's Ideapad Y530 and Ubuntu, so I decided to make only one thread instead of invading the forum.

[LIST=1]
[*]After a successful install, I don't have any kind of sound, tried to test them, but nothing happens in none of the available channels.
[*]I want to know if I can install VeriFace software, if it's available for Linux.
[*]Screen get brighter when iddle and dim when active. Isn't is supposed to be the other way? It happened before marking that option and with the live CD.
[*]Wireless card not recognized from Ubuntu. Even though with lspci is seen, it's not seen anywhere else and I'm not able to connect wirelessly.
[/LIST]

Specs: 
Intel Centrino (2 Core Duo) 2.0GHz processors
3GB DDR3 RAM
Mobile Intel 4 Series Chipset Integrated Graphics Controller
Intel Corporation 82801I (ICH9 Family) HD Audio Controller

-lspci output-
 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
02:00.0 Network controller: Intel Corporation Unknown device 4237

Please help:confused:

---

### Post by arashiko28 on 2008-11-22
bump!!! 
come on! someone has to know something!

---

### Post by Benalene on 2008-12-03
I have ordered this laptop, and hope to receive it in about a week. I'll let you know what happens when I install 8.10.

---

### Post by flowerpotcat on 2008-12-04
oops...i was going to say something but it seems more helpful info were provided in another thread. sorry!

---

### Post by arashiko28 on 2008-12-07
About my initial post:
The Lenovo company hasn't announced a veriface software for linux, so I think it's going to take a while until we see something like that.
The screen problem kinda solved, but it still turns brighter when iddle, but I unmarked the dim when iddle option and lowered the the default screen brighthess when plugged and that has been a lot of help.
About the sound... well, I'm still working on it...
The internet, all you have to do is to update to 8.10, unfortunately, the wireless card was released in july and the drivers of this card are only available in kernel 2.6.26 and up.

Actually I am pretty happy with Ubuntu's working in this computer, It's lighting fast and low resources as always.:p Just a few tweaks away from perfection:p

---

### Post by Coburn Roar on 2008-12-08
I got the sound to work most of the way; however, I still haven't figured out how to mute the sub-woofer when headphones are plugged in.  This post is about Y510s but most of the volume stuff works. 
[http://ubuntuforums.org/showthread.php?p=4427198](http://ubuntuforums.org/showthread.php?p=4427198) 
Make sure to get the newest version of alsa though.  Originally, I used the version they used and it didn't work.  Also, on the volume control menu add center, surround, and LFE. Also, change the channels form 2 to 6 in options and enable IEC958.

---

### Post by Benalene on 2009-03-05
Sorry, it took much longer for me to get my laptop than first expected, and then got I busy setting things up and forgot to reply. 

I got all the sound to work, subwoofer, and headphones muting all the speakers. And instead of reposting everything that I did (and because I don't feel like messing with the formatting of this post), here is a link to the blog post that I made about it: [[COLOR="Orange"]Dolby Surround Sound[/COLOR]]("http://iheartlinux.wordpress.com/2008/12/31/dolby-surround-sound/"). Everything just works for me. I did some things differently than [[COLOR="Orange"]wyth[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6041731&postcount=146"), thus the post.

I am very happy with this laptop and linux on it. Everything seems to just work now, except suspend and hibernate. I can't seem to get that working.

---

### Post by tmy123 on 2009-03-25
Hibernate works good with tuxonice.

---

