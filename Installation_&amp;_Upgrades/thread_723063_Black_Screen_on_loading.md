---
title: "Black Screen on loading"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by BogonAttractor on 2008-03-13
Righto' I'll be as thorough as possible as I've read many other threads on this and the OP's (no insult intended) give descriptions so vague it could be anything from broken monitor to bubonic plague.

First of all, System Spec

Core2 Duo 6750
Asus P5N32E SLI+ Mainboard (one down from a Stryker)
2 GB Kingston ram (IS compatable with the mobo)
2x nVidia 6800GS 512mb (way lower than most of the 84/86/8800 flashy people)
Generic 19" TFT monitor (this one says Ryoku but I've seen the same monitor with about 3 different name stencils so far)

The whole system is working fine, there is absolutely nothing wrong with my hardware, I can guarantee this becuase Im back in XP at the moment typing to you on it now and I've been playing TF2 while the EVE servers are down.  It's been fine since the day I built it.

Right onward with the symptoms

Ubuntu 7.10 live CD 32 bit -  Runs the splash screen, the animated bar, then the progress bar then I get the Ubuntu startup sound but no desktop just a blank screen, with very occasionally a blinking cursor top left.  The monitor light stays green and is getting a signal.  Hitting the power button brings up some text messages as the system shuts down reasonably cleanly. There are a few "failed" in there but they go to fast for me to read.  This happens in any combination of  resolution and colour depth.

Ubuntu 7.10 live CD 64 Bit - Just thought I'd try it - but same as above. Exactly.

Ubuntu 7.10 Alternate Install (64bit) - Installs fine, reboot exactly the same as above.  Removed "'quiet" did the "nosplash" thing but always the same.  Ubuntu startup jingle, black screen, appears to shut down OK.

I will update if I can find a new symptom.  As Dr House says, new symptoms are very good.  Actually scratch that, House's problems are almost always near fatal and very expensive to fix.

---

### Post by Eoghan Murray on 2008-03-13
I've got an exact duplicate of this scenario.
Video card is an nVidia GeForce Go 7600

---

### Post by PmDematagoda on 2008-03-13
I think you may have to install the Nvidia drivers manually. You can do it by doing this:-

1) Install the required packages for the Nvidia installer with:-
```
sudo apt-get install build-essential
```

2) Download the Nvidia driver with:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

3) Run the installer with:-
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

4) Reconfigure the X-Server after installation with:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the options that match your PC's hardware.

After they are done, see if the X-Server will now function properly.

---

### Post by BogonAttractor on 2008-03-13
I'm afraid I'm going to need some more guidance here as I can't work out how to get my network started in recovery mode and it's needed to make use of the commands you listed above.

My network is on eth1 (or should be) there is nothing plugged into eth0, the standard installation found it just fine.

---

### Post by BogonAttractor on 2008-03-13
Even a startup parameter to tell it not to load x11 will do if there is such a thing.. anyone?

In recovery mode ifconfig just tells me I have the loopback on local host, the  eth0 and eth1 devices are not listed.

---

### Post by BogonAttractor on 2008-03-13
Finally getting there I think.  For the sake of other's sanity I'll post the fruits of my labour.

I have just booted off the Alt CD again but booted in rescue mode.  It then asks for a few things one of which is which device you wish to open a shell on (make sure you remember which is your active linux partition, on mine it was sda2 because Im dual booting.)

I have now managed to run the first command I was given 
sudo apt-get install build-essential

Will carry on and see what happens now.

---

### Post by BogonAttractor on 2008-03-13
And FAIL at step 3

ERROR: this.run file is intended for the Linux-x86 platform, but you appear to be running on Linux-x86_64. Aborting Installation.

---

### Post by BogonAttractor on 2008-03-13
```
 wget http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run
```

is the correct package for the 64 bit OS (I hope)

---

### Post by BogonAttractor on 2008-03-13
apparently so but still fail

Verifying archive intergrity ... OK

Uncompressing NVIDIA Accelerated Graphics Driver for *snip*

Error opening terminal: bterm
#_


whatever that means.  Perhaps it means Im not running in my true linux environment.  I will reboot into recovery mode from the main HD and see if step 3 works there.

(many thanks to anyone reading this for the patience in me talking to myself)

---

