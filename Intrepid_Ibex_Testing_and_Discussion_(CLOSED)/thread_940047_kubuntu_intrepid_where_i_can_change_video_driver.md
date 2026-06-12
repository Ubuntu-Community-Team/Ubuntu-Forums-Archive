---
title: "kubuntu intrepid: where i can change video driver?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linomac on 2008-10-06
in previous kubuntu i had ability at monitor settings to choose if i want vesa or intel drivers and so on.

how i can choose video driver now?
how i can understand which one i use now?

/etc/X11/xorg.conf has no info at all about used video driver. i suppose this is because of new xorg.conf, but how i can find what driver i currently use?

problems that i have
google earth has big problem with displaying the globe.
monitor of laptop changes all the time levels of brightness 
etc

---

### Post by linomac on 2008-10-08
As I understand i must study the following:

[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

[http://ubuntuforums.org/showthread.php?t=940321](http://ubuntuforums.org/showthread.php?t=940321)
[http://ubuntuforums.org/showthread.php?t=941630](http://ubuntuforums.org/showthread.php?t=941630)

---

### Post by inportb on 2008-10-08
You can still specify your video driver in xorg.conf.

---

### Post by kforum on 2008-10-08
i know what your looking for, but its not there in the new kde, though...

maybe you need to activate new proprietary drivers through the "hardware drivers" interface, search for that in you 'K menu'.
and if you want an example of a xorg.conf...

this is how kubuntu set mine:
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
(inside the xorg.conf file) i obviously have a nvidia card, non-legacy.
i have some more developed examples, but this should give you an idea.(ill post another example if needed)
the section driver is where you 'set' your video card, if you know it.
and you should know it  ;).

cheers, 
hopes this aids you in some form.

---

### Post by linomac on 2008-10-09
i have intel x3100 on 965 chipset
it chooses intel driver.

i have problems lile:
- the display of google earth
- i have a laptop monitor (LVDS) and an external hdmi monitor (TDMS).
they are recognized automatically as one screen. I had same problem at hardy, but i expected this problem to be solved here, because of new xorg 1.5

maybe if i chose old i810 or vesa, things to work better

thanks

---

### Post by wgrant on 2008-10-09
> **linomac said:**
> i have intel x3100 on 965 chipset
it chooses intel driver.

i have problems lile:
- the display of google earth
- i have a laptop monitor (LVDS) and an external hdmi monitor (TDMS).
they are recognized automatically as one screen. I had same problem at hardy, but i expected this problem to be solved here, because of new xorg 1.5

maybe if i chose old i810 or vesa, things to work better

thanks

The intel driver is undoubtedly the correct one. i810 no longer exists as a separate driver, and vesa will give limited modesetting, no 3D acceleration, and very probably no dualhead. What gives you the idea that anything is going to be better than intel on that hardware?

---

### Post by linomac on 2008-10-09
@wgrant
ok u know better. 
probably i have wrong impression.
i remember with hardy,that although vesa was limited in possibilities, some times i had at least just the basics thing working, when i did not managed with intel.

but i think you are right.
so let's forget about changing driver.

do u have any advice how to fix my google earth and dual monitor problems?
1. what could be responsible that google earth globe does not appear clearly but flashing all time, and images are corrupted?
2. why 2 monitors (laptop and external) are recognized as one screen?

thanks

---

### Post by kforum on 2008-10-09
well i saw these problems around teh forum. so unless its something urgent, dont bother. im not sure any of them are fixed.

yet, after a bit of searching(*hint*hint*) read here:
[http://ubuntuforums.org/showthread.php?t=941630&highlight=dual+screen](http://ubuntuforums.org/showthread.php?t=941630&highlight=dual+screen)
(or post there also, maybe there are other posts, but generally i dont think its fixed yet)
and about your card issue, you can try:
[http://ubuntuforums.org/showthread.php?t=939691&highlight=x3100](http://ubuntuforums.org/showthread.php?t=939691&highlight=x3100)

or more properly here:
[http://ubuntuforums.org/showthread.php?t=909665&highlight=x3100&page=2](http://ubuntuforums.org/showthread.php?t=909665&highlight=x3100&page=2)
leading to here:
[https://bugs.launchpad.net/ubuntu/+bug/268006](https://bugs.launchpad.net/ubuntu/+bug/268006)

but from what i read generally the fix seems to be, to REMOVE completely any nvidia stuff you might have in your pc, it seems to bring conflicts.

i dont know since i have a nvidia card :p.


cheers, 
check these and see if it helps. ^^

---

### Post by paxmark1 on 2008-10-10
Might not be xorg and intel drivers but KDE  /KDM

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152)

Yes, verily, it is hard to find out info about what is going on in xorg.

      Do you have flickers when you type?

---

### Post by linomac on 2008-10-10
i dont have nvidia, no compiz, no problem with video.

My question is if it possible to fix automatically the virtual size, or it is must to edit xorg.conf

thanks

---

### Post by linomac on 2008-10-16
i have read somewhere that now xorg is configured through HAL's fdi files.
this is also for monitors?
thanks

---

