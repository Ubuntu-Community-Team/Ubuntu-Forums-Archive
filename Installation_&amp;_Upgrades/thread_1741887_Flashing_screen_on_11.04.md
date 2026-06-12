---
title: "Flashing screen on 11.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ~Aquatic on 2011-04-28
I've just downloaded and installed Ubuntu 11.04 (amd64) and every time I boot i get a flashing screen. I didn't have any problems at all with the LiveCD. The graphics card and my wireless adapter worked out of the box. But after the install it won't work. I can choose the OS in GRUB and then there's a purple screen. After that the screen starts flashing and I can hear the login sound.

I have tried using "nomodeset" but that didn't work either. There is no flashing, just a purple screen all the time. But it was possible to enter tty. I also tried booting the Recovery Mode but it just loads and then a pink flashing screen appears.

The graphics card is a XFX Radeon HD6870 1GB.

Any help is appreciated. :)

---

### Post by mirelon on 2011-04-28
I have the same issue - running 10.10 until today with no problems. 9 hours ago upgrade to 11.04 popped, so I upgraded. After reboot there is only purple screen and then black screen is flashing with some white-on-black loading text ("setting up xy... [OK]" and so).

Please, someone help, because now I have unusable machine ...if noone can help, I would like to know how to downgrade to 10.10 - still better than flashing screen.

---

### Post by mwedemeier on 2011-04-28
I am also having a similar problem. After upgrading my screen is mostly black after the grub screen. I get a slight flicker of color, mostly like static. I have an Nvidia card.

---

### Post by Hedgehog1 on 2011-04-28
Please do this (for all three posters above) :D :

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

p.s. **~Aquatic** - you MAY need one more setting - but this should get you most of the way there.

---

### Post by mwedemeier on 2011-04-28
Sorry for the noob question. How do I get to a terminal screen? Once I leave the grub screen, I can't see anything. This includes Recovery mode. Right after I choose the OS on the grub screen my screen goes black with static color.

---

### Post by mwedemeier on 2011-04-28
I was able to boot up under the previous linux versions (2.6.35-27-generic) option. I did what you said and rebooted again. I still get the same issue.

---

### Post by sikander3786 on 2011-04-28
Can you hear the login sound? If so, please press Ctrl + Alt + F1 at the blank or hang screen and see if the tty1 appears. If yes, login using your credentials, if it doesn't appear, from the Grub menu (you'll need to press and hold <Shift> key from Bios screen) select 'Recovery Mode' and then 'Drop to root shell'. Follow the commands below.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, capital 'X' for X11. The commands are case-sensitive. If it returns an error like file not found, no problem, proceed to the next command anyways.

```
sudo dpkg-reconfigure xserver-xorg
```

```
sudo reboot now
```

Lets hope you can see the desktop now. If you can't, we will need to see the outputs of these commands.

```
lspci | grep VGA
```

```
glxinfo | grep Vendor
```

---

### Post by mwedemeier on 2011-04-28
I am getting the start up sound. In fact, it even sounds like I can log in. 

Ctrl+alt+F1 did nothing.

 I can see the recovery option in Grub, but when I select it, it gets to "loading RAMDISK." Then I get the black screen again.

---

### Post by sikander3786 on 2011-04-28
> **mwedemeier said:**
> I am getting the start up sound. In fact, it even sounds like I can log in. 

Ctrl+alt+F1 did nothing.

 I can see the recovery option in Grub, but when I select it, it gets to "loading RAMDISK." Then I get the black screen again.
If there are multiple kernels, did you try the Recovery Mode from an older kernel?

---

### Post by mwedemeier on 2011-04-28
For some reason I am able to boot into the desktop if in the grub I press 'e' , then add the line 'nomodeset.' However, each time I reboot I have to redo this. Also the resolution is 640*480, I think. 

I tried your steps 1-3 once I got in and that did not work. 

lpsci | grep VGA 

