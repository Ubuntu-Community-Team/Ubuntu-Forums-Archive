---
title: "Black Screen + Blinking Cursor From Burned DVD (MAC)"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by v4d3rr00t on 2013-04-11
Hi forums. First post, sorry it had to start out with a problem. I have Ubuntu running fine on my desktop and a few other computers, but my Mac doesn't seem to want to cooperate.

Goal:
I'm trying to install Ubuntu Desktop 12.10 (ubuntu-12.10-desktop-amd64+mac.iso) on my Macbook Pro 9,2

Problem:
When I'm at the Apple/rEFIt boot manager screen, and press enter over the linux CD icon the disc spins up and the screen goes black. It then stays black, but a blinking cursor appears in the top left. There are no options on screen, and it is completely unresponsive to any sort of combinations of keys that might have worked from other peoples posts and such. 
There is no purple screen. It stays on the black screen with blinking white cursor infinitely. 

I have downloaded and burned the .ISO to brand new dvds (dvd-r) multiple times on different machines, just to rule out corruption and burn failures. I've tried multiple burning speeds (4x, 6x, and 8x). I've tried using rEFIt and the Apple boot manager neither work. I have tried for several days to make a bootable USB from multiple tutorials, none of which worked. I've tried "sudo bless"-ing the Coreservices --bootefi as it told me in another post I found recently, to my knowledge it didn't do anything. It's as if my Mac is fighting for Ubuntu not to be installed with teeth and claws. That or I'm overlooking something completely simple. 

Macbook Pro Specs:
Macbook Pro 9,2
2.5 GHz Intel Core i5
4GB RAM
Intel HD Graphics 4000 384MB

I'm probably forgetting something, but any help would be super appreciated.
Thanks!

---

### Post by v4d3rr00t on 2013-04-11
Because I can't edit my post for some reason "must enter more than one character", I **SOLVED** IT. Using an actual external hard drive (1TB) rather than a USB stick solved the problem. Probably because my USB stick has seen it's days. Following the official Ubuntu USB installation procedures for Mac it took about 5 minutes including the restart and clicking on the external HDD icon. Boom, Ubuntu splash screen!

---

