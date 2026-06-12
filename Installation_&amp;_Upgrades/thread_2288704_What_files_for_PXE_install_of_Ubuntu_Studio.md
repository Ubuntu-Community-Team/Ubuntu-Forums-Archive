---
title: "What files for PXE install of Ubuntu Studio"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by m-dw on 2015-07-29
Am building a brand new noiseless system for audio recording.  I've used Ubuntu Studio in the past, until my old system got too slow and want to use it again.  I have a working PXE server (Ubuntu server, isc-dhcp-server + tftpd), with the config based on [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer).

Older instructions talk about copying netboot files from the DVD into the TFTP root folder, but those files don't exist in the UbuntuStudio install DVD.  All the recent instructions I've found rely on obtaining the netboot image from [http://cdimage.ubuntu.com/netboot/vivid/](http://cdimage.ubuntu.com/netboot/vivid/) but obviously that will install Ubuntu, not UbuntuStudio.

I'm really struggling - can anyone offer any guidance, links to appropriate instructions etc?

---

### Post by PaulW2U on 2015-07-29
Please do not start duplicate threads as they cause confusion and dilute the community's effort to help. 

Duplicate here -  [http://ubuntuforums.org/showthread.php?t=2288712](http://ubuntuforums.org/showthread.php?t=2288712)

If you feel your post is in the wrong section and want it moved please use the report button and the forum staff will move it if appropriate.

Thread closed

---

### Post by Bucky Ball on 2015-07-29
Thread reopened. Install issue.

---

### Post by m-dw on 2015-07-29
Thanks for re-opening. Again sorry I don't understand the forum rules - I will try to do better.

---

### Post by Bucky Ball on 2015-07-29
All good. Carry on. Saw there was a response on this thread and not on the other but didn't realise it was a closed notification post. :)

If you can't install Ubuntu Studio directly you can install Ubuntu and then see [this]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu") for further details. Once you have followed it all through you'll be pretty much running Studio.

PS: 14.04 LTS is a long-term support release supported until 2019. 15.04 is an interim release supported until January 2016.

PPS: In that link it give this command to install packages:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

You can select which package you want. You might not need the graphics apps, for instance, so leave ubuntustudio-graphics out. You command might look like this:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins
```

You could probably even leave ubuntstudio-desktop out and let the others drag in what they need.

---

### Post by m-dw on 2015-07-30
Thanks, I think I might do that (that may have been what I did the last time)  I actually quite like the Unity desktop for day-to-day use, and prefer Fluxbox to Xfce for audio work so would have to do some tweaking anyway.

---

### Post by Bucky Ball on 2015-07-30
Okee doke. Well, if you install Ubuntu and don't install xfce4, then you'll have Unity by default. ubuntustudio-desktop may drag in xfce4 by as default. Not sure.

---

### Post by m-dw on 2015-07-31
OK, it appears to be even easier than Bucky Ball mentioned.  After pxe installs the base system, you're presented with a long list of optional builds, one of which is "Audio recording and editing".  Selected that, and Ubuntu desktop and pressed the go button.... Waiting but happy.

---

### Post by Bucky Ball on 2015-07-31
Great! I think that list is the tasksel list. I've never used it. I don't select anything then it reboots to a login CLI and I install from scratch. Never thought of it. The tasksel audio recording option sounds perfect for you. :)

Let us know how it works out.

(PS: As your last post was three hours ago I'm figuring you are either busy exploring your new system or busy trying to figure out what went wrong!)

---

### Post by m-dw on 2015-07-31
Yes, it's all good.  I chose two options - Ubuntu Desktop and Audio Recording and Editing. That option installed Unity and UbuntuStudio desktop (Xfce), but not the low-latency kernel.  Added that and I have got a pretty good audio workstation (or I have now I transferred my audio card).

O and I have to see if I can get it to play doom3, but that can wait for a few days.

---

### Post by Bucky Ball on 2015-08-01
Sounds great, but you don't need Unity AND xfce4. That is bloat and overkill. 

Great news, though. Enjoy. :)

---

