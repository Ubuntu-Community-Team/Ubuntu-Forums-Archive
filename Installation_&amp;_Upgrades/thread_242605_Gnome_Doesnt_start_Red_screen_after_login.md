---
title: "Gnome Doesnt start?? Red screen after login"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by charims on 2006-08-23
Okay, big problem here, both when trying to upgrade from Breezy Badger and doing a fresh install.

I believe it is related to gnome starting up, but im a noobie, so I'm just drawing conclusions. When i upgraded, i tried to login, and, after entering my login and password, i would get a blank red screen with only my mouse pointer. The computer didn't freeze, becuase the mouse pointer still moved. Now, this error happened the first time i upgraded, so i reinstalled breezy badger, and then re-upgraded. Guess what, the first time i logged in, the gnome startup screen came up and everything worked fine, until i restarted, then it went back to the blank red screen. The red screen is the background you get while loading gnome btw.

Anyways, i ordered some dapper drake CD's and decided to try a fresh install. Well, when the live cd boots, it loads ubuntu, but after the autologin (becuase its the live cd) i get the blank red screen with the cursor. I have checked the cds, they are completely error free.

Well, i guess its time for system specs.

I have an Emachines C3070

AMD Sempron  3000+ processor (1.99 GHZ)
160GB hard drive and a separate 5 GB hard drive which i plan to hold Ubuntu
AGP NVIDIA GEFORCE 4000 MX GRAPHICS CARD, but i also have an onboard GEFORCE 4 MX
512 MB DDR SDRAM

MY specs should add up, maybe you guys can help :)

BTW if te answer is on the forums somewhere, I'm sorry that i didnt find it myself, but i did do a LOT of surfing for it, there is just an overwhelming amount of info to sort through.

---

### Post by Emerzen on 2006-08-23
I really a newb myself, but you may want to diable one of your graphics sets.  I'ld go into your system BIOS and disable the onboard card as it is more likely to be the less powerful.  W/ of the video cards disabled, try the liveCD.  Hope it's that easy for you.

---

### Post by charims on 2006-08-24
Well, I checked inside the BIOs settings. in the Intergrated Peripheral section all i found was my AC97 sound card, and my Nvidia LAN, plus IDE and a few things that shouldn't matter too much.
I couldn't find anything that even hinted about disableing onboard graphics, but i did find where to modify my AGP aperature size, Fast write capability (which is off) and a few other settings, maybe these need adjusting?

---

### Post by Emerzen on 2006-08-24
I'm sorry but I reread your original post, and can't imagine why Dapper would have a problem w/ 2 graphics cards if Breezy didn't.  This is far beyond me frankly, but I'm hoping my response will bump the thread up to someone who knows what they're talking about.

A troubleshooting step I would take is to download Kubuntu 6.06 and run it live.  If that works, then you know it's a GNOME problem.  If it doesn't work, then it's something lower level like the Xserver.

---

### Post by charims on 2006-08-24
okay, i will download kubuntu and give that a test, hopefully it works. We'll see :) TY for the help btw.

Oh, forgot to say, i can access a terminal window if i hit ctrl alt F1.

---

### Post by charims on 2006-08-24
Okay, Kubuntu WORKS!! so it must be a problem with GNOME. I didn't install Kubuntu yet to ensure that if someone wants to assist me to find the bug, that we can track it down, like i said, we can access a terminal window.

---

### Post by avtolle on 2006-08-24
Or, it is a problem with the original kernel, present when you upgraded from Breezy and also on the Ship-It CD. When you D/L Kubuntu, you D/L 6.06.1, which contains the updated kernel. I guess the only way to know would be to DL Ubuntu 6.06.1 and run it from the Desktop CD to see if it also works. My 2 cents.

---

### Post by Emerzen on 2006-08-24
avtolle make a good 2-cents...I didn't realize ship-it came w/ the older kernel.  You must be getting tired of all the d/l?  I'd give it a whirl if you have a thing for GNOME.  If not, Kubuntu rocks too.  Good luck.

---

### Post by charims on 2006-08-25
Well, in the end, i decided to just use Kubuntu, I like the blue colors more, no offense gnome, haha. Kubuntu is awesome, I like this. i already fixed my first problem too, i had to hook up my Netgear Ma111 wireless adapter to access the net, had to use ndiswrapper, which, after a headache of trying to compile the source myself, i finally figured out that the debian package was on the kubuntu cd.
So, i installed, shut off the prism 2 driver that kubuntu runs normally, and WELA!! Woo hoo!!!

Thanks everyone for the help, i was just about to give up on linux all-together.

---

### Post by Emerzen on 2006-08-25
Yeah, I've used both Ubuntu and Kubuntu and find KDE more to my liking, and I tend to use mostly KDE apps, which I find run better in a native KDE environment.  I don't know if you know about these sites, but here's a couple of good one:

[http://kubuntuforums.net/](http://kubuntuforums.net/)  (Kubuntu forums)
[http://www.kde-apps.org/](http://www.kde-apps.org/)    (KDE Apps w/ links to KDE looks -- alot of fun)
[http://www.kde.org/](http://www.kde.org/)   (main KDE site to keep up to date)

Automatix also has a version tailored for Kubuntu, which works like a charm.  Have fun.

---

