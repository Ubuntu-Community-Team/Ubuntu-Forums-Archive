---
title: "Upgraded to  10.04 no Plymouth animation??"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Jimtuv on 2010-05-01
I just upgraded from 9.10 to 10.04 and everything went fine. No problems other then there is no animation while booting. It just goes to the login screen (ugly tree ) :( . I have a feeling it has something to do with the nvidia card (fx5200) i am using the 173 driver. Because the screen switches resloutions and no Nvidia screen is showing as in the previous version 9.10. Any ideas on how to fix this?? I did a search and came up with no good answers yet. The Nvidia seems to be working fine everywhere else so far.

---

### Post by manolomanolo on 2010-05-01
What's the "Plymouth animation" ?

---

### Post by manoynmonic on 2010-05-01
There are a few different plymouth animations you can choose from in synaptic.  Install the ones that sound interesting, then:

```
sudo update-alternatives --config default.plymouth

```
There you select the number of the theme you want displayed at boot.  After making your selection do:

```
sudo update-initramfs -u
```

I don't know if there is an easier way, but that worked for me.

-mn

---

### Post by Jimtuv on 2010-05-01
> **manoynmonic said:**
> There are a few different plymouth animations you can choose from in synaptic.  Install the ones that sound interesting, then:

```
sudo update-alternatives --config default.plymouth

```
There you select the number of the theme you want displayed at boot.  After making your selection do:

```
sudo update-initramfs -u
```

I don't know if there is an easier way, but that worked for me.

-mn

I did that and no change. After the grub loads and I chose 10.04 the next thing that shows is just a blank screen and just before the login screen a messed up blue bar shows up at the top of the screen for a second or two then it pops into the loggon and everything looks fine.

Edit: running the live cd I get the plymouth animation just fine.

---

### Post by manoynmonic on 2010-05-01
What graphics card are you using?  I had an issue with noveau on my nvidia card, and had to load the proprietary driver to get things working right (forgot about that step).  Using the proprietary driver requires some additional tweaking to get the animation to display correctly, but works well enough.

If you don't have an nvidia card, then I'm out of ideas :( .

---

### Post by Jimtuv on 2010-05-01
I have a Nvidia fx5200 runing the 173 driver.

---

### Post by manoynmonic on 2010-05-01
In that case, try disabling the proprietary driver and using the noveau driver (ubuntu will default to that if you turn off the proprietary nvidia driver).  Plymouth works best with that anyway (but it broke suspend for me, that's why I stuck with the proprietary driver).  Can't hurt to try.  Good luck, that's all I got.

---

### Post by Jimtuv on 2010-05-01
It sort of worked. If I disable the Nvidia 173 then it does show the plymouth animation but I no longer have acceleration. I can't live with out that so that is not an option. I would rather have an ugly boot then that. I hope someone figures this out in an way I don't have to give up either.

---

### Post by topsykretts on 2010-05-03
hhmmm..im having the exact same problem..but i have a ATI radeon 3100 gfx card instead..i just get a blinking underscore while booting..any ideas?

---

### Post by Orographic on 2010-05-03
I get the same thing on my Gigabyte 945GZM-S2 board with an E4300 dual core. Just the blinking cursor in the top right and then the log on screen. Doesn't bother me though. Does it really matter if Plymouth boot splash is missing?

---

### Post by weblayoutstudio on 2010-05-03
Hi,
I have the same problem wirh a nvidia card, I have to more splash screen now, I get a black screen unti lthe login screen.

How to fix this ???

---

### Post by austin.lund on 2010-05-03
I have seemingly the same problem (i.e. blinking cursor).  But I've noted that when a routine fsck is done, the animation does appear (when fsck is started).

---

### Post by austin.lund on 2010-05-03
I've got a plymouth debug output from /var/log/plymouth-debug.log using the plymouth:debug boot argument (attached).

Seems it doesn't want to load the renderer, but gives no clues that are obvious to me as to why not.

---

### Post by Jimtuv on 2010-05-06
Yeah I have been searching everywhere for an answer. The best I have heard is it is a problem with plymouth and video drivers mainly Nvidia.

---

### Post by alh on 2010-05-06
> **Jimtuv said:**
> Yeah I have been searching everywhere for an answer. The best I have heard is it is a problem with plymouth and video drivers mainly Nvidia.
 
Try this line here.
 
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by Jimtuv on 2010-05-08
It turns out I had a number of problems acting together to cause this. Here is what I did.

First I realized that my grub was not current. I had the old grub not the new grub2 so that was the first thing I fixed following the procedures on this thread:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Next my Nvidia driver was not current so I followed the advice on this thread.

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

Then I fixed the animation and low resolution from advice from this thread

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

I hope this helps someone. It's not perfect (no acceleration while boot-up but it at least looks ok without making something else nonfunctional.

---

### Post by topsykretts on 2010-05-08
looking through the link that "alh" posted, i found this link and it worked for me:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

hope this helps.

---

