---
title: "IBM ThinkPad R31 won't go any further than login screen"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jepong on 2008-10-10
Good Day!

I just upgraded (using partial upgrade) my thinkpad to intrepid ibex beta today. Installation went all OK but after I reboot and asked for username and password... all I can see is a brown screen and a mouse pointer.

Is there a work around for this already?

Thanks,

Jeffrey

---

### Post by jerrylamos on 2008-10-11
My R31 does the same thing.  Alpha 3 & 5 work, Alpha's 4, 6, and Beta don't. see launchpad bugs 259385, 257450, 277344 

All indications are buggy Compiz code used by Gnome in screen candy and special effects.  What's happening is linux boots successfully, Xwindows comes up fine, Gnome using Compiz builds the desktop image, then some code I assume Compiz hangs up altogether.

If you want to use Intrepid, there are maybe 4 ways I've found so far.
1. Xubuntu Intrepid works, using Xfce4 as a display manager, not Gnome & Compiz.
2. Kubuntu Intrepid works, using KDE as a display manager, not Gnome & Compiz.
3. Alpha 5 Ubuntu works, IF YOU DON'T UPDATE COMPIZ!!  You can get Alpha5 from [http://www.ubuntu.com/testing/hardy/alpha5](http://www.ubuntu.com/testing/hardy/alpha5).  If you inadvertently update Compiz you are in for a re-install.
4. Try to replace the Compiz with Metacity.  Metacity is an older simpler display code WHICH WORKS however I have only seen some crude ways to get it going which don't reliably work for me.
5. Install xfce4 onto Ubuntu which is what I'm using here.  A bit klutzy.

Crawling through the forums there are several types of PC's that have similar problems.

As far as I can tell, there has been little (no?) developer activity on this bug which seems to be persistent with Intrepid.  Unless there's a breakthrough on Compiz looks like Hardy is the last reliable Ubuntu for the R31.

Jerry

---

### Post by jepong on 2008-10-12
Thanks Jerry for the reply.

I've been tracking all your intrepid ibex posts.

Aside for the trackpoint, Compiz is also a problem in hardy heron. By default it'll install desktop effects but it slow down and hangs your system. I usually turns it off because of that annoyance.

I heard the trackpoint bug is fix with the new kernel in ibex beta. Can you comment on this?

Thanks

---

### Post by jepong on 2008-10-27
Hi Jerry,

I did your work around on RC and I can see my desktop now.

Hope compiz get fixed before final release.

---

