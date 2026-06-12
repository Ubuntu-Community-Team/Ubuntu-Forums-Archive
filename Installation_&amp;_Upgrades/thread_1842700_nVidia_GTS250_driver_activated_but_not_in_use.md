---
title: "nVidia GTS250 driver activated but not in use"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by hakuliu on 2011-09-12
so I've been running in a problem with ubuntu 11.04 recently, and I
figured this would be the right crowd to bother...

So as stated earlier, i'm running natty narwhal and it seems to
absolutely hate my GeForce 250GTS...This seems to be a recurring theme
for more geforce gpu's (i checked a bunch online and everyone seems to
be having troubles...thought I found no real fix)

...after I install the driver it says that the driver is activated but
not in use or something along those lines.
Everything actually works properly, including compiz-fusion and blah
blah, except when I move my window it becomes really really choppy.

I was perfectly fine with just dealing with it, but now i'm in
a game dev course, trying to get graphics-related stuffs to work, and the driver
is yet again causing problems.

Can anyone help me with getting the driver it running smoothly so i
can do some actual dev?

Please and thanks~!
Paul An

P.S. sorry for all the nvidia stuff, it seems like there's a lot of issues...but I haven't been able to find one that's working >.<

---

### Post by wadd92 on 2011-09-12
From my experiance with an Nvidia Geforce 7510/630i for my Laptop I found that the drivers provided by Linux and Ubuntu allow the driver to work with Unity but at a low screen resoloution. After removing the nvidia drivers I downloaded a driver from the Nvidia website and after a little trouble disabling the X server it has been working perfectly ever since. If you haven't I would get the drivers from NVidia. Most of the treads I found told me not to download the drivers from Nvidia but it seems they work better

Sorry I couldn't help much but provide my experiance, I am still new to Ubuntu and Linux

---

