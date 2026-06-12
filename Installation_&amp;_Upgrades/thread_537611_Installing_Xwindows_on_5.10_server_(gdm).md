---
title: "Installing Xwindows on 5.10 server (gdm)"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Sir P on 2007-08-29
hello folks

Im running ubuntu-server 5.10 (old but hardware does not support newer kernel) anyways.. need to get a GUI on there... a small ish one..I plan on using icewm ... i believe i need to install gdm first? so I type...

> apt-get install gdm icewm

and it complains it cant find either of those packages...

can anyone provide some help to get icewm on a ubuntu server from scratch?

assiantance much apperciated
kind regards
Sir P

---

### Post by Sir P on 2007-08-29
OK I downloaded the most recent icewm fro the icewm website ... i unpacked it and came to make and make install it and it said make command not found. So I installed make and tried again, it came up with :

make[1] g++ command not found
make[1] *** [ysmsgbox.o] error 127
make[1] leaving directory /icewm-1.2.32/src
make[1] *** [base] error 2


Anyone have any idea how to progress with this?

many thanks
Sir P

---

### Post by kerry_s on 2007-08-29
i don't think 5.10 is supported any longer, don't even know if there's still repos. you can try->

first make sure your repos are turned on->

sudo nano /etc/apt/sources.list

remove the "#" in front of the deb lines.
ctrl and x and y and enter to save

sudo apt-get update
sudo apt-get install x-window-system-core gdm synaptic icewm menu
reboot(ctrl+alt+delete)


what are the specs?
have you tried debian? debian still supports older stuff.
[http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r1-i386-businesscard.iso)
that's the net installer, you can install anything. when it comes to package selection, just uncheck everything that will give you a base install. after reboot, login as root> apt-get install xorg gdm synaptic icewm menu <
will give you a light gui and you can use synaptic to install what ever else you need.

if your stuff is really old-> [ftp://ftp.nluug.nl/pub/os/Linux/distr/damnsmall/release_candidate/dsl-4.0rc2.iso](ftp://ftp.nluug.nl/pub/os/Linux/distr/damnsmall/release_candidate/dsl-4.0rc2.iso)

Also please in the future provide as much information as you can, we only know what you tell us, there are no psychics here.

---

### Post by Sir P on 2007-08-29
hi there,

thanks for your reply.

I recon your right i recon its not supported any more.. the repos for the breezy universe are notfound when i uncomment them from the sources.list

dedian is far too big, need something around 1 gb really.

I will try and find the hardware spec to get you some more info
cheers

---

### Post by kerry_s on 2007-08-29
> **Sir P said:**
> hi there,

thanks for your reply.

I recon your right i recon its not supported any more.. the repos for the breezy universe are notfound when i uncomment them from the sources.list

dedian is far too big, need something around 1 gb really.

I will try and find the hardware spec to get you some more info
cheers


no, debian is what you make it. i use the base install & build up from there, my install plus alot of cache is only at  617mb and i'm sure i have alot of applications you probably don't even need.

install the base, that means when it comes to software selection, hit the space bar to uncheck them. then use this

apt-get install xorg jwm mc
apt-get clean
type> startx
you should be around 200mb
when you get that far, let me know what else you need, like if you want to know how to get it to autologin or something.

other wise take the short route and go with DSL, it's only 50mb using a frugal install and around 200mb using a regular hd install, they use a 2.4 kernel.> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by Sir P on 2007-08-29
hi kerry,

cheers for your help so far. 

OK I installed debian from that link you gave me.. base system only,nothing else. and then installed xorg jwm mc as you mentioned... comes to 535Mb... can deal with that.

going to do a few more things and get back to you to let you know how happy i am :)

cheers for all your help
btw what is the GUI here called?

---

### Post by Sir P on 2007-08-29
ok kerry still having a problem installing a driver onto this debian install now.. the driver is for a touchscreen input... the driver is called touchkit daemon is tpaneld

you can find the install instructions and driver at touchkit.com it says for kernel 2.6 debian so im happy with that .. i do..


make new
make all
make install

it goes through does complete but errors part way doing as it trys to put the touchkit driver file into /usr/X11R6/lib/modules/input

