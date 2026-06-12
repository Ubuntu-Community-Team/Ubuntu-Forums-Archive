---
title: "no kde since update"
date: 2009-11-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-11-25
I can't run a kde session since latest update.  Right after update I was getting an error "kstartupconfig4 error or not installed".

I found a thread about this from gutsy that said to 
```
sudo chown -R username.username /home/username/.kde

```
that got rid of the error, but now i get a blank black screen with a mouse cursor that works..... but that's it.

gnome works fine right the moment

gdm works but now kdm won't start either.

any suggestions?

---

### Post by zenarcher on 2009-11-25
I don't have a solution for the problem, but if it's any consolation, I experienced the same thing.  I did a fresh install of Lucid Kubuntu 64 bit and have not done the updates at this time and all is working fine.

Cheers,
zenarcher

---

### Post by caryb on 2009-11-25
Can confirm on my new install then upgrade = console login. I did try login as self & run sudo startx it fires up goes through the KDE panel "stuff" then crashes back to the console with message xinit: connection to X server lost.



Cary

---

### Post by tekkidd on 2009-11-25
Try deleting your user settings for it 

At the login window do CTRL+ALT+F1 then login and type

cd /home/<username>/
rm -r .kde

---

### Post by caryb on 2009-11-25
> **tekkidd said:**
> Try deleting your user settings for it 

At the login window do CTRL+ALT+F1 then login and type

cd /home/<username>/
rm -r .kde

That seems a bit extreme wouldn't the config folder suffice?


Cary

---

### Post by caryb on 2009-11-25
I just tried the config file 1st then the whole .kde folder & still no good!


Cary

---

### Post by caryb on 2009-11-25
Am suspecting it's a Intel graphics fault? are the other users with this problem using a Intel chip?


Cary

---

