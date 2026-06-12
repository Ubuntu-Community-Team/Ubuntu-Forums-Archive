---
title: "Booting from Live CD with Nvidia 7800 GT"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by s3amonster on 2007-03-08
Hey all, I've noticed that there seems to be a problem with people who own Nvidia GeForce 7800GTs, so in case someone has problems and can't find a solition--I had to patch this help together by myself, so anyone with more experience with ubuntu, please feel free to add anything:

So I did some browsing around and I found the solution (that worked for me, anyway). Apparently it's a problem with the graphics card. The 7800 has some incompatibility with the basic nvidia driver that comes on the CD. Thus, to boot from the live CD...

- press F6 at the first menu screen.
- delete "quiet-splash" and replace it with break=bottom
- Start the live CD, let stuff run and load, and then when the prompt appears, type

```
chroot /root nano /etc/X11/xorg.conf
```

- scroll down to one of the sections entitled "Device" that has your graphics card listed. Below it should be "Driver" and next to it "nv". This is the default nvidia driver on the Live CD, but apparently it has problems with our precious 7800 GTs. Replace "nv" with "vesa"

-then hit control + O
-hit enter
-and hit control + X

- at the prompt, type:

```
exit
```

The live CD should work now.

You might also run into the same problem after you've installed Ubuntu, and thus...

After you've installed ubuntu, the log-in screen will appear scrambled. Hit control alt F1. If this gives you a scrambled screen as well, reboot and select "Recovery Mode" from the bootloader.

Log in from the bootloader terminal then type:

```
sudo nano /etc/X11/xorg.conf
```

This is, essentially, the same thing you browsed before, so scroll down to the nvidia device and change the "nv" to "vesa" again. control + O, enter, and control + X to exit.

At the prompt, type:

```
sudo /etc/init.d/gdm restart
```

Now you'll log in with the vesa drivers, but since they kinda suck and will give you a big performance hit, you'll want to go ahead and install an nvidia driver.

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

There's also a program called envy which installs everything for you, found [here.]("http://www.albertomilone.com/nvidia_scripts1.html")

At the original time that I posed this, there was some security hole in the nvidia drivers, however they've since (i.e. today) released new ones, which I'm HOPING have fixed this hole. I'm not sure if envy fixes it for you or not but to fix it bring up a terminal and type

```
sudo gedit /etc/X11/xorg.conf
```

Once again, go to the device section and, above the line that says "nvidia" add this line:

```
Option "RenderAccel" "false"
```

Then log out and press control-alt-backspace. Apparently there's a slight performance hit but I guess it's better than a security hole. Not sure what exactly what it (the security hole) is.

And I'm not one to steal the credit, so I got some of this from this guy ([http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357](http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)). I patched together the rest of the stuff in here though (mainly by looking at peoples' problems with the ATI X800 series and tinkering around).

Hope it works.

---

### Post by teaker1s on 2007-03-09
bump as others will be interested in this

---

### Post by grey_1 on 2007-03-10
Thanks for posting this, you saved my sanity! After following this I was able to install the 9755s no problem, both cards are detected fine and performance is good.

Here's hoping it stays that way.:)

---

### Post by jksigurd on 2007-03-11
Wow thanks a lot for the workaround.  I searched all day for information on this problem and noone seemed to know what was causing it.  Is there anyway to get this information passed on to the right people?  I'm pretty new to Linux.

---

### Post by HumbleGod on 2007-03-12
THANK YOU! I feel somewhat validated, I was afraid this was just me. Strangely enough the CD for 6.06 works fine for me without all these shenanigans; it's only 6.10 that gives me trouble.

---

### Post by kwaichangkang on 2007-03-14
Dude, you saved my life!  I thought my system was seriously bugging out.  I installed 6.10 on a really old system and then wanted to install it on my main system.  I got all cocky thinking that my Dual Core, 2gb RAM system was going to EAT UP Ubuntu!  Then i got humbled at installation when I too encountered the 'scrambled' install screen (I too have a 7800 GT)

This workaround cleared up everything.  Your the man!

---

### Post by liveforfunnow on 2007-03-14
I have a 7800 GT, and this problem has plagued me. fantastic thread!

for those of you who don't mind installing proprietary drivers, i found it easier to:

1. boot 6.06 liveCD in Safe Graphics Mode
2. Install system as desired
3. When install is complete, boot to recovery mode
4. do the following:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-glx

then

sudo nano /etc/X11/xorg.conf

scroll down and change "nv" to "nvidia"

5. reboot, and choose the topmost GRUB entry. Ubuntu should boot just fine.

just my $.02, but this works for me every time.

---

### Post by bmccullo on 2007-03-21
This information was extremely helpful. I was pulling my hair out searching around for answers. I figured it was an incompatibility between my 7800gt and the video drivers, but I'm pretty new to linux so I really didn't know what to do.

Everything is up and running just fine, now. Thanks.

---

### Post by rizzo on 2007-03-21
> **liveforfunnow said:**
> I have a 7800 GT, and this problem has plagued me. fantastic thread!

for those of you who don't mind installing proprietary drivers, i found it easier to:

1. boot 6.06 liveCD in Safe Graphics Mode
2. Install system as desired
3. When install is complete, boot to recovery mode
4. do the following:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-glx

then

sudo nano /etc/X11/xorg.conf

scroll down and change "nv" to "nvidia"

5. reboot, and choose the topmost GRUB entry. Ubuntu should boot just fine.

just my $.02, but this works for me every time.

I have a 7600GS, and even with booting into 'safe graphics' mode with 6.10, it still wouldn't work.  Text mode was even jacked up, so I couldn't do anything.  

The fix listed at the top of this thread was the only thing that worked for me.  Thanks again for posting!

---

