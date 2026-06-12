---
title: "Cant install Ubuntu with new Graphics Card"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by overtone on 2011-11-27
Hi all,

[SIZE=4]**Problem**[/SIZE]
This may not actually be a graphics card problem but I'll explain it anyway.

I've used Ubuntu in the past and really had to tear myself away from it in the first place. I was having major problems and stutters with my ATI 4850 and it was driving me crazy. We were also moving onto .net in college so I wanted to match up my software with that in the campus (Visual studio)

I made a back up and went back to windows for a bit *shudders*.

But now as were finished .net, my girlfriend came into the room with a brand new Nvidia GTX 550 ti.. I didn't think she actually listened when i ranted about computers :D


So eager to get back to Ubuntu I went through the usual steps, grab the latest ISO, burn it and install. Only it dies before I even get to the first options screen.

It spits a lot of errors out in black and white which I can't seem to understand.

The top level erroris BUG: Unable to handle kernel NULL pointer at dereference......

Then goes on to something like:



[LIST]
[*]ffffff0x23847239
[*]ffffff0x45343578
[*]ffffff0x78736786
[/LIST]
(memory addresses?)

Others mention USBS and PCI errors all of which seem to be IO related.

I honestly don't know why this is happening but the only thing that has changed. I may go back and try it with my ATI 4850 just to make sure there isn't anything else I'm missing.

So why would I post in the Ubuntu forums if its a hardware error? Because its only with Ubuntu >=10.10

These are the things I've figured out definitively.



[SIZE=4]**Diagnostics**[/SIZE]


[LIST]
[*]It's only with Ubuntu 10.10 and above. 10.04 runs fine as does a heap of other Linux distributions including Linux mint (Ubuntu based). I haven't tried Debian yet.
[*]Its with all Ubuntu variants, Kubuntu, Xubuntu, Lubuntu, Edubuntu, Ubuntu Server but not Linux mint.
[*]32-bit or 64-bit makes no difference.
[*]It occurs on all mediums. I've tried CD, DVD, USB-live and VM (that last one is a bit of a wild card. Has its own set of problems)
[*]Its not a corrupt ISO because I've tried 3 separate downloads of it.
[*]I don't think its memory as I've ran some pretty extensive memory tests to no avail.
[*]I don't particularly want to install 10.04 and then upgrade as this will eat a lot more bandwidth and I don't want to risk going through my hard drive and deleting windows files (A bit paranoid but its happened before).
[/LIST]



[SIZE=4]**Final Thoughts**[/SIZE]

So those are my diagnostics. I suppose the first thing to clarify is the errors so my first question is, How do i scroll up from that console window that spits out errors?

The error screen that shows all the PCI errors and memory addresses shows a lot of information I imagine the first error in the list will point to the problem.

Any other thoughts are appreciated.

---

### Post by darkod on 2011-11-27
Usually the first thing to do is use the Try Ubuntu option first. Yes, we know you want to install, but running in live mode has its benefits, namely it will show if it works or not.

If booting into live mode doesn't work, for Nvidia cards usually the first thing to try is booting with using the nomodeset option.

At the main menu asking you whether you want to Try or Install, hit F6 for advanced options and look around (sorry I have no idea how exactly it looks). There is an option to turn on nomodeset. After that you can continue with Try Ubuntu.

If that worked you can install but note that on first boot it won't work without the nomodeset again. You will have to use 'e' and edit the boot line starting with linux adding nomodeset before the quiet splash.

Lets see if that worked before continuing. :)

---

### Post by darkod on 2011-11-27
My bad, they changed the access procedure a little in 11.10.
When you see the first purple screen before the language menu shows, you need to hit Esc fast. That will show a low-res language menu. Select the language and hit Enter.

Then you will see the old type standard menu and the F6 options access at the bottom. In there is nomodeset (you select with the up/down arrows and Space).

---

### Post by oldtimer7777 on 2011-11-27
You need to go purchase a graphic card that is supported Linux:

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)