### Post by caryb on 2009-11-25
This appears to be a duplicate of [http://ubuntuforums.org/showthread.php?t=1337082]("http://ubuntuforums.org/showthread.php?t=1337082")

Cary

---

### Post by tghe-retford on 2009-11-25
KDE4 completely borked here. Using Openbox for the moment. Looks like there are a few errors appearing if I run any KDE/QT application:
```

kdeinit4: kded4 [kdeinit]: symbol lookup error: /usr/lib/kde4/kded_favicons.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
kaffeine: symbol lookup error: /usr/lib/kde4/plugins/styles/oxygen.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
```
Sound is dead as well, no sound from any application.

---

### Post by Bachstelze on 2009-11-25
> **tghe-retford said:**
> KDE4 completely borked here. Using Openbox for the moment. Looks like there are a few errors appearing if I run any KDE/QT application:
```

kdeinit4: kded4 [kdeinit]: symbol lookup error: /usr/lib/kde4/kded_favicons.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
kaffeine: symbol lookup error: /usr/lib/kde4/plugins/styles/oxygen.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
```
Sound is dead as well, no sound from any application.

Same error here.

---

### Post by zenarcher on 2009-11-25
> **caryb said:**
> Am suspecting it's a Intel graphics fault? are the other users with this problem using a Intel chip?


Cary

Nope, I'm using Nvidia here.

Cheers,
zenarcher

---

### Post by caryb on 2009-11-25
That blew that theory! I just had some kdebase files upgraded & thought that might have fixed the problem, but alas....


Cary

---

### Post by buzzmandt on 2009-11-25
nvidia here as well, I'm holding off on updating my lappy with the intel graphics since you say it does it there too.

I removed the .kde folder and tried it anew, no good

I also created a new user account and tried that, still no good.

I've also tried using kdm, it completely fails

gdm works, but if the session is set to kde it fails.

still using gnome here, really missing my kde

---

### Post by caryb on 2009-11-25
That explains why when I installed openbox this morning to get around the problem it fails.


Cary

---

### Post by LKjell on 2009-11-26
> **tghe-retford said:**
> KDE4 completely borked here. Using Openbox for the moment. Looks like there are a few errors appearing if I run any KDE/QT application:
```

kdeinit4: kded4 [kdeinit]: symbol lookup error: /usr/lib/kde4/kded_favicons.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
kaffeine: symbol lookup error: /usr/lib/kde4/plugins/styles/oxygen.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
```
Sound is dead as well, no sound from any application.
Kile runs perfectly. QT virtualbox as well. I think it is just selected programs.

---

### Post by caryb on 2009-11-26
Well I got openbox going! I had to give myself permission to ~/ICEauthority


Cary

---

### Post by tghe-retford on 2009-11-26
Just updating this morning has got me back in. Sound is still broken, KDE seems to believe that all my sound devices have been removed but then still lists one as available for my onboard sound! Not that it works. KMix and Lancelot fail to work, so I can't fix any sound problems that way. I am having to use KDE's original menus as a workaround. VLC can't see my Digital TV card whilst Kaffeine can. Very odd.

---

### Post by zenarcher on 2009-11-26
I will probably wait until tomorrow to try updates again and see if the problem is fixed for me.  I'll watch here and see if anyone else finds the updates to resolve the issue.

Thanks for the update!

Cheers,
zenarcher

---

### Post by buzzmandt on 2009-11-26
This morning updates brings me back to kde, Oh how i missed my kde....

anyway, lancelot launcher and quickaccess browser are borked.  Everything else is working including sound.


Edit:  Dragon Player doesn't work and volume control in the taskbar is missing and I can't seem to put it back.  One last thing i've found so far, no right click on the desktop for menu, no desktop menu at all. Better than it was though.   Keep the updates coming boys...lol

Edit #2, right clicking inside dolphin file manager kills dolphin. and konsole doesn't work, have to use terminal emulator.

---

### Post by buzzmandt on 2009-11-26
just got a few more updates including kmix and dragonplayer, dragon is working again and i have my volume applet back in the taskbar.

still no right click menu on the desktop or konsole.  I'm sure those will be restored soon.

---

### Post by ronacc on 2009-11-26
seeing this thread last night I started to update to get in on the fun . 345 meg of update and the server running slow meant it didn't finish until this AM , cheked again 135 meg more updates , server not so loaded I guess , these took 11 min . rebooted ok , dolphin is ok here, right click does not kill it . Sound is partialy out system souds ok but won't play music . going to system settings>multimedia my sound device (onboard) is listed and tests clicking on "apply device list to" music is greyed out . also I lost one plasmoid it comes up "could not find requested component" (not sound related) , reinstalling it no help .

---

### Post by buzzmandt on 2009-11-26
> **ronacc said:**
> seeing this thread last night I started to update to get in on the fun . 345 meg of update and the server running slow meant it didn't finish until this AM , cheked again 135 meg more updates , server not so loaded I guess , these took 11 min . rebooted ok , dolphin is ok here, right click does not kill it . Sound is partialy out system souds ok but won't play music . going to system settings>multimedia my sound device (onboard) is listed and tests clicking on "apply device list to" music is greyed out . also I lost one plasmoid it comes up "could not find requested component" (not sound related) , reinstalling it no help .

ronacc, can you right click on the desktop for menu?

music plays on mine and sound is good, I have usb audio only.
right clicking empty space in dolphin still kills dolphin out.
My kdm login screen works again now too.

---

### Post by ronacc on 2009-11-26
right click on desktop brings up the menu ok , investigated sound some more mplayer would play, audacious would not , remembered that the first batch of updates removed amarok , reinstalled it and it plays ok too . sound here is onboard alc883  .

---

### Post by hikaricore on 2009-11-26
This is the reason I've not rebooted in about a week.
Some of the fault lies in the following packages:

kdebase-runtime
kdelibs5
kdelibs5-data
kde-window-manager
libplasma

Upon force replacing them with versions from karmic and leaving my package system slightly broken everything works again.

---

### Post by tghe-retford on 2009-11-26
OK - current status report on my system:

DVB-T works fine, that was an unrelated issue.
Sound is now working again, KMix update got it working again and I could adjust some of the settings to get sound back.
Lancelot is still broken, still using the old menu for now. Many other widgets (like the System Load Viewer) are broken too.

---

### Post by caryb on 2009-11-26
As of now I still have a black screen & mouse. I tried alt + f2 but that is borked too, back on openbox for now.


Cary

---

### Post by zenarcher on 2009-11-27
Well, I ran all the updates here this morning.  Rebooting was rather slow and eventually took me to a text login.  I logged in and startx got me up and going with the desktop.  

The comics plasmoid isn't working now.  Sound is working, but not pulseaudio.  When I start Firefox or Chromium browser, they begin to open, then crash. When I start Stellarium, it partially opens but all I get is the hidden bar at the bottom of Stellarium, so I can close the application out.  Googleearth is fine and most other applications I've tried.  

We'll see what comes through in updates the next day or two.

Cheers,
zenarcher

---

### Post by hikaricore on 2009-11-27
Pulse works fine here so you're doing something wrong.
The only things that seem to be crashing are things that require kdelibs and only half of those are doing so.
Idk if you are all just late bloomers here or what by kde has been screwed up for over a week now.
It'll get fixed eventually then it will break again, this is the life of a prealpha tester.

---

### Post by zenarcher on 2009-11-27
> **hikaricore said:**
> Pulse works fine here so you're doing something wrong.
The only things that seem to be crashing are things that require kdelibs and only half of those are doing so.
Idk if you are all just late bloomers here or what by kde has been screwed up for over a week now.
It'll get fixed eventually then it will break again, this is the life of a prealpha tester.

Well, Pulseaudio was working fine before this big update I did this morning, but now, I get an error message that Pulseaudio isn't working and sound is reverting back to ALC888.  Not a big deal, as I still have sound.

Yeah, the first time I did updates, KDE messed everything up, so did a reinstall and waited a couple of days and just thought I would try the updates again this morning.  It's improved at the moment, but I'm sure there will be a lot more breakage.  For me, it's the luxury of being retired and having a spare test box.  Pre-Alpha's are more interesting that spending the day at the Senior Citizen's Center...take my word for it. ;)

Cheers,
zenarcher

---

### Post by hikaricore on 2009-12-01
Incase anyone is wondering yes kde is still borked.
It's now a different borked but luckily I've not had to reboot or shutdown lately.
Now if this goes on for a two months or so.... then we have problems. ^_^
I'm sure at some point the power in Ohio is gonna go out this winter, just hope kde works again by then.  ;)

---

### Post by camrant on 2009-12-01
I had a similar problem after an update and restart x would not load and couldn't find any answer. My solution was to 

create a backup of my current /etc/X11/xorg.conf file
 
then I deleted to config section for my video card.

rebooted and x loaded some defaults to get going and then I reinstalled the drivers for my vid card.

Stress making the back up so that you can undo if you don't like results.  Finding a generic default xorg.conf file to test out may be a better idea then deleting configs but it worked for me.

---

### Post by hikaricore on 2009-12-02
> **camrant said:**
> I had a similar problem after an update and restart x would not load and couldn't find any answer. My solution was to 

create a backup of my current /etc/X11/xorg.conf file
 
then I deleted to config section for my video card.

rebooted and x loaded some defaults to get going and then I reinstalled the drivers for my vid card.

Stress making the back up so that you can undo if you don't like results.  Finding a generic default xorg.conf file to test out may be a better idea then deleting configs but it worked for me.

Hi I'm sorry, do you even have a clue what the hell you're talking about?
Various KDE libraries are broken, like broken broken, this has nothing to do with X...

---

### Post by ronacc on 2009-12-02
I updated this AM after not having done so in a couple of days , used kapckage manager and that resulted in 1 broken package , used synaptic to fix that and complete the update , as soon as the update finished I reloaded the repos and more updates showed so I installed them before rebooting . Rebooted with no problem .

---

### Post by hikaricore on 2009-12-02
But do all your kde applications run?  :p

---

### Post by ronacc on 2009-12-02
whats not running for you  , I'll try it and see .

---

### Post by Bachstelze on 2009-12-02
Kopete is the only KDE thing not working here.

---

### Post by hikaricore on 2009-12-02
Kate doesn't run and Dolphin fails with kiofile errors.
There's others but I can't test atm as I'm not home.

> kate: symbol lookup error: /usr/lib/libkateinterfaces.so.4: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei


I'm no longer getting the kwin/kdecorate errors that plagued me for a bit, but various plasmoids are locking up.

---

### Post by ronacc on 2009-12-02
dolphin is ok here , kate hasn't been working from dolphin>open with since I started 10.04 but does open from the menu and will open the same file that "open with"  wont . The plasmoids I am running are ok but I only have a few  up , which ones are locking on you , I'll give them a try .

---

### Post by Bachstelze on 2009-12-03
Yup, Kate not working either here, I wonder how I could miss it. Dolphin works fine.

---

### Post by ronacc on 2009-12-03
kate now out for me too , same error as hikaricore . ark also out same undefined symbol different lib .
```
ark: symbol lookup error: /usr/lib/kde4/kerfuffle_libarchive.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei

```

---

### Post by ronacc on 2009-12-03
has anyone bugged this undefined symbol thing yet ? if so please post bug# .

---

### Post by koso on 2009-12-03
It has its bug report, but it was closed, becase its it not bug .. problem is only that not all components of KDE were rebuild against new QT library, which is binary incopatible with previous version. It seem, that devs are waiting for new kde, which is out for a few days now and already available in kubuntu ppa (KDE 4.3.4) .. I hope that lucid will get 4.4.

btw. I updated now, and now my desktop is crashing just after login .. so i dont get desktop and plasma .. anyone else with this problem?

---

### Post by Bachstelze on 2009-12-03
> **koso said:**
> It has its bug report, but it was closed, becase its it not bug .. problem is only that not all components of KDE were rebuild against new QT library, which is binary incopatible with previous version.

That's surprising, because I installed the Karmic version of Kopete and Kate, and they work fine.

(So yes, this works as a temporary workaround, by the way.)

---

### Post by Reiger on 2009-12-03
> **koso said:**
> It has its bug report, but it was closed, becase its it not bug .. problem is only that not all components of KDE were rebuild against new QT library, which is binary incopatible with previous version. It seem, that devs are waiting for new kde, which is out for a few days now and already available in kubuntu ppa (KDE 4.3.4) .. I hope that lucid will get 4.4.

Lucid is scheduled to have 4.4 IIRC.  If only because 4.4 is due to land in time for Lucid and Lucid is LTS and 4.4. is a kind of &#8216;maturing&#8217; effort. (E.g. implementing missing features and requests as well as bug fixing.)

> btw. I updated now, and now my desktop is crashing just after login .. so i dont get desktop and plasma .. anyone else with this problem?

I have this with an experimental 2.6.32-6 kernel but I get around it by disabling KMS at boot time. (Although I have updated quite a few bits and bobs since the last time I rebooted. Might have to check. Might not want to risk it though. :P)

---

### Post by caryb on 2009-12-04
I now have a different problem, mine crashes on startup with a plasma crash then kde-desktop error then black screen & mouse only. I can use alr + F2 to start apps this time though.


Cary

---

### Post by ronacc on 2009-12-04
mines flaky also since this AM's update , I can only open 1 app at a time , nothing else will start or even receive mouse clicks or mouseover and when I close it it minimises to the taskbar and sits there for several minutes before finally closing during which time the desktop is locked .
edit: also my password in the greeter for autologin has gained a letter so it fails and I have to login manualy .

---

### Post by tghe-retford on 2009-12-04
I find that KDE works fine now, aside from having to login manually. Kate, KBattleship and KPatience will not load, stating symbol lookup errors (known bug, may not get fixed until Beta 2!):
```
symbol lookup error: /usr/lib/libkateinterfaces.so.4: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
```

---

### Post by ranch hand on 2009-12-04
What the devil do you use instead of Kate?

When I have trouble with gedit I use screem.

---

### Post by ronacc on 2009-12-04
gedit works fine in kde , when you install it it will drag in the gnome libs it needs , or use Kwrite .

---

### Post by ranch hand on 2009-12-04
I do not like KDE  so I don't use it very often but I have used it and found Kate to work fine.  I have never used Kwrite.  I think I tried it in 9.04 Kubuntu and it wouldn't come up, I forget what the problem was.

I am just a Gnome kind of guy.  I allowed a bad upgrade on one of my 3 installs and it removed gedit (said it would).  I just grabbed screem because I have used it before.

I am not sure if it is a Gnome app or not.  Works pretty nice for a replacement for gedit and it will do formats that gedit won't.

---

### Post by ronacc on 2009-12-04
I used KDE for years and in some ways like it better than Gnome , when I started using Ubuntu as my main system I switched to Gnome because it was the Ubuntu default . KDE 4.4 is looking good enough it may lure me back .There are pleanty of good text editors floating around which you use is a mater of taste .

---

### Post by hikaricore on 2009-12-04
Funny enough kate still doesn't work and a recent update removed gedit as the proper libraries have not yet fallen into place. rofl
But this is half the fun of testing.  :)