however it cant because there is no /modules directory in /usr/X11r6/lib

Do I need to install something else to get this modules directory setup?

any assisatance further much apperciated.
warm regards
SIR p

---

### Post by Sir P on 2007-08-29
to add to that.. got round that last problem by creating /modules/input

and ran install again and it copied driver ok.. it installed however warned that XF86Config-4 file not found...any idea what that is all about?
cheers

---

### Post by kerry_s on 2007-08-29
> **Sir P said:**
> hi kerry,

cheers for your help so far. 

OK I installed debian from that link you gave me.. base system only,nothing else. and then installed xorg jwm mc as you mentioned... comes to 535Mb... can deal with that.

going to do a few more things and get back to you to let you know how happy i am :)

cheers for all your help
btw what is the GUI here called?

that can be trimmed farther. using aptitude, in the terminal "su" to root and type aptitude. if thats to confusing grab synaptic(su & apt-get install synaptic) you can trim all the xsever-xorg-? drivers for vid cards you know you don't have, don't touch vesa. font's can be trimmed, like replacing dejavu with bitstream.etc...

the gui is jwm a really small window manager(WM)

---

### Post by kerry_s on 2007-08-29
> **Sir P said:**
> ok kerry still having a problem installing a driver onto this debian install now.. the driver is for a touchscreen input... the driver is called touchkit daemon is tpaneld

you can find the install instructions and driver at touchkit.com it says for kernel 2.6 debian so im happy with that .. i do..


make new
make all
make install

it goes through does complete but errors part way doing as it trys to put the touchkit driver file into /usr/X11R6/lib/modules/input

however it cant because there is no /modules directory in /usr/X11r6/lib

Do I need to install something else to get this modules directory setup?

any assisatance further much apperciated.
warm regards
SIR p

So the stock touch screen drivers didn't work?

---

### Post by Sir P on 2007-08-30
Hi Kerry,

Was not aware of the stock drivers....
got touchkit to work now.. im going to write up some docs and publish them online as there doesnt seem to be a great deal of info out there and ive been working with these for a while now.. il compile some info for others who have similar issues.

Anyway, that autologin you mentioned? ;)

---

### Post by kerry_s on 2007-08-30
first post your specs, i need to know what the heck i'm dealing with. i could inadvertently give you the wrong advice.

the only things i know so far is:
you only have 1gb to work with
you have some kind of touch device

that's it that's all i know, i would also like to know how much linux you know, so for example: if i just give you a command, do you know what to do with it or do i need to put detailed instructions, makes a difference to me that's more typing. :) i also need to know, what your goal is, like what is the intended use. also don't be afraid to wipe it and try different things. there's alot of ways to go with a custom setup. the more info i have, i can refine the install line to more what you need.
for instance, if you need it more friendly then jwm:
apt-get install xserver-xorg-video-vesa xorg synaptic icewm menu emelfm leafpad dillo
synaptic=install/uninstall packages
icewm=gui, like windows
emelfm=filemanager
leafpad=text editor
dillo=web browser
pic bellow->
ive got that & more & i'm only around 600mb.

autologin:

```
[B]su
apt-get install rungetty
mcedit /etc/inittab

line 54:
1:2345:respawn:/sbin/rungetty tty1 --autologin user

replace user with your log in name.[/B]
```

if you want it to startx after login:

```
[B]mcedit ~/.bash_profile

# starts gui
if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then
startx 
fi 
[/B]
```

the driver is called wacom, it's part of xorg so it's there, it's for touch screens. there are also other drivers for touch screens, but i have no info on yours.

---

### Post by Sir P on 2007-08-30
Thanks Kerry your ongoing support is much apperciated.

I will have to dig out the exact specs for you.... its not old hardware ..all modern just low spec is all.

I can find my way around a linux system no worries, im actually trained as a unix tech so can do bits a pieces.

Didnt isntall on the things you said, i already have setup a browser thanks.

Do you know how to or where I need to look to make a certain application start when xwindows starts? I checked xinit but couldnt see anything I thought did it.

Thanks again, most helpful..

---

### Post by kerry_s on 2007-08-30
sorry, been busy trying to get my desktop back up and running it's been down for like 3 months. :(

