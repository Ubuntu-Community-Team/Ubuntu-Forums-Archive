---
title: "Problems with ATI Radeon X1300(Feisty Fawn)"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by rygar on 2007-05-09
I'm running Ubuntu Feisty Fawn 7.04, I have a ATI Radeon X1300, Ubuntu is not recognizing my ATI card with the 3D graphical acceleration(in the "Restricted Drivers Manager" there is a red dot and it says "Not in use"). I've been trying to install graphical drivers to do this such as "fglrx" with very little success. I've read many tutorials and tried many ways to installing graphical drivers for my graphics card, but nothing seems to work. I know there are many posts with similar problems but I cant seem to find a single method that works. I'm starting to wonder if the ATI Radeon X1300 and Feisty are just not compatible. If someone could please shed some light in this tunnel that would be amazing!! Thank you. 

(Tried the wiki site, and tried all the other main google results, with no success)

---

### Post by chrisN_uk on 2007-05-09
Same here, and there doesn´t seem to be any solution. 

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Do you get the same and does anyone know how to solve this?

---

### Post by DrQuincy on 2007-05-09
I'm in the same boat - I've seen a couple of people get the X1300 to run 3D accelleration, even with Beryl on top, but it seems it all broke in the Feisty upgrade.  Whilst I've not got Beryl to work on my X1300 I did have 3D accelleration under Edgy - I'm getting the same error as you now.

It must be possible though - this [guy got Compiz running]("http://www.youtube.com/watch?v=Zz9LpJy8pgs").

---

### Post by chrisN_uk on 2007-05-09
I wonder how he's managed that...I haven't heard of anybody else doing it.

---

### Post by dodgePT on 2007-05-09
With actual ATI drivers installed (wether proprietary or free ones) you get 2D **or** 3D working and never both at the same time. I tried all methods and ended up where i started. Any way, i followed [this tutorial]("http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon") and 3d desktop is stable without crashes, but movie playback is still a problem no matter what codec i use.

---

### Post by chrisN_uk on 2007-05-09
It says the x1300 is  unsupported, what card are you using?

---

### Post by dodgePT on 2007-05-09
9600XT, nevermind ;)

---

### Post by chrisN_uk on 2007-05-09
I gave it a go anyway, it broke my x server. Had one thought though which i might try.

Edit: Nope. Didn't help at all.

---

### Post by gordo1701e on 2007-05-09
OK, Glad to hear I'm  not alone in this.  Now, I've never gotten My ATI Radeon X1300 to work in ANY version of Linux, Except with the VESA drivers.  