---

### Post by ranch hand on 2009-12-04
I really do not like the KDE menu system, just does not fit me.  I do try to have one KDE OS on my loaner HDD so folks can see it.  I know that there are folks that love it.  They need to know it is there.

Lately I have been using Mandriva 2009-1 (I need to look at the new one).  I like it because it come on a DVD and you can install Gnome, KDE or Lxde.  Or you can install all of them and choose at login.  Seeing that I prefer Gnome, I can update in it or Lxde (my number 2, it is really nice) and have a nice KDE set as default for folks to try (and they can try Lxde too).

Then I need Ubuntu in a couple of versions.

If I use Kubuntu the first thing I do is install synaptic.  KDE package management, to me, just really sucks.

---

### Post by ronacc on 2009-12-04
affirmative on synaptic thats one of the first things I install too .But if you want a real thrill try an RPM based  KDE install , the term "dependency hell" was invented to describe RPM . and thats for repo apps , if you want to install something from a 3rd party site have a fresh bottle handy .
edit: BTW I spoke too soon about gedit , the last update took it out .

---

### Post by hikaricore on 2009-12-04
> **ronacc said:**
> BTW I spoke too soon about gedit , the last update took it out .

:lolflag:

---

### Post by xebian on 2009-12-04
> **ronacc said:**
> affirmative on synaptic thats one of the first things I install too .But if you want a real thrill try an RPM based  KDE install , the term "dependency hell" was invented to describe RPM . and thats for repo apps , if you want to install something from a 3rd party site have a fresh bottle handy .
edit: BTW I spoke too soon about gedit , the last update took it out .