**your-editor ~/.Xsession**

[B]#!/bin/sh
your-app &[/B]

example:
conky &
xterm &

make it exectuable>
**chmod +x ~/.Xsession**

just keep the questions coming, i'll get to them as soon as i can. take care.

---

### Post by kerry_s on 2007-08-30
> **Sir P said:**
> Thanks Kerry your ongoing support is much apperciated.

I will have to dig out the exact specs for you.... its not old hardware ..all modern just low spec is all.

I can find my way around a linux system no worries, im actually trained as a unix tech so can do bits a pieces.

Didnt isntall on the things you said, i already have setup a browser thanks.

Do you know how to or where I need to look to make a certain application start when xwindows starts? I checked xinit but couldnt see anything I thought did it.

Thanks again, most helpful..

and easy way to get your spec's

[B]apt-get install lshw
lshw >> lshw.txt
[/B]

---

### Post by Sir P on 2007-08-31
excellent il install that and get the specs :)

I tried your steps to have an application start on startx.... but jwm opens and then dies quickly after.. in the xsession error file it reads:

> 
/bin/sh: xli: command not found
X connection to :0.0 broken (explicit kill or server shutdown).


doesnt like this xli ?
cheers again, most helpful and friendly
oh also was after remote desktop..i installed 'vncserver' though still cant connect, connection refused.. is there another one i need for jwm?

cheers

---

### Post by kerry_s on 2007-08-31
> **Sir P said:**
> excellent il install that and get the specs :)

I tried your steps to have an application start on startx.... but jwm opens and then dies quickly after.. in the xsession error file it reads:



doesnt like this xli ?
cheers again, most helpful and friendly
oh also was after remote desktop..i installed 'vncserver' though still cant connect, connection refused.. is there another one i need for jwm?

cheers

xli is the background setter, you can comment that out or just remove it from the jwmrc, remember it's in xml so commenting out is "<!--" at the beginning and "-->" at the end. you can also just install xli (apt-get install xli) and point it to a image to use for the background. i don't like xli, i used feh instead.
[B]updatedb
locate jwmrc
man jwm[/B]

but that shouldn't stop it. 

try this than>

[B]#!/bin/sh
your-app &
your-app2 &

jwm

[/B]

vnc you just have to set all the proper permissions. [http://heller.huono.org/bin/vnc.html](http://heller.huono.org/bin/vnc.html)

---

### Post by Sir P on 2007-08-31
Thanks Kerry, I'm enjoying this...

Ok nailed that by adding jwm at the end.. i see.. it specifies the window manager, makes sense.

OK playing with vnc now, got it working happy with that... you said keep em coming, i'l do exactly that untill you get bored ;)

Looking to change the desktop wallpaper... there is a jwmrc file that is all xml.. has /usr/share/backgrounds/default.jpg specified.. I put an image of my own in that location and it does not display.. did I look in the wrong please?

Also changing the screen res to something smaller would be a plus for me ;)

many thanks once again,
p

---

### Post by kerry_s on 2007-08-31
> **Sir P said:**
> Thanks Kerry, I'm enjoying this...

Ok nailed that by adding jwm at the end.. i see.. it specifies the window manager, makes sense.

OK playing with vnc now, got it working happy with that... you said keep em coming, i'l do exactly that untill you get bored ;)

Looking to change the desktop wallpaper... there is a jwmrc file that is all xml.. has /usr/share/backgrounds/default.jpg specified.. I put an image of my own in that location and it does not display.. did I look in the wrong please?

Also changing the screen res to something smaller would be a plus for me ;)

many thanks once again,
p

desktop wallpaper:
did you install xli? (apt-get install xli) 
i use feh(apt-get install feh) for mine it's alot easier. you just click or open a image and right click save as background. the line for xsession is>
**eval `cat $HOME/.fehbg`**

i don't use "&" at the end cause i want that to load before everything else, so it's the first thing in my startup.

screen res:
su
your-editor /etc/X11/xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" <--change that to the size you want
	EndSubSection
EndSection
```


finally got my desk top working again, back after 3+ months of slumber. muhaha. :lolflag:

---

