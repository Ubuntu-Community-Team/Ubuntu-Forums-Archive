---
title: "Trying and failing to make a truly minimal Lubuntu..."
date: 2015-09-16
forum: Installation &amp; Upgrades
---

### Post by herculeesjr on 2015-09-16
EDIT: Below doesn't really apply anymore. I aborted that install and switched to an Xubuntu minimal install so I can have a stable machine and run VMs to test everything I want to try out. To sum up what I'm aiming for is a fully operational laptop (everyone has different standards as far as that goes) with as few packages as possible and as little RAM/disk usage. Why? Because boredom and curiosity. So far it seems the best start is to start with the network install disk and not selecting any additional options to install. I'm wondering from here what you all would suggest to turn it into a working laptop for everyday use? For me things I'm needing are wifi, bluetooth, screen brightness adjustment, nvidia optimus, sound, full touchpad support, battery and power saving settings, Chrome/Chromium (can't truly find a difference), and for right now that's all I can think of. Examples of things I don't need is printer/scanner support, any accessibility or additional language options, additional drivers, and boot/shutdown animations. Neither of those lists are complete. Just examples.

Computer: Acer Aspire 8530TG
Intel i5 2430M 2.4GHz
6GB DDR3
nVidia GT 540M with nVidia Optimus
250GB WD Black HDD
[HR][/HR]So I've been trying for days to have fun in my spare time refreshing my mind on Ubuntu and Linux in general while ditching Windows for good (fingers crossed). I'm not new but I'm not an expert. My simple project has been to install Ubuntu minimal without anything extra selected to where you just have tty when you log in then from there build a basic lxde desktop and I've had nothing but issues. I won't write a book of everything I've tried and failed and simply reinstalled because all I have right now is my phone to type on, however here is my current situation:

I finished a mini network install with no options selected then restarted into my freshly made OS, it just boots to a black screen which is one bug that I learned I need to press Ctrl Alt F1 to get around, from there I log in and run 
```
sudo apt-get install --no-install-recommends  xserver-xorg-core xserver-xorg-input-synaptics xserver-xorg-video-intel xserver-xorg-video-nouveau lxdm lxde-core lxappearance lxde-icon-theme lxinput lxrandr lxterminal lxtask wicd chromium-browser
```
then rebooted and realized I still need to install xorg so I use 
```
sudo apt-get install --no-install-recommends xorg
```
then let that finish and reboot to see lxdm finally. However if I log in after 90seconds the screen flashes and I'm back at the log in screen, and even if I don't log in and just let it sit there the log in screen flashes and reloads. As far as I'm aware I have finally made myself a truly minimal Ubuntu-based lxde desktop but I need help with this one issue to fix it. Does anyone have any suggestions?

---

### Post by v3.xx on 2015-09-16
Why not just..

```
sudo apt-get install lxde
```

That will bring in all the basic packages.  The open source chrome browser can be upgraded by adding pepper flash.  Also gives you a display manager (lxdm) and xserver-xorg (thats one step below the xorg package).

Its also easy to remove any package you do not want (maybe like lxmusic).

Bucky Ball, where are you :) (our minimal lubuntu install guru)  See if that will chime him in.

[http://packages.ubuntu.com/trusty/lxde](http://packages.ubuntu.com/trusty/lxde)

---

### Post by ajgreeny on 2015-09-16
I don't know exactly how minimal you want your Lubuntu to be but it would be easy to use the minimal install CD as you did to install a command line only system then simply add the lubuntu-core package to it.

That would have solved all the problems you saw of not having all the xorg packages that are needed to get a GUI up and running and would leave you with a small number of what are usually though to be the essential GUI apps for an OS.  Perhaps this is still too large an installation for you, but I can assure you it is simple, fast, and for my purposes was a great way to get just what I wanted in a small OS to which I have since added packages as I've needed to use them.

---

### Post by herculeesjr on 2015-09-16
At the current moment sadly I gave up and started over with a new minimal network install which is about to finish up and I'm going to install xubuntu-core. I wanted to start fresh and try this newer light weight lxde but it looks like I'm going to have to stay with more familiar xfce and experiment in a VM with lxde till I can work out the millions of bugs. So to update my original question I suppose, I'm looking for directions on how you would make a minimal Lubuntu? Even more minimal than the lubuntu-minimal or xubuntu-core, as for those who ask why, I as usual ask why not. I'm basically having fun with it, I want a fully working desktop with the least amount of packages, so its helping me learn while having a good purpose. I'll admit I want to move away from Ubuntu for certain reasons, but I don't know anywhere near enough to try. I tried Debian and couldn't even get the WiFi to be reliable, then finding out they're so behind they still use bumblebee I called it quits.

---

### Post by Bucky Ball on 2015-09-16
> **v3.xx said:**
> 
Bucky Ball, where are you :) 

