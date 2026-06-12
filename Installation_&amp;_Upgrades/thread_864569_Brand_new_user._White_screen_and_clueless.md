---
title: "Brand new user. White screen and clueless"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by SilSpd on 2008-07-19
Never knew a thing about Linux before, but I wanted to give Ubuntu a shot after seeing some very positive reviews and such.

I burned the iso for ubuntu 8.04 x86, checked the image in the boot menu and it said it was OK. I chose to run the OS off the CD, as Ive heard you can see whether your PC is compatible and give Ubuntu a 'test drive'. It proceeded with the load screen and then went to a White Screen and never came out. So I installed Ubuntu fully on a blank ntfs drive and it does the same thing, White Screen after loading. No login, no GUI at all, just startup progress bar straight to white.

My system:
Gigabyte GA-EP35-DS4
Intel Q6600
2 gigs of DDR-1066 Mushkin
36gig WD Raptor
1gig ATi Radeon HD 2900
Lite-on CDRW
Sony DVD
3.5 Floppy
Dell 2407 wfp monitor
Brother 2070N printer

Is this hardware compatible? Do I need to intall drivers somewhere before loading? I just have no clue and I'm really excited to try this out from what Ive seen and read.

_daniel

---

### Post by Pumalite on 2008-07-19
Try the Alternate CD.

---

### Post by SilSpd on 2008-07-20
Ok I tried the alternate CD with the AMD64. An all around different combo I supposed. Still no luck though. Exactly the same situation. Just a white screen after load, no mouse.

Please help me. This is my first Linux experience and I really dont want it to leave a bad impression on me. Ive scoured Google and I haven't seen anything like this problem before, usually the white screen comes up after some graphical change someone makes, not before anything happens at all! Ive gotten really excited about this, watching movies, seeing screenshots and reading ubuntu philosophy...

Im suspecting that there must be something that it doesnt like about my hardware, can anyone confirm this? Is it something like installing drivers in a (dos? command?) prompt before boot?

---

### Post by macpointman on 2008-07-20
I had Ubuntu 6.10 running perfectly I decided once I built my desktop id upgrade to the new version.  I never should have upgraded.  I love Linux and Ubuntu but this has been nothing but a hassle getting My ATI vid card to work with it.

It seems to be an issue with ATI hardware.  Someone, especially ATI needs to figure this out.  If Linux is going to be or wants to be a viable Alternative to Microsucks Windows things need to "Just Work"

Right now it doesn't "Just Work" and this new version NEVER has.

sorry this is me Getting Frustrated.  I want my OLD Linux back.

This is supposed to be LINUX and better than windows. If Windows can make an UPGRADE work and charge more than a hundred bucks for the basic upgrade. you'd think the Linux community could. It is after all supposed to be FAR superior to Windows.

I am sorry I guess I am just frustrated. I NEVER NEVER should have tried that upgrade option.

Now I cant even log in after the new updates. I get nothing but a white screen when I boot into Gnome in Regular mode or Failsafe mode. I am not well enough versed in command line to fix it.

SO what do I do. I am keeping Microsucks as my primary on my desktop until I can get it all worked out on my notebook. Which is effectively BRICKED. My notebook is my secondary unless I am traveling. I don't like living without it but I can at the moment.

Doing a CLEAN install is completely out of the question at this moment.

MacPointMan

I can not effectively recommend this Operating system to my customers based upon this experience.

with 6.10 I was able to get everything running. I am going on almost 6 months now with the same problem and no answer. with 6.10 I could find an answer within minutes. NOW after the newest updates NOTHING AT ALL just plain old whight screen.

Ubuntu Linux does not "Just work" right now.

MacPointMan

MacPointMan

---

### Post by loboc on 2008-07-20
Once you at the white screen vcan you use the CTL+ALT+F1 to get to the command prompt or is it a hard freeze where it doesnt respond?

---

### Post by macpointman on 2008-07-20
well thats a start where the heck do I go from there?

MacPointman

Missing my old Ubuntu Oh where oh where has my 6.10 gone

---

### Post by loboc on 2008-07-20
Okay once you've logged in you can start trying to figure out what happened. the first thing i would try is 

```
 dmesg | less 
``` and read the boot up messages

then I would try to restart gdm

```
 sudo /etc/init.d/gdm restart 
```

If that doesnt get you a GUI login prompt I would check my pci cards and drivers

