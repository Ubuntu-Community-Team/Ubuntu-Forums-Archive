---
title: "Intrepid Ibex XGL"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dillzz on 2008-10-19
Does anybody know if the xserver-xgl package will be available for Intrepid Ibex? I checked and cannot find it anywhere.  

I would rather use AIGLX for compiz, but I just added a second video card and third monitor.  This prevents me from twinview and forces me to xinerama.  I can get compiz to work currently through xgl on hardy.  Any ideas/thoughts?

---

### Post by spiderbatdad on 2008-10-19
I believe the standard now is opengl, libqt4-opengl...for 3d rendering...it doesn't do much of anything regarding gui programs...as far as I understand. There have been significant advances in how older video cards are handled. If you are running intrepid and are updated...you should see some basic effects, for example just clicking on a panel icon, should produce a noticeable effect. If you enable effects in the normal way through the appearances menu and install ccsm through synaptic, you should be good to go.

---

### Post by dillzz on 2008-10-19
Unless I am wrong, installing ccsm, or compiz config settings manager, I will still be using a composite window manager, which is not supported in xinerama.  Please advise . . .

---

### Post by klange on 2008-10-19
Not sure if it matters, but as of not too long ago XGL is - officially - no longer supported.

---

### Post by wgrant on 2008-10-19
Xgl has been removed from upstream, and we removed it from Intrepid not too long ago. Xgl is dead.

---

### Post by dillzz on 2008-10-19
Anyone else have any more ideas, I am not a fan of xinerama, tested and 2d performance is not the best.  I am dreading the other option (vista), virtualizing linux, due to the fact that everything I do is *nix based.

---

