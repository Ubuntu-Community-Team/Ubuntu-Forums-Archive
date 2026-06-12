---
title: "Open source ATI driver observations"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Yashiro on 2009-03-19
I've pretty much accepted over the past 10 years that Linux has terrible desktop graphics performance.
Using my Ati 4850 card (Ati RV700) in Jaunty I've noticed a few things:

- The default install seems to have EXA disabled by default. Enabling EXA produces some considerable speed ups and most notably, artifact free scrolling.

- OpenGL is software only (eek), Compiz does not work.
Not a big deal but this is not explained when a user simply tries to 'enable desktop effects'.

- If the user enables compositing within Metacity resizing Windows becomes horrifically slow.

- Overlapping Windows can leave behind artifacts when the top most window is moved or minimized.

- Redraw is quite visible when moving overlapping Windows.

On the plus side my card is now recognised on install, heh. Not all the dis-satisfactions are due to the driver it has to be said. Xubuntu does offer a significantly faster and more artifact free experience over the Gnome default.

I am curious about other peoples Ati driver experiences with Ubuntu 9.04 (or Xubuntu, Kubuntu of course).

---

### Post by olskar on 2009-03-19
If opensource is the thing used before installing any propdrivers, I love it! Im actually thinking of not installing the propdrivers for the first time

---

### Post by RAOF on 2009-03-19
Oh!  I didn't know that the radeon driver we had at the moment actually supported any form of acceleration for r700 cards yet.  Sweet!

---

### Post by Yashiro on 2009-03-19
With EXA enabled the xorg free driver isn't too bad for basic use on r700 now, aye. Give it a test and post some observations. :)

---

### Post by krazyd on 2009-03-19
The latest builds of Jaunty have EXA and Xv acceleration enabled by default.

---

### Post by Yashiro on 2009-03-19
Yesterdays LiveCD certainly didn't or there is a bug.
Performance with/without EXA set in Xorg.conf was visibly different.

This is after getting the updated ati package from the update server (6.11git to 6.12)

---

### Post by zika on 2009-03-20
> **Yashiro said:**
> Yesterdays LiveCD certainly didn't or there is a bug.
Performance with/without EXA set in Xorg.conf was visibly different.

This is after getting the updated ati package from the update server (6.11git to 6.12)
what (tweak-)options work, now, in xorg.conf for this new version of driver?

---

### Post by Yashiro on 2009-03-20
Device section 
        Option      "AccelMethod" "exa"
        Option      "DRI" "on"

[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)
[http://www.botchco.com/agd5f/?p=33](http://www.botchco.com/agd5f/?p=33)

EXA acceleration and XVideo support *should* now (6.12) be enabled by default but ymmv.
Someone will probably come along and point out all the tweaks, hopefully.

---

### Post by racerraul on 2009-03-21
I've felt your pain...

I bought an nvidia card and that solved all my issues...

now...

-Desktop effects work!
-Compiz works!!
-3D Games work!!!
-even Java 3D games work better!!!!

I tried it all in an effort to save $ and use the embedded HD 3200 in my MB.
The open source drivers were stable, but now enough HW acceleration yet.
The restriced drivers available from Hardware Drivers (Jockey) did not work with Compiz or some 3d games (Open Arena & Nexuiz).
The AMD/ATI drivers worked with the 3d Games & Compiz, but performance was weak... at least for my expectations.

Good luck... trying to find help on the forums I took the hint.  I found there seemed to be more ATI issues than Nvidia.

I have 4 computers at home... 1 using a GeForce 4200s 128mb, 1 using a GeForce 7600 GT 256mb, and 1 using a GeForce 9600 GT.  All those can handle everything thrown at them with the 180.11 drivers.

The 4th is using the onboard HD3200 and I can't even get Compiz to work on it, although I was able to in a similar build... don't know why.  That one will be getting a new graphics card if my son brings me good grades this grade period... but I just might do it cause it will need it in the long run.

I've got no faith in ATI.

---

### Post by stoffe on 2009-03-22
> **Yashiro said:**
> I've pretty much accepted over the past 10 years that Linux has terrible desktop graphics performance.

An interesting statement. If you've picked your cards, you've been able to have good acceleration for many years. Usually it meant Nvidia, and usually it meant closed source drivers, but no problem with performance. I was also lucky with a job computer a few years back that also worked really well with some ATI card - but the closed drivers, of course.

That said, my last card was an Intel one that worked very well, and I'm now on my own first ATI card ever, a FireGL 5200 I think, in a Thinkpad a couple of years old. Using Jaunty and the default drivers I think performance seems excellent so far, though I haven't tried any 3D-heavy applications or games... no problem with desktop effects or other at least.

From what I hear ATI support is still quite a lot hit-and-miss, but I guess I was lucky. For once, I didn't really have much choice in the card to use.

---

