---
title: "ne1 have feisty w/newer nvidia?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by skot on 2007-04-22
checking to see if anyone is running 7.04 "out of the box" with a newer nvidia card.
im still trying to find the reason i cant run 7.04. i have edgy running great. time after time i do a "fresh" install from the live cd.  works great from default choices.
i download feisty 2 different times. burned out 5 copies from  those 2 image files and i cant seems to get it to run right.  i've even "upgrade" from edgy and its still not good.
it freezes when on the desktop.  some times doesnt even make it past the login screen.
ive done everything the same as my other previous ubuntu installs.  i don't know why its not working right. ive done the disk defects check on the iso file several times. all being ok with the disk. its getting really frustrating.  

heres my specs but i would like to see if anyone can get it to work with my configuration.

desktop
p4 3.0ghz
1 GB ram
gforce nvidia 7900gs 256mb pci-e

thanks,
skot

---

### Post by Spr0k3t on 2007-04-22
I'm running the Foxconn 7950GT with the nvidia-fglx-new package without problems.  Are you trying to download the drivers from nVidia or are you using the package resources.

Here's what I do after a clean install. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.clean
```
With the release of the restricted drivers manager, I enable the support for the nvidia drivers and restart X using the ctrl-alt-backspace.  Once loaded, I update the fglx package to the fglx-new package.  Again, restarting x and logging back in I make a backup of the xorg.conf to xorg.conf.nvidia.new.  From there, I load the nvidia-settings manager as root and make the needed changes for my monitors.  This has worked every time I did a fresh install.  The early betas I had to use the alternate install method as the standard method would not boot the LiveCD (known bug), but the steps I took mentioned above worked every time.

---

### Post by skot on 2007-04-22
i will try this. thanks.  if i can ever make it to the terminal to do these changes.
but to confirm ubuntu desktop was very slow and freezed before making these changes?

im trying to figure out what they did with the new version to make it not work like the last.
the previous ubuntu works fine out of the box. now they make a new "better" version and you cant even run it with out messing around with it?  i thought this version was suposed to have the latest nvidia drivers in it already? i would think it would be just like the last but better not worse. as far as usability.
im totally lost in this.  can someone enlighten me on this.  i will continue to try and get this to work.
but i dont think i should have to. i think i have a very common system (p4 w/ nvidia card) and it should work without changing anything.  which brings me to believe something im doing it wrong. but i just install using all the default selections. i install ubuntu to its own 10gb hard drive.

---

### Post by skot on 2007-04-22
> **Spr0k3t said:**
> I'm running the Foxconn 7950GT with the nvidia-fglx-new package without problems.  Are you trying to download the drivers from nVidia or are you using the package resources.

Here's what I do after a clean install. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.clean
```
With the release of the restricted drivers manager, I enable the support for the nvidia drivers and restart X using the ctrl-alt-backspace.  Once loaded, I update the fglx package to the fglx-new package.  Again, restarting x and logging back in I make a backup of the xorg.conf to xorg.conf.nvidia.new.  From there, I load the nvidia-settings manager as root and make the needed changes for my monitors.  This has worked every time I did a fresh install.  The early betas I had to use the alternate install method as the standard method would not boot the LiveCD (known bug), but the steps I took mentioned above worked every time.

im sorry but im still new to linux. ive only been using it for about 4 months.
could you please help me with the commands needed to do the tasks so describe above.
like the command to backup the xorg.conf ect.  i would really appericate it.
thanks

---