### Post by BogonAttractor on 2008-03-13
That seemed to install fine.  The nVidia installer complained because it had no internet connection in recovery mode  but happily compiled it's own interface module.

The last command ( step 4) took me on a guided tour of X configuration and one reboot later -

I have accomplished exactly nothing.  I am still staring at a black screen.

There is one change however, I no longer get the Ubuntu startup jingle.

I consider this a bad sign.


Help :(

(The system still shuts down but with error messages and I get a little drumroll if I mash the keys and occasionally the screen flicks to the last of the startup messages and then back to a black screen)

---

### Post by PmDematagoda on 2008-03-13
For now you can get your GUI back with:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I am not able to help out right now until tomorrow since I need to go to sleep. I will look into this tomorrow.

---

### Post by BogonAttractor on 2008-03-13
will try that now..thanks :) (iven that I never actually had a gui)

---

### Post by Eoghan Murray on 2008-03-13
I've followed these steps with a little more success. I installed the NVidia x86 169 drivers from the site using the install-cd recovery mode  to download it and rebooting in recovery mode to install it.  (It complained about wanting runlevel 3, but I went ahead anyway and it installed).

When I booted into the system, it failed, but booting a second time loaded up in failsafe mode, so that is where I'm at now; at least I can see my ubuntu desktop with the Vesa drivers.

---

### Post by BogonAttractor on 2008-03-13
sudo ... xorg  didn't have any effect.  

I just re-installed completely from fresh.
I still get the black screen after the orange ubuntu bar fills up.

This is where the username and pw should be typed in.

If I do this blind I actually hear the ubuntu desktop loading sound and gnome is apparently running though I can't see anything.

Will try everything I tried before again (just in case)

@eoghan yeah I did that too, except I didnt get a failsafe mode.  Still I shall try again, I'm glad you've had some apparent success. seems Gutsy really does not like nVidia cards.

---

### Post by BogonAttractor on 2008-03-13
well, partial success.  By moving my monitor to the DVI head on my card and using a DVI adapter I managed to get the xserver configuration to NOT recognise my monitor and graphics hardware.  I then rebooted and lo, there was a configuration tool asking me what monitor/hardware I was using.  I told it nvidia 6800 generic and generic monitor and it's let me into the desktop.  Im now letting it run through 194 updates.

oh and I put the monitor back on the VGA head when I rebooted.

---

### Post by monos98 on 2008-03-13
> **PmDematagoda said:**
> For now you can get your GUI back with:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I am not able to help out right now until tomorrow since I need to go to sleep. I will look into this tomorrow.



Thanks!!!  That got me working after having a similar problem with a vid card upgrade.

---

### Post by Eoghan Murray on 2008-03-13
Okay - well I've made some further progress so I thought I'd share :)

I had the vesa drivers working on the 7.10 system and decided to take the plunge (seeing as I was spending so much time at system admin) and [upgrade to hardy alpha 6]("http://www.ubuntu.com/testing").

This (long) process was succesful, and although I was dumped in the command line again on reboot, I was able to use the [new EnvyNG script]("http://www.albertomilone.com/nvidia_scripts1.html") for hardy to get my nVidia drivers working.

Hardy looks pretty sweet so far, and I'm very happy, although a lot more nervous about doing anything on my system :-?

Disclaimer–hardy is still alpha

---

### Post by LostAndFound on 2008-03-14
Hi, I just thought I'd chip in regarding the very first post, though probably a bit late. In the very first post BogonAttractor says:

"I get the Ubuntu startup sound but no desktop just a blank screen, with very occasionally a blinking cursor top left" - -- Then you hit the power button to shutdown. 

In cae you were not aware, rather than shutdown, you can try "Ctrl Alt F1" or "Ctrl Alt F2" etc. to go to a different virtual terminal. 

This will enable you to login from the command line in order to change configuration files  before rebooting /  or eventually to do "sudo halt" to shutdown cleanly.... 