Just tried Fedora and after a few hours with yum was  able to get fc13 rawhide and KDE 4.3.75. Not perfect but not as flexible as apt especially with conflicts after the transaction test.  I wish Kubuntu has something like rawhide/factory.

---

### Post by ronacc on 2009-12-04
if you have kubuntu 10.04 you are running kubuntu's equivalent of rawhide , rawhide is the testing version for their next release .if you want to get a little closer to the "cutting edge" add some PPA's .

---

### Post by ranch hand on 2009-12-04
I did mention that I use Mandriva.  It is a RPM based OS.  The only one I can stand.  Updates are SO much fun.

Installing stuff more so.  Their package manager does take care of dependencies for stuff in the repos.

Of coarse, unless you pay for it, you can't get the "restricted repos".  This is when you need to go to "easy urpmi" (a website) and get hooked up with the PLF (Penguin Liberation Front).  That is great but it is tough for a noob to find out about it.  On the other hand you can be a member of the PLF.

You just have to keep in mind the ease of getting hooked up to dial up, unlike Ubuntu, it takes answering 4 questions during installation and you are connected.

RPMs are even more fun on dial up.

---

### Post by slakkie on 2009-12-05
I just updated today, and well.. KDE starts up, but nothing is happening.

I also noticed KDE is a lot slower (starting up) then KDE on Debian.

