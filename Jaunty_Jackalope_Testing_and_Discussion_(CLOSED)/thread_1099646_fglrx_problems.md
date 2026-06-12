---
title: "fglrx problems"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Woody1987 on 2009-03-18
Im having problems with the new fglrx drivers that were made available recently, im talking about the 9.4 beta drivers that amd let the ubuntu developers use. These drivers DO support xserver 1.6 but im having trouble using them. I can install them just fine but when i get to the log on screen i get a garbled screen. Im using jaunty with all latest updates and an ATI/AMD Mobility 3650HD which according to AMD is supported. Anyone else have problems with these new drivers?

Heres a link to the article telling me about them [http://www.phoronix.com/scan.php?page=news_item&px=NzE0Nw](http://www.phoronix.com/scan.php?page=news_item&px=NzE0Nw)

---

### Post by MALEADt on 2009-03-18
+1 on troubles, having a HD4870 (r700 is supported too, I guess?) I only got presented a GDM screen full of artefacts and a locked up system.

---

### Post by helliewm on 2009-03-18
Snap I have an ATI4850 and am having the same issue. Unsure what to do about it? I have read sudo dpkg-reconfigure xserver-xorg is no longer useful? Did try it to no avail.

When it boots I can see the fglrx drivers loading and its says so OK but obviously its not OK!

Anyone any ideas?

Helen

---

### Post by Woody1987 on 2009-03-18
Happy im not the only one :)
Upset that no one has a fix...yet :(

---

### Post by helliewm on 2009-03-18
I found this [https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html](https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html) I followed the instructions in the link and removed -ati but still fglrx does not work so I reinstalled -ati and at least I have 2d but no flgrx drivers.:(

At least I can use Jaunty. I think this needs a bug report.

Helen

---

### Post by gunksta on 2009-03-18
I tried them, and they failed.

Card - FireGL 9000
Release - Updated Kubuntu

KDM generates a series of really lovely scratches and garbles across my screen. However, my computer was not locked up. I was able to press on the power button and Kubuntu recognized the input and shut itself down cleanly, rather than forcing me to do a hard reset.

Previously in the Jaunty development, I black-listed fglrx, but was able to leave it installed. For some reason after today's update this no-longer worked and I was forced to remove fglrx from my system completely. 

Oh well. I have confidence that this will be resolved before Jaunty is released.

---

### Post by laborg on 2009-03-18
i had the same problem, but just replacing the xorg.conf with the previous one (still from intrepid, updated 1 week ago) solved it.
```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


```

---

### Post by zika on 2009-03-18
> **laborg said:**
> i had the same problem, but just replacing the xorg.conf with the previous one (still from intrepid, updated 1 week ago) solved it.
so You have working fglrx? which card? did You gain anything by using it compared to xorg-ati? compiz? (I do not use it but it is a good indicator)

---

### Post by rbmorse on 2009-03-18
I've got a 4850 and it's working fine with the 8.6 FGLRX package. 

Did you open a terminal and run the commands:

sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv

after installing the driver package?

I did a system restart after installation and configuration, but I don't know if that's really necessary

---

### Post by zika on 2009-03-18
> **rbmorse said:**
> I've got a 4850 and it's working fine with the 8.6 FGLRX package. 

Did you open a terminal and run the commands:

sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv

after installing the driver package?
did You get any side-effects. what is the comparison to xorg-ati?

---

### Post by laborg on 2009-03-18
> **zika said:**
> so You have working fglrx? which card? did You gain anything by using it compared to xorg-ati? compiz? (I do not use it but it is a good indicator)

My restriced driver page says, that ATI Fire GL is loaded. I own a Ati 4670. Compiz is working...

---

### Post by Woody1987 on 2009-03-18
> I've got a 4850 and it's working fine with the 8.6 FGLRX package.

Did you open a terminal and run the commands:

sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv

after installing the driver package?

I did a system restart after installation and configuration, but I don't know if that's really necessary

Thx, worked like a charm

---

### Post by rbmorse on 2009-03-18
It's a bit "crisper" but the real change is that it works at all with Jaunty.  

I just noticed one "bug" in that TVtime works with Compiz (desktop effects) enabled (no flicker) until I try and resize or move the TVTime window. That causes it to go black and and does not come back.

---

### Post by gunksta on 2009-03-18
I can't wait to get home to try this.

---

### Post by zika on 2009-03-18
thank You all for support! it works! :)

---

### Post by helliewm on 2009-03-18
Brilliant thanks so much, that works with an ATI4850. Compiz works so I have my cube and wobbly windows:D:D

Helen

---

### Post by Ubuntiac on 2009-03-18
Obvious question...

How do you actually install the new drivers? I've installed FGLRX many times before, but restricted driver manager shows as completely empty despite me having an ATI HD4850. I've updated / upgraded, but still nothing.

How is everyone else installing? Envy? Restricted manager? The manual method at [cchtml?](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by helliewm on 2009-03-18
The upgrade did not work for me so to be simple I opened Synpatic searched for fglrx uninstall the ati radeon drivers (they also appear with this search) and then installed the fglrx drivers.

Once you have done this open the Terminal and runs these commands.

sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv

Lastly Reboot.

You could, of course, do this all in the Terminal but this saves some typing.:D

This is how I got fglrx working with my ATI4850.

Helen

---

### Post by zika on 2009-03-18
> **helliewm said:**
> The upgrade did not work for me so to be simple I opened Synpatic searched for fglrx uninstall the ati radeon drivers (they also appear with this search) and then installed the fglrx drivers.
Once you have done this open the Terminal and runs these commands.
sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv
Lastly Reboot.
You could, of course, do this all in the Terminal but this saves some typing.:D
This is how I got fglrx working with my ATI4850.
Helen
You do not have to uninstall either radeon nor radeonhd.

---

### Post by helliewm on 2009-03-18
I did because I had installed trying to find a solution. From what I read they would clash with fglrx.
See my earlier post on Page 1 with the temporary solution and links to what I read from a Ubuntu Developer I believe. 

Helen

---

### Post by gunksta on 2009-03-18
You could blacklist them, so they don't load, rather than uninstall.

---

### Post by Woody1987 on 2009-03-18
> Obvious question...

How do you actually install the new drivers? I've installed FGLRX many times before, but restricted driver manager shows as completely empty despite me having an ATI HD4850. I've updated / upgraded, but still nothing.

How is everyone else installing? Envy? Restricted manager? The manual method at cchtml?

sudo apt-get install xorg-driver-fglrx

---

### Post by zika on 2009-03-18
I have both radeon and radeonhd installed beside fglrx and they do not make any difference.

---

### Post by helliewm on 2009-03-18
Done now, yes I agree I could have blacklisted, I was feeling lazy so just fired up Synaptic:D

Helen

---

### Post by helliewm on 2009-03-18
> sudo apt-get install xorg-driver-fglrx

Yes that is correct.

Helen

---

### Post by helliewm on 2009-03-18
> I have both radeon and radeonhd installed beside fglrx and they do not make any difference.

That is interesting see here when the FGLRX Drivers where announced today it says they can conflict. This is what I was working from and how I found a temporary fix.

[https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html]("https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html")

Helen

---

### Post by zika on 2009-03-18
> **helliewm said:**
> That is interesting see here when the FGLRX Drivers where announced today it says they can conflict. This is what I was working from and how I found a temporary fix.
[https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html](https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html)
Helen
it seems that it is a bit outdated. I'm happy that I can keep all three of them, getting them updated and being able, with minor adjustments, to switch between them ... :)
video in Xv with compiz on, again, does not work and frezes my machine rock solid until REISUB. I do not even use compiz but I just tried. in metacity everything works nice. I did not try X11 as video output, probably I will later. like going to school again ... :)

**update:** this driver has big issues with Shiretoko (that is what I have tried): if I open one window and let music play in it (Deezer for example) and open another window in another workspace with Youtube music freezes and that window is ready for closing. if I open one Firefox window with music Shiretoko does not influence it. it worked perfectly with xorg-ati. You win some and You lose some ... :) as I said we are going to have lots of upgrades until it is mature. beware that tweaks are not written in the xorg.conf but in the /etc/ati/amdpcsdb and You can manipulate these only with aticonfig (read help) as You can see in my posts in [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593) way back ... :)

