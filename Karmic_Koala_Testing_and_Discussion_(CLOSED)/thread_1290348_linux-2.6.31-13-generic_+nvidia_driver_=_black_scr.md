---
title: "linux-2.6.31-13-generic +nvidia driver = black screen:-/"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by _sAm_ on 2009-10-13
Hi

I have the driver for nvidia installed, and after upgrading to linux-2.6.31-13-generic I get a black screen when starting it(just after the black/white Ubuntu logo shows). 

I updated the system with;
sudo aptitude update && sudo aptitude safe-upgrade

I tried to start with linux-2.6.32-12-generic and it booted fine, and I could remove the nvidia driver), and then boot in to linux-2.6.31-13-generic.

I installed the nvidia driver again(just to see if it worked), but the black screen returned. I am not able to boot into  linux-2.6.32-12-generic this time; it ask me for login name and password in textmode(and I cant enter it cus the screen is flickering like crazy and the keyboard don't work as normal). 

I just want to share info, and perhaps get a suggestion to how to fix it. 

Thanks for reading.

---

### Post by joey-elijah on 2009-10-13
> **_sAm_ said:**
> Hi

I have the driver for nvidia installed, and after upgrading to linux-2.6.31-13-generic I get a black screen when starting it(just after the black/white Ubuntu logo shows). 

I updated the system with;
sudo aptitude update && sudo aptitude safe-upgrade

I tried to start with linux-2.6.32-12-generic and it booted fine, and I could remove the nvidia driver), and then boot in to linux-2.6.31-13-generic.

I installed the nvidia driver again(just to see if it worked), but the black screen returned. I am not able to boot into  linux-2.6.32-12-generic this time; it ask me for login name and password in textmode(and I cant enter it cus the screen is flickering like crazy and the keyboard don't work as normal). 

I just want to share info, and perhaps get a suggestion to how to fix it. 

Thanks for reading.

You can login if you have the patience. Just enter your username and password (it'll take a lot of banging on keys repeatedly whilst the screen flickers) then once you're in startup x manually using

startx

you'll be taken to your desktop where you can download/reinstall your nvidia driver and get back to stability until you're ready to tackle the .13 issues.

---

### Post by Cuddles McKitten on 2009-10-13
"sudo apt-get install nvidia-glx-173" in a recovery console fixed it for me.  The newer drivers don't seem to work well for some reason.

---

### Post by _sAm_ on 2009-10-13
The problem is I cant use the keyboard once it ask me for username/password. Its like I need to press several times before it types(and the password is hidden so I cant know if I have typed a letter at all..). 

I can try recover mode and remove the nvidia driver.

---

### Post by ikisham on 2009-10-13
The key is patience ATM.
Karmic is still in active tweaking so a lot of things may happen.
I use nvidia-glx-185 and it's working fine (but then I've last upgraded one or two days ago).
I've last upgraded through Update Manager and one would laugh if saw what appeared on the screen (it went to gdm - old style - then to black etc.), but as long as we don't touch anything while the HD light is blinking then there's a better chance that everything goes alright.

---

### Post by bpickel on 2009-10-13
Try this.

Boot to a Live CD once to the desktop launch nautilus as root. Browse to etc > X11 and locate the xorg.conf file. Open it and change the "driver" section under Device to nv instead of nvidia.  This will probably be the only entry in the conf file as the newer version of X only use the file if it is there.    

After that you should be able to boot to the desktop of your install. 

Then add the nvidia-vdpau PPA here.

[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

Then install the latest Beta driver with 

sudo apt-get install nvidia-glx-190

This should remove all old instances of the drive as well. Then cross your fingers and reboot. 

Running just fine with the good ole' beta driver here.

---

### Post by jdeslip on 2009-10-13
Just wanted to add a me, too, here.  It seems the 185 driver and the latest kernel is borked - I boot just into a blank screen.  Installing the 173 driver does indeed fix the problem.  But, not ideal obviously.

Is there a launchpad bug for this yet?

---

### Post by donniezazen on 2009-10-13
> **_sAm_ said:**
> Hi

I have the driver for nvidia installed, and after upgrading to linux-2.6.31-13-generic I get a black screen when starting it(just after the black/white Ubuntu logo shows). 

I updated the system with;
sudo aptitude update && sudo aptitude safe-upgrade

I tried to start with linux-2.6.32-12-generic and it booted fine, and I could remove the nvidia driver), and then boot in to linux-2.6.31-13-generic.

I installed the nvidia driver again(just to see if it worked), but the black screen returned. I am not able to boot into  linux-2.6.32-12-generic this time; it ask me for login name and password in textmode(and I cant enter it cus the screen is flickering like crazy and the keyboard don't work as normal). 

I just want to share info, and perhaps get a suggestion to how to fix it. 

Thanks for reading.

Same problem here. Just reinstalled the OS.

---

### Post by darco on 2009-10-13
Here is my thread and what I did to fix....

[http://ubuntuforums.org/showpost.php?p=8064065&postcount=1](http://ubuntuforums.org/showpost.php?p=8064065&postcount=1)

also here is the link to sdennie's [script]("http://ubuntuforums.org/showthread.php?t=835573")...

good luck

darco

---

### Post by jdeslip on 2009-10-13
Oh, the joys of running a Beta OS :)

---

### Post by jdeslip on 2009-10-13
> **darco said:**
> Here is my thread and what I did to fix....

[http://ubuntuforums.org/showpost.php?p=8064065&postcount=1](http://ubuntuforums.org/showpost.php?p=8064065&postcount=1)

also here is the link to sdennie's [script]("http://ubuntuforums.org/showthread.php?t=835573")...

good luck

darco

While I appreciate this.  I would really rather use the Ubuntu nvidia packages and ubuntu's dkms system.  ...  except for the fact that it appears to be currently broken. :/

---

### Post by dreamersbrow on 2009-10-13
filed a bug with launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/450865](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/450865)

```
sudo dpkg-reconfigure nvidia-185-kernel-source
```from the command line in recovery mode fixed this for me.

It's like the new module wasn't being generated.

---

### Post by fedexnman on 2009-10-13
i dont think ill ever beta test an os again, nvidia 173 drivers work, but 185 will keep me from booting my system:(, ill sit on the fence from now on !

---

### Post by bheemboy on 2009-10-24
Having same issue in mythbuntu 9.10 rc. nvidia 185 driver shows up with blank screen. Works through VGA input on a regular monitor but does not work through DVI. My TV has only a DVI input.

Followed guidelines at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and added "Option "UseDisplayDevice" "DFP"" to xorg.conf. no good.

Followed guidelines on this thread and tried "sudo dpkg-reconfigure nvidia-185-kernel-source". Still no go.

Installed 173 and the GUI screens show up, but videos don't show. VLC and Xine run, can hear the sounds but no video.

Installed 190 beta from nvidia. No use.

All the kings horses and all the kings men cant seem to put humpty dumpty together again...

---

### Post by bheemboy on 2009-10-28
I reformated my box. Installed the vesa driver and afterwards I installed nvidia driver v173.
Everythings working now...

---

### Post by darco on 2009-10-29
Havent looked back after my first encounter w/non building modules...
Running 2.6.31.14 Karmic X64 w/Nvidia 190.42 rc drivers....

darco

---

### Post by information_entropy on 2009-10-29
I fixed mine with

```

apt-get install nvidia-glx-185
dpkg-reconfigure nvidia-185-kernel-source

```

in the run-as-root recovery console.

The flashing loging screen is extremely irritating:shock:

I guess it did not really fix it
Back to the flashing login on the next reboot.
173 did not work for me either.

---

