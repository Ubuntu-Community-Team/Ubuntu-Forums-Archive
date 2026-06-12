---
title: "ATI HD4000 and Evergreen owners?"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SeePU on 2010-04-18
I was just wondering what the state is with these newer ATI cards if you are using Lucid. 

I want to upgrade my video card which is a GeForce 7950GT and lots of people are saying to go with a newer generation card.  But, if I go with an Evergreen series card such as HD 5570 or HD 5770, I am not sure the support is any good.

I thought to consider a HD 4770 but is it....
A) too old?
B) still not supported fully?

I was wondering which to choose.

I don't really see any good choices from the Nvidia side except maybe GT 240 or a 9800GT (maybe try to get one used?)?

Which should I choose?  I was going to budget about $100 and maybe pay more if it's a better card but $150 is the max.

What I do in Linux includes watching movies/videos so I need the card to work in all the various video players in Linux.  I also want 3D to work and any of the various video editors.  I also want no issues in software apps such as Gimp, Inkscape, VLC and I need 3D working so GoogleEarth and stuff like that.

What card would allow this?  I would rather switch from Nvidia to ATI but not if the issues continue and support is really slow which it does seem to be by the sounds of it.  

Recommendations?   Also, if you can, let me know what pros and cons there are depending on the card.  I know my Nvidia card works okay for what I'm doing now but I would like a bit more potential from a card.

---

### Post by BwackNinja on 2010-04-18
It all depends, are you looking to be using the open-source drivers. If not, then things are good for a newer ATI card. The Direct2D (for 2D acceleration) is coming along nicely but has a few bugs including that Xv does not work with it (but OpenGL output works well, it is also not enabled by default for these reasons) which should be resolved by the next release of their closed-source drivers. You won't get the benefits of having KMS because you wouldn't be using the open-source drivers, but the closed-source drivers do have redirected-direct rendering (smooth 3D with compiz).

I'm not actually an owner of one of these cards, I've just been following up on these things because I'm in the same kind of situation as you. My personal choice is the radeon 5770.

---

### Post by Longinus00 on 2010-04-19
R700 (HD4000 series) has 3d support and everything in the open source drivers. It's only the newest cards, evergreen, that the open source driver doesn't have 3d for. Considering you only want videos to play smoothly and compiz to work then the open source drivers are definitely the way to go as they have tear free video play back and everything.

---

### Post by clhsharky on 2010-04-19
HI

If you play games in wine or have a low powered cpu get Nvidia,
otherwise get a ATI.

Sharky

---

### Post by BrokeMahPC on 2010-04-19
ATI Radeon HD4670 here - it's supported and works well. I get the low res plymouth thing with proprietary drivers but apart from that have not had a problem.

---

### Post by salva84 on 2010-04-19
I have an ati 5850 and a ati 4750. With the ati 5850, the installation puts the screen off, so I cant even install the operating system. With the ati 4750, Im using the open source drivers, but sometimes the system get hanged with a colour screen, and I have to reset the computer :S

---

### Post by cascade9 on 2010-04-19
> **SeePU said:**
> IWhat I do in Linux includes watching movies/videos so I need the card to work in all the various video players in Linux.  I also want 3D to work and any of the various video editors.  I also want no issues in software apps such as Gimp, Inkscape, VLC and I need 3D working so GoogleEarth and stuff like that.

What card would allow this?  I would rather switch from Nvidia to ATI but not if the issues continue and support is really slow which it does seem to be by the sounds of it.  

Recommendations?   Also, if you can, let me know what pros and cons there are depending on the card.  I know my Nvidia card works okay for what I'm doing now but I would like a bit more potential from a card.

If your current card is working fine, why upgrade? The best you will get out of it is lower CPU use with video (with nvidia VDPAU...afaik the ATI hardware video decoder is still a work in progress). 

What more 'potential' are you looking for? 

> **SeePU said:**
> II don't really see any good choices from the Nvidia side except maybe GT 240 or a 9800GT (maybe try to get one used?)? 

GT240 = slightly upgraded 9800GT. Midrange/lowend gamers card these days. If you arent gaming, a GT220 is a better choice IMO.

---

### Post by Col-1023 on 2010-04-19
Do the hd5750 and hd5770 play nicely with kaffeine dtv viewer?

I'm thinking of getting one of these cards and want to use kaffiene to watch digital tv.

TIA

---

### Post by SeePU on 2010-04-19
I'd like to know that, too.  i like Kaffeine most of the time...

So, the HD 4000 series has the option of EITHER fglrx (proprietary) OR open source radeon driver?!?  I could use it no matter the application or one is better for certain jobs?

I do use my card for basic video play, yeah, but I also will want it for 3D too so Google Earth and the other apps I mentioned.

I definitely don't want to see TEARING and yeah, I would notice it.

I mentioned the GT 240 since I read it's based on the 9600 GT.  It is lower power/lower heat though compared to my Geforce 7950 GT and the newer 40nm architecture.  It's a smaller profile too so it's good for a lower priced card.  

The Radeon cards are a better overall deal as long as the DRIVERS ARE WORKING.  I read that updates to the kernel, Xorg and maybe Catalyst or fglrx versions might cause issues.  

So, I am comparing/measuring performance of:
Nvidia - GT 240 / 9800GT v.s. ATI - HD 4770 / HD 5xxx (5750 and 5770 mainly, i guess)

I'm not too worried about gaming as I've read that that field probably belongs to Nvidia and I'm not even sure if ATI 4xxx and 5xxx cards are usable or playable with Wine.  Are they?

I'd just assume boot up Windoze and use Windows XP or Windows 7 for any gaming anyway.  Probably less hassle.  I would just have to wait for the booting up of Linux when I'm done. :)

---

### Post by Longinus00 on 2010-04-20
Here's the state of features in the radeon driver [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature).

Here's tests for the radeon driver in actual real programs [http://www.x.org/wiki/RadeonProgram](http://www.x.org/wiki/RadeonProgram).

These pages might not be 100% representative of what you get in ubuntu since they deal with the development version.

So long as you stay away from the proprietary drivers you shouldn't have too many headaches.

---