**update:** same thing happens if I use Firefox in two windows. so, it is not the Siretoko bug but it can be attributed to fglrx. it, somehow, interferes with any kind of multimedia ... we'll see ... on xorg-ati it was all clean and stable. now I will have to go through my notes to see how I can remove fglrx from kernel (dkms remove fglrx, as I recall) ... and, probably go back to xorg-ati. the only thing that is keeping me for now from doing that is the fact that the speed gain is respectable. I mean compared to xorg-ati, not to 9.2, it is the same as 9.2 in Ibex. Tormod is doing better job than fglrx ... I hope he will come soon with better (open-source) driver. we'll see...

**just a thought: **or, maybe these problems that I'm having might have somehing to do with conflicts You've mentioned. I will investigate that ...

I would be grateful if someone who unistalled radeon and radeonhd could try to replicate these problems so I do not have to go through the whole process ... :)

It seems I have solved it (in metacity at least) but I'm not sure how. At least I'm sure I did not remove anything ... :) Radeon and radeonhd are still here.

---

### Post by rbmorse on 2009-03-18
I don't see that here.  4 firsfox windows each with a different youtube clip....OK.

Firefox, VLC, TVtime all showing at the same time...OK.  Can move, resize mimimize and restore any windows without problems.  Scrolling in windows is smooth, responsive. 

