---
title: "NVIDIA + Kernal headers kills X?"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by cold_fu5ion on 2007-09-25
Hi,
I updated up Nvidia graphics drivers to the latest version form the Nvidia site about 2 days ago, everything was fine until about 2 hours ago when I turned on my system and was told there are updates. I ran the update manager which downloaded kernal headers, so I had to restart. Upon restarting two bad things hapened.

1) Grub failed to load (I thin it loaded my old config somehow), fixed this by changing the boot option to the correct partition.

2)X failed to sart, I got the message "API mismatch: NVIDA driver component has version 100.14.19, but the kernal version does not match"

I have tried to restore my xorg.conf from the last good backup but that has the same result, I also followed a post on these forums on creating a new xorg.conf using dpkg-reconfigure xserver-xorg but this also didn't work.

I read this post [http://ubuntuforums.org/showthread.php?t=355757](http://ubuntuforums.org/showthread.php?t=355757) which seems to be the same problem, and was solved using a script called Envy, which I dont know how to install without using a GUI and the internet :-(

Can anyone help me? At best I'd like to have x working properly or at worst remove the offending drivers (if possible) so I can backup my files and reinstall.

Thanks.

---

### Post by mrazster on 2007-09-25
Have you tried changing your xorg.conf sp that it loads nv or veas drivers..and then trying to reinstall/uninstall the nvidia drivers??

It should say something like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
```

change it to look like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"
```

or like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "vesa"
```

Save and reboot.
That should get you in to GUI...if not, then from CLI try to either reinstall or uninstall the drivers from nvidia site.



If the above does not work, you could also try to install the nvidia drivers from the repos...if you haven't already tried it.

 When in CLI do this:

```
sudo apt-get install nvidia-glx-new
```

or if you have an older card, then do:

```
sudo apt-get install nvidia-glx
```

to enable the drivers do:

```
sudo nvidia-glx-config enable
```

Reboot and see if that works.

---

### Post by cold_fu5ion on 2007-09-25
Horray!
Thank you so much for the help.

I did your first instruction, renaming the driver from nvidia to 

Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"


Then I got X :-)

Installed Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) which downloaded and installed nvida drivers AND! properly configured xorg.conf for me.

I <3 Ubuntu, the community really makes it great.

Thanks again :-)

---

### Post by mrazster on 2007-09-25
> **cold_fu5ion said:**
> Horray!
Thank you so much for the help.


No problem m8.....glad I could be of some help to you.

Just keep in mind for future upgrades of kernel-images or restricted-modules e.t.c....you are going to have to uninstall/disable thirdparty drivers or in this case drivers installed with envy before doing the upgrade and then reinstall/enable them again.

---

### Post by Tex_Arcana on 2007-09-25
This is great for an experianced user but it hardly helps a newby that is having the same problem and doesn't know how to get to xorg.conf from the CLI.

---

### Post by zurn on 2007-09-25
> **cold_fu5ion said:**
> Horray!
Thank you so much for the help.

I did your first instruction, renaming the driver from nvidia to 

Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"


Then I got X :-)

Installed Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) which downloaded and installed nvida drivers AND! properly configured xorg.conf for me.

I <3 Ubuntu, the community really makes it great.

Thanks again :-)

Thank a lot, this is exactly what makes Ubuntu stand out, the great community. I thought I'd show my appreciation cause without these forums a lot of us would be lost :)

---

