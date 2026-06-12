---
title: "Cannot upgrade or Install &gt; 12.04. (i7, HyperX ssd, 16gig ram, GTX 770m)"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by gwill83419 on 2013-12-27
Happy Christmas and west wishes for the new year.

I cannot upgrade beyond 12.04 which probably accounts for the webcam not working (and yes, I have switched it on) and the wired LAN also not working. The wireless networking is fine. Unity Desktop seems ok. When I tested GNOME Desktop it only works in 2D mode.
Hardware: Pc Specalist SkyFire Series (G52-17632X4-CB8) 17.3" laptop, i7, HyperX SSD, 16Gig Ram, GTX 770m.
1) Reseting the Bios boot to Legacy and the boot order appropriatly.
 With only the SSD drive installed the following observed:
2) Known working and tested Cds/DVDs of 13.10, 13.04, 12.10 will not boot to the Test or Install page. The screen going to Black before this point.
3) 12.04 will load (from Cd) immediatly. I can then upgrade to the latest version of 12.04. (Let me call it 12.04+)
4) Using the wireless connection to try and upgrade to 12.10 leaves me with a broken system.
 Then adding a Hard Drive, pre installed with (13.04) from another computer and changing the Bios to boot only from the HD.
5) The system boots with this drive into 13.04 immediatly, though the Webcam and wired LAN still do not work but GNOME 3 works in 3D and Unity work fine.

Additional Notes: 
I have added Bumblebee to 12.04+.
I have tried upgrading 12.04+ to the 3.10 Kernel with no change.
Adding the Gnome 3 Desktop to 12.04+ allows me to boot into GNOME in 2d only mode. Booting from the old HD (5 above) allows me to use gnome 3 in 3D mode?

Some guidance please.
I can give you lots of information about the system and outputs of lsusb ect but don't want to bore you at this early stage.

Graham.

---

### Post by gwill83419 on 2013-12-29
Everything works bar the Webcam.
A couple of articles printed here and some suggestions led me to the article explaining how to change the start-up options on the Boot CD.
Press any key as it opens. Choose F6 and put a cross next to 'nomodechange'. This last found by inspection. Bingo - one happy bunny.
OK, any suggestions concerning the webcam?
 It's a BisonCam, NB Pro. 5986:014C . 
GUVCViewer tells me what it is but 'no go in Cheese, Skype or GuvCvideo' I'm affraid. Read [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) and [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/) I'm not sure I understand this, it seems to suggest that it should work?

Graham.

---

### Post by gwill83419 on 2014-01-05
No Joy with the webcab.
Bumblebee is not working:
[ 1173.731970] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

Funny, it worked under 13.04
G

---

### Post by gwill83419 on 2014-01-05
~$ primusrun vlc
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
primus: fatal: Bumblebee daemon reported: error: Could not load GPU driver

It looks like Nouveau is doing its thing and blocking the Nvidea driver from getting to my GTX card.

---

### Post by gwill83419 on 2014-01-10
Ha. Got the Webcam Working. Yes, the camera PC card had come loose and fallen behind the screen. This morning the sunlight hit the screen 'just so' and i saw nothing behind the camera window. Removed the Bezel and there it was, stuck behind the screen, camera and associated pc board.

Not all computer problems are software related.
Graham.

---

### Post by efflandt on 2014-01-10
I had not heard of 'nomodechange', maybe that is why you cannot change to the GTX card. What you want is 'nomodeset', so video modules are used instead of built-in kernel mode setting. At least that is what I used successfully while installing 13.10 on i7-4700 with Intel HD 4600/Nvidia GTX 765M graphics. Not sure what nvidia driver is best (I used nvidia-experimental-310 which is currently 319.60 in 13.10).

With nvidia drivers installed **optirun** works fine to use my GTX 765M, but I have not figured out how to do anything with **primusrun** yet. **primusrun glxinfo** works, but primusrun crashes for anything with actual graphics.

---

### Post by gwill83419 on 2014-01-17
Thanks for your reply.
This sounds like the thing.
Can you only change nomodeset during the install or do you know how I do it otherwise.
At the moment, I don't think the GTX770 card is running at all (everything is using the Mother board video and a bit slow). In addition, I have no HDMI output, I'm sure this is because I'm nt using the Nvidia card.

Graham

---

### Post by gwill83419 on 2014-01-17
My Apologies. 'nomodechange' should have read 'nomodeset' as you say.
I have checked Grub and 'nomodeset' in part of the default.

Still Software & Upgrades / Additional Drivers reports that ' No Additional Drivers available' - 'No proprietary drivers are in use'  making it a bit difficult to install 319.60.

Any suggestions?
Graham.

---

### Post by gwill83419 on 2014-01-17
Bumblebee - nvidia isn't working either. Tried installing latest 331-331.38 from the edgers ppa but that's not working either.

Hmm.

---

### Post by gwill83419 on 2014-01-19
Hmm. It's all very unsatifactory. I now have a system that refuses to boot past the splash screen.

Graham

---