All that without Compizx (which I don't normally use anyway). With Compiz if I move or resize a TVTime or VLC window it goes dark. Trying to decide whether to file the bug against Compiz or FGLRX.

---

### Post by DougieFresh4U on 2009-03-18
Being in a hurry I did not run these 2 commands

```
sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv
```

so of course you know what happened!! I am presented with blank screen upon boot up. Is there a way I can do these commands from recovery. 
I am kind of lost, thanks to my stupidity

---

### Post by zika on 2009-03-18
> **DougieFresh4U said:**
> Being in a hurry I did not run these 2 commands

```
sudo aticonfig --initial -f
sudo aticonfig --overlay -type=Xv
```so of course you know what happened!! I am presented with blank screen upon boot up. Is there a way I can do these commands from recovery. 
I am kind of lost, thanks to my stupidity
press Alt-Ctrl-F1 and You will get to CLI. login and do these commands. after that reboot with```
sudo shutdown -r now
```and You should be back home ... :)
You might want not to do the second command now. wait until You see if You like Xv output ... .;)

---

### Post by DougieFresh4U on 2009-03-18
> **zika said:**
> press Alt-Ctrl-F1 and You will get to CLI. login and do these commands. after that reboot with```
sudo shutdown -r now
```and You should be back home ... :)
You might want not to do the second command now. wait until You see if You like Xv output ... .;)

Thanks, back on track now :D:D

EDIT: I couldn't boot into .29 kernel which I have been using, but got into .28 kernel with out any trouble

---

### Post by zika on 2009-03-18
> **DougieFresh4U said:**
> Thanks, back on track now :D:D
EDIT: I couldn't boot into .29 kernel which I have been using, but got into .28 kernel with out any trouble
this starts to look like "Prison Break" ... :)

wait a minute what .29 kernel? ...

---

### Post by excogitation on 2009-03-18
I was facing the same issue as mentioned in the first post (Ati Radeon Mobility X700), but after removing the xorg-driver-fglrx package it works - even Compiz works fine.

---

### Post by gunksta on 2009-03-18
No dice for me. I have a Mobility FireGL 9000.

According to what I can find out on the web, I am supported up through fglrx 8.28.8, but that evidently only supports up through xorg 7.1, so I guess this isn't the version of fglrx provided by Jaunty (I am buying intel for all future graphics cards, I'm tired of fighting the complications imposed by wanting proprietary drivers).

But, when I look at the version of fglrx in Intrepid, it looks like it says (on my machine):

dpkg-query -l fglrx*
fglrx-driver-fglrx         2:8.600-0ubuntu1


So, what version of fglrx is this? Ubuntu's numbering scheme is different from AMD/ATI's.

I really don't want to use the radeon driver for this card. It's terrible.

---

### Post by zika on 2009-03-18
> **excogitation said:**
> I was facing the same issue as mentioned in the first post (Ati Radeon Mobility X700), but after removing the xorg-driver-fglrx package it works - even Compiz works fine.
I do not get it. which driver are You using now? You still have (DKMS) fglrx in kernel but no driver? what is in xorg.conf? sorry for asking so many questions but I did not get it when I read the first post and I still do not ... :-k

---

### Post by DougieFresh4U on 2009-03-18
> **zika said:**
> 
wait a minute what .29 kernel? ...
It's not officially in 'out' but there is a thread here with links to the .debs, I think it's up to '.29 rc8'

---

### Post by zika on 2009-03-18
> **gunksta said:**
> dpkg-query -l fglrx*
fglrx-driver-fglrx         2:8.600-0ubuntu1
```
dpkg-query -l fglrx*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  fglrx-amdcccle 2:8.600-0ubunt Catalyst Control Center for the ATI graphics
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-driver   <none>         (no description available)
ii  fglrx-kernel-s 2:8.600-0ubunt Kernel module source for the ATI graphics ac
ii  fglrx-modalias 2:8.600-0ubunt Identifiers supported by the ATI graphics dr
```

---

