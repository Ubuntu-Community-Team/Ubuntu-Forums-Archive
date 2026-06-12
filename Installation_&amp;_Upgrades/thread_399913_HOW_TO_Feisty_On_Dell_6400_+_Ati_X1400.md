---
title: "HOW TO: Feisty On Dell 6400 + Ati X1400"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by lifeempowered.com on 2007-04-02
[COLOR="DarkRed"][B]***IMPORTANT NOTE: This Script is Not Necessarily Up To Date.  I've Decided To Stop Updating This Thread and Focus All My Updates On My Blog.  Please Find My Blog at [http://www.mylittleubuntuguide.com ]("http://www.mylittleubuntuguide.com") Thanks.

ABOUT THIS HOW TO:
Following are two sections.  The first is to be used to install a complete system onto your Dell Inspiron 6400 with ATI graphics.  The second section lists individual scripts you can use to install parts, such as ATI, or just wifi, etc.  At the end of this post is information about the script and what it installs.[/B][/COLOR]

Please note my system hardware:
**Dell Inspiron 6400**
ATI X1400 128 MB (not shared) - [COLOR="Lime"]Works[/COLOR]
BCM4311 (Dell 1390) WiFi - [COLOR="Lime"]Works[/COLOR]
BCM4401 LAN - [COLOR="Lime"]Works[/COLOR]
160 GB HD - [COLOR="Lime"]Works[/COLOR]
DVD Writer - [COLOR="Lime"]Works[/COLOR]
2 GB RAM - [COLOR="Lime"]Works[/COLOR]
15.4" LCD w/ 1280x800 Res. - [COLOR="Lime"]Works[/COLOR]
Firewire - [COLOR="Lime"]Works[/COLOR]
Intel 82801G High Def. Audio - [COLOR="Lime"]Works[/COLOR]
Synaptic Touchpad - [COLOR="Lime"]Works[/COLOR]
56K Modem - [COLOR="Gray"]Not Tested[/COLOR]
Ricoh MultiCard Reader - [COLOR="Red"]SD Card Works, Sony Memory Stick Doesn't[/COLOR]


[SIZE="5"]**[COLOR="Red"]INSTALLING FEISTY ON 6400 WITH SCRIPT - FULL INSTALL[/COLOR]**[/SIZE]

[U][B]
INITIAL INSTALL & PREP[/B][/U]

**1.  Download the Ubuntu Desktop Live CD from Here: [Download ISO Here]("http://www.ubuntu.com/getubuntu/download").  Burn the ISO to CD and boot.**

**2.  After booting into the CD X won't start.  Hit Enter to say OK to the error messages and get back to the black screen.  You may need to switch to ALT-F4 to get an "ubuntu" user.  Do the following, one at a time, to get X working:**
```

wget http://www.mylittleubuntuguide.com/files/ati
chmod +x ati
./ati

```

You'll see X start and you are now running the Live CD in your native resolution!

**3. Double click the Install icon and configure your install how you like it.**

**4. After your system finishes installing it will prompt you before rebooting, ensure you have a network cable connected, and when it boots into the new system you'll see an error about X.  Use your arrows to select NO, hit ENTER and then OK to get to the black login screen.  You'll see an error regarding BCM43xx appearing, ignore it and type as if it wasn't there.  The command line can't "read" that error so don't try to backspace over it, etc.  Login using your username and password.**

**5. Download the script:**
```

wget http://www.mylittleubuntuguide.com/files/dellinstall

```

**6. Make it executable and run it:**
```

sudo chmod +x dellinstall
./dellinstall  # NOTICE Do NOT Run As Sudo

```

Sit back and relax for a moment until you hear your system BEEP at reboots.

**7. After the system reboots X still won't start, login to the black login screen (X still errors out) and run the 2nd script:**
```

sudo ./dellinstall2

```
*_During this second script, near the beginning, you'll be prompted to accept the license agreements of several applications.  You'll also be prompted to enter a serial key for VMWare Server.  Get one for free at [www.vmware.com](www.vmware.com).  After the prompt for VMWare, the install will complete without your input and will reboot the system._*

Get a cup of coffee, relax, watch some TV...When it's finished the system will BEEP, reboot, and you can now use it!

[COLOR="SeaGreen"]***Some additional notes:***[/COLOR]
1. Your system will reboot automatically and after it comes up you'll have X.  To login to Beryl, before you login select the GNOME with XGL session from the Options>Sessions menu in the bottom left corner.  
2. To see your system temp, right click the top panel and select "Add to Panel", choose the "Hardware Sensors Monitor" and click Add.


[SIZE="5"]**[COLOR="Red"]INDIVIDUAL SCRIPTS[/COLOR]**[/SIZE]
[SIZE="4"]**[COLOR="Blue"]INSTRUCTIONS: If You've Already Installed Using the Full Install Above, You Do NOT Need to Run ANY of the Following.  The following scripts are setup in such a way that they can be run independantly from each other, however, certain scripts must be run before others...take note of the dependancies on each.[/COLOR]**[/SIZE]

[COLOR="Red"]_**INITIAL INSTALL & PREP**_[/COLOR]

**1.  Download the Ubuntu Desktop Live CD from Here: [Download ISO Here]("http://www.ubuntu.com/getubuntu/download").  Burn the ISO to CD and boot.**

**2.  After booting into the CD X won't start.  Hit Enter to say OK to the error messages and get back to the black screen.  You may need to switch to ALT-F4 to get an "ubuntu" user.  Do the following, one at a time, to get X working:**
```

wget http://www.mylittleubuntuguide.com/files/ati
chmod +x ati
./ati

```

You'll see X start and you are now running the Live CD in your native resolution!

**3. Double click the Install icon and configure your install how you like it.**

**4. After your system finishes installing it will prompt you before rebooting, ensure you have a network cable connected, and when it boots into the new system you'll see an error about X.  Use your arrows to select NO, hit ENTER and then OK to get to the black login screen.  You'll see an error regarding BCM43xx appearing, ignore it and type as if it wasn't there.  The command line can't "read" that error so don't try to backspace over it, etc.  Login using your username and password.**
[COLOR="Red"]
_**SCRIPT 1 - UPDATE SYSTEM (No Dependancies)**_[/COLOR]

**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/update
sudo chmod +x update
sudo ./update

```
[COLOR="Red"]
_**SCRIPT 2 - INSTALL BUILD TOOLS (OPTIONAL)(Install Script 1 Prior to This)**_[/COLOR]
This script installs all the tools necessary to build stuff in the future.  So if you wanted to build an application from it's source, you'd need these installed first.
**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/build
sudo chmod +x build
sudo ./build

```

[COLOR="Red"]_**SCRIPT 3 - INSTALL VIDEO DRIVERS (Install Script 1 Prior to This)**_[/COLOR]

**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/video
sudo chmod +x video
sudo ./video

```
[COLOR="Red"]
_**SCRIPT 4 - INSTALL BERYL + XGL (Install Scripts 1 & 3 Prior to This)**_[/COLOR]

**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/beryl
sudo chmod +x beryl
sudo ./beryl

```

[COLOR="Red"]_**SCRIPT 5 - INSTALL HARDWARE MONITORING (No Dependancies - However Make Sure Sources.list is Open or Run Script 1 Prior)**_[/COLOR]

**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/hwmonitor
sudo chmod +x hwmonitor
sudo ./hwmonitor

```

[COLOR="Red"]_**SCRIPT 6 - INSTALL AUTOMATIX2 (No Dependancies...Recommend Script 1 Prior)**_[/COLOR]
This is a great utility which allows you to easily and effortlessly install all sorts of nice applications, drivers, codecs, and more using a gui.
**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/automatix
sudo chmod +x automatix
sudo ./automatix

```

[COLOR="Red"]_**SCRIPT 7 - INSTALL WIRELESS (No Dependancies - However Make Sure Sources.list is Open or Run Script 1 Prior)**_[/COLOR]

**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/wifi
sudo chmod +x wifi
sudo ./wifi

```

[COLOR="Red"]_**SCRIPT 8 - Extras (No Dependancies - However Make Sure Sources.list is Open or Run Script 1 Prior)**_[/COLOR]
In the Extras Script is DeVeDe (a DVD authoring app), scanbuttond (a necessity if you have a Canon scanner), gstm (a proxy tunneling app), and Kompozer (a nice HTML editor/web page developer)
**Download and run the script.  Open a terminal and do each of the following commands.**
```

wget http://www.mylittleubuntuguide.com/files/extras
sudo chmod +x extras
sudo ./extras

```

**[COLOR="Red"]Information About This Script[/COLOR]**

**What This Script Does:**
1. Configures a New System
2. Blacklists Necessary Modules
3. Installs Drivers
4. Installs Applications

**What This Script Installs:**
1. System/Kernel Update with Reboot
2. Build/Compilation Tools
3. FGLRX Driver for ATI
4. XGL for Use With Beryl
5. Beryl by Trevino (0.3) w/ Unsupported Plugins, Video Capture Plugin, Seom, and Avant Window Manager
6. i8k Utils, GKRellm, and Sensors Applet for Hardware Monitoring (gkrellm is optional&#8230;for controlling the temp thresholds and fans yourself)
7. Automatix2 (A Super App By [www.GetAutomatix.com](www.GetAutomatix.com) That Allows You To Easily Install and Remove Cool Applications and Drivers)
8. Kompozer Web Editing Software, formerly NVu
9. DeVeDe DVD Authoring Software
10. gSTM Proxy Tunneling Software
11. Scanbutton Deamon (for use with Canon scanners)
12. Wireless Driver Using ndiswrapper for Dell 1390 and/or Broadcom 43xx (Any Broadcom Wireless Driver Which Uses the bcmwl5.sys / bcmwl5.inf Driver File)
13. JAVA Plugins and Software
14. Skype Chat Software
15. VMWare Server (You&#8217;ll Need a Serial, Get One for Free at [www.vmware.com](www.vmware.com))
16. Multimedia Codecs
17. Kino Video Editing Software
18. F-Spot Photo Organization Software (Similar to Picasa)
19. Extra Fonts
20. Compression Tools (For Creating Tarballs and Zip files)
21. Adobe Acrobat Reader + Firefox Plugin
22. Gnome Baker CD/DVD Burning Software
23. gFTP FTP Client Software
24. GNU Cash Money Management Software
25. Liferea RSS Reader
26. Firestarter Firewall
27. ClamAV Antivirus Software
28. Audacity Audio Editing Software
29. DVD Ripping Software
30. Mplayer + Firefox Plugin
31. Totem Xine Video Player
32. VLC Media Player
33. Beep Media Player
34. Realmedia Player
35. Opera Web Browser
36. Avidemux Video Editing Software
37. Bittornado Bittorent Software
38. Bluefish Web Editing Software
39. Scribus Graphics/Publication Software
40. Picasa by Google
41. Wine (For Running Windows Apps)
42. Nautilus Scripts (For Opening Nautilus as Root, etc.)
43. Openoffice.org Clipart
44. Backup & Restore
45. GAIM Chat
46. Flash Plugin for Firefox
47. Gmail Checker
48. Thunderbird 2.0
49. RecordmyDesktop (Record Video From Desktop)
50. Google Desktop (Indexing of All Your Files for Fast Searching)

---

### Post by adzdavies on 2007-04-08
I also have a dell 6400 with an ATI x1400 card.
It Worked!  Cool!

I've done most of this before with edgy, but the beryl specific parts helped me out :)

Two points:
1) For my dell, wireless worked out of the box.  It's an:
"Intel Pro/Wireless 3945". 


2) Beryl!

I see that after re-enabling universe repositories, there's an upgrade of beryl:
"0.2.0~0beryl1 to 0.2.1-0ubuntu2"

Well, I had beryl working some time ago on edgy, then it mysteriously stopped working.... I'm guessing this is why you recommend NOT upgrading to the one in the ubuntu repository.

Can you shed any more light on why?  I'd like to jump back on the ubuntu version at some point, but need to know what kills it. 

One more question:
Is there a way to 'peg' it at 0.2 so it won't keep showing up as an update, or to somehow blacklist it from the repository?

Thanks in advance!!!!

---

### Post by bwhite82 on 2007-04-14
This is the first ATI/Beryl guide that I have ever followed that worked, first time and without a hitch. (It helps that it is specific to my computer, E1505) THANK YOU very much!

---

### Post by tehmatticus on 2007-04-15
adzdavies,

The beryl in the universe repos does not include beryl-xgl, so if you're using the proprietary ATI drivers, it wont work.  Hopefully they'll fix this soon, as there's a pretty lengthy bug on the issue.

---

### Post by allforcarrie on 2007-04-15
my 9800 pro works now but beryl is still not starting.

---

### Post by xbisont on 2007-04-16
> One more question:
Is there a way to 'peg' it at 0.2 so it won't keep showing up as an update, or to somehow blacklist it from the repository?

Thanks in advance!!!!

First as a little background, i have Beryl working with Feisty Fawn + XGL on a laptop with an ATI Radeon 200m, i did it just by following just this HOW TO and everything is just ok, thanks a lot

I just found out how avoid the beryl related updates when we reenbled universe repository, i got the idea from a "[apt-build, HowTo]("http://julien.danjou.info/article-apt-build.html")" and the idea to use the version as the Pin is from [another ubuntu forum](http://www.ubuntu-es.org/index.php?q=node/2109#comment-32625). The idea is to set a Pin-Priority for each package installed by beryl

all you need to do is edit or create the file /etc/apt/preferences
use your favorite text editor, i used vi, but you can use nano, gedit, emacs,...
```
sudo vi /etc/apt/preferences
``` 
and add this lines
```

Package: beryl
Pin: version 0.2.0*
Pin-Priority: 990

Package: beryl-core
Pin: version 0.2.0*
Pin-Priority: 990

Package: beryl-manager
Pin: version 0.2.0*
Pin-Priority: 990

Package: beryl-plugins
Pin: version 0.2.0*
Pin-Priority: 990

Package: beryl-plugins-data
Pin: version 0.2.0*
Pin-Priority: 990

Package: beryl-settings
Pin: version 0.2.0*
Pin-Priority: 990

Package: beryl-settings-bindings
Pin: version 0.2.0*
Pin-Priority: 990

Package: libberyldecoration0
Pin: version 0.2.0*
Pin-Priority: 990

Package: libberylsettings0
Pin: version 0.2.0*
Pin-Priority: 990

Package: emerald
Pin: version 0.2.0*
Pin-Priority: 990

Package: emerald-themes
Pin: version 0.2.0*
Pin-Priority: 990

Package: libemeraldengine0
Pin: version 0.2.0*
Pin-Priority: 990

