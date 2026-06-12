---
title: "No nvidia drivers"
date: 2008-06-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by waspbr on 2008-06-29
I am trying out intrepid just like I did with hardy from alpha 1 to the end. anyway So I had this partition with 32 bit hardy that I wasn't using, so I just installed intrepid 64 on it.

Everything went fine, except that HArdware drivers does not list the necessary nvidia drivers that I would need. So I am stuck with no 3d graphics at a resolution of 800 by 600.

In order to solve this I went to synaptic and tried downloading nvidia-glx-new, which it did, but nothing really happened. 

Any pointers here?

Is there anything I might be missing?

oh yeah, before I forget, does anyone know if there has been any improvement in the broadcom cards debacle, I got a broadcom 4328 and I was wondering it has become compatible with the help of any module (not ndiswrapper).

PS: my video card comes up when I do lspci, so it is being detected.

---

### Post by yetilinux on 2008-06-29
I am encountering the exact same problem with the nVidia card.I tried to download the latest driver etc but still nothing happens and I can only get the 800 x 600 resolution.
With this problem I cannot install Evolution as I cannot access whatever instructions it may be giving at the bottom of the screen. 
I also cannot run Google Earth with it.

Need help urgently.

Thank you.

---

### Post by omha on 2008-06-29
you need the latest nvidia beta driver and patch it with this patch [http://ubuntuforums.org/showthread.php?t=833633](http://ubuntuforums.org/showthread.php?t=833633) then it works good.

---

### Post by Nullack on 2008-06-29
Not for me atleast, I found the patched nvidia driver to be unstable. GPU errors, getting kicked back to GDM on x failure etcetc. I have an 8600gt.

---

### Post by flytripper on 2008-06-29
make sure the driver is enabled in system>admin>hardware drivers.. also try ```
 sudo apt-get install nvidia-settings
```

---

### Post by Raptor45 on 2008-06-29
nvidia drivers haven't been done yet for the new kernel. You can manually patch + install them with the link given above, but you're better off just waiting until they hit the repos. Until then just use the nv driver. If you can't increase the resolution, your xorg.conf is messed up and you need to fix it.

[QUOTE=yetilinux]Need help urgently.[/QUOTE]

If you didn't read the warnings, this is a developmental release and not for everyday use. It is entirely expected that things may be broken for a time, so there is no reason you might "urgently" need help. You are welcome to ask around here for help, but you should expect things to be broken, and not necessarily fixed right away.

---

### Post by Nullack on 2008-06-29
> **flytripper said:**
> make sure the driver is enabled in system>admin>hardware drivers.. also try ```
 sudo apt-get install nvidia-settings
```

No dont do this, the kernel revision 2.6.26 is not compatible with whats currently available in the repos. You need to download .09 and custom patch it but as I said, its not stable

---

### Post by flytripper on 2008-06-29
mines fine

---

### Post by PmDematagoda on 2008-06-29
> **yetilinux said:**
> I am encountering the exact same problem with the nVidia card.I tried to download the latest driver etc but still nothing happens and I can only get the 800 x 600 resolution.
With this problem I cannot install Evolution as I cannot access whatever instructions it may be giving at the bottom of the screen. 
I also cannot run Google Earth with it.

Need help urgently.

Thank you.

Why are you even using this release in order to use Google Earth or Evolution for normal uses? Please use a current and stable release such as Ubuntu Hardy Heron 8.04.

---

### Post by waspbr on 2008-06-29
thanks i was expecting to wait til the next update/release.But yeah, this is not my primary OS, I still got hardy so now we play the waiting game.../me strokes proverbial beard

---

### Post by G.Ray on 2008-06-30
Oh, but yes.
The patched nvidia driver(.09) is reasonably stable.
Tested with compiz, sauerbraten, postal2MP, glest, openarena.
Nexuiz fall from test, but it is probably a nexuiz(early...and somehow mouse(pointer) related) bug.
8.10 x86 on intel_core2_E4400/nvidia 8500 gt videocard.
Sorry for my english.

---

### Post by syko21 on 2008-07-01
It's easier to just compile the driver until one is made available in the repos. I did it in gutsy and hardy with little effort, only had to make sure to uninstall and remove all traces of it before I installed a repository based driver.

---

### Post by andrek on 2008-07-01
The problem is, that you can't install the driver on 2.6.26 ( and 2.6.25 too ) kernel without some patches..
However, regarding the 2.6.26 kernel, there's only one patch - for the newest card's driver, such as NVIDIA 7xxx and 8xxx. As a Geforce 4mx user ( who needs 96.43.x drivers ), I won't have 3d acceleration until Nvidia will release a patch/new driver.

---

