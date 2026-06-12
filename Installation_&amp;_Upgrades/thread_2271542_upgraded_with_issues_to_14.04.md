---
title: "upgraded with issues to 14.04"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by Ka Fish on 2015-03-30
I can only guess this started with a bad processor four upgrades ago. I've always had a slight instability even when I was running FreeSpire.  My main monitor is some generic brand, AOC. I'm using a 256 Nvidia GeForce 6200 a.g.p. card. I noticed after the upgrade my video seems to lag a bit. In the process of seeing what's where I see I only have one screen resolution 1024 x 768 (4:3). I installed L.M.M.S. after the upgrade lost it & it said I had to remove five things dealing with Nvidia. I don't remember what they where & there was no suggestion as to replacing them. If I hit a few buttons too fast the sound distorts like the amp. is clipping. I can log out & in to get that back to normal. Sometimes it freezes for a minute or two. The whole desktop dissappear leaving only the background. I've tried apt-get update --fix missing with no success.

---

### Post by sandyd on 2015-03-30
Quite possible that Unity UI is too graphically intense for your graphics card, which is a Nvidia GeForce 6200 from 2005.

Anyways, the proprietary drivers could have possibly been removed.
They can be reinstalled with
```

sudo apt-get install nvidia-304
```

If it fixes it, and the desktop is still slow, 

Boot from the following, and see if any of them are faster:
[LIST]
[*]Xubuntu
[*]Lubuntu
[/LIST]

---

### Post by Ka Fish on 2015-03-31
I installed the 304 driver & it removed L.M.M.S. I opened synaptic package manager to install it again & got "To be removed nvidia-libopencl-304 To be installed ocl-icd-libopencl1 wine1.6 wine1.6-i386. It seems to be working better now. It's not crashing where it did before. What is the best agp cared I can put in? Thanks.

---

### Post by sandyd on 2015-04-01
Apparently, its a bug.
See [http://askubuntu.com/questions/449507/nvidia-libopencl1-331-has-to-be-removed-before-installing-wine](http://askubuntu.com/questions/449507/nvidia-libopencl1-331-has-to-be-removed-before-installing-wine) for fix (answer with a green tick)

---