```
 lspci 
``` will list your cards
and ```
 lsmod | less 
``` will list your drivers 

if the ati drivers show up in lsmod then try reconfiguring the Xserver to use the cards and set the proper resolution for your monitor

```
 dpkg-reconfigure xserver-xorg 
```

IF that doesn work you can try the old ati drivers so you can at least login in but first lets see if any of that helps

---

### Post by macpointman on 2008-07-20
First of all Thank you for your help.  Anything is better than nothing.

Nope I have absolutely NO IDEA WHAT I AM LOOKING FOR.

and reconfiguring the Xorg didnt work  Same result

MacPointMan

I so want Linux to gain in popularity but this is the reason why it has not.  If people are not going to be able to get the goodies.  I/E the way it looks in gui they darned sure are not going to buy it.  and the purchase process is nothing more than a free download.

---

### Post by loboc on 2008-07-20
Yeah I know its tough to decipher what all that stuff is, I was in you boat way back when the nvidia drivers were just coming out for my old stuff. Anyway does your box have net connectivity. Try 

```
 ping www.google.com 
``` and see if you get a reply

If you do try doing a update/upgrade of your packages from what was on the cd

```
 sudo apt-get update 
``` will download new information
```
 sudo apt-get dist-upgrade 
``` will upgrade the installed software while trying not to break anything if thats any comfort. apt-get upgrade updates every package availiable and sometimes breaks a dependency.

---

### Post by loboc on 2008-07-20
if you get that far 
```
 sudo apt-get install xserver-xorg-video-ati xorg-driver-fglrx 
```

might give you a few more options in the driver listing in the dpkg-reconfigure xserver-xorg dialogue to try out. 

Another option in the dpkg-reconfigure has to due with the framebuffer you could try toggling that and see if switching from one to the other helps, I think one is the cards buffer and one is the kernel's buffer.  

Does you monitor have menu button on it were you can see the resolution that its trying to display.  I know mine blanks when my laptop tries to push anything higher than 1280x1024  to it.

---

### Post by loboc on 2008-07-20
After reading your post update above I just realized i may be addressing the wrong issue are you able to get a login manager and enter you name and password at the pretty picture? If so does the mouse cursor appear but you have no desktop?

---

### Post by loboc on 2008-07-20
I am going to bed I ll check the thread tomorrow and see how you did  hopefully that apt-get update and dist-upgrade will set you right.   Alot can change in 6 months on the repositories I assume you have a pretty big download and install going on. Once its done restart and see if it boots up correctly for you. Good luck

---

### Post by SilSpd on 2008-07-20
loboc, your responses were great and pretty on-the-mark in terms of what logically could be going wrong

You were right with your first understanding of the problem, the only pretty thing I have is the uuntu logo with the progress bar, which then switches immediately to a white screen after some console-looking text.

I downloaded and install all the updates via ctrl-alt-f4, including the ati drivers. I also looked at the boot log which nothing seems particularly alarming to my nooby eyes.

But no luck...wsod :(

I'm willing to give anything a try though, keep chugging along.

---

### Post by Pumalite on 2008-07-20
Have you tried Envy?:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by loboc on 2008-07-20
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) 
That envy script might help. Using the envyng -t from the command line  and  following the faq.  This is a laptop right so you cant swap out the card ? 

The other thing todo is to select the vesa driver in dpkg-reconfigure xserver-xorg.  You wont have any 3d support and it might only do like 800x600 but getting to the gui might make it easier for you to hack around and try to figure stuff out

---

### Post by loboc on 2008-07-20
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) heres a more detailed install for the fglrx drivers

---

### Post by SilSpd on 2008-07-21
Ok so I tried to get all those things done. I'm unaware of whether any of them would solve the problem however since none of them actually went through and completed.

I can't remember which is which but, the Envy one required me to open up restricted and universal sources, which I couldn't do but in synaptic which is unavailable outside the gui. I researched to try and find and how to change sources.list or how to edit sources options in the terminal with no avail.

So I tried to get that basic 2d 800x600 deal you recommended but when I do that xserver command, all it asked me were a bunch of questions about my keyboard layout and that was it?

Essentially I tried like 3 different ways to get new video drivers installed, but none of them worked since I was missing files or it couldnt find a file.

No Im on a desktop, the guy on the laptop was that angry one posting earlier in the thread. I could switch out my gpu but Im unwilling. this machine also has my main windows installation on another hd.

---

