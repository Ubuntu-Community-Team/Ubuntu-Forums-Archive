---
title: "Installing Creative Live cam Vista IM"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by bex552 on 2006-09-27
Hi guys just wandering if anyone can help me because im pulling my hair out over this webcam. 
I have inserted the disc that came with the webcam and have done everything it tells me. It asks me to insert the webcam. After inserting the webcam it says something along the lines of - we cannot open installer for image please contact vendor.

Any ideas? Im a bit of a novice so if u guys can help me can it be explained easy please :D

---

### Post by vyruss on 2006-11-13
> **bex552 said:**
> Hi guys just wandering if anyone can help me because im pulling my hair out over this webcam. 
I have inserted the disc that came with the webcam and have done everything it tells me. It asks me to insert the webcam. After inserting the webcam it says something along the lines of - we cannot open installer for image please contact vendor.

Any ideas? Im a bit of a novice so if u guys can help me can it be explained easy please :D


Are you asking a question about the operating system Windows Vista in the forums for the operating system Ubuntu? Or am I mistaken?

---

### Post by bart7simpson7 on 2006-12-02
You are totally wrong. This is the name of the webcam. I have the same model and I haven't managed to get it to work in ubuntu :(.

---

### Post by fidolip on 2006-12-05
Creative prepared its products for Windows only I'm afraid. We have to wait till someone (I mean some Linux-knowing-smart-lad) writes drivers for ubuntu.

---

### Post by dneary on 2007-03-23
I found this page, which suggests that the camera works with the ov51x driver (or some variant). I still haven't got it working, though. [http://www.qbik.ch/usb/devices/showdev.php?id=3960](http://www.qbik.ch/usb/devices/showdev.php?id=3960)

Dave.

---

### Post by albox on 2007-03-30
Hi,
I bought this webcam today and I'm also interested to get it to work on Ubuntu.
Did somebody manage to make it work ?
Thanks

---

### Post by sirclaudio on 2007-04-10
I also have one of those. I've emailed creative asking for drivers, their answer:

> 
Linux isn't a comercial OS, no company makes drivers for this platform.
Our products are only compatible with windows.


In others words, wait for the ovcam/ov51x-jpeg people to finish their drivers because creative doesn't care for linux customers...

---

### Post by alfonso.acosta on 2007-04-12
Support for this camera is on its way. 

The driver is already usable but causes a big load and noticeable latency, please [ [COLOR="Blue"]test and report back[/COLOR]]("http://www.rastageeks.org/ov51x-jpeg/index.php/Testing_IM_Live_Support") in order to get a better driver as soon as possible.

---

### Post by skrimpy on 2007-04-26
I have this webcam as well and I'm having trouble getting it working.  I followed instructions for installing the ov51x-jpeg drivers on this page: [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall) 

I installed from the debian package and didn't seem to get any errors.  However, I'm still getting no response whatsoever from my webcam. 

I am very confused about what to do and where to look next.  All the webcam instructions I read are cryptic and hard to understand for me :(

I get this output if I try and run xawtv:

```

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
```

---

### Post by BjoernVDM on 2007-05-14
I just got this cam, and also followed the instructions from the rastageek site. 

I do have it working - somehow.


hehe, see the picture:

Better than nothing...black and white though, and in three small stripes

Forget it. Camorama doesnt't support this driver. I get a perfect picture in VLC, with vlc v4l:/dev/video0

---

### Post by TomBentley on 2007-05-31
Works for me, at least with Ekiga. I did something like the following:


```
sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.20-16-386
make
sudo make install
sudo modprobe ov51x-jpeg
```

---

### Post by freeride on 2007-06-03
Tom, thanks a lot! I've just bought this web cam and I've been immediately able to get it work!!!
Maybe the driver could be further optimized, but at least I can use it without getting back to windows.

Thanks again!

---

### Post by dimas869 on 2007-07-01
Hello,
i did installed the ov51x driver with the rastageek web page instructions and the cam works good on ekiga and xawtv, the picture display is cut in half on gyache and in any video web page chat using flash player the software (flash player) recognized the cam but i cant have any picture display, so i believe some how the transmission is block (output)...so what should i do to have it work on flash player? any idea?
thanks for your help!!!

Dimas

---

### Post by skrimpy on 2007-07-02
> **TomBentley said:**
> Works for me, at least with Ekiga. I did something like the following:


```
sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.20-16-386
make
sudo make install
sudo modprobe ov51x-jpeg
```

This worked like a charm for me.  Restarted my system after inputting above code into a terminal and ekiga picked up my cam right away.  Thanks!

---

### Post by yknivag on 2007-07-31
Thank you. Thank you!

After months of trying my webcam now works. :o)

Well, after a fashion, it works in Ekiga. It doesn't work in Xine nor does it work in a flash based chatroom (flash says I have no cam!) :o(

