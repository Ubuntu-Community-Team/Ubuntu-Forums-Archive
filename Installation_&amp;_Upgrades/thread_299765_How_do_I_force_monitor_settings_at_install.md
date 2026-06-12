---
title: "How do I force monitor settings at install?"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by xweaklinkx on 2006-11-14
Hello,

I'm having a problem installing Ubuntu due to my LCD monitor. I have a Dell Dimension E510, a Dell 1907FP Flat Panel Monitor, and ATI PCI_E x16 X600. On booting the Ubuntu installation disk I see the initial splash page correctly. As Ubuntu begins to install I recieve this text:
> 
2:Digital Input 
Cannot Display this Video Mode
Optimum resolution 1280 X 1024 @ 60hz


At this point the whole screen is blank besides this error message, and it just sits there. I have to manually oscillate the switches at this point. (shut off power) I am fairly sure this is a monitor error. Via googling I've seen some posts suggesting the monitor is reporting itself as capable of 70hz at higher screen resolutions which the monitor can not do. I have seen other posts suggesting that the monitor will work fine if set to 60hz. I think perhaps there has been an error at Dell as their product specs list this monitor of being capable of higher resolutions but this error evidently implies that is untrue.

I know I can use the monitor with Linux, as I am presently using the Knoppix live cd, as I've already formated my Windows, Dell Restore, and Dell troubleshooting partitions. Knoppix on booting will flash several times when trying to start the x server, and retry's using VESA which then works, absolutely fine. I don't quite understand what VESA is, after doing some initial quick reading.

What I would like to know is what command I need to make at the boot up splash screen to force Ubuntu to use 60hz, or alternately VESA.

Things I have tried that have given me the exact same error message:
[LIST]
[*]Ubuntu 6.10
[*]Ubuntu 6.06
[*]Ubuntu Alternative CD
[*]Older Versions of Ubuntu, specifically Hoary Hedgehog
[*]Gentoo LiveCD
[/LIST]

Any help is greatly appreciated. Thanks.

---

### Post by xweaklinkx on 2006-11-19
I've made some progress on this. I've got Ubuntu installed, but it gives me a blank screen and locks up, I'm assuming when it tries to start the X windows server. 

What I did was to use the Edgy Eft 6.10 alternative CD. (This is available on the bottom of the download page.) On the splash screen I chose text install and then option F6 and typed in:

```
Linux vga=771
```

**Note:** when you press F6 you will get a text box with a bunch of gobble-dy-gook already typed in. If you don't know what the gobble-dy-gook  means then leave it alone and type the above kernel option at the end of the gobble-dy-gook.

If you review all the options vga=771 is listed as the option to use for laptops with display problems. I figured since a laptop has an LCD and I'm having problems with my LCD I'd give it a try. I was able to get the install boxes and set everything up. **Note:** Text install would not work until appending the vga=771 option. Without that option it responded just like I described in my previous post.

My next goal is to play with either my X configuration, whatever that file is called, or try to use a different driver. From my reading, some folks suggest using the fglrx driver for ATI cards. I am assuming that I'm not presently using the fglrx driver, but I don't know how to check-- yet.

Again if anyone has ideas, and wants to save me on time, I'd love the assistance, otherwise I'll update more when I make progress to help other folks out.

---

### Post by triwave on 2006-11-21
Hi - I'm a noobie to ubuntu (and linux) and have been trying to get an installation on my Dell D610 laptop. The 6.06 LiveCD runs great so I decided to install - but it dies during install. 

I have tried several ways - graphical way from desktop of live CD, text method and also Xubuntu LiveCD. I researched a bit a thought installing from text (alternate CD) would be best bet - it does everything untill it switches from the basic ASCII graphics and progress messages to try to load a graphical window - then it hangs. Display freezes with a couple squares on it. CD whirs for a while and then all goes quite. ctrl-alt-del restarts the machine but I can't seem to do anything else.

xweaklinkx - I was wondering if you had any flakey display issues during install? It sounds like you installed successfully but can't run; I ran CD fine but can't install. 

I was thinking to try your command but hesitate to experiment too much - the install process is quite a long thing. Anybody know what the issue is here and a direct way to solve it?

Odd ... if it's a video card or gui issue why does it run flawless with a LiveCD ? 

Help is appreciated - I really want to try this Linux thing!! ;)

---

### Post by xweaklinkx on 2006-11-23
Hi Triwave,