### Post by gunksta on 2009-03-18
Zika, thanks but it doesn't technically answer my question. That's where I got my initial numbers. What I can not seem to figure out is how these numbers relate to the official version numbers as released by ATI/AMD. They aren't organized in the same way. I'm just trying to figure out if my card is still supported or not.

---

### Post by zika on 2009-03-18
> **gunksta said:**
> Zika, thanks but it doesn't technically answer my question. That's where I got my initial numbers. What I can not seem to figure out is how these numbers relate to the official version numbers as released by ATI/AMD. They aren't organized in the same way. I'm just trying to figure out if my card is still supported or not.
9.1 was 8.573
9.2   is  8.582
this one 8.600
numbers are in order ... :)

---

### Post by rbmorse on 2009-03-18
and 9.3 should be 8.59x but I haven't actually seen that one, yet.  

The one we're talking about here is Catalyst version 9.4 which includes the FGLRX driver 8.60.

---

### Post by zika on 2009-03-18
I've just looked and most of people here are still using Ibex, at least according to information provided below Your user-name ... ;) so, just to make it clear ...

---

### Post by Devil_of_Chaos on 2009-03-18
I solved the problem at my laptop with 
start recovery mode got to root

apt-get purge fglr*
load default xorg.conf

then reboot normal

go terminal

apt-get install fglrx*

aticonfig --initial

reboot

this worked for me with ati mobility x3400

---

### Post by mortti on 2009-03-18
> **Devil_of_Chaos said:**
> I solved the problem at my laptop with 
start recovery mode got to root

apt-get purge fglr*
load default xorg.conf

then reboot normal

go terminal

apt-get install fglrx*

aticonfig --initial

reboot

this worked for me with ati mobility x3400

How does one "load default xorg.conf"? I tried this but found no restricted ATI drivers no more. The one I had was also gone. Should I do something with xorg.conf first or try to get the driver after the reboot and reinstalling the fglrx files? 

I've got a ATI Radeon 200M on my laptop.

---

### Post by rbmorse on 2009-03-18
Install the driver, then open a terminal and run:

sudo aticonfig --initial -f

This will cause a new instance of xorg.conf to be written. The old one will also be saved in the /etc/X11 directory.

---

### Post by mortti on 2009-03-18
> **rbmorse said:**
> Install the driver, then open a terminal and run:

sudo aticonfig --initial -f

This will cause a new instance of xorg.conf to be written. The old one will also be saved in the /etc/X11 directory.

For me being pretty amateur in all this: how do I install the driver as it cannot be found automatically? Does the one on ATI website do? 

BTW: Nothing actually seems different now when I don't have eighter the driver or the flgrx-files from the situation I had before all this. 2D, but everything works as it did before...

---

### Post by excogitation on 2009-03-18
> **zika said:**
> I do not get it. which driver are You using now? You still have (DKMS) fglrx in kernel but no driver? what is in xorg.conf? sorry for asking so many questions but I did not get it when I read the first post and I still do not ... :-k