Any one got any ideas on the flash thing?

---

### Post by Zulius on 2007-09-28
In my newly installed kubuntu 7.04 running a 2.6.20-16-generic kernel it still doesn't work.
I've followed the nice rastageek guide and the ov51x-jpeg module correctly loads when I plug the camera into the usb hub; additionally the camera LED it's flashing for a while at this stage.

Camorama, VLC, xawtv, kopete & ekiga are giving the same answer:  no /dev/video0 exist!

I've tried to create the device manually using mknod (sudo mknod /dev/video0 c 81 0) and the response is always the same:----device does'nt exist.....but it's there.....I CAN SEE IT INSIDE /dev DIRECTORY!!!!

Ok, try to change its permissions (sudo chmod 777 /dev/video0).....same result: no device exist!
Tried to use MAKEDEV script.....it creates tonnes of devices----video0 included---but inside /dev/.static/dev....k, try to move/copy it:.....error: could not read /dev/.static/dev

Anyhow, when created manually at next reboot the device disappears....I've read this is normal.

I ran udevmonitor and saw it creates some devices when I plug the cam in such as /dev/usbdev47-ep00 & usbdev47-ep81....tried to use them with xawtv:     no /dev/video0 exist............AAAAARRRRGHHHHHH!!!

This is driving me crazy!!!!!
Any suggestions?

Thanks 
Francesco

---

### Post by Zulius on 2007-09-30
IT' DONE!!!!!!!!!!!!!!!!!

just don't plug it into a usb Hub but directly into a usb port on your Computer.
Bye, bye 

Francesco

---

### Post by halitech on 2007-11-11
I believe this is the same webcam I just bought and I just plugged it in (in a hub) and went to aMSN and it worked

---

### Post by schlox on 2007-11-25
> **TomBentley said:**
> Works for me, at least with Ekiga. I did something like the following:


```
sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.20-16-386
make
sudo make install
sudo modprobe ov51x-jpeg
```



There is a problem with the rastageeks.org, Does anyone have an alternative source?

---

