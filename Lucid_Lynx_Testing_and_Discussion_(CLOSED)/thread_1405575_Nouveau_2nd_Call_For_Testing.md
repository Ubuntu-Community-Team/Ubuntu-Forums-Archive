---
title: "Nouveau: 2nd Call For Testing"
date: 2010-02-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-02-12
Quoting Bryce Harrington:

> Hi all,

Do you have Nvidia graphcis hardware?  If so we need your help.

Nouveau is nearly ready for Lucid.  Us Ubuntu-X guys have been testing
this on our own hardware with decent results.  We need more people to
test this.  We need you!

Paint-by-number directions for installing and testing nouveau are
available here:

**[https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)**

There is also a table at the bottom for you to list your testing
results.

Bryce

Test! Test! Test! :cool:

---

### Post by donniezazen on 2010-02-13
> **MacUntu said:**
> Quoting Bryce Harrington:



Test! Test! Test! :cool:

I tried it couple of days ago and was not able to start X. I am not sure if that problem is fixed. I have a Dell E1505/6400 with a Nvidia GEforce 7300 graphic card.

---

### Post by cookiecruncher on 2010-02-13
It seems to be up and running on my pc.  My monitor's native resolution is 1440x900 and the resolution I'm expected to use is 1280x1024 which displays everything meant to be round as 'egg-shaped'.

Most definitely better than 800x600 ;)

```
$ xrandr
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0*
   1024x768        0.0
   800x600         0.0
   640x480         0.0

```

Asus website works fine.

'glxinfo'  lists a whole bunch of stuff ;)

```
$ glxgears
1686 frames in 5.0 seconds
1749 frames in 5.0 seconds
1750 frames in 5.0 seconds
1732 frames in 5.0 seconds

```

My pc's specs:
Core2duo E7400
Nvidia 9600GT
LG Flatron L192WS

---

### Post by MacUntu on 2010-02-13
Please don't forget to post your results to the Wiki! :)

---

### Post by SevenMachines on 2010-02-13
i do still seem to have problems with detected resolutions/xrandr, i've had that off and on with nouveau for a while when i've tested it. otherwise good though

---

