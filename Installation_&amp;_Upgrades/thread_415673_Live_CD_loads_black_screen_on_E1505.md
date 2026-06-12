---
title: "Live CD loads black screen on E1505"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by slugicide on 2007-04-20
When I tried to load the live CD on my Dell E1505 the screen went black and useless.  I read somewhere that you could use F4 to adjust your screen resolution and maybe fix this.  I tried but there is no option of 1680 X 1050 and when I use another option it goes to the command line.  
Is there a fix for this?

---

### Post by thayerw on 2007-04-20
There is a fix:

When the screen goes blank and the CD spins down, do the following:

[LIST=1]
[*]Press CTRL+ALT+F6
[*]Type:
[B]sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo startx[/B]
[/LIST]

This should get the desktop GUI loaded and from there you should be able to proceed with the installation.  After the installation, you may need to repeat this process when you start the notebook for the first time without the Live CD.  At that point it should be fine.

My question is why did they release the final Feisty knowing this bug existed for hundreds (if not thousands) of users?

---

### Post by slugicide on 2007-04-20
Thanks for answering!  I also cannot believe that Ubuntu doesn't support my *absolutely mainstream* computer (mid-priced Dell laptop).

---

### Post by slugicide on 2007-04-20
Pressing ctrl+alt+F6 has no effect.  No command line.

---

### Post by thayerw on 2007-04-20
Hi slugicide, I'm sorry that didn't do the trick for ya.  If you're still trying to get it working, give this a shot:

Boot the Live CD and when the options menu appears, press F6
Replace "splash" with "single"
Press enter

This should put you straight to a command line.  Then you can follow the directions I outlined above.  Good luck and I hope you find a solution.

---

### Post by odelay on 2007-04-20
> **thayerw said:**
> My question is why did they release the final Feisty knowing this bug existed for hundreds (if not thousands) of users?

Good question...however I'd say there are more than a few thousand people affected by this.  It's not just people with Dells or HPs.

I'm kinda waiting it out for no particular reason.  I know I can easily install the fglrx drivers on the live CD, then on the clean install again (I was going to anyway)...I'd just rather wait till they get the bug fixed.  I was so excited for Feisty...this has kinda killed that for me.  I don't even want to install it now.

I don't suppose they'd release a Feisty 7.04.1??

---

### Post by slugicide on 2007-04-23
> **thayerw said:**
> Hi slugicide, I'm sorry that didn't do the trick for ya.  If you're still trying to get it working, give this a shot:

Boot the Live CD and when the options menu appears, press F6
Replace "splash" with "single"
Press enter

This should put you straight to a command line.  Then you can follow the directions I outlined above.  Good luck and I hope you find a solution.


Thanks!

---

### Post by kn1ghtmare on 2007-04-24
After it boots and you get the black screen, do an alt+ctrl+f3. Once you're at the terminal, type:

Xorg -configure

This will rebuild X and make a new file, /etc/X11/xorg.conf.new . After it builds this file, move it to your xorg.conf file by typing:

sudo mv /etc/X11/xorg.conf.new /etc/X11/xorg.conf

After you're done, type startx and you should get a GUI. I was having problems installing the ati driver so I tried the x64 version. Oddly enough, the 64bit version works great (core2duo is 64bit, core duo is 32bit) while i386 is messed up. Go figure. Good luck!

---

### Post by Praill on 2007-04-25
Well, we cant get too mad. Fiesty is in BETA, and this is the sort of thing youd expect.
This is a legitimate bug though. Im using the inspiron 6400 (e1505) with the ati x1400 and receiving the exact same problem.
Alt+CTRL+f6, Alt+CTRL+f3, and changing boot option from 'quiet splash' to 'quiet single' or to 'single' all does nothing.

If there's a working solution out there I would be eager to receive it.
Im actually perplexed that its so difficult (or maybe impossible) to install from command line.

---

### Post by odelay on 2007-04-25
> **Praill said:**
> Well, we cant get too mad. Fiesty is in BETA, and this is the sort of thing youd expect.

O RLY? :D

---

### Post by Praill on 2007-04-26
Ok I've figured it out! I am actually posting this from the Live CD.

I'll make my instructions more specific after I install feisty and can go back and re-do what I did.


1 - on the first load screen hit F6 and change 'quiet splash' to 'single' (without quotes of course). Also add vga=771 somewhere in this option list. I added it before the **whole** "quiet splash" option (not just the quiet splash part itself but the whole option string).

2- Alt-Ctrl-F6 will now work. So once the loading screen pauses for a bit on one of the options hit it, it will take about another 30 seconds and then you will have a command prompt.

3- I ran into another snag here: my wired connection wasnt resolving a DHCP server, but I got it to work with wireless. If you run into the same problem it is easy to set up wireless. First, take off any encryption you have on the wireless signal. Second make sure your wireless hardware switch is on :). Third, execute 'iwconfig eth1 essid network-name (replace eth1 with your wireless interface and network-name with your networks ssid). Fourth, execute /etc/init.d/networking restart.

4- Now do as instructed above. sudo apt-get update ... sudo apt-get install xorg-driver-fglrx

5- Set X to use the fglrx driver. sudo pico /etc/X11/xorg.conf and change the line **vesa** to **fglrx**

6- now type /etc/init.d/gdm restart


You should be good to go. I havent tried to install yet but this has at least got everything loaded.

Good luck.


*Update: install went fine.. been up and running great.*

---

### Post by strabes on 2007-05-16
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3)

Or just use the alternate CD since all of the hardware on inspiron laptops has full support anyway.

---