To be honest I never had Compiz working without fglrx before - but it seems that it now runs with the opensource driver:
```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

I will still try to go back to the fglrx driver in a bit because it has like 3x the performance of the opensource one (maybe that's just felt, but that's all that matters, not?).

---

### Post by rbmorse on 2009-03-18
> **mortti said:**
> For me being pretty amateur in all this: how do I install the driver as it cannot be found automatically? Does the one on ATI website do? 

BTW: Nothing actually seems different now when I don't have eighter the driver or the flgrx-files from the situation I had before all this. 2D, but everything works as it did before...
Do not use the ATI Linux driver from the ATI site with Jaunty. It won't work. 

Also, I'm not entirely sure, but I don't think the driver we're talking about in this thread can be used with cards that do not have ATI RV6XX or RV7XX family chipsets (HD3xxx or HD4XXX). 

You can get this beta, pre-release Catalyst 9.04 for Ubuntu 9.04 (not any of the earlier versions) from The jaunty repository.  I used Synaptic with a search term of 

fglrx

If you select the main driver (something like xorg-video-driver-fglrx(?)) it will also select about four other packages it needs.  Tell Synaptic to install the packages and let it run. When it's finished, open a terminal window and enter the following command:

sudo aticonfig --initial -f

This command is optional, but recommended if you watch video on your computer:

sudo aticonfig --overlay-type=Xv  

At this point you will need to at least restart the x server, but I recommend a full reboot. Why?  Chicken superstition and too many years trying to beat certain other PC operating systems into submission.

---

### Post by zika on 2009-03-19
> **rbmorse said:**
> At this point you will need to at least restart the x server, but I recommend a full reboot. Why?  Chicken superstition and too many years trying to beat certain other PC operating systems into submission.
You have to reboot because module fglrx is embedded in kernel via DKMS. that is why I susspect this thing works even after "driver" removal ... :)

yes, I was right. I removed dkms module and I get no compiz. :) I guess You left fglrx-kernel-source installed ...

I removed everything since tormod announced progress in open-source driver i.e. radeon ... :)

---

### Post by arunthopil on 2009-03-19
hi..............:)

           i recenly having issues with FGLRX  drivers, I am using an onborad ATI radeon X1200 grphics.........  i too had some driver isses........ I have fixed it..............  


actualy the main issue that we will face is in getting the 3D accelaration support......... By default Ubuntu had some Fglrx and also Ati drivers  ...................


 what i cud sujjest is the easiest way jus to install " **[COLOR="Red"]envyng[/COLOR]** from synaptic manager........... you just go through the blog.......... i have provided enough detailed explanation there

so friend you can check my blog  i just uploaded the FIX before an hour


[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)     :D   :D

---

### Post by arunthopil on 2009-03-19
> **Woody1987 said:**
> Im having problems with the new fglrx drivers that were made available recently, im talking about the 9.4 beta drivers that amd let the ubuntu developers use. These drivers DO support xserver 1.6 but im having trouble using them. I can install them just fine but when i get to the log on screen i get a garbled screen. Im using jaunty with all latest updates and an ATI/AMD Mobility 3650HD which according to AMD is supported. Anyone else have problems with these new drivers?

Heres a link to the article telling me about them [http://www.phoronix.com/scan.php?page=news_item&px=NzE0Nw](http://www.phoronix.com/scan.php?page=news_item&px=NzE0Nw)



hi woody i cud guarntee you the fix

go [http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)

---

### Post by zika on 2009-03-19
> **excogitation said:**
> I will still try to go back to the fglrx driver in a bit because it has like 3x the performance of the opensource one (maybe that's just felt, but that's all that matters, not?).
no, You are just right in numbers. all the measurements confirm something about the number 3 ...
but this is interesting, without the xorg-driver-fglrx, with the module fglrx in kernel via DKMS, You get correct speed for open-source driver but running compiz, am I right? You removed the xorg-driver-fglrx via apt-get? previously You would have to remove the module in order to get radeon working again. they are surely converging ... :) that is a good thing and hope for us to get a good driver sometime ... :)

---

### Post by excogitation on 2009-03-19
> **zika said:**
> no, You are just right in numbers. all the measurements confirm something about the number 3 ...
but this is interesting, without the xorg-driver-fglrx, with the module fglrx in kernel via DKMS, You get correct speed for open-source driver but running compiz, am I right?
not too sure what you mean, but I don't have an fglrx dkms module
```
$ sudo dkms status
vboxdrv, 1.6.6, 2.6.28-11-generic, i686: installed 
```

about the speed ... I can't really tell - the only thing that gives me some numbers is glxgears ~1500fps - with fglrx ~5500fps, but from what I read that doesn't mean much.

> **zika said:**
> 
You removed the xorg-driver-fglrx via apt-get? previously You would have to remove the module in order to get radeon working again. they are surely converging ... :) that is a good thing and hope for us to get a good driver sometime ... :)
Yes, I removed it through apt-get 
```

apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

```

Does that mean, the previous libGL.so overlap is now history?

---

### Post by zika on 2009-03-19
> **excogitation said:**
> not too sure what you mean, but I don't have an fglrx dkms module
```
$ sudo dkms status
vboxdrv, 1.6.6, 2.6.28-11-generic, i686: installed 
```about the speed ... I can't really tell - the only thing that gives me some numbers is glxgears ~1500fps - with fglrx ~5500fps, but from what I read that doesn't mean much.
Yes, I removed it through apt-get 
```

apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

```Does that mean, the previous libGL.so overlap is now history?
You do not have dkms module because You did the right thing and removed everything. by removing kernel-source You removed dkms module. numbers are just the same as mine only I get 350 and 1100. ratio is 3 and that is the same. they really do not mean much since I feel that ati is snappier than fglrx. and the final question: compiz is still working? I do not use it but it is a kind of test for other stuff. that is what bothers me, here compiz is not working. I would like to know what is the difference. ... :)

---

### Post by excogitation on 2009-03-19
> **zika said:**
> You do not have dkms module because You did the right thing and removed everything. by removing kernel-source You removed dkms module. numbers are just the same as mine only I get 350 and 1100. ratio is 3 and that is the same. they really do not mean much since I feel that ati is snappier than fglrx. and the final question: compiz is still working? I do not use it but it is a kind of test for other stuff. that is what bothers me, here compiz is not working. I would like to know what is the difference. ... :)

Yep, Comiz is working - and I'm really surprised about that.

Clean xorg.conf?

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by zika on 2009-03-19
> **excogitation said:**
> Yep, Comiz is working - and I'm really surprised about that.

Clean xorg.conf?

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```
ditto. no compiz ... :)

