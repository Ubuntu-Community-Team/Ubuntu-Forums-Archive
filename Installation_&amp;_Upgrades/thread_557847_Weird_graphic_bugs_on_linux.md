---
title: "Weird graphic bugs on linux"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by S0meguy on 2007-09-23
Hey,

I wanted to install Linux on my system and I was interested in this Ubuntu Gamers Edition because a friend of me uses this one([here](http://ubuntusoftware.info/ubuntu_ultimate_gamers/)).

But first of all I wanted to try this thing on a virtual machine. So I created a mirror of my desktop PC(2 HDDs, one has vista, other has xp) on MyVirtualPC.

Then I loaded the ubuntu ISO and tried to start it from the menu but then I get some WEIRD graphic bugs: [http://someguysdomain.de/gamers%20edition.JPG](http://someguysdomain.de/gamers%20edition.JPG)

I thought that maybe its because of the gamers edition so I downloaded the normal ubuntu feisty fawn 7.04.

Same problem: [http://someguysdomain.de/linux.JPG](http://someguysdomain.de/linux.JPG)

I tried that "choose safe graphics mode + vga=771" thing but didnt work.

I know that linux doesnt really like ATi but I do have a ATi Radeon HD 2900XT. Though another friend of me who has the same card, got no problems with ubuntu.

---

### Post by luisromangz on 2007-09-23
It isn't an issue with your ATI card, as you are running Ubuntu inside VirtualPc so Ubuntu can't use your card directly. What ubuntu uses is the virtual device provided by VirtualPc. 

The vga=771 option doesn't work for the desktop environment (or any other X based program), it is just the virtual terminals resolution.

I don't think that this is an Ubuntu problem. Something tells me that it is not a good idea to run a non Windows operative system in Microsoft's Virtual Pc, which is such an inferior product compared to WMware  Server (which is free as in beer after registration). You could also try VirtualBox.

PD: A google search pointed me to this. Hope it works for you: [http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx](http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx)

---

### Post by S0meguy on 2007-09-23
Its not because of MyVirtualPC because I tried to boot from my real desktop PC and I got the same problems.

Edit: Well, I only tried the gamers edition though because I didnt burn the usual Ubuntu yet but I think it will be the same.

Edit: this link doesnt help because I cant even get to the "desktop" in linux because of those bugs

---

