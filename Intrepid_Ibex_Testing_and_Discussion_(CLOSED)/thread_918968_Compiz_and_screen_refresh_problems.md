---
title: "Compiz and screen refresh problems"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-09-13
I seem to be having some screen refresh problems when using compiz: parts of the screen are refreshed, but others aren't. That means nautilus doesn't show files or folders until I move the cursor over them, firefox doesn't show webpages properly until I scroll down, and so on.

Are you guys having this problem too? I would attach a screenshot, but for some reason all these artifacts seem to be corrected when I push the print screen key.

---

### Post by soapytheclown on 2008-09-13
indeed i have had this problem since i updated i didnt tihnk it was compiz though untill you mentioned it for some reason i thought it was an Nvidia problem but i just turned off compiz and voila it is fixed.. no idea why this is happening my borther told me he had the same problem so he went back to hardy

---

### Post by Bou on 2008-09-13
> **soapytheclown said:**
> indeed i have had this problem since i updated i didnt tihnk it was compiz though untill you mentioned it for some reason i thought it was an Nvidia problem but i just turned off compiz and voila it is fixed..

Yeah I thought it was a Firefox problem since it's most noticeable using FF.

---

### Post by lefthand on 2008-09-15
I'm seeing that as well. I figured it was related to this thread about weak Intel drivers:

[http://ubuntuforums.org/showthread.php?t=909665](http://ubuntuforums.org/showthread.php?t=909665)

must be something else though.

---

### Post by Bou on 2008-09-15
Yeah, I filed a bug about it:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904)

---

### Post by plun on 2008-09-15
One way to get clues about this, I have both Ubuntus version and
Compiz-fusion from GIT installed.

- Install fusion-icon

- Start terminal  > fusion-icon  > check output

With Ubuntus binary, compiz.real, **8 bit GLX is missing**.

If I starts with the compiz script (GIT) everything is OK.

---

### Post by RAOF on 2008-09-15
That probably indicates either (a) the video plugin is no longer checking for an 8bit GLX visual, which only ever existed in a patched Xgl, or (b) that the Video plugin is no longer being loaded.

That warning is entirely benign.

---

### Post by plun on 2008-09-15
> **RAOF said:**
> That probably indicates either (a) the video plugin is no longer checking for an 8bit GLX visual, which only ever existed in a patched Xgl, or (b) that the Video plugin is no longer being loaded.

That warning is entirely benign.

Well.. it was about finding clues.

Something went "messed up" with glx on Thursday/Friday last week.

Jockey, Mesa, Xserver, Xorg and a new nVidia source.

The new nVidia source perhaps....:)

---