```
so when you have universe repository enabled and perform a apt-get update, there are no more Beryl updates

```
usuario@laptop:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
```

i thing it would be nice to include the Pin-Priority idea as part of the HowTo so people don't need to scroll all the thread in order to find it, but it's just a suggestion

---

### Post by Bjwebb on 2007-04-17
Will the Beryl how to work for any computer with a Raedon graphics card. Specifically, will it work for a Dell Dimension 5150C with a Raedon X600 or a Packardbell with a Radeon 9550 (two computers that I want to get beryl running on).

Thanks in advance.
Ben Webb

---

### Post by Gadren on 2007-04-17
Thanks so much for this guide!  This is precisely what I needed as my Dell notebook came in today...
Everything works great (except I haven't tried the wireless; haven't gotten a chance yet.  We use DSL, and I had to rip out our DSL modem and connect it directly to my notebook...maybe I'll get a wireless router someday).

---

### Post by njbetzen on 2007-04-17
Alright, so I'm fairly certain that I followed the guide correctly, yet I still seem to be having a pretty strange problem.  I should start out by saying that I did not do the wireless install, because my wireless card is already detected and works, and I also didn't do the VMWare player, because I don't imagine that has anything to do with Beryl.

Here's my problem.  When I attempt to load Beryl and XGL on startup, I get a blue screen.  If I click ctrl+alt+right, I get back into the regular gnome world.  

After playing around with the blue screen, I realized that it actually is the cube.  I can make it spin and be pretty and exciting.  Unfortunately, I can't DO anything with it.  It is just a blue cube without any application bars or anything.

Any thoughts?

Edit:  
my specs are:
Ati x1400 mobility
dell e1505
1680x1050 screen

I've also noticed that when in XGL mode, videos that I watch turn blue.  Weird.

---

### Post by ibanezix on 2007-04-20
I am posting this here, because it's the thread that Dell Inspiron 6400 owners are more likely to see.

The testing releases of Feisty Fawn worked with ATI Radeon Cards X1300, X1400 and X1600 up to Herd4. These cards are common in many laptops from many companies, not just Dell. From Herd5 and onwards, due to a reason that I have yet to discover, normal installation will not result to a propely working X system. This has been issued as a bug since the release of Herd5, and even though a few workarounds or fixes have been proposed, none made it to the final release of Feisty, thus rendering it unusable for a great lot of people who will be discouraged by such a problem.

I strongly believe that this is a major problem, and as soon as a proper fix is found, there should be a 7.04.1 release to include it immediately. There is no excuse to asking beginner users to install from a command line, unless they willingly choose to do so.

Some references:
1. [The Launchpad entry for this problem]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853")
2. [A guide in the beginner's section]("http://ubuntuforums.org/showthread.php?t=414194")
3. [Binary driver how-to for ATI in the wiki, not specific to this problem]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
4. [The Dell Inspiron 6400 entry in the wiki, not yet updated with information on this problem]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron6400")

I will try to find some time in the weekend to update the wiki page, in the meantime please have your eyes open for related threads in the support forums, and direct them accordingly.

Thanks to the original poster for the guide.

---

### Post by garg on 2007-04-20
I got everything working according to these instructions. I have one problem though. When I change to workspace 2,3 or 4, all the windows start leaving trails which don't go away. This problem does not occur on workspace1 

So after a while workspace2,3,4 all have images of the windows. They go away if I try to move the cube around so I'm thinking it has something to do with the refreshing?

Thanks

---

### Post by Dexter. on 2007-04-20
I could use someones help with this.

When I login with The 'Gnome with XGL' Session, everythings black, white and orange and blurry beyond recognition. Still I can tell it's some kind of desktop. What could be wrong?

When I did 
sudo aticonfig --initial 
it said:
Found fglrx primary device section
Nothing to do, terminating.

Is that a problem? 

Thanks.

---

### Post by markdbd on 2007-04-20
Well I tried to install Feisty 2 times with the alternate CD but it breaks on 85%, I also checked the integrity of the CD.

Strange but I can't install feisty, normal CD doesn't work with ATI, alternate CD hangs for me at the 85% of the instalation.

---

### Post by Double-X on 2007-04-20
> **Dexter. said:**
> I could use someones help with this.

When I login with The 'Gnome with XGL' Session, everythings black, white and orange and blurry beyond recognition. Still I can tell it's some kind of desktop. What could be wrong?

When I did 
sudo aticonfig --initial 
it said:
Found fglrx primary device section
Nothing to do, terminating.

Is that a problem? 

Thanks.


I got a ATI Mobile X1600 and I got the same problem.
Can't get Beryl to work properly....
Someone got any idea's?

---

### Post by nickuzzy on 2007-04-20
Wow! ok so now everything loads and works great except for desktop effects and beryl both.   When I try to enable desktop effects an error comes up that says: Desktop Effects could not be enabled.   Beryl runs but there are no differences in any graphics... I had errors earlier today that would say a composite is not found or something but I was able to fix it by enabling it in my xorg.conf.

---

### Post by Dexter. on 2007-04-21
> **Double-X said:**
> I got a ATI Mobile X1600 and I got the same problem.
Can't get Beryl to work properly....
Someone got any idea's?

I that problem solved by running something called Envy, which downloads the drivers and configures X automatically.  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 
Same way the guy in the thread "Good Lord Ubuntu Sucks at getting 3D accel to work!".

Now I have another problem though. Even though fglrx is working, I have no direct rendering

$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6400 (8.35.5)

So beryl doesn't really work. When I log-on with the 'Gnome with XGL' session beryl isn't running. So I do 
$beryl 
And I there doesn't appear to be any effects except the titlebars disappear.

Does anyone have an idea to solve this problem?
Thanks.

---

### Post by lifeempowered.com on 2007-04-21
Ok, I'm wondering if the above issues are related to either:
1. Your ATI card being x1600
2. Your Feisty install being the "official" release?

I'm downloading the official CD now and will attempt a fresh install following my instructions.  As i run into differences I'll post them on the guide!  

Later.

---

### Post by lifeempowered.com on 2007-04-21
Something else curious:

After I install java using Automatix and install the TOS software (think or swim) it doesn't want to "paint" while running the Beryl window manager.  It works fine in Metacity of course.  I assume this happens with other Java programs, anyone?

---

### Post by pertti on 2007-04-21
> **lifeempowered.com said:**
> Something else curious:

After I install java using Automatix and install the TOS software (think or swim) it doesn't want to "paint" while running the Beryl window manager.  It works fine in Metacity of course.  I assume this happens with other Java programs, anyone?

Hmm, I installed Java 6 through Synaptic and Java apps work fine (at least Eclipse and MagicDraw UML).

On the other hand, MPlayer crashes when using Beryl and looks terrible with XGL and Metacity.  [Totem-gstreamer colors are still wrong]("http://ubuntuforums.org/showthread.php?t=202598") when using Xv. And 3D apps (glxgears and Frets on Fire) run choppy using XGL. glxinfo says there's no direct rendering:

```
$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
direct rendering: No
```

I'll try to find a solution for these. Great guide, though.

EDIT: 3D apps do work fine without XGL, with direct redering enabled.

---

### Post by Gustave on 2007-04-21
> **markdbd said:**
> Well I tried to install Feisty 2 times with the alternate CD but it breaks on 85%, I also checked the integrity of the CD.

Strange but I can't install feisty, normal CD doesn't work with ATI, alternate CD hangs for me at the 85% of the instalation.

I had the same problem with my install.  It 'broke' on an X11 file of some sort for me.  During the text install, I was asked to choose a resolution.  My second time through, the only one I chose, other the the default ones, was 1280x800 (native resolution for my laptop) and the install went through fine.

I have no idea if this will help ya at, all, but I thought I'd mention it.

---

### Post by Dexter. on 2007-04-21
I finally got it working. I don't really know what fixed it, I restarted the beryl-manager and beryl is now working.

I have a radeon mobility x1400 card, and I installed Feisty by upgrading from Edgy with Update Manager.

glxinfo still says that I have NO direct rendering. I don't really know what this means. Apparently it's not very important since beryl is running very smoothly.
glxgears is running with about 4000 fps, which is way better than with the mesa driver, so I'm pleased with that.

I think(not sure) what made it work for me, was to use Envy, and then install the specific version of beryl from this guide. 

Thanks for the help.

---

### Post by nickuzzy on 2007-04-21
This is the error I get when I try to enable Desktop Effects and it is similar to when I enable Beryl, Beryl just flashes around then goes back to the Metacity:

nicholas@nicholas-laptop:~$ desktop-effects
modinfo: could not open /lib/modules/2.6.20-15-generic/volatile/fglrx.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.20-15-generic/volatile/fglrx.ko: No such file or directory
nvidia hardware not available
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"


Anyone got any ideas how to fix this?  Not sure why it is saying nvidia hardware not available, but I am pretty new to Ubuntu.

---

### Post by zarmando on 2007-04-22
Hello there,
First post here.

I got Ubuntu Feisty Fawn running after a less  than friendly install.
And I didn't try to install Beryl as it seems to be more trouble than fun... I'm trying to stay a bit productive... :) 

Anyway, I'm wondering if you guys have a functionning **suspend to ram or hibernate mode**... My "suspend" doesn't resume : the screen is black and I have to power off. Which is a drag because it doesn't cleanly unmount my other partitions properly, to say the least -- I don't want to damage my Windows  partition before I make sure everything is okay with Ubuntu... So I won't even try the hibernation for now...

So, is it possible to have **a working suspend mode** ??? A laptop is not very useful if one has to "power off" / "power on" all the time. :confused: 

Thanks for any help

Z.

---

### Post by curtiscartmell on 2007-04-23
Hi,

I've got a Inspiron 6400 with X1400

I followed the guide - even using "cut & paste" and Beryl will not load on start up.  When I open the terminal and change to:

cd /usr/local/bin

I see 2 files:
start_beryl.sh
startxgl.sh

when I try to manually start beryl I get the error:
Error: beryl-manager not launched. Xgl not running?

so then I type "startxgl.sh" from terminal and my screen goes grey with checkers.  I can't see anything and the only thing I can do is hit the power button to log off and Gnome will reload fine, or  "Ctrl Alt right click" and to switch desktop spaces and see Gnome.

Any ideas?  When I click on "Applications" "System Tools" there is the "beryl manager" - when I click on that it will load but  when I right click and try to change the Window Manager to Beryl the screen flashes a few times and then automatically resets to "MetaCity".  I've try to remove that auto fall-back and nothing happens - Beryl will simply not load.

Thanks for your help!  The guide was great - but something doesn't see to work for some reason.  Screen display is 1280x800 - looks great on ATI X1400

thanks,
Curtis :confused:

---

### Post by Dexter. on 2007-04-23
> **curtiscartmell said:**
> Hi,

I've got a Inspiron 6400 with X1400

I followed the guide - even using "cut & paste" and Beryl will not load on start up.  When I open the terminal and change to:

cd /usr/local/bin

I see 2 files:
start_beryl.sh
startxgl.sh

when I try to manually start beryl I get the error:
Error: beryl-manager not launched. Xgl not running?

so then I type "startxgl.sh" from terminal and my screen goes grey with checkers.  I can't see anything and the only thing I can do is hit the power button to log off and Gnome will reload fine, or  "Ctrl Alt right click" and to switch desktop spaces and see Gnome.

Any ideas?  When I click on "Applications" "System Tools" there is the "beryl manager" - when I click on that it will load but  when I right click and try to change the Window Manager to Beryl the screen flashes a few times and then automatically resets to "MetaCity".  I've try to remove that auto fall-back and nothing happens - Beryl will simply not load.

Thanks for your help!  The guide was great - but something doesn't see to work for some reason.  Screen display is 1280x800 - looks great on ATI X1400

thanks,
Curtis :confused:

Do you log in with the 'Gnome with XGL' Session? What does it say when you do 
$ fglrxinfo

---

### Post by curtiscartmell on 2007-04-23
Dexter,

Oh man...  I forgot to login with XGL - that's what I get for installing at 3am...  Beryl works AWESOME!!!! 

Crazy that Ubuntu wouldn't set this as a default option... Beryl is unreal...  goodbye Windows!

Thanks everyone!
Curtis :)

---

### Post by markdbd on 2007-04-23
Well as I said in my last reply, I can't install Feisty using liveCD, I think the bug is well known but I can't install it with the alternate CD :(

My solution was to install Edgy, update all changes and then update to Feisty.

When Feisty booted the first time, my ATI failed but this guide helped me out, and all instructions worked perfectly :) 

Thanks for your great work lifeempowered, I subscribed to your blog :)

---

### Post by lifeempowered.com on 2007-04-23
> **markdbd said:**
> Well as I said in my last reply, I can't install Feisty using liveCD, I think the bug is well known but I can't install it with the alternate CD :(

My solution was to install Edgy, update all changes and then update to Feisty.

When Feisty booted the first time, my ATI failed but this guide helped me out, and all instructions worked perfectly :) 

Thanks for your great work lifeempowered, I subscribed to your blog :)

Are you using the latest CD?  If so this could be the problem...I'm going to do a fresh install later today and see how it goes.  I'll update my blog and this thread as needed.  

BTW: thanks for all the excellent feedback everyone!

---

### Post by rotk on 2007-04-23
Thanks John,
 
 I almost made it :)
 I was worried coz it didn't have gui in install, so i ended up upgrading from edgy. 
 Now I can have my Beryl back again. Wireless didn't show up though,I'll give it a try soon.

 Thanks again! 

 :KS

---

### Post by woody_sud on 2007-04-23
Man, I just had same problem but after 10 or 11 tries installation was completed...  I did this process twice couse firts time i tray to install propietary ati drivers and results in no 3d accell, later have to reinstall and again with problems at 85% some other time at 6% but with persistence u will made it. I expose same problem in others forums with no responses, seems we are the only users with this wier problem.

---

### Post by woody_sud on 2007-04-23
> **pertti said:**
> 

EDIT: 3D apps do work fine without XGL, with direct redering enabled.

Well, I have a Inspiron 9600 with Ati x1400 +XGL + Beryl and no problems with 3d app, actualy I'm playing Enemy Territory right now.

---

### Post by zarmando on 2007-04-23
Evrything worked here. Inspiron 6400, intel WIFI ( IPW3945 ), AtiX1400.

The only problem is the Intel Wifi with WPA encryption. There seems to be somekind of conflict with the  network manager applet.

 I posted my workaround somewhere else. Here's the essence of it :

**** THIS WORKAROUND ONLY WORKS IF YOUR CARD IS ALREADY DETECTED, IF YOU CAN DETECT NETWORKS, etc. BUT STILL CAN'T CONNECT****

-A-
1- "Right click" on the network manager Icon
2- Enable (check) the "enable Wireless"
3- Make sure the card is ON (fn+F2 on my keyboard, Inspiron 6400 laptop)

-B-
Left click on the Icon, choose your network - It should be detected

-C-
Then
1- Disable (uncheck) the "Enable networking" option
2- re-enable (recheck) networking.

It should then connect.
If it doesn't work, retry C, retry again. Make sure the proper network is selected

Strange workaround. But it's a workaround that works...!!! At least for me.

Z.

---

### Post by curtiscartmell on 2007-04-23
Just a thought,

For those having install problems with the ALT CD - all I did to get it working on install was to use text mode (as usual) and then when I got to the screen resolution page options... delete all options except 640x480 - when the install is over - Ubuntu will load your screen with 1024x768 scretched... but very workable until you follow the guide.

Curtis =)

---

### Post by zarmando on 2007-04-23
> **curtiscartmell said:**
> Just a thought,

For those having install problems with the ALT CD - all I did to get it working on install was to use text mode (as usual) and then when I got to the screen resolution page options... delete all options except 640x480 - when the install is over - Ubuntu will load your screen with 1024x768 scretched... but very workable until you follow the guide.

Curtis =)

Also, one could just **use the Live CD **if access to internet is possible (which should be, in most cases). Whe X crashes, just go back to the command line and write (one line at a time, then press "enter"):

```
sudo -s -H
apt-get update
apt-get upgrade
apt-get install xorg-driver-fglrx
sudo aticonfig --initial
startx
```


Then, just experience the LIVE CD... And go to the install proces with the install Icon in the menus, somewhere...

One thing I really hate with the Ubuntu Installation process is the unfriendliness of the Grub configuration. Every time I want to install Grub on the **Master Boot Record of the partition instead of the disk**, it's pretty stressful -- Grub doesn't use the SD1, sd2, etc. protocol, but some weird (hdx,x) one. Not that hard once you know, but such a pain when you don't want to mess with your hard drive and break your other installations.

---

### Post by shuqi on 2007-04-23
Thanks a lot for sharing this guide, lifeempowered.com !

I have been trying to get Beryl installed for literally weeks now and followed the instructions of several guides, but it never worked. Finally I can see Beryl in all its glory, thanks to your post :)

Only one question remains: what would one have to do to get it working under KDE as well?
I tried the setup instructions under kubuntu feisty as well, but Beryl won't start. I assume it's a problem with one of the custom startup scripts and I already modified it to start the correct window manager, but still no luck.

---

### Post by pertti on 2007-04-23
> **woody_sud said:**
> Well, I have a Inspiron 9600 with Ati x1400 +XGL + Beryl and no problems with 3d app, actualy I'm playing Enemy Territory right now.

Do you have direct rendering working with XGL? I don't and I see quite a huge difference between glxgears and Frets on Fire, with and without XGL. GL screensavers are also bit jerky. Or maybe it's not related to direct rendering and it's something else I'm missing.

Here are the relevant parts of my xorg.conf, in case you notice anything wrong:

```
Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Section "ServerFlags"
        Option          "AIGLX" "off"
EndSection
```

And here's the output of fglrxinfo:

```

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)
```

Thanks a lot.

---

### Post by lifeempowered.com on 2007-04-23
> **shuqi said:**
> Thanks a lot for sharing this guide, lifeempowered.com !

I have been trying to get Beryl installed for literally weeks now and followed the instructions of several guides, but it never worked. Finally I can see Beryl in all its glory, thanks to your post :)

Only one question remains: what would one have to do to get it working under KDE as well?
I tried the setup instructions under kubuntu feisty as well, but Beryl won't start. I assume it's a problem with one of the custom startup scripts and I already modified it to start the correct window manager, but still no luck.

Sorry, I'm not a KDE fan and have avoided it since 2005.  Maybe someone else here can help?...

> Just a thought,

For those having install problems with the ALT CD - all I did to get it working on install was to use text mode (as usual) and then when I got to the screen resolution page options... delete all options except 640x480 - when the install is over - Ubuntu will load your screen with 1024x768 scretched... but very workable until you follow the guide.

Curtis =)
Thanks!  I'll include this in the guide as it's a fairly simple addition.

> Also, one could just use the Live CD if access to internet is possible (which should be, in most cases). Whe X crashes, just go back to the command line and write (one line at a time, then press "enter"):

Thank you for the suggestion, I'm going with the other one simply because it makes more of a "clean" install process and because the Text install is WAY faster than waiting for the Live CD anyway!

Thank you everyone again!

---

### Post by zarmando on 2007-04-23
> Quote:
Also, one could just use the Live CD if access to internet is possible (which should be, in most cases). Whe X crashes, just go back to the command line and write (one line at a time, then press "enter"):  

Thank you for the suggestion, I'm going with the other one simply because it makes more of a "clean" install process and because the Text install is WAY faster than waiting for the Live CD anyway!

Thank you everyone again!

The reason I suggested that is because, sometimes, people only have the Live CD at hand and it's really not convenient for them to donwload another 700mb (poor connection, expensive internet connection, etc...)

Also : 

**1-  concerning the Wifi Problems** with the Intel (IPW3945) : would you consider adding a paragraph on the subject ? (see one of my previous my posts)

**** THIS WORKAROUND ONLY WORKS IF YOUR CARD IS ALREADY DETECTED, IF YOU CAN DETECT NETWORKS, etc. BUT STILL CAN'T CONNECT****


-A- **Make sure the card is ON ** (fn+F2 on my keyboard, Inspiron 6400 laptop)
1- "Right click" on the network manager Icon
2- Enable (check) the "enable Wireless"

-B-
Left click on the Icon, choose your network - It should be detected

-C-
Then
1- Disable (uncheck) the "Enable networking" option
2- re-enable (recheck) "Enable networking".

It should then connect.
If it doesn't work, retry C, retry again. Be patient. Make sure the proper network is selected

Strange workaround. But it's a workaround that works...!!! At least for me.

2- **Horizontal scroll for the touchpad ** :

```
sudo gedit /etc/X11/xorg.conf
```

Then modify "Section "InputDevice""

```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "1"
	Option      "SHMConfig" "on"
EndSection
```


After that : ctrl+Alt+backspace to restart X.


3- **Suspend to RAM **: same thing : it'S easy to get it to work editing acpi-support (/etc/default/):

```
sudo gedit /etc/default/acpi-support
```

then replace you acpi support file (after backing it up) with :

```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="fglrx"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

```

Et voilà.

Thank you.

---

### Post by shuqi on 2007-04-23
> **lifeempowered.com said:**
> Sorry, I'm not a KDE fan and have avoided it since 2005.  Maybe someone else here can help?...

I figured it out for KDE. It seems a little bit less stable than under gnome, but I finally got it running.
Simply replace the last line of the startxgl.sh script from
```
exec dbus-launch --exit-with-session gnome-session
```
to
```
startkde
```

Beryl may fail at first, but try executing 'beryl-manager' after the KDE login with the new session and it should work - at least that's how it worked out in my case :)

Thanks again for this excellent step-by-step guide!

---

### Post by Evdawg on 2007-04-23
Anyone know anything about controlling fans on this laptop? The right side is getting really hot whereas the left side is fine, I just want to make sure the fans are working OK,

---

### Post by pertti on 2007-04-24
> **Evdawg said:**
> Anyone know anything about controlling fans on this laptop? The right side is getting really hot whereas the left side is fine, I just want to make sure the fans are working OK,

I found [this post]("http://www.markdbd.com/2007/04/23/controlando-la-temperatura-de-un-portatil-dell-en-ubuntu-mediante-i8kutils/") on markdbd's (from page 3 on this thread) blog, but's in spanish ([link to Google's translated version]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F23%2Fcontrolando-la-temperatura-de-un-portatil-dell-en-ubuntu-mediante-i8kutils%2F&langpair=es%7Cen&hl=es&safe=off&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools")). I haven't tried it yet, but if you have any problems reading the translation I can help you out.

---

### Post by jonnymccullagh on 2007-04-24
Zarmando,
> Also, one could just use the Live CD if access to internet is possible (which should be, in most cases). Whe X crashes, just go back to the command line
When X crashes on the Live CD I just get a flashing cursor - no command prompt. Am I doing something wrong? How can I get the command prompt?
Thanks in advance,
jonny

---

### Post by markdbd on 2007-04-24
> **lifeempowered.com said:**
> Are you using the latest CD?  If so this could be the problem...I'm going to do a fresh install later today and see how it goes.  I'll update my blog and this thread as needed.  

BTW: thanks for all the excellent feedback everyone!
I burned the CD 2 times, and both times I check the Alternate CD and it was ok, I also burn it at 4x but the installation stops always at 85% :(

---

### Post by pertti on 2007-04-24
> **jonnymccullagh said:**
> Zarmando,

When X crashes on the Live CD I just get a flashing cursor - no command prompt. Am I doing something wrong? How can I get the command prompt?

Try Ctrl+Alt+F6 (or any function key from F1 to F6) and see if it works.

---

### Post by markdbd on 2007-04-24
> **Evdawg said:**
> Anyone know anything about controlling fans on this laptop? The right side is getting really hot whereas the left side is fine, I just want to make sure the fans are working OK,

Just follow this instructions:
1. Install this package, sudo apt-get install i8kutils
2. Run, sudo modprobe i8k force=1
3. Edit the file /etc/modules, sudo gedit /etc/modules
4. add this line at the end of the file, i8k force=1

To see the temperature just use:
i8kctl temp

To run a fan:
i8kfan -r 2

r = right fan, l=left fan, I get only to work the right fan. Speed goes from 0 = stopped, 1 = normal speed, 2 = high speed

To check the fan status:
i8kctl fan

pertti Thanks for the link :)

---

### Post by jonnymccullagh on 2007-04-24
thanks pertti,
I will give this a try when I get home this evening.
cheers,
j

---

### Post by Diversion on 2007-04-24
At first I want to thank you for giving this guide.
I am a complete linux/unix newbie and now trying to follow your guide step by step.
I need to install a linux/unix client for my school projects, so I decided to use the Feasty Fawn version.
Only thing I didn't know where all the problems with Ati video cards( I got an X1600 mobile).

Now for my problem:

I installed the alternate cd version following the steps until step 4. When I restarted and it's booting up. I get the "failed to start the X server message" again with the "no screens found" fatal error. when I'm then led back to the command line mode and try to advance by blacklisting the 2 modules I just can't.

I am wondering if anyone would be willing to help me with this.
It should be quite easy, but me being a complete noob using linux, I just can't find the sollution.

Thanks in advance,

Colin

---

### Post by Wintaru on 2007-04-24
Thanks for the great guide!  Unfortunately I'm having an issue.  When I log in Beryl doesn't start.  So I try running beryl-manager and the emerald appears but the windows don't change.  When I run Beryl --replace I loose the bars at the top and bottom and this is what is displayed in the terminal:

```

Detected xserver :XGL

Checking Display :1.0 ...

Checking for XComposite extension  : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to managed screen: 0
beryl: No manageable screens found on display :1.0

```

I've triple checked the guide and it seems I've done everything I should.  My machine is a Dell E1505 with the Ati Mobility X1400 card like the Author has.  Any help would be very much appreciated.

---

### Post by phinn on 2007-04-24
This is a wonderful guide for Beryl.  It now works perfectly on my Thinkpad T60 with the X1400 128mb video card

---

### Post by SomeoneYouKnow on 2007-04-24
Thanks a lot for your guide... I've just tried it with my Dell Inspiron 6400 and an ATI Mobility Radeon **X1300 **and am glad to say: the exact same way worked also fine with my X1300.

---

### Post by garion on 2007-04-24
I am really disappointed... what's going on there?  The beta live cd boots up perfectly and runs on my Dell 6400 + ATI x1300 with 1400x1050 resolution, installed well too.  And the final release live cd just won't boot correctly at all... suspend also got broken, tried a million things with no luck, and it used to work well with beta out-of-box.

Is it really that big a rush to push the release out of the door and have a bunch of things hanging out there broken? :confused:

---

### Post by SomeCallMeTim on 2007-04-25
Phinn what did you do to get beryl finally working? Are you using XGL ?

I've got a n IBM R60 with an ATI 1400 Mobility and I've already installed the 8.36.5 drivers using

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

(method 1)

If you are using XGL + Beryl is the speed of 3D apps OK ?

Tim

---

### Post by lifeempowered.com on 2007-04-25
> **Wintaru said:**
> Thanks for the great guide!  Unfortunately I'm having an issue.  When I log in Beryl doesn't start.  So I try running beryl-manager and the emerald appears but the windows don't change.  When I run Beryl --replace I loose the bars at the top and bottom and this is what is displayed in the terminal:

```

Detected xserver :XGL

Checking Display :1.0 ...

Checking for XComposite extension  : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to managed screen: 0
beryl: No manageable screens found on display :1.0

