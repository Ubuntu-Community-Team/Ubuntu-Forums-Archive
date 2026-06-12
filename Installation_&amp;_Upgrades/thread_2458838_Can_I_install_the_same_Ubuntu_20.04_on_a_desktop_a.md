---
title: "Can I install the same Ubuntu 20.04 on a desktop and a old HP laptop?"
date: 2021-03-04
forum: Installation &amp; Upgrades
---

### Post by Swan_DB on 2021-03-04
I have 20.04 on a 4GB usb stick, the install went surprising well on my desktop (Intel i5 3570k, 64 bit, gigbit mobo, not sure what else is relavent, sorry, oh, ddr3 RAM, I think) built new in 2011-2012-ish.
Will this same 20.04 install work on a HP laptop that has a intel celeron, assuming it's 32 bit, and had Windows vista originally, now it has....  like Ubuntu 14.xx from a while ago?
Or do I need to download Ubuntu specifically for the HP laptop?  

In the process of trying to install the 20.04 (same one I have now on Desktop, and am writing this here now with) on the old HP laptop from probably 2010 or maybe before even, idk.
It's loaded into the "Welcome; Try Ubuntu; Install Ubuntu" menu, which gives the impression it might work?:confused:

PS. I have a brain injury, and searching/googling/reading stuff isn't feasible sometimes, hence this "just google it" type of post:(.  Thanks for any input at all, even just some relevant facts about installs, it's appreciated : )

EDIT: I'm at the "installation type" step, and it's asking to erase Ubuntu 12.04.5 :popcorn: w/ reinstall (why reinstall 12.04.5?), or install 20.04.1 alongside 12.04.5 (don't really have the disk space for this), erase disk and install Ubuntu (I assume this is the one I want):p Let's do it!
wait, I remember using the 4th option, "something else" and creating my own partitions for my desktop install, maybe I should do this for the laptop too?  Idk....  [-o<

EDIT 2: It's a dinosaur of a laptop...  Not 80's old, but wouldn't surprise me if it was from like...  hang on..................   Hahaha!  2008, so 13 years old, lol, it's a 64 bit system, as most are, like u/CatKiller said: [https://www.google.com/search?q=hp+compaq+presario+cq50&oq=hp+compaq+presario+cq50&aqs=chrome..69i57j0l6j0i22i30l3.41927j0j7&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=hp+compaq+presario+cq50&oq=hp+compaq+presario+cq50&aqs=chrome..69i57j0l6j0i22i30l3.41927j0j7&sourceid=chrome&ie=UTF-8)

---

### Post by CatKiller on 2021-03-04
> **Swan_DB said:**
> Will this same 20.04 install work on a HP laptop that has a intel celeron, assuming it's 32 bit, and had Windows vista originally

Ubuntu is not available for 32-bit processors. At all.

Early 64-bit versions of Windows were pretty terrible, so it's possible that you had 32-bit Vista on a 64-bit processor. It's worth checking. If you've got a 64-bit processor then, yes, you can use the same installer. If you've got a 32-bit processor then you can't use any installer; you'd need to pick a different distro that caters to obsolete machines.

---

### Post by Swan_DB on 2021-03-04
Would this install likely not have gotten to the "installation type" part, if it weren't compatible?  (Edit in my main post)
Thank you for the info, it's appreciated more than you know : )

---

### Post by roadrunner510 on 2021-03-04
requirements for Ubuntu2 GHz dual core processor 
4 GiB RAM (system memory) 
25 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 
VGA capable of 1024x768 screen resolution 
Either a CD/DVD drive or a USB port for the installer media 
 :

---

### Post by Swan_DB on 2021-03-04
> **roadrunner510 said:**
> requirements for Ubuntu2 GHz dual core processor 
4 GiB RAM (system memory) 
25 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 
VGA capable of 1024x768 screen resolution 
Either a CD/DVD drive or a USB port for the installer media 
 :

Geezus, I'm pushing it on the RAM, I've got 2GB installed, but 4GB supported (not sure if I make it or not), I linked my specific "HP laptop compaq presario cq50" model in the original post and it's....  it's just sad.  Thanks for the input, it is much appreciated :guitar:

---

### Post by Swan_DB on 2021-03-04
My HP laptop is struggling to finish the install, maybe it's the slow wifi, or the laptop is overheating and running slow, but she's struggling; I may have to changed from "yes it installs" to "it might install on yours, but mine caught on fire during install", lol.
Specs seem to line up, it *should* install, maybe I should have opted for the "something else" install option and made my own partitions, as well as not installed the option for "3rd party softwares"...  idk.  Will update this thread after it's all over with the final result.
Thanks for the input, guys.

EDIT: **[SOLVED] **It installed, but the laptop is just too old to be productive, laptop overheats and starts slowing down/locking up, plus the RAM is at the limit for Ubuntu 20.04 install at 4GB.  I may try to find a Linux distro with less RAM requirements and try again another day.

---

### Post by Impavidus on 2021-03-05
There's no need for a different distro, a different flavour is enough. Lubuntu, Xubuntu and Ubuntu Mate are flavours of Ubuntu, using the same repositories from where they get their software. They are largely identical, but have different desktop environments and default applications, making them run comfortably on computers with only 2GB RAM. You can at least try one of those.

---

### Post by oldfred on 2021-03-05
My Toshiba laptop from 2006, purchased 2 weeks before Vista released with XP & "Vista Ready" had only 1.5GB of RAM.
I used to be able to install full Ubuntu, but terribly slow, so changed to fallback which is another lighter weight gui.
But with 20.04 full Ubuntu would not install, had to install server version & then add fallback. Fallback install did not add all the required Gnome bits & became a hassle to get working.

About same time, it was suggested to try Kubuntu, so ended up converting desktop to Kubuntu. Kubuntu not considered lightweight install, but is lighter than full Ubuntu. It worked to install it to old laptop (bit surprised). 

Laptop is retired as main battery dead, so only runs when connected to power and coin battery dead as I have to reset time everytime I fully power it up after being disconnected. But it still runs if needed.

I also suggest the lightweight flavors as Impavidus suggested above.
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

---