### Post by aerorahul on 2007-11-30
I followed the instructions on the previous post. All went smoothly, ie. no errors what so ever. But the green LED on the cam still doesnot blink, ergo the cam does not work. What am I missing. I tried loading skype and ekiga and they say no devices found for the video :( Help, someone , anyone??

---

### Post by Icarosaurus on 2007-12-03
> **aerorahul said:**
> I...But the green LED on the cam still doesnot blink, ergo the cam does not work. What am I missing. I tried loading skype and ekiga and they say no devices found for the video :( Help, someone , anyone??

Ekiga, detects my webcam... my version of skype doesn't have webcam support.
The led on camera stays off all the time, even if the cam is working... maybe something is still missing in the driver.

Try:
```

dmesg | grep camera

```
and look what it says.

You should see few lines confirming your cam is working... among them:
```

...    Device at usb-0000:00:02.0-2 registered to minor 0

```

Open VLC (install it if you don't have it) and choose to Open a Video4Linux device.
Specify to open /dev/videoX where X is your minor number (0 in my case).

You should then see your big face, or something else on the screen :)

---

### Post by aerorahul on 2007-12-03
this is what I get when I type 
$:>dmesg |grep -i 'camera'
[ 7708.162585] /usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: 1.5.1 : ov51x USB Camera Driver

no minor no.

---

### Post by Icarosaurus on 2007-12-04
Try to disconnect and connect your camera and simply type 'dmesg'...you should see something in the last lines of the output
Anyway... probably, your camera is /dev/video0, if you don't have other cameras, tv tuners or something similar attached to your pc.
Did you try to open it using vlc, mplayer, xine... etc.?
Are you sure we are talking about the same camera?
Type lsusb... you should see this in the output:
```

...
Bus 001 Device 005: ID **041e:4052** Creative Technology, Ltd 
...

```

---

### Post by aerorahul on 2007-12-11
negative. lsusb yields
Bus 005 Device 004: ID 041e:4055 Creative Technology, Ltd

and there is no /devvideo at all.

---

### Post by Icarosaurus on 2007-12-11
We aren't talking about the same camera, then.
[LIST]
[*]your Product ID 4055 is a Creative Live! Cam Video IM **Pro **(VF0230)
[*]my product ID 4052 is a Creative Live! Cam Vista IM  (VF0260)
[/LIST]
That "Video Pro" designates a completely different Camera, with a completely different bridge-sensor couple.
Unfortunately it seems there's no linux driver for your camera nowadays :(
See here :
[http://ubuntuforums.org/showthread.php?p=3872489]("http://ubuntuforums.org/showthread.php?p=3872489")

Regards...

---

### Post by aerorahul on 2007-12-12
Thanks Icarosaurus.
I realized that *a posteriori* I will wait till some "guru" writes a driver for the Creative Live Cam  IM Pro

---

### Post by techboy31 on 2007-12-12
I've definitely got this same camera:

**041e:4052 Creative Technology, Ltd **

I can get it to work fine in Ekiga and in the VLC player (following the posted instructions)

However, camorama gives me the black and white three way split screen (that someone else reported)

Weirdly (as reported by others) the LED on the camera stays OFF the whole time! As if it's not powering up, but it is definitely working in some apps.

I've also upgraded to the latest Skype beta 2.0.0.27 (previously 2.0.0.13), but still no joy in the video test.  It's listing the correct camera (OV519 USB Camera /dev/video0), but the test screen stays black when the test button is pressed.

Has anyone got this working in skype yet?  I'd really love to get this working so i can move my stuff over from Windows.

---

### Post by leon_mcnichols on 2007-12-24
> **TomBentley said:**
> Works for me, at least with Ekiga. I did something like the following:


```
sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.20-16-386
make
sudo make install
sudo modprobe ov51x-jpeg
```



did sudo apt-get install linux-headers-2.6.20-16-386 got e: Could't find package linux-headers-2.6.20-16-386 and drops me back to blah@Eve:~/webcam-driver$ 

Resolution please?
its a Creative Labs Live Video pro .....

---

### Post by justinpickard on 2007-12-25
> **leon_mcnichols said:**
> did sudo apt-get install linux-headers-2.6.20-16-386 got e: Could't find package linux-headers-2.6.20-16-386 and drops me back to blah@Eve:~/webcam-driver$ 

Resolution please?
its a Creative Labs Live Video pro .....

I'm experiencing the same thing.

Any ideas?

---

### Post by Blackcomb on 2007-12-26
> **techboy31 said:**
> I've definitely got this same camera:

**041e:4052 Creative Technology, Ltd **

I can get it to work fine in Ekiga and in the VLC player (following the posted instructions)

However, camorama gives me the black and white three way split screen (that someone else reported)

Weirdly (as reported by others) the LED on the camera stays OFF the whole time! As if it's not powering up, but it is definitely working in some apps.

I've also upgraded to the latest Skype beta 2.0.0.27 (previously 2.0.0.13), but still no joy in the video test.  It's listing the correct camera (OV519 USB Camera /dev/video0), but the test screen stays black when the test button is pressed.

Has anyone got this working in skype yet?  I'd really love to get this working so i can move my stuff over from Windows.

Same here (on my laptop):

- works partially with Camorama : Black&White and 3 horizontal copies of the image
- works fine with Ekiga
- no test view with Skype, but Skype "finds" the camera OV519 USB Camera (/dev/video0).

My desktop computer has, next to my camera, 2 video interfaces (cheap Medion tv card). When I do exactly the same procedure as on my laptop my camera doesn't work at all. Skype, Ekiga, etc. find my two video interfaces, but no camera). The video interfaces are on /dev/video0 and /dev/video1 . Maybe my tv-card isn't configured properly.

I would like to get it done on my laptop first (for skype) and later I'll try to fix it on my desktop computer. So please if anyone has been capable to make it work with Skype, help me :) I'll do the same if I find a solution [-o<

regards

---

### Post by Blackcomb on 2007-12-26
> **leon_mcnichols said:**
> did sudo apt-get install linux-headers-2.6.20-16-386 got e: Could't find package linux-headers-2.6.20-16-386 and drops me back to blah@Eve:~/webcam-driver$ 

Resolution please?
its a Creative Labs Live Video pro .....

I've installed the linux-headers-2.6.**22-14**-386, which is a newer version. You can easily avoid these problems by using tab completion. In this case you type:
```

$ sudo apt-get install linux-headers-2.6.

```

and then press TAB twice. You will get a list of possible packages and just pick the right one.

---

### Post by RchaEcke2 on 2008-01-04
I just got a vista computer and the creative camera does the video but not the sound

---

### Post by lo_moixo on 2008-04-11
Hi!

I'm quite newbie at Ubuntu (Linux).

I have the** creative Live! IM** webcam, and didn't knew how to start with it in my Ubuntu (7.10).
So I found your solutions.

**[COLOR="Blue"]1)[/COLOR]** First I tried with the driver:

```
sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.22-14-386
make
sudo make install
sudo modprobe ov51x-jpeg
```

So I installed the last "linux-headers" as suggested, and not the "*linux-headers-2.6.20-16-386*" I first read on previous post of this thread.

**[COLOR="Blue"]2)[/COLOR]** Checking if it works.
After reboot, I tried VLC, with vlc v4l:/dev/video0
(As I read in this thread)
Wow! I can see the image, but too dark, as if in my room was no light on 8-[

I can obtain a better image playing with the colors/contrast/bright/... but not good at all.
Still looks like as if I was in a cave.

**[COLOR="Blue"]3)[/COLOR]** Testing it with Ekiga. (v.2.0.11 on ubuntu 7.10)
I had no SIP account, and never used Ekiga, so I launched it and followed teh wizard.
Created a free account, and configured all.

I can't see anything in the Ekiga Video windows (all black), when I activate the webcam icon.
(Also I have to mention I couldn't connect to the test Ekiga call, but this should be another thing)

- - -

So now, I'm trying to find another video-conference program, and checking if there are better drivers.
Any ideas about the problem?

Would be great to use Ekiga, so I can use it on WinXP Laptop (wife).

The need to use video-conference is that I'm setting up a new PC, with Ubuntu 7.10.
It's for my dads, so I will introduce them to Linux.
And this summer my daughter (4 years old) will be for weeks with them (more than 300km ago).
So as all of us have DSL we can chat and see her each night. :-)

Any of them (dads for older, daughter for novice) will NOT be able to config. all this.
Then I have few months to check, test, and find the more stable solution.
(Last option will be, reinstall XP on that new PC and make it work with MSN
Please Help! I don't want to shoot this last option)

Thanks in advance.

---

### Post by Angelos72 on 2008-04-15
Creative Live cam Vista IM works with Skype

Here's how to do it...

SebTV and Paulatz from Skype forum found the answer: 

SebTV wrote a patch that I attach here.

Here's how to apply the patch:

- Copy it into the ov51x-1.5.3 Source directory (where ov51x-jpeg-core.c resided)

Then write

- patch -p1 < ov51x-jpeg-core.noblock.patch.txt
- make clean
- make

sudo make install
sudo rmmod ov51x-jpeg
sudo modprobe ov51x-jpeg forceblock=1

If you get a message like

"patch -p1 < ov51x_jpeg_core.noblock.patch
missing header for unified diff at line 3 of patch
patching file ../ov51x-jpeg-1.5.3/ov51x-jpeg-core.c"

Try to change the second line from "patch -p1" to "patch -p0" (the rest of the line does not change).

The above has worked for me (using the patch -p0 option)

Also Please notice that the patch was originally made for the driver 1.5.3 version. That's the version that I installed. I do not know if it will work for a different version of the driver.


Here are the links to the original postings

[http://forum.skype.com/index.php?showtopic=100897&pid=465545&mode=threaded&show=&st=59&#entry465545]("http://forum.skype.com/index.php?showtopic=100897&pid=465545&mode=threaded&show=&st=59&#entry465545")


[http://forum.skype.com/index.php?showtopic=100897&pid=467424&mode=threaded&show=&st=59&#entry467424](http://forum.skype.com/index.php?showtopic=100897&pid=467424&mode=threaded&show=&st=59&#entry467424)

---

### Post by Icarosaurus on 2008-04-22
I use the svn version of the driver.
Loading it with the forceblock=1 option makes the camera work under skype without the need to patch it.
Maybe the patch has been already applied in the svn version. Thanks!

---

### Post by Angelos72 on 2008-04-28
> **Icarosaurus said:**
> I use the svn version of the driver.
Loading it with the forceblock=1 option makes the camera work under skype without the need to patch it.
Maybe the patch has been already applied in the svn version. Thanks!

That seems to work fine. However when I reboot, skype still finds  the webcam, but I get a blank screen.

What I have to do to make it work is unload the module 

```
sudo rmmod ov51x-jpeg
```

and then reload it with forceblock=1

```
sudo modprobe ov51x-jpeg forceblock=1
```

Is there anyway I can make Skype work without having to unload and reload the module all the time? :confused:

---

### Post by Icarosaurus on 2008-04-28
> **Angelos72 said:**
> That seems to work fine. However when I 
reboot, skype still finds  the webcam, but I get a blank screen.

What I have to do to make it work is unload the module 

```
sudo rmmod ov51x-jpeg
```

and then reload it with forceblock=1

```
sudo modprobe ov51x-jpeg forceblock=1
```

Is there anyway I can make Skype work without having to unload and reload the module all the time? :confused:

Create a file in /etc/modprobe.d
```

sudo gedit /etc/modprobe.d/ov51x-jpeg

```

Paste in it the options you want:

```

options ov51x-jpeg forceblock=1 led=2

```

with "led=2" you'll have a working led on your camera :)
Check the other available options with
```

modinfo ov51x-jpeg

```
No need to reboot: you just need to 
```
sudo rmmod ov51x-jpeg
sudo modprobe ov51x-jpeg

```
and it will work.
...And it will work at the next reboot, of course :D

---

### Post by kumarnarain on 2008-07-04
Very useful...Thank you

---