---

### Post by excogitation on 2009-03-19
> **zika said:**
> ditto. no compiz ... :)

I have these packages
xserver-xorg-video-ati
xserver-xorg-video-radeon
radeontool

installed that might be related.

In "Hardware Drivers" the Ati doesn't show anymore (guess because it's removed).

Why it works for me but not for you - I don't know.

---

### Post by Woody1987 on 2009-03-19
I dont know if this affects anyone here, but for those that it might, all future fglrx releases from 9.3 onwards (which includes this one) do NOT support cards older than the 2000 series. So if you have an x1900 for example then your out of luck with this driver, you will have to use the opensource drivers, which i should point out work pretty damn well on cards of that generation almost on par with the fglrx drivers.

---

### Post by Woody1987 on 2009-03-19
Another issue here seems to be lack of compiz. Same happened to me, but if you install the fusion-icon package and then run it, an icon will appear in the system tray, you should be able to select the window manager from there.

---

### Post by Lorenz on 2009-03-19
I had the same problems as reported here, only way to solve it is to purge the fglrx drivers (I feel like back in the days when I started with Ubuntu...). Anyway, from what I have gathered in the past days, new fglrx doesn't support our X series ATI cards anymore. So we can either use the open source ATI drivers or revert to the universal mesa drivers. Is that correct? In any case, a step back for us :(

---

### Post by zika on 2009-03-19
> **Woody1987 said:**
> Another issue here seems to be lack of compiz. Same happened to me, but if you install the fusion-icon package and then run it, an icon will appear in the system tray, you should be able to select the window manager from there.
icon is there but when I try anything related to compiz I get white screen and have to revert to Alt-Ctrl-F1 to get to CLI and stop gdm ... it will come ... just wait .. :)

---

### Post by dazzler on 2009-03-19
I updated 9.04 today and now after it boots after text checkup it's just a garbled mess, dpkg-reconfigure doesn't work 

Anything I can try before a reinstall?

---

### Post by Woody1987 on 2009-03-19
> icon is there but when I try anything related to compiz I get white screen and have to revert to Alt-Ctrl-F1 to get to CLI and stop gdm ... it will come ... just wait .. 

Worked for me

---

### Post by excogitation on 2009-03-19
> **dazzler said:**
> I updated 9.04 today and now after it boots after text checkup it's just a garbled mess, dpkg-reconfigure doesn't work 

Anything I can try before a reinstall?

boot to a root shell using recovery mode (or use e.g. ctrl + alt + f2 if that still works)

1st try 
```
sudo aticonfig --initial -f
sudo aticonfig --overlay-type=Xv
```

if that doesn't work you probably have an Ati card prior the 2000 series
```
apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
```

Someone said support for all Ati models before the 2000 series has been dropped that's why we can now only use the opensource driver.

---

### Post by Lorenz on 2009-03-19
> **dazzler said:**
> I updated 9.04 today and now after it boots after text checkup it's just a garbled mess, dpkg-reconfigure doesn't work 

Anything I can try before a reinstall?

Had the same problem as you, just do what the user above me suggested - that will work :) 

about the x series and fglrx - perhaps someone less noobish than me can confirm, but I gathered that the support for the X series has been dropped by ATI.

---

### Post by Yashiro on 2009-03-19
Sad to see basic issues like this still persist.

"I tried ubuntu but I got garbled mess/black screen/insert video bug on first install here"

"I'll try it again in a few years"

---

### Post by zika on 2009-03-20
> **dazzler said:**
> I updated 9.04 today and now after it boots after text checkup it's just a garbled mess, dpkg-reconfigure doesn't work 
Anything I can try before a reinstall?
You did not install fglrx or You did? that would make a difference in our suggestions.
(at least it would in mine). radeonhd installed?
if You have fglrx do 
```
sudo aticonfig --initial -f
```and not ```
dpkg-reconfigure -phigh xserver-xorg
```
after that because it will undo the previous.

---

### Post by zika on 2009-03-20
> **Woody1987 said:**
> Worked for me
lucky You ... .)

---

### Post by dazzler on 2009-03-20
> **excogitation said:**
> boot to a root shell using recovery mode (or use e.g. ctrl + alt + f2 if that still works)



