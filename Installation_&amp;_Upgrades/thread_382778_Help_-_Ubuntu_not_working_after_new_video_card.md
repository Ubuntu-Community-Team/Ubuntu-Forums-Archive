---
title: "Help - Ubuntu not working after new video card"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by W@LT on 2007-03-12
Hi

Ubuntu was working fine untill I installed a new Graphics Card (GeForce NVidia 7600 GT)

On boot up it goes through the normal wake up screen and then goes into a terminal mode state very similar / equivalent to the old DOS Prompt screen.

I guess that the problem is something to do with Ubuntu not recognizing the Graphics Card and not being able to suggest the right drivers.

As a complete novice I am stumped and would welcome any help on recovering the situation

Any suggestions on how I proceed from here?

Thanks

W@LT

---

### Post by kokiri on 2007-03-13
Ok, since you bought this card for all the fancy features this card can do we'll get everything working for you.

At the prompt that comes up, login like you normally would with your user name and your password
keep in mind that your password won't echo anything back to you stars or anything, if you typed it just hit enter and don't worry.

First things first lets get the drivers needed installed
```
sudo apt-get install nvidia-glx
```
That will go out and grab the correct nvidia drivers and modules
After that finishes type: 
```
cd /etc/X11 && sudo nano xorg.conf
```

Find your old video card config by finding this section: (you can scroll up and down using the arrow keys)
```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL" (this will be different for your card, obviously)
        Driver          "i810" (this will be different and tuned to the old card)
EndSection

```
The above is from my file your's would be different but the Section "Device" will be the same and that's where you'll want to edit.

Change the Identifier (the text inbetween the "") to something generic like "New Card"
Change the Driver to "nvidia" exactly like that as that will be the new driver
So then it would look like this in this example:
```
Section "Device"
        Identifier      "New Card"
        Driver          "nvidia"
EndSection

```
Next find the: 
```
Section "Screen"
        Identifier      "Default Screen"
        Device         "Intel Corporation 82845G/GL" (you change this line)

```
Section and change the Device line to the new Identifier line, in this example it would be changed to "New Card" 

Now save the file by pressing ctrl-o and answer Y and exit out of nano by ctrl-x
You should be back to the DOS like prompt

We need to do one more thing and then you'll be able to restart and have a good time with the new graphics card.

Type:
```
cd /etc && sudo nano modules
```

At the bottom of the file type nvidia and then ctrl-o answer Y and then ctrl-x like we did before

Then finally type sudo reboot

Enjoy!!! After the reboot your card will be ready to rock and roll!!!

---

### Post by W@LT on 2007-03-13
Sorry

But I seem to have failed at the first hurdle!!

It download the package but then I get the error below:

The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4492kB of archives.
After unpacking 13.7MB of additional disk space will be used.
(Reading database ... 112572 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.9631+2.6.20.3-10.9_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.9631+2.6.20.3-10.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.9631+2.6.20.3-10.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas where to go from here?

Thanks

W"LT

---

### Post by dannyboy79 on 2007-03-13
what you should do is manually edit your xorg.conf and change the "driver" to vesa. then download envy ([http://albertomilone.com/nvidia_scripts1.html)](http://albertomilone.com/nvidia_scripts1.html)). it's awesome. use it to first uninstall, then restart x, then use it to install your nvidia driver. good luck

---

### Post by W@LT on 2007-03-13
Xconfig is already showing Vesa

And the link provided seems to go nowhere..

Still stuck :confused:

---

### Post by dannyboy79 on 2007-03-13
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

ok, so with vesa, you at least have x-server running? gnome or kde is running? you're right, I tried the link, but went there again and this is it???? if it doesn't work again, just remove the end and go to his home site first, then projects, then envy. [www.albertomilone.com](www.albertomilone.com) is his home site.

---

### Post by W@LT on 2007-03-13
Great!!

OK I have got the card working...

It seems to be working OK... some nice resolution when trying out the Screensavers but the text on the screen looks really naf... I am sure that there must be an adjustment somewhere.. :confused: 

OK... the next thing is to try and get Beryl installed ... I am running Feisty and have tried the tutorials but it does not seem to load..

Any ideas on this one??

Thanks

W@LT

---

### Post by dannyboy79 on 2007-03-13
i don't use beryl so I can't help. there are many guides but try to read a current one. also, if you don't like the font, can't you check font smoothing or something like that within nvidia-config? it should be in your pul down menu now. otherwise, maybe try ttf fonts? again, I don't play around with fonts so not sure. glad your card is working. can you please post how you got it instead of just saying you got it, this way others can benfit from your hard work. thanks

---

### Post by W@LT on 2007-03-15
Thanks .... I managed to get the NVidia card working by downloading the latest drivers from the NVidia web site and using those... it seemed to work first time!!

The only issue I have now is that although I set up the resolution (1400 x 900) in the NVidia control panel and save it .. the next time I boot up it has forgotten the settings..

The font issue still is a problem.. I have tried selecting different fonts from within Ubuntu but they all seem a tad blurd... 

Oh Well .. at least I am making progress...

W@LT

---

### Post by FruitieX on 2007-03-15
Hi W@LT, I just registered into this forum just to post this :) (Thanks! :D). You could try "sudo dpkg-reconfigure xserver-xorg" from a terminal (the "command line") and from this little setup tool chose your resolutions that your screen supports. Use tab to switch to the ok button if needed ;). The best resolution will be used when the X server is started. Remember to back up the file /etc/X11/xorg.conf as it will be overwritten with all its settings! From here you might also get your refresh rate correct if you had problems with it... I'm @ work now do I'll help you more when I come home. 

PS. The first screen asks for your driver. Chose "nvidia" and not "nv"!

I'll also post a link to an easy beryl setup when I am home at my own PC. It's then as simple as aptitude install beryl :) (You just have to add the repos that I don't have right at the moment) [http://ubuntu.beryl.com](http://ubuntu.beryl.com) something? Don't try that just yet :).