### Post by loboc on 2008-07-21
```

deb http://archive.ubuntu.com/ubuntu/ hardy main universe multiverse restricted 
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted 
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted 
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted 
deb http://archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted 


## BANSHEE 1.0
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main


```

Thats my hardy apt list in /etc/apt/sources.list use 

```
sudo nano /etc/apt/sources.list 
``` to edit it

---

### Post by loboc on 2008-07-21
> **SilSpd said:**
> Ok so I tried to get all those things done. I'm unaware of whether any of them would solve the problem however since none of them actually went through and completed.

I can't remember which is which but, the Envy one required me to open up restricted and universal sources, which I couldn't do but in synaptic which is unavailable outside the gui. I researched to try and find and how to change sources.list or how to edit sources options in the terminal with no avail.

So I tried to get that basic 2d 800x600 deal you recommended but when I do that xserver command, all it asked me were a bunch of questions about my keyboard layout and that was it?

Essentially I tried like 3 different ways to get new video drivers installed, but none of them worked since I was missing files or it couldnt find a file.

No Im on a desktop, the guy on the laptop was that angry one posting earlier in the thread. I could switch out my gpu but Im unwilling. this machine also has my main windows installation on another hd.

"""
I used to use the command "dpkg-reconfigure xserver-xorg" to configure my X server. But in the last version of ubuntu (I'm using 8.04 alpha5) this command only ask for the mice and the keyboard, and not for the graphic card, the resolution etc. which is the important part for me. Is this a bug or just normal, and if it's normal there's a new way to do it?
Thanks
 Christoph Langner said on 2008-03-05:

This is normal. Hardy uses xserver-xorg 1.4 which tries to get rid of xorg.conf. Hardware should be detected when starting the xserver and while hotpluging devices like mice, tabletts and monitors.

"""  

I dont know why they did that makes all my dpkg knowledge now worthless.  

apprently xrandr is the new hotness to select display modes from the command line but it doesn select driver xorg 1.3 + is supposed to that all by itself

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by macpointman on 2008-07-22
> **loboc said:**
> After reading your post update above I just realized i may be addressing the wrong issue are you able to get a login manager and enter you name and password at the pretty picture? If so does the mouse cursor appear but you have no desktop?

This is exactly the problem.  I apologize I have been unable to check the forum and get online the past couple of days.  Again thank you for your efforts.  I am sure there are many people that appreciate any help that can be received.

I have used Ubuntu Linux 6.10 with Beryl installed for a full year with absolutely NO problems whatsoever.  Those that I have found were easily resolved or explained.  The upgrade as recommended by the software has been like pulling teeth.  I have recommended Ubuntu Linux to EVERYONE that I have come into contact with and had a computer related conversation with (I have MANY MANY MANY computer related conversations).  This new experience has led to me refrain from recommending the new version.  A clean install is OUT OF THE QUESTION.  Just to iterate, My father is a systems engineer He and his company swears by Intel and Microsoft both for their servers and workstations.  The reason?  You are witnessing it right here. Linux is simply unreliable at this point.  A Windows upgrade is much easier and reliable. A Linux upgrade as recommended by the installed software is currently not 100% reliable.

Until Linux can reliably detect and automatically set the appropriate video settings as far as the computer configuration is concerned you will not have regular Joe blow users using this Operating system.  Joe citizen needs it to "Just Work" no tweaking and God forbid no Terminal entries.  

Advantage Microsoft Windows XP

MacPointMan

---

### Post by loboc on 2008-07-22
> **macpointman said:**
> This is exactly the problem.  I apologize I have been unable to check the forum and get online the past couple of days.  Again thank you for your efforts.  I am sure there are many people that appreciate any help that can be received.


MacPointMan

So you have totally different problem than ~slidell guy and we have been hacking at the wrong thing 

All right mac point man if you getting a x environment without panels or windows then beryl might be messed up from the upgrade.  At the command line in CTL+ALT+F1  do a 

```


ps -ax | grep beryl

and

ps -ax | grep compiz


```

use 

```

sudo kill ##### 

```

Where ##### is the process numbers listed next to the compiz or beryl processes

then do a 

```


export DISPLAY=:0
metacity --replace&
gnome-panel&

```

to run metacity and gnome panel and get you desktop back 



Then i would run synaptic and remove everything having to do with compositing and if you want it back install the gnome desktop effects

the compositing stuff changed alot from 6 - 7 and all the package names changed.

---

