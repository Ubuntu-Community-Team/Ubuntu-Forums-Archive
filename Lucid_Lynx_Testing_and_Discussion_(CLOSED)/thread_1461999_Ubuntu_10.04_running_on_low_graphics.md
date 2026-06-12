---
title: "Ubuntu 10.04 running on low graphics"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zabaglione on 2010-04-25
heloo...everyone..
Since i downloaded the update for ubuntu 10.04 RC..
my Ati Graphic card failed me...compiz stopped working & my laptop is only running low graphics...

tried many solutions from the forum...but failed...
anyone have any more solution??? suggestions?

tried to reinstall...purge and etc...but nothing seems to work yet...

regards..

---

### Post by Gyrra on 2010-04-25
when this happened to be a few weeks ago, I just used apt-get to fix it for me.
ctrl-alt-f2 for console and the used the meta ati packages.
sudo apt-get install xserver-xorg-video-ati && xserver-xorg-video-all

This installed all the ati drivers (you will need an active internet connection unless you have all of these packages cached).

I am sure there are better solutions, as I am still quite new to linux.
But since I have yet to find a viable solution to my graphics issues, I tend to play around with various packages and config files, so I use this method quite often.
(exactly why I prefer to cache my packages)

---

### Post by zabaglione on 2010-04-25
thanks for the reply....

it didn't work....

have to keep on trying...

