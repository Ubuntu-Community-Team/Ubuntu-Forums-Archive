---
title: "This installation is giving me a headache... nVidia Drivers."
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by TB2 on 2007-08-21
Hi,

I had some experience with penguins before, and even managed to install those crappy ATI drivers on my old computer, but now I've got myself a new machine with a GeForce 8800GTS. I'm using two screens on that, a 21" and a 19" and I'd like to use 1600x1200 on both of them, one at 85hz and the other one at 75hz.

I did kind a lot of research and got some bits and pieces solved, but I'm not getting any further now...

Things worth mentioning:
1. Ubuntu installed fine, but after grub there's just a black screen, no progress bar. If I press CTRL-ALT-DEL once after a while, the gdm login shows up on the *secondary* Screen. The primary one is left dark.
2. I can login, and everything works. I tried using the automatic proprietary driver thingy in Ubuntu, but it left me with a dark screen after rebooting, which I wasn't able to force away with "CTRL-ALT-DEL".
3. I went into recovery mode and back to the "nv" driver in xorg.conf, downloaded the latest driver manually, killed gdm, installed the driver from the console (which gave me an error "Unable to perform the runtime configuration check for library 'libGL.so.1" (...bla...); assuming successful installation") and I was able to start gdm directly after that with 3D acceleration enabled - and it showed up on the *primary* Screen. Great!
4. After rebooting, black screen again, no CTRL-ALT-DEL working, no Alt-F1 console. Back to recovery, back to "nv", back to seconardy screen. Installed the drivers again, played around with twinview, which also worked directly after reinstalling the drivers from within the normal login (if I install the drivers while in recovery mode, I get a runlevel1 error and after that, when I start gdm a "Failed to initialize HAL"-or-something error.)

Final problems:
1. Always a black screen while booting, no progress bar. Have to press CTRL-ALT-DEL for gdm to show up on secondary screen, then essentialy working with "nv" drivers.
2. Always a black screen when rebooting after installing the nvidia drivers, no chance to get an empty console (Alt-F1), no gdm login. Have to enable "nv" drivers in recovery to get it working again.

What I want is of course:
1. A progress bar and the primary screen acting like a primary screen... ^^
2. Working nvidia drivers
3. Last but not least, two screens working with 3D acc and high res & hz.

And as I said, I'm just not getting any further with what I collected until now :(

Can anyone help me?

---

### Post by dabl on 2007-08-21
That sounds like me on Day #2 of my Linux experience :mad:

OK, if I were you, first I would attempt to configure a plain vanilla VESA GUI, as described in the first 3 steps here :[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

Assuming that it boots to the first screen and stays there after you log in, that's _progress_! :)

If that much works, then the next thing I would do is download and install the Envy script installer from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) you want the file "envy_0.9.7-0ubuntu8_all.deb" about halfway down the page.  Download it to your desktop, then right-click it and "GDebi Install" it.

Envy will be installed in your System folder.  However, to be really safe and conservative, open a console and run it in text mode, i.e. ```
sudo envy -t
``` This will install the latest Nvidia driver -- works for about 95% of the folks who try it, so I'll cross my fingers.

HTH! :)

---

### Post by maybeway36 on 2007-08-21
All CTRL+ALT+DEL does in Linux is make your computer restart :\

---

### Post by TB2 on 2007-08-21
@ maybeway36:

Yeah, thats what I thought, too. But it does work. The screen is black, I wait until I don't hear any harddisk noise anymore, press CTRL-ALT-DEL, and a second later, there's my gdm login. Fact. ^^ As I said, I have no clue and discoverd this "feature" by accident.

@ dabl:

Thanks for your answer!

With the vesa there was no difference, then the gdm login showing up on the primary screen after CTRL-ALT-Del instead of the secondary one. I then used envy, and it worked so far, which means, that I now can reboot and press CTRL-ALT-DEL to get into gdm an after that into a working 3D accelerated Desktop.
Unfortunately I didn't get the res to 1600x1200 and TwinView worrking yet, but I guess I can solve that on my own.

