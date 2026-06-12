---
title: "Graphical Issue with install and boot"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by kchimko on 2007-04-12
Hi Guys,

I know this to be a hardware issue with my system and am looking for some advice on how to correct this.

Bascially i have tried isntalling ubuntu v6.10, fedora core6, and fedora core 7beta3, and all of these result in the same issue which is how i know this is a hardware issue. 

The thing that is really weird is that i also have SUSE v10 which does not create this issue when installing.

The issue is that if i chose to install eithe rof the 3 distro's above in the graphical interface regardless if its in the safe mode or not it will result in what appears to be lines going across my screen asoon as it boots into the graphical interface. 

Basically i will see the ubuntu logo or fedora logo but every second line of pixels will be distorted or clear which will cause the insatll to freeze. 

even weirder is that i can see my mouse pointer just fine and it will move around freely without any issues. 

The only way i can get linux isntalled is through the text base mode which will work just fine although on first boot right at the login screen or when it shows any graphics it will result in the issue. i can see the background but every second line is distorted but my mouse can move and looks fine but the system freezes and will not allow me to put any inputs in. 

On this same system SUSE linux will isntall just fine nomatter what installation method i chose and boot no problem aswell as both winxp and winvista will install without any issues. 

Any advice would be much appreciated and i wish i could take a picture of what my screen looked like to show you guys.


COMP SPECS
amd athlon 64 3000+
NVIDIA 7800GT
IDE 120GB HDD
2gb kingston pc3200 (4x512mb)
Asus A8N SLI Premium
Audigy 4 Sound Card0
Thank you

---

### Post by kchimko on 2007-04-12
Hi Guys, doing a bit of searching on my end here for a solution and i found a post with a guy that had the same issues as me and he posted a picture. 

This is sorta what mine looks like but i am able to make out some of the background. 

hopefully this helps you get a better grasp of whats going on. and just to mention this only occurs when loading the grpahical install or booting up one of the distros after doing a text install.

Thank you 

[http://i63.photobucket.com/albums/h139/kloroformd/163559061253_3300_2.jpg](http://i63.photobucket.com/albums/h139/kloroformd/163559061253_3300_2.jpg)

---

### Post by kchimko on 2007-04-12
bump and an update.

i tried removing my sound card, and ram aswell while swapping them around which was a nogo. aswell i reburned another ubuntu dvd at 4x speed to ensure it was not some issue with the burn and that was a nogo aswell. 

Pretty much the only thing i can think of is a compatability issue with my graphics card or the driver that ubuntu is loading. 

I dont have another video card to swap in either and my board does not have an integrated graphics solution so i am kinda hooped unless anybody knows a way to lead a different graphics driver during the bootup sequency that will work on my 7800gt.

please any advice will be helpfull.

Thank you

---

### Post by zvacet on 2007-04-12
**ctrl+alt+F1**

```
sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv**

---

### Post by kchimko on 2007-04-12
Thank you thank you!

I am at work right now but when i get home i will try this!

I appreciate your help!

Thank you!

---