### Post by vishalrao on 2010-02-13
ummm, why do i have kernel 2.6.32-13.13  and an older nouveau which fails to load in Xorg log with some DRM failure? : [http://pastebin.com/f21e7965d](http://pastebin.com/f21e7965d)


```

vishal@thunderbird:~$ apt-cache policy linux
linux:
  Installed: (none)
  Candidate: 2.6.32.13.13
  Version table:
     2.6.32.13.13 0
        500 http://fr.archive.ubuntu.com lucid/main Packages



vishal@thunderbird:~$ apt-cache policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: 1:0.0.15+git20100128+2630a15-0ubuntu1~ppa3
  Candidate: 1:0.0.15+git20100128+2630a15-0ubuntu1~ppa3
  Version table:
 *** 1:0.0.15+git20100128+2630a15-0ubuntu1~ppa3 0
        500 http://ppa.launchpad.net lucid/main Packages
        100 /var/lib/dpkg/status
     1:0.0.10~git+20090823+569a17a-0ubuntu1 0
        500 http://fr.archive.ubuntu.com lucid/universe Packages

```

Is the PPA outdated already?

---

### Post by MacUntu on 2010-02-13
git20100128+2630a15**5** seems to be a typo, and yes - it's only for the -12 kernel (no backports-modules for -13).

---

### Post by Elfy on 2010-02-13
I found the same thing here - I will leave it alone for the time being I think.

---

### Post by aamukahvi on 2010-02-13
I've been using nouveau from xorg-edgers for a while, but the latest updates screwed things up. Now on nvidia-glx.

7600GT

---

### Post by SevenMachines on 2010-02-13
Note for testing rotation/reflection. i get errors with the 1.1 extension both with nouveau and nvidia. is it worth also testing rotation with the 1.2 api? eg,
$xrandr --output <output> --reflection xy

due to this on either driver, 
$ xrandr -o 1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  148 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

---

### Post by SevenMachines on 2010-02-13
yes, no problems with that. just resolution detection and xrandr, which i'm guessing are related

---

### Post by phillw on 2010-02-13
Just a quick BTW...

>  * update nouveau to mainline 2.6.33-rc4
  * add new LBM package for nouveau
  * nouveau -- fix major numbers and proc entry names
  * fix up firmware installs for -wireless
  * clean up UPDATE-NOVEAU
  * update Nouveau to v2.6.33-rc6


Heading to the repos now, or very soon - just had the email with the details on.

[https://launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/2.6.32-12.1](https://launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/2.6.32-12.1) 

Regards,

Phill.

---

### Post by LKjell on 2010-02-13
> **SevenMachines said:**
> just a quick addition, it might be a good idea to separate the 'should nouveau be default' and the 'how to test and report on nouveau bugs' discussions into different threads. this should really be a practical testing thread to try and generate good information on the situation for various cards

That could be a good idea. 

However on my machine it works perfectly. The only problem which is not really one is that xrandr is saying that my maximum resolution is 8192 X 8192. Which is crazy. The current is 1440 x 900 and is the default. The card is Quadro NVS 140M (NV86). Therefore for my part it is rock solid.

---

### Post by SevenMachines on 2010-02-13
> **LKjell said:**
> That could be a good idea. 

However on my machine it works perfectly. The only problem which is not really one is that xrandr is saying that my maximum resolution is 8192 X 8192. Which is crazy. The current is 1440 x 900 and is the default. The card is Quadro NVS 140M (NV86). Therefore for my part it is rock solid.

i'm in the same situation as you, rock solid performance with nouveau, but xrandr problems with the identification of resolutions. if only the maximum resolution was 8192 X 8192 :)

---

### Post by donniezazen on 2010-02-13
> **MacUntu said:**
> Exactly one. :D



Cause that's not the point?

[https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

**Evaluation**. ;)

I bet if number system in your tribe starts with 2nd. Read the title '2nd Call'.

> **SevenMachines said:**
> just a quick addition, it might be a good idea to separate the 'should nouveau be default' and the 'how to test and report on nouveau bugs' discussions into different threads. this should really be a practical testing thread to try and generate good information on the situation for various cards

I agree and i think if some people are urging other to test then they should provide help too. If they are novice then this thread should be moved to community cafe.

---

### Post by 23meg on 2010-02-13
Off-topic posts have been split to a separate thread, and this one will remain sticky for a week. Further off-topic posts not pertaining to **testing Nouveau for possible default inclusion in Lucid** will also be removed/deleted, and further action will be taken if necessary. 

Please keep on topic. Happy breakage.

---

### Post by ronacc on 2010-02-13
passed all except glxinfo and xrandr , did not test suspend etc never use them . noticeable lag opening windows or minimise and maximise, scroll ok . sys amd64 video card 7600gs .

---

### Post by MacUntu on 2010-02-13
Isn't suspend supposed to work with all but TNT2 cards? It's only working on 2/14 systems in the Wiki (not that it ever had worked for me with -nv). :(

---

### Post by ibuclaw on 2010-02-13
Am just downloading Lucid now and will post results here on a 8400GS.

I've been meaning to wipe / reshuffle several partitions on my lappy for a while now anyway. ;)

Update:
```

lstdio@lstdio:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

```
```

lstdio@lstdio:~$ glxgears
2164 frames in 5.0 seconds
2659 frames in 5.0 seconds
2770 frames in 5.0 seconds
2782 frames in 5.0 seconds

```
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS-1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-D-1 disconnected (normal left inverted right x axis y axis)

```

Flash works.
Sauerbraten (poorly) works.
No Compiz ... but I always preferred [xcompmgr]("apt:xcompmgr") anyway. ;)

Regards
Iain

---

### Post by uBeer on 2010-02-13
> **phillw said:**
> Just a quick BTW...



Heading to the repos now, or very soon - just had the email with the details on.

[https://launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/2.6.32-12.1](https://launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/2.6.32-12.1) 

Regards,

Phill.

Too bad, the update didn't do much good to me. Before the update everything worked well, switching VT's, glxgears, xrandr rotation. Even suspend! Then I restarted after the update and now I get freezes sometimes and when I try to switch VT's my mouse disappears but the rest stays on the screen. When I do Ctrl-Alt-F7 my mouse appears again and I can interact with my desktop again.

Btw, how can I easily make the setup of my screens the default (or: how can I produce an xorg.conf from my current setup)? I have two screens and when the pc starts it puts them in mirror mode, but I would rather have them be never in mirror mode. I think plymouth fails because of that. When I shut down my pc I do see plymouth working nice on both screens, but not when on startup.

---

### Post by ronacc on 2010-02-13
how do I add my results to the wiki ? I am signed in but can't find where to add my results.

---

### Post by ronacc on 2010-02-14
I'll ask this again here since I'm not getting an answer on the testing thread , how do I add my results to the wiki page ? I sign in with my launchpad ID but all it wants to do is let me edit the whole page and that don't seem right .

---

### Post by 23meg on 2010-02-14
> **ronacc said:**
> I'll ask this again here since I'm not getting an answer on the testing thread ,

I've moved your post to the testing thread.

[QUOTE=ronacc]how do I add my results to the wiki page ? I sign in with my launchpad ID but all it wants to do is let me edit the whole page and that don't seem right .[/QUOTE]

It *is* right. Click "Edit", scroll down to the "Report Your Results" heading, and if you've never edited a wiki table before, simply mimic the table format others have used via copy/paste.

---

### Post by SevenMachines on 2010-02-14
have to admit, its not the easiest looking way to add test results. here's mine

|| x86-64 ([GT200] GTX 260 Core 216)  || [[[]"]https://launchpad.net/~sevenmachines|SevenMachines]]]("https://launchpad.net/%7Esevenmachines%7CSevenMachines)  || (./) || (./) || {X} || {X} || {X} || (./) || (./) || (./) ||  {X} || 2010-02-13 || Resolutions wrong in settings and xrandr. xrandr -o causes BadMatch errror. suspend untested  ||

firstly, '(./)' is a tick, the test has passed, {X} is a cross, the test has failed. the entries are...

|| <card model>  || <my launchpad address>|<my name>]]  || <boots?> || <vt switching?> || <default resolution?> || <resolution listing?>|| <invert?> || <movie playing?> || <flash?> || <3d?> ||  <suspend?> || <date> || <comments>  ||

the details on how to carry out the tests are on the web page, entries with a ? should have a tick or a cross.

log in using your launchpad id and edit the page (yes it does edit the whole page!), add your entry to the bottom of the table of entries already there, then click preview to see if everythings ok before saving the changes

---

### Post by ronacc on 2010-02-14
thanks , I was unsure about editing someone elses page .

---

### Post by SevenMachines on 2010-02-14
> **ronacc said:**
> thanks , I was unsure about editing someone elses page .
i know what you mean, it doesnt seem right to be able to ruin the entire thing with an accidental edit, such is the wiki way though :)

---

### Post by gnomeuser on 2010-02-17
I installed the PPA on the day the first testing was announced and outside of lag playing movies in fullscreen and no Plymouth beauty on boot it was great.

Then I switched back to the nvidia driver since a friend was coming and we needed to watch some fullscreen goodness (and no time to dig into the fix since I know nouveau has XV acceleration). 

However upon cleaning out the driver the day after and reenabling the PPA, it now fails. The nouveau module simply isn't loaded.

Looking at the PPA it seems that a number of the packages are now outdated by versions in the Lucid repos. I suspect this might have a thing or two to do with why it fails for me now.

Any pointers?

---

### Post by SevenMachines on 2010-02-18
hi there. the nouveau stuff is now in the main repository so the ppa shouldnt probably be used at the moment. for the modules you'll need to be using kernel 2.6.32-13 unless you've got the -12 ones left over from a previous install

module packages,
linux-backports-modules-nouveau-lucid-generic
nouveau-firmware

you'll need xserver-xorg-video-nouveau too but it needs dependencies update from 2.6.32-12 to -13 at the moment. if you change the dependencies and rebuild the package it will work just now (i'm using it right now!)

if the nouveau module isnt loading it might be worth checking that all nvidia packages are completely gone, i've a funny feeling they prevent nouveau loading to avoid problems, a modprobe nouveau would give a FATAL: error in this case

---

### Post by LKjell on 2010-02-18
Thanks for the tip. You know why the git version from Debian is less than the one from lucid?

> **SevenMachines said:**
> hi there. the nouveau stuff is now in the main repository so the ppa shouldnt probably be used at the moment. for the modules you'll need to be using kernel 2.6.32-13 unless you've got the -12 ones left over from a previous install

module packages,
linux-backports-modules-nouveau-lucid-generic
nouveau-firmware

you'll need xserver-xorg-video-nouveau too but it needs dependencies update from 2.6.32-12 to -13 at the moment. if you change the dependencies and rebuild the package it will work just now (i'm using it right now!)

if the nouveau module isnt loading it might be worth checking that all nvidia packages are completely gone, i've a funny feeling they prevent nouveau loading to avoid problems, a modprobe nouveau would give a FATAL: error in this case

---

### Post by donniezazen on 2010-02-18
> The following packages are BROKEN:
  linux-backports-modules-nouveau-2.6.32-12-generic 
The following NEW packages will be installed:
  libdrm-nouveau1{a} nouveau-firmware{a} xserver-xorg-video-nouveau 
0 packages upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 896kB of archives. After unpacking 2,245kB will be used.
The following packages have unmet dependencies:
  linux-backports-modules-nouveau-2.6.32-12-generic: Depends: linux-image-2.6.32-12-generic which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-backports-modules-nouveau-2.6.32-12-generic [Not Installed]
xserver-xorg-video-nouveau [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


Any solution for this.

Thanks.

---

### Post by LKjell on 2010-02-18
> **soham_1207 said:**
> Any solution for this.

Thanks.

Do you have the kernel installed package somewhere? Since it says it is not installed and you try to install it first. But that kernel is old and is not in the repo anymore. So you need the new kernel's backport but you will also need xserver-xorg-video-nouveau which you will have to compile it yourself...

---

### Post by donniezazen on 2010-02-18
> **LKjell said:**
> Do you have the kernel installed package somewhere? Since it says it is not installed and you try to install it first. But that kernel is old and is not in the repo anymore. So you need the new kernel's backport but you will also need xserver-xorg-video-nouveau which you will have to compile it yourself...

Hmmm may be later. But the xserver-xorg-video-nouveau is available in repo so if i install the new kernal's backport why do i have to compile it.

Thanks.

---

### Post by LKjell on 2010-02-18
> **soham_1207 said:**
> Hmmm may be later. But the xserver-xorg-video-nouveau is available in repo so if i install the new kernal's backport why do i have to compile it.

Thanks.

Because it depends on the kernel you do not have.

---

### Post by rubenverweij on 2010-02-19
If I'm not mistaken, there is a package for the standard 2.6.32-13 kernel now in the official repos. There were also some updates to the x server to fix the dependency errors. Should I still keep the xorg-edgers ppa on my system or should I use the official versions for testing?

---

### Post by SevenMachines on 2010-02-19
i think i'd be moving to the main repository rather than the ppa to test, it looks like thats where the newer packages and changes will be added now, unless someone knows different.

the xorg module update is available now so all packages should install fine on the 2.6.32-13 kernel 

installing the packages below should do it

linux-backports-modules-nouveau-lucid-generic
xserver-xorg-video-nouveau
nouveau-firmware

i dont know if the  firmware one is still needed, i think so, but its gradually being replaced by work in the actual nouveau driver as i understand it

---

### Post by gnomeuser on 2010-02-19
Sadly either I am doing it wrong somehow or nouveau is broken whereas it used to work during the first call for testing. *sob*

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/524415](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/524415)

---

### Post by lion1969 on 2010-02-19
xserver-xorg-video-nuoveau  depends on the standard (= non PAE) version of linux-backports-modules-nouveau-lucid-generic
as a result last xorg update installs the non PAE kernel on systems already using the PAE kernel which is not so smart

---

### Post by donniezazen on 2010-02-19
Hi,

The latest upgrade which included nouveau has broken my system. I am not able to get to GDM and not even recovery mode to get to command line. Please help.

Thanks.

---

### Post by anders_c_ on 2010-02-19
Didn't work for me first either, then when i purged plymouth it started working again.

---

### Post by donniezazen on 2010-02-19
Due to enter key freeze bug i already purged plymouth long time. For some reason i am not even able to install Nvidia drivers.

Thanks.

---

### Post by Digital Hick on 2010-02-19
Something like 12 packages marked **new install** landed in the update manager yesterday.  I seems they have backported Nouveau from 2.6.33 into 2.6.32.  I am not sure if this is a good idea for an LTS.:icon_frown:

After the reboot plymouth looked like it was going nuts.  It scrolled *broken pipe* all over the screen and flickered like crazy in Virtualbox 3.1.4.  It eventually started.  After that it seemed alright.  Rebooted a few times since and installed more updates and it is stable for me.

Try reinstalling plymouth from a tty if you can get to one.
**Ctrl+Alt+F2** for example.

If you can't get that far hold down **Shift** as soon as you turn the machine on until you get through GRUB.  It should bring up the boot loader menu.  Try typing 'e' get a boot editor.

I think, holding down **esc** during plymouth will bring out some kind of utility was well.  I have seen something there when I was fighting with Lucid earlier, but I can't remember for sure.

Other than that prepare to reinstall. :popcorn:

---

### Post by donniezazen on 2010-02-19
> **Digital Hick said:**
> Something like 12 packages marked **new install** landed in the update manager yesterday.  I seems they have backported Nouveau from 2.6.33 into 2.6.32.  I am not sure if this is a good idea for an LTS.:icon_frown:

After the reboot plymouth looked like it was going nuts.  It scrolled *broken pipe* all over the screen and flickered like crazy in Virtualbox 3.1.4.  It eventually started.  After that it seemed alright.  Rebooted a few times since and installed more updates and it is stable for me.

Try reinstalling plymouth from a tty if you can get to one.
**Ctrl+Alt+F2** for example.

If you can't get that far hold down **Shift** as soon as you turn the machine on until you get through GRUB.  It should bring up the boot loader menu.  Try typing 'e' get a boot editor.

I think, holding down **esc** during plymouth will bring out some kind of utility was well.  I have seen something there when I was fighting with Lucid earlier, but I can't remember for sure.

Other than that prepare to reinstall. :popcorn:

Since i am getting a frozen black screen after Grub, i guess its time to reinstall.

Thanks anyways.

---

### Post by rubenverweij on 2010-02-20
I just updated nouveau to version 1:0.0.15+git20100128+2630a15-0ubuntu2 and get a whole bunch of warnings from update-initramfs:
```
update-initramfs: Generating /boot/initrd.img-2.6.32-13-generic
W: Possible missing firmware /lib/firmware/nouveau/nvac.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvac.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvaa.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvaa.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva8.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva8.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva5.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva5.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva0.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva0.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv98.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv98.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv96.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv96.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv94.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv94.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv92.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv92.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv86.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv86.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv84.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv84.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv50.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nv50.ctxprog for module lbm_nouveau

```
Anything I can do about it/should worry about/report a bug/be patient? :D
TIA

---

### Post by SevenMachines on 2010-02-20
from a previous post, try installing the below package, it is gradually being replaced it seems but you might find it useful for the moment

> nouveau-firmware

i dont know if the  firmware one is still needed, i think so, but its  gradually being replaced by work in the actual nouveau driver as i  understand it

---

### Post by doctordruidphd on 2010-02-20
You don't need to reinstall, if you have an older kernel still installed on your system.

Boot into the older kernel. Hopefully that will get you the low graphics mode, or at least a console.

You then need to 

```
sudo apt-get remove --purge linux-backports-modules-nouveau-2.6.32-14 
```

or whatever kernel it installed on.

Next boot should get you to the low graphics mode.
I was able to reinstall the proprietary NVIDIA driver, but only after purging and restarting.

I did actually manage to get the nouveau driver to come up, but I couldn't figure out how to set the screen resolution, so I dumped it.  You have to change your xorg.conf file, commenting out the device section referencing to your old driver, and inserting:

```
Section "Device"
       Identifier      "Device0"
       Driver          "nouveau"
EndSection                  
```

If someone can figure out how to set the screen resolution to a reasonable value, I'd like to try this, although the documentation says it doesn't support 3d acceleration, so it's of limited value.

---

### Post by 23meg on 2010-02-20
Nouveau is now set as the default driver, and testing to ensure smooth switching to the NVIDIA proprietary driver and back continues.

[https://lists.ubuntu.com/archives/ubuntu-x/2010-February/000766.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-February/000766.html)

---

### Post by donniezazen on 2010-02-20
> **doctordruidphd said:**
> You don't need to reinstall, if you have an older kernel still installed on your system.

Boot into the older kernel. Hopefully that will get you the low graphics mode, or at least a console.

You then need to 

```
sudo apt-get remove --purge linux-backports-modules-nouveau-2.6.32-14 
```

or whatever kernel it installed on.

Next boot should get you to the low graphics mode.
I was able to reinstall the proprietary NVIDIA driver, but only after purging and restarting.

I did actually manage to get the nouveau driver to come up, but I couldn't figure out how to set the screen resolution, so I dumped it.  You have to change your xorg.conf file, commenting out the device section referencing to your old driver, and inserting:

```
Section "Device"
       Identifier      "Device0"
       Driver          "nouveau"
EndSection                  
```

If someone can figure out how to set the screen resolution to a reasonable value, I'd like to try this, although the documentation says it doesn't support 3d acceleration, so it's of limited value.

Their was only one Kernel in Grub list and i was not able to get a command neither tty nor the recovery mode. I have already reinstalled Lucid. 

> **23meg said:**
> Nouveau is now set as the default driver, and testing to ensure smooth switching to the NVIDIA proprietary driver and back continues.

[https://lists.ubuntu.com/archives/ubuntu-x/2010-February/000766.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-February/000766.html)

Isn't it too early to make Nouveau in LTS? It doesn't support 3D and most of the people will be forced to go back to Nvidia.

Thanks.

---

### Post by LKjell on 2010-02-20
> **soham_1207 said:**
> Their was only one Kernel in Grub list and i was not able to get a command neither tty nor the recovery mode. I have already reinstalled Lucid. 



Isn't it too early to make Nouveau in LTS? It doesn't support 3D and most of the people will be forced to go back to NV.

Thanks.

NV is the 2D driver not the 3D one.

---

### Post by donniezazen on 2010-02-20
> **LKjell said:**
> NV is the 2D driver not the 3D one.

Sorry i meant nvidia graphic drivers.

---

### Post by archish on 2010-02-20
> **soham_1207 said:**
> Their was only one Kernel in Grub list and i was not able to get a command neither tty nor the recovery mode. I have already reinstalled Lucid. 



Isn't it too early to make Nouveau in LTS? It doesn't support 3D and most of the people will be forced to go back to Nvidia.

Thanks.


The idea is manily for those who dont need 3d/older cards and dont want to install the binary driver. If I am only going to watch movies and browse around then nouveau makes more sense than installing the binary blob. On the long run it would be easier to maintain from the user end perspective and should have less stability issues.

---

### Post by JasperK on 2010-02-21
I have been testing nouveau on my pc for some time now. I works beautifully in a separate install of lucid I use for testing, but I can't get it to work in my main install. Plymouth loads, I get a high-resolution terminal, but gdm won't start.

I get this error in my X log:
```
(II) [drm] nouveau interface version: 0.0.15
(EE) [drm] KMS not enabled
(EE) No devices detected.
```But this dmesg line says that the drm is initialized, doesn't this mean that KMS is enabled?
```
[lbm-drm] Initialized nouveau 0.0.15 20090420 for 0000:05:00.0 on minor 0
```There is probably something left over from the early testing packages I installed. I did a purge and reinstall of xserver-xorg-* and libdrm packages, but that didn't help.

When i try to build xserver-xorg-video-nouveau deb from source myself I get the folowing error:
```

  CC     nouveau_dri2.lo
../../src/nouveau_dri2.c: In function &#8216;nouveau_dri2_create_buffer&#8217;:
../../src/nouveau_dri2.c:50: error: &#8216;DRI2BufferDepthStencil&#8217; undeclared (first use in this function)

```Seems like I there is a version difference somewhere, but I can't find it.

Any ideas?
[B]
EDIT[/B]: I found the offending files in /usr/local, it works now.
I have a "nVidia Corporation NV41GL [Quadro FX 1400] rev 162" and two 20" screens. Every thing works as far as I can see, good work!

---

### Post by gnomeuser on 2010-02-21
Afte a few more updates, I am now using nouveau to power my Ubunt experience. Sure there is no 3d acceleration (and thus no glorious compiz wobbly windows to distract me) but what I miss the most is frankly working XV acceleration which should be present in Nouveau but I suspect it just hasn't been implemented for ION yet.

I am looking forward to the remaining highly unstable bits hit the Xorg-edgers ppa, then I should be able to easily start testing the 3d support in nouveau which the nice Fedora people made headlines showing off as being one package install away on their F13 development platform about 2 weeks ago.

Regardless aside the inability to play movies in fullscreen till the xv situation is sorted out I am very pleased with Nouveau. I am glad to see it being made the default 2d video driver for Nvidia over nv for Lucid.

---

### Post by tito_torrisi on 2010-02-21
I also have an Acer Revo, and after a reinstall nouveau worked (also told you in the bug report).
I can watch xvid or divx videos fullscreen with smplayer and xv (not working with totem). I would rather like gnome-shell to work. I guess getting something like vaapi or vdpau (which would be very important for the hd stuff) to work is not possible.

edit: I have the Atom 330 (2x1,6) dualcore edition with 4 GB RAM, maybe that's the difference?

vdpau+nouveau [http://www.phoronix.com/scan.php?page=news_item&px=NzE0Mg](http://www.phoronix.com/scan.php?page=news_item&px=NzE0Mg)

---

### Post by uBeer on 2010-02-21
Too bad xv doesn't work for you yet. Here it's working nicely I guess: fullscreen video's work nicely. Only fullscreen flash movies don't play nice, but at least it stretches well now! The Youtube movies now have the right ratio when having multiple screen setup and it takes the screen where the movie was when pressing the full screen button, so if it would only play it fluid than it would be awesome!

Edit: Actually, ratio is still not right, but at least it now you can put it on the screen you want...

---

### Post by gnomeuser on 2010-02-21
> **tito_torrisi said:**
> I also have an Acer Revo, and after a reinstall nouveau worked (also told you in the bug report).
I can watch xvid or divx videos fullscreen with smplayer and xv (not working with totem). I would rather like gnome-shell to work. I guess getting something like vaapi or vdpau (which would be very important for the hd stuff) to work is not possible.

edit: I have the Atom 330 (2x1,6) dualcore edition with 4 GB RAM, maybe that's the difference?

I have the same hardware Acer Aspire Revo R3610.

I only tested with Gstreamer (effectively your totem test) via gstreamer-properties, and it utterly fails. I filed a [bug](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/525273)

Let's hope this can get resolved.

---

