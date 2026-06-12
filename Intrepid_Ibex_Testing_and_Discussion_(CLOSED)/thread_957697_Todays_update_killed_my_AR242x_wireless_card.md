---
title: "Todays update killed my AR242x wireless card"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2008-10-24
Hey folks, 
           I have seen a couple of posts about this, but they are now marked solved. 

I done some updates today including kernel updates and it has killed my wireless. It was all working happily before with ath5k. 

ifconfig doesn't return any wireless cards, and nothing I seem to do will bring them back up. 

George

---

### Post by cantas on 2008-10-24
Just install the backports modules. It worked for me.

---

### Post by gmclachl on 2008-10-24
> **cantas said:**
> Just install the backports modules. It worked for me.

You mean linux-restricted modules?

---

### Post by ebb on 2008-10-24
Looks like the latest updates replaced ath5k with ath9k, which isn't working.  do:

```
sudo apt-get install linux-backports-modules-intrepid
```

Hopefully you have a wired connection to use.  That will install the ath5k module again, which should work same as before.  

Does anyone know if ath9k module is supposed to support this card?

---

### Post by gmclachl on 2008-10-24
> **ebb said:**
>   
Does anyone know if ath9k module is supposed to support this card?

 Well, that's an interesting question. I cannot for the life of me get it to work with ath9k. However, before Ibex moved to 2.6.27, I grabbed the linus tree and compiled a kernel with ath9k and the wireless worked beautifully. 

*EDIT* 
Oh my manners forgot to say thank you.
George

---

### Post by gmclachl on 2008-10-24
Ah well it still doesn't work, a grep of lsmod gives me some extra results


ath9k                 260024  0 
ath5k                 106496  0 
lbm_cw_mac80211       210728  2 ath9k,ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  3 ath9k,acer_wmi,ath5k
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

I wonder if there is a conflict or something else going on?

George

---

### Post by arfalconi on 2008-10-24
I had the same problem,

try disabing any driver on System->Administration->Hardware Drivers and reboot the computer. After that, check if any driver is loading automatically (none should be loaded), load manually the ath5k module.

Unfortunelly today's update caused my soundcard stop working (snd-hda-intel module)   :(

-Ariel

---

### Post by Demoncrat on 2008-10-25
When I checked this morning, the ath5k module was just not there (the ath9k was). After installing the backport thing in above post, everything works fine again, thanks. (I do have the AR242x as well)

---

### Post by thatgg on 2008-10-25
I tried doing this with my Acer One however it said some log folder was missing. Is there any other method?

---

### Post by blakamin on 2008-10-25
double post

---

### Post by blakamin on 2008-10-25
> **thatgg said:**
> I tried doing this with my Acer One however it said some log folder was missing. Is there any other method?

Try the stuff in this post... worked for me

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=5711824&postcount=6](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=5711824&postcount=6)

---

### Post by KenHagan on 2008-10-26
> **thatgg said:**
> I tried doing this with my Acer One however it said some log folder was missing. Is there any other method?

I've an AA1, too, and at least one of the how-tos for Intrepid on this machine suggested some fstab tricks to place all the logs on temporary file systems (to preserve the SSD). It mentioned that this might upset some installations. Perhaps that's the problem.

Then, again, it might not be worth it. The backported ath5k gives me no joy at all. I'm sitting a few feet underneath my router and seeing no wireless networks at all.

---

### Post by gmclachl on 2008-10-26
I managed to solve the issue, I had to go in the restricted drivers manager and unselect the current driver then select the ath5k one, and then reboot, and then dick about with it some more and then reboot and then it did work.

---

### Post by daily_grind on 2008-10-26
-> gmclachl:
could you be more specific about "dick around"?

---

### Post by joffe on 2008-10-26
Just built a computer from ground up and tried to make sure that all components were Linux safe. I bought an Abit WLP-01 PCIe card which identifies itself as
```
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Installs 64-bit Ubuntu, and no wireless... Recompiling the driver seems like a little overkill for me so i just add the **ath_pci** module to ```
/etc/modprobe.d/blacklist
```
and voilà! Wireless is up and running!

---