But still, the problem with the non-existing progress bar and that weird CTRL-ALT-DEL remains. The screen turns black after Grub - and goes into standby - and no ALT-F1 or similar inputs can change that. Only CTRL-ALT-DEL gets it to the gdm login. And I have no clue how to solve this.

mysterious ;)

---

### Post by TB2 on 2007-08-21
Now THIS is totaly amazing:

I tried pushing some other buttons. Most of them don't do anything, but others give a "beep" on the system speaker. Iit seems like its kinda random, which buttons do beep and which don't, but they are always the same! De beeping buttons are:

Single-Keys:
~
TAB
All F-Number Buttons
Delete
Pg Up
Pg Down
Arrow Key Right
NUM 3 (With NumLock Off)
NUM 5 (With NumLock Off)
NUM 6 (With NumLock Off)
NUM 9 (With NumLock Off)

CTRL-Combinations (are even weirder):
CRTL+ Q, E, U, I, O, B, N, F, G, H, ...and most of the others. Some just don't beep

With NumLock On, none of the Num Key beep. Weird thing, that only the right arrow key beeps, and the others dont, and why does NUM 5 beep? And after pressing all those buttons, I still can push CTRL-ALT-DEL and theres my gdm login, untouched...
I don't get any of this...

edit2:
And here we are with a fabulous screenshot of my twinview. Twinview with 1600x1200 and 1280x1024 works, but if I go up to 1600x1200 on the second screen, a big part is just cut off. So the actual resolution is in fact 1600x1200, and I can see the mouse cursor, if I hover onto the black area, but if I drag a window over there, it just "goes under" the black stuff, instead of over it. And on the upper edge there's no frame refreshing, if I drag a window over there, the images just stick there instead of getting cleaned after. And the resolution while in the gdm login is 1600x1200 and 1280x1024 after a reboot. Then in gnome, the second screen turns black and I need to replace the xorg.conf with my backup to get it back again.

FUN:

[img]http://img207.imageshack.us/img207/4899/twinviewef9.jpg[/img]

---

### Post by dabl on 2007-08-21
HEY -- is that the Nvidia Settings utility I see there?

BEAUTIFUL!

OK, if you want to set your defaults, in a console window run ```
sudo nvidia-settings
``` which will bring up the utility in _S_uper _U_ser mode.  First, do "detect displays", then set the resolution and refresh rates that you want.  Finally, click the "Save to X Configuration File" button in the lower right of the panel, and this will write your settings to xorg.conf.

BTW, it is Ctrl-Alt-_Backspace_ to restart the xserver without rebooting your PC.

Enjoy!  :)

---

### Post by TB2 on 2007-08-21
(edited - clean up)

Yeah well... ;)

I tried like 30 different options and sequences of configuring them, and finally I got it working. It didn't work because I went after [this](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn) tutorial at ubuntuguide.org, where it says I should write -Option "TwinView"- and that stuff manually into xorg.conf. It never worked, no matter what I tried, alway wrong resolutions or cut-off screens. What I did, was simply loading an old backup, where only one screen was configured, no TwinView, and than only used the nVidia Utility to configure the two screens. It's amazingly handy! I remeber the Ati Tool, a horribly useless thing it was...

Compiz-Fusion running on two screens... sweet :)

I'll open another thread for the remaining problems, they haven't got much to do with this.

**If anyone needs to know how to get two screens working with the nvidia drivers, make sure you do it in this order, most of it can be googled easily:**
1. Use the "vesa drivers" and get your primary screen working at a moderate Resolution.
2. Use "envy" to install your nVidia drivers.
3. Reassure that xorg.conf is clean and that your primary screen works at a moderate resolution.
4. After that, *only* use the nVidia Tool to configure both screens as a dual screen setup. Dont try to fiddle with the xorg.conf any longer. *Merge* the additional settings into xorg.conf ii the nVidia Tool, *don't* replace it.

---