And here is a nice guide after you get that installed:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Don't let your girlfriend purchase your computer parts for you anyone either. You need to put the big boy pants on and be a man.

---

### Post by overtone on 2011-11-27
> **oldtimer7777 said:**
> You need to go purchase a graphic card that is supported Linux:

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)

And here is a nice guide after you get that installed:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Don't let your girlfriend purchase your computer parts for you anyone either. You need to put the big boy pants on and be a man.

Gtx 550 ti is supported by Linux. She bought it because I had it circled in an store catalog.

There is nothing helpful about what you've posted above. Kindly stop trolling and get lost.


> **darkod said:**
> Usually the first thing to do is use the Try  Ubuntu option first. Yes, we know you want to install, but running in  live mode has its benefits, namely it will show if it works or not.

If booting into live mode doesn't work, for Nvidia cards usually the  first thing to try is booting with using the nomodeset option.

At the main menu asking you whether you want to Try or Install, hit F6  for advanced options and look around (sorry I have no idea how exactly  it looks). There is an option to turn on nomodeset. After that you can  continue with Try Ubuntu.

If that worked you can install but note that on first boot it won't work  without the nomodeset again. You will have to use 'e' and edit the boot  line starting with linux adding nomodeset before the quiet splash.

Lets see if that worked before continuing. :)

Sorry about that but it never even gets to the initial screen to give you the option of try or install. The only ubuntu that allows me to get that far is 10.04. Anything after that gives errors before any graphics can be displayed.

---

### Post by Hakunka-Matata on 2011-11-27
Remove the new Graphics Card, and try installing with your old graphics GPU active? maybe a good idea????
My BIOS allows me to select which GPU to use on boot-up,

[LIST]
[*]PCI-installed Graphics Card
[*]PCIe-installed Graphics Card
[*]ON-BOARD (MOBO) GPU
[*]The above examples are just that, I'm not sure they are presented with that exact text.......... did it from memory......... sort of
[/LIST]
Another user successfully installed in this manner, then simply re-inserted the PCI(e) graphics card and it booted, after which he searched for and installed, "**Additional Drivers"**.


blah-blah-blah............


Good Luck

---

### Post by overtone on 2011-11-27
So shift page up is how you move through the console. Learn something new everyday.


The first error that occurs is BUG: Unable to handle kernel NULL pointer at dereference......

And goes on for a while. Theres also a word that keeps popping up. Nouveau.

---

### Post by Hakunka-Matata on 2011-11-27
[http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=geforce%20gtx%20550%20ti%20ubuntu&pbx=1&oq=Gtx%20550%20ti%20ubuntu&aq=1m&aqi=g1g-m1&aql=&gs_sm=sc&gs_upl=1930l5700l1l9031l7l7l0l0l0l0l172l910l1.6l7l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=e9de948b95aa575a&biw=1920&bih=840&pf=p&pdl=300](http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=geforce%20gtx%20550%20ti%20ubuntu&pbx=1&oq=Gtx%20550%20ti%20ubuntu&aq=1m&aqi=g1g-m1&aql=&gs_sm=sc&gs_upl=1930l5700l1l9031l7l7l0l0l0l0l172l910l1.6l7l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=e9de948b95aa575a&biw=1920&bih=840&pf=p&pdl=300)

---

### Post by overtone on 2011-11-27
> **Hakunka-Matata said:**
> [http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=geforce%20gtx%20550%20ti%20ubuntu&pbx=1&oq=Gtx%20550%20ti%20ubuntu&aq=1m&aqi=g1g-m1&aql=&gs_sm=sc&gs_upl=1930l5700l1l9031l7l7l0l0l0l0l172l910l1.6l7l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=e9de948b95aa575a&biw=1920&bih=840&pf=p&pdl=300]("http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=geforce%20gtx%20550%20ti%20ubuntu&pbx=1&oq=Gtx%20550%20ti%20ubuntu&aq=1m&aqi=g1g-m1&aql=&gs_sm=sc&gs_upl=1930l5700l1l9031l7l7l0l0l0l0l172l910l1.6l7l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=e9de948b95aa575a&biw=1920&bih=840&pf=p&pdl=300")