### Post by liveforfunnow on 2007-03-21
> **rizzo said:**
> I have a 7600GS, and even with booting into 'safe graphics' mode with 6.10, it still wouldn't work.  Text mode was even jacked up, so I couldn't do anything.  

The fix listed at the top of this thread was the only thing that worked for me.  Thanks again for posting!

yeah, i've had problems with 6.10 and Safe Graphics Mode. I use 6.06 in Safe Graphics Mode, and it works every time. 

glad you were able to get up and running!

---

### Post by ichimeno on 2007-03-21
does this also work with a Nvidia 6800?

---

### Post by liveforfunnow on 2007-03-21
> **ichimeno said:**
> does this also work with a Nvidia 6800?

i don't see why not. give it a shot, and let us know how it works out.

---

### Post by ichimeno on 2007-03-21
ok thnx i shall.:)

---

### Post by liveforfunnow on 2007-03-23
update:

I tried Feisty Fawn Herd 5 LiveCD/Instal in Safe Graphics Mode last night - and it worked like a charm! I was able to install and then boot to a GUI, and install the nvidia drivers with a simple

```

sudo apt-get install nvidia-glx
```

I didn't even have to manually edit xorg.conf! The Restricted Drivers Manager allowed me to enable the nvidia drivers. I logged out, Ctrl+Alt+Backspace'd, and logged back in. 1680x1050! No problems!

Hoorah to Feisty!

---

### Post by xi_Slick_ix on 2007-04-20
Anyone have any experience / idea if this fix would be compatible w/ an Nvidia 6600 (256mb - AGP 8x) card?  I've been battling some similar issues, and have had no luck or response yet to my questions (which leads me to believe i might be hopeless).  

If anyone has some ideas i'm more than interested

-ThAnX

---

### Post by xi_Slick_ix on 2007-04-27
All right this is incredibly odd....   Just purchased a new Samsung LCD  (SyncMaster 941BW) and somehow through the magic of Ubuntu, this display works! (the CRT did not).  I am somewhat dumbfounded as to how a change of viewing device can bring this about, but i am certainly not complaining!

---

### Post by dannymichel on 2007-05-17
> **s3amonster said:**
> Hey all, I've noticed that there seems to be a problem with people who own Nvidia GeForce 7800GTs, so in case someone has problems and can't find a solition--I had to patch this help together by myself, so anyone with more experience with ubuntu, please feel free to add anything:

So I did some browsing around and I found the solution (that worked for me, anyway). Apparently it's a problem with the graphics card. The 7800 has some incompatibility with the basic nvidia driver that comes on the CD. Thus, to boot from the live CD...

- press F6 at the first menu screen.
- delete "quiet-splash" and replace it with break=bottom
- Start the live CD, let stuff run and load, and then when the prompt appears, type

```
chroot /root nano /etc/X11/xorg.conf
```

- scroll down to one of the sections entitled "Device" that has your graphics card listed. Below it should be "Driver" and next to it "nv". This is the default nvidia driver on the Live CD, but apparently it has problems with our precious 7800 GTs. Replace "nv" with "vesa"

-then hit control + O
-hit enter
-and hit control + X

- at the prompt, type:

```
exit
```

The live CD should work now.

You might also run into the same problem after you've installed Ubuntu, and thus...

After you've installed ubuntu, the log-in screen will appear scrambled. Hit control alt F1. If this gives you a scrambled screen as well, reboot and select "Recovery Mode" from the bootloader.

Log in from the bootloader terminal then type:

```
sudo nano /etc/X11/xorg.conf
```

This is, essentially, the same thing you browsed before, so scroll down to the nvidia device and change the "nv" to "vesa" again. control + O, enter, and control + X to exit.

At the prompt, type:

```
sudo /etc/init.d/gdm restart
```

Now you'll log in with the vesa drivers, but since they kinda suck and will give you a big performance hit, you'll want to go ahead and install an nvidia driver.

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

There's also a program called envy which installs everything for you, found [here.]("http://www.albertomilone.com/nvidia_scripts1.html")

At the original time that I posed this, there was some security hole in the nvidia drivers, however they've since (i.e. today) released new ones, which I'm HOPING have fixed this hole. I'm not sure if envy fixes it for you or not but to fix it bring up a terminal and type

```
sudo gedit /etc/X11/xorg.conf
```

Once again, go to the device section and, above the line that says "nvidia" add this line:

```
Option "RenderAccel" "false"
```

Then log out and press control-alt-backspace. Apparently there's a slight performance hit but I guess it's better than a security hole. Not sure what exactly what it (the security hole) is.

And I'm not one to steal the credit, so I got some of this from this guy ([http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357](http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)). I patched together the rest of the stuff in here though (mainly by looking at peoples' problems with the ATI X800 series and tinkering around).

Hope it works.

I get ```
kernel panic - not syncing: vfs unable to mount root fs on unknown-block(8,1)
```

---

### Post by dannymichel on 2007-05-19
Bump?

---

### Post by dannymichel on 2007-05-21
> **dannymichel said:**
> I get ```
kernel panic - not syncing: vfs unable to mount root fs on unknown-block(8,1)
```
Please help...

---

### Post by Pupp on 2008-05-05
I tried that, and when I load the xorg.conf file, I don't get anything in the file.. just empty. 

Any suggestions?

Kinda hard to edit a blank file. Did I miss something?

:confused:

---

### Post by lswest on 2008-05-05
> **Pupp said:**
> I tried that, and when I load the xorg.conf file, I don't get anything in the file.. just empty. 

Any suggestions?

Kinda hard to edit a blank file. Did I miss something?

:confused:

Make sure the path is right: /etc/X11/xorg.conf (linux is case-sensitive, the X must be capitalized).  Otherwise, make sure you didn't typo anywhere along the way, it's happened to me a few times ;)

---