```

I've triple checked the guide and it seems I've done everything I should.  My machine is a Dell E1505 with the Ati Mobility X1400 card like the Author has.  Any help would be very much appreciated.

Ok, are you selecting the XGL session before logging in?  This is the first troubleshooting step.  Let me know.

---

### Post by lifeempowered.com on 2007-04-25
> **SomeCallMeTim said:**
> Phinn what did you do to get beryl finally working? Are you using XGL ?

I've got a n IBM R60 with an ATI 1400 Mobility and I've already installed the 8.36.5 drivers using

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

(method 1)

If you are using XGL + Beryl is the speed of 3D apps OK ?

Tim

Try using my video section for installing... Also, while Beryl is running most OpenGL apps won't run...you'll need to start a normal Gnome session for that.  However, some will run if you simply change the window manager to Metacity by right clicking the Beryl icon and selecting that option.

---

### Post by lifeempowered.com on 2007-04-25
Does anyone have the knowledge to assist me with putting much of this guide into a script?  I would like to automate as much of it as I can.

---

### Post by mulino18 on 2007-04-25
Hi all...

I upgraded from Edgy and ran into the X server not starting problem.
I tried the solution proposed in many different places namely :

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
and editing xorg.conf...
still on startx I got X version mismatch -detected X.org 7.2.0.0 required 7.1.0
what do I miss?

thanks for your help!

---

### Post by lifeempowered.com on 2007-04-25
> **pertti said:**
> I found [this post]("http://www.markdbd.com/2007/04/23/controlando-la-temperatura-de-un-portatil-dell-en-ubuntu-mediante-i8kutils/") on markdbd's (from page 3 on this thread) blog, but's in spanish ([link to Google's translated version]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F23%2Fcontrolando-la-temperatura-de-un-portatil-dell-en-ubuntu-mediante-i8kutils%2F&langpair=es%7Cen&hl=es&safe=off&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools")). I haven't tried it yet, but if you have any problems reading the translation I can help you out.

I included my old fan guide from my edgy how to in the guide.  Check it out, you can control fan speeds using the GUI.

---

### Post by lifeempowered.com on 2007-04-25
> **mulino18 said:**
> Hi all...

I upgraded from Edgy and ran into the X server not starting problem.
I tried the solution proposed in many different places namely :

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
and editing xorg.conf...
still on startx I got X version mismatch -detected X.org 7.2.0.0 required 7.1.0
what do I miss?

thanks for your help!

I'm not sure exactly, but it sounds like it still is installing version 7.1.0.  Try clearing your apt of all downloaded files.  I think the command is ```
sudo apt-get autoclean
``` and then do ```
sudo apt-get clean
```...Then try doing the first command to install fglrx again.

---

### Post by mulino18 on 2007-04-25
> **lifeempowered.com said:**
> I'm not sure exactly, but it sounds like it still is installing version 7.1.0.  Try clearing your apt of all downloaded files.  I think the command is ```
sudo apt-get autoclean
``` and then do ```
sudo apt-get clean
```...Then try doing the first command to install fglrx again.

... Nope... error still the same... :O(

---

### Post by markdbd on 2007-04-25
> **lifeempowered.com said:**
> I included my old fan guide from my edgy how to in the guide.  Check it out, you can control fan speeds using the GUI.

Have you tried sensors-applet, I think it's much cleaner than gkrellm and it detects i8kutils automatically. In the following link I wrote a guide in spanish to configure it:

Translated with Google

[http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F25%2Fsensors-applet-monitorizando-y-controlando-la-temperatura-en-ubuntu%2F&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F25%2Fsensors-applet-monitorizando-y-controlando-la-temperatura-en-ubuntu%2F&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

---

### Post by Wintaru on 2007-04-25
> **lifeempowered.com said:**
> Ok, are you selecting the XGL session before logging in?  This is the first troubleshooting step.  Let me know.

Yes.  The options I have for Session are:

1. Run Xclient script
2. GNOME
3. GNOME with XGL

I chose option 3.  Another thing I noticed is that when I choose this option, I get strange things happening such as windows not refreshing properly.  It makes me think it's trying to start it but for whatever reason it can't.  I figured I should include my xorg.conf file, here it is:

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "ServerFlags"
	Option		"AIGLX"		"off"
EndSection

```

---

### Post by lifeempowered.com on 2007-04-25
> **markdbd said:**
> Have you tried sensors-applet, I think it's much cleaner than gkrellm and it detects i8kutils automatically. In the following link I wrote a guide in spanish to configure it:

Translated with Google

[http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F25%2Fsensors-applet-monitorizando-y-controlando-la-temperatura-en-ubuntu%2F&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F25%2Fsensors-applet-monitorizando-y-controlando-la-temperatura-en-ubuntu%2F&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

Sorry, haven't tried it...I will however

Thanks!

---

### Post by lifeempowered.com on 2007-04-25
> **Wintaru said:**
> Yes.  The options I have for Session are:

1. Run Xclient script
2. GNOME
3. GNOME with XGL

I chose option 3.  Another thing I noticed is that when I choose this option, I get strange things happening such as windows not refreshing properly.  It makes me think it's trying to start it but for whatever reason it can't.  I figured I should include my xorg.conf file, here it is:

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "ServerFlags"
	Option		"AIGLX"		"off"
EndSection

```

It seems correct, are you sure you have the 2.0 version of Beryl installed, not the latest?  Read that part again.  It's important that you don't install the latest version or updates from Beryl as it breaks Beryl and you have the very symptoms you are describing.

---

### Post by shuqi on 2007-04-25
Just a quick note: 
```
wget http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz
```
in your guide comes up with a broken link, since it's at version number 109 now. Please replace it with:
```
wget http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz
```

And regarding Beryl & KDE:
if you are following the guide to get Beryl working under KDE, then don't forget to ```
apt-get install aquamarine
``` which is the window manager for KDE. Emerald works fine as well, but if you want to keep the look of Kubuntu, then you need to install aquamarine as well.

---

### Post by Wintaru on 2007-04-25
> **lifeempowered.com said:**
> It seems correct, are you sure you have the 2.0 version of Beryl installed, not the latest?  Read that part again.  It's important that you don't install the latest version or updates from Beryl as it breaks Beryl and you have the very symptoms you are describing.

I seem to remember manually installing some deb's from a thread I found that I thought might fix it.  In that case, what would be the easiest way to remove it all and start over from scratch without reinstalling Ubuntu?

Edit:

Oh and thank you so much for your help.  What a great community!

---

### Post by pertti on 2007-04-25
> **markdbd said:**
> Have you tried sensors-applet, I think it's much cleaner than gkrellm and it detects i8kutils automatically. In the following link I wrote a guide in spanish to configure it:

Translated with Google

[http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F25%2Fsensors-applet-monitorizando-y-controlando-la-temperatura-en-ubuntu%2F&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.markdbd.com%2F2007%2F04%2F25%2Fsensors-applet-monitorizando-y-controlando-la-temperatura-en-ubuntu%2F&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

I finally got the time to take a look and try that and it's been great so far! I has been a long time since I last heard the fan at full power, or had the CPU under 38ºC :). This thread is a real goldmine.

---

### Post by lifeempowered.com on 2007-04-25
> **shuqi said:**
> Just a quick note: 
```
wget http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz
```
in your guide comes up with a broken link, since it's at version number 109 now. Please replace it with:
```
wget http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz
```

And regarding Beryl & KDE:
if you are following the guide to get Beryl working under KDE, then don't forget to ```
apt-get install aquamarine
``` which is the window manager for KDE. Emerald works fine as well, but if you want to keep the look of Kubuntu, then you need to install aquamarine as well.

Awesome!  Thanks, will update now.  BTW anyone know the format for making the link check and download the latest version without having to update it over and over.  I'd like to do the same for ndiswrapper.  cheers.

---

### Post by lifeempowered.com on 2007-04-25
Hey all,

I just created a really BETA script for this install guide.  You can try it at your own risk.  I haven't, I REPEAT, HAVE NOT, tested it yet.  I'll test it tonight when I have time.  But you're welcome to it before that:
[URL="http://www.mylittleubuntuguide.com/files/feistydell.tar.gz"]
Feisty Dell Script[/URL]

It doesn't install Vmware, Automatix, or fan utils...yet.

---

### Post by Wintaru on 2007-04-25
Ok, I figured it out partially.  The window manager in Beryl was set as metacity rather than Beryl.  However, now that I have it running (working pretty well) the buttons on my windows are missing.

---

### Post by grahams on 2007-04-25
Great Howto, I now have Beryl running on my HP nw8440 laptop (ATI X1600). Thanks :guitar: 

Now I'm getting greedy :). Is there a way to run beryl on two screens with the fglrx driver? 

I have a dual screen fine setup working without xgl, my fglrxinfo is 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6458 (8.36.5)

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: 
OpenGL version string: 2.0.6458 (8.36.5)

If I select the Gnome_xgl session I get beryl on 1 screen, and a black screen on the other, but an X appears on the 2nd screen if the mouse travels there.

Is it possible to edit  /usr/local/bin/startxgl.sh and/or /usr/local/bin/start_beryl.sh to enable this?

Thanks in advance.

Update: 
there is a thread on this at [http://forum.beryl-project.org/viewtopic.php?f=36&t=4612&hilit=dual+screen](http://forum.beryl-project.org/viewtopic.php?f=36&t=4612&hilit=dual+screen)
looks like a common request.

---

### Post by Neuralgia on 2007-04-26
I'm sorry to report that on my Dell 6400 with ATI x1300 Beryl doesn't work.

Everything else ok.

I even tried this tutorial, which is kind of famous
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

The weird part, is that when I had Edgy, it worked great. After upgrade, no beryl at all, just "white screen of death" (only mouse cursor shows)

---

### Post by agiamba on 2007-04-26
i would like to voice agreement with others in this thread, this was awesome and i have an ATI card which is supposedly a lot more difficult, this guide was beautiful and i installed Beryl/Compiz with no problems. Thank you!!

---

### Post by Wintaru on 2007-04-26
Any suggestions on how to get windows decorations working with the Beryl window manager?  My xorg.conf file is on page 5 I believe, I checked to make sure the color depth is 24, which is about the only advice I've been able to google up so far.

---

### Post by nachotronics on 2007-04-27
Hello, here's how i got to install feisty on my dell inspiron 6400 (ati x1400):

I used the alternate CD, but the first time the installation slowed down at 6%, after a minute it continued, but then got stuck at 85% installing the braille display driver "brltty" package. When i looked at the details of the installation it seemed as it was trying to reach some files on the internet repos. 

The laptop was not connected at the time, as it never has been during my previous Ubuntu installations, anyway, I tried the 640x480 fix with the same results(stuck at 85%). I finally solved the problem by chosing not to configure any network adapter before install, wich i did by first selecting the wired lan card, then during the dhcp request i hit "cancel" the it gave me a few configuration choices manual, automatic or not to configure network at the time, i chose this one. Installation went through flawless

At first boot X server didn't start, so after unloading(sudo rmmod bcm43xx) and blacklisting the annoying bcm43xx module i connected to internet using the wired lan adapter, also typing
```
sudo dhclient
```
will get it going if dhcp is enabled. Then i installed xorg-driver-fglrx following the howto, and voila! X started at max res.

I didn't have any problem with beryl, ndiswrapper or the wlan card, but i still can't get the front keys to work in xmms, they do within rhythmbox. In edgy i fixed this by installing the xmms-xfree86 plugin, but this didn't work on feisty. Any ideas??

Hope this helps :wink:

---

### Post by Praill on 2007-04-27
Wow this is great. Like many here I have the same laptop and have never been able to run beryl until now.

A couple notes for people using a KDE desktop instead of gnome (i hate the stupid african theme):
- in the startxgl.sh script where it says 'gnome-session' change it to 'startkde'

- there is no SYSTEM > PREFERENCES > SESSIONS in KDE. You have to create a symlink yourself. So instead execute: 
ln -s /usr/local/bin/start_beryl.sh ~/.kde/Autostart/beryl-manager
at a terminal.

Thanks again!

---

### Post by lifeempowered.com on 2007-04-27
[COLOR="Red"]**This How To Has Been Updated!  You Can Now Use Automated Scripts!**[/COLOR]  Go back to the first post to see how: [Click Here]("http://ubuntuforums.org/showthread.php?t=399913")

---

### Post by ijn on 2007-04-27
hi.
just a question....
can I follow your guide for kubuntu 7.04 using the method 1(with the script)???
i definitely don't like gnome so I must download kubuntu, but I've seen that the download page of kubuntu don't have the check/uncheck possibility for pc lees then 256mb.

dell inspiron 6400 core 2duo 2ghz, 1024 mbram, ati x1300, wireless draft 802.11n(vey important hardware though, never worked) and bluetooth (never worked) I don't even think about ricoh card reader 5 in one.:( 
 thank u in advanced:)

---

### Post by lifeempowered.com on 2007-04-27
> **ijn said:**
> hi.
just a question....
can I follow your guide for kubuntu 7.04 using the method 1(with the script)???
i definitely don't like gnome so I must download kubuntu, but I've seen that the download page of kubuntu don't have the check/uncheck possibility for pc lees then 256mb.

dell inspiron 6400 core 2duo 2ghz, 1024 mbram, ati x1300, wireless draft 802.11n(vey important hardware though, never worked) and bluetooth (never worked) I don't even think about ricoh card reader 5 in one.:( 
 thank u in advanced:)

Sorry, I'd have to rewrite the script for kubuntu.  But if you're game, feel free! I'll post it here if ya do:)  And, you should go with Gnome.  Just try it.  I know it's a matter of opinion, but it's 100 times better than KDE.

---

### Post by on.journey on 2007-04-28
Hi, 
I got a newbie question. I followed the guide from the beginning and everything works fine. Except, how do I use the effects of beryl? I started the computer in Gnome+XGL session and opened the beryl manager, but nothing happens, I turn on effects but I can't see or do anything. Help pls :) I wanna have fancy effects.

---

### Post by ijn on 2007-04-28
many many thankx to lifeempowered:guitar: you were right for gnome, it's faster more stable and better supported than KDE. I just personalized it a bit and it looks cool. i followed the guide starting from installing fglrx, cause feisty was installed all alone by text install and after reboot recognized the Xserver.I have to say...never ever dealt with a guide so easy to install fglrx...and beryl works beautifully.seriously thank u...
one more question though... I have dell wireless 1500 draft 802.11n. do u think I should follow the wireless guide of course changing the windows driver version???
take care.

---

### Post by nachotronics on 2007-04-28
> **ijn said:**
> 
one more question though... I have dell wireless 1500 draft 802.11n. do u think I should follow the wireless guide of course changing the windows driver version???
take care.

Dell provides the exact same driver for:

Wireless 1350 WLAN MiniPCI Card, 
Wireless 1350 WLAN PC Card, 
Wireless 1370 WLAN MiniPCI Card, 
Wireless 1390 WLAN ExpressCard,
Wireless 1390 WLAN MiniCard, 
Wireless 1450 WLAN miniPCI Card, 
Wireless 1470 Dual-Band WLAN miniPCI Card, 
Wireless 1490 Dual-Band WLAN MiniCard, 
[COLOR="Red"]**Wireless 1500 Draft 802.11n WLAN mini Card**[/COLOR]

So it should work, just give it a try. On Edgy, the driver downloaded from [http://support.dell.com](http://support.dell.com) didn't work on my Dell WLAN 1390, while the one in this post did. You'll know if it worked after doing:
```
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
ndiswrapper -m
sudo modprobe ndiswrapper
```
after loading this module your wifi light should turn on right away

I know some people got your wlan card to work on edgy, it should be the same here(hopefully:wink:)

Tip: sometimes when i am far from the access point(low signal) i get disconnected and then i don't know why but it wont connect again even though i have enough signal power. I solved this by typing these 2 commands:
```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```
This is similar to the "Repair" option in windows, it turns the wlan card off and on again.

Hope this helps :wink:

---

### Post by Wintaru on 2007-04-28
The script fixed my problems with Beryl yay!

---

### Post by ijn on 2007-04-29
hi
I followed the howto wireless, but it did't worked. I used the driver R151517 which is the latest driver for my Dell Wireless 1500 Draft 802.11n WLAN mini Card. the light indicator it wont turns on. so I presume that it does not work. maybe need some manually configuration,but I don't see around any tool who can help me with,(exe:like KnetworkManager in KDE).I think I followed the guide properly cause every command came with a positive output. here is when I give LSPCI:
@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [ATI Mobility Radeon X1300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

please help:)

---

### Post by argux on 2007-04-29
Here is a 'me too'. Before trying the guide for the wireless card, the Network Settings applet in KDE would show the wireless card, though it wouldn't activate it. After manually installing ndiswrapper and the driver according to the guide, I rebooted and the applet no longer shows the card. I tried rmmod'ing and modprobing again and it still wouldn't do anything.
 
When I do a 'ndiswrapper -l', the output is this:
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

It might be worth mentioning that this is not a 6400, but an Inspiron 1501. Also, blacklisting the video module didn't give me the ability to dim the brightness on my screen. I am using the fglrx drivers from the repos. Does that  matter at all? Should I try the official ones?

---

### Post by ijn on 2007-04-29
argux.... dell 6400/1501 it's the same machine. it just how dell decided denomination for respectively Europe and USA.
so if u have a dell wireless draft 802.11n installed on your machine and find a successful  howto please let me know.
I have the same problem.

---

### Post by lifeempowered.com on 2007-04-29
> **on.journey said:**
> Hi, 
I got a newbie question. I followed the guide from the beginning and everything works fine. Except, how do I use the effects of beryl? I started the computer in Gnome+XGL session and opened the beryl manager, but nothing happens, I turn on effects but I can't see or do anything. Help pls :) I wanna have fancy effects.

I'll need your system specs to continue.  Are they the same as mine?  Also, did you follow the Method 1 or Method 2 guide?

---

### Post by lifeempowered.com on 2007-04-29
> **ijn said:**
> many many thankx to lifeempowered:guitar: you were right for gnome, it's faster more stable and better supported than KDE. I just personalized it a bit and it looks cool. i followed the guide starting from installing fglrx, cause feisty was installed all alone by text install and after reboot recognized the Xserver.I have to say...never ever dealt with a guide so easy to install fglrx...and beryl works beautifully.seriously thank u...
one more question though... I have dell wireless 1500 draft 802.11n. do u think I should follow the wireless guide of course changing the windows driver version???
take care.

Awesome, glad to hear you "converted" over!  Although KDE offers many extras over Gnome, not only is it as you put, less stable/supported, it's a bit too cluttered for me. 

Ok, about your 1500 problem...I'm looking for a solution so I can add it to this guide.  I'll let you know.

---

### Post by lifeempowered.com on 2007-04-29
Sorry...don't need this post anymore.

---

### Post by ijn on 2007-04-29
ok thanku a lot for all
 here are some output from my machine after i tried your guide.
di@ubuntu:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
adi@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
adi@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

I don't understand..why it don't work. who is suposed to care the wireless connection over gnome??? the same app that handel my lan network?? network manager??

thank u

---

### Post by entropic_existence on 2007-04-29
Well after extended fights with my video settings with Fiesty Fawn and my x1400 video card I think I am going to rollback to Edgy Eft. If I get the 3d acceleration working in Fiesty right now I get jumpy video playback with AVI files. If I revert so the MESA driver is loading I can't use one of the visualization programs I need to use for work. Edgy was stable, I should have read the forums a bit closer before upgrading.

I'm still sticking with Ubuntu of course, I happen to rather like it after all :) I just think the rush of the Feisty release was a mistake.

---

### Post by lifeempowered.com on 2007-04-29
> **ijn said:**
> ok thanku a lot for all
 here are some output from my machine after i tried your guide.
di@ubuntu:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
adi@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
adi@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

I don't understand..why it don't work. who is suposed to care the wireless connection over gnome??? the same app that handel my lan network?? network manager??

thank u

To use the iwlist tool do the following:

sudo iwlist scanning

that will scan and show any results.

---

### Post by metadude on 2007-04-30
i use this in my /etc/apt/preferences instead of your rather long listing of packages:

```
Package: *
Pin: origin ubuntu.beryl-project.org
Pin-Priority: 999
```

---

### Post by lifeempowered.com on 2007-04-30
> **metadude said:**
> i use this in my /etc/apt/preferences instead of your rather long listing of packages:

```
Package: *
Pin: origin ubuntu.beryl-project.org
Pin-Priority: 999
```

If that works, great, I'll update my guide...however I've tried a short entry in my tests and found it faulty, meaning I got the wrong packages.  I'm about to blow my system away again to do some more script tests, so I'll add this and see what happens!  Thanks!

---

### Post by ShaneR on 2007-04-30
I'm having a problem with the script...

Every thing goes well untill it's time to execute step1:

./step1

I get a chmod error that it cannot access a or b, no such file or directory.  The files look fine and all steps were performed correctly.

Any help?

Thanks

---

### Post by ShaneR on 2007-04-30
I figured it out.

The first command in the guide (mkdir) didn't create the directory in the proper place.  I'm fairly new to linux, so I probably misunderstood.

Anyway, after booting and loging in, I just had to "mkdir /install" and that was it. I guess that means I was already in my home directory after booting...heh, who knows, I said I'm new ;)

I'm posting this from FF in Ubuntu, so i guess it worked :)

---

### Post by lifeempowered.com on 2007-04-30
> **ShaneR said:**
> I figured it out.

The first command in the guide (mkdir) didn't create the directory in the proper place.  I'm fairly new to linux, so I probably misunderstood.

Anyway, after booting and loging in, I just had to "mkdir /install" and that was it. I guess that means I was already in my home directory after booting...heh, who knows, I said I'm new ;)

I'm posting this from FF in Ubuntu, so i guess it worked :)

Yup, when you first boot up you are in /home/YOURNAME  where YOURNAME is whatever your user name is.  That's where any command is executed.  To keep things clean is why I have you create the "install" directory and cd into it before downloading and extracting, etc.  Anyway, thanks for your feedback as it's important for others who may be experienced but in a hurry and forget this important step!

---

### Post by allspiritseve on 2007-04-30
lifeempowered,

I used your howto to get my feisty to boot up (and I very much appreciate it). What is it that your script does that fixes feisty to work with 6400/ati1400/broadcom? Will feisty and later releases be updated to work on this hardware without having to run a script? I wouldn't want to have to do that every time I upgrade (or make a fresh install).

Cory

---

### Post by lifeempowered.com on 2007-04-30
> **allspiritseve said:**
> lifeempowered,

I used your howto to get my feisty to boot up (and I very much appreciate it). What is it that your script does that fixes feisty to work with 6400/ati1400/broadcom? Will feisty and later releases be updated to work on this hardware without having to run a script? I wouldn't want to have to do that every time I upgrade (or make a fresh install).

Cory

What it does is pretty verbose.  You can see exactly by looking at Method Two.  That's what the script basically does automatically.  I doubt Ubuntu will do much any time soon, remember the operating system has to work on EVERY computer, not just our 6400s.  That's why guys like me do this, to support our own system and make it work.  Cheers!

---

### Post by lifeempowered.com on 2007-04-30
Ok All, I have added the automatix commands to the script so it now installs it automatically.  I'm also considering adding an entry that forces the step2 part to run automatically when you login after step1.  Anyone care about that?  Or will it be a waste of my time.  I personally don't mind typing the command for step2.  Let me know!

---

### Post by carpex on 2007-04-30
Just a note to x86_64 bit users like me: i8kutils is not available in a 64 bit version in the repos. Does anybody know of an alternative?

C

---

### Post by garion on 2007-04-30
The Beryl part works great for me, thanks!  On my Dell 6400 with ATI x1300 card, vesa driver actually works at 1400x1050 after installing with Alternate CD iso, I am not sure why, because I couldn't boot the final livecd.

One question though: there seems to be some issue with DRI under XGL.  Hence, my mplayer video seems to behave a little odd with various vo settings.

Under my XGL Beryl session, fglrxinfo gives me:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6334 (8.34.8)

```
No error, looks normal.

But with fgl_glxgears, I get:
```
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Error: couldn't get fbconfig

```
Error, and I don't get the rotating gears showing on screen.

With glxgears, I get:
```
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
11544 frames in 5.1 seconds = 2276.842 FPS
11053 frames in 5.1 seconds = 2186.234 FPS
...

```
The video is a little bit jagged.  I don't think the fps means much here, since a normal gnome session works with DRI and gives about 800 fps, and it looks smoother too.

Finally, glxinfo | grep direct gives me:
```
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
direct rendering: No

```
Seems like no DRI here again.

Anyone knows how to fix this?  Beryl is working fine, but the graphics seems to be a bit slow, not unusable, but just not as snappy as a regular gnome session, where DRI is fine and every test from above passes with no error.  Thanks! :)