I'm definately no master at Linux, but if the Ubuntu Live CD is running fine for you then you are experiencing a different problem than I am. I can't run the LiveCD. The only LiveCD that I know works for me is Knoppix.

Now to answer your question about flakiness-- it installed fine, but locked up after rebooting when trying to run X-Windows. That sounds like the same spot yours is hanging. Do you know what you are using for video on your laptop, Video card, onboard video? I haven't had the time to goof around and try to mess around with fixing mine, but will be doing that later this weekend.

---

### Post by xweaklinkx on 2006-11-23
Alright. I have the problem fixed. I'll give a quick run-down, because I need to finish Thanksgiving dinner, I should have a better write up that I'll stick on my blog before the week-end is over. This is for Edgy Eft i.e. Ubuntu 6.10 but I bet 6.06 will setup the same. It is also for my particular computer, you'll want to know your monitors native resolution. Also note that it is only for folks who need the fglrx ati driver. So here's the steps.
[LIST=1]
[*]Get the Alternative Ubuntu Installation CD. Scroll down the download page and choose, "other installation options" for the mirror nearest to you. Choose the Alternative CD. Download and burn the iso image.
[*]On the startup screen press F4, and choose your monitors native resolution. That's 1280x1024 for the Dell 1907FP. Then choose install a command-line system. Press enter.
[*]Go through the install process, fill in the blanks, follow the install instructions. You'll be asked to remove the CD when done, the computer will reboot, do some stuff, and then give you the log in prompt. Log in with the user name and password you created during the install process.
[*]Type:```
sudo nano -w /etc/apt/sources.list
``` 
You'll be asked for your password, and then you'll see a file. Find the lines that don't start with #, add the terms universe and multiverse to the lines that contain the words edgy and edgy-updates,and the term universe to the lines containing security. The six lines should read thusly when you are done:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe

```
Press CTRL-X , and type Y to save.
[*]Type: ```
sudo apt-get update
``` It may ask you to reinsert the install CD, you should do that if asked.
[*]Type: ```
sudo apt-get install x-window-system-core x-server-xorg-core xserver-xorg-input-all xserver-xorg-video-vesa
```Pay attention to the last one there is no hyphen between x and server. So that should have installed everything you need for X windows. so...
[*]Type: ```
startx
``` If everything is working properly you should have a cursor in the shape of an x that you can move around, and a text box in the upper left of your screen. If so click that text box and type: ```
exit
``` That will put you back to the text mode... you might be able to do the rest from that x terminal-- but I didn't, so...
[*]Type one then the next: ```
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
```
That will take you through the x-windows configuration again. After you finish that...
[*]Type: ```
 sudo apt-get install gnome-core gdm synaptic gnome-system-tools file-roller
``` That installs gnome stuff if you want a different manager like kde you'll need to look up those for yourself for now.
[*]Type: ```
startx
``` If everything went right you should see gnome and you can use synaptic to add whatever other bits and sundries you wish.

[/LIST]

**Note:** you may need to to run pppoeconf if the install cd wasn't able to figure out your internet stuff. You do that by typing: ```
sudo pppoeconf
```

If you have problems let me know. If you want to point out the flaws in my newb hack-ery, please do.

---

### Post by madcow72 on 2006-11-23
Hey!

Just read through your guys' problems.  I've only been using Linux for about 3 months, but had a suggestion:  xweaklinks, when your computer seems to stall during bootup, can you do a CTRL-ALT-F2 (F6,F7,F8,or F9 even) to get to the shell?  My guess is your monitor isn't being recognized correctly and you need to do:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` After you enter your password, this will reconfigure X and you can choose to manually input your monitor settings.  You need to know not only the accepted resolution, but also the vertical and horizontal refresh rates for your model.  ```
 Horizontal: 30 - 81 kHz
Vertical: 56 - 76 Hz
``` Those values came from the Dell website, using the model number you mentioned earlier. After reconfiguring, see if you can then start up into X-Windows. I think this, if it works, will be a much easieir way to get you going, although triwave had a very nice, detailed way that may also work.

Good luck!

---

### Post by xweaklinkx on 2006-11-24
Hi Madcow72,

I was curious so I tried switching consoles (alt + (f2, f6,etc.)) when I got the monitor error on the installation/livecd. You aren't able to switch between consoles so the method you outlined won't work. Thanks alot for trying to save folks some time.

---