if that doesn't work you probably have an Ati card prior the 2000 series
```
apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
```

Someone said support for all Ati models before the 2000 series has been dropped that's why we can now only use the opensource driver.

Thanks this worked for me :)

---

### Post by Bert Mariën on 2009-03-21
I didn't read the posts on this.

But please read this:

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

### Post by markharding557 on 2009-03-22
> **Bert Mariën said:**
> I didn't read the posts on this.

But please read this:

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

are you getting bored with posting this everywhere? it's already been mentioned in this thread

---

### Post by ktp on 2009-03-22
I had the same issue.  It was because my card is not supported anymore.  As soon as I removed the fglrx drivers, things worked.  So people having issues, please make sure your card is still supported by latest fglrx drivers.  If not then remove them and open source drivers will work.

---

### Post by rbmorse on 2009-03-22
> **Lorenz said:**
> about the x series and fglrx - perhaps someone less noobish than me can confirm, but I gathered that the support for the X series has been dropped by ATI.

Dropped is not quite the right way to express the situation.  

What they are doing is shifting support for the "X" cards (RV300-RV500) over to the open source "Radeon" and "RadeonHD" drivers.  Both projects are proceeding in parallel and are very closely related at this juncture and both receive official support in some form from AMD/ATI.  

Nominally, radeonhd is a Novel project (open SuSE) and radeon is a Red Hat (RHEL/Fedora) effort. 

What you need to understand is that the entire Linux graphics subsystem is in the middle of a sweeping re-architecture effort.  The kernel interface, the "X" server and the hardware driver interface are ALL being completely overhauled *simultaneously*...and as a result the ATI open source drivers may be lacking a certain level of polish at any given moment -- in addition to one or more core capabilities.  

But, progress is rapid.  We're told that by Summer the open drivers ought to produce roughly the same capabilities and overall performance as the FGLRX package -- at least as far as the Linux desktop user is concerned.  

Both drivers are in repository (search on "radeon" and "radeonhd") and the "radeon" driver is the default driver installed by 8.10 and 9.04(alpha) on systems where ATI chipset video cards are detected by the installer. 

I have an RV770 card (HD4850) and can report both open source drivers work quite well, except the known issue that "HD" cards do not yet have hardware accelerated 3D and support for Xv video output is still sort of experimental. 

Other outstanding issues of which I am aware...no TV out, no dynamic power management (this hurts laptops)  and some users report various issues when using a composited desktop manager (c.f., compiz or whatever KDE calls their compositor --  Kwin?) 

So, to say ATI has dropped support for the "X" cards is not correct, but future driver development for those cards will be done by the community in an open source framework, with ATI providing some (limited)  technical support.  This could be good news or bad news depending upon your view of the sustainability and acuity of open source software development in general and drivers for legacy hardware in particular.

---

### Post by fipoo on 2009-04-03
Hello!
Maybe you can help me!

I'm having some problems after installing fglrx drivers on my new Kubuntu Jaunty recently downloaded distro.

I have a laptop with an Ati HD 2400 video card. The first thing I done after installing the sistem (alternate install) was try to install the fglrx drivers, everything gone ok, i mean, with no errors. Then, I run:
```
aticonfig --initial
aticonfig --resolution-0,1280x800
```

After that, I rebooted my system and what I got was a totally black screen just after the graphical boot.
With that black screen, I was unable to do nothing, except rebooting by pressing the power button.
Then, I restarted the system in recovery mode and got the log files. Here they are:
[HTML]

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux KubuntuFipoo 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 x86_64
Build Date: 20 March 2009  02:02:41PM
xorg-server 2:1.6.0-0ubuntu4 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.058568] (--) probed, [    0.058583] (**) from config file, [    0.058592] (==) default setting,
	[    0.058601] (++) from command line, [    0.058610] (!!) notice, [    0.058618] (II) informational,
	[    0.058627] (WW) warning, [    0.058635] (EE) error, [    0.058644] (NI) not implemented, [    0.058653] (??) unknown.
[    0.058746] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr  2 22:46:08 2009
[    0.072687] (==) Using config file: "/etc/X11/xorg.conf"
[    0.072837] (==) ServerLayout "aticonfig Layout"
[    0.072851] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    0.101158] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    0.101475] (**) |   |-->Device "aticonfig-Device[0]-0"
[    0.101502] (==) Automatically adding devices
[    0.101511] (==) Automatically enabling devices
[    0.139508] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.257255] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.257278] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.257287] (II) Cannot locate a core pointer device.
[    0.257294] (II) Cannot locate a core keyboard device.
[    0.257300] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.257319] (II) Loader magic: 0xb40
[    0.257326] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.257352] (II) Loader running on linux
[    0.257364] (++) using VT number 7