Good luck!
FruitieX.

---

### Post by FruitieX on 2007-03-15
SORRY for doublepost


There ya go (Feisty only,you have to upgrade to it if you already haven't*, I personally think it's stable enough and I like to have the latest available programs/daily upgrades/brand new features, anyway the feisty repos got beryl v2.0 today at the morning :)): Try the 123 NoFile Automatic Installation Method. They say it has broke some instances but it didn't for me. Well I had the exactly same problem once and I had to reinstall the nvidia driver at each reboot (from the nvidia.com website), but then i removed the nvidia kernel modules with aptitude, reinstalled the official nvidia drivers and it worked perfectly then. I am anyways using Xfce4 with this because of the gnome-panel got broken once (now it's fixed) and i have never used gnome after that, might do it again sometime, or not! AND IT'S FAST!! Xfce4 is almost perfect for my needs! The only 2 things that I'm missing are that the panel background would be transparent and that the screensaver would work... Sure I'll fix em' one day. Otherwise fast and great. I'm still a linux newbie :). Enough off-topic talking here: 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia)

Hope it won't break your system... I don't think so but you never know... IF it does you should always be able to switch to the vesa driver and troubleshoot. (if you aren't familiar enough with the "command line")

The way I installed these was the following:
I did the 123 NoFile Automatic Installation Method step and got beryl up and running with autostart and everything. And as I said, I want my pc to be up to date so I did the Add beryl repositories and install Beryl step. Well actually I only added the repos manually and did aptitude install beryl (As superuser). After this, beryl is now upgraded when I run aptitude update;aptitude dist-upgrade or use the ubuntu upgrader program. 

I don't think this had much to do with the topic but I helped him to install beryl ^.^

Again, Good Luck! :)
FruitieX

* = Edit: I see that you are running Feisty already :D

Edit2: If you get into trouble, you can PM, e-mail, or chat with me on MSN or IRC (if you find me on IRC, I should be on the #nexuiz or #nexuiz.pb channel in irc.quakenet.org after 4 hours;)).

---

### Post by dannyboy79 on 2007-03-15
> **FruitieX said:**
> The only 2 things that I'm missing are that the panel background would be transparent and that the screensaver would work... Sure I'll fix em' one day.  

I use Xubuntu Dapper, you can enable the xscreensaver, it works just fine with my laptop.\
heres a guide:
[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---

### Post by W@LT on 2007-03-15
j

---

### Post by W@LT on 2007-03-15
Hi FruitieX

Thanks for all the info

All working well.... One minor issue which I am sure is a setup problem

At the moment the Beryl cube is the height and width of the monitor screen... however in all the good demo's I have seen the cube is withing the screen.. (if you know what I mean)

How do I set it up to work like this

Last question... Honest :) 

W@LT

---

### Post by FruitieX on 2007-03-15
Fire up the beryl settings manager (from the red diamond in your system tray, it SHOULD be there, otherwise fire up a terminal and run beryl-settings), go to Desktop, then Rotate Cube, *Expand the General umm.. let's call it a tab until someone finds a name for it? :D and from here select your value into Zoom. The bigger the value, the further away from the cube the camera will be. (This is what makes me sleepy all days, too much tweaking of different settings. Make sure you won't get hooked!)

:D

*=Edit: Forgot that you have to expand this "tab". Nothing urgent, you would have figured it out yourself too :)
FruitieX.

---

### Post by FruitieX on 2007-03-15
And hey, thanks dannyboy79 for the howto link! :lolflag:

---

### Post by W@LT on 2007-03-16
Thanks... yes I have opened the Beryl Manager and expanded the General Tab (thingy!!) and I have played with all the settings but nothing seems to change .... 

I do not seem to have a ZOOM button or slider... is it called something else??

As for being hooked... I have been trying to get this thing to work for a week now and on the verge of a divorce... I fear that there is a lot more interesting things to do :( 

Thanks for all your help

W@LT

---

### Post by W@LT on 2007-03-18
Hi

Everything now working OK :) 

I decided to do a complete re-install from scratch..

I have reverted to Edgy rather than Feisty and all is a lot more stable..

Thank you all for your help..

W@LT

---