---

### Post by lifeempowered.com on 2007-04-30
Garion,

I get the DRI missing message also but the gears appear and run smoothly.  Not sure what is going on with yours.  Perhaps the difference in the graphics card model?  Not sure.  Anyone else have input on this?

---

### Post by kalani on 2007-05-01
Thx for the guide is very useful but i have a problem, beryl is already installed but when i select beryl as my window manager the white screen of dead appears can you help me?

---

### Post by garion on 2007-05-01
Well, I guess it's not fair to say that my XGL is sluggish, it's not.  Yah, I've seen this DRI missing problem in Mandriva too, but I recall having this working at some point in PCLinuxOS (I could be wrong on that though, it's been a while...).

I guess the question boils down to how to get video and other DRI dependent stuffs to work nicely, most importantly, video playback.  Mplayer (or any player for that matter) does not play well with any choice of vo driver, xv, x11, gl, gl2.  I tried another frontend, smplayer, and that seems to marginally work with x11 driver, playing okay with small window sizes (800 width or below), but becoming slow and drawing a lot of cpu power at full screen.  I am not really familiar with the XGL thing, so I am wondering whether there is a way to fix that or is it just an inherent issue with XGL at the moment.  Well, I guess the real blame should go to ATI for not providing an AIGLX compatible driver :).

Finally, I have another question for all of you guys here.  Does anyone here have suspend to ram working on his/her 6400/E1505, with x1300 video in particular (seems like x1400 behaves a little different with suspending, and people are having more luck there)?  Mine has a x1300 unfortunately, which works well with just changing "POST_VIDEO=false" in Edgy and even Feisty beta!  But it was broken a week or so before the final release and has since then been broken.  I tried fresh installing and many different combination of tweaks and nothing worked so far.  I always get a black screen on resume... arrrgh!  Though I am not 100% sure, but I'd bet a dollar that it's the video, so if anyone DOES get suspend to ram to work on a Dell 6400 w/ ATI X1300, I'd appreciate it if you could share your success story here :), thanks.







> **lifeempowered.com said:**
> Garion,

I get the DRI missing message also but the gears appear and run smoothly.  Not sure what is going on with yours.  Perhaps the difference in the graphics card model?  Not sure.  Anyone else have input on this?

---

### Post by Cueto_99 on 2007-05-01
Thanx Lifeempowered! First time I install linux and everything went smooth following your tutorial!  and I use the non-script guide!

I still have an issue i can't resolve... I installed Beryl according to all the steps, and all the eyecandy and fancy efects are working great, except the 3D Cube... I already assigned the shortcut keys for the cube, it is already checked and configure in the beryl manager, but when I press the key combination the desktop goes back, and i get one workspace beside the other... like a slideshow... I can move through each workspace...

The only detail I see is that when I log in with the Gnome with XGL session I get the black and white checkers screen (that some others have mentioned) for like 3 seconds before loading the desktop... then everything goes back to normal...

If someone is having the same problem or knows how to solve this, please let me know...
My laptop specifications are the same according to this thread: Dell 6400, ATi X1400, 1Gb Ram, 1280 X 800, Core Duo T2250...

Thanks everyone, Linux rules! :KS

---

### Post by Cueto_99 on 2007-05-01
> **kalani said:**
> Thx for the guide is very useful but i have a problem, beryl is already installed but when i select beryl as my window manager the white screen of dead appears can you help me?

Im a little new on linux, but, are you login in with the "GNOME with XGL" Session?? to do this, on the login screen you have to go to Options, Select Session, Gnome with XGL, and then type your usual login and password...

I don't know if this will help, but at least I didnt knew how to do this... so it might help someone...

---

### Post by kalani on 2007-05-01
yeah i already login into gnome with xgl session but the white cube stills there

---

### Post by SuperD2000 on 2007-05-01
Hello everyone,

I am having several problems with my Dell e1505 that I really need some help on.

1) I installed ndiswrapper and the driver, but when I open the windows wireless drivers under the system -> administration menu it says that the driver is installed but there is no hardware present.

I have the network manager running and it can detect my wireless network, but when i select it from the menu it will not connect. Then only way I can connect to my wireless network is to do it manually.

2) How do I get the RIcoh memory card reader to work?

Thank you for your help.

---

### Post by Pugwash on 2007-05-01
Thanks very very much for this guide!!!:) :) :)  Worked wonderfully! Enjoying the Beryl goodness!!

---

### Post by lifeempowered.com on 2007-05-01
Thanks for the props everyone!  FYI, I'm now only updating the script, I have not updated or touched the step-by-step for a while.  So if you're having problems, doing a fresh install and using the script may fix them.

Cueto_99:
Now, about the "slide" vs. "cube" ... There is a setting that allows you to use a slide rather than cube feature.  My guess is your key combos are conflicting.  You may have a key combo for switching to slide mode that is conflicting with the others.  Check those first and make sure all your hotkeys are unique and that in the process of entering one combination you don't enter another before finishing the desired one.  Like CTRL+ALT+K, but CTRL+ALT does something.  Get it?

kalani
As for the white screen of death, can you remind me of your system specs again?  Also, did you follow the guide or use the script?  You may want to do a fresh install and use the latest version of the script as it's been heavily updated.

SuperD2000:
I think I have a similar issue and this all may be a "bug" with Network Manager.  I have trouble connecting to unsecured networks, no problems with WPA or WEP though.  Weird...I'll do some more checking into it, but see if you can connect easier to a secured network.
 
As for the Ricoh memory reader, it should work perfectly with SD and MMC cards, just not with Sony Memory Stick.  I'm still trying to fix this and will update when I find a solution.

---

### Post by SuperD2000 on 2007-05-01
Thank you for your help!!!

I have been messing around with my interface file to see if i can get the network manager to work with my system and I don't remember what it is suppose to look like. This is what I got currently:

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth1 inet dhcp
wireless-essid XXXXXXXXX

auto eth1
```

Is this correct?

---

### Post by Pugwash on 2007-05-01
Just a question, are the dual cores working or do I have to install the smp kernel?

Edit - The generic kernel seems to detect both cores.

---

### Post by garion on 2007-05-01
lifeempowered, what settings have you been using for your mplayer/totem in xgl?  does video playback work well for you in xgl compared to a regular x session?



> **lifeempowered.com said:**
> Thanks for the props everyone!  FYI, I'm now only updating the script, I have not updated or touched the step-by-step for a while.  So if you're having problems, doing a fresh install and using the script may fix them.

Cueto_99:
Now, about the "slide" vs. "cube" ... There is a setting that allows you to use a slide rather than cube feature.  My guess is your key combos are conflicting.  You may have a key combo for switching to slide mode that is conflicting with the others.  Check those first and make sure all your hotkeys are unique and that in the process of entering one combination you don't enter another before finishing the desired one.  Like CTRL+ALT+K, but CTRL+ALT does something.  Get it?

kalani
As for the white screen of death, can you remind me of your system specs again?  Also, did you follow the guide or use the script?  You may want to do a fresh install and use the latest version of the script as it's been heavily updated.

SuperD2000:
I think I have a similar issue and this all may be a "bug" with Network Manager.  I have trouble connecting to unsecured networks, no problems with WPA or WEP though.  Weird...I'll do some more checking into it, but see if you can connect easier to a secured network.
 
As for the Ricoh memory reader, it should work perfectly with SD and MMC cards, just not with Sony Memory Stick.  I'm still trying to fix this and will update when I find a solution.

---

### Post by ijn on 2007-05-02
> **lifeempowered.com said:**
> Awesome, glad to hear you "converted" over!  Although KDE offers many extras over Gnome, not only is it as you put, less stable/supported, it's a bit too cluttered for me. 

Ok, about your 1500 problem...I'm looking for a solution so I can add it to this guide.  I'll let you know.

hi lifeempowered everything is going well on my ubuntu + gnome. exept the wireless.here is output of commands that you told me:
adi@ubuntu:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
adi@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
adi@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
adi@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

if you can say something I'll appreciate that, otherwise thank you again. you already help me a lot.
any one who uses a dell 6400 have information about well working of those two devices:
Dell Wireless 355 Bluetooth Module (Bluetooth 2.0 + EDR)
Ricoh card reader 5 in one.

thank you.

---

### Post by lifeempowered.com on 2007-05-02
Sorry everyone, been really busy here working on another project...I'll respond to you all soon.

---

### Post by Cueto_99 on 2007-05-02
Hey, Thanks Lifeempowered! I've got myself a 3D Cube! Excellent... I Mean... Amazing!
You were right, somehow I messed up the shortcut, so I did the following:
I went to:

 /home/"Username"/.beryl
(.beryl folder is hidden, so press Ctrl+H to show hidden files)

And deleted the file: Settings

When Beryl loads again, It will load the default settings... and create a new Settings file

By the way, the default way to bring up the 3D Cube is: Ctrl + Alt + Left Click + Move The Mouse!

Thanks everyone

:confused:  And now I think why did I bought Vista Premium... :confused:

---

### Post by alanrt on 2007-05-03
Thanks so much for the script! It worked fantastically on my e1505.

I have my laptop hooked up to a Dell 2405fpw monitor, but I can't figure out how to enable 1920x1200, the monitor's native resolution. I tried adding the resolution to the xorg.conf file but nothing has worked so far. But I don't even see 1680x1050 in there, and that's what I'm currently running with.

Has anyone been able to do this?

Thanks!

---

### Post by lifeempowered.com on 2007-05-03
> **Cueto_99 said:**
> 

:confused:  And now I think why did I bought Vista Premium... :confused:

Exactly! LOL, I actually obtained Vista from a local IT department and installed back when it was about to be released.  I was impressed, for Windows it's a huge leap.  Unfortunately for Microsoft, it's not ready.  All I can say is compatibility, compatibility, compatibility.  Hell, if you were a huge windows fan and wanted to dedicate yourself to Vista, you'd be far better off running Ubuntu with VMWare and XP inside it.  No compatibility issues there!  

I love Ubuntu!

---

### Post by lifeempowered.com on 2007-05-03
> **alanrt said:**
> Thanks so much for the script! It worked fantastically on my e1505.

I have my laptop hooked up to a Dell 2405fpw monitor, but I can't figure out how to enable 1920x1200, the monitor's native resolution. I tried adding the resolution to the xorg.conf file but nothing has worked so far. But I don't even see 1680x1050 in there, and that's what I'm currently running with.

Has anyone been able to do this?

Thanks!

Adding the resolution won't work since X is not utilizing that section, you'll notice there's a duplicate section that X uses instead which doesn't have the resolutions listed.  You may be able to add it in that section (the duplicate) as in my example below.  This is, however, not tested since I don't have a monitor that handles higher res... the other issue may just be your graphics card.  If it doesn't support a higher res you won't get one:
Ok, here's what the screen section that is being used looks like now:
```
Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection
```

And here's what you might try and see if it works:
```
Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1920x1200"	"1680x1050"	"1280x800"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

You can do the numbers however you want of course...Tell me if that works :)

---

### Post by lifeempowered.com on 2007-05-03
> **ijn said:**
> hi lifeempowered everything is going well on my ubuntu + gnome. exept the wireless.here is output of commands that you told me:
adi@ubuntu:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
adi@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
adi@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
adi@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

if you can say something I'll appreciate that, otherwise thank you again. you already help me a lot.
any one who uses a dell 6400 have information about well working of those two devices:
Dell Wireless 355 Bluetooth Module (Bluetooth 2.0 + EDR)
Ricoh card reader 5 in one.

thank you.

Ok, I don't see an eth1 listed in the output of iwlist scanning.  That's weird, try this command:
```
sudo iwlist eth1 scanning
```

Post your output.  Also, is the WiFi light lit?  Another thing to try, make sure your ndiswrapper module is running:
```
sudo modprobe ndiswrapper
```

Cheers!

---

### Post by lifeempowered.com on 2007-05-03
> **garion said:**
> lifeempowered, what settings have you been using for your mplayer/totem in xgl?  does video playback work well for you in xgl compared to a regular x session?

Actually, I installed totem and mplayer using Automatix and didn't touch the settings.  It works perfect.  I've had trouble in the past when trying to install them manually, so I'd use automatix if I were you.  I may even write some of those things into my script so that Automatix won't be necessary.  We'll see.

---

### Post by lifeempowered.com on 2007-05-03
> **SuperD2000 said:**
> Thank you for your help!!!

I have been messing around with my interface file to see if i can get the network manager to work with my system and I don't remember what it is suppose to look like. This is what I got currently:
Is this correct?

Here's my interfaces file contents and everything works perfect now, even the unsecured networks:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by lifeempowered.com on 2007-05-03
> **SuperD2000 said:**
> Hello everyone,

I am having several problems with my Dell e1505 that I really need some help on.

1) I installed ndiswrapper and the driver, but when I open the windows wireless drivers under the system -> administration menu it says that the driver is installed but there is no hardware present.

I have the network manager running and it can detect my wireless network, but when i select it from the menu it will not connect. Then only way I can connect to my wireless network is to do it manually.

2) How do I get the RIcoh memory card reader to work?

Thank you for your help.

One more thing, can you watch your log files while you attempt to connect and post any relevant output?  Just go to System>Administration>System Log, then click on syslog and try to connect using Network Manager.  Copy and paste the output from when you clicked to connect to the time it either times out or whatever.

---

### Post by shauns on 2007-05-03
I just followed the steps got as far as finishing the install, rebooted selected Ubuntu (dual booting with Vista) It Shows the Kubuntu loading screen, then flashes and goes to a black sreen with a curser blinking never does anything. Never shows any error or screen to start doing the other steps, any help?

Specs:
E1505
Core Duo 1.6
1gig
X1400

---

### Post by lifeempowered.com on 2007-05-03
> **shauns said:**
> I just followed the steps got as far as finishing the install, rebooted selected Ubuntu (dual booting with Vista) It Shows the Kubuntu loading screen, then flashes and goes to a black sreen with a curser blinking never does anything. Never shows any error or screen to start doing the other steps, any help?

Specs:
E1505
Core Duo 1.6
1gig
X1400

Use the script first of all.  Second of all, what is handling your boot?  Ubuntu or Vista??

---

### Post by shauns on 2007-05-03
Im unable to get to the point to use scripts. and Ubuntu is handling boot.
Like i said Kubuntu shows the loading bar. then i see a flash and it looks like it wants me to login.. then the Kubuntu screen shows back up then goes away and then the screen goes black with ONLY a blinking _

---

### Post by lifeempowered.com on 2007-05-03
> **shauns said:**
> Im unable to get to the point to use scripts. and Ubuntu is handling boot.
Like i said Kubuntu shows the loading bar. then i see a flash and it looks like it wants me to login.. then the Kubuntu screen shows back up then goes away and then the screen goes black with ONLY a blinking _

Ok, first problem is you're using Kubuntu.  The install will be different and my script won't work.  Sorry.

---

### Post by shauns on 2007-05-03
Im installing Ubuntu now... i will see what happens. I just wanted to use the KDE i thought everything would be the same.

Ill update when its done.

---

### Post by shauns on 2007-05-03
I got it to start the scripts but i am getting connection time out errors now.
[LINK TO IMAGE]("http://www.shaunbarrow.com/shaun/0503071837a.jpg")
any clue?

---

### Post by shauns on 2007-05-03
*update*
its still stuck trying to connect

---

### Post by lifeempowered.com on 2007-05-03
That's either a connection issue on your computer/internet or the websites for ubuntu.  Sorry...it may be best to restart the install.

---

### Post by shauns on 2007-05-03
yay! im installed!
anybody find a fix to get t he full rez on the ati 1400?
1680x1050 i think it is?

Thanks for the help btw =)

---

### Post by garion on 2007-05-03
Thanks for the discussion.  I was using mplayer installed from the synaptic directly, and it didn't work well with any vo setting under xgl.  But today I uninstalled the 8.34 fglrx and installed 8.36 driver with Envy's script, and the mplayer frontend smplayer seems to be working well with both xv and gl2 drivers.  The original mplayer works with those two drivers as well, but somehow can't get the original video aspect ratio right, but playing fullscreen is okay.


> **lifeempowered.com said:**
> Actually, I installed totem and mplayer using Automatix and didn't touch the settings.  It works perfect.  I've had trouble in the past when trying to install them manually, so I'd use automatix if I were you.  I may even write some of those things into my script so that Automatix won't be necessary.  We'll see.

---

### Post by garion on 2007-05-03
installing fglrx should give you the full wsxga+ resolution, at least for me it works with x1300.  you may try "sudo aticonfig --resolution=0,1680x1050" if it doesn't work automatically.



> **shauns said:**
> yay! im installed!
anybody find a fix to get t he full rez on the ati 1400?
1680x1050 i think it is?

Thanks for the help btw =)

---

### Post by garion on 2007-05-04
Ah, i announced my success too early.  It actually didn't work, video is still crappy in xgl.  I tried automatix as well, but it doesn't make a difference, since it uses the same repo as synaptic to install mplayer, so it's the exact same thing.  I actually didn't like automatix after using it.  It installed a bunch of packages with multimedia codec, and later on doesn't let me reverse the process at all, which is annoying.




> **garion said:**
> Thanks for the discussion.  I was using mplayer installed from the synaptic directly, and it didn't work well with any vo setting under xgl.  But today I uninstalled the 8.34 fglrx and installed 8.36 driver with Envy's script, and the mplayer frontend smplayer seems to be working well with both xv and gl2 drivers.  The original mplayer works with those two drivers as well, but somehow can't get the original video aspect ratio right, but playing fullscreen is okay.

---

### Post by Orion2000za on 2007-05-04
> **markdbd said:**
> Well I tried to install Feisty 2 times with the alternate CD but it breaks on 85%, I also checked the integrity of the CD.

Strange but I can't install feisty, normal CD doesn't work with ATI, alternate CD hangs for me at the 85% of the instalation.

maybe someone replied to you already - I had the same problem "on and off" and have no explanation except I disconnected network during install and then I would manage eventually

thanks for the guide btw, I was going NUTS trying to do a clean sweep install after clearing out a rather messy but working edgy install...

Sinclair

---

### Post by komoleponemo on 2007-05-04
> **shauns said:**
> Im unable to get to the point to use scripts. and Ubuntu is handling boot.
Like i said Kubuntu shows the loading bar. then i see a flash and it looks like it wants me to login.. then the Kubuntu screen shows back up then goes away and then the screen goes black with ONLY a blinking _

Just press Ctrl + Alt + Backspace (you will see the command line) and then just follow the how to.

---

### Post by lifeempowered.com on 2007-05-05
I'm working on individual scripts, this way whether you use Ubuntu or Kubuntu you'll be able to run scripts.  Hopefully!   Also, there's now a much easier work around for the Install Live CD not running X, check it out in the first post.

---

### Post by zarmando on 2007-05-05
> **on.journey said:**
> Hi, 
I got a newbie question. I followed the guide from the beginning and everything works fine. Except, how do I use the effects of beryl? I started the computer in Gnome+XGL session and opened the beryl manager, but nothing happens, I turn on effects but I can't see or do anything. Help pls :) I wanna have fancy effects.