---

### Post by hikaricore on 2009-12-05
Still fine here I just rebooted this morning.
There haven't been any signifigant changes to kde in the last day or so, not sure what your trouble is.

---

### Post by slakkie on 2009-12-06
I need to boot up Ubuntu for a sec to start troubleshooting it. I didn't bother yesterday, since I wanted some work done. So I booted Debian.

My problems just got bigger: [http://ubuntuforums.org/showthread.php?t=1347444](http://ubuntuforums.org/showthread.php?t=1347444)

---

### Post by caryb on 2009-12-07
It's easy to see that Kubuntu is the poor cousin when it takes days to fix problems, It's very hard to test when you spend so much time with a borked machine.


Cary

---

### Post by tghe-retford on 2009-12-07
And just to add to the fun, I now see that KDE 4.4 Beta 1 packages (a.k.a. 4.3.80) are starting to come through on the updates. Here's hoping it won't be too painful like the introduction of KDE 4.3 was once or twice during Karmic testing.

---

### Post by Bachstelze on 2009-12-07
> **caryb said:**
> It's easy to see that Kubuntu is the poor cousin when it takes days to fix problems, It's very hard to test when you spend so much time with a borked machine.

I had a broken KDE only for a few hours, now it is just a handful of KDE apps that are broken (Kopete and Kate here).

---

### Post by jbernardo on 2009-12-07
Right now I don't even have kdm, everything breaks with a unknown symbol in kdelibs5.

Anyone saw that blue haired kid anywhere?

---

### Post by tghe-retford on 2009-12-07
> **jbernardo said:**
> Right now I don't even have kdm, everything breaks with a unknown symbol in kdelibs5.
Yep. Many packages which are needed for KDE 4.4 Beta 1 still haven't made it to the servers and mirrors yet. Hence a lot of breakage. There are also X updates tonight as well, so double the danger that an update at the wrong time could break both and drop you to a command line.

I'm always intrigued by these major updates and have contingency in place - Openbox + FBPanel - worked well when KDE borked not so long ago. If you are mad like me, keep updating away. If you would like a working system for now, wait until the updates calm down.

---

### Post by hikaricore on 2009-12-07
Worst dist-upgrade ever? :

```

The following packages will be REMOVED:
  kubuntu-desktop xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-amd
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
The following packages have been kept back:
  ark dragonplayer gwenview kamera kcalc kde-window-manager kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins
  kdegraphics-strigi-plugins kdemultimedia-kio-plugins kdepim-runtime kdeplasma-addons kdm kgpg klipper kmag kmix kmousetool ksnapshot ksysguard ktux
  kwalletmanager kweather libkcddb4 liblancelot0 okular okular-extra-backends plasma-dataengines-addons plasma-dataengines-workspace
  plasma-runners-addons plasma-scriptengine-qedje plasma-scriptengine-superkaramba plasma-scriptengine-webkit plasma-scriptengines
  plasma-wallpapers-addons plasma-widget-lancelot plasma-widgets-addons plasma-widgets-workspace systemsettings
0 upgraded, 0 newly installed, 46 to remove and 40 not upgraded.
After this operation, 16.0MB disk space will be freed.
Do you want to continue [Y/n]?

```

It wants to remove most of xorg and not install anything. ROFL!
I'll be waiting a few days again.

---

### Post by ronacc on 2009-12-07
yeah it sure looks like a good time to sit on your hands .Hopefully they will have it straightened out by A1 .

---

### Post by ruik on 2009-12-08
The Kubuntu devs are working hard to get things fixed. :)