I get:
[COLOR=#000000][FONT=Tahoma]00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GTX 460M] (rev a1)[/FONT][/COLOR] 


glxinfo | grep Vendor

I get:
[COLOR=#000000][FONT=Tahoma]The program 'glxinfo' is currently not installed.  You can install it by typing:
 sudo apt-get install mesa-utils[/FONT][/COLOR]

---

### Post by ~Aquatic on 2011-04-28
> **Hedgehog1 said:**
> Please do this (for all three posters above) :D :

```
gksudo gedit /etc/default/grub
```[COLOR=Red]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR=red]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR=red]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```***The Hedge***

:KS

p.s. **~Aquatic** - you MAY need one more setting - but this should get you most of the way there.

This worked perfectly, thank you! :)

> **mwedemeier said:**
> For some reason I am able to boot into the  desktop if in the grub I press 'e' , then add the line 'nomodeset.'  However, each time I reboot I have to redo this. Also the resolution is  640*480, I think. 

I tried your steps 1-3 once I got in and that did not work. 

lpsci | grep VGA 

I get:
[COLOR=#000000][FONT=Tahoma]00:02.0 VGA compatible  controller: Intel Corporation 2nd Generation Core Processor Family  Integrated Graphics Controller (rev 09)
 01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GTX 460M] (rev a1)[/FONT][/COLOR] 


glxinfo | grep Vendor

I get:
[COLOR=#000000][FONT=Tahoma]The program 'glxinfo' is currently not installed.  You can install it by typing:
 sudo apt-get install mesa-utils[/FONT][/COLOR]

If you want to permantly set nomodeset follow this tutorial: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mirelon on 2011-04-28
I have just resolved my case:

Booted rescue CD, mounted harddisk, checked /var/log/Xorg.0.log
There was a segmentation fault of graphic driver fglrx.

The solution in my case was remove flgrx (it was defined in /etc/X11/xorg.conf, but after renaming xorg.conf it just read another configs - flgrx was apparently default driver)
After reboot, another default driver was used (ATI Radeon) and I am able to log in again.

Conclusion: flgrx just cant bear with upgrade

---

### Post by nava69 on 2011-05-06
Hi
i installed 11.04 64bit but when im booting to ubuntu (choose 11.04 in boot loader) my screen start to flashing white and purple and i cant see any thing after that,also i tried 32bit but it had same problem
I have ATI HD6870

sory for my english

---

### Post by ~Aquatic on 2011-05-14
> **nava69 said:**
> Hi
i installed 11.04 64bit but when im booting to ubuntu (choose 11.04 in boot loader) my screen start to flashing white and purple and i cant see any thing after that,also i tried 32bit but it had same problem
I have ATI HD6870

sory for my english

Have you tried what Hedgehog suggested?

> **Hedgehog1 said:**
> ```
gksudo gedit /etc/default/grub
```[COLOR=Red]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR=red]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR=red]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```

---

### Post by ad~ on 2011-07-08
It sounds like I'm having a similar problem.
If I add the "nomodeset" line, it looks like maybe I can get in to recovery mode.  The screen turns blue and there's text, but I can't read it since everything flickers and part of the screen just looks black.

The other difference is that I haven't actually upgraded to 11.04 so I don't know why my computer is suddenly not booting.

Any more advice?

EDIT: Never mind, problem solved.
Sorry, I was being dumb.  I put "nomodeset" in the wrong place.  But after I used it to replace "quiet splash," I got to tty1 and did what Hedgehog1 said.  Then I reconfigured xserver-xorg like sikander3786 said, and now everything seems to be working.  Thanks a lot guys!

---

### Post by diandal on 2011-07-30
i have been having the same problem, after an update of drivers i could not load 11.04 

again. i have managed to get on by when it asks for log in details, at bottom of screen you 

have options to what you want to boot up, i selected ubuntu classic and am running on that

now. Didnt think i was going to be able to get it working again, for somehow linux mint 11 

was no problem, but i prefer ubuntu as its easier to change things to how i like.

---

### Post by k eleskandarany on 2012-04-09
thank you very much man @sikander3786
it worked
thanx ;)

---

### Post by shad686 on 2012-04-15
Having the same problem with 6670 series. Runs fine from the disk, but on a boot from the hdd I'm getting a flashing purple or black screen. Seems like the anwser to my problems have been posted above, but I cant even seem to get to the grub. I created a disk for 11.10, but am thinking of getting a previous version if i can't get the grub to show. Anyone got any ideas?

---

### Post by zzapper on 2013-01-15
> **Hedgehog1 said:**
> 

```
sudo vi /etc/default/grub
```[COLOR=Red]    and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

to

GRUB_GFXMODE=640x480

exit

```
sudo update-grub
``` Don't forget this: reboot is not enough
 



Worked brilliantly for us thanx. We are using toshiba flat screen tv  as monitor and could previously never see any of the boot info just got the flashing screen

---

