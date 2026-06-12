---
title: "Workaround: Boot Feisty Live CD with ATI X1400 (Dell 6400)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by thayerw on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

If your Live CD keeps booting to a blank screen and you have an ATI X1400 (or similar ATI card) chances are this workaround is for you. In my case, it worked for my Dell Inspiron 6400:

[LIST=1]
[*]Boot the Live CD as normal
[*]When the screen goes blank and the CD spins down, press CTRL+ALT+F6
 (you can also press Ctrl+Alt+F6 if you receive an X error instead of a blank screen)
[*]Type: 
[B]sudo -s
apt-get install xorg-driver-fglrx
aticonfig --initial
startx[/B]
[/LIST]

This should get you to the desktop... if you use the Live CD to perform a full installation, you may need to repeat this process when you start the notebook/PC for the first time without the CD.

Cheers, 

~Thayer

---

### Post by bro on 2007-04-20
stupid question, but would this need a working internet connection? (meaning: should i configure my wireless wep keys over the commandline first?) Or does it install the driver from the cd?

---

### Post by felixfurtak on 2007-04-20
Can report the following procedure works for Ubuntu Feisty 7.04 (final) live cd to at least boot into gnome:-

1. Boot CD as normal. 
2. Select Safe Graphics Mode
3. Press F4 and Select 1024x768x16
4. Press F6 and remove options for quiet and splash
     Eventually you get the X server fail to start and end up in the command prompt
5. Plug in your wired network connection (wireless may work, but didn´t for me since I have intel 4965agn - but that´s a different story) so that it can dhcp to your router
6.  sudo apt-get install xorg-driver-fglrx
7.  sudo nano /etc/X11/xorg.conf 
8.  In Section ¨Device¨ change ¨vesa¨ to ¨fglrx¨
9.  CTRL-X to save
10. sudo /etc/init.d/gdm restart

You should then be into the live CD. That´s as far as I´ve got.  Installation process can then be done as normal (i think).

---

### Post by carpex on 2007-04-20
Installing fglrx worked for me with the live cd, but I had to configure my static wired connection manually ([http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)) and I had to edit /etc/apt/sources.list to uncomment the debs there. I don't think fglrx can be pulled from the cd.

GL

---

### Post by thayerw on 2007-04-20
Wireless probably won't work out-of-the-box, because I don't think network-manager is loaded at this point, but wired network connections should work fine without configuring anything.

Also, there's no need to modify the apt sources beforehand, at least there wasn't in my case.

---

### Post by bro on 2007-04-21
ahh.. the above by thayerw worked for me with Kubuntu. At least for starting the live cd. (I typed slightly different and more elaborate): 
> 
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx


thanx!
I'm quite confident it will install now as well. I'll report back if it did. Might take a few hours though. I'm going to format my entire system - and the weather is nice outside.

Okay, I've got everything installed now, works like a charm! 

p.s. Nice to see how after my fresh windows install (with the recovery cd that's supposed to match my laptop) which I also just did *nothing* works. No ati-drivers installed, no internet, no proper playing of media formats... and of course no other progs then just the OS and patience... Are people still actually using this other OS? For any other reason then not knowing any better? Ubuntu should definitely be able to fix bug #1.
(don't ask, I installed it on a 15gb partition in case anybody decides to mail me one of those 'other' formats - unfortunately this happens sometimes)

---

### Post by nunes on 2007-04-23
Hi,

first post ever here btw ;)

I came here in search for help to install Feisty on my new Fujitsu laptop with a X1400.

I come here often when I have a problem with my Ubuntu (been using it for a few years now) or when I want to install something and can't do it on my own (like Beryl).

This time I had to reply to thank you for this guide, as I was already climbing the walls in despair for not being able to use Ubuntu on my new laptop.

Thank you **thayerw** and **bro** ;)

Note: I had to repeat the guide after installation to get it to work, but it is working :D

~ Nunes ~

---

### Post by MasterRoshi on 2007-06-14
alright...my first post. im pretty excited to be using ubuntu...being a total n00b to linux and w/e. i just wanted to contribute a little saying that wireless DID work with my new e1705 notebook.

it has an Intel PRO/Wireless 3945 802.11a/g Mini Card (54Mbps) for Inspiron 9400/E1705...and it runs natively in linux. im assuming wireless works with anything thats native. 

well thats it for my first post; really glad to be here :D

---

### Post by bro on 2007-06-15
Welcome to the club of satisfied computer users.. In my experience these forums are very fast and helpfull. Often the answer is already posted somewhere for you. You succesfully installed your ati-drivers? Then please talk [about your happiness here]("http://ubuntuforums.org/forumdisplay.php?f=103"). 

There is place for everything...

---