.... Yes i've already googled it.


And no, i'll just leave this here isn't helping.

---

### Post by darkod on 2011-11-27
If you feel up to it, you can try the alternate install cd. It installs the same desktop system, but the installer is text based, not GUI and because of this has a wider options to work.

After that you should be also able to add a driver in text mode. Just investigate previously which is the correct driver for your card model. And whether you can install it directly on the net or have to download, copy it to that computer and run it.

---

### Post by overtone on 2011-11-27
> **darkod said:**
> If you feel up to it, you can try the alternate install cd. It installs the same desktop system, but the installer is text based, not GUI and because of this has a wider options to work.

After that you should be also able to add a driver in text mode. Just investigate previously which is the correct driver for your card model. And whether you can install it directly on the net or have to download, copy it to that computer and run it.


Good idea, 

I hadn't actually considered the alternate installer and am downloading it now. Im pretty sure i'll need to download it from the net to the computer and install it but in order to install the nvidia drivers, x and gdm have to be disabled so its going to be console based anyway,

Thanks for the help. I'll post back once I have an update. Also I'm still nto 100% sure its driver based but i'll let you know.

---

### Post by MAFoElffen on 2011-11-27
> **darkod said:**
> If you feel up to it, you can try the alternate install cd. It installs the same desktop system, but the installer is text based, not GUI and because of this has a wider options to work.

After that you should be also able to add a driver in text mode. Just investigate previously which is the correct driver for your card model. And whether you can install it directly on the net or have to download, copy it to that computer and run it.
+1... Just read all through this.  Kudo's on Darkod for his comments.

Additions to his and things not touched on yet:


On the LiveCD:
The menu Darko discribed is called the "Advanced Install Menu." After selecting "nomodeset", by arrowing down to it and pressing the spacebar... Press escape to get back to the main menu (keeps the selects). Then select "try"
 - Try using " nomodeset " again.  Nouveau is the Opensource driver for Nvidia, which doesn't work yet for that new a card.  If your getting Nouveau errors while using the kernel boot parameter, then something is aerie.
 - If that locks up at a black/purplish screen, then try these boot options:
```

xforcevesa
vga=792

```If those still do not work... (Share this method with others)

Get to the Advanced Install Menu.  Press escape. It will post a message saying that you are leaving the graphical instalation and entering a text mode installer...  It will  then probe the Graphics and try to find a mode.  It will do one of 3 things, 
- Find a mode and use it.
- Error, display the mode it didn't recognize and display a text menu  asking you what mode to use for a text install (I usually use 640x480x16  colors.)
- Error, dump the error as it crashes.  


Other Options--
Use a text based installation disk. These are my usual choices in order  of my persoonal preference. All 3 of these disks "say" text... (well...  trying to keep this short.)
- The Ubuntu Alternate Install Disk.
- The Ubuntu Minimal Install Disk.  This disk, if you did not selsct a  ttty text install and selected a normal/default install, when "tasksel"  comes up during the install, you have to select a desktop environment to  install.  If not, the Sys will be hung.  


After your install, you will have to use a "nomodeset" again at the Grub menu to boot... So you can install your drivers.

---

### Post by MAFoElffen on 2011-11-27
> **overtone said:**
> Good idea, 

I hadn't actually considered the alternate installer and am downloading it now. Im pretty sure i'll need to download it from the net to the computer and install it but in order to install the nvidia drivers, x and gdm have to be disabled so its going to be console based anyway,

Thanks for the help. I'll post back once I have an update. Also I'm still nto 100% sure its driver based but i'll let you know.