### Post by realzippy on 2011-09-12
run
```
sudo nvidia-bug-report.sh
```
and attach the file (got created in user's home folder)

---

### Post by hakuliu on 2011-09-12
I've tried installing the driver from the nvidia website, but it got all wonky and stopped booting gnome... =( but if i can't find anything else, i'll probably try that again.  I've also attached the nvidia-bug-report.log.gz here as requested.
took a look in there...looked kindda crazy XD

---

### Post by realzippy on 2011-09-12
Sorry,your log file is fine.
Drivers is running.no complains...
You could try newer driver by adding xswat,no need to install manually from nvidia website.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by hakuliu on 2011-09-12
=( i'm confused.  why else would moving my windows around make everything so choppy, then?

Additionally, when I run a really simple test benchmark for a project i've been working with SDL (a small window of a yoshi walking) it freezes all of the graphics, until certain triggers such as clicking a file makes it upgrade frame per frame...

---

### Post by realzippy on 2011-09-12
what does

```
glxspheres
```

report ?

---

### Post by hakuliu on 2011-09-12
gooood morning.

I went and installed the latest nvidia driver from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) but nothing seems to have changed.

glxspheres says command not found =(

---

### Post by realzippy on 2011-09-12
> **hakuliu said:**
> gooood morning.

I went and installed the latest nvidia driver from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) but nothing seems to have changed.

glxspheres says command not found =(

Morning!
Ok,glxspheres is part of virtualgl package....
```
sudo apt-get install virtualgl
```
Then try again.Is your card reported as OpenGL renderer?
How many frames?

Did you update apt after adding xswat and reinstalling nvidia-driver?
Does nvidia-settings now show 280.13 ?

---

### Post by hakuliu on 2011-09-12
nvidia-settings says 280.13.

also:

paul@Izanami:~$ sudo apt-get install virtualgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualgl
paul@Izanami:~$ glxspheres
glxspheres: command not found
paul@Izanami:~$ sudo apt-get install virtualgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualgl
paul@Izanami:~$ 

i'm reeeeaally confused here lol

---

### Post by realzippy on 2011-09-12
Sorry,didn't notice that virtualgl is not in the regular sources.
Also it will not fix your issue,only is a very basic benchmark.
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install virtualgl
glxspheres
```

---

### Post by hakuliu on 2011-09-12
i'm at classes right now, but i will get that benchmark to you as soon as I can!  thanks for sticking around =D

---

### Post by realzippy on 2011-09-12
Maybe you are affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/764330](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/764330)

---

### Post by hakuliu on 2011-09-12
this is exactly the same behavior that I am getting! i will look at it once I get back to my machine.  thank you!

---

### Post by hakuliu on 2011-09-12
whoa...i've been reading the bug report at class...and apparently it's a mouse-polling problem?  but funny thing is after I got the virtualgl stuffs installed (or when i came back from class, rather) it seems that all the gl stuff as well as the window-dragging is completely smooth all the sudden....i'm going to restart now and see if it's persistent or...if it's just...a fluke.

---

### Post by hakuliu on 2011-09-12
here's the output from running glxgears and glxspheres a couple of times.  it after reboot it went back to the old, boo behavior =(



paul@Izanami:~$ glxgears
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 46 requests (46 known processed) with 0 events remaining.
paul@Izanami:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: GeForce GTS 250/PCI/SSE2
1209.177115 frames/sec - 1349.441660 Mpixels/sec
1147.733063 frames/sec - 1280.870099 Mpixels/sec
1207.070045 frames/sec - 1347.090170 Mpixels/sec
1192.601784 frames/sec - 1330.943591 Mpixels/sec
1207.165132 frames/sec - 1347.196288 Mpixels/sec
1198.217037 frames/sec - 1337.210213 Mpixels/sec
1199.391479 frames/sec - 1338.520891 Mpixels/sec
1204.303317 frames/sec - 1344.002502 Mpixels/sec
1166.695552 frames/sec - 1302.032236 Mpixels/sec
1128.867582 frames/sec - 1259.816221 Mpixels/sec
1121.058051 frames/sec - 1251.100785 Mpixels/sec
paul@Izanami:~$ glxgears
35958 frames in 5.0 seconds = 7191.409 FPS
37683 frames in 5.0 seconds = 7536.475 FPS
36163 frames in 5.0 seconds = 7232.209 FPS
37233 frames in 5.0 seconds = 7446.532 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 46 requests (46 known processed) with 0 events remaining.
paul@Izanami:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: GeForce GTS 250/PCI/SSE2
1178.473308 frames/sec - 1315.176212 Mpixels/sec
1206.556707 frames/sec - 1346.517285 Mpixels/sec
1206.314205 frames/sec - 1346.246653 Mpixels/sec
1207.058538 frames/sec - 1347.077328 Mpixels/sec
1113.211764 frames/sec - 1242.344329 Mpixels/sec
^C
paul@Izanami:~$ ^C
paul@Izanami:~$ 



the behavior I see is actually quote funny!  in glxgears, the gears ONLY turn when i'm moving the mouse~!  this is possibly related to (but not the same as)  the problem I was running into while coding some SDL stuff in dev, where my yoshi sprite would only animate after I click/highlight a file in the GUI.

Additionally I do believe that this is definitely related to the bug that you linked me to, where there is some strange bug with mouse polling (although from the observed behavior of the glxgears...it seems to be exerting the opposite behavior than what was seen with compiz wobbly windows...)

Not sure EXACTLY how to six it, as I wasn't able to find what the exact fix was from that bug thread... =/ sorry...but would you be able to clarify?  (I wasn't able to find the /etc/modprobe.d/usbhid.conf...

---

### Post by hakuliu on 2011-09-13
Here's an update from trying to get this thing to work...

After reading all the potential fixes from 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/764330](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/764330) 
I tried various ways of slowing the mouse polling down when i'm on ubuntu, and finally found a fix for THAT.  now my window dragging is no longer making all the rendering choppy, etc.

HOWEVER

this does not seem to fix the problems I was having with gl and my yoshi sprite that I made in SDL.
The behavior that I see from glxgears, glxspheres, and my yoshi sprite is this (before and after the mouse fix) running any of these programs causes everything graphics related (except for mouse) to freeze and up and not redraw.

what I found amusing also is this!
I ran strace glxgears, strace glxspheres and strace ./yoshi-demo, and they all updated and redrawed smoothly!
My guess is that this is due to the fact that because Terminal is requesting to display a newline, it is causing everything to redraw all the time, while for some reason just running the gl programs blocked the redraw somehow...

Another thing to note is that 
glxspheres returns about 1203 frames/sec
and,
strace glxspheres returns about 447 frames/sec.

Obviously this is caused by the terminal trying to print out a bunch of stuff...
BUT THE INTERESTING PART IS:
gl is actually doing all the rendering...it's just my screen that's not beint updated...at all.


Okay...this is all the information I can gather for now.
This bug is starting to reeeeeaaally amuse me =D and I would really like to see the end of it!

PLEEEAASE give me suggestions of what I should do from here!

Thanks!
Paul

---

### Post by realzippy on 2011-09-13
Good morning ...
Same problem without unity,means when choosing "classic session" ?

---

### Post by hakuliu on 2011-09-13
it's not morning at all here...but rather almost 4 AM (and i'm stuck on wootoff... XD)

but I actually default on using Ubuntu Classic...I haven't actually tried it on Unity =X

---

### Post by realzippy on 2011-09-13
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

```

Hm,wondering why there are 2 device sections in xorg.conf...
You have 2 acer monitors connected,but you do not use 2 graphic cards,do you?
Don't think it is related to your problem,but to sort this out,you could create a new xorg.conf by:

```
sudo nvidia-xconfig
```
................................................
Does problem occur when using just 1 monitor?
................................................
Maybe downgrading compiz gives a hint?
Stumbled about a few posts in the past,where this solved compiz issues in 11.04...

---

### Post by hakuliu on 2011-09-13
running nvidia-xconfig still gives me the same code you mentioned above.  also it is 5am here and i'm going to sleep =P again, thank you for the input.  I really appreciate it.

---

### Post by miroi on 2011-09-13
Hi all, I have the same (or very similar) problem on 3 ubuntu machines with nVidia cards:

nvidia driver activated but not in use...says "Additional drivers" (jockey-gtk program). 

I want to make the recommended NVIDIA accelerated graphics driver , which is active,  to be used.

Experts can you help, please ?

On to of it: "nvidia-detector" says none. What to do ? I also disabled xserver-xorg-nouveau driver.

---

### Post by realzippy on 2011-09-13
@ miroi

If you don't have a problem with "moving windows" or running
OpenGL apps as OP,then I suggest to open a new thread.
Note that "driver is not in use" normally only is a jockey bug,which can be ignored.

---

### Post by hakuliu on 2011-09-13
although the double device thing led nowhere, it seems that downgrading compiz for gnome classic made everything magically work!!!

Thank you so much for your help

however, i'm kind of confused and curious why this would be the case...is there something funky going on with OpenGL for the new version of Compiz?  would you happen to know? =P

---

### Post by PsyWolf on 2011-09-14
out of curiosity, did you ever try disabling the vert refresh sync in compiz options?  That seemed to fix it for almost everyone in the launchpad bug.  Downgrading compiz might have done that as a side effect.

---

