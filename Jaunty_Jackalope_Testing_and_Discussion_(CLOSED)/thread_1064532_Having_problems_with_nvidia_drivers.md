---
title: "Having problems with nvidia drivers"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by airbornemist6 on 2009-02-08
I'm currently having problems with the nvidia restricted drivers. I have two geforce 9600 GTs in SLI and I've tried installing both 173 and 180, with no luck. Whenever I install them and then reboot, I get thrown to terminal, which I'm not good in. The screen flashes a bit as if it's trying to start GDM, but can't. I had something similar happen in Intrepid if I remember right, and I eventually found something that made it work (90% of the time, which was better than the 0% previous). Anyway, does anyone have any ideas? I could really use some help here.

---

### Post by minisori on 2009-02-08
The 180 is 180.27 version from repos?

---

### Post by airbornemist6 on 2009-02-08
> **minisori said:**
> The 180 is 180.27 version from repos?

Yes. Sorry. I meant to say that, but I kind of assumed restricted drivers might give it away. I got in the habit of talking in the most confusing way possible about things since I work at a helpdesk. Makes people feel more confident that I know what I'm talking about.

---

### Post by minisori on 2009-02-08
Hmm probably the kernel module differs from x driver. Check if both are the same version. Also check the log from xserver from any error.

---

### Post by airbornemist6 on 2009-02-08
You know, I'm not sure how do do that.

---

### Post by emerson999 on 2009-02-09
I think a recent X update killed it and we're stuck just waiting for one or the other to be updated again.

---

### Post by autocrosser on 2009-02-09
If you are using SLI, you need to define your main card---My SLI setup didn't work until I did... I'm including my xorg.conf for you to look at--Alberto (nVidia driver maintainer) clued me in where it needed to be modified to work correctly--my cards are at BusId 3.0.0 & 4.0.0--I'd bet yours are the same--if not, you need the BusId numbers for your setup....

More info---if you don't know how to find your BusId--startup with only the main card you are going to use..then make sure you have nvidia-settings installed---just look at your GPU 0 information--that will include the BusId. You don't really need the second card's number--you just need the card that Xorg needs to start up first.

---

### Post by airbornemist6 on 2009-02-09
I think that's what I did last time, I'll try it.

EDIT:

YES! I did a quick copypasta of the device part of your xorg, changed the pcibus, and omg it's booting and I'm logging in and... BALLS! It's stuck at a blank wallpaper. Any other ideas?

---

### Post by Archmage on 2009-02-09
> **airbornemist6 said:**
> I'm currently having problems with the nvidia restricted drivers.

Since the restricted driver is broken and will be fixed in the Beta latest, you don't need to report this bug. Kindly test other things and try to find there bugs.

---

### Post by ronacc on 2009-02-09
for the "stuck at blank wallpaper issue " see this thread .
[http://ubuntuforums.org/showthread.php?t=1061919](http://ubuntuforums.org/showthread.php?t=1061919)

---

### Post by autocrosser on 2009-02-09
Yea--the "compiz" bug.......

---

### Post by airbornemist6 on 2009-02-13
Yeah... well I haven't had much time to play with it this week, but I finally got some time today. I applied the fix, and that got me in once, until I decided it was a good idea to try and install the new nvidia drivers that are supposed to fix this problem. Well, apparently, that didn't go well. I can't get GDM to start now. I have added the appropriate lines to my xorg.conf, yet it just won't launch GDM. Now, granted, every time I install the nvidia drivers I always have trouble getting it to start GDM, it tries and fails 4 or 5 times before it manages to finally launch it, but it does it; but this time around, it's not managing a single launch. Any ideas guys?

(Please note, I just did a sudo apt-get remove nvidia* restricted-modules* to get back in to post this xD)

---

### Post by airbornemist6 on 2009-02-13
sorry but:

IMMA CHARGIN MAH [bump] LAZER!


LAZER FIRE'N

SHOOP DA WHOOP


(too much caffiene and i wanted to make my bump semi-interesting)

---

### Post by airbornemist6 on 2009-02-14
My fun and interesting bump didn't work, I guess I'll have to try a boring one then:

*bump*

---

### Post by ronacc on 2009-02-14
what version nvidia driver are you trying to install ? I am currently using nvidia-glx-180.29-0ubuntu1  and it is working fine on my 64bit sys (7600gs) there is a version -0ubuntu2 which is giving a python error during upgrade so try to find the -0ubuntu1 and try that .

opps just looked again it is the dev files that are giving the python error, so the 0ubuntu2 driver itself is ok .

---

### Post by airbornemist6 on 2009-02-15
I have 180.29. I was able to start X with 180.27, however, with 180.29, I can't apparently. I'd really like to know why it's doing this, I mean, in theory, it shouldn't. I'm so confused.

---

### Post by ronacc on 2009-02-15
try this when it dumps you to a terminal , run top to see if mabye x is running but not working for some reason  , stop top with the q key . If x is not running type startx <cr>  and see what it tells you , if x is running kill it with kill xxxx where xxxx is the process number (pid) from top , then startx .

---

### Post by gwenn on 2009-02-15
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180)
Here you can find the driver.
Save  on Desktop and extract from the tar.gz ,you'll have a folder called nvidia... 
sudo apt-get remove --purge nvidia
Hit Ctrl-Alt-F1
You will have the CLI 
sudo /etc/init.d/gdm stop
cd Desktop/nvidia...
sudo sh NVIDIA-linux-x86_64-180.29-pkg2.run
sudo nvidia-xconfig
sudo reboot
THIS IS FOR 86_64!
It works for me ...for 32 you must use the other file
For making work compiz you must install Compiz fusion icon

---

