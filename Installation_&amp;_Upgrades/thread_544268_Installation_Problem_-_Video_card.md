---
title: "Installation Problem - Video card?"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by croquagei on 2007-09-06
Hey guys

I've been experimenting with Ubuntu on my laptop for almost a year now and decided it was time to make the complete shift to Linux (i.e my desktop).

I put in the installation dvd for feisty (just downloaded the ISO and burnt it, same disk i used to install on laptop).  After it finished loading at the splash screen i see what i imagine should have been the Gnome desktop with an icon to choose to install.  Unfortunately... this was not the case. 
My screen went some crazy weird colours and that's all i got.

I found a screen shot of something similar from another post (although not exactly as i will explain below)
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-1-4.png[/IMG]

This for the most part represents what i see, only in the screen shot above you still see the gnome task bar and a window.  All i see is the weird colour at the back.

I'm assuming it's a video card problem, i run a Leadtek 6600TD.  The only real hassle is I can't install a working video card driver if i can't see what I'm doing

So how can i get around this problem?

---

### Post by akarun on 2007-09-06
Even I have similar trouble. I tried installing ubuntu 7.04. 
I have,
AMD 64  X2  4000+ processor,
NVIDIA 8500 GT graphics processor,


When I try to install ubuntu with the installation CD (this is the Ubuntu 6.06, I didn't have the new ISO CDs), the X server doesn't come up. Hence I was not able to click the "Install Ubuntu" button on the desktop. This was because of the NVIDIA card I suppose.

My institute is a repository for Ubuntu,Debian. So I tried a network installation of Ubuntu 7.04. I read in many reviews that 7.04 has come up with a neat way of installing the restricted display drivers for nvidia. That was very nice to hear. But the problem in the first place is, the X server wouldn't come up. So, I had another option of installing the NVIDIA drivers "non-ubuntu" way, rather the "NVIDIA way", i.e. downloaded the executable from NVIDIA website and installed it. When I restarted the comp, this time X server booted up, but I couldn't make any sense on the screen. It was highly skewed. I could type my login and password (purely out of guess), and I could log in (The login sound from Ubuntu confirmed me). Now I am really clueless. I couldn't make out anything on the screen. The screen was worse than the picture in the previuos post.

Please help me with the problem. Is there any command line way of enabling the restricted drivers so that ubuntu can install it and X could come up for me? I have access to the virtual terminals.


Thanks in advance,
Arun

---

### Post by dabl on 2007-09-06
@crocquagei -- I have no clue about Leadtek cards, but I suspect you and akarun can both run a VESA display.  Either via installing a "text mode" system using the Alternate Install CD, or else using Ctrl-Alt-F1 from your (broken) GUI, you need to get to a command line prompt, aka "text console".  Once there, you can follow this guidance to set up a VESA display:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

It will be functional, even though it won't take maximum advantage of your graphics cards' capabilities.  :)

---

### Post by Kevin Jones on 2007-09-23
Thanks for the infor,
Can you tell me if will this work for vtek,  VT 1300 card?


Kevin Jones

---