There's lots of fascinating info about virtual terminals here:
[http://www.linuxjournal.com/article/5303](http://www.linuxjournal.com/article/5303)
and if your system won't allow you to go to a different Virtual Screen there's a thread here:
[http://ubuntuforums.org/showthread.php?t=414032](http://ubuntuforums.org/showthread.php?t=414032)

---

### Post by BogonAttractor on 2008-03-14
> **LostAndFound said:**
> Hi, I just thought I'd chip in regarding the very first post, though probably a bit late. In the very first post BogonAttractor says:

"I get the Ubuntu startup sound but no desktop just a blank screen, with very occasionally a blinking cursor top left" - -- Then you hit the power button to shutdown. 

In cae you were not aware, rather than shutdown, you can try "Ctrl Alt F1" or "Ctrl Alt F2" etc. to go to a different virtual terminal. 

This will enable you to login from the command line in order to change configuration files  before rebooting /  or eventually to do "sudo halt" to shutdown cleanly.... 

There's lots of fascinating info about virtual terminals here:
[http://www.linuxjournal.com/article/5303](http://www.linuxjournal.com/article/5303)
and if your system won't allow you to go to a different Virtual Screen there's a thread here:
[http://ubuntuforums.org/showthread.php?t=414032](http://ubuntuforums.org/showthread.php?t=414032)

Ahh thanks, I did try that as it happens but forgot to mention it.  I'm very much a newbie to linux but I have used it before.  As it happens I was hitting CTRL F1 and ALT F1 but didnt actually try CTRL-ALT F1.. ahh well.

Just to continue my diatribe however.  It ran through it's updates.  I've told it roughly what monitor I have - it refuses to work recognise my monitor correctly, but I do have the nVidia restricted drivers that Ubuntu downloaded for itself working.  Indeed I am typing this message in Ubuntu now.  Definite progress though I'm not sure my graphics drivers are properly installed yet or that I'm using the correct ones.

Happiness Level: +2

I've backed up my working xorg.conf file to somewhere safe and I'm ready to dive back into the settings to see if I can't get the monitor recognised correctly.

---

### Post by Eoghan Murray on 2008-03-14
As regards getting multiple monitors to work, assuming you've already got the nVidia drivers up and running, I've always had success with the nvidia-settings graphical tool:

```
gksudo nvidia-settings
```

I'm not sure how to install it, I think Envy installs it for you, but I'm sure you can install it separately if you need to.

---

### Post by PmDematagoda on 2008-03-14
> **Eoghan Murray said:**
> As regards getting multiple monitors to work, assuming you've already got the nVidia drivers up and running, I've always had success with the nvidia-settings graphical tool:

```
gksudo nvidia-settings
```

I'm not sure how to install it, I think Envy installs it for you, but I'm sure you can install it separately if you need to.

The Nvidia Settings Manager is automatically installed along with the driver downloaded from the Nvidia web site, it is also included in the nvidia-glx packages.

---

### Post by BogonAttractor on 2008-03-14
Ahh thanks, Im not using multiple monitors though.  It's just that Ubuntu doesnt seem to recognise the full range of refresh rates and resolutions for my monitor.  Im using a 1280x1024 TFT which can use up to 75hz vertical refresh.  If I tell it to "detect" my monitor it gets the refresh rates right but limits me to 800x600.  If I force it to Generic 1280x1024 TFT then I only get the choice of 60hz refresh (which actually looks ok, I'm just being pedantic I guess).

I will look into Envy though. At the moment I'm dealing with job hunting :)

The reason I have 2 cards in my system is because they run in SLI in Windows.

---

### Post by BogonAttractor on 2008-03-14
Just installed Envy, it did it's stuff and now my monitor is recognised as plug and play with a larger range of resolutions than it can cope with but the full range of refresh rates and it's working and I have a decent driver and the whole thing seems stable :)

I think I will mark this topic as solved.

Big thanks to all that posted, all appreciated whether tips and advice or simply "me too!".

Special thanks to PmDematagoda because I'd still be stuck on a black screen without his original post to set me on the right path.

---

### Post by bigdaddysky on 2008-03-14
Hey all, 
I don't want to hijack the thread or anything but, my compaq R4125 laptop has a black screen on boot up too. Im using gutsy, my video card is an ATI 200m, When i boot up i get an error saying PCI: Cannot allocate resource region 3 of device and then a set of numbers, i get 2 of these errors one for region 3 and 4 i believe but i have to double check that. and thats when i get the black screen. right up until i have to log in and thats when i actually get to see any kind of gui.
Can anyone help with this?

---