[    0.288548] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 2400 rev 0, Mem @ 0xd0000000/134217728, 0xd8000000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    0.288850] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.288907] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.289035] (II) "extmod" will be loaded by default.
[    0.289044] (II) "dbe" will be loaded by default.
[    0.289050] (II) "glx" will be loaded by default.
[    0.289057] (II) "record" will be loaded by default.
[    0.289063] (II) "dri" will be loaded by default.
[    0.289070] (II) "dri2" will be loaded by default.
[    0.289080] (II) LoadModule: "extmod"
[    0.320658] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.320964] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.321008] (II) Loading extension MIT-SCREEN-SAVER
[    0.321017] (II) Loading extension XFree86-VidModeExtension
[    0.321023] (II) Loading extension XFree86-DGA
[    0.321029] (II) Loading extension DPMS
[    0.321036] (II) Loading extension XVideo
[    0.321044] (II) Loading extension XVideo-MotionCompensation
[    0.321051] (II) Loading extension X-Resource
[    0.321061] (II) LoadModule: "dbe"
[    0.321374] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.321488] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.321551] (II) Loading extension DOUBLE-BUFFER
[    0.321560] (II) LoadModule: "glx"
[    0.321830] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.322065] (II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.322114] (II) Loading extension GLX
[    0.322125] (II) LoadModule: "record"
[    0.322417] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.322548] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.322586] (II) Loading extension RECORD
[    0.322595] (II) LoadModule: "dri"
[    0.322865] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.338377] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.338418] (II) Loading extension XFree86-DRI
[    0.338427] (II) Loading sub module "fglrxdrm"
[    0.338433] (II) LoadModule: "fglrxdrm"
[    0.338499] (II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
[    0.358571] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
[    0.358627] (II) LoadModule: "dri2"
[    0.358930] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.367752] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.367795] (II) Loading extension DRI2
[    0.367807] (II) LoadModule: "fglrx"
[    0.367976] (II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.917744] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
	Module class: X.Org Video Driver
[    0.949020] (II) Primary Device is: PCI 01@00:00:0
[    0.949042] (WW) Falling back to old probe method for fglrx
[    0.949051] (II) ATI Proprietary Linux Driver Version Identifier:8.60.40
[    0.949059] (II) ATI Proprietary Linux Driver Release Identifier: 8.60.4                               
[    0.949065] (II) ATI Proprietary Linux Driver Build Date: Mar 14 2009 21:46:40
[    1.104402] (II) Loading PCS database from /etc/ati/amdpcsdb
[    1.104452] (WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
[    1.104461] (WW) Video driver ABI version of the X server is 5.0
[    1.104995] (--) Chipset Supported AMD Graphics Processor (0x94C9) found
[    1.105220] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    1.105536] (II) AMD Video driver is signed
[    1.114098] (II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    1.114269] (II) fglrx(0): pEnt->device->identifier=0xa71a80
[/HTML]
As you can see, the log doesn't displays any error... strange.

and here is my xorg.conf file:
[HTML]
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
[/HTML]

By the way, to get my system working again, i removed the xorg-driver-fglrx package and comented the two lines from my xorg.conf:
[HTML]
Driver      "fglrx"
BusID       "PCI:1:0:0"
[/HTML]

My question is: Why there is no error in the log file, and either I didn't got any errors in the fglrx-driver installation?
Is there anybody who knows how to solve it?
Thanks, FiPoO!

---

### Post by carrozza on 2009-04-04
Fipoo I have exactly your issue (laptop with ATI Mobility Radeon HD 2600).

Unfortunately I wiped a smooth 8.10 installation to try 9.04 beta... but that's my fault.

---

### Post by fipoo on 2009-04-04
> **carrozza said:**
> Fipoo I have exactly your issue (laptop with ATI Mobility Radeon HD 2600).

Unfortunately I wiped a smooth 8.10 installation to try 9.04 beta... but that's my fault.

I just think we are doing something wrong...
For me, It's strange the fact that xorg server don't start correctly and don't give us any feedback of what's  going wrong.

Please help us!

---

### Post by pig-flower on 2009-04-07
in my case, ati proprietary fglrx  driver is not graphic acceleration driver. it is just trouble making driver. with this driver, TVtime and VLC make system freezing, compiz demands high and higher cpu usage. some 3D garmes are not launched. in linux, using ati graphic cards is terrible experience.

---