:(

---

### Post by utnubuuser on 2010-04-25
post the output of > lspci -v | grep ATIso poeple can see exactly which card it is.

xorg.conf setup is different for each card.

---

### Post by zabaglione on 2010-04-25
zabaglione@Zabaglione:~$ lspci -v | grep ATI 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
    Subsystem: ATI Technologies Inc RS780 Azalia controller

---

### Post by zabaglione on 2010-04-25
Here are the  details...

anybody have any solution?

Cheers..

seems that ubuntu failed me.............

too bad... after 2 days...still no solution...........

---

### Post by zabaglione on 2010-04-25
Still no fix???? 

:(

---

### Post by RickyCodes on 2010-04-26
Which RC did you install?

Try the alternate install. 

Drivers can then be installed post installation of the OS.

---

### Post by dino99 on 2010-04-26
which driver is used ?

can follow these commands:

- remove/purge video driver
- remove xorg.conf
- reinstall video driver
- reboot

if you still have problems:

- goto system-admin-hardwareDriver and see if the driver is recognized and activated

in case, can reconfigure xserver: sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Tadhg B on 2010-04-26
Heya dude I have 10.04 and I'm a real newbie so please be easy with me - I try and change the screen resolution in my version but the highest it goes is 800x600. You would be my hero if you could help :)

---

### Post by dino99 on 2010-04-26
> **Tadhg B said:**
> Heya dude I have 10.04 and I'm a real newbie so please be easy with me - I try and change the screen resolution in my version but the highest it goes is 800x600. You would be my hero if you could help :)

have you read post 9 ?
and you can look at my signature's links below for more help

---

### Post by Tadhg B on 2010-04-26
[INDENT]$ xrandr
[/INDENT] This will display the allowed resolutions
 **Sample output**
 [INDENT]Screen 0: minimum 320 x 200, current 1024 x 768, maximum  4096 x 4096
VGA1 connected 800×600+0+0 (normal left inverted right x axis y axis)  267mm x 200mm
800×600 85.1* +
640×480 75.0 60.0
720×400 70.1
[/INDENT] If you want to add a mode with resolution 1024X768, you can enter the  following command: (The output is shown following.)
 [INDENT]$ cvt 1024 768
[/INDENT] Sample output
 [INDENT]# 1024×768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk:  63.50 MHz
Modeline “1024×768_60.00&#8243; 63.50 1024 1072 1176 1328 768 771 775 798  -hsync +vsync
[/INDENT] Now you need to create a modeline
 [INDENT]$ xrandr --newmode <Modeline>
[/INDENT] copy the modeline of the previous output to the place mode line
 [INDENT]$ xrandr --newmode “1024×768_60.00&#8243;   63.50  1024 1072  1176 1328  768 771 775 798 -hsync +vsync
[/INDENT] Now you need to add the above mode using the following command
 [INDENT]$ xrandr --addmode VGA1 1024×768_60.00
[/INDENT] here for VGA1 you have to use what ever that was there for $ xrandr  output
 [INDENT]$ xrandr --output VGA1 --mode 1024×768_60.00




I have a message after I enter this saying "xrandr: screen cannot be larger than 800x600 (desired size 1024x7680"

[/INDENT]

---

### Post by Tadhg B on 2010-04-26
> **dino99 said:**
> which driver is used ?

can follow these commands:

- remove/purge video driver
- remove xorg.conf
- reinstall video driver
- reboot

if you still have problems:

- goto system-admin-hardwareDriver and see if the driver is recognized and activated

in case, can reconfigure xserver: sudo dpkg-reconfigure -phigh xserver-xorg
I dont know how to remove or purge the video driver.
I dont know how to remove xorg.conf or reinstall the video driver.
Hardware drivers it says "No proprietary drivers are in use on this system"

---

### Post by zabaglione on 2010-04-26
> **RickyCodes said:**
> Which RC did you install?

Try the alternate install. 

Drivers can then be installed post installation of the OS.


Which RC? i just updated from Update Manager... 
Ubuntu 9.10 > Beta 2> 10/04 RC

how & where to alternate install?

best regards'

---

### Post by dino99 on 2010-04-26
> **Tadhg B said:**
> I dont know how to remove or purge the video driver.
[COLOR="MediumTurquoise"]goto synaptic (system-admin-synaptic) and right-click on package-name[/COLOR]

I dont know how to remove xorg.conf or reinstall the video driver.
[COLOR="MediumTurquoise"]sudo rm -f /etc/X11/xorg.conf[/COLOR]

Hardware drivers it says "No proprietary drivers are in use on this system" [COLOR="MediumTurquoise"]so into synaptic which video driver is installed ?
[/COLOR] which graphic card or chipset ?

---

### Post by Tadhg B on 2010-04-26
> **dino99 said:**
> [COLOR="MediumTurquoise"]so into synaptic which video driver is installed ?
[/COLOR] which graphic card or chipset ?
Thanks for your help - unfortunately Im very new and have very little idea what Im doing here. I appreciate your time though.

I dont understand what you want me to do in Synaptic package manager.

When i entered "sudo rm -f/etc/X11/xorg.conf"
I got "rm: invalid option -- '/-
Trt 'rm --help' for more information"

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> [COLOR=MediumTurquoise]so into synaptic which video driver is installed ?
[/COLOR] which graphic card or chipset ?


I tried but still have the same problem Dino99.....

here are my screenshots... could u guide me...

cheers..

---

### Post by dino99 on 2010-04-26
> **Tadhg B said:**
> Thanks for your help - unfortunately Im very new and have very little idea what Im doing here. I appreciate your time though.

I dont understand what you want me to do in Synaptic package manager.

When i entered "sudo rm -f/etc/X11/xorg.conf"
I got "rm: invalid option -- '/-
Trt 'rm --help' for more information"

look: sudo rm -f /etc/X11/xorg.conf
is that the same as yours ?

you are newbie but maybe you are able to copy/paste, if not ask your mom

---

### Post by zabaglione on 2010-04-26
OMG...i've managed to solve the 'running on low graphics' 
laptop boot normally now...
Thanks Mr.Dino99..... you are my Hero.....

Thanks a lot....

but...... i can't still use compiz or enable it....
can't play some games....

how can i solve this???
any ideas or suggestions???

best wishes...

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> I tried but still have the same problem Dino99.....

here are my screenshots... could u guide me...

cheers..

try with: sudo dpkg-reconfigure jockey

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> OMG...i've managed to solve the 'running on low graphics' 
laptop boot normally now...
Thanks Mr.Dino99..... you are my Hero.....

Thanks a lot....

but...... i can't still use compiz or enable it....
can't play some games....

how can i solve this???
any ideas or suggestions???

best wishes...

if you are using "fglrx", as you can read into synaptic comments, it only deal with 2D, so forget compiz

instead install and try with xserver-xorg-video-ati or/and xserver-xorg-video-radeon (3D)

note: looking your sreenshoot i wonder if you use lucid or something else.
you might clean your system:
- sudo apt-get autoremove
- sudo apt-get install -f

---

### Post by Tadhg B on 2010-04-26
> **dino99 said:**
> look: sudo rm -f /etc/X11/xorg.conf
is that the same as yours ?

you are newbie but maybe you are able to copy/paste, if not ask your mom
Ok thank you. I entered that sudo rm -f /etc/X11/xorg.conf and it just moved to the next line in terminal

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> if you are using "fglrx", as you can read into synaptic comments, it only deal with 2D, so forget compiz

instead install and try with xserver-xorg-video-ati or/and xserver-xorg-video-radeon (3D)

note: looking your sreenshoot i wonder if you use lucid or something else.
you might clean your system:
- sudo apt-get autoremove
- sudo apt-get install -f


lol..... tried to clean my system but nothing.... (check screenshot)

how do i install xserver-xorg-video-ati or/and xserver-xorg-video-radeon (3D)???
Synaptic?? or software source??
how do i do it?

sorry to trouble u again.... Dino99 = Ubuntu Guru... :)

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> lol..... tried to clean my system but nothing.... (check screenshot)

how do i install xserver-xorg-video-ati or/and xserver-xorg-video-radeon (3D)???
Synaptic?? or software source??
how do i do it?

sorry to trouble u again.... Dino99 = Ubuntu Guru... :)

i do everything with synaptic, enter "ati" on top

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> i do everything with synaptic, enter "ati" on top

Its already installed....

but my Compiz & games are still not working....

what's the next step?

---

### Post by Tadhg B on 2010-04-26
Can somebody help me please. Ubuntu 10.04 - cannot get the resolution above 800x600.
SIS 771/671 PCIE VGA Display Adapter

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> Its already installed....

but my Compiz & games are still not working....

what's the next step?