Hehe. I did look at this before but couldn't see what exactly what was missing. In fact, this is probably more than I would start with. I go the basic and add xfce4, a few other things, Synaptic PM and take it from there. 

@herculeesjr: LXDE and Synaptics was pretty much it to start with a couple of other things. lxde would have dragged in what you needed to get up pretty much (and possibly some of the stuff you're installing manually).

Back to it. Look at this again, just wondering if this is your problem:

```
xserver-xorg-video-intel xserver-xorg-video-nouveau
```

You have two graphics drivers installed. Maybe there is a problem with one or the other or the fact there is both.

You could try getting rid of one of them (boot to the login screen then ctl+alt+F1 and login) and see what happens. My theory is perhaps it is using the open-source nouveau and when you login attempting to use the intel one and crashing. Are you positive you need that driver or that it is the right one for your graphics card? Where did you get the install line from? 

Shots in the dark, nothing else is stands out for me, but it is 6am here and I'm about to go to bed so not exactly sharp as a tack right now. :)

PS: @herculeesjr: Please see last link in my signature for using code tags for terminal output. Thanks.

PPS: Why this?

```
xserver-xorg-input-synaptics
```

---

### Post by v3.xx on 2015-09-16
> **ajgreeny said:**
> I don't know exactly how minimal you want your Lubuntu to be but it would be easy to use the minimal install CD as you did to install a command line only system then simply add the lubuntu-core package to it.

That would have solved all the problems you saw of not having all the xorg packages that are needed to get a GUI up and running and would leave you with a small number of what are usually though to be the essential GUI apps for an OS.  Perhaps this is still too large an installation for you, but I can assure you it is simple, fast, and for my purposes was a great way to get just what I wanted in a small OS to which I have since added packages as I've needed to use them.

Yes, this will also work.

```
sudo apt-get install --no-install-recommends lubuntu-core

```
And you end up with a working desktop.

[http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

Edit
Hey bucky :)

---

### Post by Bucky Ball on 2015-09-16
> **v3.xx said:**
> Yes, this will also work.

```
sudo apt-get install --no-install-recommends lubuntu-core

```
And you end up with a working desktop.



True, but I would personally go again and leave out 80% of the original line. Keeping in mind I don't know lxde so not sure of its basic requirement, I'd try this:

```
sudo apt-get install lxde synaptic lxterminal pcmanfm firefox [or chromium]
```

Add to this a network manager and any other basic APPS, not other stuff, you might need, reboot and see how it goes. At this point, you're only looking to get to a desktop and get online. Once there, you have a terminal and Firefox. :)

But that's just me ...

---

### Post by herculeesjr on 2015-09-16
> **Bucky Ball said:**
> Hehe. I did look at this before but couldn't see what exactly what was missing. In fact, this is probably more than I would start with. I go the basic and add xfce4, a few other things, Synaptic PM and take it from there. 

@herculeesjr: LXDE and Synaptics was pretty much it to start with a couple of other things. lxde would have dragged in what you needed to get up pretty much (and possibly some of the stuff you're installing manually).

Back to it. Look at this again, just wondering if this is your problem:

```
xserver-xorg-video-intel xserver-xorg-video-nouveau
```

You have two graphics drivers installed. Maybe there is a problem with one or the other or the fact there is both.

You could try getting rid of one of them (boot to the login screen then ctl+alt+F1 and login) and see what happens. My theory is perhaps it is using the open-source nouveau and when you login attempting to use the intel one and crashing. Are you positive you need that driver or that it is the right one for your graphics card? Where did you get the install line from? 

Shots in the dark, nothing else is stands out for me, but it is 6am here and I'm about to go to bed so not exactly sharp as a tack right now. :)

PS: @herculeesjr: Please see last link in my signature for using code tags for terminal output. Thanks.

PPS: Why this?

```
xserver-xorg-input-synaptics
```

I had both video drivers installed due to having an optimus system, not sure if I wasn't supposed to do that though. I just figured since they all get installed by default it'd be fine, and the synaptics is for my touchpad. Sure would have helped if I had posted specs about the computer. I'll add that to my OP now.

---

### Post by Bucky Ball on 2015-09-17
The base kernel, which is what the minimal install is, takes care of most hardware. In fact, all, but may have problems with graphics (as I think you've found out here) and wireless.

There is no need to add things for touchpad and mouse or any basic stuff like that. Your initial install line can be a lot more basic than that.

I'd say install a basic one, get to a desktop and then start working out what you need re. graphics drivers, etc. You'll find that the minimal install also drags in enough to get the screen with the open-source drivers. I still suggest getting rid of that intel driver at least and see if it makes a difference.

---

### Post by MAFoElffen on 2015-09-19
> **Bucky Ball said:**
> The base kernel, which is what the minimal install is, takes care of most hardware. In fact, all, but may have problems with graphics (as I think you've found out here) and wireless.

There is no need to add things for touchpad and mouse or any basic stuff like that. Your initial install line can be a lot more basic than that.

I'd say install a basic one, get to a desktop and then start working out what you need re. graphics drivers, etc. You'll find that the minimal install also drags in enough to get the screen with the open-source drivers. I still suggest getting rid of that intel driver at least and see if it makes a difference.
Well... sort of.

You know me and my work work with server and with the Linux graphics layer. I have a minimal X install routine I've been doing for years, with instance loadable xorg and openbox... I've posted that script a few times on the forum. I used to do the --no-install-recommends with xorg packages... and my script worked out for that. That worked just fine... until something changed with xorg. (Last fall?)

I never had the time to debug which part of that changed (had other fires to put out at the time), but if I install xorg full, without the --no-install-recommends switch, then it works out fine. <-- that was my interim fix on my minimal X scripts, until I have more time to go back through that this Winter. It's not the kernel core, but rather something that changed in the new xorg-server packages.

As for Optimus... if he has optimus graphics, then minimal would be the Intel driver, without nVidia. Soon as you add nVidia into it (in an Optimus scenario), it is not minimal any longer (IMHO). Current full for that is now the pertinent nVidia driver, plus nVidia Prime... but I cut back from that to others ([Info here]("http://www.thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux")). What is it is the Nvidia drivers and another nVidia package, nVidia Prime (ubuntu package name: nvidia-prime) that handles the driver/GPU switch, instead of the earlier Bumblebee/ironhide affairs. Like I said, others are better at specializing on just that. so I kept to what I was good at... Debugging problems the Linux graphics layer, and High-end, straight forward, gaming type graphics. Note that you add nVidia drivers, it adds DKMS as a module to the kernel... So installing nVidia does change the kernel.

On touchpad and mouse (and keyboards)... You're right. Those old drivers were deprecated. PnP now.

For a minimal wifi manager, I add wicd.

EDIT-- Note that for a minimal X install... the order you install packages matters lots. Xorg and Xserver packages first, then video drivers, then your desktop, then your login manager (optional), then applications. I noticed that the OP forgot xorg, then add ed later... so that was out of order. The reason the order is important, is that some things have to be in place for the background wiring of things together. If you get it out-of-order, then it screws up that wiring...

If he remove --purges the packages and installs them again in the right order, he might find different results.

---

### Post by herculeesjr on 2015-09-26
So needless to say trying to figure this out on my daily laptop, even if it's not needed daily, and being the only computer in the house has made this fun task old... fast, I've resulted in keeping the Xubuntu Minimal install and moved fully to using VMs and taking VM snapshots to give me room for error. However I haven't made any progress. I have the minimal install finished, I restart to tty and log in fine in tty, yet I don't now what I'm doing wrong because no matter what I install when I restart I'm always greeted again with tty. What is it you guys would suggest for a minimal install? Right now I'm doing xserver-xorg, xorg, and xfce4 (I've been using xfce since I know it better) in that order and letting it install recommends along with them yet when I restart I have to log in with tty and typing startx brings me to a full screen terminal. I must either be missing something I need to install or edit/setup.

---

### Post by Bashing-om on 2015-09-26
herculeesjr; Hello;

A minimal install has no login manager. So long as you are the only user, and do not mind booting to terminal and starting the GUI, there is no need of the login manager.
If you add a login manager you are getting farther away from that small footprint; and it takes just that tad bit longer to boot.

I too install from minimal, 
I only install xorg 
and xfce is also my preference when I want a GUI.

I like it that-a-way !

[INDENT][INDENT][INDENT]me; KISS
[/INDENT][/INDENT][/INDENT]

---

### Post by herculeesjr on 2015-09-26
> **Bashing-om said:**
> herculeesjr; Hello;

A minimal install has no login manager. So long as you are the only user, and do not mind booting to terminal and starting the GUI, there is no need of the login manager.
If you add a login manager you are getting farther away from that small footprint; and it takes just that tad bit longer to boot.

I too install from minimal, 
I only install xorg 
and xfce is also my preference when I want a GUI.

I like it that-a-way !
[INDENT][INDENT][INDENT]me; KISS
[/INDENT]
[/INDENT]
[/INDENT]


Right now I'm unable to even get to a working desktop. I've tried multiple guides online on minimal installs and none of them can get me to a desktop and I've gone as far back as re-downloading the network install iso and starting from scratch. I'm missing something or doing something completely wrong in setup and can't figure out what.

---

### Post by Bashing-om on 2015-09-26
herculeesjr; Well ...

A UEFI system ? Be aware the minimal install does not support UEFI out of the chute, A real pain to get UEFI booting !

Standard install of minimal: 
Download the .iso and verify the md5sum.
Boot the installer and install the minimal operating system.
Reboot to the command line interface 
run 1st !
```

sudo apt-get update
sudo apt-get upgrade

```
next is to install X - all I install is ;
```

sudo apt-get install xorg

```
Then I install the DE 
```

sudo apt-get install xfce4

```
That gets me a fully functional working desktop. At this point to start that desktop is terminal command:
```

startxfce4

```
You can make up a .xinitrc file to tweak the startup.  I added
> 
exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

And with the terminal command :
```

startx

```
it hooks .xinitrc and starts the desktop from .xinitrc.
To get logging operational I also installed anacron ( because cron has a call for it ).
You might want to have a look at how you want logging conducted:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

see:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/](https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/)


[INDENT][INDENT]it - should be -
[INDENT][INDENT][INDENT]as simple as falling out of bed wide awake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-27
Install lightdm or gdm. Any desktop manager should give you a login screen.

---

### Post by herculeesjr on 2015-09-27
So an interesting update, as stated earlier I did a fresh start in my VM again to start all over. Here's the results:
I do a minimal install with zero options selected then restart and install xorg, xfce4, and lightdm, all with --no-install-recommends. Then I restart again and it either freezes at boot, I have to use ctrl-alt-F1 to log in and get a black terminal as if there's no window manager installed, or a bunch of errors scroll by on the screen too fast for me to read (all I could catch was "systemd") and one of the latter things then happens. No matter what there is no getting to a functioning desktop.
So just for the heck of it I start Debian Stretch in another VM and do the same completely minimal install, not a single thing is set up different, after installing xorg, xfce4, and lightdm I restart and everything is flawless. Not sure what that tells me but it's a result?
:lolflag:

---

### Post by VMC on 2015-09-27
I wonder if it freezes because of your video card. Try adding '*nomodeset*' on boot to see. Then again, its a VM, so that shouldn't matter. Mabe remove 'quiet' to observe the outputs.

---

### Post by herculeesjr on 2015-09-27
Fresh install on a new VM hard drive with nothing extra selected, installed xorg, xfce4, and lightdm with --no-install-recommends... It starts and stays at
[ATTACH=CONFIG]264692[/ATTACH]
no matter how long I wait, and switching to tty1 just gives me
[ATTACH=CONFIG]264693[/ATTACH]
so I restarted and disabled splash and quiet and it brings me to tty login, I can log in however startx gives me
[ATTACH=CONFIG]264694[/ATTACH]
and thus startxfce4 gives me
[ATTACH=CONFIG]264695[/ATTACH]

I tried reconfiguring xserver-xorg however it didn't fix anything, just the same results. Before I found that xorg was failing I tried restarting lightdm too, but no luck it reported failing too. Most of my Linux knowledge is from Googling UbuntuForums, and I haven't been able to find anything on xorg failing that fits this, so I'm out of knowledge. Lol

---

### Post by Bashing-om on 2015-09-27
herculeesjr; Humm ...

Mind you I do not know, as I can not reproduce your situation; but ->
As this is a VM, and the error is that it can not find a screen ...
Is there a  "guest-sessions /guest-additions " application that should be installed ?

[INDENT][INDENT]seems reasonable
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-09-27
herculeesjr; Hey !

See if this sheds light on our subject:
[http://www.mesa3d.org/vmware-guest.html](http://www.mesa3d.org/vmware-guest.html)
looks like:
```

apt-cache show xserver-xorg-video-vmware

```

whattaya think whatta ya think

---

### Post by Bucky Ball on 2015-09-27
When you get to the first screen you show which gets stuck, the 15.04 with the dots, does anything happen when you hit F6, shift, escape or space bar?

---

