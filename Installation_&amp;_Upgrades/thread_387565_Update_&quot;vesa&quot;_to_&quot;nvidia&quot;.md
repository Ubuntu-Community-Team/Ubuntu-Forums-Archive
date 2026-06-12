---
title: "Update &quot;vesa&quot; to &quot;nvidia&quot;"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by blockdude14 on 2007-03-18
I recently installed Ubunty Edgy 64bit. I'm using the **"vesa"** driver. How can i update **safely** to **"nvidia"** driver? I'm a newbie. I have an Geforce 7800 GT SLI OC 256MB. please help. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by hardyn on 2007-03-18
there are lots of tutorials on the installation of the nvidia binary drivers... 
have a quick search, im sure you will find more than one.

---

### Post by taurus on 2007-03-18
> **blockdude14 said:**
> I recently installed Ubunty Edgy 64bit. I'm using the **"vesa"** driver. How can i update **safely** to **"nvidia"** driver? I'm a newbie. I have an Geforce 7800 GT SLI OC 256MB. please help. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by blockdude14 on 2007-03-18
> **taurus said:**
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I just ttried this and it totally skrewed up everything. I switched back to "vesa" driver.

---

### Post by blockdude14 on 2007-03-18
Does anybody know a way that will work with my graphics card? :confused:

---

### Post by blockdude14 on 2007-03-18
help ???

---

### Post by hardyn on 2007-03-18
what is your graphics card?

---

### Post by blockdude14 on 2007-03-18
I have an Geforce 7800 GT OC SLI 256 MB

---

### Post by blockdude14 on 2007-03-18
I can't start Synaptic also. A error message shows "Unable to copy user's Xauthorization file." :(

---

### Post by rsambuca on 2007-03-18
You can try```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
Then restart X using Control-Alt-Backspace

---

### Post by blockdude14 on 2007-03-18
I just tried doing this and I got the shut down and restart button back but my sound disappeared. ?? The nvidia driver is still not working. :(

---

### Post by blockdude14 on 2007-03-18
does any body know how to fix this?

---

### Post by vincedia on 2007-03-18
[http://ubuntuforums.org/showthread.php?p=2276536](http://ubuntuforums.org/showthread.php?p=2276536)

I found that forum post by searching google for 7800 GT ubuntu

I followed those directions for post live CD and it worked.

Pay special attention to the line about envy! That little script worked for me with the exact same vid card.

Make sure that you are only working on the vid card, and shut down the PC after Envy a few times. It took a few times of restarting for it to stick for some reason.

Good luck!
Vince

---

