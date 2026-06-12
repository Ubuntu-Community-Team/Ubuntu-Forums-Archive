---
title: "Nvidia 177.80 not working"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kangaroo on 2008-10-18
I 've been trying for a couple of days to get the NVIDIA-Driver up and running to no avail. 

Updated from 8.04 via update-manager and ever since driver will not run. 

Tried both jockey and envyNG, but they can't seem to enable it. 

Error message is allways the same: 
(EE) Failed to load module "glx" (module does not exist, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0) 
(EE) No drivers available 

Graphics Card is a GeForce 8800GT 512MB on an Asus P5N32-E SLI 

If anyone could pls bump me in the right direction. If more info is needed, i'll be happy to provide it.

---

### Post by mosimea on 2008-10-18
One thing you might try is to check /etc/modprobe.d/lrm-video, as, at least prior to 8.10, I needed to comment out any lines referencing nvidia (e.g., nvidia, nvidia-legacy, nvidia_new).  You might also try a manual install, getting the driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us), booting up in recovery mode to a terminal and installing.  The drawback is that you'll have to reinstall the driver the next time you have a kernel upgrade.

---

### Post by gjoellee on 2008-10-18
the driver is still in BETA isn't it? If it is it means the driver still is in development!

---

### Post by Kangaroo on 2008-10-18
@mosimea 
Thanks. That did it. Awesome ! 

Now, the window borders of Firefox disappear upon enabling Compiz-Fusion. Ah well, there's always something, isnt it ;-) 

Thanks for the help.

---

### Post by mosimea on 2008-10-18
Glad to help.  For the window borders, you might try to add:

```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "AllowGLXWithComposite" "True"

```

to the pertinent Device section in your xorg.conf. While 8.10 is moving away from using xorg.conf, it may still help.

---

### Post by JPorter on 2008-10-18
> **gjoellee said:**
> the driver is still in BETA isn't it? If it is it means the driver still is in development!

177.80 is an official release, as of October 7.  IT IS NOT BETA.

Details:  [http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1)



Details on the Ubuntu packages for 177.80:

[http://packages.ubuntu.com/source/intrepid/nvidia-graphics-drivers-177](http://packages.ubuntu.com/source/intrepid/nvidia-graphics-drivers-177)

---

### Post by shane19174 on 2008-10-18
> the driver is still in BETA isn't it? If it is it means the driver still is in development!

No, 177.80 is the final.

Kangaroo, good to see you got it working, but it's weird you have to jump through these hoops. I also did an upgrade from Hardy, where I had been doing manual installs of the beta drivers for my 8600GT, and everything worked right off the bat. That is, "system > hardware drivers" took care of everything automatically. And I've never had a problem with Firefox's window borders. (I use the "extra visual effects" setting for Compiz without problems.)

I know this doesn't help much, but I'm writing this to suggest that there must be a problem somewhere (in your user config?) that you carried over from Hardy. Maybe you could set up a new, clean user profile to test and see if you have the same problem.

Wish I could help more,
Shane

---

### Post by shane19174 on 2008-10-18
> I would really like to see this release included in Intrepid... who are the package maintainers for Ubuntu? If it is not yet in the repos, what are the chances of a quick backport? Some of the features enabled in this release are critical for owners of newer Nvidia cards.

It's already in Intrepid. Did yours not get updated?

---

### Post by JPorter on 2008-10-18
> **shane19174 said:**
> It's already in Intrepid. Did yours not get updated?

My mistake... brain not turned on this morning.  I'm actually using it on my desktop box, too.  /facepalm



I do have an issue though, that maybe someone here can help with.  I'm not able to get multi-monitor working properly using the Nvidia control panel in 177.80.  Whenever I try to save to the config file using the current settings, the applet crashes.  It looks like I am going to need to do the multiple X approach to multiple monitors, because my screens are different sizes.  Are there instructions anywhere on the web for configuring this properly?

The card is a 9500GT, by the way.  One monitor connected DVI @ 1680x1050, the other connected VGA @ 1280x1024.



[edit] Nevermind!  Solved in another post here:  [http://ubuntuforums.org/showpost.php?p=5850115&postcount=6](http://ubuntuforums.org/showpost.php?p=5850115&postcount=6)

---

### Post by Kangaroo on 2008-10-18
> **shane19174 said:**
> No, 177.80 is the final.

Kangaroo, good to see you got it working, but it's weird you have to jump through these hoops. I also did an upgrade from Hardy, where I had been doing manual installs of the beta drivers for my 8600GT, and everything worked right off the bat. That is, "system > hardware drivers" took care of everything automatically. And I've never had a problem with Firefox's window borders. (I use the "extra visual effects" setting for Compiz without problems.)


@Shane19174
Yep, i find the hoops weird too, this installation is quite old by now, always updated since Dapper, never reinstalled. Maybe i'll do a reinstall sometime.

---