When you Login using the xgl session, Beryl should just work.
test it by moving a window. It should woble. or try the cube by pressions ctrl+alt and then left or right arrow key.

If it doesn't work, and you have the same video card mentionned in the first post of this thread, you might have done something wrong in the process.

Good luck.

P.-S. lifeempowered.com  : your scripts are great but is it still possible to have access to the whole detailed installation process  ? I believe it would be usefull for those having one or two doffrent hardware pieces only but wanting to have a working machine...

---

### Post by vradovic on 2007-05-06
MAN. THANKS A LOT. 

I HAVE Notebook HP dv6205us with  

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)


i follow your post from first page and everything works just fine. 
I just need to rebood my notebook two times... ??? but not problem anymore 

THANKS 10x

---

### Post by zero_2x on 2007-05-08
Great, this script work great for me, I'm still having a problem with my dell 355 bluetooth adapter, but everything else is working fine, beryl too.

Thanks. :D

---

### Post by binky1 on 2007-05-08
Hey!  Sweet! !
This is the first HOWTO that has ever worked for me.

Beryl looks **great!!**


I am using a Dell Inspiron E1705 with an ATi X1400.

Thanks a bunch!

Cheers,

Mike

---

### Post by Orion2000za on 2007-05-10
Thanks for the efforts, it really helped me in doing a fresh Feisty install on my Dell 6400 with ATI X1300. 

However - I wish you would still leave the "no-script" advise for those who might not want Beryl or who run Kubuntu. I run Kubuntu and all I wanted was to get things up and running with proper resolution. 

Along the way I found a post to get suspend and hibernate working in the thread - and it finally does! Brilliant! 

thanks everyone,
Sinclair

---

### Post by lifeempowered.com on 2007-05-10
> **Orion2000za said:**
> Thanks for the efforts, it really helped me in doing a fresh Feisty install on my Dell 6400 with ATI X1300. 

However - I wish you would still leave the "no-script" advise for those who might not want Beryl or who run Kubuntu. I run Kubuntu and all I wanted was to get things up and running with proper resolution. 

Along the way I found a post to get suspend and hibernate working in the thread - and it finally does! Brilliant! 

thanks everyone,
Sinclair

Hey Sinclair, 

I'll be adding some scripts in the following hours or day.  So far I have these in my list, if anyone has any others they want, let me know:

1. Full Ubuntu w/ Beryl + VMware
2. Full Ubuntu w/ Beryl
3. Full Ubuntu NO Beryl + VMware
4. Full Ubuntu NO Beryl
5. Full Kubuntu w/ Beryl + VMware
6. Full Kubuntu w/ Beryl
7. Full Kubuntu NO Beryl + VMware
8. Full Kubuntu NO Beryl

The Kubuntu will be coming within a day or so.  The others will be ready soon.

---

### Post by yayayamon on 2007-05-10
I used this script to install Kubuntu 7.04. This may have already been covered in the thread, but there's 15 pages and it wouldn't hurt to be posted again since it helped me.

I followed the tutorial up until the part where the laptop rebooted and I had to run 
```

cd install
sudo ./dellinstall

```

I kept getting an error that dellinstall could not be run. I could however type 'startx' and get into KDE no problems, everything worked great.

After poking around in the install folder, I realized dellinstall didn't have execution rights.
I solved this by simply making it executable. (remember this is inside the install directory)

```

sudo chmod +x dellinstall

```

I exited x, back to the text-based command line and voila, the sudo ./dellinstall worked. My laptop now boots right into Kubuntu 7.04.


EDIT: btw my configuration is a 6400 w/ x1400

---

### Post by jadz0r on 2007-05-12
Hi guys,

First of all, thanks for the article.

I had no issues at all installing Feisty on my 6400.

I do however have an odd problem...i'm not sure if it's a common problem or not, but I thought it'd be best to ask.

I have noticed a high pitch sound coming from my laptop (it seems to be the left hand side) whenever i scroll up and down a webpage, or hover over an element on the screen that seems to animate.  The sound actually sounds like it's a cd spinning in the drive, or a hard disk being read, however there is no cd in the drive.

I'm wondering if it's an issue with my X4100 and the drivers?  I followed the guide in the first post about the drivers, so I have not installed anything else.

Any help would be great.

Thanks

---

### Post by lifeempowered.com on 2007-05-14
> **jadz0r said:**
> Hi guys,

First of all, thanks for the article.

I had no issues at all installing Feisty on my 6400.

I do however have an odd problem...i'm not sure if it's a common problem or not, but I thought it'd be best to ask.

I have noticed a high pitch sound coming from my laptop (it seems to be the left hand side) whenever i scroll up and down a webpage, or hover over an element on the screen that seems to animate.  The sound actually sounds like it's a cd spinning in the drive, or a hard disk being read, however there is no cd in the drive.

I'm wondering if it's an issue with my X4100 and the drivers?  I followed the guide in the first post about the drivers, so I have not installed anything else.

Any help would be great.

Thanks

I get the same thing.  When direct rendering in windows it does the same thing...probably an ATI thing.

---

### Post by trashjedi on 2007-05-15
> **lifeempowered.com said:**
> I get the same thing.  When direct rendering in windows it does the same thing...probably an ATI thing.
I get that high pitch noise, except it's **all the time!!**
I contacted Dell a few times already, and one of the tecnicians said I should send it to a depot for replacement or repair, but I couldn't at the time, and then I try again now that I can, and the new technician makes me go through all the same steps as the last one! 
The thing is I need to do tests with the Dell Bios Diagnostics thing (Fn + F2 at startup I think), and when I didn't have linux, I think it rebooted and I could then choose the custom tests. Except that now GRUB shows up, and I can't do any custom tests... :(

So I hope I'll be able to solve this problem, because it's slightly getting on my nerves (a high pitch noise the whole time when the computer is on is definitely not fun!! I can tell you)

I think it may have to do with the graphics card and small vibrations or whatever. It's specific to this Dell configuration I think.

---

### Post by hubert.muchalski on 2007-05-18
Hello,

This thread is very long so I didn't read the whole content, but as far as my searches go I couldn't find solution for my problem. I'm having troubles with installing Ubuntu on my E1505. The configuration is the same except for intel pro wireless.

The issue is that after I run the script second time it aborts during installation of vmware and stops. After reboot system works fine, I mean Beryl works OK, ATI drivers and screen resolution is fine. 

However, I don't see Automatix and VMware activator is present in Applications Menu, but nothing is starting out. Any clue?

hubert

P.S. I don't know if it should be like that but both scripts (with or without vmware) are the same and actually running two separate scripts, you're doing the same thing. I'm not a programmer and maybe I'm wrong but in no-vmware-script in line 4 should be

```
wget http://www.mylittleubuntuguide.com/files/novm/feistydell.tar.gz
```

and is
```
wget http://www.mylittleubuntuguide.com/files/feistydell.tar.gz
```

---

### Post by revout on 2007-05-19
> **Orion2000za said:**
> Thanks for the efforts, it really helped me in doing a fresh Feisty install on my Dell 6400 with ATI X1300. 

However - I wish you would still leave the "no-script" advise for those who might not want Beryl or who run Kubuntu. I run Kubuntu and all I wanted was to get things up and running with proper resolution. 

Along the way I found a post to get suspend and hibernate working in the thread - and it finally does! Brilliant! 

thanks everyone,
Sinclair

I agree here. The individual sections were very well-written and helpful. I bookmarked this thread because the Beryl instructions helped me to get Beryl running on a friend's non-Dell desktop. I was sad to see it gone as they were great instructions; I'm sure I'll want to install these components again at some point on some computer and would like to have the control of step-by-step.

Any chance of the instructions in a new thread or on a site somewhere if you don't think they belong here anymore?

---

### Post by nachotronics on 2007-05-20
You can try this link from the beryl wiki:

[_**Install Beryl on Ubuntu Feisty with XGL**_]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by TheLostMigrant on 2007-05-21
Rudimentary question - 

I have essentially the same machine and the same problem - BUT - I don't want to install Ubuntu at this time, just test drive it with the DVD.

So, can I type in all those commands, and NOT install Ubuntu, but just run it off the disk / in RAM to test drive it?

(Backstory:  I wasn't planning on migrating to Linux right now, but the wife's computer may need a rescue disk in the near future, so why not try a Linux live CD .... )

Thanks.

---

### Post by mikedep333 on 2007-05-21
I just noticed this thread. My friend and I have inspiron 6400's with the ati x1400. I have a dell truemobile 1390 in mine (bcm43xx.)

Before I noticed this thread, I setup my laptop manually. I ran:
sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

this got my 2d video with 3d acceleration working properly, but ubuntu's default desktop effects didn't work

I then used bcm43x-fwcutter to get the firmware for my wireless, and it worked fine.

I then ran lifeempowered.com's scripts but modified them so they wouldn't install vmware or ndiswrapper

However, after running the script, desktop effects do not work. sudo startxgl.sh only yields a blank desktop or fails to start because "Server is already active for display 1". From a graphical session, start_beryl.sh does nothing. I have verified that lifeempowered.com's xorg.conf is in use, but I don't see how it can even work with composite disabled.

starting beryl manager and switching over to beryl instead of metacity does nothing

So my main question is, what do I need to do to get my desktop effects working.

My secondary question is why use ndiswrapper over bcm43xx?

I apologize if these questions have already been answered but I have looked through the first 5 or so pages, and the last 5 or so pages.

Update:
I saw this thread [http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684) and looked over it more
apparently I didn't have /etc/X11/sessions/xgl.desktop, so I added that

still, when I go to run startxgl.sh, I get the following:
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
gnome-session: you're already running a session manager

Can anyone help me on getting Xgl to startup?

---

### Post by carpex on 2007-05-23
@mikedep. My feeling is that you are simply not login in to an xgl session. If you have properly created xgl.desktop, click on log off (or ctrl-alt-backspace) and then select sessions...xgl session before you log in. Then, hopefully everything will work as expected. 

HTH, 

CP

---

### Post by nothumphrey on 2007-05-23
lifeempowered.com... thanks. everyone... thanks.  : )

---

### Post by mikedep333 on 2007-05-23
> **carpex said:**
> @mikedep. My feeling is that you are simply not login in to an xgl session. If you have properly created xgl.desktop, click on log off (or ctrl-alt-backspace) and then select sessions...xgl session before you log in. Then, hopefully everything will work as expected. 

HTH, 

CP

Whoops, I feel so stupid for not thinking about selecting the session.

carpex, lifeempowered.com, thanks so much!

Still, I would like to know why ndiswrapper is used over bcm43xx.

---

### Post by lifeempowered.com on 2007-05-29
the bcm driver is broken.  that's why we use ndiswrapper.  on another note, after updating my kernel via the manager, my system broke.  Hmmm, I'm going to try to reinstall tonight and see what happens.  Later.

---

### Post by hubert.muchalski on 2007-06-01
I wanted to ask if kernel update is OK for the system but your previous post gives me negative answer. I'll upgrade when safe.

Cheers

---

### Post by shauns on 2007-06-01
I did the kernel update and everything seems fine with me.

---

### Post by JoePits on 2007-06-01
> **Gustave said:**
> I had the same problem with my install.  It 'broke' on an X11 file of some sort for me.  During the text install, I was asked to choose a resolution.  My second time through, the only one I chose, other the the default ones, was 1280x800 (native resolution for my laptop) and the install went through fine.

I have no idea if this will help ya at, all, but I thought I'd mention it.

hey this happened to me last night and i figured out by going to the other consoles that it was trying to download stuff, so i think it kind of requires an internet connection at 85%

---

### Post by lifeempowered.com on 2007-06-04
the kernel upgrade shouldn't break anything.  and by the way, the script now includes Travino's beryl which is way cooler and is at version 3 or something, works great!  The "lamp" effect allows you to go to 0 which emulates the Genie effect of mac.  very cool. 

Oh, and i would like to know more about the bcm thing, what's this fwcutter fix?  If i can avoid using ndiswrapper, I'd love it.

Also, the new script does NOT install vmware, it just does automatix with which you can do vmware player or server.

Cheers!

---

### Post by trashjedi on 2007-06-04
Hello there. I haven't tried the script install yet, but I was wondering how I could get it to work since I am on a university network, and I need to set a proxy server before being able to connect to the Internet. 
How can I set the proxy with the command line so that I can download the script and install Feisty?

Thanks a lot.

---

### Post by lifeempowered.com on 2007-06-04
> **trashjedi said:**
> Hello there. I haven't tried the script install yet, but I was wondering how I could get it to work since I am on a university network, and I need to set a proxy server before being able to connect to the Internet. 
How can I set the proxy with the command line so that I can download the script and install Feisty?

Thanks a lot.

Hmm, do you already have access to a proxy server?

The most effective way I've found of using a proxy is the following scenario:

Ubuntu Server running ssh + squid.

You ssh to squid for all your http traffic like this on the command line:

sudo ssh -L 8080:localhost:3128 yourproxy.com -l sshuser -p 22

You can change the -p to be 443 and make sure your proxy server is set to listen for SSH on port 443 if your network blocks ssh port 22.  Then when squid is setup, just make sure it's listening on port 3128.  Finally, in your browser or on your machine, set it to forward all port 80 traffic to localhost port 8080.

I use this configuration all the time.  It also makes your DNS requests go through the proxy server rather than the location you are at, which is really nice and secure.  I run my SSH over port 443.  

Hope this helps!

By the way, the script was just updated to avoid using ndiswrapper and instead use the fwcutter route.  Seems to work.  I'll keep it updated as needed.  I'll also do a little step by step for those who want to do just 1 or 2 steps.

---

### Post by misos on 2007-06-06
How can I remap the multimedia keys, I want to use them with Exaile? MediaDirect opens Rhytmbox, while Play, Stop, Back and Forward do not work.

---

### Post by lifeempowered.com on 2007-06-06
> **misos said:**
> How can I remap the multimedia keys, I want to use them with Exaile? MediaDirect opens Rhytmbox, while Play, Stop, Back and Forward do not work.

Easy, 

System > Preferences > Keyboard Shortcuts

Then find the thing you want and click it, next press the media key you want to control that.

Done!

---

### Post by designer17 on 2007-06-06
I followed the instructions and beryl worked fine for about 5 mins then the window bars(the part that has the minimize and exit buttons) around the open windows disappeared and I can no longer minimize anything and none of the beryl effects work now.  The systems appears to be rather slow now.  Not really sure what happened or how to fix this.  The only thing I really did before this happened was try and set up multiple desktops so I could use the 3D cube, which I never got working.  So does anyone have any idea as how to fix this?  One last question,  after I followed the instructions and got ubuntu boot up the update manager said there were somewheres around 7-9 new updates all related to beryl being installed.  Is it ok to install these updates?
Thanks in advance.



Acer TravelMate 4670
Intel Core Duo T2500
Ati Radeon X1400
120gb sata hd
2gb DDR2 ram

Ubuntu is running off of a 120gb 2.5" external usb scsi hd(very smoothly I might add, besides the whole beryl thing)

---

### Post by lifeempowered.com on 2007-06-07
> **designer17 said:**
> I followed the instructions and beryl worked fine for about 5 mins then the window bars(the part that has the minimize and exit buttons) around the open windows disappeared and I can no longer minimize anything and none of the beryl effects work now.  The systems appears to be rather slow now.  Not really sure what happened or how to fix this.  The only thing I really did before this happened was try and set up multiple desktops so I could use the 3D cube, which I never got working.  So does anyone have any idea as how to fix this?  One last question,  after I followed the instructions and got ubuntu boot up the update manager said there were somewheres around 7-9 new updates all related to beryl being installed.  Is it ok to install these updates?
Thanks in advance.



Acer TravelMate 4670
Intel Core Duo T2500
Ati Radeon X1400
120gb sata hd
2gb DDR2 ram

Ubuntu is running off of a 120gb 2.5" external usb scsi hd(very smoothly I might add, besides the whole beryl thing)

You should be ok to install the updates.

As for the other issue, it's an easy fix and shouldn't happen ever again...

Right click the maroon Beryl icon and click "Reload Window Manager"

That should do the trick.

---

### Post by designer17 on 2007-06-07
I clicked on the "Reload Window Manager" and it didn't fix it.  Every application that I open, opens up with out the window bar at the top.  I still cannot minimize any open windows and I can't exit anything unless I click file then click close.  I also cannot move any of the open windows around on my screen.  None of the open apps appear  on the bottom task bar either.  I am completely lost as to why everything worked for about 5 mins then stopped.  I would really like to get this working.  I have tried getting it working for almost 3 weeks now using other tutorials that I have found online.  I never dared to try this tutorial because it said it was for a Dell and I was unsure if it would ruin my system.  Yesterday I gave in and decided it to give it a try.  I was so excited when  I booted my machine up and beryl was running but after 5mins my excitement was lost.  So any help would be greatly appreciated.

---

### Post by lifeempowered.com on 2007-06-07
> **designer17 said:**
> I clicked on the "Reload Window Manager" and it didn't fix it.  Every application that I open, opens up with out the window bar at the top.  I still cannot minimize any open windows and I can't exit anything unless I click file then click close.  I also cannot move any of the open windows around on my screen.  None of the open apps appear  on the bottom task bar either.  I am completely lost as to why everything worked for about 5 mins then stopped.  I would really like to get this working.  I have tried getting it working for almost 3 weeks now using other tutorials that I have found online.  I never dared to try this tutorial because it said it was for a Dell and I was unsure if it would ruin my system.  Yesterday I gave in and decided it to give it a try.  I was so excited when  I booted my machine up and beryl was running but after 5mins my excitement was lost.  So any help would be greatly appreciated.

Using that same menu, try ensuring that beryl is being used.  Check in "Select Window Manager" and "Select Window Decorator" that both are using Beryl.

---

### Post by MR Bacardi on 2007-06-13
I can't make it work with 64-bit base system.
There is no avant-window-navigator or beryl-vidcap available for AMD64 architecture.
I did manage to manually install avant-window-navigator.
Beryl-vidcap I tried to install, I found it in a third party repository. However, it was called beryl-plugins-vidcap and therefore the dellinstall would not continue.

I could not find anyone else talking about 64-bit version, could I really be the only one trying to use it? Or did I do something wrong?

---

### Post by lifeempowered.com on 2007-06-13
> **MR Bacardi said:**
> I can't make it work with 64-bit base system.
There is no avant-window-navigator or beryl-vidcap available for AMD64 architecture.
I did manage to manually install avant-window-navigator.
Beryl-vidcap I tried to install, I found it in a third party repository. However, it was called beryl-plugins-vidcap and therefore the dellinstall would not continue.

I could not find anyone else talking about 64-bit version, could I really be the only one trying to use it? Or did I do something wrong?

It's possible that you are the only one:)  But then again, anything is possible!  So, here's what you do...after running the first Dellinstall script, right after it reboots and BEFORE typing it again, go into the /install directory and locate a script called "b"  Use nano to edit it and locate the lines in that script you need changed.  Change them, save it, and run dellinstall for the second time.  That should work.

---

### Post by Clydez on 2007-06-14
Dear All,
I would like to install **k**ubuntu on my dell 6400. 

Can I use simply the same scripts posted on first page or are other steps I should be aware of?

Thankyou,
Clyde.

---

### Post by boheme on 2007-06-14
> **MR Bacardi said:**
> I can't make it work with 64-bit base system.
There is no avant-window-navigator or beryl-vidcap available for AMD64 architecture.
I did manage to manually install avant-window-navigator.
Beryl-vidcap I tried to install, I found it in a third party repository. However, it was called beryl-plugins-vidcap and therefore the dellinstall would not continue.

I could not find anyone else talking about 64-bit version, could I really be the only one trying to use it? Or did I do something wrong?

Hi. I have the same problem. I've installed the 64bit version, and beryl doesn't works. I get the "can't find avant-window-navigator package". If i remove the line that installs avant-window-navigator I get the same error with "beryl-vidcap" and the same with "seom"

Removing both beryl-vidcap and seom doesn't works.

What can I do?

Thanks in advance, and greetins for those great scripts!

PD: Just one question: Why nearly everybody of us has installed the 32bit version in a 64bit machine?

---

### Post by MR Bacardi on 2007-06-15
> **boheme said:**
> Hi. I have the same problem. I've installed the 64bit version, and beryl doesn't works. I get the "can't find avant-window-navigator package". If i remove the line that installs avant-window-navigator I get the same error with "beryl-vidcap" and the same with "seom"

Removing both beryl-vidcap and seom doesn't works.

What can I do?

Thanks in advance, and greetins for those great scripts!

PD: Just one question: Why nearly everybody of us has installed the 32bit version in a 64bit machine?
I have now tried too.
I can make it install after having changed things in a and b scripts, but without:
beryl-vidcap, seom and Hardware Monitor (i8kutils etc.)

However, Beryl does not work. I seems that beryl-manager is not a part of the beryl package and neither is beryl-xgl.
Beryl-manager I could just install through apt-get and should therefore not be any problem.
Beryl-xgl is not a part of beryl-core 0.2.1 which I got installed.
On my 32-bit (installed with the original script) I have beryl-core 0.3.0-svn - I believe this is the key issue so I will try to find the beryl-core 0.3.0-svn for AMD64 and make it a part of my edited script.

---

### Post by agoldfinger on 2007-06-20
Hello,

I'm totally new to Ubuntu and Linux. I've downloaded Ubuntu 7.04 desktop  today and installed it on my Dell Inspiron 6400 machine. The graphic desktop loaded with no problems at all.
Should I still follow the instruction in this thred or do Ubuntu have everything supported "out-of-the-box" in this version?
Should I follow only certain steps?

