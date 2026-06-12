---
title: "Ubuntu 10.4 and ATI X1200"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by necotheone on 2010-05-03
Hello!

I installed the 10.4 but I can't use the Hardware aceleration...

I tried to install the privative drivers, but it show this error...

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

installing the fglrx, when I execute fglrxinfo, it shows

"Fallo de segmentacion"

Do you know what is happening?

Thank you!

---

### Post by Landie_UK on 2010-05-04
I have the same ATI card in my netbook I tried to install 10.04 and as the installation got further along the graphics got worse and worse. Everytime i went to a webpage with lots of pictures my screen just became a blocky mess of colours. I tried 64 bit 32 bit and netbook remix versions and they all did the same thing it must be this video card as 10.04 works fine on my desktop which has ATI 9550 card. I haven't had time to play with it yet. I will try different settings on the weekend hopefully.

---

### Post by necotheone on 2010-05-04
You don't know any solution?

---

### Post by Landie_UK on 2010-05-04
the only solution I have found so far is to  install all fglrx packages in synaptic package manager and uninstall all other ati driver packages. once I restarted I didn't get all the blocky mess. I can only get 1024 X 768 resolution and still can't install the proprietary driver, I get the same results as you but at least I can see what I am doing for now

update:\

Removed fglrx packages and installed the following packages:


xserver-xorg-video-radeon
xserver-xorg-video-radeon-dbg
radeontool
xserver-xorg-video-radeonhd-dbg

I now get 1376 X 768 resolution but still no enhanced effects. I can live without compiz for now and I can see my screen clearly without any blocky areas

---

### Post by Mark Phelps on 2010-05-06
You're NOT going to get the fglrx driver working because ATI dropped support for this driver and your card over a year ago.  The current drivers will not work with your card -- even though you can force an installation.

Your only recourse now is to remove the fglrx drivers and allow Ubuntu to install the default open source drivers.

---

### Post by Landie_UK on 2010-05-06
It's the xserver-xorg-video-ati package that is causing my problem, this is also the package that enables enhanced desktop. This package was installed when installing 10.04, I have uninstalled it. I don't really need compiz on a netbook anyway I can always WOW people with it on my desktop which is easier for them to see.

I guess you won't be able to enable enhanced desktop either necotheone, unless someone comes up with a different driver at a later date.

---

### Post by Landie_UK on 2010-05-06
It's the xserver-xorg-video-ati package that is causing my problem, this is also the package that enables enhanced desktop. This package was installed when installing 10.04, I have uninstalled it. I don't really need compiz on a netbook anyway I can always WOW people with it on my desktop which is easier for them to see.

I guess you won't be able to enable enhanced desktop either necotheone, unless someone comes up with a different driver at a later date.

---

### Post by Landie_UK on 2010-05-06
It's the xserver-xorg-video-ati package that is causing my problem, this is also the package that enables enhanced desktop. This package was installed when installing 10.04, I have uninstalled it. I don't really need compiz on a netbook anyway I can always WOW people with it on my desktop which is easier for them to see.

I guess you won't be able to enable enhanced desktop either necotheone, unless someone comes up with a different driver at a later date.

---

### Post by Landie_UK on 2010-05-06
It's the xserver-xorg-video-ati package that is causing my problem, this is also the package that enables enhanced desktop. This package was installed when installing 10.04, I have uninstalled it. I don't really need compiz on a netbook anyway I can always WOW people with it on my desktop which is easier for them to see.

I guess you won't be able to enable enhanced desktop either necotheone, unless someone comes up with a different driver at a later date.

---

### Post by Landie_UK on 2010-05-06
It's the xserver-xorg-video-ati package that is causing my problem, this is also the package that enables enhanced desktop. This package was installed when installing 10.04, I have uninstalled it. I don't really need compiz on a netbook anyway I can always WOW people with it on my desktop which is easier for them to see.

I guess you won't be able to enable enhanced desktop either necotheone, unless someone comes up with a different driver at a later date.

---

### Post by Landie_UK on 2010-05-06
Sorry I don't know why it posted more than once I got 1 error so I reposted but not this many just 2 times.

---

### Post by axelfoley on 2010-06-19
Yup I have this issue as well on a Packard Bell Z8A dot ma netbook (same as gateway and Acer models). It is driving me completely nuts and was only introduced when I upgraded to 10.4. Ubuntu 9 was fine. My laptop has been useless ever since upgrading to lucid lynx :-(

I have to now boot into Windows ........ errrrggg I feel dirty !

In summary my screen is fine for about 5 min using the Xorg ati driver then the screen starts to tear and corrupt making the laptop bl**dy  unusable !!!

It looks like graphics memory corruption but in essence its a bug in the xorg ati driver.

The graphics is a ATI x1200 as part of an integrated RS690 chipset and unfortunatly those ***'s at ATI no longer support it in their proprietarty driver :-(

You can drop all the compix effects and it appears to be more stable / last longer but I WANT THOSE FEATURES!!!!   I specifically bought the laptop for the 64 Bit AMD CPU
and the cube desktop.

The more I learn the more I realise you should NEVER buy ATI Graphics chips if you want seamless integration with Linux. I have found other issues with a discrete HD3450 Card on a mythtv server where I could not get the resolution to get to 1080p.


So if you are making a decision to buy a graphics card for linux ,,, my advice is to buy an Nvedia !
 
In the meantime we need to kick ATI's **** to support the latest Xorg release with the generic flgrx driver or help the Xorg developers know this is a real genuine issue that needs to be fixed in the Xorg ATI Driver.

They obviously broke something in the driver when they ported it to the latest Xorg release.

---

### Post by ninhalo5 on 2010-08-19
Strange, I've just updated my laptop recently to 10.04 and my x1200 is running better than ever with whatever driver Linux installed. I'm loving this build... the only hang ups I get is no real 3d grafix for gaming; yet the GL screen savers work just fine, and XMBC is not liking my laptop at all or vice versa. Compiz is running like a champ and I can even watch DVDs without lines going through the video as I have with older builds and Compiz running.

The only other time I was able to get this good of a graphics was when I downgraded Juanty to Karmic and was able to painstakingly install the catalyst. maybe someone can find a way to incorporate the Karmic catalyst into Lucid or even Maverick.

Heck my laptop in a whole is running better on Lucid than with the prior distros  and my cpu is an AMD :)  I better knock on wood....

I'm also running Ultimate Edition 2.7 which is Ubuntu LTS based,  maybe the differences lies there?

---

### Post by taesoobear on 2011-01-30
I am an Ubuntu 10.10 (AMD64) and ATI X1200 user, and I found that the latest experimental open source driver works better than the default driver. (Still there are some problems in 3D, but much less. I disabled compiz though)
I enabled the following PPA, and reinstalled xserver-xorg-driver-ati
[https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon)
For more details, see
[http://ubuntuforums.org/showthread.php?t=1451727](http://ubuntuforums.org/showthread.php?t=1451727)

---