[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**
[/SIZE][/COLOR][/SIZE][/COLOR]
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 

[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")
[/SIZE][/COLOR][/SIZE][/COLOR]
All the instructions you'll need.  Note that with your card Nvidia Binary is v290.10. Ubuntu packaged would be nvidia-current-updates, which also could be installed from the Alternate Drivers applet, after booting the GUI using a boot option during boot.

Notes: 
 - 11.04 and earlier was GDM... 11.10 and Later is LightDM.
 - Many users in my sticky report that the NVidia GTX 520 and newer works better on v290.10... which the packaged nvidia-current is now at 280.13, the nvidia-current-updates at 285.05 = not there yet.  For "your" card, the current recommend is the binary.

---

### Post by overtone on 2011-11-27
> **MAFoElffen said:**
> [COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**
[/SIZE][/COLOR][/SIZE][/COLOR]
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 

[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")
[/SIZE][/COLOR][/SIZE][/COLOR]
All the instructions you'll need.  Note that with your card Nvidia Binary is v290.10. Ubuntu packaged would be nvidia-current-updates, which also could be installed from the Alternate Drivers applet, after booting the GUI using a boot option during boot.

Notes: 
 - 11.04 and earlier was GDM... 11.10 and Later is LightDM.
 - Many users in my sticky report that the NVidia GTX 520 and newer works better on v290.10... which the packaged nvidia-current is now at 280.13, the nvidia-current-updates at 285.05 = not there yet.  For "your" card, the current recommend is the binary.

I noticed the change in display managers. I still cant figure out why the difference between 10.04 and above is fatal.


On that note, I installed the alternate version of ubuntu just fine. It ran to completion but then wouldn't boot. Most liekly because I couldn't get to install the drivers themselves.

I also couldn't access the control panel with "Ctrl + alt + F1". Usually it works fine. Ill keep messing with it but I'd like to at least get the binary installed before i dismiss it.

```
Sudo apt-get install nvidia-current 
```

Should work I think. Thanks for giving me a target. I would have just tried any driver but some statistics are nice, cheers.

---

### Post by overtone on 2011-12-02
Just to give an update on whats happening. I'm having trouble with ubuntu installer detecting windows. I'd like a dual boot so once I'm sure that I have everything secure Ill proceed with the alternate install

---

### Post by efflandt on 2011-12-02
Just so you know, the GTX 550 Ti does work great with 64-bit 11.10.  Although, I installed (and reinstalled) Ubuntu using an off brand GT 430 that began failing after a year (video freeze ups, would often totally lose video signal between grub and login or if trying to return to X from console, even though Maverick seemed to work fine).

Since I installed EVA GTX 550 Ti, my 11.10 and Win7 issues have disappeared and everything works great.  Boots are without issue (faster than waking from suspend for some reason), I can return to X from console, and no freezes.

Do you have the extra power cable connected to the card and are you sure that your PSU has enough power.  I my PSU is 375 watt and NVIDIA recommends 400 watt, but Dell may rate them conservatively and my PSU had the proper power connector.  So all is well with no glitches.

I had been using **nomodeset** kernel boot parameter in 11.10, from when I was troubleshooting the GT 430, but I probably do not need that, because I never needed it in Maverick which is using same nvidia 290.10 drivers from x-swat repository.

---

### Post by overtone on 2011-12-04
SOLVED!!!


So i got it running. A nice dual boot with dual screens sorta working and a pretty quick unity.

Asides from everything else thats in the forum, here was the solution.


[LIST=1]
[*] Grab a alternate install cd of ubuntu 11.10
[*] Start up and before clicking install ubuntu, click f6 and select nomodeset
[*] If possible, have your internet connected so it will download the packages needed to run lightdm.
[*] one your finished installing you should have a very minimalist looking UI desktop running. If not the hit ctrl alt f1 to do a console login.
[*] once logged in, use the command
[/LIST]

sudo apt-get install nvidia-current

& restart. 


The rest is just business. Thanks to everyone who genuinely helped. I learnt a fair bit about bootloaders, drivers and grub. Also learned the apt-cache search command.

Teach a man to fish :D



And shame on the people who quoted stupid answers or just posted google searches expecting gratitude. The ubuntu forums have a very good reputation and it only takes a few bad apples to spoil the bunch.

Rock on Ubuntu Users!

---