---

### Post by DanaG on 2009-12-08
Hmm, I've gotten some of KDE 4.4 beta to install... but when I try to log in, I get kdostartupconfig4 looping on god-only-knows-what, and absolutely devouring my CPU.
Here's the output of GDB from when I forcibly feed it SIGSEGV (a reliable way to get a stacktrace):
```


[www.csc.calpoly.edu/~dgoyette/kde_gdb.log](www.csc.calpoly.edu/~dgoyette/kde_gdb.log)  (388 KB) (now with debugsyms)
3352  total lines (cat kde_gdb.log | wc -l),
1895 unique lines (cat kde_gdb.log | sed "s/^#[0-9]* //" | sort -u | wc -l)
                                      ^ removes #nnnnnn from output.


And here's a strace:
[www.csc.calpoly.edu/~dgoyette/kde_strace.log](www.csc.calpoly.edu/~dgoyette/kde_strace.log)
315352  total lines (cat kde_strace.log | wc -l),
 35992 unique lines (cat kde_strace.log | sort -u | wc -l).

```

---

### Post by Bachstelze on 2009-12-08
X segfaults here. :D

---

### Post by viikinki on 2009-12-08
> **Bachstelze said:**
> X segfaults here. :D

+1 Hopefully there is a fix soon available :)