I Checked on the ATI website and they claim that their driver works with the X1300.  Anybody have any ideas at all.  I keep getting the black screen of death, regardless of witch version I install of either linux or the ATI drivers!!!!! GRRRRR.  I going to Vista at this rate!@!!!:(

---

### Post by chrisN_uk on 2007-05-09
You could try sabayon linux. Worked like a charm for me graphics wise.

---

### Post by Inspire1997 on 2007-05-09
X1600 here and it will not do Beryl or 3D :(

---

### Post by chrisN_uk on 2007-05-09
```
chris@chris-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


```

Does anyone know what this means?

---

### Post by rygar on 2007-05-09
welp, my housemate and i got beryl working with the x1300, but it has it's issues

basically, he did a clean install, and got an older version of the fglrx drivers working.  the newest version does not work, as many of you might know.  i forget which version he has installed, but i'll check when i get a chance.  i think it's 8.34.something.

then just follow the automated install script from: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)
which does a whole bunch of crazy crap.

make sure you load XGL session for the gnome terrminal, or beryl wont work.  if the automated script doesnt install emerald themes, do that too.  i can't remember.


fglrxinfo should tell you you're using ATI Radeon X1300.

don't have beryl start on start-up, it will crash.  you must load this at the terminal first:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

then beryl-manager.

even then, its not perfect.  beryl works, cube and all, but after a while your gnome-panels (or your whole screen) might go white, and you have to alt+ctrl+backspace.  plus, i cant figure out a way around the pre-load.  if you're not into beryl, desktop effects works just fine, and ive heard compiz 0.5.0 may be stable.  not sure.

if and of you have an x1300 and it's not working, whats your error?

---

### Post by rygar on 2007-05-09
Another useful thread:

[http://ubuntuforums.org/showthread.php?t=429090](http://ubuntuforums.org/showthread.php?t=429090)


Key thing to note is that you can't use the newest fglrx drivers.  The automated script should take care of the rest for Xgl and whatnot.  Test by logging into Xgl without beryl--graphics should look better right away, and Desktop Effects should work.

---

### Post by Palmstroem on 2007-05-10
Hi folks,

I am having the same problem as chrisN_uk. Hardware is Opteron 64bit system with Radeon X1300 graphics. I installed the latest fglrx driver (8.36.5) from ATI following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") excellent guide, method 2, but it did not work. I am getting software (mesa) only with complains about missing DRI.

Now, I am no expert but IMO it could mean several things:
1. The fglrx driver from ATI is broken - as usual! - so the only solution is to wait for better drivers (HAHA).
2. The fglrx driver does not support the X1300 card - could well be but the docs claim it should.
3. The fglrx driver cannot find a piece of software which it needs, probably a module. Seems very probable. A look into Xorg.0.log shows that Feisty installed Xorg version 7.2. However, two modules are loaded that were compiled for version 7.1, namely "fglrxdrm" and "glesx". The first one definitely is from ATI, and since drmOpenDevice always gives -1 **the problem appears to be that the driver cannot establish a DRM connection**. Therefore it dies and mesa is started. What to do? I don't know.:confused: 

An old fglrx driver (8.28.8) definitely worked with 64bit Edgy. So there is still some hope!

---

### Post by DrQuincy on 2007-05-10
How do you go about using an older driver then?

---

### Post by Palmstroem on 2007-05-10
As I said: I changed both the fglrx driver version and the Ubuntu version. Don't know at the moment if 8.28.8 will run with Feisty, will try later.

---

### Post by rygar on 2007-05-10
downgraded beryl to ~1.9999.2,  and no ld_preload or white screens.  that's right, X1300 with beryl, and it's stable!

dont use 8.36.x.  use an older version.  and make sure you log in via Xgl or fglrxinfo might give you the wrong info.

---

### Post by DrQuincy on 2007-05-11
> **rygar said:**
> downgraded beryl to ~1.9999.2,  and no ld_preload or white screens.  that's right, X1300 with beryl, and it's stable!

dont use 8.36.x.  use an older version.  and make sure you log in via Xgl or fglrxinfo might give you the wrong info.

Could you post a how to for newbs like me please?

---

### Post by rygar on 2007-05-11
how to... do what exactly?  here's the whole thing:

install the fglrx drivers, but NOT the newest ones.  i dont know which are supposed to work best, but id go with 8.34.8, i think that works.  this is what one of the wikis says:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx

that might try to give you the newest fglrx, so you could try forcing a lower version in synaptic.  if you can, you might be better off finding a .deb installer on google.

if you haven't yet, run the automated ati+xgl+beryl script listed earlier.  this will do a bunch of stuff like disable composite and set up an Xgl session automatically.

check your version of beryl in synaptic.  to install the old version of beryl, go to synaptic.  remove all of the components starting with "beryl", as well as a few starting with "libberyl".  reinstall them, forcing the older version (package -> force version).  they should be in the repositories.

reboot your computer, and make sure you choose "Xgl" from the sessions list on the login menu.  the graphics should look better.  under system->adinistration->restricted drivers manager, make sure it lists your ATI card as enabled.

if you type "fglrx" at a terminal, it should list your ATI Radeon x1300 card.  if it doesn't, it's probably not working.
this was tested using an ati x1300 so if you have anything else, it may or may not work.

i would be more descriptive, but this isn't an issue with my computer, so i'm recalling this from memory.  plus, it wasn't really a straightforward process so i can't give a straightforward answer.  sorry!

---

### Post by chrisN_uk on 2007-05-11
Thanks rygar. I don't have time now, I have two hours of digital hardware lectures, but I'll give this a go too and post the results (and what i did hopefully) up maybe later today. I'm totaly new to linux so this has been a bit of a learning curve for me.

---

### Post by DrQuincy on 2007-05-11
I didn't work for me unfortunately, I install the old ATI driver through Force Version.. in the package manaer then I tried manually installing the driver as per the wiki but still I get the same error - the one I must have read a hundred times this week. :(

```
glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

---

### Post by rygar on 2007-05-11
> **DrQuincy said:**
> I didn't work for me unfortunately, I install the old ATI driver through Force Version.. in the package manaer then I tried manually installing the driver as per the wiki but still I get the same error - the one I must have read a hundred times this week. :(

```
glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

are you in an Xgl session?  is your card listed as 'Enabled' in the restricted drivers manager?

---

### Post by chrisN_uk on 2007-05-11
I cant even manage to install the older fglrx versions.  It gives me this error...


```
Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window

Detected version of X does not have a matching 'x720' directory
```

---

### Post by chrisN_uk on 2007-05-11
I'm really fed up with this right now. Not enough to make me want to boot back into windows though...

---

### Post by rygar on 2007-05-11
> **chrisN_uk said:**
> I cant even manage to install the older fglrx versions.  It gives me this error...


```
Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window

Detected version of X does not have a matching 'x720' directory
```


hmm i remember getting the same error, i can't remember how to fix it though... what version are you trying to install?

---

### Post by chrisN_uk on 2007-05-11
8.34.8 Should i try another?

---

### Post by rygar on 2007-05-11
i don't even know anymore...

if ATI would just release some decent linux drivers this would never be an issue

---

### Post by chrisN_uk on 2007-05-11
Indeed. I guess I'll just leave it for the moment...

---

### Post by rygar on 2007-05-12
my last attempt:

some guy here [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/89793](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/89793)
said you can force the 8.34.8 driver:

"8.34.8 driver works, I managed to force it to install on my machine by overriding the detection of the Xorg version:
X_VERSION=x710 sudo ./ati-driver-installer-8.34.8-x86.x86_64.run"

if you can manage to run the automated script (that disables composite and sets up Xgl), then ensure you have these installed:

linux-restricted-modules-2.6.20-9-generic
xorg-driver-fglrx (8.34.8 )
beryl (1.99.2--ALL beryl components should be this version, including libberyl*)

(in synaptic, lock beryl fglrx components so they are not updated by your system)

reboot, boot into Xgl from the sessions list, and make sure your card is listed as enabled under the restricted drivers list...  everything should work fine.

---

### Post by chrisN_uk on 2007-05-12
I cannot get fglrx to work! It seems 8.34.8 is the default in feisty now...But I always get the black screen of death with fglrx. :cry: I'm going to try *another* fresh install tomorrow I think and try again.

Thanks for all you help by the way rygar.

---

### Post by DrQuincy on 2007-05-13
> **rygar said:**
> my last attempt:

some guy here [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/89793](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/89793)
said you can force the 8.34.8 driver:

"8.34.8 driver works, I managed to force it to install on my machine by overriding the detection of the Xorg version:
X_VERSION=x710 sudo ./ati-driver-installer-8.34.8-x86.x86_64.run"

if you can manage to run the automated script (that disables composite and sets up Xgl), then ensure you have these installed:

linux-restricted-modules-2.6.20-9-generic
xorg-driver-fglrx (8.34.8 )
beryl (1.99.2--ALL beryl components should be this version, including libberyl*)

(in synaptic, lock beryl fglrx components so they are not updated by your system)

reboot, boot into Xgl from the sessions list, and make sure your card is listed as enabled under the restricted drivers list...  everything should work fine.

Is yours working now?

---

### Post by rygar on 2007-05-13
more or less

the beryl cube doesn't work (it doesn't freeze, it just doesn't work), though it's definitely possible--it works fine in desktop effects, and i think it worked in beryl 0.2.1 as well.  however, the system is entirely stable, and all other features of beryl seem to work fine.

---

### Post by suprughetto on 2007-05-13
Hi,
I have an ATI X1300 and this is the output:
suprughetto@fragolaudio:~$ glxinfo |grep rendering
direct rendering: Yes
suprughetto@fragolaudio:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series
OpenGL version string: 2.0.6334 (8.34.8)

driver is working,and  I have glx session on login but my screen becomes grey. If I understood corectly beryl won't work under normal gnome session, right?
However I did clean install of 7.04 and I had no problems with video card. In Edgy 6.10 I had to work a lot to make it work. Did you try to use Envy? Ciao from Italy

---

### Post by rygar on 2007-05-13
i did not use envy.

you are getting the correct output from fglrx, so i'd say you're very close.  no, beryl will not work on a normal gnome session with an x1300.

do you have beryl starting with start-up?  if you do, try starting without.  if you don't, try starting with it.
if you have 0.2.0/1, it might just freeze your session or turn your screen/panels white.

what version of beryl do you have?  your screen WILL look ugly for a second or two while you boot up, before the drivers take effect.

one wiki said if your gnome looks ugly, load "gnome-settings-daemon" on startup in your sessions list.

also, don't forget to make sure your card is listed as "Enabled" in the restricted drivers manager.

i realize i've said everything twice on this thread, but if i can help one or two people get their graphics working maybe it's worth it.

oh, and right click the beryl-manager icon and make sure its set as your default window manager and window decorator.  emerald
should be installed.  if your window frames are missing, go to a terminal and type "emerald --replace &"

---

### Post by Palmstroem on 2007-05-14
> **suprughetto said:**
> Hi,
I have an ATI X1300 and this is the output:
suprughetto@fragolaudio:~$ glxinfo |grep rendering
direct rendering: Yes
suprughetto@fragolaudio:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series
OpenGL version string: 2.0.6334 (8.34.8)

driver is working,and  I have glx session on login but my screen becomes grey. If I understood corectly beryl won't work under normal gnome session, right?
However I did clean install of 7.04 and I had no problems with video card. In Edgy 6.10 I had to work a lot to make it work. Did you try to use Envy? Ciao from Italy

Hi suprughetto,

I am getting the same fglrxinfo output as you. Hardware is X1300 card with Dual Opteron processors running 64bit Feisty.

**BUT:**
Xorg.0.log reports the following error:
```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
```

Don't know what it means... Much worse: some progs like Matlab, Comsol Multiphysics, DrScheme, sometimes Firefox, just freeze!

Is your system stable? Are you on 32 or 64bit?

Any help from X1300 card users welcome!

---

### Post by DrQuincy on 2007-05-14
When I log into XGL session the display is all skew whiff.  Also, in a Gnome session my card is not in the list - how do you add it or does it add itself when the driver is working properly?

Come on ATI give us a working driver!

---

### Post by xav42 on 2007-05-16
Hi,

I've got a X1600 and indirect rendering is used (mesa) :
```
$ LIBGL_DEBUG=verbose fglrxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

I had the same issue with Edgy and I solved it by creating the following symlink :
```
mkdir -p /usr/X11R6/lib/modules/dri 
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

as explained here : [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting).

But with Feisty it does not work... Maybe because Xorg is version 7.0 now ?

Any idea someone ?

---

### Post by su27 on 2007-05-27
```
X_VERSION=x710 sudo sh ati-driver-installer-8.36.5-x86.x86_64.run
```
worked for me

---

### Post by Palmstroem on 2007-05-29
> **su27 said:**
> ```
X_VERSION=x710 sudo sh ati-driver-installer-8.36.5-x86.x86_64.run
```
worked for me

Hi su27,

is your system stable? No freeze? I am wondering...

---

### Post by wheredidrealitygo on 2007-05-30
POTENTIAL FIX!!!

WORKED FOR ME!!!!!

AHHHH I'M SO HAPPY I COULD CRY!!!!

Okay, I wanted to share this with everyone cause it made me so freaking happy..
*CALM*

I have an ATI Radeon X1300, PCI-E running Kubuntu feisty. I stopped caring about beryl, compiz, xgl, and aiglx, just wanted my max resolution of 1680x1050 which I finally got.

I have done so much that I am trying to recall from memory what I did this time, and I hope it works for everyone who has had this same, insane problem.

I was getting the dreaded "XLib: extension "XFree86-DRI" missing on display ":0.0"." message.

Backup xorg.conf first!!

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Firstly, I *completely* removed: Envy, everything in /usr/src/ with the word "fglrx" in it, all the .debs with fglrx i had previously created, the linux-restricted-modules, and everything from adept/apt-get/synaptic with fglrx in it, including xorg-driver-fglrx.

Start from scratch.

What I did was, I had to compile my own driver for it from the proprietary one off the ATI site following this procedure: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")
going along method _2_.

HOWEVER, at this point: 

> Create .deb packages:

sudo bash ati-driver-installer-8.36.5-x86.x86_64.run --buildpkg Ubuntu/feisty

I did 

```
X_VERSION=x710 sudo bash ati-driver-installer-8.36.5-x86.x86_64.run --buildpkg Ubuntu/feisty
```

to simulate the old xorg version, as technically this ati-driver won't work for it (thankfully found it, it will!)

Then at the "**Configure the Driver**" section of the walkthrough, _do not_ aticonfig it at all, simply

```
sudo nano /etc/X11/xorg.conf
```

and change the "vesa" section under Device to "fglrx", then save it (with nano this is "ctrl+x").

then i restarted my xserver with ctrl-alt-backspace.

This led me to a blinking screen, do not fear!!

alt-f1 for the console

then

```
fglrxinfo
```

led me a result of something along the lines of "xorg-driver-fglrx is not installed", so downloaded that, along with it's dependances.

```
sudo apt-get install xorg-driver-fglrx
```

done. then 
```
startx
```

fini!

If someone could explain to me how I possibly did this, if anyone else gets this to work, any logs I can possibly post (not touching the desktop for a while now that it's working, basking it's warmth) ask anything cause I'm glad I finally fixed this problem for myself and hopefully can for others too!

---

### Post by life on 2007-06-03
> **wheredidrealitygo said:**
> 
POTENTIAL FIX!!!


Potential suxx!

read this - [link]("http://www.phoronix.com/scan.php?page=article&item=730&num=4")
and this - [link]("http://www.phoronix.com/scan.php?page=article&item=735&num=1")

and hold your breath

---

### Post by devil3000 on 2007-06-03
Okay hello every one, i am new to this complicated system, i am a windows user i have been reading over 50 threads of problems and yet i am still stuck with like 20 of them 
1. When installing ubuntu 7.04 on my dell xps 210 2.66 dual core ati x1300 1gb ram very fast computer.

i run the installation goes thru very well   like a drink of water, but when i try to install my graphic card so i can change the resolution i get no where . i have tried the following steps ([http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html))
and completed them 6 times meaning 6 additional steps of formatting my drive to remove ubuntu so i can re-install and try these steps again, why because every time i complete these steps ubuntu will lose my lcd display when entering the login screen and i am left with a blank screen , from what i understand it has to do with my ati x1300 which i have tried to configure several times

ok about now your probably wondering how stupid i am i agree because this ubuntu is so dam hard to understand comparing to xp , and the name its self is hard to read ( u.b.u.n.t.u ) who made that name any ways its sounds like a error in my head .

The only reason i would ever consider using ubuntu is because it looks hot. But dam how many of us had to go thru problems and problems


Now i am still looking to make the best of it if any one can help me or forward me to information easy to understand i would greatly appreciated my email address is [email]alexisright1000@yahoo.com[/email] 
Now I am a new Yorker so time is every thing

---

