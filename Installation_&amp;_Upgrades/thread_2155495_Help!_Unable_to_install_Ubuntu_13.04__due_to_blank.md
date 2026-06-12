---
title: "Help! Unable to install Ubuntu 13.04  due to blank screen after grub"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by xaegis on 2013-06-18
I am attempting to install Ubuntu 13.04 on a Lenovo ideapad 510y
I have changed the BIOS to legacy support and USB boot.
I get a blank screen after the first grub screen, then it finishes booting and I hear the drum sound but no video. It is using the Nvidia 750m video card which is iirc not yet supported in nuov. How can I work around this? Can I create a USB with the Nvidia binaries installed? Any help would be appreciated. 

Thanks,

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]xaegis;
You have not said, but, what results when you try and boot the liveUSB with the "nomodeset" boot parameter option ?
[/COLOR][INDENT=2][COLOR=#000000]
just a thought 

[/COLOR][/INDENT]

---

### Post by xaegis on 2013-06-18
Using "nomodeset" I was able to install. Ubuntu 13.04 and then install the propriatairy drivers for nvidia using wget.
Now I am trying to get the resolution to work properly and solve the problem that the screen freezes after login.(but Ctrl + Alt + t still gets me a terminal)

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]xaegis;

Are you certain the correct driver was obtained ?
What does the utility Additional Drivers advise for a graphics driver ? Be advised I am not running unity on my 13.04 (xfce4) ,,so not certain where that utility is located in 13.04. Try:
Software Sources -> Additional Drivers.
[/COLOR][INDENT=2][COLOR=#000000]
still try'n to help

[/COLOR][/INDENT]

---

### Post by xaegis on 2013-06-19
> **Bashing-om said:**
> [COLOR=#000000]xaegis;

Are you certain the correct driver was obtained ?
What does the utility Additional Drivers advise for a graphics driver ? Be advised I am not running unity on my 13.04 (xfce4) ,,so not certain where that utility is located in 13.04. Try:
Software Sources -> Additional Drivers.
[/COLOR][INDENT=2][COLOR=#000000]
still try'n to help
  
[/COLOR][/INDENT]

Thanks for all of your help! :) 
Because the GUI isn't working I am doing everything from command line.
I tried to load (alternately) the xswat and edgers ppa but neither of them seemed to give me a GUI uppon reboot(I might not have installed the proper packages after adding the ppa though). I was able to get the Latest NVIDIA driver loaded and almost working but it ended up just being a Square box in the center of the screen. Everything seemed to work though as I could press Ctrl + Alt + t and get to a terminal, although I dont think the HUD was coming up when I pressed the Super key.
I am trying again from a fresh install, what do you reccomend I try next.

---

### Post by xaegis on 2013-06-19
OOokkkaayyyyy. So now there is a new development. I did a fresh install of the system vanilla 13.04 and it boots to a blank screen but with the drum/login sound. I found that if I close (latch) my laptop screen and then reopen it I have a full GUI available and everything works perfectly when it returns from sleep. Any ideas on this?

---

### Post by Bashing-om on 2013-06-19
[COLOR=#000000]xaegis; Hey...
Depends on install method and what you are trying to install. For a GUI one must have "xorg" installed;
```
dpkg -l xorg
```
Then is the desk top environment started and loaded ? Are we talking unity ?
```
 sudo service lightdm start
``` 
Maybe there are hardware issues beyond "nomodeset"
[/COLOR][https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
[http://ubuntuforums.org/showthread.php?t=1743535&page=108](http://ubuntuforums.org/showthread.php?t=1743535&page=108)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
These because hardware compatibility solutions can be tough to isolate.

where there is a will there is a way;[INDENT=6]will keep plugging away

[/INDENT]

---

### Post by xaegis on 2013-06-19
it is one of the Haswell chips and is using the INTEL video instead of the discreet nvidia 750M card apparently.

---

### Post by arpanaut on 2013-06-19
Bumblebee maybe?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=bumblebee&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=bumblebee&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Bashing-om on 2013-06-19
[COLOR=#000000]xaegis ;
Intel + Nvidia = BumbleBee as a general rule, BB is a work in progress and a year later looks good !

@[/COLOR][COLOR=#000000]arpanaut; Good call !
[/COLOR][INDENT=2][COLOR=#000000]
where solutions exist there are no problems

[/COLOR][/INDENT]

---

### Post by xaegis on 2013-06-20
ok, so should I install the xswat or edgers ppas as well?

---

### Post by Bashing-om on 2013-06-20
[COLOR=#000000]xaegis; Hey

I have no experience with dual graphics cards or BumbleBee directly...What I "assume" is install the BB ppa, and BB will take care of all drivers required. Google is our friend, and should provide the info to install and use BB. There are several threads on this forum in respect to BumbleBee that will be worth while to investigate.
[/COLOR][INDENT=2][COLOR=#000000]
long on want-to, short on know-how

[/COLOR][/INDENT]

---

