---
title: "nano xorg - how to edit?"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by nparayo on 2008-06-26
This is the image i get when i type in 

nano xorg

[[IMG]http://img291.imageshack.us/img291/3950/26062008106sq4.th.jpg[/IMG]](http://img291.imageshack.us/my.php?image=26062008106sq4.jpg)


there is no text its blank, so there isnt anything for me to edit, i want to change to vesa driver as my display messes up and fades into blank:
[[IMG]http://img522.imageshack.us/img522/6812/25062008103rn5.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=25062008103rn5.jpg)

also when can i press F6 to enter safe graphics mode? people have submitted this as a solution but all throughout boot sequence i pressed F6 and nothing differs.

I am trying to run 8.04, installed using alternate CD

---

### Post by tamoneya on 2008-06-26
you need to type```
sudo nano /etc/X11/xorg.conf
```Then do you editting.  When you are finished hit ctrl-x and then hit y to save.

---

### Post by nparayo on 2008-06-26
hi thanks i tried adding Driver "vesa" i wasnt sure where so i put it were i though necesary and it still does not work should i even replace ALL Driver instances with vesa including keyboard?
e including:

Driver "kdb"
Driver "mouse"
Driver "synaptics"

i would just try but im afraid it might make the devices useless, then i wouldnt be able to use the keyboard?

heres what i did do:
[[IMG]http://img241.imageshack.us/img241/6724/26062008107ni9.th.jpg[/IMG]](http://img241.imageshack.us/my.php?image=26062008107ni9.jpg)

or any other solution?

---

### Post by logos34 on 2008-06-26
it might be better to run the interactive xorg editor:

sudo dpkg-reconfigure xserver-xorg

select 'vesa' from list of graphics drivers and proceed.  You can probably accept defaults for everything

---

### Post by nparayo on 2008-06-26
sudo dpkg-reconfigure xserver-xorg

only gives me the options to edit keyboard settings and thats it, this is the final screen and sends me back to command line:

[[IMG]http://img80.imageshack.us/img80/8441/26062008108xy8.th.jpg[/IMG]](http://img80.imageshack.us/my.php?image=26062008108xy8.jpg)

---

### Post by lemuriaX on 2008-06-26
Hi.

When editing config files, always should make a backup first - like this example:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Then if you lost your Xwindows you could navigate there to /etc/X11 directory with command line and open the backup copy and save it as xorg.conf to get back to what you had before making any edits.

---

### Post by nparayo on 2008-06-26
hi yes thats fine i have restored the original file but the problem still remains even wen i try to do it interactively only keyboard options are given.

in fact i did the interactive version before i attempted to do it myself so i dont think ive messed anything up.

---

### Post by logos34 on 2008-06-26
hmm, you're right, just keyboard options...killing xserver (ctrl+alt+f1) doesn't make a diff...maybe my (your?) enabled graphics driver is blocking it.  Try rebooting into recovery mode and rerun it there

---

### Post by nparayo on 2008-06-26
I went into recovery mode and im presented with another three options:
i chose the second: drop to root shell prompt

typed 

sudo dpkg-reconfigure xserver-xorg

same result :(

---

### Post by logos34 on 2008-06-26
I guess you have to disable the restricted graphics driver altogether before you can run that program...They must have changed it for hardy because I was able to before.

Just go back to manually editing xorg.conf

---

### Post by nparayo on 2008-06-26
ok thats fine but do you know exactly where i need to edit because it doesnt give me much options there either i posted a screencap of what i did do i even changed all the instaces of 

Driver "kdb"
Driver "mouse"
Driver "synaptics"

to Driver "veso"

and added extras where there werent:
[[IMG]http://img241.imageshack.us/img241/6724/26062008107ni9.th.jpg[/IMG]](http://img241.imageshack.us/my.php?image=26062008107ni9.jpg)

---

### Post by avtolle on 2008-06-26
Try```
gksudo displayconfig-gtk
```to select your monitor and set your resolutions. Also, click on the graphics tab to see if the correct graphic card is being detected, and, if not, select the correct one if available in the list.

---

### Post by nparayo on 2008-06-26
this gives me this message:

(gksudo:4499): Gtk-WARNING **:cannot open display:

i tried that in recovery mode, and after screen blackout, CTRL + ALT + F1 still same message

---

### Post by avtolle on 2008-06-26
In recovery mode, has there been a menu appear that has three items on it, one of which is something like Fix X ? If so, have you selected that?
From terminal, you might try```
sudo xfix
```to see if it will run that utility (I believe that is the correct command).

---

### Post by mali2297 on 2008-06-26
> **nparayo said:**
> hi thanks i tried adding Driver "vesa" i wasnt sure where so i put it were i though necesary and it still does not work should i even replace ALL Driver instances with vesa including keyboard?
e including:

Driver "kdb"
Driver "mouse"
Driver "synaptics"

i would just try but im afraid it might make the devices useless, then i wouldnt be able to use the keyboard?


You should only change the driver entry in *Section "Device"*; leave everything else as it is. 

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

```

Also, post the output of
```

lspci | grep VGA

```

---

### Post by nparayo on 2008-06-26
yes i have tried that before it has given me the best result so far it gives  me a quick glimpse of this before the screen fades off a blacks out again its not selectable it comes up for an instance the screen just has not refreshed and eventually fades away:
[[IMG]http://img116.imageshack.us/img116/7240/26062008109zw1.th.jpg[/IMG]](http://img116.imageshack.us/my.php?image=26062008109zw1.jpg)

---

### Post by logos34 on 2008-06-26
Does anyone know why you can't choose a new video driver in dpkg-reconfigure xserver-xorg anymore?  This is the first time I've run it since feisty.  When did they change it?

---

### Post by nparayo on 2008-06-26
I really appreciate the support

mali how do i perform this part

```

lspci | grep VGA

```

i have no idea do i just write it below: Driver "vesa"

---

### Post by Pumalite on 2008-06-26
Hi logos34. I think since Hardy

---

### Post by mali2297 on 2008-06-26
> **logos34 said:**
> Does anyone know why you can't choose a new video driver in dpkg-reconfigure xserver-xorg anymore?  This is the first time I've run it since feisty.  When did they change it?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)

---

### Post by mali2297 on 2008-06-26
> **nparayo said:**
> I really appreciate the support

mali how do i perform this part

```

lspci | grep VGA

```

i have no idea do i just write it below: Driver "vesa"

That line should **not** be added to xorg.conf but entered at the command line prompt. It will tell us your graphics card.

---

### Post by avtolle on 2008-06-26
> **nparayo said:**
> I really appreciate the support

mali how do i perform this part

```

lspci | grep VGA

```

i have no idea do i just write it below: Driver "vesa"
No, you enter that command in the terminal. Do not put it in your /etc/X11/xorg.conf file.

---

### Post by nparayo on 2008-06-26
hi reason for delayed reply ive been trying

lspci | grep VGA

but returns:

bash: 1spci: command not found

just to be sure | is the key next to the Z key right GB keyboard using shift?

ohh and trying the Driver "vesa", it improved boot, now i get the drum beat as the screen fades to blackout.

---

### Post by logos34 on 2008-06-26
> **mali2297 said:**
> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)

so it's a bug, or do we now have to use displayconfig-gtx in Hardy?

back to the launchpad page to read the whole thing...

---

### Post by nparayo on 2008-06-26
I see that this is a new version of Ubuntu, i remember about 1.5 years ago i had ubuntu running on an identicle laptop fine, i was wondering why i was having problems this time round is it possible i can install the older one and perform an upgrade would this keep the settings?

well thanks for the help do reply ill check in the morning! and ill keep at it.

---

### Post by Pumalite on 2008-06-26
Generally, yes.

---

### Post by logos34 on 2008-06-26
omg, why did they change it?  (displayconfig-gtk is a gui app---lot of good it does you if you can't start the x server!).  dpkg-reconfigure worked just fine

sometimes I wonder about ubuntu...

---

### Post by avtolle on 2008-06-26
From what I've been reading, this is not limited to Ubuntu; other distros are, as I understand it, moving to the "new, improved, bullet-proof X", which it is not.

As to how to get into the displayconfig-gtk app when graphics aren't working, yeah, I don't know myself. Perhaps a boot into safe-graphics mode is contemplated by those who think that they have a better way, from which this might be accomplished. Or, in recovery mode, running xfix (I think that's the name of it) is supposed to take care of things? Dunno, but it shore is inconvenient there.

---

### Post by lemuriaX on 2008-06-26
> **nparayo said:**
> hi reason for delayed reply ive been trying

lspci | grep VGA

but returns:

bash: 1spci: command not found

just to be sure | is the key next to the Z key right GB keyboard using shift?

ohh and trying the Driver "vesa", it improved boot, now i get the drum beat as the screen fades to blackout.

looks like you may have the number 1 there instead of the letter l

try cutting and pasting the code:

```
lspci | grep VGA
```

---

### Post by logos34 on 2008-06-26
> **avtolle said:**
> From what I've been reading, this is not limited to Ubuntu; other distros are, as I understand it, moving to the "new, improved, bullet-proof X", which it is not.

As to how to get into the displayconfig-gtk app when graphics aren't working, yeah, I don't know myself. Perhaps a boot into safe-graphics mode is contemplated by those who think that they have a better way, from which this might be accomplished. Or, in recovery mode, running xfix (I think that's the name of it) is supposed to take care of things? Dunno, but it shore is inconvenient there.

For a test, I backed up xorg.conf then altered it so the machine would choke loading the xserver.  Then (since I have a nvidia card) I ran sudo nvidia-xconfig at the console prompt, which generated a new xorg file, but even then the graphics still didn't start! So if it had been for real I'd have been, well, SOL.  I think the only thing left to do would be to run the live cd, download the restricted drivers, configure video with nvidia-settings, then copy the saved settings in xorg.conf file to the one on the hard drive

---

### Post by Pumalite on 2008-06-26
xfix will get you a basic xserver going.
'The new Xorg is supposed to be all nice and hotplugable, but dpkg-reconfigure xserver-xorg is no more. /etc/X11/xorg.conf is also now very barebones. This is for the hotplugability. The correct way to configure this new version of X is with the xfix command. Changing resolution is done on the fly with xrandr.'

---

### Post by nparayo on 2008-06-27
> **lemuriaX said:**
> looks like you may have the number 1 there instead of the letter l

try cutting and pasting the code:

```
lspci | grep VGA
```

Hi here it is

```
00:02. VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controler] (rev 04)
```

if it helps I got this information using dxdiag when I had windows running:

Fujitsu Siemens S6010
Pentium 3 CPU - M
1000MHz
502MB RAM

Intel 82830M Graphics Controller
Total memory: 48MB

BIOS: PhoenixBIOS 4.0 Release 6.0

---

### Post by nparayo on 2008-06-27
> **Pumalite said:**
> xfix will get you a basic xserver going.
'The new Xorg is supposed to be all nice and hotplugable, but dpkg-reconfigure xserver-xorg is no more. /etc/X11/xorg.conf is also now very barebones. This is for the hotplugability. The correct way to configure this new version of X is with the xfix command. Changing resolution is done on the fly with xrandr.'

Hi i tried 

sudo xrandr

it says

Cant open display

xfix i can access by going to recovery mode and that did not work

either way im installing 7.10 at the moment, hopefully i can perform an upgrade and things should be ok.

---

### Post by nparayo on 2008-06-29
hey guys I actually got it working this is how i did it:

Download and Install Ubuntu 7.04
perform updates on 7.04
then update to 7.10
Running 7.10 update to 8.04

now im running 8.04 Hardy Heron and after some messing about ive got wireless working as well, what hassle but im there!

---

### Post by davlaw2000 on 2008-08-19
Hi guys I hope you can help. I have the same laptop as the person who started this thread - it is a Fujitsu Siemens S6010. I have been experiencing exactly the same problems too, and have even tried installing the same older version of Ubuntu to see if that worked. I am sorry to say that I was unable to install version 7.10! I got a lot of promising messages, then I heard the fanfare, but then all I got was a blank screen :-(

As an experiment I tried installing Xubuntu 8.04 but I got the same problems as those first reported - corrupt screens, stripey screens which seem to fade to black. 

I would love to put Ubuntu onto my machine but have so far failed miserably. Any suggestions?

---

### Post by nparayo on 2008-08-19
> **davlaw2000 said:**
> Hi guys I hope you can help. I have the same laptop as the person who started this thread - it is a Fujitsu Siemens S6010. I have been experiencing exactly the same problems too, and have even tried installing the same older version of Ubuntu to see if that worked. I am sorry to say that I was unable to install version 7.10! I got a lot of promising messages, then I heard the fanfare, but then all I got was a blank screen :-(

As an experiment I tried installing Xubuntu 8.04 but I got the same problems as those first reported - corrupt screens, stripey screens which seem to fade to black. 

I would love to put Ubuntu onto my machine but have so far failed miserably. Any suggestions?

Hi there i have push email so i got here quick. You need to in back to  ubuntu 7.04! Download the alternate cd, once installed, use an ethernet cable for the internet, and perform the updates using the update manager within ubuntu, once those are done, perform the upgrade using the same tool. Then just keep doing the same for each version until you get to 8.04. This does take ages! The reason for this is ubuntu doesnt like old hardware so they (try to) stop supporting them.

---

