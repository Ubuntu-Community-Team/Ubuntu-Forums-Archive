---
title: "Ati HD woes"
date: 2009-01-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by waspbr on 2009-01-18
I am sorry if this has been discussed before, well, I have taken my traditional 6-month plunge and downloaded jaunty alpha 3 onto my old and trusty desktop. It had a radeon HD3850 AGP (I know), since I wanted jaunty to play nice with my existing ext3 /home and other distro that I have in different partitions, then I decided to install it in ext3. 

anyway, everything went smoothly, wireless worked out of the box and everything. although I did notice that the rendering was a little...well... bad... sluggish But I dismissed it because I hadn't enabled the display drivers yet. 

So there I go, enable the drivers, but oddly enough it didn't  ask me to reboot, but I did it any way, so I rebooted and there were no improvements. Same sluggishness and slow rendering. Then  I thought that envy may be able to sort this one...not . I had to recover the display settings upon reboot. then tried to see if the Open Source radeonhd drivers would make any difference... no cake there. 

anyone having similar problems, has this been expected, I was out of the loop for a while so pls bear with me. 

cheers

---

### Post by ssam on 2009-01-18
the open source drivers for the hd3xxx and 4xxx radeons should improve a lot now that amd have opened up all the needed specs.
[http://www.phoronix.com/scan.php?page=article&item=amd_r600_oss_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_oss_3d&num=1)

i am not sure if this will make it into jaunty though. fingers crossed

---

### Post by rbmorse on 2009-01-18
Also, check the release notes (?) for Alpha 3.  I recall  an item somewhere indicating the current proprietary (restricted) ATI drivers (FGLRX) won't work with the Jackalope at this stage of development.

---

### Post by Quikee on 2009-01-18
Nope.. Ati fglrx drivers drivers aren't working because Xserver used in Jaunty is (in-development) 1.6 version which is "too new" to be supported by the drivers. I hope 9.1 release of fglrx drivers (that will happen any day now) will support xserver 1.6 as otherwise we will need to wait for yet another month for the support.

---

### Post by rbmorse on 2009-01-18
I just installed Alpha3 onto a machine with an ATI HD4850.  The default driver is "radeon".  Works great, withing the limits of the driver (no accelerated 3D, yet).

---

### Post by Quikee on 2009-01-18
> **rbmorse said:**
> no accelerated 3D, yet

And no 2D and video acceleration (by this I mean simple (XV) scaling acceleration and not support for hardware decoding of h.264 videos) either.. yet.

---

### Post by theApokalypsis on 2009-01-18
ATI's 9.1 Catalyst driver is in RC2 and provides (still beta glitchy) accelerated(xV) playback/Compiz3D. i.e. no flickering etc.



The main point is that yes, OSS or Proprietary, the specs are out for R6xx/7xx. So they are almost..... there.

---

### Post by ntbutler on 2009-01-30
Heya.

I have been having some similar issues (detailed [here]("http://ubuntuforums.org/showthread.php?t=1054591")). I had that thing about the computer not wanting to restart, but when I did anyway, all I seem to get is a black screen (I am using a HD3850). 

Does anyone know of a solution yet, or if there is really any hope on my card working on ubuntu?

---

### Post by theApokalypsis on 2009-01-30
> **ntbutler said:**
> Heya.

I have been having some similar issues (detailed [here]("http://ubuntuforums.org/showthread.php?t=1054591")). I had that thing about the computer not wanting to restart, but when I did anyway, all I seem to get is a black screen (I am using a HD3850). 

Does anyone know of a solution yet, or if there is really any hope on my card working on ubuntu?



I am using the latest 9.1 fglrx driver released two days ago (I reccomend purging any old fglrx drivers from system before hand). This is how I set it up. using a HD 3300 onboard until i get my 4870 back.

Ubuntu 8.10


- drop into recovery mode as root OR if in GNOME/KDE etc ctrl + alt + f2 into terminal and log back in:

sudo /etc/init.d/gdm stop
cd /download/location/of/driver/here
sudo sh atiFILENAME.sh

- now run through the installer (defaults support ubuntu) (need build libraries for this) and after its done:

sudo dpkg-reconfigure -phigh xserver-xorg
sudo aticonfig --initial -f (EDIT: -f removes any extra duplicate layout options)
sudo reboot



hopefully that points you in the right direction. the --initial config should set you up with a generic config which you can edit using the Catalyst Control Centre GUI.

(sudo amdcccle)

hopefully this helps :)

[32/64 Bit Download]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

---

### Post by Miguel on 2009-01-30
No need for those two links. The fglrx package is so "great" that no matter what you choose, you download both 32 and 64 bit drivers.

---

### Post by ntbutler on 2009-02-01
You are a champ man. Thanks for that. I'll try it out as soon as i get home.
Thanks!

---

### Post by kanukatchit on 2009-02-01
theApokalypsis,

That did not work for me, i have tried installing the new ATI 9.1 driver. but its GNOME crashes on login. I have a Radeon HD 3300 on a TA790GX. Can you please suggest some remedies ?

Thanks,

---

### Post by theApokalypsis on 2009-02-01
hmmm... by any chance did you have the open source drivers installed? I saw mention you need to completely remove those as well.

could that be it?

---

### Post by ntbutler on 2009-02-03
hmm, didn't quite work. I got a black screen again, but it didn't make the screen go into standby mode like it usually does, it just stayed on and black. I also couldn't ctrl+alt+f1 or anything, just stuck there...

---

