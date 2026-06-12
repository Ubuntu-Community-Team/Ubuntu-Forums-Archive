---
title: "[SOLVED] Compiz error"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nano Geek on 2008-10-02
Hello all,

I'm trying to enable Compiz on my Intrepid Alpha 6 install. I have Nvidia's driver installed, but I get the following error message when I try to enable it. ```
User@Intrepid:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

``` Does anyone know how to fix this problem?

Thanks

---

### Post by macroshaft on 2008-10-02
That's bog standard compiz vs video driver probs. Bare this in mind from the release notes on intrepid beta

> The fglrx and two of the older nvidia binary drivers are not available for X.Org 7.4 yet, so users of these drivers will be automatically switched to the corresponding open source drivers. 

Your post states XGL is missing, which if memory serves suggests a fglrx issue. Check your Xorg version I think you'll find it's 7.4. I'm not 100% on what all this means but I 'suspect' that it means compiz is a no-go for you until the new drivers have been built.

Can anyone confirm this?

---

### Post by klange on 2008-10-02
Do you have compositing enabled with Metacity by chance?

---

### Post by ktp on 2008-10-02
Can you provide more information on your video card and driver you have installed?

---

### Post by wilsong on 2008-10-02
Hey run this script for checking to see if your computer can run Compiz. and post the information 

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Heres an Screen shot of the script ran on my Ubuntu Box, and it shows you what you need, what you might not have see if it runs and gives you the All Green, this will also give us info on your video card and everything..

---

### Post by RAOF on 2008-10-02
> **WindowsSucks said:**
> Do you have compositing enabled with Metacity by chance?

^^^ This person knows the answer :)

And to go one further - turning *off* metacity's compositor will fix compiz for you.  You can find that in gconf-editor at the /apps/metacity/general path.

---

### Post by Nano Geek on 2008-10-03
> **RAOF said:**
> ^^^ This person knows the answer :)

And to go one further - turning *off* metacity's compositor will fix compiz for you.  You can find that in gconf-editor at the /apps/metacity/general path.Hey, it works! Thank you very very much. :)

And thanks to everyone else who took time to help me. I really appreciate it.

---