Thank you,
Avi

---

### Post by guillepb on 2007-06-21
This tutorial worked great for me and I've been enjoying feisty with beryl for a couple of months now, however I can't get google earth to run with Beryl and I guess it has to do with those errors some other guys have reported here in this thread:

this is the output of my fglrxinfo:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)


this is part of the output of glxinfo:

> name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No


and this is the error I get when running googleearth:

> Xlib:  extension "XFree86-DRI" missing on display ":1.0".


Any ideas on how I can fix this? And why the discrepancy on the display numbers from glxinfo and fglrxinfo?

Thanks a lot for your help.

---

### Post by trashjedi on 2007-06-21
Have you tried running google earth with a normal gnome session (not an xgl/beryl one) ?

---

### Post by guillepb on 2007-06-21
Yep, and it works perfectly.

---

### Post by Vulcan on 2007-06-21
For some reason I tried to do this, but when I tried to do Script 3, I can't get into my X Session?

---

### Post by slugicide on 2007-06-22
Avi, this is for fancy eye candy.  If you like the way things look right now, you're sitting pretty!

---

### Post by slugicide on 2007-06-22
> **Clydez said:**
> Dear All,
I would like to install **k**ubuntu on my dell 6400. 

Can I use simply the same scripts posted on first page or are other steps I should be aware of?

Thankyou,
Clyde.
Clyde, I think there are some differences in the apps that would be called on.  Like Kate instead of Gedit.  You should ask someone who knows more than me, though.

---

### Post by agoldfinger on 2007-06-22
> **agoldfinger said:**
> Hello,

I'm totally new to Ubuntu and Linux. I've downloaded Ubuntu 7.04 desktop  today and installed it on my Dell Inspiron 6400 machine. The graphic desktop loaded with no problems at all.
Should I still follow the instruction in this thred or do Ubuntu have everything supported "out-of-the-box" in this version?
Should I follow only certain steps?

Thank you,
Avi

Wireless network and screen resolution were not detected out of the box. I tried this .dellinstall script - and the result - I had to reinstall ubuntu after X wouldn't load and I couldn't get the command line.

I tried all kinds of HOW-TO's described here, but the only one which worked is :
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

It got my wireless working right away.

Plus I installed the 915 driver from the package manager and it fixed the resolution.

Thanks! ;)

---

### Post by slugicide on 2007-06-22
The beryl script didn't work for me.  Linux* is so much work.*

---

### Post by jamigre on 2007-06-23
um.... how am i supposed use a wget command from the web, when I cant connect to the net from the live cd?

---

### Post by MR Bacardi on 2007-06-23
> **jamigre said:**
> um.... how am i supposed use a wget command from the web, when I cant connect to the net from the live cd?
You can use a cabled connection, but are you sure you can not access the Internet?
I was able to use both cabled and wireless without using the scripts, though I did an install right away with the Alternate CD.

---

### Post by djremix71 on 2007-06-23
First off, thank you so much lifeempowered. This is a killer guide, which worked great. But, I have one problem. My dell load right into GNOME + XGL no problem. But, beryl doesn't show any window boarders. No close button, no minimize, nothing. I have tried reinstalling beryl, and everything to no avail. Anyone got any suggestions.

---

### Post by jamigre on 2007-06-23
> **MR Bacardi said:**
> You can use a cabled connection, but are you sure you can not access the Internet?
I was able to use both cabled and wireless without using the scripts, though I did an install right away with the Alternate CD.

I'll give it a go, but my wireless, and my router need a password to gain access, and I know nothing of linux prompt commands. regardless. i'll try connecting via cable tomorrow.

---

### Post by lifeempowered.com on 2007-06-25
Whew!  So many questions!  Where to start...Hmmm.  

Ok, first off, many of you are referring to questions that are related to hardware NOT listed in my config.  Sorry, but I did this whole guide based off my hardware.  If you would like to find a way for it to work with your hardware, then submit the working method to me, I can create scripts for each hardware set.  That would be cool!

Next, this is not a Kubuntu guide.

And finally, if you choose to do the "one script at a time" method rather than the full script install, expect some errors.  It's not perfect yet.  The best bet is to follow the full install guide.

I'm planning on obtaining the latest copy of Ubuntu and doing a fresh install this week to find any new problems and resolve them in the scripts.  You can stay updated via my blog: [http://mylittleubuntuguide.com](http://mylittleubuntuguide.com)

Thanks all!

John

---

### Post by lifeempowered.com on 2007-06-26
Ok, here's the deal.

I'm really interested in making the script workable on all Dell laptops.  So here's my petition:

Send me your laptop specs and what you did to get it working.  I will in turn, create a script for your specific laptop!

---

### Post by lifeempowered.com on 2007-06-27
> **agoldfinger said:**
> Wireless network and screen resolution were not detected out of the box. I tried this .dellinstall script - and the result - I had to reinstall ubuntu after X wouldn't load and I couldn't get the command line.

I tried all kinds of HOW-TO's described here, but the only one which worked is :
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

It got my wireless working right away.

Plus I installed the 915 driver from the package manager and it fixed the resolution.

Thanks! ;)

It sounds like you have a totally different configuration.  Can you please outline what it is?  e.g. cpu, video card, sound card, wireless card, LAN card, etc...

---

### Post by Hyrup on 2007-07-03
Your site is down, I cannot use the scripts!#-o

---

### Post by lifeempowered.com on 2007-07-03
Hmm, must have been a "hiccup" as I see it up.

---

### Post by Hyrup on 2007-07-03
Working now:popcorn:

---

### Post by FireeLizard on 2007-07-03
During “dellInstall” script i am getting a problem:

Message says

Resolving [www.getautomatix.com](www.getautomatix.com)... 216120.255.9
Connecting to [www.getautomatix.com](www.getautomatix.com)... 216120.255.9: :80… connected.
HTTP request sent, awaiting response… 404 Not Found
ERROR 404: Not Found

Please help :KS

---

### Post by FireeLizard on 2007-07-03
Dear lifeempowered.com :)
I used your Script before (month ago) and it worked Nice !!!
Dell 1505
ATI X1400
But wireless 3965 (Intel)

Today when i tried to install "dellinstall" script - i got this message:

...

Resolving [www.getautomatix.com](www.getautomatix.com)... 216120.255.9
Connecting to [www.getautomatix.com](www.getautomatix.com)... 216120.255.9: :80… connected.
HTTP request sent, awaiting response… 404 Not Found
ERROR 404: Not Found

...
Can it be a pronlem with a site or files update?
Thank you

---

### Post by lifeempowered.com on 2007-07-04
It's the Automatix site having an issue.  I'll look into it.

---

### Post by Brewster123 on 2007-07-04
Looks like the file requested in the script is no longer available on the automatix server.  When you look in the directory they must have updated the files and eliminated the one the script calls for...

automatix2_1.1-4.5-7.04feisty_i386.deb

at

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/)

(only 4.7, 4.8 and 4.9 versions now)

Hopefully a "simple" matter of updating the install script ... and that from a total newbie.  

I get the same error on my Dell 6400 install too.

Cheers and thanks in advance.

---

### Post by chamaz on 2007-07-04
hello, im from sudamerica so sorry if my english is not so good.
i use the script many times, and all that times is a succesful instalation,  instalation witout problems. But now i reistall ubuntu end the script doesnt work for me, i tried to make it work but i cant,... i read every post in here for try to resolve my problem but i cant, the previous post say that for fix the problem i have to change the script, but i dont know how., every time the script send me the error of automatix error 404

please if any can tell me , step by step how i cant make work the script il be very very happy.
thanks 
bye bye
tomas

---

### Post by lifeempowered.com on 2007-07-04
Ok all, sorry for the slight delay...4th of July party!  Anyway, got the script updated with the Automatix fix.  I'm going to find a better solution to this for the future so it doesn't happen again...

Happy 4th!

---

### Post by Hyrup on 2007-07-04
> **FireeLizard said:**
> Dear lifeempowered.com :)
I used your Script before (month ago) and it worked Nice !!!
Dell 1505
ATI X1400
But wireless 3965 (Intel)

Today when i tried to install "dellinstall" script - i got this message:

...

Resolving [www.getautomatix.com](www.getautomatix.com)... 216120.255.9
Connecting to [www.getautomatix.com](www.getautomatix.com)... 216120.255.9: :80… connected.
HTTP request sent, awaiting response… 404 Not Found
ERROR 404: Not Found

...
Can it be a pronlem with a site or files update?
Thank you

Not working here either

---

### Post by chamaz on 2007-07-04
but can i do something to fix the script...or i have to wait to mylittleubuntuguide release a new one?

---

### Post by MR Bacardi on 2007-07-05
> **chamaz said:**
> but can i do something to fix the script...or i have to wait to mylittleubuntuguide release a new one?
The current release from mylittleubuntuguide contains a name for a valid deb package.
So I think the problem has been solved?
Try downloading the dellinstall script again.

---

### Post by lifeempowered.com on 2007-07-05
Yes, all, the problem is fixed and I do apologize for the inconvenience!  I'm currently writing a new script that will  install automatix from the repos instead of downloading.  The reason we were relying on downloading a deb package was due to an error when installing the key for the repos to work.  The script would quit unexpectedly.  But, I think I've almost solved this and will be testing it shortly.  Once that is fixed I'll be moving the entire script in this direction: Using repositories over debs.  

Thanks to all of you who alerted me to this error as quickly as you did!  You'll need to download a fresh copy of the dellinstall script to get the fix.  

Let me know of any further issues please!  And happy independence day everybody!

:popcorn:

---

### Post by FireeLizard on 2007-07-05
Thank you Jhon,
Everything is working now :)

Can you tell us more detailes about scripts#   2, 6, 8?
I did not run these scripts (Just "dellInstall" and "Beryl" :) - 1,3,4), but i want to now more about it.

Thank you one more time for your help :KS

---

### Post by lifeempowered.com on 2007-07-05
Ok everyone, the new script is created and should work great.  Let me know if it doesn't.  It will now do Automatix using the repos so in the future as they update, it shouldn't break our script.

---

### Post by lifeempowered.com on 2007-07-05
> **FireeLizard said:**
> Thank you Jhon,
Everything is working now :)

Can you tell us more detailes about scripts#   2, 6, 8?
I did not run these scripts (Just "dellInstall" and "Beryl" :) - 1,3,4), but i want to now more about it.

Thank you one more time for your help :KS

No problem, check the first post again, I updated it.

---

### Post by glosman15 on 2007-07-08
I am doing the step by step script installation, and am only choosing to install

update
video
automatix
wifi

everything works fine until i get to the wifi step, i followed all the proper instructions and it popped out this when i typed sudo ./wifi

dkpg: error processing bcm43xx-fwcutter_006-1_i386.deb  (--install):
cannot access archive: no such file or directory
Errors were encountered while processing:
bcm43xx-fwcutter_006-1_i386.deb
rm: cannot remove 'bcm43xx-fwcutter_006-1_i386.deb ': no such file or directory


I am extremely new to ubuntu and linux in general, I have reinstalled numerous times but nothing has fixed this, I tried the full script install too and my wireless didnt work that way either.  Can someone please assist me? I would be extremely grateful.

EDIT: nevermind, I made a stupid mistake.  It's working properly now.

---

### Post by lifeempowered.com on 2007-07-13
Just successfully created a custom Live CD with ATI support.  I have a how-to with scripts for you to automate at my website mylittleubuntuguide.com.  It creates an ISO that's over 1 gig, so it's got to be put on a DVD or USB.  Anyway, the reason it's so big is I went all out and made it so it has all the multimedia stuff, VMWare, etc.

Hope this helps someone out there!

:popcorn:

---

### Post by GreyShadow on 2007-07-15
It worked!
 Just a minor blip..on step 7 had to
 sudo chmod +x dellinstall
./dellinstall 
not just ./dellinstall for all to work.
Your method ends _much_ frustration on getting the ati graphics to work. Thank you so much for your efforts. My Dell laptop has the same specs. as yours.:) The only thing left is to get the cube effect going.

---

### Post by lifeempowered.com on 2007-07-18
Ok, it's official!  

I got the LIVE CD customized the way I want it.  So instead of an install script or process, you just use this nifty Dell 6400 Live DVD, install, run the "FinishUp" script when you login to the new system and WALLA!  All the applications are there already, your sources.list file works, and your system is upgraded!

This is so freakin great!

It is a big download if you choose to get the ISO, about 1.3Gigs, but saves a ton of time in the long run.  Or you can create your own custom Live CD/DVD using my how-to on my blog.

I also wrote out a script that you are welcome to use in my How-To for installing everything into a Live DVD to "mimic" what my iso is.

The ISO will be uploaded and available for download on my blog by tomorrow at 12 PM EST.  

Later!

---

### Post by PePeR34GTR on 2007-07-20
So let me get this straight, I plug in my ethernet cord into my laptop, boot it from the disc, and follow all the steps directly from the first page.

Only thing Im confused about is when he types out a code and puts a url there, am I supposed to go to that url and print out the code, or will the comp pick it up by itself while plugged in via ethernet.

Thanks in advance

---

### Post by -Dan on 2007-07-20
Hello,

I tried your ./dellinstall before and it was working.
Then I tried to reinstall my ubuntu and somehow you have updated with ./dellinstall2

Somehow I got a problem with it.

I got this error:

Your session only lasted less than 10 seconds........
Then the ~/.xsession-errors file is

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdmPreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/lib/gdm:0.Xservers" -h " " -l ":0" "myusername"
/etc/gdm/Xsession: Beginning session setup...
Could not create gnome accelerators directory `/home/myusername/.gnome2/accels': Permission denied

Any help for this? Since I am totally newbie with this thanks.

Edited:
I found out that this was not the script installation problem. Somehow my directory is belong to root instead of myself. So I change the owner of the directory to myself and it works.

---

### Post by lifeempowered.com on 2007-07-20
Ok everyone, there was an issue with the bcm43xx-fwcutter install where it wasn't working correctly.  I've updated the scripts, all of them, using ndiswrapper.  

Yes, the Dellinstall script is different, cleaner really.

Here's how it works:

1st you download the dellinstall script, chmod it and run it as "sudo":
sudo ./dellinstall

2nd, after the reboot, you will run dellinstall2 (NOTICE THE "2") as "sudo":
sudo ./dellinstall2

That's it, everything should work, I've tested and works perfectly!

---

### Post by -Dan on 2007-07-20
Perhaps my mistake :) 

I will reinstall again then .... that's the fun part of learning :)

Also I just figured out that I need to edit dellinstall2 too. Since it contains some extras too.

Thank you very much John for helping me with this dell 6400... It's a big step for me to learn linux :)

---

### Post by lifeempowered.com on 2007-07-20
Ok, currently uploading a new files.tar.gz, so things won't work for the next 15 min.

Alright...all done!  Everything should work now.  Please report bugs/errors!  Thank you!

Again, make sure you run everything with "sudo" in front of it!

---

### Post by -Dan on 2007-07-20
Thanks... I will give it try to my fresh ubuntu installation again.

Finger cross.

---

### Post by lifeempowered.com on 2007-07-20
Everyone, please also note that the 2nd script, dellinstall2, is run from the same location as the first.  So when you login, there is no need to change directories, just run it.

---

### Post by PePeR34GTR on 2007-07-20
After step 6 when the first dellinstall does its installing then reboots, I go back into the cmd prompt to type sudo ./dellinstall2  and it asks for my password, then I it tells me the command is not found.

So then I type sudo -i to get into root, and try it again, and command not found again.

Help please.


*Edit*  If I happen to do a reinstall of the entire thing, cause it looks like you updated stuff, do I have to delete anything or do I just run the new commands and the files overwrite and add whatever needs to be added?

Thanks in advance

---

### Post by lifeempowered.com on 2007-07-20
> **PePeR34GTR said:**
> After step 6 when the first dellinstall does its installing then reboots, I go back into the cmd prompt to type sudo ./dellinstall2  and it asks for my password, then I it tells me the command is not found.

So then I type sudo -i to get into root, and try it again, and command not found again.

Help please.


*Edit*  If I happen to do a reinstall of the entire thing, cause it looks like you updated stuff, do I have to delete anything or do I just run the new commands and the files overwrite and add whatever needs to be added?

Thanks in advance

I'd remove the "install" directory.  Also, ensure that you are in your home directory when you do everything.  To make sure, after logging in just type:
cd ~/

Then continue.

Also, you may need to do the following to make dellinstall2 executable:

sudo chmod +x dellinstall2

Hope this helps!

---

### Post by PePeR34GTR on 2007-07-20
I did a reinstall of the dellinstall, it works now, Im on the serial number forvmware now, thanks man! :)

---

### Post by lifeempowered.com on 2007-07-20
Excellent!  BTW, I'm having trouble with Beryl.  It appears that the repo is down.  I'll have to work on it later.

---

### Post by azntfl on 2007-07-21
I am trying to setup using the individual scripts but the first one is not working.  Here is what I get:

> root@TFL:/home/thomas# sudo ./update
--05:00:07--  [http://www.mylittleubuntuguide.com/files/sources.list](http://www.mylittleubuntuguide.com/files/sources.list)
           => `sources.list'
Resolving [www.mylittleubuntuguide.com](www.mylittleubuntuguide.com)... 64.111.124.212
Connecting to www.mylittleubuntuguide.com|64.111.124.212|:80... connected.
HTTP request sent, awaiting response... 404 
05:00:08 ERROR 404: (no description).

root@TFL:/home/thomas# 

---

### Post by jtwhitford on 2007-07-21
Thanks for the great help!!! As a first-time linux user, I would never have gotten Ubuntu running without this guide!

Now, running the dellinstall2 (as well as the individual beryl script), my script is freezing on the following line:
```
Setting up google-desktop-linux (1.0.1.0060) ...
```
I had left my laptop running the script overnight and woke up to this. So I decided to run the beryl script by itself, with the same results.

Any clues?

---

### Post by lifeempowered.com on 2007-07-21
> **azntfl said:**
> I am trying to setup using the individual scripts but the first one is not working.  Here is what I get:

OOOOPS!  Sorry, I deleted the file sources.list by accident!

It's back now.

---

### Post by lifeempowered.com on 2007-07-21
> **jtwhitford said:**
> Thanks for the great help!!! As a first-time linux user, I would never have gotten Ubuntu running without this guide!

Now, running the dellinstall2 (as well as the individual beryl script), my script is freezing on the following line:
```
Setting up google-desktop-linux (1.0.1.0060) ...
```
I had left my laptop running the script overnight and woke up to this. So I decided to run the beryl script by itself, with the same results.

Any clues?

Hmmm, don't know but I'll look into it.  I'm pretty busy today with family, but I'll try to clean everything up before the weekend is over.  And the ISO is not ready yet, sorry everyone, but almost.  When it is I'll upload it and you won't need to do the install guide, just download the ready made ISO that does everything for you!  It should be done and working by Tuesday the latest.  Follow along on my blog at [www.mylittleubuntuguide.com](www.mylittleubuntuguide.com)


UPDATE: Actually, that's the very last program in the list for the script to install.  It could be that the script did install it but did not reboot your pc.  Just reboot and see what happens.  My guess is everything works.

---

### Post by jtwhitford on 2007-07-21
Well, it didn't. However, I decided to go ahead and re-run the dellinstall and dellinstall2 scripts.  Seeing as they have apparently changed since I first ran just dellinstall.  I'll post results! 


**EDIT:** It works! I ran through both updated scripts, and logged in under gnome xgl, and its seamless.  Certainly beats my Windows box's "Window Blinds" (or something like that) to a pulp.  Yipee!

Thanks so much again!
Bless God,
God Bless.
Todd.

---

