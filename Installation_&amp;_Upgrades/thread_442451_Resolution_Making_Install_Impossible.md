---
title: "Resolution Making Install Impossible"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by nate_2k5 on 2007-05-13
ok so heres the deal, i have my computer running to a 32" toshiba LCD. i downloaded the official 7.04 release on ubuntu.com and burned it correctly to a disk. when i go to install of course it brings up the live cd and in there is the option to install. well the problem is is that the resolution will not work with my screen as the window is too big for me to see all of the buttons at the bottom to install. is there any easy way to get the resolution changed so i can see the whole box so that i can get it installed?

---

### Post by nate_2k5 on 2007-05-13
also i am using a geforce 7900 and it is the x64 edition

---

### Post by nodanero on 2007-05-13
has you tried with "ctrl alt -" to change to other video mode?

---

### Post by nate_2k5 on 2007-05-13
change to other video mode?

---

### Post by nodanero on 2007-05-13
sorry, other resolution.

Using ctrl alt - or + you rotate the differents resolutions of the X11 server.

---

### Post by snoopdoggydogg on 2007-05-13
do you know what resolution you are running it at the moment?

---

### Post by nate_2k5 on 2007-05-13
> **snoopdoggydogg said:**
> do you know what resolution you are running it at the moment?

its at 640x480, ideally it should be 1176x664 as my screen looks great at that res

---

### Post by snoopdoggydogg on 2007-05-13
if you go to system/prefrences/screen resolution you should be able to turn it up but i doubt up to your ideal reolution

---

### Post by nate_2k5 on 2007-05-13
> **snoopdoggydogg said:**
> if you go to system/prefrences/screen resolution you should be able to turn it up but i doubt up to your ideal reolution

tried it, when i click on the res box it just becomes solid, won't allow up or down changing

---

### Post by snoopdoggydogg on 2007-05-13
well im out of ideas im only 13 and still sort of a noob so   sorry...

---

### Post by nodanero on 2007-05-13
why dont you try with the hotkeys that i said?

It Will let you install the system and then you with the first start you must  configure your graphics card and screen.

---

### Post by nate_2k5 on 2007-05-13
> **nodanero said:**
> why dont you try with the hotkeys that i said?

It Will let you install the system and then you with the first start you must  configure your graphics card and screen.

i did try them, didn't work.

---

### Post by thetejon on 2007-05-13
I had to set my screen so that the panel at the bottom auto-hid itself, and the panel at the top was on the left side rather than at the top, but I managed to get the forward/back buttons on screen.  If you right click the panel you can adjust the options.

---

### Post by SkotsmanU on 2007-05-13
Im having the same problem I cant change my resolution settings. Im running a 19 inch Viewsonic and the resolution is stuck on 640x480. im using onboard nvidia video. Im a newbie. this is the only issue I have with Ubuntu right. Please help me out. Thanks
:guitar:

---

### Post by Neuralgia on 2007-05-14
on your terminal you should type this:

> sudo dpkg-reconfigure xserver-xorg

A windos will pop, letting you reconfigure your xorg file.

You shoul have ALL of yor monitor specs, specially the vertical and horizontal rates (No manual? goolge for specs, NOT only for the refresh rate, but fer the vertical and horizontal values)

At one point, there is an option to set your resolution, and your monitor specs... type them and continue.

After all that, reboot (CTRL+BCKSPC should do tha trick), and voila.

Sometimes, a regular restart is prefered.

PS: remember to get your graphics card driver installed also, without this, your stuck w/crappy resolution

---

### Post by SkotsmanU on 2007-05-14
Thank you so much **Neuralgia** worked well.

:guitar:

---

### Post by Neuralgia on 2007-05-14
glad it worked... wonder if it helped someone else?

---

### Post by md5hash on 2007-05-19
it didnt work ..

ubuntu@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070519065307

---

### Post by ggwood on 2007-06-21
I had a similar problem.  I would highly recommend either making the installation window accessible in 640x480 mode, or at least making an option once in the installer to change to a mode which is usable at lower resolution.  My graphics card was the issue: an Intel 845 chipset.  I knew I could try the various fixes mentioned.  I knew they might not work, but seemed promising.  Some time ago, I installed Dapper Drake on a machine in 640x480 mode, and although I could not see the whole window each time, as I recall there was a logical pattern of either one or two tabs followed by an enter which would get me through the process.  (On Feisty, I wasn't able to get past the timezone select screen.)  Post-install I could install more advanced drivers and was able to get it working.

Obviously there are bigger fish to fry.  I have no idea how hard it would be to change; I hope not very.

---

### Post by Pumalite on 2007-06-21
> **ggwood said:**
> I had a similar problem.  I would highly recommend either making the installation window accessible in 640x480 mode, or at least making an option once in the installer to change to a mode which is usable at lower resolution.  My graphics card was the issue: an Intel 845 chipset.  I knew I could try the various fixes mentioned.  I knew they might not work, but seemed promising.  Some time ago, I installed Dapper Drake on a machine in 640x480 mode, and although I could not see the whole window each time, as I recall there was a logical pattern of either one or two tabs followed by an enter which would get me through the process.  (On Feisty, I wasn't able to get past the timezone select screen.)  Post-install I could install more advanced drivers and was able to get it working.

Obviously there are bigger fish to fry.  I have no idea how hard it would be to change; I hope not very.

When I installed 7.04 I had the same problem. Not knowing better, I just removed the DVD or CD (Don't remember which), and plugged it back in 2 or 3 times until the resolution was correct and I could see all the buttons.

---

### Post by Ultra Magnus on 2007-06-21
I had the same problem on my old laptop - but all I did was increase the video memory in the bios setup and it worked... I'm not really sure what it actually did but My old laptop had an integrated graphics card so I think it just increased the amount of memory it used up.

---

### Post by Woodsy on 2007-06-22
> **thetejon said:**
> I had to set my screen so that the panel at the bottom auto-hid itself, and the panel at the top was on the left side rather than at the top, but I managed to get the forward/back buttons on screen.  If you right click the panel you can adjust the options.

Thanks thetejon...that worked a treat with my 800x600 screen.  An easy workaround.

---

### Post by tarnold on 2007-11-15
Well, none of these worked for me.   I FINALLY got it to work by walking the top toolbar to the left side - I then could JUST catch the very top of the 'Next' button and get through the install.

I am a newbie - but many doing an install are.   I spent 3 hours getting through this obviously simple error.   Almost gave up.

This is an interesting experiment.   Funny how one small item can give you a 'not ready for primetime' feeling.

Tom

---