---

### Post by Bachstelze on 2009-12-08
> **viikinki said:**
> +1 Hopefully there is a fix soon available :)

It's fixed. KDM is still not working, but at least I can run Fluxbox. :p

---

### Post by slakkie on 2009-12-08
I could not even install packages anymore due to a dependency hell with KDE packages..

---

### Post by Reiger on 2009-12-08
It's just one package, actually:
> Preconfiguring packages ...                                                                                                                                                     
(Reading database ... 209161 files and directories currently installed.)                                                                                                        
Preparing to replace kdelibs5 4:4.3.3-0ubuntu4 (using .../kdelibs5_4%3a4.3.80-0ubuntu1_i386.deb) ...                                                                            
Unpacking replacement kdelibs5 ...                                                                                                                                              
dpkg: error processing /var/cache/apt/archives/kdelibs5_4%3a4.3.80-0ubuntu1_i386.deb (--unpack):                                                                                
 trying to overwrite '/usr/lib/libnepomukquery.so.4', which is also in package libnepomukquery4 4:4.3.3-0ubuntu3                                                                
Errors were encountered while processing:                                                                                                                                       
 /var/cache/apt/archives/kdelibs5_4%3a4.3.80-0ubuntu1_i386.deb                                                                                                                  
E: Sub-process /usr/bin/dpkg returned an error code (1) 

And the rest has a dependency chain right to that new kdelibs5 package so nothing gets installed/upgraded etc. etc. which puts off dpkg. :P

---

### Post by Reiger on 2009-12-08
Fixed it with:
```

sudo dpkg --force- --purge libnepomukqueryclient4
sudo dpkg --force- --purge libnepomukquery4
sudo aptitude -f install

```

---

### Post by Bachstelze on 2009-12-08
> **Reiger said:**
> Fixed it with:
```

sudo dpkg --force- --purge libnepomukqueryclient4
sudo dpkg --force- --purge libnepomukquery4
sudo aptitude -f install

```

Vou could also just remove them with [font=monospace]dpkg -r[/font].

---

### Post by Seren on 2009-12-08
From the Launchpad bug report,

[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/494027](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/494027)

[quote="Jonathan Thomas"]
As a workaround you can remove /usr/share/locale/currency/yourlocale.desktop where yourlocale is your locale
[/quote]

I don't know if it works or not. :)

---

### Post by viikinki on 2009-12-08
> **Seren said:**
> From the Launchpad bug report,

[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/494027](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/494027)



I don't know if it works or not. :)

After removing /usr/share/locale/currency/usd.desktop (my currency locale) I was able to log in. :)

I still have some problems. My plasma-desktop won't start but I am able to start applications by using alt+F2. I have not had time to check the reason behind it.

---

### Post by Yofel on 2009-12-08
For those that have no plasma-desktop after upgrade: check if you have the 'plasma-desktop' package installed. It has it's own package now and the dependency was forgotten.

---

### Post by Yes_It's_Me on 2009-12-08
Awesome, that fix does the trick! Thanks man.

---

### Post by hikaricore on 2009-12-08
With today's updates Kate finally runs again but complains about kiofile.
Thanks for the plasma-desktop fix btw.  ^_^

---

### Post by caryb on 2009-12-09
Well I'm back from openbox to KDE, no wireless applet & graphics are a bit ugly but it works:D


Cary

---

### Post by hikaricore on 2009-12-09
Facebook applet doesn't work but everything else seems to be fine.  ^_^

---