### Post by jtwhitford on 2007-07-21
Only my WiFi doesnt work.  The Network Manager shows my Wireless network (ie. Pink Fluffy Bunny [don't ask]), but will not connect to it. Not in roaming, or even when I specify that network with all my credentials etc.

I'm not sure about that one, but Beryl works great.

---

### Post by lifeempowered.com on 2007-07-21
> **jtwhitford said:**
> Only my WiFi doesnt work.  The Network Manager shows my Wireless network (ie. Pink Fluffy Bunny [don't ask]), but will not connect to it. Not in roaming, or even when I specify that network with all my credentials etc.

I'm not sure about that one, but Beryl works great.

Ok, first leave it on roaming mode.  When you start screwing around with that things can get muddled.  Here's what you do.

1. Change it back to "Roaming Mode".
2. Turn WiFi off in the Network Manager by Right Clicking the panel icon and unchecking "Enable Wireless".
3. Reboot.

That should get it back to normal.

Now, if your router is running in G Only mode that may be an issue, not sure as I haven't tried that.  The other thing I'd check is the type of key your network requires.  Is it WEP?  I'd go with WEP first to ensure that works before trying WPA.

Let me know.

PS: Yes, the scripts have been updated and I've also created a Live DVD that works like a charm, avoiding all the self-install steps.  You just boot from it, click install, and when it finishes and you login to the new system you run a script called "FinishUp" that's on the Desktop.  It disappears and you reboot.  Then the system is complete!  Very cool and simple.

You can read about it on my blog.  mylittleubuntuguide.com.  

I'll upload the ISO later this weekend. 

I'm also going to start shipping pre-made DVDs to anyone that wants one.

---

### Post by jtwhitford on 2007-07-21
Thanks for the info!

What I wound up doing, is following a tutorial that I found here: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902), using my own .inf and .sys files (from my windows partition @ C:/drivers/network/ where in one of the folders here, I grabbed the bcmwl5 inf and sys files)

Works like a dream now! Well, I may not get the full bars connection like I can with Windows, but I have a 56% connection at least. 

I believe that the problem was as noted in the above thread:
> Problem 1
Totoro found a fix for the eth1 problem. Thank You Totoro!
add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
Code:
```

sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab

```

I *think* the Network Manager couldn't couldn't use my WiFi card correctly b/c the /etc/iftab file was referencing it as eth1 rather than wlan0. Maybe?
Either way, its working now.
sw33t!

Bless God,
God Bless.
Todd.

---

### Post by lazydrumhead on 2007-07-21
I am having a problem similar to Dan's

When I try and log in, the errors file tells me "Could not create gnome accelerators directort '/home/username/.gnome2/accels : Permission denied"

I don't particularly understand your explanation (Dan) How specifically do I fix this?

---

### Post by jtwhitford on 2007-07-21
Correction on my last post. Now, after some hours and a reboot, my wireless network isn't even showing up anymore... Ugh. Lol. Anyway. Just an update.

---

### Post by azntfl on 2007-07-21
> **lazydrumhead said:**
> I am having a problem similar to Dan's

When I try and log in, the errors file tells me "Could not create gnome accelerators directort '/home/username/.gnome2/accels : Permission denied"

I don't particularly understand your explanation (Dan) How specifically do I fix this?

I have the same problem also:(

---

### Post by lazydrumhead on 2007-07-21
ahhh well I fixed it by doing this:

open a terminal session then do

sudo chown *username* /home/*username*/.gnome2



...it runs, but now I can't get any programs to load!

EDIT: every program EXCEPT firefox loads! :( :( :(

---

### Post by PePeR34GTR on 2007-07-22
I am getting that error aswell when tryin to log in, the "could not create gnome accelerators directory.."

Although I would like to hear from "lifeempowered.com", cause he made this thread with the guide, so :P

Please post with a solution and instructions on how to fix it, appreciate it :)

Thanks in advance!

---

### Post by lazydrumhead on 2007-07-22
well....what I did worked fine...did you not read it or do you not have faith in my answer :-p ?

---

### Post by PePeR34GTR on 2007-07-22
Well you said Firefox didnt work :P

And it's just me, I like to make sure of things, and since lifeempowered.com made this guide, a solution from him would be comfortable for me. It's no offense to you :)

Also, do the computer fans work from this guide?

And how do I get the computer LEDs to show up?

---

### Post by jtwhitford on 2007-07-22
> **lifeempowered.com said:**
> Ok, first leave it on roaming mode.  When you start screwing around with that things can get muddled.  Here's what you do.

1. Change it back to "Roaming Mode".
2. Turn WiFi off in the Network Manager by Right Clicking the panel icon and unchecking "Enable Wireless".
3. Reboot.

That should get it back to normal.

Now, if your router is running in G Only mode that may be an issue, not sure as I haven't tried that.  The other thing I'd check is the type of key your network requires.  Is it WEP?  I'd go with WEP first to ensure that works before trying WPA.

Let me know.
Well, seeing as my WiFi isn't working anymore (not even showing the network), I tried your suggestion. Unfortunately, it doesn't work.

1. My router isn't running in G Only mode, but, looking in the configuration, it has a feature called "Super G with Dynamic Turbo" enabled. I don't know what that does, but I thought I would just put that in. 

2. My router's security is set to: "WPA2-Auto Wireless Security".   I'll go back and try it set to WEP.

Well gtg. Lunch time here. Thanks for the help LifeEmpowered.

Bless God,
God Bless.
Todd.

---

### Post by PePeR34GTR on 2007-07-22
Where is lifeempowered.com!!?!  lol :)

---

### Post by nightlite on 2007-07-22
you are doing a great job and it wasn't until I stumbled across your post I decided to give linux a try. Beryl doesn't work yet but I am never considering windows again.

---

### Post by PePeR34GTR on 2007-07-22
> **-Dan said:**
> 

Your session only lasted less than 10 seconds........
Then the ~/.xsession-errors file is

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdmPreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/lib/gdm:0.Xservers" -h " " -l ":0" "myusername"
/etc/gdm/Xsession: Beginning session setup...
Could not create gnome accelerators directory `/home/myusername/.gnome2/accels': Permission denied

Any help for this? Since I am totally newbie with this thanks.

Edited:
I found out that this was not the script installation problem. Somehow my directory is belong to root instead of myself. So I change the owner of the directory to myself and it works.

How did you fix it exactly?

---

### Post by PePeR34GTR on 2007-07-22
Lazydrumhead, is that what you did, what Dan did?

---

### Post by HarrisonHopkins on 2007-07-22
What I did, was I installed using the Alternate install CD. After it booted, and I didn't get X to start, I ran the following;

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay=Xv
sudo shutdown -r now

After running those, your computer will restart, and X will start as well.

---

### Post by PePeR34GTR on 2007-07-22
> **lazydrumhead said:**
> ahhh well I fixed it by doing this:

open a terminal session then do

sudo chown *username* /home/*username*/.gnome2



...it runs, but now I can't get any programs to load!

EDIT: every program EXCEPT firefox loads! :( :( :(


I went to open gnome terminal session, then typed:

sudo chown pepe/home/pepe/.gnome2

Then it gave me a missing operand error.

(pepe is my login username)

---

### Post by lifeempowered.com on 2007-07-23
If I were you, I'd start fresh.  Sounds like something is totally messed up there.

---

### Post by PePeR34GTR on 2007-07-23
I gave my comp to my programming teacher and he let me login.

:)

Now, how do I config the wireless, and how do I config Beryl?

---

### Post by PePeR34GTR on 2007-07-23
Nvm, I think I got Beryl, but I cant get Firefox to open, and still dunno how to config the wireless.

*edit* is the computer fan setup with your installtion? If not, how do I config the fan.

---

### Post by lifeempowered.com on 2007-07-23
Why not run the full install script?

---

### Post by PePeR34GTR on 2007-07-23
I did run the full install, but now I dunno how to pick up wireless networks, like my home or my school.

Please tell me :)

Also, Firefox doesnt load still, how do I fix that?

---

### Post by lifeempowered.com on 2007-07-23
> **PePeR34GTR said:**
> I did run the full install, but now I dunno how to pick up wireless networks, like my home or my school.

Please tell me :)

Also, Firefox doesnt load still, how do I fix that?

Does Firefox load at all?  If it loads but crashes, could be the flash plugin.  Check for the flash plugin by doing:
sudo updatedb
locate libflashplayer*.*

If you find it in any mozilla directory, remove it.  Then open Firefox.  If it works, go to youtube and download the plugin using the browser.  

This is  a problem that was showing up in a previous version of the install script, but is fixed in the latest release.

As for the wireless, do you have WEP or WPA enabled?

---

### Post by lifeempowered.com on 2007-07-23
Ok everyone, I've rewritten both the Full Install script and the DVD install script.  They install a lot more stuff now.  Including Cinelerra (video editing).

Feel free to edit the 2nd script before running it.  It's called dellinstall2, so after you run dellinstall and the system reboots, you can do the following:
1. nano ~/dellinstall2
2. Find any app you don't want and comment it out with #
3. To save do CTRL O (that's the letter O)
4. To exit do CTRL X

Make sure you only comment out the applications you DON'T want.  

Enjoy!

---

### Post by PePeR34GTR on 2007-07-23
I dunno, but my other wireless setups on Windows, it wanted one of those, the WEP or WAP, I know I use a 10 digit number though.

---

### Post by PePeR34GTR on 2007-07-23
How bout to the new scirpt you put up, can I just run all that through Terminal?

Also on Beryl, how do I get it to do that cube thing, I open it up on Gnome with XGL and when I do the command for Unfold Cube, it zooms out, you see the current window with a window on the left and right, but I want it to do that cube thing, with the brackground.

---

### Post by PePeR34GTR on 2007-07-23
Im getting permission denied when I try to put delete it,

I getL /home/pepe/.mozilla/plugins/libflashplayer.so

Then I do: rmdir .mozilla/plugins

Then permission denied.

Btw, I think Its a WEP system for my home, for the wireless. I am not sure on the school though, you never had to setp anything with them. You just found the network and it connected.

Thanks in advance man, you're a big help.

---

### Post by lifeempowered.com on 2007-07-24
To delete it, do:

sudo rm FILENAME

---

### Post by lifeempowered.com on 2007-07-24
> **PePeR34GTR said:**
> 

Btw, I think Its a WEP system for my home, for the wireless. I am not sure on the school though, you never had to setp anything with them. You just found the network and it connected.

Thanks in advance man, you're a big help.

When you left click on the network icon on your top panel what do you see?  Do you see the name fo your network?  If so, click it.  If WEP is enabled it will prompt you for the key.  Make sure you enter it right or it won't connect.

As for the School network, I've had issues with non-secure networks connecting correctly.  It's a little bug and the fix is to keep trying to connect by clicking the network SSID in your panel's netowrk list.

---

### Post by PePeR34GTR on 2007-07-24
Ok, as for Firefox, I did the sudo rm, the file is not there, but Firefox is doing the samething.

I click on Firefox from the panel, and it opens up like an invisible window, like you can see it was execued, but there is nothing there, also, the Firefox is on the task bar when you click on it. The circular clock thing runs for 10 seconds or so, then it looks like it closes. It disapears from the taskbar. Note, when I click on it, no window appears, I still see the desktop. 

(Btw, you only wanted me to delete the "libflashplayer.so" file right?)

For the wireless, I wasnt sure which network thing you meant in the panel, I assumed the one it comes with after you install it, but when I left click it, it only gives me the option to manually configure.

---

### Post by PePeR34GTR on 2007-07-24
I think I am having major administration problems too, how do I make it so I am full admin of this system.

When I loaded opera, cause opera works, but Firefox doesnt. (I still want Firefox on my comp though please if you can help me fix that problem.)

Anyway, when I was browsing the web, it prompt me to install the flash player, but I couldnt save the file to install it on my desktop, it told me I dont have permission, and ever since I actually got to login, I been having permission issues, I wanna be able to do anything I want please.

Also, what does your 2 cores run at usualy, temperature wise. Cause ine runs at 50 Celsius usualy, and I am wondering, cause the fan never seems to go off, or is it just really quiet, not sure.

Thanks in advance man, I feel like I should be paying you.

---

### Post by PePeR34GTR on 2007-07-24
[[IMG]http://img520.imageshack.us/img520/9688/downloadtodesktoperrorzn6.png[/IMG]](http://imageshack.us)
Shot at 2007-07-24

---

### Post by Orion2000za on 2007-07-25
To get the modem to work; go to Dell's site, choose Support and Downloads.

choose the Inspiron 6400/E1505 and you find that you can set an option to see files for Ubuntu Feisty 7.04. 

One file is the deb-package for the hsf-modem built-in! 

Progress, finally... for us who want/need dial-up. :)

Sinclair

---

### Post by lifeempowered.com on 2007-07-25
> **Orion2000za said:**
> To get the modem to work; go to Dell's site, choose Support and Downloads.

choose the Inspiron 6400/E1505 and you find that you can set an option to see files for Ubuntu Feisty 7.04. 

One file is the deb-package for the hsf-modem built-in! 

Progress, finally... for us who want/need dial-up. :)

Sinclair

NICE FIND!  Thanks for the info!  I'll include it in the auto install scripts.

---

### Post by lifeempowered.com on 2007-07-25
PePeR34GTR, wow, you have some problems for sure!  I'd reinstall.

But, once you get a "normal" system, here's a quick visual guide to help you and anyone else, understand the process to getting online to the wifi.  First of all make sure you have not changed the Network Settings.  They should look like this:
[IMG]http://www.mylittleubuntuguide.com/images/screenshot1.png[/IMG]

Now, here's the steps in image format:

[IMG]http://www.mylittleubuntuguide.com/images/Screenshot.png[/IMG]

[IMG]http://www.mylittleubuntuguide.com/images/Screenshot-1.png[/IMG]

[IMG]http://www.mylittleubuntuguide.com/images/Screenshot-3.png[/IMG]

[IMG]http://www.mylittleubuntuguide.com/images/Screenshot-4.png[/IMG]

Again, my advice is to start fresh.  Format the system and follow the install guide to a "t".  Then login and test.  If it's not working don't mess with anything until you contact me!

Cheers!

---

### Post by PePeR34GTR on 2007-07-25
Do I have to do a fresh install where I boot from the Ubuntu disk and reinstall everything. Or do I just reinstall the dellinstalls from Terminal. 

Also, are your scripts from the first page, like the steps that say sudo ./dellinstall, and ./dellinstall 2, are those scripts up to date? Like do they include the Dell Support Files you found? Just lemme know if its up to date with everything before I install anything.

Also, did you get you're install file from the website? I used the Desktop i386 one. Im pretty sure thats a good one.

Here is a screenshot of what I see when I get into the Network Settings:

[[IMG]http://img255.imageshack.us/img255/5526/networksettingsun8.png[/IMG]](http://imageshack.us)
Shot at 2007-07-25


Thanks in advance!

---

### Post by PePeR34GTR on 2007-07-25
Also I noticed, cause I have Gnome with XGL as my default session, sometimes it doesnt load the Beryl setup with the cube.

And when I download a Skydome image change the Skydome image to what I downloaded, the whole Beryl thing crashes I think and doesnt work anymore, and it messes with the resolution a bit. And I cant change the windows.

---

### Post by PePeR34GTR on 2007-07-25
*Update* I didnt do any reinstall of the OS yet, nor the dellinstalls.

I got Firefox to load, but after I type out a url, it closes Firefox, or whenever I go to the preferences, it closes, but I got it to load!

Also, I changed the ownership of the desktop to me.

---

### Post by PePeR34GTR on 2007-07-25
Only thing I really need is how to config the wireless, Lets get er done please!!! :)

Can I just run both ./dellinstalls from the terminal and reinstall everything and it can overwrite the files that are already there, or do I have to reinstall Ubuntu, I dont think I have to do that though.

---

### Post by lifeempowered.com on 2007-07-25
First:
What is your system hardware config?
ATI? Dell 1390 wifi?

Second:
Yes, install from scratch, meaning to boot from the cd...etc.

Third:
No, the install script doesn't include the Dell Modem driver.  I'm not going to include any new drivers until I've tested them.

---

### Post by PePeR34GTR on 2007-07-25
Its the same setup you got I think.

Dell Inspiron 6400, with an ATI x1400 video card, anything else you need to know about the machine?

Ewww, full reinstall, takes so long! :P, alright I guess.

Question though, would if I get that error after I do the reinstall, the error that appears when you try to log in, like your session didnt last less than 10 seconds, couldnt create gnome accelerator directory, permission denied, I think it read.

What should I do then?

---

### Post by PePeR34GTR on 2007-07-25
Intel® Next-Gen Wireless-N  I believe was the card

---

### Post by lifeempowered.com on 2007-07-26
> **PePeR34GTR said:**
> Intel® Next-Gen Wireless-N  I believe was the card

Ok, found the problem...I think

The dellinstall script was creating the .gnome2 folder in your home folder which was making it be not owned by you, the same is true for the .mozilla folder.

So a big apology for that.  I didn't think about that.

That's fixed now.  The folders are created as you, as long as you run the dellinstall script WITHOUT sudo in front of it.  So, when you reinstall at the point where you download the dellinstall script, do this:

wget [http://www.mylittleubuntuguide.com/files/dellinstall](http://www.mylittleubuntuguide.com/files/dellinstall)
sudo chmod +x dellinstall
./dellinstall

Notice you run dellinstall as you.

That will do the necessary folder creation and then will run the rest of the commands as sudo.

let me know

---

### Post by PePeR34GTR on 2007-07-26
Will this fix my wireless problem? Because that is the only problem I am having right now.

My wireless is the only thing not working. The card is a Intel® PRO/Wireless 3945, I think

---

### Post by PePeR34GTR on 2007-07-26
Found this;

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I am really really really confused on how to install it though

---

### Post by lifeempowered.com on 2007-07-26
> **PePeR34GTR said:**
> Will this fix my wireless problem? Because that is the only problem I am having right now.

My wireless is the only thing not working. The card is a Intel® PRO/Wireless 3945, I think

Hmm, not necessarily.

In fact, you'll need to NOT install the broadcom driver that the script installs.  Since you're using Intel, you may have it working out of the box.  Try this:

sudo rmmod ndiswrapper
sudo gedit /etc/modules
# Remove the line that says ndiswrapper and save/close the file
sudo gedit /etc/modprobe.d/blacklist
# Remove the line that says blacklist bcm43xx and save/close the file

Now reboot and see if your WiFi works

Sorry, I don't have Intel so I'm not sure how it sets up.

---

### Post by PePeR34GTR on 2007-07-26
Ill try that before I reformat.

If that fixes it, thats all I really need, is my wireless to work

---

### Post by PePeR34GTR on 2007-07-27
Ok, I guess Ill do a clean install, I kinda messed with the wireless too much that I have no idea what Im doin anymore.

You said not to install the Broadcom drivers or whatever. How do I make it so I dont install them?

And when you say try this, do you mean type all that after it's installed w/o removing the Broadcam install thing, or with removing the Broadcam install thing?

You've been my best help so far, I really appreciate it. 

If we can just find out how to get my my wireless how to work, I will be out of your hair

---

### Post by lifeempowered.com on 2007-07-27
If your wifi is all that's screwy, no need to reinstall.  Linux is very good about being able to repair stuff.  You just need to know exactly what to do.  Which, unfortunately, I don't know since I don't use that wireless card.  Do a search for your exact card model in the forums and I'm sure you'll find something.

Sorry bout that!

---

### Post by PePeR34GTR on 2007-07-27
No problem man, and I appreciate you helpin me out :) Definetly this page will always be on my favorites lol.

If you could also take a look at that intel link I posted, it has a driver for my card for linux, but I am not really sure how to install it, can you help me out?

---

### Post by PePeR34GTR on 2007-07-27
Bah, after researching it for a bit, and finding my print out on the build of this laptop.

I have a "Intel Next-Gen Wireless-N", which is also "Intel® Wireless WiFi Link 4965AGN". And I looked at the supported cards, and mine isnt supported yet, or hasnt been added to the list.

I also found this site: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I followed the instructions where it told me I needed their "mac80211 subsystem package" first, so I began installing that, then I didnt get very far, I got to:

```
mac80211-9.0.2/origin/GIT
```

Which is after you extract the file that you get, and it gave me a "Permission Denied" error, and I couldnt continue. 

So they dont officially have a driver for my card, but it looks like Intel put a team together to get my particular card supported by linux.

I just cant get by that step, any suggestions lifeempowered?

---

### Post by kurty_77 on 2007-07-29
Hi John,

I downloaded the custom livecd iso and tried booting it on my 6400, but after i choose the first option in the menu (something about load or install ubuntu), the screen goes blank and it just hangs indefinitely. Should I choose the second menu choice (boot in safe graphics  mode) or should I try downloading the iso again?

Also, could you please post an md5 so i can check for errors before burning the dvd? 

thanks
Kurt

---

### Post by lifeempowered.com on 2007-07-29
> **kurty_77 said:**
> Hi John,

I downloaded the custom livecd iso and tried booting it on my 6400, but after i choose the first option in the menu (something about load or install ubuntu), the screen goes blank and it just hangs indefinitely. Should I choose the second menu choice (boot in safe graphics  mode) or should I try downloading the iso again?

Also, could you please post an md5 so i can check for errors before burning the dvd? 

thanks
Kurt

Download the dvd at [http://www.mylittleubuntuguide.com/files/livedvd.iso](http://www.mylittleubuntuguide.com/files/livedvd.iso)
md5 at [http://www.mylittleubuntuguide.com/files/livecd.iso.md5](http://www.mylittleubuntuguide.com/files/livecd.iso.md5)

I'd re-download it.

---

### Post by kurty_77 on 2007-07-29
thanks John, I checked the md5 and they do not match, i will re download and then update on my progress.

while i was waiting i booted a regular feisty cd and tried the ati script, and it worked great!

---

### Post by lzy2k1 on 2007-07-29
hi all, i got the same issue as pepe.

the problem is that i copied the instructions to a piece of paper before all of pepes problems so i sudo'ed the first ./dellinstall

i only tried to install it today and got the error...

well, ill do everything again... :s

ill post again when everything is ok

btw, my system is pretty much like yours

dell inspiron 6400
intel core 2 duo at T5500 1.66
atix1400
2gbs ram
dell bluetooth... intel 3945 for wirelss conections
dvd writer, 120gb hdd, etc...

Leo

---

### Post by norman_ on 2007-07-29
> **lifeempowered.com said:**
> Download the dvd at [http://www.mylittleubuntuguide.com/files/livedvd.iso](http://www.mylittleubuntuguide.com/files/livedvd.iso)
md5 at [http://www.mylittleubuntuguide.com/files/livecd.iso.md5](http://www.mylittleubuntuguide.com/files/livecd.iso.md5)

I'd re-download it.

Just downloaded the dvdiso and the md5sum didn't match. Then I noticed the string you linked to was called livecd.iso not livedvd.iso

I'll still try to burn it and boot it to see if I've got the right md5sum ( 3f5505bf90e5daf9855a8cdc1b3987d7 )

Edit: It's a no go. Downloaded once with wget, once through epiphany browser, got two different md5 and both hang right after the ubuntu logo with the orange bar that goes back and forth on a black background. 

I'll try downloading the livecd.iso that's on the server and see what that gives me.

---

### Post by lzy2k1 on 2007-07-29
it worked!

i have a running dual boot vista+ubuntu system... yaaaay

thanks man!

Leo

---

### Post by kurty_77 on 2007-07-29
Ok so I downloaded again from the link, and I checked it again with the given md5 and it failed that again and it still hangs. could someone else compare to the given md5 and let me know if it is just me? i also noticed that the md5 is "livecd.iso.md5" but the file is "livedvd.iso"

Also, as I mentioned above, I tried the regular feisty cd + ati script and it worked fine, so if I just use the steps from the scripts page on the website will I end up with the all of the features of the custom live dvd?

lastly,

could someone seed a torrent of the custom livedvd, that way it is faster to download and has built-in error checking.

thanks,

Kurt

---

### Post by kurty_77 on 2007-07-29
So i took a look at the directory and the date for the md5 file matches up with the old iso "livecd" this is why it didn't match!

I then decided to mess around with my freshly burned dvd and got it to boot to gnome by passing the vga 1024x768 command after pressing f4 at the ubuntu boot menu.

But beryl isn't working in the livecd mode, when i try to open the desktop effects window i get "the composite extension is not available" error message.

oh well, i will lnstall anyway to see what happens!

---

### Post by norman_ on 2007-07-29
Well kurty, I am happy to report that by using your trick (F4 vga 1024X768), the live cd boots perfectly, installs fine and that everything seems to work as it is supposed to. Beryl included

YAY!

---

### Post by djgaz89 on 2007-07-30
i cannot get past step 2
it says something about resolving the address?
could someone please help, was really looking forward to this version too

---

### Post by djgaz89 on 2007-07-30
anyone at all?

---

### Post by lzy2k1 on 2007-07-31
hey, i got beryl runing, with all the eyecandy and stuf,

but i cant play any 3d "demanding" games.

tremulous is unplayable, and torcs looks really uglyl.

glxinfo says i dont have direct rendering.

however, glxgears gives me more than 4000 fps.

anyone has a clue?

i have a x1400 card and i used this guide to install ubuntu.

Leo

---

### Post by d13k on 2007-07-31
7. After the system reboots X still won't start, login to the black login screen (X still errors out) and run the 2nd script:
Code:

sudo ./dellinstall2



after I run this it says command nt found

help?:confused:

---

### Post by d13k on 2007-07-31
> **djgaz89 said:**
> i cannot get past step 2
it says something about resolving the address?
could someone please help, was really looking forward to this version too

ensure you have network cable connected not WIFI and it will work fine

---

### Post by trashjedi on 2007-07-31
Some programs won't work properly with Beryl working (dunno why).

If you need to play a game or if some program opens but the window stays blank, go to the beryl menu, and select window manager, and choose Metacity (Gnome).
It should work. At least for some things.

> **lzy2k1 said:**
> hey, i got beryl runing, with all the eyecandy and stuf,

but i cant play any 3d "demanding" games.

tremulous is unplayable, and torcs looks really uglyl.

glxinfo says i dont have direct rendering.

however, glxgears gives me more than 4000 fps.

anyone has a clue?

i have a x1400 card and i used this guide to install ubuntu.

Leo

---

### Post by djgaz89 on 2007-07-31
thanks that got me installed with ease :D

---

### Post by lzy2k1 on 2007-07-31
> **trashjedi said:**
> Some programs won't work properly with Beryl working (dunno why).

If you need to play a game or if some program opens but the window stays blank, go to the beryl menu, and select window manager, and choose Metacity (Gnome).
It should work. At least for some things.

It didn't work :s.

anyone has a suggestion?

---

### Post by lifeempowered.com on 2007-07-31
UPDATE: Someone Just Created a Torrent for the Live CD version...You can get the link and instructions on installing it [here.]("http://www.mylittleubuntuguide.com/live-cd/")

Hey all

Don't understand why so many issues.  Weird.  I have no trouble.

I just did a new iso.  It's a CD and installs the main system, ATI, BCM43xx wifi, and Beryl.  Along with a couple other apps.  Just make sure after installing that BEFORE you run beryl you run the FinishUp script and reboot!  The link is on my blog:

[http://www.mylittleubuntuguide.com](http://www.mylittleubuntuguide.com) and the link is called "NEW! Custom Live CD"

Although the DVD installs all the applications in one shot, the CD presents a more reliable solution and reaches a broader audience.  If you want the same applications that the DVD installs, after the system is installed you can run Automatix2 (which is installed during the CD install) and install anything else you want.

Hope this helps you all!!

John.

---

### Post by d13k on 2007-08-01
thanks
gonna check if it works

---

### Post by d13k on 2007-08-02
i just downloaded your CD ISO and when I tried to burn it   an error occurred at 5% gonna redownload the file maybe it was corrupt ...
just informing you
and I think  your previous tutorials didn't work on me because of different version of BIOS . I am running  BIOS A17 that's the newest dell BIOS . 
What version are you running ?

---

### Post by d13k on 2007-08-02
> **lzy2k1 said:**
> It didn't work :s.

anyone has a suggestion?

why don't you run your 3D demanding games in XP or Vista that is if you have dual boot I mean Linux is okay but still not ready for games ... just sharing my advice/opinion

---

### Post by trashjedi on 2007-08-03
> **d13k said:**
> why don't you run your 3D demanding games in XP or Vista that is if you have dual boot I mean Linux is okay but still not ready for games ... just sharing my advice/opinion

Tremulous (and torcs?) is one of the few Linux playable games. What is the point of even playing those linux compatible games on windows if the whole point of them is we don't have to go back on windows to play?
I don't think it should use up a lot of resources, but I don't know much at all about linux and game support to help lzy2k1.
Is there a tremulous forum you can ask questions lzy2k1? They may know better than us.

---

### Post by lifeempowered.com on 2007-08-03
> **d13k said:**
> i just downloaded your CD ISO and when I tried to burn it   an error occurred at 5% gonna redownload the file maybe it was corrupt ...
just informing you
and I think  your previous tutorials didn't work on me because of different version of BIOS . I am running  BIOS A17 that's the newest dell BIOS . 
What version are you running ?

Lots of people have downloaded and are using it successfully, sorry you're having so much trouble!

---

### Post by lifeempowered.com on 2007-08-05
Ok everyone, I've created a CD for testing.  This is hopefully gong to solve the issue some of you have experienced with the ATI drivers, especially at higher resolutions.  The problem, as those of you who have it know well, is when booting from my normal CD it just goes to a black screen.  

So my new CD is up for testing.  Please give your feedback as you test so I can solve this issue.

Thanks! 

Find the CD for download from my blog: [http://www.mylittleubuntuguide.com](http://www.mylittleubuntuguide.com)

It's the latest blog post.

Later...

John

---

### Post by PePeR34GTR on 2007-08-05
Hey John, its me again :P

Have you gotten around making Ubuntu Fiesty work with the Intel Next Gen Wireless-N card? The Intel® Wireless WiFi Link 4965AGN

Lemme know, thanks :)

---

### Post by lifeempowered.com on 2007-08-06
> **PePeR34GTR said:**
> Hey John, its me again :P

Have you gotten around making Ubuntu Fiesty work with the Intel Next Gen Wireless-N card? The Intel® Wireless WiFi Link 4965AGN

Lemme know, thanks :)

As there were more people experiencing problems with the ATI card issue, I did that first.  It's the latest CD that's available, and I think you were one of the ones who had issues with the previous.  So this CD should fix your problem. 

As for the new WiFi card, here's what you should do sinice I can't test it without the Card on my system:

1. Install Ubuntu using the new CD at [http://www.mylittleubuntuguide.com](http://www.mylittleubuntuguide.com) (the download link is in the latest blog post)

2. After you install, log into your new system and run the "FinishUp" script.

3. After it reboots and you log in.  Open a terminal and create a new folder for your work:
```

mkdir ~/work
cd ~/work

```

4. Now download and extract ndiswrapper and your Intel 4965 drivers:
```

wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
tar -zxvf ndiswrapper-1.47.tar.gz
wget http://www.mylittleubuntuguide.com/files/4965.tar.gz
tar -zxvf 4965.tar.gz

```

5. Now follow these steps to install and configure ndiswrapper for your card:

a. Now go into the new ndis directory and make sure it's clean:
```

cd ndiswrapper-1.47
sudo make uninstall

```

b. Now make and install ndiswrapper:
```

sudo make
sudo make install

```

c. Now go into the folder where your 4965 driver files are extracted to:
```

cd ~/work/4965

```

d. Next, install the drivers using ndiswrapper:
```

sudo ndiswrapper -i w29n51.inf
sudo ndiswrapper -l

```

e. Now you can start ndiswrapper with the drivers:
```

sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

6. As a final step, add ndiswrapper to the modules that load on boot:
```

sudo gedit /etc/modules

```
Add the following line and save the changes:
ndiswrapper

That's it!

---

### Post by shauns on 2007-08-06
any chance for a compiz fusion update on the cd/dvd?

---

### Post by lifeempowered.com on 2007-08-07
> **shauns said:**
> any chance for a compiz fusion update on the cd/dvd?

Wow, I feel out of the loop! I just saw the video on it, sweet!  Ok, the answer is definately YES.  I'll get it started immediately!

Also, the new CD will have Suspend and Horizontal scrolling fixed.

---

### Post by shauns on 2007-08-07
Wow just now seeing it!?
heh let us know and we will test it out for you =)

---

### Post by lifeempowered.com on 2007-08-07
> **shauns said:**
> Wow just now seeing it!?
heh let us know and we will test it out for you =)

Yeah yeah yeah, rub it in, look, I have a lot on my plate ok?!  I don't have time to look at fancy Youtube videos of these compiz-fusion folks!  LOL, JK...yeah I'm amazed I didn't see this stuff yet.  I've been busy, but I didn't realize just HOW busy.

Anyway, just tested on my system and it works BEAUTIFULLY!  I'm creating the ISO now.  I'll do a fresh install on my system with the new ISO for testing and then upload for ya'll to download!

And again, this new ISO will also address some additional issues:

-Fixed suspend
-Fixed Horizontal scrolling on touchpad
-Fixed blank screen on Live CD boot for some ATI users

Later...:)

---

### Post by shauns on 2007-08-07
hey can you add in the new UbuntuWasher?
please tell me you heard about this!?
you know the addon that makes ubuntu wash your clothes for you?





















































=)~

