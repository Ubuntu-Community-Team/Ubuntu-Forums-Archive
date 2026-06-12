---
title: "NVIDIA Drivers Problem"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by jack-o on 2012-02-05
Hello everyone,

So Im having problems installing NVIDIA drivers, I've been trying to install them for about a month now and nothing. When I install Ubuntu 11.10 the graphics are good but I notice when I watch a video that the graphic drivers aren't the appropiate ones. 

I have an Alienware M14X with an NVIDIA GeForce GT 555m 1.5GB.


Everything works fine when installing the drivers through "sudo apt-get install nvidia-current" until I got to start the X server settings and it tells me to run "nvidia xconfig" and afterwards to restart the X Server. Well after I do this and reboot my PC it gets stuck trying to log in, I try to log in (startx) in terminal mode and it tells me "fatal error: no screen found". I've followed several posts with people having the same issue but it does not seem to work at all. 

Some of them are: 

[http://alexsleat.co.uk/2011/03/04/how-to-fix-fatal-server-error-no-screens-found-ubuntu/](http://alexsleat.co.uk/2011/03/04/how-to-fix-fatal-server-error-no-screens-found-ubuntu/)

[http://www.prash-babu.com/2008/11/how-to-fix-no-screen-found-error-in.html](http://www.prash-babu.com/2008/11/how-to-fix-no-screen-found-error-in.html)

[http://www.youtube.com/watch?v=ReyT56rTWnA](http://www.youtube.com/watch?v=ReyT56rTWnA)

and many youtube videos and nothing. It just keeps saying "no screen found"

Curious thing is since I know (or at least I think I know) that the one causing the trouble is the "xorg.conf", I cd to it and then I rm (delete it, Im sure all of you know) it and when I type "startx" it logs in perfectly as if nothing happened. 

I dont know what to do and neither am I a super computer genius, considering I cant even get the graphic to work flawlessly. If anybody has any knowledge in what the solution to this I would greatly appreciate it.


Thanks,
jack-o

---

### Post by cybergalvez on 2012-02-05
try deleting your xorf.conf file its not really needed all that much any more. If you've installed the nvidia drivers they should be working be default. To test if your system starts normally after deleting the xorg.conf file load up nvidia-settings it will tell you if you are actually running the propritary drivers and which version you are using

---

### Post by kc1di on 2012-02-05
It would be better to install the nvidia drivers via the additional driver tool found under system setting. 

try that first.  

system settings can be found by clicking on the log out icon on the upper right if your using Ubuntu 11.10 and unity desktop

---

### Post by jack-o on 2012-02-05
Ok, so I tried both of them and in the X Server setting does not say anything about the drivers and a pop up shows telling me:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

And like I said when I do that it gives me the error of  "fatal error: no screen found"

That's before with the drivers installed from sudo apt-get install nvidia-current and with the drivers it recommend in the system setting-additional drivers. It says they're active and yet it keeps telling me the message I quoted previously about the X configuration file. 

The stock drivers that 11.10 comes with work and the resolution is good but one sees the lack of the actual video drivers when one watches a video or for example try to open the X Server setting saying that I dont have the NVIDIA X Driver.


Thanks,
Jack-O

---

### Post by BC59 on 2012-02-05
You could try this:
Open synaptic (if you don't have it, install it) and purge everything related to nvidia
then add xorg-edgers ppa (or x-swat) and update.
remove again xorg.conf, just in case
reinstall nvidia-current, nvidia-settings (needs dkms installed first)
and finally, deactivate the added ppa, and update again.

---

### Post by dino99 on 2012-02-05
a few things to note:
- always use the driver from ubuntu archive or from a trusted repo like xorg-edgers
- your card is one of the newest, so you needs too the latest driver
- xconfig (which a nvidia command) often break the system video, as ubuntu use custom settings

so from a terminal:

- sudo rm /etc/X11/xorg.conf
- sudo apt-get install synaptic
- sudo synaptic
     1) purge ALL the nvidia installed packages
     2) install this ppa to get the latest driver: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
     3) update
     4) check that: dkms & the linux-headers for your kernel(s) are already installed
    5) installed nvidia-current, nvidia-settings
    6) deactivate the added ppa into synaptic
    7) update again
- sudo reboot

After reboot: sudo jockey-gtk  ( to check the driver activation )

---

### Post by jawilljr on 2012-02-05
The Alienware M14X [uses optimus](https://www.dell.com/us/p/alienware-m14x/pd)

So he needs to use [Bumblebee](https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage)

Jerry

---

### Post by jack-o on 2012-02-05
Ok, I tried dino99 and BC59's ways and none of them worked. Then I did a little research and jawilljr is right, I need to use Bumblebee. So I purged all my nvidia drivers and settings and installed Bumblebee.  I played a 720p video and it was pretty good.

I did a glxsphere test and here the results without optirun

Polygons in scene: 62464
Visual ID of window: 0x97
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
59.643627 frames/sec - 66.562288 Mpixels/sec
59.614587 frames/sec - 66.529879 Mpixels/sec
58.917371 frames/sec - 65.751786 Mpixels/sec
59.775749 frames/sec - 66.709735 Mpixels/sec



and here are the results with optirun glxspheres


Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 555M/PCI/SSE2
80.424449 frames/sec - 89.753685 Mpixels/sec
83.584539 frames/sec - 93.280345 Mpixels/sec
79.478399 frames/sec - 88.697893 Mpixels/sec


What I dont know is if I should install the recommended drivers in the "additional drivers" option within system settings. Just because I don't have X Server settings or anything like that. AND in the Bumblebee webpage the install instructions say to purge any nvidia-current drivers. 

Does Bumblebee come with the Nvidia Drivers altogether or do I need to install it separately. I also read about ironhide and it says that it comes with the nvidia drivers included but I dont if its any different from Bumblebee. 



P.S. When I run lspci in terminal, next to VGA compatible controller it says "00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)" shouldn't it say Nvdia GeForce...?



Thanks, 
Jack-O


EDIT ******

I did find in the lspci command this "01:00.0 VGA compatible controller: nVidia Corporation GF108 [GeForce GT 555M] (rev ff)"

---