need to check your repo into synaptic - config - repo:
- you might have only official "lucid" repos, check each tab and edit to see details
- if you have exotic repo and/or ppa, deselect them

be sure you are using the main server into synaptic

then right-click on xserver-xorg-video-all and remove/purge it (dont need all the driver, only the ones u need/use)

note to clean your system: into synaptic, see on the left side "installed and can be removed" or so, select them all and uninstalled

here are mine:
xserver-xorg-core, ""input-mouse, "" input-all, ""input-evdev, ""input-wacom, ""input-vmmouse, xserver-xorg

add yours: xserver-xorg-video-radeon, and remove/purge all the others

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> need to check your repo into synaptic - config - repo:
- you might have only official "lucid" repos, check each tab and edit to see details
- if you have exotic repo and/or ppa, deselect them

be sure you are using the main server into synaptic

then right-click on xserver-xorg-video-all and remove/purge it (dont need all the driver, only the ones u need/use)

note to clean your system: into synaptic, see on the left side "installed and can be removed" or so, select them all and uninstalled

here are mine:
xserver-xorg-core, ""input-mouse, "" input-all, ""input-evdev, ""input-wacom, ""input-vmmouse, xserver-xorg

add yours: xserver-xorg-video-radeon, and remove/purge all the others


Ohh....  Dino99... help me

i did what u have told me....
restarted my laptop... & i don't seem to be able to load...
only command mode....terminal....
what should i do now.....
restarted 3 times but can't load..... oh my....

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> Ohh....  Dino99... help me

i did what u have told me....
restarted my laptop... & i don't seem to be able to load...
only command mode....terminal....
what should i do now.....
restarted 3 times but can't load..... oh my....

is that install is an dist-upgrade or a fresh one ? seems there are old settings left behind.

into console:
- sudo rm -f /etc/X11/xorg.conf
- sudo apt-get install xserver-xorg-video-radeon
- sudo apt-get install -f
- sudo dpkg-reconfigure -phigh xserver-xorg
- sudo dpkg-reconfigure jockey

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> is that install is an dist-upgrade or a fresh one ? seems there are old settings left behind.

into console:
- sudo rm -f /etc/X11/xorg.conf
- sudo apt-get install xserver-xorg-video-radeon
- sudo apt-get install -f
- sudo dpkg-reconfigure -phigh xserver-xorg
- sudo dpkg-reconfigure jockey


its Dist-upgrade....

tried the 1st line - sudo rm -f /etc/X11/xorg.conf... it returned=

rm: invalid option -- '/'

as for - sudo dpkg-reconfigure jockey=
package jockey is not installed...

what to do now?

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> its Dist-upgrade....

tried the 1st line - sudo rm -f /etc/X11/xorg.conf... it returned=

rm: invalid option -- '/'

as for - sudo dpkg-reconfigure jockey=
package jockey is not installed...

what to do now?

use copy/paste (there is space !!!)

my bad its jockey-gtk

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> use copy/paste (there is space !!!)

my bad its jockey-gtk

i know the space... but i can't copy paste cause i can't load into the main..
black screen with commands only.... 

maybe i mess up my video driver?

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> i know the space... but i can't copy paste cause i can't load into the main..
black screen with commands only.... 

maybe i mess up my video driver?

so always in trouble ?

if we cant do better, reinstall fglrx, then google around about your graphic+ubuntu/lucid

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> so always in trouble ?

if we cant do better, reinstall fglrx

how to do that boss?

i m so devastated right now.....

can't load into my ubuntu....

what are the commands for that?

---

### Post by dino99 on 2010-04-26
> **zabaglione said:**
> how to do that boss?

i m so devastated right now.....

can't load into my ubuntu....

what are the commands for that?

that's easy  :) sudo apt-get install fglrx && sudo apt-get install fglrx-modaliases

there is fglrx-amdcccle also if you want the catalyst control center

---

### Post by zabaglione on 2010-04-26
> **dino99 said:**
> that's easy  :) sudo apt-get install fglrx && sudo apt-get install fglrx-modaliases

there is fglrx-amdcccle also if you want the catalyst control center


Sorry Dino99...its not working..... still got the black boot screen...to login...

do i need to reinstall my ubuntu? last option.....

---

### Post by Podex on 2010-04-26
> **zabaglione said:**
> its Dist-upgrade....

tried the 1st line - sudo rm -f /etc/X11/xorg.conf... it returned=

rm: invalid option -- '/'


what to do now?

You didn't do this correctly. Please try again. (You probably wrote 'sudo rm -f/etc/X11/xorg.conf' instead, without a space between -f and the location).

---

### Post by zabaglione on 2010-04-26
> **Podex said:**
> You didn't do this correctly. Please try again. (You probably wrote 'sudo rm -f/etc/X11/xorg.conf' instead, without a space between -f and the location).


command not found....

i m lost...with black screen command & don't know what to do anymore...

---

### Post by Podex on 2010-04-26
> **zabaglione said:**
> command not found....

i m lost...with black screen command & don't know what to do anymore...

You are really doing it wrong then. This is what you should type:

```
sudo rm -f /etc/X11/xorg.conf
```

And then press Enter/Return.

---