---

### Post by lifeempowered.com on 2007-08-07
> **shauns said:**
> hey can you add in the new UbuntuWasher?
please tell me you heard about this!?
you know the addon that makes ubuntu wash your clothes for you?


=)~

Ha ha ha, very funny!  You are now NOT allowed to download the CD when complete.  :lolflag:

---

### Post by shauns on 2007-08-07
if you put a torrent up let me know ill seed it for you =)

---

### Post by kurty on 2007-08-07
The first alternate cd booted in live mode for me. But the wireless (Dell 1500n) doesn't seem to work, although the light is on.

Hopefully the new cd with compiz-fusion will also have this working.

John, and anyone else,

what do you think of a custom kernel? given that this is a dell 6400/1505 specific cd, the modules required in the kernel are pretty few even taking into account the options available.

Kernel compiling is one of the few things I have tried so I could help with figuring out what can be chopped, and it isn't that hard the second time! But seriouslywhat do people think?

kurt

---

### Post by lifeempowered.com on 2007-08-07
> **kurty said:**
> The first alternate cd booted in live mode for me. But the wireless (Dell 1500n) doesn't seem to work, although the light is on.

Hopefully the new cd with compiz-fusion will also have this working.

John, and anyone else,

what do you think of a custom kernel? given that this is a dell 6400/1505 specific cd, the modules required in the kernel are pretty few even taking into account the options available.

Kernel compiling is one of the few things I have tried so I could help with figuring out what can be chopped, and it isn't that hard the second time! But seriouslywhat do people think?

kurt

Hey Kurt, I like the idea.  If you can come up with a good working kernel, let me know and I'll implement it in the CD.  As for the 1500n, I'm not sure what the deal is with that.  I'll research it.  You'll probably need to use ndiswrapper.

---

### Post by kurty on 2007-08-07
Ok, my last exam is on saturday so I'll start on sunday.

as for the wireless 1500 Draft n, it is a broadcom chip, so i thought it would use the same dirver but i guess not, I'll look into that as well.

---

### Post by Pepsta on 2007-08-08
Hi all,

first post yay! Anyway would just like to add that I downloaded the "Live CD" from [http://www.mylittleubuntuguide.com/](http://www.mylittleubuntuguide.com/) and followed the steps and my I6400 is working fine!! All drivers are ok and I even have Compiz Fusion working perfectly (followed another tutorial [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)) Only thing is not sure what size the image has to be for the skydome and need to find a version of Kiba Dock and I'm set!

---

### Post by lifeempowered.com on 2007-08-08
> **Pepsta said:**
> Hi all,

first post yay! Anyway would just like to add that I downloaded the "Live CD" from [http://www.mylittleubuntuguide.com/](http://www.mylittleubuntuguide.com/) and followed the steps and my I6400 is working fine!! All drivers are ok and I even have Compiz Fusion working perfectly (followed another tutorial [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)) Only thing is not sure what size the image has to be for the skydome and need to find a version of Kiba Dock and I'm set!

Try Avant, it should be on your system if you used my CD.  It's very stable and you can adjust the size in the system configuration to your liking.  I'll post a screenshot of mine here.  Also, everyone, if you use my CD and run the FinishUp script, it should install and configure CompizFusion for you!  I've changed a few things for that to work.  So no need to go trying to do it manually, I hope.  Let me know if my script is broken please!

Thanks!

[IMG]http://www.mylittleubuntuguide.com/images/ubuntu1.png[/IMG]
[IMG]http://www.mylittleubuntuguide.com/images/ubuntu2.png[/IMG]
[IMG]http://www.mylittleubuntuguide.com/images/ubuntu3.png[/IMG]
[IMG]http://www.mylittleubuntuguide.com/images/ubuntu4.png[/IMG]
[IMG]http://www.mylittleubuntuguide.com/images/ubuntu5.png[/IMG]
[IMG]http://www.mylittleubuntuguide.com/images/ubuntu6.png[/IMG]

---

### Post by Pepsta on 2007-08-08
:oops: yep found that, Avant is great! Thanks for that, don't know why I waited so long to switch to linux it truly does rock!

 Here's my layout. :guitar:

---

### Post by strabes on 2007-08-09
> **zarmando said:**
> Hello there,
First post here.

I got Ubuntu Feisty Fawn running after a less  than friendly install.
And I didn't try to install Beryl as it seems to be more trouble than fun... I'm trying to stay a bit productive... :) 

Anyway, I'm wondering if you guys have a functionning **suspend to ram or hibernate mode**... My "suspend" doesn't resume : the screen is black and I have to power off. Which is a drag because it doesn't cleanly unmount my other partitions properly, to say the least -- I don't want to damage my Windows  partition before I make sure everything is okay with Ubuntu... So I won't even try the hibernation for now...

So, is it possible to have **a working suspend mode** ??? A laptop is not very useful if one has to "power off" / "power on" all the time. :confused: 

Thanks for any help

Z.

See the link in my profile. It's an ATI video card issue.

---

### Post by shauns on 2007-08-09
When is the cd going to be updated!? you act like you might have a life! =P

---

### Post by lifeempowered.com on 2007-08-09
> **shauns said:**
> When is the cd going to be updated!? you act like you might have a life! =P

tee hee

patience, patience.

I'm trying to finish a large project that actually pays me money right now. :)

So after running into the snag yesterday, I had to put things on hold while I troubleshoot.  I'll work on getting it uploaded tomorrow.  Really the only difference with it will be that Compiz is installed instead of Beryl.  So if you can't wait, just go to my blog and read the latest post on how to update your current system to match what the new CD will do.

Oh, by the way, the person who spoke to the issue regarding suspend not working...with my new CD and the update script on my blog, it's fixed.

---

### Post by kurty on 2007-08-09
It seems like most things are working for me now, with the exception of wireless and random compiz instability during the rain effect (beryl is still rock solid though).

So might I request that after this next update to the cd, that you try your hand at gutsy tribe 4? It was released yesterday and it looks pretty good, other than all the usual problems that your custom cd's fix.

I am going to play around starting next week with modifying the scripts to "gutsy-fy" them while I am waiting for some experiments to finish at the lab.

---

### Post by lifeempowered.com on 2007-08-10
> **kurty said:**
> It seems like most things are working for me now, with the exception of wireless and random compiz instability during the rain effect (beryl is still rock solid though).

So might I request that after this next update to the cd, that you try your hand at gutsy tribe 4? It was released yesterday and it looks pretty good, other than all the usual problems that your custom cd's fix.

I am going to play around starting next week with modifying the scripts to "gutsy-fy" them while I am waiting for some experiments to finish at the lab.

Yeah, I've been a little hesitant to attempt Gutsy, as I wanted to bring more stability to my current CD.  But let's do a vote...I'm all for trying it if the majority wants it.  So tell me what you guys want!  A simple post of "Gutsy" or "Feisty" will do.  Thanks!

---

### Post by kurty on 2007-08-10
Well I'm for gutsy, but I think you can edit the original post to make it a poll. that might allow more people to see it and vote.

---

### Post by lifeempowered.com on 2007-08-10
> **kurty said:**
> Well I'm for gutsy, but I think you can edit the original post to make it a poll. that might allow more people to see it and vote.

Good idea, i'll do that soon.

By the way, the new CD is finished and tested out perfect!  

Get it at [www.mylittleubuntuguide.com/live-cd/](www.mylittleubuntuguide.com/live-cd/)

---

### Post by dotancohen on 2007-08-11
Work on Gusty. Feisty will be outdated soon.

And just for your specs:
Dell Inspiron E1505/6400
2.0 GHz DuoCore processor
2 GB RAM
ATI X1400
1680x1050 widescreen
80 GB 7200 RPM harddrive
Intel wireless

After much mucking around I've got Beryl working in KDE with the full 1680x1050 resolution, and suspend to RAM working. I've got a lot of info here, and I'm not sure what did/did not work in getting the system properly configured. Next time I install I'll document and I'll let you know.

Note that GoogleEarth does not work. I have my old xorg.conf files from previous Ubuntu installs in which GE worked. I'll see what I can do to enable it.

---

### Post by shauns on 2007-08-11
downloading new cd now =)

---

### Post by gottferdamnt on 2007-08-18
Hi everybody.
Read this please:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

PS: I'm not the author, it's not an ad... just some informations.

---

### Post by bmdavis on 2007-08-19
How long does the DellInstall take?   I'm overseas right now for a while and only have a 56k connection, so I'm curious. The ATI one was fast, but the Dell one seems to be doing hundreds of updates, for openoffice and all sorts of stuff.  Anybody have an idea how many MB? (looks like over 250!)  

Or maybe I did something wrong?

Thanks.

---

### Post by shauns on 2007-08-26
Hey hey... i just got around to doing the new live cd.. and it installed beryl as defaul? its using it also... whats up? Shouldnt it be using compiz fusion?

---

### Post by Orion2000za on 2007-09-20
This could be old news, I have not followed this thread for some time. Dell is now providing ISO files with their Ubuntu setup on them:

[http://linux.dell.com/dru/](http://linux.dell.com/dru/)

Sinclair

---

### Post by joe64716 on 2007-09-22
Hey, I'm a total newbie, so expect dumb questions.

i installed linux ubuntu onto my dell inspiron 6400 w/ati radeon 1400, (wait for it) through wubi. i'm not sure if it makes any difference that i used wubi, i just figured it was the easiest option if i decided linux wasn't for me. in any case i have a problem. 

wubi installed ubuntu fine, but it's won't boot. i go through the paces and an error appears that there's a problem with the x server, (the gui), and then when i go to details, it simply states that there were no screens found. i don't have confidence in my cd drive, so i'm avoiding the suggestions that simply say, install the live cd!
in any case, i'm a newbie, take pity or something, because i can't think of a good reason why you'd help me, but please do.

---

### Post by Pumalite on 2007-09-22
Install an Alternate CD. (Because of your graphics; that's why you ended up without xserver in your wubi installation).

---

### Post by joe64716 on 2007-09-22
Look, i just want to know what to do to enter in code to allow ubuntu to "find" screens.

do i press ctrl+alt+F1 or alt+F4? do i need to press enter after all the code is typed in. why do some codes need to be retrieved from other sites?
break down these steps please, it's great that newbies with a bit of know-how can learn what needs to be done somehow, but more of us groundlings need annoying obvious guides to be written for us.

---

### Post by Pumalite on 2007-09-22
I know nothing about wubi.

---

### Post by joe64716 on 2007-09-22
wubi isn't important, i just need to know the steps others followed to enter in the codes provided. i just discovered aircrack, so now i really need linux to work. please help...

---

### Post by Pumalite on 2007-09-22
If what you are trying to do is to get a command line, then Ctrl+Alt+F1 will do it.

---

### Post by xlr8ed on 2007-10-09
Excellent scripts, they were a total life saver!

You should consider a paypal donation button on your website.

---

### Post by _mirinda_ on 2007-11-17
Thanks! Now I have all the bling :)

However, my DVD player/burner does not seem to work... if I put a CD or a DVD in, nothing happens.
Newbie question: How do I access my DVD drive?

I have a Dell Inspiron 6400 laptop, so that's why im posting my problem in this thread.

Thanks in advance

---

