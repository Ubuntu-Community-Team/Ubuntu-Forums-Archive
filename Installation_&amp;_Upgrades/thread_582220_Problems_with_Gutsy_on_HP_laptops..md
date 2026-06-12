---
title: "Problems with Gutsy on HP laptops."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by old_salt on 2007-10-19
If you have an HP Laptop - especially an HP 6000 or 9000 series laptop, steer clear of Gutsy 7.10 release. 

Too many hardware issues, lack of available apps to satisfy dependencies and less than half the available programs as found under Feisty 7.04 release. 

Not sure what happened here but I can't even obtain the necessary requirements to even compile from source. Hardware is not supported and despite the efforts of many in submitting to the hardware database for developers to support this platform, it appears everything went to the "bit bucket".

About the ONLY thing they did right was provide the Broadcom wireless nic firmware via the restricted drivers option and that was it.  Nothing else works. You can't even manually fix the problems because the tools to do so are not available. 

PLEASE PLEASE stick with Feisty or whatever distro you may have used before in efforts to send the message to the developers that they missed the boat BIG TIME on this release.

As a 20 yr professional, I cant recall a release take such a large step backwards. I'm beginning to wonder if this release is for Dell only.

---

### Post by EXCiD3 on 2007-10-19
I too am extremely disappointed in Gutsy. As a user of the Hp dv9000t and author of several HP related threads/tutorials I am **VERY **disappointed in Gutsy's support. Yes it does provide support for the Broadcom chipset, however it lacks functionality that we could attain in Feisty fairly easily. I strongly feel that users should continue with Feisty until Gutsy has had time to mature and develop into a better OS than Feisty was. The few features that Gutsy has implemented in hopes of being useful are nothing to compensate the usability of your hardware you use compatibility of.

As an HP user and seeing how many other students us HP laptops, I feel that this topic should be of great concern to the community/developers. Well over half of the fellow students I have in my classes use HP laptops. If there are that many HP users in such a small area, think of the amount of Ubuntu HP users that are going to be disappointed with Ubuntu. Fedora works great with HP laptops and if users are disappointed with Ubuntu, they are just going to turn to OpenSUSE, Fedora, or another distrobution. I would hate to see users leave the community in search of a more capable linux distro.

If you are an HP user, I strongly recommend using Feisty for the time being. There is plenty of support for Feisty and lots of information/tutorials on problems you may encounter, for example: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

Please post your thoughts on this, as I feel it is a very important topic and should be corrected as soon as possible.

---

### Post by scorp123 on 2007-10-20
> **EXCiD3 said:**
> I too am extremely disappointed in Gutsy .... If you are an HP user, I strongly recommend using Feisty for the time being.  Same here! Feisty works wonderful on my hp Pavilion dv2108ea laptop. Everything that I care about works superb. Standby, hibernate, resume, WiFi, Beryl, Compiz-Fusion, 3D acceleration, HP remote control, multimedia buttons .... Everything works on Feisty. On Gutsy? Nope. Many annoying bugs. Sorry to say so but "Gutsy" really feels like a step backwards. Above all things that annoy me: Why in the world was the framebuffer disabled?? Now when I use parameters such as "vga=791" in my 'menu.lst' my tty1 - tty6 remain black and cannot be used. And none of the workarounds I found so far seem to work.

Thank you but no thank you: I'd too recommend to stay on Feisty for now.

---

### Post by cowkiller on 2007-10-20
I use a HP dv2570 and also feel a bit disappointed with Gutsy. All the good vibrations I had during the installation process got vanished when I tried to configure my video settings with the new interface. The monitor is not even recognized and the graphic drivers doesn't work properly, not even the Nvidia restricted drivers. No matter what I do, I have constant resolution and refresh rate issues. So I'll consider going back to Feisty and hang on for a better HP support on Gutsy, hopefully sooner than later.... or keep trying to solve it by myself if I've got time. 
Anyway, good luck to all HP users that try Gutsy. Always make a backup first ^^

---

### Post by elj4176 on 2007-10-20
thanks for the info. I'll stick w/7.04 on my hp for now. I already tried to upgrade a dell desktop and have some problems with it - think i have it figured out now tho.

---

### Post by conanjb on 2007-10-20
Yikes! I was just about ready to click the upgrade button, and then I thought i'd better double check the forum for any issues others may be having. I have an older HP Pavilion zd7280 that works great on 7.04. Does anyone think I'd run into the same issues as the HP users with dv model laptops?

Glad I saw this post.

jb

---

### Post by Rapidsnow on 2007-10-20
Grr I wish I would have seen this before I upgraded. I am having fewer problems than you guys with a dv6000 but I have no sound. My nvidia drivers, compiz, multimedia buttons, and pretty much everything is working fine, but for some reason sound isn't. I had no problem when installing Feisty with anything except the broadcom chipset (which has now crapped out in my motherboard.) Well I will try to fix this, too late (i.e. lazy) to go back almost.

---

### Post by gcrussell1 on 2007-10-20
I'm running an HP zx5000 laptop - older generation (I think) than the DV line. Anyone know if the zx series machines work well with gutsy? I'm planning on dual-booting XP and Ubuntu to learn Linux, since I've never used Linux before, but I don't want my first experience to be a bad one. 

Any suggestions? Am I safe with 7.10, or should I try out 7.04 to start out?

---

### Post by EXCiD3 on 2007-10-20
gcrussell1 I think you would be safer off using Feisty and getting the drivers installed for it. Gutsy may prevent some of your hardware from being usable. If you want to try it, be my guest, but I have had a rediculous amount of problems.

Here is a link to my tutorial that might help you on installing Feisty and its drivers: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by Oatworm on 2007-10-20
Just upgraded to Gusty Gibbon from Feisty on my Compaq V6000Z, and I'm less than impressed.  Things that I have run into thus far:

1.  The newest kernel version (2.6.22-14) won't boot.  I have to use Grub and boot off of the original 2.6.20-16 kernel.
2.  Gnome crashes whenever my screensaver turns on and whenever I access certain parts of my NVIDIA control panel.  It wasn't doing this under Feisty.  I suspect it's because the video drivers are compiled against the new kernel - I can't upgrade the drivers on the "old" kernel since I don't have access to the old header files anymore.

Past that, everything else works, though that's probably because of the old kernel more than anything.  I was excited about Gutsy, hoping to actually have real multi-monitor support.  Plus, after having a kernel update in Feisty knock ACPI out on me and render my battery meter useless, I was hoping that Gutsy would have better security and application upgrades that wouldn't nuke my laptop.  Suffice it to say, I'm not finding this encouraging.

---

### Post by pangalactic on 2007-10-20
I'm on a dv8000- the only problem I've had is getting the Broadcom to work with ndiswrapper. I've literally spent 40 of the last 48 hours trying to break this, and nothing else seems wrong at all. I will admit, the ndiswrapper stuff was a beeeeyotch. In fact, the only real nuisance has been having to map the special keys for DVD launcher, calc, etc. 

Pang

---

### Post by magestar on 2007-10-20
I am impressed, I cannot even boot the Gutsy live CD... I was so impressed with Fiesty and had removed Vista completely since I am now feeling very comfortable with Fiesty. Sadly I will continue to see if anything is done with Gutsy and but it looks like I have to wait until April for the next version.

---

### Post by QkEterror on 2007-10-21
Unfortunately I saw this warning too late to save my perfectly working Feisty on my nx9010. I'm now stuck with an operating system that can only output a blurry screen (it looks like it paints everything distibuted over a centimeter) and a bar on the left side. So again. Don't upgrade!

Is there a possibility to downgrade back to Feisty?

---

### Post by joscht on 2007-10-21
As it seems, fortunately, I was not even able to install Gutsy Gibbon. But it's a pity, I was really looking forward to the release..

---

### Post by zelsuk on 2007-10-21
i m also hp laptop owner (dv4000) but i am happy with gutsy.. everything works good esp. my video card..

---

### Post by Dr Sketch on 2007-10-21
I have a DV8000, and haven't seen any problems with Gutsy yet...

---

### Post by Thanawho on 2007-10-21
Funny Story:

two of my friends and I got together to dual boot Gusty on three (new) HP laptops.

Friend 1: bcm43xx wireless does not work, and will not enable itself. Graphics card works, sound works.
Friend 2: Graphics card not recognized. Compiz fusion not usable. Wireless card works, Sound works.
Myself: Sound card detected, no sound. Graphics card works (w00t nVidia), wireless card works.

Seems to be a bit of a problem here.....

Anyone actually know how to enable sound on hp laptop? Its odd because everything is detected, but it seems like the quickplay button isnt allowing the sound to play because its always orange...Friend 1 installed Ubuntu with his sound on (from Windows) and got sound, but i cant. Its like ubuntu thinks the sound is on when it boots up(when its actually not) and proceeds to shut down the sound when it thinks it is turning it on (sorry for the brain twist).

---

### Post by J-Morris on 2007-10-21
I have an hp dv2000 laptop, and gutsy killed my sound which was working well even in the BETA. The ALSA mixer looks ok, I am in the 'audio' group,  my sound card is recognized, and all my application act like they are playing sound but there is no sound. I use my computer for music and so this is unacceptable. 

If you have an hp laptop DO NOT UPGRADE TO GUTSY. Not yet anyway. 

I also want to know how to upgrade back to a prior working version, preferable the beta.

---

### Post by martijnterpstra on 2007-10-21
I have a HP presario v6000 and the sound doesnt work on gutsy (worked of fietsy).
besides that it works perfect.

---

### Post by buzzmandt on 2007-10-21
test this sound problem.....
turn your laptop off, unplug it, turn it on, log in and see if you have sound....

bet you do,

I fixed this with adding the option apci=off on the boot line.

I have a perfectly running hp dv2000

---

### Post by Thanawho on 2007-10-21
I think I'm going to wait until a single DEFINITIVE solution to the sound problem is released. There are too many posts about too many solutions that are either outdated, work on certain laptops but not others, or simply do not work at all. PLEASE post a link on this sticky if you make a guide to fix the sound problems in Gusty.

---

### Post by rjs987 on 2007-10-21
I also have a HP zt1230 laptop that runs Fiesty just fine. It's an old laptop that only has 256 MB RAM and will not run the Live CD of any version I've tried due to that. I used the alternate CD to install Fiesty and that was working perfect as far as I can tell. I am new to using Linux, have a friend who has run it for years though. I just found out about kubuntu just before Fiesty released last spring and have it installed (unofficially) on a test box at work as a dual partition with Windows Vista (must have the Vista for testing for work since that is what they want). I only just installed Fiesty on my laptop at home just over a week and a half ago and have been playing with it every night since.

I tried the online upgrade to Gutsy over this weekend and many failed processes including the NIC, x11, and others. Can't run adept, says there is already one process open and offers to repair so I can open it but that fails as well. Didn't have time to mess with it since I was trying to do some things on the laptop so just re-installed Fiesty and am back up and running fine again.

---

### Post by Thanawho on 2007-10-21
> **buzzmandt said:**
> test this sound problem.....
turn your laptop off, unplug it, turn it on, log in and see if you have sound....

bet you do,

I fixed this with adding the option apci=off on the boot line.

I have a perfectly running hp dv2000

Tried booting down, unplug, and restart...still no sound.


Please specify the "apci = off on bootline"

---

### Post by dentament on 2007-10-21
install from scratch on hp pavillion zd7229ea
in recovery mode I get:

```
vfs: cannot open root device "uuid=xxxxx" or unknown-block(0,0)
please append a correct "root=" boot option; here are the available partitions: [blank]
kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```
the partitions and data are there, booting from an old gentoo boot cd i can see them

---

### Post by GoBieN on 2007-10-21
i have a HP Pavilion DV6000 laptop (DV6017ea to be exact) and everything works fine except sometimes (about once in 5 minutes) the laptop freezes for 10 seconds, mouse still works but nothing responds, not even ctrl + alt + backspace. And then after 10 seconds everything is back (including the ctrl alt backspace so the x restarts). very strange problem.  The broadcom wifi is working excellent with the ndiswrapper that i set up on feisty so i did not choose to use the restricted broadcom firmware option. I'm happy the way wifi is working now.

I must say that for feisty to work on this laptop i had to add boot option **noapic** to the kernel, and it still is enbaled in grub so i still boot with this option. 


Perhaps you guys should try booting with noapic. 

use the following line in your /boot/grub/menu.lst and grub will always add the noapic option:

> defoptions=noapic splash (the splash is already there, just add noapic in front of it.


Good luck, and if someone knows a solution about the freezes please tell me :)

---

### Post by J-Morris on 2007-10-21
I've gotten my sound back! I used the method here:

[http://ubuntuforums.org/showthread.php?p=3589977#post3589977](http://ubuntuforums.org/showthread.php?p=3589977#post3589977)

I'm new to ubuntu and linux and pretty ignorant, but this fix was easy. Mad props to holodad! 

Good luck...

---

### Post by portach king on 2007-10-21
Having a Pavilion zv6000, the main problem I've had (as far as I've noticed) is an incredibly long boot time with no graphical interface at all, just a black screen for close to 5 minutes and then the operating starts as normal.

It's so disappointing as I was looking forward to this release a lot. Lets hope this all gets fixed in an update asap.

It is worth noting though, that in spite of the booting error my broadcom wireless card and my ati radeon 200m xpress were all working perfectly within three clicks. That really was incredible.

---

### Post by cipher27 on 2007-10-21
I have an older zv6000,I recently upgraded from feisty to gutsy 64 bit version everything works fine except for the usplash screen. :(

---

### Post by IMSciFi on 2007-10-21
Just got done installing Gutsy from the i386 dvd on my dv6426 with no problems, yet.  I actually had Feisty not recognize my i950 gma vid driver and so only had 800x600 after install, but Gutsy is working at full resolution without any updates.  Also no problems with sound or wireless (intel pro).

---

### Post by s_raghu20 on 2007-10-21
Hi,

Putting in "my two cents". I am running a HP Compaq 6710b.

On this one, I did the update from Feisty yesterday. All seems to work fine, (as in all I could test), except the desktop effects. 

Sound works, I could play some online streaming stuff.. Tried to play a bit of dvd video also, and that works fine.

Internet works (with dhcp to my router). Not tested wireless yet, since I dont use it much.

I was pretty surprised to read reviews from people about gutsy being a backward step, since I too was expecting it to take Ubuntu to new heights. And yes, I can agree, not much looks changed since Feisty, at least on the top level. May be somethings have changed at lower levels (in core stuff), but only time will tell about their reliability.

When I installed Feisty about two-three months back for the first time on this laptop, I found out that my hardware was too new for the drivers to be supported built in and I had to do some manual tweaking. Then it worked, I could do some desktop effects and stuff like that, but it was not complete. For example, when desktop effects were switched on, I couldn't play video. For that, I had to switch off the desktop effects and then things were fine. I expected that Gutsy will fix this problem since my "new hardware" wont be all that new to Gutsy and therefore there would be built in support for my graphics card, thereby removing need of my manual tweaking to make it work and the small things with dekstop effects will not only disappear but will grow in quality.

Disappointed. :(

regards
raghav..

---

### Post by handaxe on 2007-10-21
You did not write if you had Feisty on this machine before without problems... guess you did...

Nothing in "system" -> "administration" -> "System Log" (see messages. kernel for eg) as a clue to the freeze? In Feisty mine is a SATA issue that  gets logged (Acer tho' not HP - however ....)

HA

> **GoBieN said:**
> i have a HP Pavilion DV6000 laptop (DV6017ea to be exact) and everything works fine except sometimes (about once in 5 minutes) the laptop freezes for 10 seconds, mouse still works but nothing responds, not even ctrl + alt + backspace. And then after 10 seconds everything is back (including the ctrl alt backspace so the x restarts). very strange problem.  The broadcom wifi is working excellent with the ndiswrapper that i set up on feisty so i did not choose to use the restricted broadcom firmware option. I'm happy the way wifi is working now.

 ...
Good luck, and if someone knows a solution about the freezes please tell me :)

---

### Post by root@localhost on 2007-10-21
I've been trying to install 7.10 on a hp pavilion zt1130--an ancient laptop--for several days now, and the graphical installer always locks up. Should I try to use 7.04, backtrack to the LTS version, or find a different way to install 7.10. I'm hoping that the hardware is old enough that it will still be supported, but it obviously won't install. 

Thanks!

root

---

### Post by blackrim on 2007-10-21
perfect on fiesty -- can't get a clean install (or live cd ) working on gutsy with a thinkpad. so it isn't just hp. i feel bad for the linux community (myself included). this could have been a great release if it worked for ubuntu considering the mac soon to be released. 
not this time

---

### Post by gamedesignerwol on 2007-10-21
Hey everyone I wanted to let everyone know that DV8000's seem to run great on 7.10 and I am sorry the 9000, series is still behind..the only issue I am having is of course this D#AMn ATI Drivers, I know i have been told a million times over to get nvidia in laptops and I am a huge nvidia fan..but this was free;;;so I could not complain. The only question I have and it should be a easy one...Imma just a noob..but 
When I goto system----> Appearance----->Visual Effects and try and get the cool stuff turned on i get this message.
The Composite extension is not available
I am using the restricted driver and do have some 3d acceleration
Gears Test Results. 
6551 frames in 5.0 seconds = 1310.055 FPS

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
"fglrxinfo" command

And have this card
ATI's Radeon Xpress 200M

I have no and I mean no Other issues.....I just would like to see the full ubuntu experience like I have seen....am I at the hands of ATI/AMD...and awaiting a driver release and If so how long? I have mutli boot to windows xp FLP version for backup just waiting to kill that soon as this part works...
oh wait one more issue I did forget...Streaming a live broadcast from a radio station
does not work..here is the link..may as well hope someone see's this and can direct me in the right direction...I am a noob but doing my best to learn this wonderful new OS.
Good job to development of this release...can't wait to see the next update!!!

[http://www.1460thefan.com/?sec=podcasts](http://www.1460thefan.com/?sec=podcasts)

I do have mplayer and all that jazz as the forums have suggested.

---

### Post by BoardDWorld on 2007-10-21
I'm really sorry to hear all your problems and faults (as well as everyone else's it seems). I have the DV9224TX (specs in sig) which has the intel chipset to match the Core2Duo CPU of course. Everything works out of the box except the webcam. Sound works including all the touch keys, I can restart my Laptop with WIFI off and turn it on in Ubuntu and fire up the internet, video is brilliant, all these problems I'm hearing about I'm just not getting at all.

The only problem I had was the CUPS didn't detect my DCP-115C and the annoying compiz effect that allows a window to bump into another can't be turned off using the Advanced Desktop Effects Manager(there will be a way some how).

The Webcam driver has already been compiled and packaged here:
[http://www.arakhne.org/spip.php?article50](http://www.arakhne.org/spip.php?article50)

Download the .deb direct from here:
[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.22-14-generic/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.22-14-generic/)

It's running perfect! In the program you're using your webcam with remember to select V4L2 as it doesn't seem to support V4L anymore.

---

### Post by frego on 2007-10-21
I just did a fresh install of Gutsy on an HP Pavilion ZE4500 laptop.  It appears to be running fine.  I used the alternate install disc and used options vga=771 noapic lapcic or something like that.  It's on the F2 or F3 screen of the help during the alternate install.

---

### Post by charon79m on 2007-10-21
Afraid I'm in this boat as well.

I have a HP NX9600 that works flawlessly with Feisty.  I had installed beryl and made many customizations so I figured I'd wipe and do a clean install of Gutsy.

I burned the ISO and did the install.  Toward the end of he install my machine just powered off.  I thought this odd and checked power cables and such, all looked fine.   I did the install again and had the same issue.  I figured I'd try the alternate CD image just to see if that would help.  Same problem.

Well, I booted to the limited install that I had on my system and found major issues w/ permisions in /dev.  I ran MAKEDEV and found that the system reboots there, so the issue seems to be in running the MAKEDEV script.

I ran MAKEDEV in a verbos state and found that it rebooted when creating devices for raid devices... I have no idea why.

I've reinstalled using Feisty and am contemplating an upgrade from here.  Thoughts?

lspci:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by philven on 2007-10-22
I have an HP 5370.  I hit the upgrade button and the only problem I have had was I needed to reinstall the Broadcom drivers to get the wireless working again.  Everything works and the video resolution stayed the same.  Sound is working.  The only thing I have not tried is the DVD burner.  Gutsy is working great on my HP.  Now if I can figure out how to upgrade my desktop which has Kubuntu on it.

---

### Post by Melcar on 2007-10-22
I don't feel hopelessly alone anymore :).  Trying Gutsy on my Presario V2000, and while it does work, I have been experiencing some "minor" issues that just weren't there with Feisty.  The most blatantly noticeable one is the fact that it takes literally 1min and 30sec. to load (from the initial OS boot up to the login screen).  Feisty used to do it in about half the time, and an old Latitude laptop I'm trying Gutsy on just takes 30sec to do it (that laptop only has about 1/3 of the hardware power as my Presario).
I haven't had any major hardware problems (but neither did with Feisty).  Even the integrated dial up modem works now.  Shouldn't have bothered with fwcutter thought, since it's still slow as hell (went back to using ndiswrapper now).

---

### Post by gamedesignerwol on 2007-10-22
Installed 7.10 and thanks to another member got this link...gutsy works PERFECTLY~~~ even got the effects going now which is to die for...great job ubuntu team

[http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045)

---

### Post by Rex_Mundi on 2007-10-22
Ah finally I found the thread I was looking for. Gutsy is indeed a big no no for me. I couldn't get my external monitor to work what ever I tried. Other than that I didnt notice any big apparent problems.

---

### Post by hollowhead on 2007-10-22
All these HP laptop reports are worrying.  Anyone sucessfully installed gutsy on a compaq HP NX6100.  Feisty works perfectly on it apart form not detecting my winmodem and my old PCMCIA modem a long standing problem with ubuntu on my laptop.

---

### Post by MrMasterplan on 2007-10-22
Someone should put a big fat warning sign beside the upgrade button that people should check the forum before upgrading. I've got a hp pavillion ze5400. Everything worked brilliantly on Fisty, and now after the update I get the fuzzy screen just like many others here. I wish I would have read these forums first. I _used to be_ a big ubuntu fan, and advertise it to all my friends. Now I'm just about ready to peel that ubuntu sticker off my laptop.
Someone should have tested this stuff _before_ the release.

Thanks a billion to whoever cocked this one up.
:-(
S

-----------------
UPDATE:

Ok, maybe I overreacted a bit.

**_To anyone with the fuzzy screen problem:_**

Here's the solution. Form another post I saw, I found out that you can do this:
Start in safe mode, and when you get to the command line enter:

sudo dpkg-reconfigure -a

You will now be asked every question there is to ask about the configuration of you system, so you need some patience. But importantly one of these questions will be about the resolution and refresh rate of you monitor. I selected medium expertise and from there I knew that I have a 1024x...@60Hz. You'd better know what this is for you screen, because I think that's what got detected wrongly.
When you are finally done just restart and voila.

My faith in Ubuntu has been restored.

I hope this helped someone. If it did, pm me (that'll make me feel good :-) )

Have fun with your now working installation of Gutsy:

S

---

### Post by BoardDWorld on 2007-10-22
Just adding to my comments of everything working perfectly on page 4 of this thread. The external display works brilliantly. I just use the function key to (fn+f4). This actually changes between display modes faster than any other operating system I've had, this includes both Feisty and Vista. I didn't boot up with the external display plugged in either...

---

### Post by Wobedraggled on 2007-10-22
I have a nx9420, No issues what so ever, I did upgrade from 7.04, which I had issues with the video, but those were resolved.

---

### Post by nene3 on 2007-10-22
just upgraded to gutsy on my hp nx6125... works ok for now, no problems what so ever...

---

### Post by OmahaZ on 2007-10-22
For anyone with problems with Graphics on HP Pav with Nvidia Go: Dont blame Ubuntu or HP.

The bugs are apparently in the Nvidia 100.xx.19-driver. A beta 100.xx.23 is available at Nvidia - if you want to compile.

I am using a DV 6000 with Gutsy. To avoid the troubles with graphics install and configure the **Nvidia9639-driver** manually (no - no need to compile it) thus do not use restricted manager as this will attempt the 100.xx.19 driver.

Best thing I believe is to install the driver on a fresh install - ie without having attempted the restricted manager first - alternatively purge your xorg.conf....
[B]
For the sake of good order: here are the commands for GENERIC kernel 386 at your own risk - no explanations given:[/B]

[B]sudo apt-get install linux-generic

sudo apt-get install nvidia-glx

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nvidia-xconfig[/B]

(Just close the empty file aftewards)

[B]sudo nvidia-xconfig --add-argb-glx-visuals

sudo gedit /etc/X11/xorg.conf[/B]

(Change DefaultDepth to 24)

Restart  X  or reboot.

---

### Post by skiold on 2007-10-22
Hi,

I had no problem upgrading from Feisty to Gutsy on my HP pavillion 6324.
Everything works better, because on Feisty I couldn't use the internal microphone and the web cam. I just let the upgrade application running automatically an say yes to everything (Including removing some applications like Avant and some repos like automatix). Now I'm waiting for new updates for some programs.

---

### Post by EXCiD3 on 2007-10-22
Does anyone know about configuring their Nvidia card to get dual monitors in Gutsy? I was unable to get the nvidia driver working, especially not with dual monitors. I have a dv9000t with 7600go. Any help would be great as I cant figure this out.

---

### Post by xxrealmsxx on 2007-10-22
> **portach king said:**
> Having a Pavilion zv6000, the main problem I've had (as far as I've noticed) is an incredibly long boot time with no graphical interface at all, just a black screen for close to 5 minutes and then the operating starts as normal.

It's so disappointing as I was looking forward to this release a lot. Lets hope this all gets fixed in an update asap.

It is worth noting though, that in spite of the booting error my broadcom wireless card and my ati radeon 200m xpress were all working perfectly within three clicks. That really was incredible.

You have long boottimes even with the computer plugged in?

---

### Post by EXCiD3 on 2007-10-22
portach king have you tried removing the splash parameter from bootup?

---

### Post by loveshackdave on 2007-10-22
> **gcrussell1 said:**
> I'm running an HP zx5000 laptop - older generation (I think) than the DV line. Anyone know if the zx series machines work well with gutsy? I'm planning on dual-booting XP and Ubuntu to learn Linux, since I've never used Linux before, but I don't want my first experience to be a bad one. 

Any suggestions? Am I safe with 7.10, or should I try out 7.04 to start out?

I'm running Gutsy on a zx5000, no problems at all.

---

### Post by dagrump on 2007-10-22
I bought a HP6000 series, & had no luck getting things to work, 5 days later I took it back & got a toshiba, it's no powerhouse, but it sure took to ubuntu much better. I had a HP desktop & it had some issues too. Gave that critter to my daughter, she got it infected ( damn MS) & I installed Feisty works fine now. Guess I'll avoid HP for now. Glad to see the warning going out, should save some headaches.

---

### Post by blackdevil on 2007-10-22
I'm using a HP Pavillion dv9000 and I had zero issues with Gutsy. Sure you have to enable the restricted drivers for NVidia and the wireless, and I had to use noapic nolapic commands at CD boot to get it to work. But those are the same issues I had initially with Feisty. After that though, everything updated fast, the ease of getting Flash now (for 64bit) is absurdly amazing. Everything works great for me, I wish I knew what the problem was for all of you. Even the little buttons for sound controls work fine, mic, webcam.... everything. Fresh install, if that makes a difference. Plus I think its a little silly to expect a new release to solve all of your problems and run exactly like all of your customizations and optimizations you did for Feisty. This was much less painful for me, still a little bit of tweaking, but nothing I would expect to be automatically done for me.

---

### Post by BoardDWorld on 2007-10-22
> **blackdevil said:**
> I'm using a HP Pavillion dv9000 and I had zero issues with Gutsy. Sure you have to enable the restricted drivers for NVidia and the wireless, and I had to use noapic nolapic commands at CD boot to get it to work. But those are the same issues I had initially with Feisty. After that though, everything updated fast, the ease of getting Flash now (for 64bit) is absurdly amazing. Everything works great for me, I wish I knew what the problem was for all of you. Even the little buttons for sound controls work fine, mic, webcam.... everything. Fresh install, if that makes a difference. Plus I think its a little silly to expect a new release to solve all of your problems and run exactly like all of your customizations and optimizations you did for Feisty. This was much less painful for me, still a little bit of tweaking, but nothing I would expect to be automatically done for me.

What's the exact model?

---

### Post by dsiddens on 2007-10-23
To the devs who look after the code for the AMD64 machines:  my HP dv8000 hard drive appears to be bricked.  I was able to use our second machine to download the Gutsy 64 .iso and make a CD which I've been able to boot this machine with.  But using Krusader and Krusader's MountMan I can find no trace of hda or hdb (this laptop has two hd's in it)  I had a disk wipe out when upgrading from Dapper to Edgy and am not willing to plow ahead with the install without being able to remove certain files.  As I said, at this point I can't even see the hda nor hdb.

In good faith I followed the upgrade notice that appeared in Synaptic Package Manager only to find many notices of dependency failures and install failures.  When I took a chance to see the "differences" between an existing file and the proposed file, a command line screen popped up and  that was the end of all.

Your help with this matter will be appreciated.
Thank you, Doug

---

### Post by whistl3r on 2007-10-23
My dv6000 series laptop is working just fine, better than feisty. Although it does take a longer time to load since i enabled a few effects in compizfusion. Didnt try installing the webcam driver yet but Bluetooth and Wifi works right out of box.

---

### Post by misfitpierce on 2007-10-23
I have a HPdv8000 series laptop and it works perfect. All except suspend but ATI says thats their fault. Gutsy runs fast and beautifully. Startup is quick as well as shut down and I love it.

---

### Post by peblin on 2007-10-23
I have a HP/Compaq nc4010, and I'm sorry to say that my upgrade failed miserably as well.

Upgrade seemed to go well, but system is exceptionally unstable. Had to run "dpkg --configure -a" manually, which helped a bit. However, still LOTS of kernel panics, random crashes and basically, a completely useless system. Damn.

Never had any problems with Feisty.

---

### Post by nitro99 on 2007-10-23
I hv a DV6291 and 7.04 worked like a charm. Hv installed Gusty and so far everything seems to be ok including Compiz....except maybe bootup speed when unpluged from the network. It takes like forever if unpluged :confused: 

I hv p2 machines that can do better

---

### Post by misfitpierce on 2007-10-23
> **peblin said:**
> I have a HP/Compaq nc4010, and I'm sorry to say that my upgrade failed miserably as well.

Upgrade seemed to go well, but system is exceptionally unstable. Had to run "dpkg --configure -a" manually, which helped a bit. However, still LOTS of kernel panics, random crashes and basically, a completely useless system. Damn.

Never had any problems with Feisty.

Try fresh install? Upgrades dont always go perfectly sadly. Fresh installs are nice though.

---

### Post by peblin on 2007-10-23
> Try fresh install? Upgrades dont always go perfectly sadly. Fresh installs are nice though.

misfitpierce: I'd love to do a fresh install if I could figure out how. My laptop don't have a CD-player (anymore) and I don't want to reformat the disk. So if anyone have any idea on how to do a fresh OS install, from HD, without reformatting, I'd be very happy.

(Yes, I've looked at the netboot HOWTO and it seems... ridiculously complicated setting up PXE servers and all. Where's the "/bin/clean-install gutsy.iso" command!?!?)

---

### Post by portach king on 2007-10-23
Hi, thanks for replying directly

> **xxrealmsxx said:**
> You have long boottimes even with the computer plugged in?

Yes, when it is both plugged in and running of battery, the boot time is the same. I should correct myself though, It take 3 minutes (exactly!) from the time GRUB disappears to the time the logon screen finally shows up.

> **EXCiD3 said:**
> portach king have you tried removing the splash parameter from bootup?

I'm sorry, I'm really not sure how one would do this.

---

### Post by kazuya on 2007-10-23
Had same issue at first. I would not back to feisty though. Gutsy is more at the bleeding edge. On my HP, it installed flawlessly. Everything works faster. Boot time is always slow on that machine.

On my HP a1410n desktop, I guess the nvidia driver does not seem to work as well after my upgrade from Linux Mint Celena {feisty} to Gutsy repo.

First off, did everyone do this link:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

In terminal, eneter in the following

gksu "update-manager -c" 

gksudo gedit /etc/apt/sources.list     
OR
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list 

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 

Hit Y or N or I when prompted

Just to be totally sure that everything is installed properly, run these commands: 

  sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 


Problems with X
If after the upgrade the X server doesn't start (i.e. if you can't get the graphical login), then that can be caused by either a misconfigured X server or because the xserver-xorg package has been removed. 

Most of the times a reconfiguration of the xserver-xorg package will be enough. To do so issue the following command: 

  sudo dpkg-reconfigure xserver-xorg  

If that didn't work or if the package wasn't installed anymore, try to reinstall it, and thus do a reconfiguration too: 

  sudo apt-get install --reinstall xserver-xorg  

Instead of using the following command as stated before, which didn't work for me for some reason, plus it wouldn't reinstall if it is installed already (using the --reinstall switch it will allways work; twosouls82 on 20061212): 

  sudo apt-get install xserver-xorg  


I shall test it out for myself. sorry to sound repetitive.

---

### Post by whistl3r on 2007-10-23
> **whistl3r said:**
> My dv6000 series laptop is working just fine, better than feisty. Although it does take a longer time to load since i enabled a few effects in compizfusion. Didnt try installing the webcam driver yet but Bluetooth and Wifi works right out of box.

Webcam also works perfectly. Compiz fusion was slow because i had my old .beryl directory in my home folder, removing it makes it work great. The only prob I have is that suspend and hibernate does not work.

---

### Post by samuraiCat on 2007-10-23
Yep, I tried to put it on my Presario and it so totally hosed it, I had to completely reinstall 7.04 from scratch. Edited to add: After the install, it would lock up at the point during the bootup where it configures the network manager.

I have never been so mad at a piece of software in my life as I am at Ubuntu Gutsy Gibbon 7.10.

Too bad nobody can really be held accountable in a substantive way, but I think I might submit a Launchpad ticket asking for those five hours of my life back.

---

### Post by EXCiD3 on 2007-10-23
The only way they can improve their product is by people submitting bug reports. If you find any problems, make sure there is an bug report posted on launchpad. The developers read these and can hopefully fix the problems. Hopefully there have been engouh complaints about Gutsy that the devs will respond and give more support for nonDell hardware. This release was obviously intended for Dell computers.

---

### Post by cburki on 2007-10-23
I guess my problem is just a bit lighter than the previous posters... I have a dell inspiron 8600 with a 1280x800 screen. When I upgraded... no problem... I'll even say it was perfect except for the thunderbird icon that I had on my bottom panel: It didn't appear, I had to click on it to get the icon from the icon database.

Ok but then, I enabled the nividia driver and did a restart. That's when it didn't work anymore... I managed to get a 1400x1050 dell laptop screen resolution. I also had gray lines in the background and had to change the frequency to 60hz to have gray lines and a message box. Ok I accepted this 1400 screen and started up! Then I noticed that the desktop was a bit bigger than my screen since some of my icons are just off the screen on the right. I tried to change the screen settings but to no avail...

Another problem is that my keyboard was not recognised... If I remember correctly, feisty asked me if my settings were correct... gutsy just took for granted that since it was english language settings that the keyboard was an american one... But a few clicks on the menu to find the keyboard setting corrected this! I can now type the letters that I see on my keyboard.

edit: I'm looking for the right thread, coz this ain't the right one... I have a Dell Laptop...  ](*,)

Ok, Try this out, Download envy to install nvidia and ATI drivers... It worked to install the correct drivers on my laptop. Just search on google fore envy ubuntu or click here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by trarman on 2007-10-23
I've got a dv9408ca which mostly worked in Feisty, but had a bad habit of randomly locking up.  I upgraded (via fresh install) to Gutsy hoping that problem would disappear.  As of yet the lockup hasn't occurred, and everything seems to be working, but EVERYTHING seems significantly slower.  Even typing in this window is slower than I am hitting the keys.  Feisty was nice and quick, but even opening a terminal in Gutsy leaves enough time to wait, sigh, wait some more.  :(

---

### Post by kaurxxl on 2007-10-23
I have HP Pavilion dv2208ea, and I did do fresh install and installed ubuntu 7.10.
Only problem I have is that REMOTE CONTROL isn't working. I can live without remote, but I would love to see it working. 

Everything else worked with fresh install.

---

### Post by gamedesignerwol on 2007-10-23
Re: Problems with Gutsy on HP laptops,This solved my issues, I have a 200m ATI Card, but it seems to work for alot of people, with different ATI Cards...Hope this helps HP people....DV8000 is now done..

[http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045)

---

### Post by Keyper7 on 2007-10-23
My dv6258se's Broadcom wireless chipset didn' t like Gutsy too. :(

With both ndiswrapper and bcm43xx, the network manager segfaults most times I try to connect to a new wireless network. When it does not crash, it never connects to the network, it tries and tries and eventually gives up.

Wireless was flawless on Feisty and I'm really sad to see that no workarounds seem to have been found for Gutsy so far... I was really excited about 7.10 but I guess I'll have to wait a bit more.

---

### Post by SaiGoN DraGoN on 2007-10-24
I had a few issues with my upgrade to Gutsy; one of them was the Nvidia driver which would not stick whenever i try to install it with envy but after a few tweaks it did. Not quite the way i wanted it to do it but what the heck as long as it lets me use compiz fusion i am okay; i can't have control over brightness, well kind of, not as well as i used to be able on Feisty but it's alright i guess. 
Second, whenever it tries to to connect to the internet it forgets my password, asks for the keyring because it's "locked"  i have to type the password once and when it pops up again i have to deny it a couple of times until it stops asking me for it, but once it connects it's cool.
Despite the little bumps i had to go through, i know that it can be fixed once manufacturers support drivers for Linux.

---

### Post by aa_siempre on 2007-10-24
I'm running a HP Compaq nc6000 laptop (yes, I know it's old) on 7.04, have been for a couple of months and it works fine (much better than it did on Windows, it was freezing every 5 minutes there).

I was just about to upgrade to 7.10 because I saw it had greater Firefox plugin coverage, something I'm having problems with at the moment (specifically uploading photos to Facebook).

Anyway, is anybody running an nc6000? By the look of the previous posts I'd probably best to steer clear of 7.10. Thoughts?

---

### Post by ShodanjoDM on 2007-10-24
> **aa_siempre said:**
> 
I was just about to upgrade to 7.10 because I saw it had greater Firefox plugin coverage, something I'm having problems with at the moment (specifically uploading photos to Facebook).

Anyway, is anybody running an nc6000? By the look of the previous posts I'd probably best to steer clear of 7.10. Thoughts?

Did a net upgrade from ubuntustudio 7.04 to 7.10 on this Compaq nc6000 few days ago. The first boot after the upgrade failed completely. Then I rebooted into recovery mode and run complete packages reconfiguration:

$ sudo dpkg-reconfigure -a

And it works.

Haven't tested the wireless though, but so far everything else are ok. Even Compiz-Fusion runs well.

---

### Post by pveatx on 2007-10-24
I have successfully upgraded from 7.04 to 7.10 on a Compaq nx9420 laptop. No issues after cleaning up Fiesty XGL installation issues. All hardware works out of the box.

Peter

---

### Post by portach king on 2007-10-24
Hey Guys, 
Just a heads up, an ubuntu forum member named decargo was kind enough to point me to this thread in Absolute Beginner Talk. 
[http://ubuntuforums.org/showthread.php?t=579568&highlight=gutsy+boots+slow&page=2](http://ubuntuforums.org/showthread.php?t=579568&highlight=gutsy+boots+slow&page=2)
And Voila!
Boot-up is now perfect! I'm delighted.

---

### Post by donniet on 2007-10-24
Here's another Gutsy Gibbon horror story for you, except that this one has nothing to do with Hewlett-Packard machines.

I first performed the upgrade procedure on an old P-III 450 machine that was running Fiesty Fawn.  It worked fine, except that that machine has a cheap video card, so I can't use the Compiz effects with it.

I then downloaded the Gutsy .iso, and burned my CD.  Each time that I tried to boot my homebrew AMD 6000+ machine from it, the X-server would always crash before boot-up could complete.  It didn't matter whether I used normal boot or "safe-video" mode, the results are always the same.  (By the way, I already have three Feisty Fawn partitions on this machine, and they all boot up just fine.)

To make sure the the CD was good, I used it to boot up my other old P-III 450 machine.  It booted up fine, and, since this machine has a halfway decent video card, the Compiz effects work perfectly.

I do plan on filing a bug report, as soon as I get a chance to collect all relevant data.  I would encourage anyone else who's having problems to do the same.

I hate to say it, but I'm beginning to think that Gutsy Gibbon is the Ubuntu equivalent to WindowsME.

---

### Post by Lal2017 on 2007-10-24
Ubuntu 7.10 is RUBBISH on HP Laptop dv6000 (6258se)
Bugger, I wish I went to this forum BEFORE I performed the upgrade (downgrade!) . After many months I just about got 7.04 working to a basic degree. The upgrade totally took a backward step and stuffed up. i have tried re-installing afresh using NOAPIC for Live Boot-up CD, it hangs everytime during formatting of the drive! This release is a big screw-up. Lucky I have dual boot into XP to rely on otherwise Ubuntu is just too buggy and not very easy to use. Doesn't do everything that XP can in the same ease. Been trying to sell how wonderful linux is to family and friends and this is just a disheartening kick in the balls.

---

### Post by camini on 2007-10-24
Full install (not upgrade) on an HP dv2000 (dv2386ea exactly) works very well for me.
Better video support & rendering.
Sound works.
Have not tried wifi yet.

Works better than a 7.04 full install.

---

### Post by DHGE on 2007-10-24
Everything is perfect here!

i810 graphics on nc6400

Radeon on an ancient Omnibook 500

nVidia on a home built ATHLON tower.

The upgrade even managed an encrypted / and /home

Typing this from Windows XP/Opera in a VMWare-session ...

Kubuntu, no Compbiz

---

### Post by tonafernandez on 2007-10-24
i know i havent been doing something different and that i dont have a lot of experience but reading some threads i have been able to work around most of the issues
im running 7.10, on an hp2000 dv 2120, havent tried yet the webcam or the headphones jack
but as far as 
dvd/cd/audio/media buttons/hybernate/performance/wireless/video

im not a linux/unix guru but with a basic amount of search you will be able to get your laptop working with in a couple of hours

---

### Post by quietas on 2007-10-24
HP Compaq 8510p
Intel T7300
4gb RAM
160gb SATA
ATI HD2600 Video


Vista x64 = Working damned well out of the box, better once reinstalled minus a very few pieces of bloatware.

XP x32 = Secondary boot, works great also. Clean install with HP provided XP and drivers.

Gutsy x32 = Poo, pile of steaming. Killed off my Vista bootloader, Grub killed Vista and XP, Ubuntu would load though.


Here's my reflection on Gutsy. - - Released too early.

Grub has issues with Vista, x64 even more so it seems. most of the drivers loaded, but video had issues. ATI/AMD still doesn't ahve decent drivers in the repo's, why not? Hard drive performance was slower, why? Compiz, couldn't find it, didn't look much with video not doing 3D in hardware.

Oh well, it's back to Vista x64 with XP and various Linux flavor of the month in Virtual PC or VMWare.

---

### Post by EXCiD3 on 2007-10-24
Gutsy's problem is with the new kernel. The kernel is what is causing all the problems. If you are experiencing these problems I strongly suggest you use Feisty for the time being. The developers are working very hard to get these problems resolved. Be patient and hopefully the problems will be fixed soon.

---

### Post by earthcreed on 2007-10-24
I'm running an HP dv2500t.  I love Gutsy.  Everything works (but lightscribe)!

Wireless -- works out of the box with iwl4965 driver.
Sound -- works out of the box with SND-HDA-Intel.  Headphones and quick buttons work.
Webcam -- works out of the box with v4l2
Ethernet -- works out of the box
SD/MS/MMC/XD card reader -- detects and mounts cards out of the box (only tested SD cards)
Power management -- I can set events to occur on certain battery level thresholds, but battery consumption is to high.  CPU throttling does not seem to be happening
Lightscribe -- HP has pulled the debian native download for their disk labeler.  Have not attempted to make the RPMs work.  
HD out -- haven't tested

I am very happy with Gutsy.  I get very fast boot times with it.

---

### Post by Jonothewright on 2007-10-24
I just put Gutsy on my laptop and now it won't even begin to startup when I select 7.10.
Thankfully I did a partition before this and can still use 7.04.  How do I uninstall Gutsy?

---

### Post by nolis615 on 2007-10-24
yeah I use an "ancient" dv1000 series hp laptop and feisty ran great on it but when i upgraded to gutsy...yikes...too many bugs with graphics. all the hardware fine but i had to go through a bunch of crap to get to where i have it now...the developers kinda dropped the ball with hp compatibility

---

### Post by EXCiD3 on 2007-10-24
> **Jonothewright said:**
> I just put Gutsy on my laptop and now it won't even begin to startup when I select 7.10.
Thankfully I did a partition before this and can still use 7.04.  How do I uninstall Gutsy?

If you want to uninstall it just remove the entry from /boot/grub/menu.lst and format the partition. Make sure that grub is installed on your feisty partition and not your gutsy one. This is one reason why you would want to have a separate /boot parititon. Yours is most likely installed to the gutsy partition. You will need to reinstall grub. You can do this from the liveCD of either gutsy or feisty by following this tutorial: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck!

---

### Post by obanarama on 2007-10-24
My two cents:  I upgraded my dv9000 from Feisty to Gutsy.  I've gotta say that I like Gutsy and have had no problems at all.  In fact, there were enough small, nagging problems, with Feisty that I continued to use Vista more than 50% of the time for work and play.  Now, with Gutsy, I only boot to Vista when its time to play Madden.

Great work Ubuntu.  I dig it.

---

### Post by KevinCLovesU on 2007-10-25
Hi everyone. I *just* purchased a dv6500z (it's "in production" at this moment), so I will have a [mostly] clean slate to work (although I'm keeping Vista on 40 GB of my 120 GB HDD) and I'm totally cool with messing around, and I've been running Ubuntu since June 06, so I know a fair amount of it (including the command line). I don't see that anyone here has this *particular* model (please speak up if you see this and have issues with this model) , so I'm wondering if it would be worth my time to test Gutsy (I already have the AMD64 disc burnt) on my new HP Pavilion and attempt workarounds. Or would I be wasting my time?

I have no issues not upgrading (I had to downgrade from Edgy to Dapper last year) and Feisty has almost everything I want. I do have two successful Gutsy installs where EVERYTHING works (one Gateway desktop and an HP Pavilion ze4600). Yes, I have an HP laptop that's taking to Gutsy flawlessly, but keep in mind this has a Mobile Sempron and was made almost 5 years ago. There are only three gutsy features that I really want: Compiz Fusion (I've installed it in Feisty before, so no Gutsy needed here), Bluetooth-applet (I think that's available in Feisty too), and the multi-monitor GUI. But you guys are saying that this feature won't even work (certainly doesn't work on my old HP) so Gutsy has no advantages.

But still, I think it could be worth a shot. What are your opinions?

Here are my specs for those who are interested:

Genuine Windows Vista Home Premium (32-bit) 
AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-62 (2.1 GHz, 512KB+512KB L2 Cache ) 
15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800) 
2GB DDR2 System Memory (2 Dimm) 
128MB NVIDIA GeForce 8400M GS 
HP Imprint Finish (Radiance) + Webcam + Microphone 
Wireless LAN 802.11a/b/g/n and Bluetooth 
120GB 5400RPM SATA Hard Drive 
LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support 
12 Cell Lithium Ion Battery 

OT: For those who say "this release was for Dell only", even they [aren't recommending](http://direct2dell.com/one2one/archive/category/1021.aspx) it.

---

### Post by Keyper7 on 2007-10-25
> **earthcreed said:**
> I'm running an HP dv2500t.  I love Gutsy.  Everything works (but lightscribe)!

If everything else works, I don't see why lightscribe wouldn't... Have you tried the simple labeler from [www.lightscribe.com](www.lightscribe.com) or the Lacie labeler?

---

### Post by Keyper7 on 2007-10-25
> **EXCiD3 said:**
> Gutsy's problem is with the new kernel. The kernel is what is causing all the problems. If you are experiencing these problems I strongly suggest you use Feisty for the time being. The developers are working very hard to get these problems resolved. Be patient and hopefully the problems will be fixed soon.

Maybe it's the kernel, maybe it's not. My Feisty installation is working perfectly with a 2.6.22 vanilla kernel. In fact, it's thanks to the update to 2.6.22 that my laptop can suspend and hibernate properly.

---

### Post by blank89 on 2007-10-25
Huh, that's weird. I upgraded to gutsy on my hp dv4670us (2x AMD 2.2ghz, 200gb hd, 2gigs ram) to try and fix some of the problems I had with fiesty. In fiesty if I tried to hibernate I would get a kernel panic, my wireless card wouldn't be detected even if I used ndiswrapper, cpu scaling was unresponsive, software level brightness wouldn't work at all and battery time was poor at best.

In gutsy hibernation doesn't work, but it no longer throws a kernel panic (just an error message and a prompt to log back in), the wireless card works as long as you reinstall the driver every time you reboot, cpu scaling and brightness works out of the box and I added about 30 minutes of battery time on.

If nothing is broken in fiesty, just use fiesty. However, gutsy did fix quite a few things specifically for the hp dv6000,9000 series laptops.

---

### Post by dgar on 2007-10-25
Gutsy works better than any other OS ever did on my HP/Compaq nx9500.

```

dan@sodoku:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX Go5700] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by slash123 on 2007-10-26
Hi.

New Ubuntu user here.. Was very excited about Gutsy just from reading about it and downloaded it on the third day...

Overall: The experience has been good, and I'm well on my way to making Windows redundant. Here's my install experience on a Compaq nc6230 (ATi Radeon Mobility X300).

1. The Live CD refused to be written! Had to download the alternate CD (am going to insist on doing that from now on)
2. Install was a breeze - everything went flawlessly as I used a method to boot and install without burning a cd [http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html)
Got vmlinuz and initrd.gz from [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/)
3. Sound works perfectly. Only thing, remember to double click on the sound icon on the panel, select switches, and check the 'Headphone jack Sense' check box or ubuntu will continue to play sound from the laptop speakers even when headphones are plugged in.
4. Some keyboard buttons were not working. To remedy this, I went to System > Preferences > Keyboard. Clicked on the layouts tab. Clicked on the 'Choose...' button next to 'Keyboard Model' and selected the 'Hewlett-Packard SK-2501 Multimedia Keyboard'. Everything works now.
5. As expected, compiz (desktop effects) were not working. More importantly, the desktop would freeze leaving the mouse cursor moving after 5 minutes of working. This was of course because of the graphics driver. I installed fglrxinfo by verbatim following instructions from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). I recommend downloading the driver and installing it instead of using the repositories. The driver I installed was 8.40.4. Since I installed, a new version - 8.42.3 has been released, with the same installation instructions... but I am quite ok working with an old driver - why change something when it isn't broke, I say. Note: wherever it says to restart X by using Ctrl-Alt-Backspace, I recommend restarting the machine and not just X.
6. Compiz still crashes every once in a while (takes X down with it). But, all I have to do is log back in, go to desktop settings and re-enable extra visual effects. Dont forget to install *sudo apt-get install compizconfig-settings-manager* and increase the number of desktops to 4 to see the cube and really enjoy expo.

Apart from these teething troubles, everything else seems to be running fine. I havent once had a crash or an unscheduled restart (keeping fingers crossed). I thing all solutions are out there, but need to be found explicitly. What's the fun of installing Linux if everything works perfectly from day one :). Still, I agree that things could be much more stable,

Though I'm not an expert in Ubuntu, I am good at finding solutions over the Internet (I made this work, didn't I?). So if anyone needs help from HP compaq nc6000 series, do send me a message. If I can do it, so can everyone else.

Regards,

ML

---

### Post by cerebro on 2007-10-26
I have a Compaq nx5000 and this new Gutsy release is a mess. Issues with OpenOffice because of Gnome skins. Power management has a life of its own. 

And most importantly, I can't get sound capture to work. I connect a mic on the line input. I can hear the mic through the speakers. But it won't get sound into any sound recording or telephony application like Audacity or Skype, no matter what setting I try, I get a "failed to construct audio pipeline" error message and that's it. This all used to work fine under Feisty.

---

### Post by feng.yang@sbcglobal.net on 2007-10-26
Recently, I upgraded my HP laptop, NX9110, with Ubuntu Gutsy.  Everything seems working fine, except my wireless connection.  It had problem connecting to internet.  I spent a couple of nights trying and searching.  Finally, figured out the problem was caused by IPv6 enabled by default by Gutsy upgrade.  Once it is disabled, I don't have any problem connecting to internet now.

The only problem left now is that the wireless connect to my router is not automatically set up after booting up and logging in.  I have to bring interface ath0 down, and then up again manually.  Only after that, it works perfectly.  I suspect that is caused by avahi-daemon.  Before ath0 is brought down, ifconfig -a shows there is an interface ath0:avahi.  At this time, ath0 interface doesn't have an IP.  Once it is down and up again, ath0:avahi disappears and ath0 is assigned with an IP by the router, the DHCP server.  I tried to disable the avahi-daemon service from System->Services menu.  It doesn't help.  Any help on disabling avahi at boot up time will be appreciated greatly.

Thanks!

---

### Post by crisnoh on 2007-10-26
I've been running Gutsy on my HP zv5500 (can't be sure that's the correct model as I'm at work and it's at home) and it's actually running better than it was under Feisty.  The only problem I've encountered is using Standby and Hibernate.  Upon waking up my computer I get a black screen and have to hard restart my system.

---

### Post by Farmdogg on 2007-10-26
As an owner of a dv1049cl, I just have to say,

BOOOOOOOOO!!!!!!!!!!

Everything but the card reader on my machine should be natively supported by linux.  I just switched from Arch to Ubuntu, and I can't get my Intel 2200BG to work.  The doc system for Ubuntu is not very navigable, and therefore sucks.  I don't like having to go to google to find docs when I should be able to use the search box on my build's site!  WTF!

The 'Wireless' button on my lap. works in Arch, but not Ubuntu.  I've tried both a desktop and a laptop in Ubuntu with wireless.  One is natively supported (or so they say,) and the other I've tried the Community docs for ndiswrapper.  NEITHER has worked.  NEITHER has given me a wlan0 interface.  Only eth0.  And I'll be damned if I can find Ubuntu docs on the problem, or very much in the way of basic info regarding config files for Ubuntu.

This sucks.  Ubuntu documentation sucks.

I cut my Linux teeth on Gentoo, and had an easier time finding what I needed.  The only bad part was compiling w/ every upgrade or install.

I give up.:confused:

---

### Post by wavell2003 on 2007-10-27
hp compaq nx6310
Had do many partial upgrades plus some troubleshooting to get this upgrade to work
Needed to replace my /var/lib/dpkg/status file (I have to do this often during large upgrades) with an old one
Had to do a apt-get remove uml-utilities (I guess I didn't need this) but somehow this was affecting ubuntu-desktop
Had to add noacpi to my kernel line in grub

Then my desktop actually allowed me to open windows.

Some things I've noticed in these first 5 minutes.

1) The refresh rate on the windows is a lot worse.  when I drag a window it looks quite choppy.
2) I see a blue tooth icon now which I am definitely going to play with :)
3) All the icons in the menu list look better/more professional
4) My wireless config is amazingly still working.  I have been using the wifi-radar app to configure my wifi

**Edit**

I'm going to blast my machine and reinstall fiesty.  I can't get compiz/metacity to stay up without crashing.  I tried uninstalling compiz but the crashes are still there.  I read somewhere that there may be a problem with WINE fooling around with the windows decorators and confusing metacity.

---

### Post by paulkater on 2007-10-27
I can relate.
After a long consideration I set up 7.10 (sorry, not yet current with all the names) on my HP DV6137, and there I sat, looking at a stack of problems.
I am now downloading the 7.04 DVD image and set that up when it is done.

On my main PC I run Linux since almost 10 years and want the notebook on Linux also.
Glad I found the advice to use the previous release. Thanks, all!

---

### Post by objem on 2007-10-27
I have a dv6000 and everything works fine except the nvidia proprietary driver. Upgraded from working Feisty with absolutely no problems apart from that.

So I don't get the cool new graphics effect just the basics. From what I read this is a nvidia problem with the Linux driver for my card however. Hopefully nvidia opens the source so these things can get fixed!

---

### Post by Big Grizzle14 on 2007-10-27
Truly bizarre.

I'm using a HP DV6000. I did the upgrade via synaptics and everything worked. Sound, Compiz, DVD playback, IR Remote. Being a particularly thourough dude, I decided to back up my stuff and do a fresh instal using the live CD. Again everything works. 

I am amazed at the number of people with the same or similar laptop as I, that are having problems. :/

---

### Post by komsas on 2007-10-27
I`m using Gutsy on my hp6129eu laptop and "all" problems witch I had in Faisty like WPA, CPU frequency disappeared but now I have one big problem. Sometimes my Gutsy freeze. I must restart laptop, because sound, keyboard and mouse freeze. I thought that it is problem with compiz but I turned it off, problem is still here. I found same problem in others posts but there no answer. Someone have same problem or know how to solve it? :)

---

### Post by ag65151 on 2007-10-27
I have an HP Pavilion ZE5500 laptop and it has taken me a week to get all the bugs worked out. The livecd boots with a garbled display, but booting in "graphics safe" works. 

I have a Radeon IGP 340M card that has always been borderline with any Linux distro I've tried, but with Ubuntu 7.10 it works great. It is not the most robust of cards and I still get the medium level of "visual effects". I won't even try the high level. 

I also have a Broadcomm 34xx wireless card that didn't work "out of the box", but when I used ndiswrapper with the M$ drivers works great. 

I chose to do a fresh install since my /home is on a separate partition from /. This cleaned up much of the problems I had introduced in trying to fix things in the past.

Overall, I have found 7.10 to be better than 7.04. I have better speed even with visual effects. The feel of the system is more stable and I don't have any doa apps that I use everyday. 

Yes, I said it took me a week to get all the bugs with my particular hardware worked out. But I enjoy working to have a great product. I don't have a bunch of things installed that I don't need or want. I have a very trim (less than 3GB) OS with the vast majority of my hard drive available for data.

Well done Ubuntu team. Thanks for a good distro. I would say great, but I had too much "tweaking" to do to call it great.

---

### Post by paulkater on 2007-10-27
Things are looking grim again.
I downloaded the DVD for 7.04 and burnt that (MD5Sum was okay).

I boot from the DVD and all seems to go well, until X loads. I see the 'x' cursor, then the sound goes "plonk plonk plonk". Clearly something is thrown in a loop. Sound continues to go plonk,plonk, until I switch off the notebook, and that is all that continues. Loading from DVD stops, nothing appears.

What could I do?
The kernel parms I use to boot, additional to what Ubuntu suggests, are

pnpbios=off noapm noirqdebug acpi=off

Am I missing something?

---

### Post by mirek on 2007-10-27
hello ag65151

i am the owner of igp 340m at my compaq presario 2570us also, but never had so much problems to set it up like in 7.10. can you please send me your xorg.conf?

---

### Post by rabzzz on 2007-10-27
Hi All

I'm newbie here, and newbie on ubuntu too...

First, sorry for my english haha... you will know why haha

So Slash123 you said, we can ask you about if we need help on HP nc6000 Laptop.

my problem is  : Wifi card ( intergrated) is not recognized by Gusty.

Do you have any solution?

ps : i hearded about a Cd Version with Hp driver inculded.. where can i find it ?

---

### Post by tomWright on 2007-10-27
Too late.

I am using an HP zd8000 and upgraded due to the upgrade notice I received.

Now the system stops whenever I visit some pages in FF.

Example:
[http://www.thesun.co.uk/sol/homepage](http://www.thesun.co.uk/sol/homepage)

Will stop the system every time, black screen, drive stops, no log entries that I can see.

This is using the latest Gutsy release and FF 2008:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.8) Gecko/20071022 Ubuntu/7.10 (gutsy) Firefox/2.0.0.8

The problem is that I can not anticipate what will crash the system. I follow a link and without warning, black screen.

Is there a way to back this out, since it seams that while I can still boot the Feisty kernel, I am unsure there are other problems now, such as messages that flash on boot about not being able to allocate PCI memory areas.

---

### Post by THEDARKNESSHASCOME on 2007-10-27
> **tomWright said:**
> Too late.

I am using an HP zd8000 and upgraded due to the upgrade notice I received.

Now the system stops whenever I visit some pages in FF.

Example:
[http://www.thesun.co.uk/sol/homepage](http://www.thesun.co.uk/sol/homepage)

Will stop the system every time, black screen, drive stops, no log entries that I can see.

This is using the latest Gutsy release and FF 2008:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.8) Gecko/20071022 Ubuntu/7.10 (gutsy) Firefox/2.0.0.8

The problem is that I can not anticipate what will crash the system. I follow a link and without warning, black screen.

Is there a way to back this out, since it seams that while I can still boot the Feisty kernel, I am unsure there are other problems now, such as messages that flash on boot about not being able to allocate PCI memory areas.

i think your srew - ed but i have a friend that uses an hp with gutsy and runs just fine

---

### Post by iamdavid on 2007-10-27
> **Big Grizzle14 said:**
> Truly bizarre.

I'm using a HP DV6000. I did the upgrade via synaptics and everything worked. Sound, Compiz, DVD playback, IR Remote. Being a particularly thourough dude, I decided to back up my stuff and do a fresh instal using the live CD. Again everything works. 

I am amazed at the number of people with the same or similar laptop as I, that are having problems. :/

What specs are in your 6000? been hesitant on installing 7.1.... Mine is the dv6000 dv6305us

Thanks,
david

---

### Post by bg1256 on 2007-10-27
Hi all,

I'm wondering if these problems are limited to HP notebooks, or if desktops might be affected as well.

I realize it's not the topic of this thread, but I thought I would ask just incase, as I have both an HP laptop and HP desktop.  Both are over one year old, so maybe it's not an issue...

---

### Post by TroutStalker on 2007-10-27
Hi all,

I'm trying to install gutsy on a compaq x6000.  I can boot both the install CD and the live DVD.  Things look good - sound display, wireless etc.  However, when I click on the install icon I can choose the language and, sometimes, the timezone before the system dies.  A complete poweroff.   

I'm very disapointed.  I'm running Feisty on my desktop and was looking forward to getting the laptop off of SUSE.  I'm not sure what I'll do now.

---

### Post by #Reistlehr- on 2007-10-28
Guess im lucky. I got Gutsy running pretty decently (But still not 100% happy) on my dv9000z.

Biggest problems:

gnome-panel takes 2 minutes to load after login when compiz is enabled. Had to tweak suspend to get it to work. No smp.. Gutsy has improved support for batteries and ACPI i personally feel. But, i made a review thread in General help. if ou go read it, you'll see what i have and don't have working (find it by searching threads i've posted.)

---

### Post by headlessspider on 2007-10-28
hi, i guess i'm one of the lucky ones.

i have an hp compaq nx6120. pretty stock -- 256 meg, runs on 1024x768. i was able to install 7.04 on it using the alternative cd. the desktop install cd just didn't work for me. a day after 7.10 came out i upgrade via the network (internet actually) and it went fine. most of everything works fine except for

1. the mmc/sd reader -- i haven't fully tested it because i think the 1 gig mmc card may be borked in the first place. but 7.10 doesn't mount it.
2. it seems it is having sleep problems. i'll dive into that later.

---

### Post by Cyber-J on 2007-10-28
> **bg1256 said:**
> Hi all,

I'm wondering if these problems are limited to HP notebooks, or if desktops might be affected as well.

I realize it's not the topic of this thread, but I thought I would ask just incase, as I have both an HP laptop and HP desktop.  Both are over one year old, so maybe it's not an issue...

I can say that the video (specifically dual display and/or external monitor setups) problems are NOT limited to Hp notebooks as well as not limited to NVidia but also Intel and ATI graphics. Something that was specifically incorporated into Gutsy that wasn't in any of the earlier versions that broke the whole thing. I had problems getting correct resolution on an external monitor with Feisty but installing the proprietary video driver fixed the problem. I'm thinking that it is the so called "bullet proof X" that could be messing things up but it's just my theory.

---

### Post by wilmark on 2007-10-28
I just signed up and have been trying to get Gutsy working on my brand new HP Pavilion 9628. I was about to ask for help setting up sound and the nvidia stuff, but after reading this i will just install 7.04 over this and hopefully get that working. 
I've been using Debian for nearly five years on desktops and acer laptops (all older rejects), but with this new HP it couldn't get ethernet working so here i am a newbie to Ubuntu.

---

### Post by daanemanz on 2007-10-28
No problems at all on my dv6137eu! The only thing I had to do was booting the livecd with noapic irqpoll noirqdebug options. When using only noapic nolapic, the USB ports disable after a minute or so... Now it works like a charm, even by Broadcom wireless is working with WPA2.

I've heard a lot of trouble about gutsy on HP laptops, and at first this made me hesitate whether I should install it or not. But now I'm glad I did, it's just a matter of trial&error and browsing the forums.

---

### Post by Cyber-J on 2007-10-28
The video to external monitor issue is the only thing giving me problems with Gutsy. When the laptop is un-docked, video to the laptop's LCD is fine. It is when I dock it that output to the external monitor gets screwed up or becomes just a blank screen. I might try reinstalling feisty and then upgrading to gutsy again to see if that fixes things. I had originally upgraded from feisty to gutsy during the beta and it worked well but I decided to go with a clean slate upon the official release.

---

### Post by Madmoose on 2007-10-28
I have to agree you all here. 7.04  I had almost everything working great, but not with gusty. Finally unistalled Ubuntu off my laptop all around. 

I really liked how the headphone issue I was having was fixed, and that my wireless worked out of the box. Yet, I got sick of my sound only working every other boot, and a list of others. Mostly with programs such as flash not working. 

Anyway, I think I'm going to wait a few months to reinstall Ubuntu on my laptop. Though, I'm having the same sound issues with my two other Ubuntu computers.

---

### Post by EXCiD3 on 2007-10-28
I strongly encourage everyone to continue to use Feisty until we have more information on fixing Gutsy's problems. If anyone would like to contribute their experiences on my website, register and contact me so I can give you priviledges to write articles. I am looking for authors who own HP laptops to contribute their thoughts on Ubuntu and HP/Compaq laptops. If ANYONE wants to help please contact me! The site can be found here: [http://excid3.my2gig.com/wordpress](http://excid3.my2gig.com/wordpress)

---

### Post by digitalgecko on 2007-10-28
I just upgraded by dv5000 hp laptop and it worked flawlessly. Actually improved my Broadcom connection.

---

### Post by jctaft on 2007-10-28
Well I have the hp zv5000, and I just upgraded to gutsy a week or so ago and everything that worked before still works.  Sound, video, nvidia driver, etc.  I still have no wireless for my broadcom 43xx, but I haven't had that working since dapper and I got fed up with trying every how-to in the world, so I Just gave up.  I also don't have dvd support, but I didn't get that working even with feisty, so who knows.

---

### Post by taleg on 2007-10-28
I've done a clean install on my Hp pavilion dv9550eo and the only problem so far has been:

- No camera support
- Haven't tried the card reader, but as far as I've read on the net that does'nt work either.
- I have'nt been able to get the lauchpad buttons to work properly, but I have'nt tried that hard either
- Had to do some manual configuring to get audio to work

Every ting else works as it should, I haven't tested everything yet, but none of the problems described i this thread has occured. 

Simply put the only thing it lacks are some small tings enabled out of the box (like dvd, xvid and mp3 playback or at least a very simple way of adding them for first time users), better hardware support (It would be nice if everything worked, but I'd guess they get around to it eventually and if hardware suppliers could make proper drivers for linux in the first place)

Love it...

Taleg

---

### Post by jbaerbock on 2007-10-29
I have an HP zv6000 and Gutsy worked fine except a few easily fixed querks. Wireless needed a script I found online to be run but otherwise works fine.

---

### Post by s57nev on 2007-10-29
What about nx7300. I happen to own one and I use it for work. That's why i can't afford using broken wireless or something like that. Anyone with same laptop ? 7.04 works like a charm. It uses ipw3945 module for wireless and has Intel Mobile 945GM graphic. 

Is it safe to upgrade yet ?

---

### Post by shadowhywind on 2007-10-29
I installed gutsy a day or two after it came out on my dv6000 and I had no major issues. I did have to downgrade the nvidia drivers to eliminate random freezes and flickers of the screen. Suspend and Hibernate works fine for me * i am using s2disk for hibernation*. Compiz-fusion also installed with no issues. Built in webcam also works. the broadcom 4312 is also working *using it to write this*. every bodies computer is slightly different, with its own personality, The only way you know if gutsy is going to work is do upgrade and see. Just make sure you do it when you have the time to fix the random bugs that may happen.

---

### Post by neutro on 2007-10-29
> **headlessspider said:**
> hi, i guess i'm one of the lucky ones.

i have an hp compaq nx6120. pretty stock -- 256 meg, runs on 1024x768. i was able to install 7.04 on it using the alternative cd. the desktop install cd just didn't work for me. a day after 7.10 came out i upgrade via the network (internet actually) and it went fine. most of everything works fine except for

1. the mmc/sd reader -- i haven't fully tested it because i think the 1 gig mmc card may be borked in the first place. but 7.10 doesn't mount it.
2. it seems it is having sleep problems. i'll dive into that later.

Just to add one data point to the benefit of those performing searches in this thread for specific models -- I confirm headlessspider's results. I have an HP/Compaq nc6120 with an Intel video card and an Intel wireless card, and upgrading to Gutsy from Feisty seemed to work flawlessly. 

It's only been a few days so I can't say anything about sleep problems and haven't tested the memory card reader, but everything else (sound, video, multimedia buttons on the keyboard, sleep mode, wireless connexion etc.) seems to be working good for now.

---

### Post by mock_alien on 2007-10-29
I have a 9000 HP Pavilon Laptop (1.86 C2D 2GB)

I did an upgrade to Gutsy.
(i used i386 (32 bit) feisty live cd before, which installed everyting flawlessly i i thought gutsy would do the same)
When i rebooted i lacked a lot of hardware support. I was really disapointed (and spent some hours cursing and so until i tried something)
For some reason the i386 was the first kernel to be loaded. When i switched kernel to -generic everything went so much smoother, wireless, sound graphics worked!
(i still have some problems with random freezes and sometimes my satadrives dies. (suddenly maps are empty. I have tried noapic command in grub, but it proved dissatrous (as nvidia graphics faild to be  detected) - just a side note, my graphics display is not yet correctly detected. Iaws forced to do a "sudo nvidia-config" to have the right refreshrate et.c.

Hope they will make a 7.10.1 release with the problems fixed so i dare to upgrade my parents computer.

anyone know how to check satadrives drivers et.c.? why isn'y my noapic command working? (does nvidia restricted need to me configured?)

is i wrote i did a upgrade. and i was wondering if i should do a clean install just to be sure.

---

### Post by ChristDude on 2007-10-29
Will a fresh Ubuntu install on this Compaq Presario V2000 laptop be fine? I know the Broadcom wireless drivers won't work until I work with those, but everything else should be fine, right?

---

### Post by swoskow on 2007-10-29
I have an HP dv2000 that I dual boot (I need XP for work) with XP on the hard drive and Ubuntu installed on a usb external hard drive.  I boot Ubuntu with grub from the usb drive.  Mostly the install went well.  The following are the main problems people have and how I got them to work:

video drivers - Nvidia worked for me right out of the box using the restricted drivers.  
Wireless: not so easy -  I have the broadcam chip and the wireless initially worked from the restricted drivers but for some reason it stopped.  I tried the Windows driver in ndiswrapper (installed in Gutsy) but that did not work either.  I uninstalled the ndiswrapper and reinstalled the latest version from sourceforge following how to's in the forum- worked great.  I also installed wcid because it just did a better job than the native network manager.
Video and audio:  No problem with video.  I like smplayer for watching videos.  I downloaded a few codecs and worked fine.  Audio though initially worked but stopped for some reason.  I found a post that suggested unplugging the power cord and checking the sound.  For some reason the sound worked when I unplugged it.  I added the noapic to my boot and the sound works great now.
Others:  Everything I have used works fine (Samba, Lamp server, email etc).

For those of you that are leary about switching you might try it from an external usb hard drive first.  it is easy to set up - just take out your main hard drive, connect the usb drive and install Ubuntu as you normally do.  If you can get everything working from the usb drive then go ahead and make the switch on your main hard drive.

Also, try a fresh install instead of an upgrade.  It seems a lot of the problems are related to having tried too many tweaks and a fresh install sometimes solves the problems.  Make sure you backup - or make a separate home partition.

I hope this helps.  FYI - at the same time I was installing Gutsy I had a problem with a Windows computer and I had to reload XP.  It isn't a piece of cake either - I had to search for drivers, reinstall codecs etc etc.

---

### Post by ityro on 2007-10-29
I have an HP/COMPAQ nx9010. I did a fresh install of Gutsy 3 days ago and have had  no problems. In fact it has cleared up some Gnome problems that an upgrade from Feisty to Gutsy did not help. Fresh install did the trick and I have not found any new problems.

---

### Post by Dave in Tempe on 2007-10-29
I have a zv6000 and by-and-large Gutsy has worked great for me.  I would even say it's a substantial improvement over Feisty.  Compiz works much better.  The only problem I have now that weren't there before is that I cannot suspend/resume, but that's because I have an ATI card and use fglrx.

---

### Post by Symbolis on 2007-10-29
7.10 runs(mostly) fine on my HP Pavilion dv5000(EZ524UA#ABA) laptop. Only issues I have are:

1) "Cannot allocate resource..." error(PCI thing) that a number of people have experienced. Slows down boot a bit.

2) Trying to get either Compiz/Compiz Fusion working(ATI Radeon Xpress 200M card. Blargh)

3) Getting City of Heroes/Villains running under wine(with above-mentioned graphics card. Graphics are all...echo-y.)

More to come, maybe. ;)

---

### Post by geordee on 2007-10-29
I have problems with sound and wireless. Sound worked for me first, but suddenly it stopped working. Wireless does not work. I keep entering the keys, but Ubuntu doesn't seem to care!

By the way, I could not install Gutsy from a Live CD or Alternate CD. The install would stop during software setup. Unfortunately :(, I was determined and installed a command-line system first. Then I "apt-got" ubuntu-desktop from Internet.

Let me now try out various suggestions in this forum.

---

### Post by geordee on 2007-10-30
Strange things are happening. In an attempt to recover sound, I added noapic to boot options and the sound vanished - completely. Gibbon offered me to remove volume applet as well. Thinking that I was better off earlier, I edited menu.lst to remove noapic grafts and rebooted the machine.

Voila! Gibbon greeted me with the familiar Ubuntu drum-beat. It didn't stop there... more surprises! I changed my wireless router to broadcast SSID, and it was detected, and the gibbon asked me to enter WEP key. It works now... cool!

Monkey business. What else?

---

### Post by dahoba on 2007-10-30
Hi every one that use HP Laptop. I want to share this information with the hp laptop community. I use HP dv2018tx and just try to (fresh) install **Gutsy amd64 DVD** and everythings goes great! :D 

 - No ethernet hang (with Yokon ethernet)
 - Nvidia and Compiz work great
 - dvd-rom, headphone work fine.
 - card reader work
 - wireless (intel) work great

I'm didn't test webcam right now, but I think it's also work too ;)

Note: I test once with gutsy amd386 live-cd but hang on screen rc.local loading...

---

### Post by swoskow on 2007-10-30
> **geordee said:**
> Strange things are happening. In an attempt to recover sound, I added noapic to boot options and the sound vanished - completely. Gibbon offered me to remove volume applet as well. Thinking that I was better off earlier, I edited menu.lst to remove noapic grafts and rebooted the machine.

The post I read in the forum that gave me the info on noapic said to first try the sound with the power cord unplugged.  If it works with the power cord unplugged (but not when it is plugged in) then add the noapic to the boot.  This worked for me.  Most people should try this first before you do the noapic.  If the sound does not work with or without the power cord plugged in then noapic may not fix it.

---

### Post by TheGibson on 2007-10-31
Thank God I found this thread.  I've been trying to get Ubuntu on my HP dv6140us and nothing iis really working. Had to go to the alternate ISO to get it to start the process at all.  Tossing my Gutsy ISO.

Thanks!

Question though: which distro should I try?  I'm looking for something to ease myself into Linux as a learning experiment and don't have a ton of time to do major tweaking (new baby, going to school, working ...) Should I go back to Fawn or over to Linspire or...what?  Is there something that seems to work better with HP6000 series laptops?

EDIT: Oh, and I've searched around but haven't found any info on my particular install.  When I first put XP on my laptop. I left a 14GB partition open to install Linux on later.  I'm assuming this is no problem and you get to choose your partition before it installs, but having never done this I have no first hand knowledge.  Anything I should be looking out for?  I will also continue searching the forums and knowledge base, but thought I'd ask here too.  Thanks.

---

### Post by geordee on 2007-10-31
> **TheGibson said:**
>  I left a 14GB partition open to install Linux on later.  I'm assuming this is no problem and you get to choose your partition before it installs, but having never done this I have no first hand knowledge.  Anything I should be looking out for?  I will also continue searching the forums and knowledge base, but thought I'd ask here too.  Thanks.

A 14GB partition is good enough. Ubuntu installer has a menu for partitioning. Select Manual partitioning, and assign the partitions to mount points. I'd prefer having a separate partition for swap. You will get more information on this if you look around a bit. I could not install Gutsy in a straight-forward manner. If the alternate CD fails while setting up software, try installing a command-line system and get the package ubuntu-desktop using apt-get.

Gutsy comes with NTFS write support which is something you may like. There are other ways to get this though!

---

### Post by EXCiD3 on 2007-10-31
I would recommend using Feisty on your laptop. Installing Ubuntu will automatically install Grub (a boot loader) and will automatically setup your laptop to dual boot most any OS you have currently installed. It should automatically give you options for Ubuntu and XP.

> **TheGibson said:**
> Anything I should be looking out for? I would recommend reading through and following my Howto for Feisty. It covers most problems that you will run into. You can find it here: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

Good Luck!

---

### Post by TheGibson on 2007-10-31
Oh, does anyone here have an opinion on Edbuntu?  I'm getting my teaching license and am fascinated by the possibilities...

---

### Post by mgaskell on 2007-11-01
I have a three year old HP Pavilion dv1000 laptop. Feisty was great. Gutsy is a major pain. My sound is OK but often the system hangs or crashes. Selecting a link in Firefox sometimes causes the browser to dim and lock. I have to "force quit" do to non response.

Often when I just put the cursor over the "Applications" in the bar the drop down menus will drop down and the system freezes. If I wait for 30+ seconds I usually regain control.

I hope the package manager will put out patches without me having to wait for the next release.:(

---

### Post by finite9 on 2007-11-01
Is it really valid to say that the problems encountered are "HP Problems"?  Isn't it the case that the problems experienced by all these HP users are down to the graphics chipset or the wireless chipset or the ATA controller used etc etc etc.  To say that "HP's have problems with Gutsy" is a bit too broad a statement.  I have a Pavilion dv9297ea with Fiesty, and have not tried Gutsy yet, but as far as I know, there are no issues with Intel PRO Wireless 3945 or nVidia Go 7600.

---

### Post by EXCiD3 on 2007-11-01
Yes, but these problems are generally found in the AMD based models. Congrats, you lucked out and purchased the extremely compatible HP laptop like I did. It is another story to install Fiesty on the other laptops. Boot parameters just to get into the live cd...sometimes tty job control...wireless hassles...we just lucked out. :)

---

### Post by evolutionx on 2007-11-01
> **old_salt said:**
> If you have an HP Laptop - especially an HP 6000 or 9000 series laptop, steer clear of Gutsy 7.10 release. 

Too many hardware issues, lack of available apps to satisfy dependencies and less than half the available programs as found under Feisty 7.04 release. 

Not sure what happened here but I can't even obtain the necessary requirements to even compile from source. Hardware is not supported and despite the efforts of many in submitting to the hardware database for developers to support this platform, it appears everything went to the "bit bucket".

About the ONLY thing they did right was provide the Broadcom wireless nic firmware via the restricted drivers option and that was it.  Nothing else works. You can't even manually fix the problems because the tools to do so are not available. 

PLEASE PLEASE stick with Feisty or whatever distro you may have used before in efforts to send the message to the developers that they missed the boat BIG TIME on this release.

As a 20 yr professional, I cant recall a release take such a large step backwards. I'm beginning to wonder if this release is for Dell only.

I've just installed Ubuntu 7.10 x86_64 on a HP Pavilion dv9514TX Notebook for the first time and couldn't be happier.

The installer picked up the majority of my devices straight away. Only thing I have not tested is the built in webcam (which i dont use much anyway) and the bluetooth. The wireless worked straight away even off the live CD. Nvidia drivers installed fine and Compiz was running with in minutes.

Only issue encountered was the sound drivers, install detected the Intel HD audio sound card but no sound was present. Compiled latest ALSA drivers, very quick fix.

Very happy with the install!

HP Pavilion dv9514TX Notebook
-- 2.0 GHz Intel Core 2 Duo processor T7300
-- 2048 MB DDR2
-- NVIDIA GeForce 8600M GS
-- Intel PRO/Wireless 802.11a/g/n WLAN
-- 5-in-1 integrated Digital Media Reader for Secure Digital cards,

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01178406&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01178406&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

---

### Post by theox26 on 2007-11-01
I admit I didn't read all the posts, but it's not just the AMD laptops.

I have the DV5000 with an Intel processor and chipset, wifi, SATA controller, etc.  The upgrade killed it, the video didn't work and I don't know what else cuz the video didn't work.

When I went for a full install it didn't see my partition table, normal or alternate version.  So I'm stuck going back to fiesty for the time being since i don't want to lose my other partitions.

I really hope they fix this, but I can't say I'm holding my breath.  Though I am using this opportunity to try some other distros. Haven't liked any so far though.

---

### Post by QkEterror on 2007-11-01
Talking about fixing... Is there anyone from Canonical who can tell us if there is going to be a fix and if it will come could he/she give an estimation of the time it's going to cost?

---

### Post by gillis on 2007-11-01
I have a nc8000 equal to a nc6000 but with firewire and 1400x1080 resolution
7.10 is running, but there are some problems.

i am running the default install with opensource ati drivers.

- sometimes i get lockups when i turn the cube in compiz.
- the fan inside the computer is running almost all the time. Is this because compiz is enabled? anyway ubuntu is making the cpu hot without doing something.
- i got pci not responding during boot. is this maybe the ir device?
- computer wont wake up after sleep. maybe ati related.
- I cant get lirc working with the infrared device. that sucks.

besides these problems ubuntu is running nice. fast, and except for the turning cube thing very stable.

---

### Post by vogellied on 2007-11-01
I did an upgrade onto a HP NC6220 from 6.06 and 7.04, both worked though a few broken library's did emerge (though I think this is an issue with the upgrade route I have read a time or two before). The bulk of the upgrade worked and worked very well. In fact an ALSA (I am guessing) issue I had (that I never bothered to trouble shoot) where I would loose audio switching inbetween users and coming out of stand-by was fixed. I did a clean install on a HP NC600 and a NC6230 and I had NO problems (though I now have a long load time issue since I then rebuilt in a dual-boot configuration). I am sorry to hear about the above scenarios and just wanted to temper that with my positive experience with both the upgrade and clean install process. I also think that if you can make it work, it is very worth while. Many of the added bits are superfluous to the power long time user, and a thrill to the newbie, but I would think even the long time user would find it worth backing up their current data and giving it a shot. The newbie bits (i.e. deskbar applet, system admin. stream lining, added basic folders) make it an even easier sell to newbies for the experienced person looking to convert. Cheers!

I haven't tried to run Compiz/Beryl bits on any yet, so I son't know if I would have the same experience as gillis.

---

### Post by Beernut on 2007-11-01
I upgraded my HP dv6000 from 7.04 to 7.10 and seems like everything worked wireless included except I didn't have any sound.  I haven't tried the compiz stuff I really don't have any need for spinning desktops.  Anyway the thread below fixed my sound issue very easy to do.

[URL="http://ubuntuforums.org/showpost.php?p=3677919&postcount=3"]
Recompile alsa drivers and downgrades to version 14.[/URL]

---

### Post by KevinCLovesU on 2007-11-01
Hey everyone. I got my dv6500z (yay!) but I've decided to be cautious and use Feisty. The LiveCD doesn't get me anywhere (apparently it's my AMD processor) so I have the alternate 64-bit disk in the drive right now. I'll tell you how it goes when it's all over.

---

### Post by Speedboxer on 2007-11-01
I have a Compaq Presario F565CA, and LiveCD won't even load. The loading bar just freezes, and the DVD drive powers down.

---

### Post by gubemton on 2007-11-01
I have a dv6258se: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00847924&lc=en&cc=us&dlc=en&product=3340175&rule=41746&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00847924&lc=en&cc=us&dlc=en&product=3340175&rule=41746&lang=en)

Ubuntu (7.04/7.10) has buggy kernels, in order to not require 'noapic' to boot I have to compile the source from kernel.org. I've also tried Slackware and its included kernels don't have any problems with the hardware to require noapic or other kernel parameters. noapic causes flaky USB / not work at all and various options like 'irqpoll' for some reason disable power management (always runs at full speed / no battery detected / etc). So by compiling a new kernel, I don't have to use any additional kernel parameters or give up anything.

Also, the onboard video (GeForce 6150) isn't supported by the 'nv' driver in any distro, so I have to use the installer from nvidia.com for that.

---

### Post by offchance on 2007-11-02
I am running a V6000z/AMD with Gutsy and it works better than with Feisty. I used to have to boot with "noapic nolapic irqfixup" and now I can boot without nolapic. My wireless works better with ndiswrapper. The only weird thing is that Gnome loads up a little slower (and without a splash image with little icons), but besides that it's been running without incident.

---

### Post by TRStealthX on 2007-11-03
I couldn't even get gutsy to install properly. Tried it with feisty and what do you know!

---

### Post by EGRAD on 2007-11-03
I have a hp dv9000. I can't even get gutsy to go past the "start/install" screen with the live cd. I guess I'm no the only one. I'll stick with feisty. on another note gutsy works great on my dell desktop. 

I'm glad I didn't spend hours trying to figure it out. 

Is there a stable emerald for gutsy. I have problems with it. 

Thanks

---

### Post by Gideon147 on 2007-11-03
Not just HP. Too many issues. I upgraded my Dell Inspiron 4100 from Feisty to Gutsy.

It's been a 3 day nightmare. Day 1 after initial upgrade I noticed I didn't have the Cube or Wobble. No big deal, but I liked the cube and my wife liked the Wobble. So I turned to this forum and dozens of other websites for support. Day 2, after 7 hours of "fixes" I lost resolution of my monitor to a measly 800x600. Day 3, after an additional 4 hours of "fixes" I lost the ability to log in to anything other than GNOME failsafe, but I did get my resolution back.

All for a stupid cube. I've scrapped 7.10 and am reinstalling Feisty. These elements that Feisty came packaged with are what will mean the difference between a Linux or Vista household. I'm doing my best but Gutsy can't back me up. Back to Feisty.

---

### Post by cyb3rj on 2007-11-03
> **ag65151 said:**
> I have an HP Pavilion ZE5500 laptop and it has taken me a week to get all the bugs worked out. The livecd boots with a garbled display, but booting in "graphics safe" works. 

I have a Radeon IGP 340M card that has always been borderline with any Linux distro I've tried, but with Ubuntu 7.10 it works great. It is not the most robust of cards and I still get the medium level of "visual effects". I won't even try the high level. 

I'm having a dickens of a time to get my display to use anything other than the vesa driver.  What was your trick?

---

### Post by ag65151 on 2007-11-03
I added one option to the Device section of xorg.conf that cleared up all of the video issues I have been having since Feisty. It's awesome. I get the compiz eye-candy as well as AWN working great. I haven't tried to up my video to the "high" mode, but I get all I want at the intermediate level.

Back up your xorg.conf file before modifying!!!!!!!!! I have really screwed up my system by forgetting to back up. 


Modify your /etc/X11/xorg.conf as follows:

```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon IGP 330M/340M/350M"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        option          "LVDSBiosNativeMode"    "off"
EndSection

```

---

### Post by s_raghu20 on 2007-11-04
Hey guys,

I have a Compaq 6710b with intel X3100 Graphics adapter.

In Feisty it was possible to get compiz working (with a few limitations), but in Gutsy it just doesnt work. Doesnt even give a proper message.

My Gutsy is an upgrade from Feisty. Does anybody here has any tip for X3100@Compaq 6710b ?

regards
raghav..

---

### Post by mimsmall on 2007-11-04
Gutsy installed on my hp pavilion ze4400, AMD Athlon XP-M, mobile. Everything works with the exception of the Gutsy cinelerra package I added after installation.

Perhaps the HP and Gutsy problems are only occurring with the newer model laptops.

---

### Post by jhyatt7823 on 2007-11-05
I'm running 7.10 on a dv8000 and I am not experiencing any of the problems being talked about so far.  But I am a relative noob and probably don't know whats good or bad :confused:

---

### Post by QkEterror on 2007-11-06
> **ag65151 said:**
> I added one option to the Device section of xorg.conf that cleared up all of the video issues I have been having since Feisty. It's awesome. I get the compiz eye-candy as well as AWN working great. I haven't tried to up my video to the "high" mode, but I get all I want at the intermediate level.

Back up your xorg.conf file before modifying!!!!!!!!! I have really screwed up my system by forgetting to back up. 


Modify your /etc/X11/xorg.conf as follows:

```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon IGP 330M/340M/350M"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        option          "LVDSBiosNativeMode"    "off"
EndSection

```

Wooot!!! This works for me too! Thanks ag6515! You're a life saver

---

### Post by SomeGuyDude on 2007-11-06
HP dv6244us user here. Outside of not having my webcam work and some minor issues (wonky sound, network poops out when returning from suspend but this is just on my college network), it's been flawless.

I wouldn't have installed it otherwise!

---

### Post by joergmoe on 2007-11-06
I have a HP Omnibook 6100 and the following problem with Gutsy

- I can only start the GNOME desktop in recovery mode
- My notebook often turns off during boot process (since Kernel 2.6.20). 

I found a solution for the last problem in [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892)
Rename the file "intel-rng.ko" in "intel-rng.ko.off". This makes the file invisible to the boot process
The file is in lib/modules/2.6.22-9-generic/2.6.22-9-generic/kernel/drivers/char/hw_random/ 

This is not solved yet in Kernel 2.6.22 !

---

### Post by gimmy_bond on 2007-11-06
> **gcrussell1 said:**
> I'm running an HP zx5000 laptop - older generation (I think) than the DV line. Anyone know if the zx series machines work well with gutsy? I'm planning on dual-booting XP and Ubuntu to learn Linux, since I've never used Linux before, but I don't want my first experience to be a bad one. 

Any suggestions? Am I safe with 7.10, or should I try out 7.04 to start out?
I just moved from desktop to our old lady zv5000 (x64). So far the main engine seem to work fine. except wireless connection, is a bit challange. 
I would suggest to those wishing to upgrade to gutsy. just partition the disk for separate /Home drive and install gutsy fresh.

---

### Post by Asymmetry on 2007-11-06
I've got a dv8000 series HP laptop. I personally hate the thing, but that's the fault of the laptop, not Ubuntu or any other OS. I plan on getting a System76 when it comes time to get a new laptop.

Gutsy hasn't been too bad for me, so far. About the only *real* problem I've experienced is the colorful death of my ttys, something that annoys me to no end. That and the usplash resolution bug, but that's an easy fix.

To go more in depth, my ttys and such work just fine, up until I install the ATI fglrx driver. Once that's installed, I get all of my compiz eye-candy, but then my ttys are gone - All I get on tty1-6 are colorful vertical lines. After that, it took me about eight hours of digging to figure out why compiz didn't work from the start.

One odd thing I noticed during that process... The Restricted Drivers manager informed me that my ATI card (Radeon Xpress 200M) had non-free drivers available for it. So, I told it to enable them (I want compiz!) and it came back with a single complaint: "Package xorg-driver-fglrx not installed," or something along those lines. Last I checked, linux-restricted-modules-2.6.22 had the fglrx driver included. So what gives, there? Is that only included on the DVD, or something? I had to download the ATI driver from ATI's website and build that way.

Then I realized that compiz was set to not recognize the fglrx driver once it WAS installed, and I had to both whitelist the driver, and remove my GPU's PCI ID from the blacklist. Then everything was wonderful, except for one issue with compiz and the cube plugin. Every time I try and rotate using the keyboard shortcut, it skips every other desktop. If I'm on 1, and I Ctrl-Alt-Right, it goes to 3, then back to 1, skipping 2 and 4. If I'm on 2, it goes to 4, and back to 2. Same if I go the other direction. It's rather odd/annoying. For the time being, I've disabled the cube/rotate plugins.

Things would probably go alot different if I had access to a repo besides the install CD, but at my current location, that's no dice. The military is kind of anal retentive about hooking up personal computers to the network. :)

It's probably the closest to an OOB functional distro as I've seen. I'm about to install Debian Etch onto it and see what happens.

Edit: I wouldn't mind some help in trying to fix that tty issue, if anyone's got a clue. A compiz cube-skipping fix wouldn't be bad, either. Cheers!

---

### Post by Inxsible on 2007-11-08
an HP dv9000t user here.

I am VERY HAPPY with Gutsy. It has recognized more of my hardware than Feisty ever did.
Things that DID NOT work in Feisty, now work for me on Gutsy.
1) Suspend
2) Hibernate
3) Built in webcam with Kopete
4) Most importantly, my machine runs much quieter than it did in Feisty. In Feisty, the cpu fan was constantly on. I was worried about the life of my CPU. 
5) VGA
6) DVI
7) HDMI (honestly never tried this in Feisty -- but it works out of the box in Gutsy :) )

S-Video is the only thing that I haven't tried out yet in Gutsy, but I think it will work with "gksudo nvidia-settings". It didn't work in Feisty for me.

Number 4 alone makes me like Gutsy far more than Feisty. 

Rest all worked out of the box just like it did in Feisty 
1) nvidia graphics card (after enabling restricted drivers)
2) sound,
3) resolution, 
4) no need for any boot parameters
5) bluetooth(after installing gnome-bluetooth)
6) Wireless
7) all media buttons

All in all, a huge improvement over Feisty. I wouldn't go back to Feisty for anything.

NOTE: I moved from 32 bit Feisty to 64 bit Gutsy. I am not sure if all the above good things happened to me because of the switch from 32 ->64 or because of the switch from Feisty -> Gutsy. But either way, I am happy :D

---

### Post by ejb11235 on 2007-11-08
Oh yeah, us Dell owners have it made ... 

I just tried upgrading to Gusty on a Dell 530N with pre-loaded Feisty. I figured I didn't have to worry about hardware support issues because I already had Ubuntu running from the get-go ... that was one of the reasons I bought the Dell in the first place.

Now --> no network drivers...

---

### Post by manhinli on 2007-11-08
I too am very disappointed with Gutsy.

I had to manually get Dapper and Feisty to work on my HP/Compaq Presario F503 laptop (especially with acpi, apic and X.org/nvidia). That was some work.

Now, with Gutsy, it's worse! ](*,)

Here's what went wrong:

- noapic, nolapic, acpi=off had to be used in the boot sequence - I had to use noapic and nolapic for Feisty. Both terrible.

- Sound screwed up. When the CD started (and now on my normal installation) sounds would echo and repeat in small segments through the whole track (startup's terrible!). This was fixed only with the installation of nvidia-glx, but it too is terrible (read below).

- Display screwed up. Well, in Feisty, it got nvidia-glx-new, which was incompatible, and I installed nvidia-glx. Got the resolution right after ages fixing it. Now, in Gutsy, it also got nvidia-glx-new, but this time, installing nvidia-glx wouldn't let me get 1280x800! Editing xorg.conf would make it revert to 1280x768! Reverting back to good 'ol nv, but misses Compiz...

Not a happy camper here :-x

---

### Post by nnamdi on 2007-11-09
i have a hp pavilion dv6536en lappy dv6500 series and am not really feelin gusty on it cos 

1.got no sound on it
2.cant enable my webcam
3.cant enable my desktop effect man too bad

i really want to fix,cos iwant to say bye to windows and face linux sqaurely

---

### Post by kxr1der on 2007-11-09
So does anyone know if efforts are being made to fix the problem. I have a DV2000 running windows and i want to switch to ubuntu on it but if its not gunna work i will hold off i guess,

---

### Post by keskew on 2007-11-10
I have an HP Pavilion ze2000.  I tried to upgrade from Feisty to Gutsy and it did not go well.  I had a lot of problems.  Almost too many to work through.  So, I did a fresh install of Gutsy and almost everything worked out of the box.  For what it's worth.

---

### Post by fieldstone on 2007-11-10
I can confirm there are serious problems on my Compaq V3000 series laptop also. Makes sense, since it has mostly the same guts as the HP dv6000 series.

I installed Gutsy literally ten times, and every single time either network-manager suddenly started saying "no network interfaces detected", or Gnome refused to start with a message about a program using setuid or setgid improperly (usually related to compiz). I tried every fix I could find for these, with no success at all.

It seems to me Gutsy has the same problem as Windows Vista, much as I hate to say it - it was released before it was ready, and as a result it has a number of unfixable bugs. I am very disappointed, as I'm sure are all of you. I really hope whoever's in charge reads this thread.

---

### Post by maceintn on 2007-11-11
Let me say right off the bat that I have only read the first and last pages of this thread.

Also, I don't have HP laptops. I have an HP desktop. I've tried installing multiple UBUNTU versions, both regular(not sure what to call it) and alternative disks, without success. After this post I'm going back to the beginners thread.

The one thing I've noticed in these posts, I'm not seeing good explanations for these problems.

Well, Here I go again!

---

### Post by magicman5421 on 2007-11-11
For what it's worth, I have a hp dv9500 running gutsy and everything works ok. I mean occasionally my wireless stops working, and i've had 1 or 2 crashes, but i guess it comes with the territory. if you're not willing to work a little, then you might even be better off with windows (ugh...)

---

### Post by doctorbrowder on 2007-11-12
I am SOOOOO glad I checked the forum before I upgraded my HP laptop to Gutsy! I have it working like a charm with Feisty... I guess I'll wait until the next distro for the next upgrade. However, I did make the mistake of allowing the update manager to run the UPGRADE TO 7.10, which told me I had 500+ updates. Since I have a dialup connection, and it was going to take over 30 hours to download the updates, I hit cancel. But, now, is update manager going to keep insisting I get those 500+ updates, or can I cancel them somehow? Thanks!

---

### Post by Orval on 2007-11-13
> **shadowhywind said:**
>  the broadcom 4312 is also working *using it to write this*. 

How did you do that?

---

### Post by old_salt on 2007-11-13
Wow !!!! never thought this would have such a turnout. I appreciate everyone's posts as my attempts to escalate or call attention to the myriad of issues listed here have resulted in my getting beat up pretty bad by Ubuntu developers and staff, Excid3 can vouch for that.

What's new?

Most everything is working fairly well for my Dv9000 after approximately what... 30 some updates already posted? I have 2 major issues remaining. High Hardware interrupt utilization that only increases regardless of appended kernel parameters and inop USB (partially).

The noapic parameter still remains the d facto standard in order to install and run Gutsy and Feisty for me. All other parameters have adverse effects. I did discover that adding the irqpoll kernel boot parameter does resolve my USB issues but my Hardware Interrupts end up hovering between 80-90%. Not good unless you want to fry your system. If i drop the irqpoll parameter I must unload the USB2 module in order to use my USB ports in USB1 mode. This has also complicated the setup and synch to my Treo 680. 

Fedora 8 ran from live CD without any extra parameters. Performance was.... typical for a live CD. I didn't install because I left Fedora because the RPM package management system is experiencing serious issues - one tends to get caught in dependency he##. 

I can't say for sure what I plan on doing as it was a pain to get Feisty going but it worked. Gutsy DID overcome a lot of obstacles that no other distro has managed for 64bit users such as flash, java and multimedia codecs that are pretty much required in order to do anything on-line nowadays. Before you suggest running the 32bit version ------- I tried that. Hardware issues galore. Hey what do you expect for a 32bit OS on 64bit hardware? Performance also lagged terribly. 

I wished I had better news or info for everyone. I wished I could have reported back from a few weeks of MIA for experimentation and t-shooting to have everyone's answers but I'm scratching my head in disappointment. It would appear to me that in efforts to successfully ":Commercialize" Ubuntu to gain marketing and media attention, someone forgot to put the "Guts back into Gutsy". Also of note is KDE is lagging severely now with all focus and efforts being the Version 4 release next month which only supports my claims that I think it's ludicrous to try and maintain a 6mo release cycle - period !!! Maybe yearly would work but the entire community including all distros should be a coordinated effort really. It's unimaginable to think that a distro is having it's release weeks from the new release of desktop environment. I don't know, I think maybe the community has advanced as far as possible without some leading figure or committee to help facilitate and coordinate these events. It looks like we have an un-choreographed play going on and MS is sitting in the corner laughing away.

So much for my ramplings, thanks for reading though.

If I get answers I will post whatever works for me. You can bet on that.

Thanks everyone!!!!

---

### Post by Lometari on 2007-11-13
I have an HP nx6325. I had it working pretty well with Feisty, though I had no desktop effects and skype would break pretty much always.

I installed Gutsy from scratch last weekend. Everything started out well, but now I'm getting random gui freezes. I think I'll go back to Feisty for the time being. The Compiz effects are great but I cannot work like this...

---

### Post by Rubelcy on 2007-11-14
Tengo una Presario 565la, Y TAMBIEN opino igual que todos, gutsy a matado todas las esperanzas y mi capacidad de resolver problemas en ubuntu, por ahora les cuento que al instalar feisty y poner las nuevas actualizaciones se vulve loco y se pierde la configuracion de video y sonido.
Por otro lado si aun asi lhacen funcionar  a gutsy tomen en cuenta que el office, esta fallando al manejar las imagenes q se postean de calc, es decir que genera un proceso de recuperacion de documentos al manipular estas imagenes asi, que mejor si graban cada minuto. suerte.:confused:

---

### Post by wolfchri on 2007-11-14
If you experience problems booting the LiveCD or the Alternate installation CDs, please check my little howto for Gutsy on the NX6325 here, those tipps might help also on other models.

[http://vale.homelinux.net/wordpress/?p=202](http://vale.homelinux.net/wordpress/?p=202)

---

### Post by ayoli on 2007-11-14
I have a hp compaq nc6400 which seems to work fine with ubuntu 7.10 release.
I haven't yet tested suspend/hibernate and the sd-mmc card reader (which didn't work with feisty (7.04)).
I was just a bit surprised the first times because tracker deamon cpu usage, but this not hp related.

---

### Post by garitd on 2007-11-14
My dv2500t is loving Gutsy so far with only 2 exceptions.  On first install there was no sound.  But all i did to fix it was install the newest alsa and like magic it started working.

The only complaint I have is getting the wireless to work.  As far as i can tell it just cant see any wireless access points.. and therefore cant get an IP.

Seems like I am the only one who is having wireless problems.. and also the only one what doesnt have all the other problems.. lol

---

### Post by old_salt on 2007-11-14
I believe the key here is hardware detection. I broke out my trusted Knoppix CD's. I've always been amazed at how this flavor has been so great at accurately detecting hardware. When looking though all the postings not just this one, it all boils down to hardware detection. Plain and simple. Knoppix 5 booted up, detected everything including the webcam and worked. Now why can't other distro's adopt this method? I hope some developer or Canonical staff member reads this because if Ubuntu could do this with their next release, headlines would break; "Ubuntu rivals Windows:. 

Oh well.

---

### Post by sandstig on 2007-11-15
Practically everything worked out of the box on the HP 8510p. I installed the binary ATI drivers following _[these instructions](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3)_ so I could use my screen at 1680x1050 and it worked fine. When I heard about _[Envy](http://albertomilone.com/nvidia_scripts1.html)_, I decided to give that a shot as well, and things were pretty smooth. Much quicker way to get things going.

Now the only thing I need to figure out is the fingerprint reader. ;)

---

### Post by aydin on 2007-11-15
I have an HP pavillon dv6500. I installed Gutsy as dual-boot with vista. I have problems with graphics card (intel 965, blacklisted, cannot run compiz) and sound (there is none).

Everything else is OK (such as wireless). I hope that support for above features will be available in time.

---

### Post by methane on 2007-11-15
Does anyone know how to start diagnosing freezes?  I have an HP zv6000 running Xubuntu ,previously Ubuntu - both gutsy - and both distros freeze.  I didn't have any problems installing the restricted drivers for ATI and the Broadcom wireless.  

The freezing only happens sometimes.  I can sometimes go for days without a freeze.  Other times, a minute or less.  The commonality with the fast freezes seems to be a call to the wireless service.  I also think that using a bluetooth mouse was causing it to freeze as well.  The Bluetooth was iffy to begin with.  The mouse worked, but then would cease to work after about 5 minutes.

Generally, I will say, if I get past the first wireless access, and don't use bluetooth, the computer is pretty stable.

Maybe I should try a different source for the restricted Broadcom drivers than the one that gets used by default?  Has anyone had any luck with this?

Thanks, and good luck.

---

### Post by stldirty on 2007-11-16
ok.  im using noapic noapci nolapic noirqpoll nosmp for my boot parameters and i followed the instructions here 

[http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve](http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve)

ubuntu has been running strong on my dv6000 ever since i've done those things and completed the recent updated that came up.  i haven't touched firefox tho, i'm using opera.  i'll write back if it freezes.

---

### Post by Zerol on 2007-11-16
Unbelievable that they supported the HP laptops SO bad.. Almost everybody in my surroundings owns one. I insisted that my friend would get Ubuntu to instead of Windows wanted to install 7.10 on his laptop and then one mine since I own 7.04 atm.

But then I read this thread! Thanks! Maybe you can edit the beginnerspost if the problems or most of them are over.

---

### Post by clmcdanne on 2007-11-16
After reading the threads: upgraded HP ze4220 from 7.04 to 7.10.  Upgrade failed initially; reinstalled and it worked!  However VERY SLOW boot up and after shutting down for the evening  woke up to a drained battery!  The drained battery condition was also common in 7.04 until it was fixed. :lolflag:

---

### Post by mock_alien on 2007-11-20
i Have a dc9000t (dc9072)

I did an upgrade from 7.4.

At first i was dissapointed. but now i manage to get fairly everything feist had except:

a)wifi askes for password dispite that it is in the keyring manager (vpn connection works, so it must be something i did)

b) sometimes the screen has black flashes (had that in feisty too) and freezes (but *knock on wood*) now it was long age (some hours) it happend last.

thats my gripes (of course there are many many things that can be improved)

The key to my succes was using the generic kernel, (i386) was nothing but trouble. i don't know why it's preferd when new kernels are download, but i change my grub menu to boot the generic default (no no need for "noapic" or anything, that is  not needed)

---

### Post by didli on 2007-11-20
> **mock_alien said:**
> (..)The key to my succes was using the generic kernel, (i386)(...)
Same here with the HP DV9051ea i own. I did not meet so much troubles i'd seen here, but nervertheless Gutsy gave me a **real hard time** to have everything i need running fine. Maybe twice the effort that was needed with Feisty ...

---

### Post by rundee_f on 2007-11-21
hear hear!

im using V3000 and just upgraded to Gutsy from Festy within this week.. yups,, i found something goin worse than Feisty.. For example, and the main problem to me now (and i still searching what should i do) is my BATTERY LIFE decreases! When i boot to windows, my battery is doin fine...

Next is bout the ALSA mixer, i in Feisty i can make the QuickLaunch Mute button to mute/unmute my lappy, but it cant be done in Gutsy! I tried everything i used to do in Feisty.. No change.. i have to click it manually... sad.. :(

Havent test CompizFusion and Emerald yet...

---

### Post by Newbie1978 on 2007-11-21
Well after a lot of frustration I discover that my new laptop don't work with Linux (hardware issues) this are my specs HP Pavilion Entertainment-center notebook PC DV6660se 64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 250 GB hard drive, 2 GB RAM Nvidia GeForce Go 7150 graphics if anyone manage to install a Linux distro in this model please help me

---

### Post by offchance on 2007-11-21
ok. I posted [earlier]("http://ubuntuforums.org/showpost.php?p=3692674&postcount=155") about how things were working fine. that has changed. all my networks apps (pidgin, swiftweasel, etc) are incredibly slow to start-up and slow when working. I also seem to be forced to reboot my computer a lot more than with feisty. sadly, this seems to be the case with everyone whether they are running gutsy on an hp machine or not.

---

### Post by Apple.boi on 2007-11-21
to the contrary i had the best time with my hp laptop and ubuntu 7.10 worked perfect. dv6315ca is my laptop. restricted drivers caught the broadcom wireless card and well like nothing else was a problem. i was even more surprised i had better support then i did in vista, things like my media buttons were supported with out driver download. and my intel graphics 945gm/something was amazing, better then my desktop graphics **Card**. the only thing i have ifs with is.... second monitor support only clones my desktop rather then extend my desktop. the only thing i did was burned a ubuntu 7.10 dvd. so iunno

---

### Post by Newbie1978 on 2007-11-22
Hello! I only try once to install Ubuntu ultimate 1.4 which I believe is base on Ubuntu feisty 7.04, the results where horrible not only the live dvd never load even when I try with "noapic" (which works fine in my other laptop an HP pavilion DV6000 Athlon 64 X2 1.7Ghz) but also when I try to get back in windows to research some info about my problem, I was shock to discover that I ruined my Windows Vista, I try some quick fixes to get back in graphics mode but nothing works so I end up re installing from partition (good thing this is a brand new laptop so I didn't t loose anything) I use the same Ubuntu Live DVD in both laptops and my HP DV6000 works pretty well on Linux, also both laptops uses x64 so I'm don't think the problem is the version of the OS or the DVD it self, when I try to load the Live dvd I get the PIDOF error first after a while goes on and then I get the xserver config error I set the configuration in the xserver and the progran goes on loading the live DVD but never finish the installation, I'm yet to try another time with a newly downloaded version of Ubuntu Gusty 7.10 x64, I don't know what to do now I'll appreciate all the help possible I'll even try any other distro of Linux before settle to run on Vista for the time being. Thanks for the help

PIDOF [3266] can't read sid from proc /1/stat
PIDOF [3266] can't read sid from proc /10/stat
PIDOF [3266] can't read sid from proc /11/stat
PIDOF [3266] can't read sid from proc /163/stat

Not sure if Gusty works in my HP laptop because Feisty didn't

---

### Post by greenwom on 2007-11-22
I have the DV9000 series laptop.  I went with the 64bit version

Just installed Gusty.
I had to run the following boot options to get the install to run
```
-noapic -nolapic 
``` 

The nv driver worked to get it up and running.  The restricted Nvidia driver also worked.  I did have a few problems getting it to work but I just re ran the installer and all was well.

The broadcom wireless from the restricted drivers also worked well. 

As far as performance it seems to run extremely well with one exception.  There seems to be a memory leak(or something else) with either thunderbird, firefox, or another common programs.  I've been killing the app and restarting, no big deal.

i've also installed this on a Lenovo 3000 c200, no problems there either.


Just like fiesty I can't get my webcam to work (haven't really tried hard but there's a support issue there to )

---

### Post by Persian5life on 2007-11-22
i own a DV6565ca and everything so far works for it except for sound which is driving me crazy I went to the realtek website but some how i could not install my sound card (although my sound card works on vista). i am so frustrated right now, i was thinking of downgrading  ubunru 7.04 but I don't know where to get ubuntu7.04 which supposedly works fine on HP laptops. any suggestions? anyone else with this problem or am I extra special? if anyone dose have solution for this i must say i idolize you as a god for i did my research and no one has a solution for this yet (take note i am very new to ubuntu i just learned waht alt+f2 dose).

---

### Post by EXCiD3 on 2007-11-22
Previous releases of Ubuntu can be found at [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by twist2b on 2007-11-25
ok well i have a HP Pavilion tx 1000 and i want to just use the older version.
The live cd works totally fine if i change the resolution setting. but when its actually on my hard drive ubuntu will boot but wont do anything else... no buttons work and it black screens

any help?

---

### Post by a13kurt on 2007-11-26
I recently obtained an HP dv6000 series laptop and when booting to the live CD, all of the drivers, kernel, and everything else loads, but when it comes time for the GUI to pop up my entire screen turns white and then fades to black from the outside in over a period of a minute and a half to two. I installed Gusty on an old Toshbia Techra M1 and it works great. All I can say is WTF!?

---

### Post by clbaines on 2007-11-26
I to am glad I checked this forum. I am having problems with the upgrade to 7.10.
I can't get it to download all files. It gives a message that it can't access a server for 
security files. I posted a note with on the developer site and they said it was a bug
in the upgrade software. So I don't think the upgrade is for Dell either. I am going to
forget it for the time being.

---

### Post by fatmano on 2007-11-27
Ok so I just got an hp dv9000, I tried installing w/ live cd, no luck....I tried installing w/ alternate cd and had some luck.  The live cd stalled when installing the generic-linux-kernal then would spit me out in to a red screen with an error (cant really remember what it was, but the CD was checked twice and record speed dropped to 4x ).  I was able to get past that with the alternate cd, but it still would not completely install. What I ended up doing was each step on its own in rescue mode. That at least got me to here.  I got my nVidia drivers running w/ envy ( I highly recommend it for anybody who is having problems w/ their nVida card ).  But I was hardwired at the time.  I got the wireless running using the ndiswrapper and getting the driver from a previous post on hp.  My biggest problem now is that grub does not seem to recognize my sata drive.  It works fine if edit the kernel line, any tell it exactly where it is ie not using the UUID, If I edit the root= to be root=/dev/sda1 it will boot.  If I edit the /boot/grub/menu.lst to always read root=/dev/sda1 it will light my hard drive light and do nothing.  All I really need to do is edit my kernel line and then press b and it works great.  Now can I say what a PITA that really is....

I am sure I am missing something really simple, I just cant find anywhere.  Please help,
I am committed to making Gutsy work, and other than having to issue my essid for my bcm4312 ( which I dont like having to either, but can sort of live with ) I have made this Gutsy my OS of choice and want to stick it out.

I upgraded from Fiesty on my work desktop in ~40 mins.  It went great, that is what started me down this road.  I can go backwards if need be, I already dropped from the AMD-64 to x86-32 to get to where I am now.  But if I could get that grub thing fixed I am going to stay.


-eo
HP dv9000
2GB
SATA 160GB
AMD-64
Broadcom 4312 a/b/g ( rev 2 )



==== Follow-up  ====

I tried updating splash screen settings but no help.  I still end up with a :
initramfs> prompt.  This is where I see that my /dev/sda1 is not mounted to boot from.

---

### Post by Xylograph on 2007-11-27
Hi. Im a complete Linux newby, currently running DSL on an old IBM 380ED, and XP on a Compaq Presario desktop, and a Compaq Presario V5000 laptop.

Would I encounter any problems do you think, installing Gutsy on the V5000?

Its got:

AMD Turion64 (Im going to install the 32bit version however, for ease of use)
512MB RAM
40GB HD (With WinXP - Id like to dual boot if possible)
ATI Radeon Xpress 200M

And if it is not possible, would you recomend either using Feisty Fawn (would I lose the any features?) or OpenSUSE 10.3 (i got a disc free in LXF).

Also, for the desktop, as I enjoy moviemaking, music making and photography, would you recomend Ubuntu 7.04/7.10 or Ubuntu Studio 7.04/7.10?

Thanks in advance

-Xylo'

---

### Post by taistelutipu on 2007-11-28
Hi everyone,

my sister ran Feisty on a COMPAQ Evo N610c laptop and everything worked fine. When she upgraded to Gutsy the first error was that the internet didn't work anymore. Since she had experienced already network problems in her dorm earlier she thought a restart might do the trick. But on restart the internet still didn't work. She tried to fix it in the network settings and for this she needed root rights. But the root login window didn't work either. It just froze. She decided then to restart again and then the computer didn't even boot anymore, it stopped right in the beginning of the booting process with the infamous message:
[   8.898347] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Does the upgrade from Feisty to Gutsy include also a kernel update? If so, it is possible that the kernel needs to be rebuilt or recompiled? When I entered the error message above in google I got hundreds of hits which hinted at similar problems when upgrading the kernel. On of the suggestions was the following: "You can either include the filesystem support in your kernel or create an initrd to load the module at startup."
Another problem could be the lilo entry not matching: "The problem was in lilo, i asumed that my loader was pointing to hda3; when in reality it was pointing to hda1"

I'd like to know how I can get these informations, e.g. which kernel version my sister uses or how her grub (she's not using lilo) entry looks like. The problem I encounter is that the blinking cursor at the end of the message freezes, i.e. I can't write anything in the command line.
Is there a way how to interrupt the erronous booting procedure before it freezes to get to these informations? I searched for hours in forums to get help for the problem but I didn't find anything. I guess it is considered common knowledge so that no-one includes it in the instructions how to deal with kernel related problems.

I run a debian distribution at home which my friend set up for me. I know how to maintain it but I never set anything up myself from the very beginning. So when it comes to the basics I'm a beginner. Further I haven't been present when he set up my sister's computer so I don't know anything about it (kernel version, file systems, modules etc.) I can't access anything with the knowledge I have right now since the booting process halts after a couple of seconds. 

I suspect that the update somehow messed up the root account since my sister could not log in anymore, for example the directory appointed to root does not match reality anymore or something like that. 

Can anyone tell me what I can do about it? My sister recently changed from Windows to Linux so she knows even less than I do. My friend mentioned above lives now in another country so he can't help us with it and I'm now in charge of our distributions. Thank you very much in advance for your advice. It's much appreciated.

Best wishes
taistelutipu

---

### Post by Loopsurgeon on 2007-11-29
I know this is an Ubuntu forum and all....but NO version of Linux runs very well on my HP Pavilion dv9010 I have tried several flavors and no luck including Feisty and was on this forum to see if 7.10 would be any better....I guess not. Can anyone recommend a flavor of Linux that will work including the all important Wireless card? I'd like to get on the internet WITHOUT WINDOWS!!!!!!!!

---

### Post by kle on 2007-11-29
(Using HP Pavillion Dv 6000)

I just started as a Linux user last week. Installed and reinstalled, several times, and the Gnome seemed very impressive and all, but there were too many cold crashes to live with. So I switched to Kubuntu (still 7.10, since I had not seen these posts and was not warned). Now I have been quite happily getting to know Kubuntu for a couple of days without serious crashes. (Only problem: no OpenOffice)

---

### Post by scradock on 2007-11-29
I have an HP Pavilion zv6000 laptop; I've been running Gutsy since about June (when the testing repos started operating). Not a lot of problems that I can see; 32-bit Gutsy with the latest generic kernel is boringly reliable, does Compiz and all that stuff, just waiting for a newer ATI proprietary driver to get the speeds up a bit. Restricted drivers works fine on both the fglrx driver and the Broadcom wireless.

Now the Hardy repos are open I'm running hardy on another partition; it's a bit broken at the moment, waiting for upgrades to xorg, etc., but what works works well.

Only problem I have is using 64-bit Gutsy with the latest ATI driver (8.42.3) AND Compiz (no Xgl; uses AIGLX). There's a massive rise in the memory usage (about 5MB a minute) when idling; makes it very difficult to use Firefox or Evince, as stuff gets shifted to swap, and something seems to thrash around a lot (cpu goes very high when memory usage gets over 85% or so). Turning OFF desktop effects cures the problem. I'm not sure if going back to the 8.37.6 fglrx driver would fix this; in any case it clearly involves Compiz/emerald in some way too.

The durn thing even runs XP Home as well, very occasionally.

---

### Post by gambothell on 2007-11-30
I tried to upgrade my HP Business Computer nc6000, doing a fresh install of the live CD when Gusty first came out and I had many problems. Today 11/30/07 I backed up my 7.04 and did the upgrade using Update Manager. Wow, it looks like for me all the problems have been fixed. I am running wireless and everything is OK with no surprises.

thanks a lot to all the people who have put in so many hours fixing these problems. You all are great.  Go Ubuntu ...:)

---

### Post by gumbi18 on 2007-12-02
I tried to upgrade Feisty on my HP nx6125, but it crapped out half way through. (I think it had something to to do with compiz fusion running on feisty and the upgrade.) I then wiped the HDD and did a fresh install of Gutsy. Have had no issues since, except that VMware server will not boot bootable CD's. But that doesn't seem to related to Gutsy itself. Everything else works including graphics (the dreaded ATI Express 200m), wireless and even the card reader.

---

### Post by TouchuvGrey on 2007-12-02
Quick question here, i am very new to linux, i have an an HP laptop
with 7.10 Gutsy Gibbon. Given the issues with Gutsy and HP laptops
should i "upgrade' to Feisty, and if so, how do i do it ?

Or, should i go to the Alpha of 8.04 Hardy Heron ?


                                                                          Mike

---

### Post by EXCiD3 on 2007-12-02
> **TouchuvGrey said:**
> Quick question here, i am very new to linux, i have an an HP laptop
with 7.10 Gutsy Gibbon. Given the issues with Gutsy and HP laptops
should i "upgrade' to Feisty, and if so, how do i do it ?

Or, should i go to the Alpha of 8.04 Hardy Heron ?


                                                                          Mike

You cant "upgrade" to an older version. Feisty would need a fresh install from the CD to be installed. The Hardy Alpha is most likely LESS stable than Gutsy, as it is continuing from Gutsy release. I would recommend fiesty.

---

### Post by TouchuvGrey on 2007-12-02
Ok, i can download "Feisty" and burn an ISO easily enough. 
I see you have posted an install guide for Feisty so that
takes care of that.

        I'm presuming that i will lose everything i have done
when installing Feisty, no real loss. I know a little more than i 
did a week ago so i can do it better this time.

     Due to having no idea what i was doing during the
install of Gutsy i have 2 copies of 7.10 on my computer,
how do i uninstall them ?

                                                            Mike

---

### Post by EXCiD3 on 2007-12-02
Just format the partitions. Then you can resize and create/delete partitions for your new install of Feisty.

---

### Post by TouchuvGrey on 2007-12-02
> **EXCiD3 said:**
> Just format the partitions. Then you can resize and create/delete partitions for your new install of Feisty.

       If it was windows, i could easily. How do i format the partitions
in linux ?

---

### Post by EXCiD3 on 2007-12-02
Use GParted on the LiveCD ;)

---

### Post by yippy on 2007-12-03
I have a HP zv5380.  After upgrading to Gutsy I had two issues:  The default kernel fails immediately with a "Kernel panic", and the nvidia driver.  I just reverted to the previous kernel version, and to get functional so I can work I replaced the nvidia driver in xorg.conf with the old nv driver.  Obviously that's not ideal, but at least I'm able to work.

Wireless is working great, but the restricted driver never worked for me in Feisty so I'm still using ndiswrapper.

Sound is working great.

My main applications are working:
Zend and Aptana IDE both had no issues.
I had to change the executable on my Thunderbird link from "mozilla-thunderbird" to just "thunderbird", and I had to fix the icon.

So far it seems that, except for the video, things are working well.  I just have to boot to the 2.6.20 kernel every time.  The crappy nv driver is working for me for now because I don't use any compiz effects (I'm using Gnome with Metacity and Nautilus stripped out of the session and Openbox3 running instead), apparently my minimalist desktop was a good thing!  I'll try and get that working again when I have some time later.

---

### Post by Newbie1978 on 2007-12-03
Hello, I try again to install Linux Ubuntu in my HP dv 6660SE, unsuccessfully this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work. Thank you

---

### Post by DizzyTech on 2007-12-04
I'm sorry for you guys, but my dv6654us runs flawlessly from the Gutsy CD.  The only forseeable problems I have are suspend and hibernate, which I read is fixed easily, and sound, which is fixed in ALSA 1.0.15.

---

### Post by gabo on 2007-12-05
> **Newbie1978 said:**
> Hello, I try again to install Linux Ubuntu in my HP dv 6660SE, unsuccessfully this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work. Thank you

I have the same problem. I just bought a new HP Laptop yesterday and that's exactly my same problem running the Live CD. I think that the bcm43xx_microcode5.fw is not about the graphics card but the wireless broadcom card.  I am thinking in a solution... maybe even moving to another distro...

I'll keep you inform in whatever I find out.

Saludos!

---

### Post by colomob on 2007-12-05
i was able to install 7.10 into my hp laptop.all my drivers work ok.BUT..am only having one problem and that is when i run the update and restart the system it goes into a bage color screen. and thats it..how can i fix this.??

---

### Post by colomob on 2007-12-05
to e exact is when opening to install something called cupsys.what can i do?

---

### Post by colomob on 2007-12-06
> **colomob said:**
> to e exact is when opening to install something called cupsys.what can i do?
nvm.. i fixt it..my gutsy is running perfectly..:guitar:

---

### Post by deathblossom on 2007-12-06
So, are there any solutions for these issues? I've read the whole thread and I'm not seeing a lot to help me.

I just installed 7.10 over the weekend (HP dv2109nr laptop; dual-booting with Vista) and it was a complete nightmare. I've gotten enough set up on it that I'd rather not have to repeat the whole process again to downgrade to 7.04, but I was wondering if there was anything I could do to improve some of the functionality. My wireless is fine, but some of the other problems I'm having are:

*Screen. Specifically, I can't change the brightness/gamma/anything (the brightness panel won't work and the laptop keys don't work either), which is bad for when I'm running the pc on my battery.
*In regards to the battery, I don't think Ubuntu is accurately measuring my battery life. It stays on well past the time that Ubuntu says it should be depleted.
*Suspend and Hibernate don't work either.
*Sound. I have sound; however, it's buggy. The sound out of my speakers is incredibly soft and nothing I do will increase it (the volume controls on the laptop and Ubuntu do nothing; the laptop media buttons will register as being pressed and the volume meter will move in Ubuntu, but nothing happens). It won't mute at all. On the other hand, the sound out of my headphones is insanely loud, but similarly, nothing can be done to lower the volume unless what I'm listening to has some volume controls of its own.

Granted, I can live with these problems, but no harm in seeing if they can be fixed or someway managed for the time being.

---

### Post by tinman6700 on 2007-12-07
I see a lot of messages on here about Gutsy being for Dell laptops, but unless I missed it, no one has actually gotten on this thread and reported success with a dell. I am really starting to get nervous now also, because I am now in the process of updating from Ultimate Gamers, on my P4 latitude, which ran beautifully. Already I have seen signs of problems (mostly with openofffice dependancies), but it also appears to be locking up the whole machine. I am really considering taking my chances, doing a hard shutdown, and a reinstall if necessary. I will know better from now on than just to click upgrade, ALWAYS CHECK THE FORUMS FIRST

---

### Post by tinman6700 on 2007-12-07
Well, I did shut it down, and it was definately locked up tight, but it dod go better than I had actually anticipated. My computer restarted ok, just a lot of broken dependancies for openoffice, and update manager would not work. At least I am getting my first real dose of rinning scripts tonight, as I fix things, and thank god for this forum, as much of a noob as I am, I would probably be doing a fresh install if I weren't able to look up the commands, and syntax on here.

---

### Post by Jeff_From_VA on 2007-12-07
I bought my wife a HP dv9500T for Christmas. She had no want for Vista, and I offered her XP, but she told me she wanted to start with linux as she likes how my PC is setup.  I tried yesterday to get it working with Feisty for several hours following the instructions in several threads here and was unsuccessful.  This is likely my fault, as many seem to get it up with no issue with Feisty.  

I chose Feisty originally because of my own experiences with Gutsy being very unstable, and I had a great run with Feisty in the past.  

I had to break down and try gutsy on this laptop.  I used the alternate installer as I prefer it, the alternate cd installs much quicker.   Gutsy worked for the most part out of the box.  Everything but sound.  I got sound up and going very easily though.  I also had to do some changes to the wireless so that it would autologin to the home network with out bugging my wife for the keyring password, but wireless did work out of the box. 

So far so good, only time will tell how it works out.

I have not yet tried the webcam or fingerprint reader, or anything like suspend or hibernate. I will play with that this weekend and see what I come up with.

I am not endorsing gutsy on an HP, I am honestly scared of it, as I have had it blow up on me before a few times.  I just wanted to share my install experience with it to help others who may be trying to decide.

*EDIT*  - I am realizing while wireless does work out of the box, it works at dialup speeds @ 15-25k, and I am on a 12mb cable modem.....

---

### Post by marildo on 2007-12-08
I have tried to install Ubuntu Gutsy Gibbon on a hp dv6220BR but it didn't work as well. First of all, I had installed the Feisty Fawn twice and it seemed be working fine but when I tried the upgrade for Gutsy, it locked. Now, nor even Feisty is possible to be installed anymore.

Sorry about the English language, I'm trying to report my experience here from Brazil.

hugs,
Marildo Dantas

---

### Post by colomob on 2007-12-08
when i was duel booting it with vista i had a nightmare..but when i got the alternate cd and i used the hole space i was able to used it perfectly and all my drivers are working..i have an HP pavillion dv6000.80GB harddrive and 1GB of ram.Nvidia graphic card and the same wireless card as everyone else..

---

### Post by asnd16 on 2007-12-08
I have to say I have had no issues with anything other than the battery never getting more than 43% full. . . Does anyone know how I can fix this?  I have ran it down to nothing and let it discharge but not sure if it is discharging?    

Crazy . . . But yeah I have a dv4000a version and it works fine. .

---

### Post by n.aoix on 2007-12-08
Well I'm also ower of a HP Laptop(dv6520ez) 

HP Pavilion dv6520ez Notebook

• AMD Turion™ 64 X2 Dual-Core Mobile Technologie TL-56
• Original Microsoft® Windows Vista™ Home Premium
• 120 GB HDD
• 2 x 1024 MB RAM
• 15,4" TFT WXGA BrightView Widescreen (1280 x 800)
• Wireless LAN 802.11b/g Broadcom 4311
• nvidia 8400M GS with HDMI

so far I've had no luck installing Ubuntu 7.10 on this notebook. Doesn't matter if I use the Live CD, the Alternate CD with NOAPIC NOLAPIC, wittout that. If anyone can help me out or point me in the right direction it would be nice. The problem I am having is that I can't even boot on the live cd, nothing is displayed, and when I finish the Alternate CD installation I don't get a thing on my display.

If there isn't a real way to deal with this, can someone point me out to another distro that works well with HP notebooks? Specially the dv6520ez. 

Thank you for your time.

---

### Post by Kulaspiro on 2007-12-09
Great info..it saved me from inconvinience... i was planning to upgrade...and i guess i am gonna stick with feisty for now...thanks a lot

---

### Post by jaybeoh on 2007-12-09
I have gutsy running on a HP dv8000 laptop and it works perfectly!

---

### Post by jeromio on 2007-12-11
> **martijnterpstra said:**
> I have a HP presario v6000 and the sound doesnt work on gutsy (worked of fietsy).
besides that it works perfect.I think there must be multiple variations of the compaq presario V6000. I have a dual core AMD64 w/ NVidia graphics and Gutsy *completed crapped out on me*.  I 1st installed Kubuntu 7.10 and had a host of problems. The video and sound worked, compiz did not, wireless did not. But the machine was REALLY SLOW. Dragging windows around? It would ghost as it tried to keep up with the painting operation. Opening windows would take forever. Every little operation would take 100X longer than it should. Pretty much unusable. I couldn't use the system monitor (too slow), but top would show a handful of procs eating up all the cycles. Not all the time - whenever something had to get done, it would apparently consume all the CPU cycles to do it. As if it was a 386 or something.

SO, I figured it was a problem with the kubuntu fork. I re-installed w/ straight ubuntu 7.10. This time, w/ the boot CD, I tried to play around a bit. Not slow. I mean, it would drag as it tried to hit the CD, but overall, it was normal - usable. Video and sound  worked from the liveCD. Wireles, no, but that's okay. I installed. Reboot and it came up with video errors. Got it to accept 800X600, but that's it. No wireless. Super, crazy, unbelievably SLOW! Can't do anything. Can't change the video off of 800X600. I was able to move to restricted drivers for video and wireless (process took about 20minutes!), but changing the settings using the GUI tools wouldn't take. It ignored my changes. Plus, the video settings dialog kept exiting. This thing is maxing out - the fan is on. CPUs are bouncing up to 100% utilization - and I'm not really doing anything! This is even slower than with Kubuntu 7.10. It's completely unusable.

I guess I will try again with 7.04....

---

### Post by stlcoptony on 2007-12-11
Just wanted to say hi and join the HP-problems club. I have the HP dv6646us laptop with amd64 x2 tl-58 processor, 2gb of RAM, the nvidia geforce go 7150M graphics card and broadcom 4321 802.11 wireless card. I have yet to even get a live cd to the GUI screen. I am currently downloading the ISO files again just to be sure it's not my media thats bad. Anyone know if these problems are being addressed in hardy heron? I could wait that long if it will work...

---

### Post by Jeenyus on 2007-12-13
Well I wanted to give Ubuntu a try so I downloaded the latest version 7.10, and was having issues with the installation and basic "setting up" and NOW I stumble across this thread :mad:  I have an HP zv6000 w/ AMD Athalon 64 3200+, 512 RAM, 80GB HDD, and ATI Xpress 200M.  I guess now I have to start from scratch with 7.04 :/  Oh well, still looking forward to the ubuntu experience :)

---

### Post by stlcoptony on 2007-12-13
Check out this thread [here]("http://ubuntuforums.org/showthread.php?t=575750"). I used his how-to on an HP dv6646us (amd 64x2 tl-58 1.9GHz, 2gb RAM, nvidia 7150m) and I now have a perfectly functional ubuntu laptop

thanks

---

### Post by therrmann on 2007-12-14
I don't think it is only with HP machines.  I had to do a clean install on my Dell Latitude after upgrading to Gutsy, because on boot I got kernel panic and if I booted with an earlier kernel, GDM would not work.   Now it won't give me a virtual terminal or shut down properly at all.  If I try to log off, the screen just goes completely blank (slowly, like the power is somehow shut off to the hardware drivers) and the whole machine hangs. Same if I try to use a virtual term.    It's usable, but just.

---

### Post by DarkRookie on 2007-12-14
know 7.10 doesn't work on my Pav 6406nr
The live CD won't boot up.
With a little modifcation I can get 7.04 booted from the live CD and even installed
The problem is if I try to boot from my hard drive. I get a blank black screen.
If anyone can send my some tips.
I have tried different solution found in the forums already. None seem to work

---

### Post by klymster on 2007-12-14
I was able to intall Gutsy on my new HP Pavillion dv9608nr using the alternate CD.  Dual boot with Vista.  Unfortunately it freezes early during the boot after the Ubuntu screen with progress bar.  I will try Fiesty next and see if I have any better luck.  Anyone have success on this model with Gutsy?

Thanks

---

### Post by mdshann on 2007-12-14
I have a HP Pavilion Entertainment PC dv6000 and have had no problems with anything. The Athlon 64 X2 is fast and I have the nVidia drivers installed on the 7150 mobile chip. In short I can't understand why this thread is here as I had to do nothing out of the ordinary to get it going. I am definatley not a guru either!

---

### Post by Icehuck on 2007-12-14
> **mdshann said:**
> I have a HP Pavilion Entertainment PC dv6000 and have had no problems with anything. The Athlon 64 X2 is fast and I have the nVidia drivers installed on the 7150 mobile chip. In short I can't understand why this thread is here as I had to do nothing out of the ordinary to get it going. I am definatley not a guru either!

HP Laptops vary considerably from model to model. While my laptop model is an HP DV6648se, its actually a DV6500 according to HP. The 6648se just refers to just 1 hardware configuration out of the 100 hundred configurations available in the DV6500 series.  Also things like chipset and  bios versions can have an impact how an OS behaves with hardware.

HP DV6648se  Installs and boots into gutsy no problem from LiveCd. Wifi works with NetworkManager disabled.  No sound, suspend, or hibernate, haven't researched if there is a fix or not for any of it.

---

### Post by dgavenda on 2007-12-15
I have a HP dv2500.  Sound was working then vanished w/o any obvious chgs (on my part at least).  

Been going thru suggestions from the ubuntu forums with no success.  Such a pain.  

- It's not the acpi issue
- It's not the latest alsa driver issue
- The snd_hda_intel module it loaded.
- The device is found.
- No errors.  
- Sound is very high.
- Card is:  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


I can't believe it works from LiveCD and at one time it worked, then magically stopped.  Also, I have notice bluetooth mouse seems to randomly not work on boot too.

Any suggestions to either problem..especially the audio problem, would be GREATLY appreciated.

Dan

---

### Post by jgriffinpark on 2007-12-15
I had installed 7.04 on my Media Center dv6000, but gave up because I was tired of trying to get the broadcom wireless working. My question is, is it worth trying to install 7.10 (others on this thread have had success on the same laptop) or should I wait until a later release?

---

### Post by NineseveN on 2007-12-15
The 7.04 alternate CD installed fine on my dv6324us, but after the updates in the Update Manager, I couldn't boot into the new Kernel (just hung with a black screen no matter which boot options I tried). I had tried the live CD of 7.10 on it a few weeks ago and it worked great, so I installed 7.10 on it and now it's downloading the 7.10 updates.

I'm reasonably confident that I can get it working on 7.10 now after having gone through 7.10 with an ATi card and the restricted drivers fiasco on my desktop...we'll see though. So far, everything I tested worked (sound/audio playback, headphones, SD card reader, media controls-volume/mute/play etc...).

As long as the updates don't hose my laptop and my Broadcom card works as well with the Gutsy driver as it does for others, I can't see a reason to even think of going back to Feisty on this machine...but that seems to be a big "IF". I'm keeping my fingers crossed.


I don't even care if the Nvidia drivers work, it's mostly a work/internet laptop, but it looks like I should be able to get them working as well.


*hopes updates don't hose his system again*

---

### Post by stlcoptony on 2007-12-15
> **jgriffinpark said:**
> I had installed 7.04 on my Media Center dv6000, but gave up because I was tired of trying to get the broadcom wireless working. My question is, is it worth trying to install 7.10 (others on this thread have had success on the same laptop) or should I wait until a later release?

Try following this thread [here]("http://ubuntuforums.org/showthread.php?t=575750"), and see if it works. It worked perfectly on mine.

---

### Post by mwacky on 2007-12-16
HP Pavilion zv6000

Everything works awesome with little or no tweaking, Suspend is the only issue...

---

### Post by NineseveN on 2007-12-17
Okay, so an update.

The updates stalled when trying to start CUPS for some reason (though CUPS has been known to hang on my desktop as well so no big deal). 

I had to force quit the updater after an hour of watching it sit there. When I logged back into Ubunutu, my window borders were gone (no close, minimize/maximize controls) and my terminal was solid white. After a quick search on these forums, I found out it's a Compiz bug/issue, all I needed to do was open the blank terminal and type "compiz" and hit enter. Totally solve the issue. The laptop has been running perfectly with 7.10, everything I need works and it even boots faster than my desktop machine.

Suspend locks the system, but this laptop doesn't need to use suspend anyway (though maybe there's a fix for it in 7.10 somewhere).

Overall, 7.10 was easier for me to install and it didn't get hosed like Feisty did. I was even able to use the Live CD for install and only had to add noapic irqpoll noirqdebug to get it to boot fully.

I'm still keeping an eye on it for issues, but so far, things are running great. USB works, sound works, wireless works, Nvidia card works with the right resolution and refresh rate. It's all good from here.

---

### Post by icest0rm on 2007-12-19
> **dgavenda said:**
> I have a HP dv2500.  Sound was working then vanished w/o any obvious chgs (on my part at least).  

Been going thru suggestions from the ubuntu forums with no success.  Such a pain.  

- It's not the acpi issue
- It's not the latest alsa driver issue
- The snd_hda_intel module it loaded.
- The device is found.
- No errors.  
- Sound is very high.
- Card is:  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


I can't believe it works from LiveCD and at one time it worked, then magically stopped.  Also, I have notice bluetooth mouse seems to randomly not work on boot too.

Any suggestions to either problem..especially the audio problem, would be GREATLY appreciated.

Dan

Same problem here, please suggest any fix :(

---

### Post by dgavenda on 2007-12-20
> **dgavenda said:**
> I have a HP dv2500.  Sound was working then vanished w/o any obvious chgs (on my part at least).  

Been going thru suggestions from the ubuntu forums with no success.  Such a pain.  

- It's not the acpi issue
- It's not the latest alsa driver issue
- The snd_hda_intel module it loaded.
- The device is found.
- No errors.  
- Sound is very high.
- Card is:  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


I can't believe it works from LiveCD and at one time it worked, then magically stopped.  Also, I have notice bluetooth mouse seems to randomly not work on boot too.

Any suggestions to either problem..especially the audio problem, would be GREATLY appreciated.

Dan


Errr...seems like the sounds issue 'magically' went away.  Very odd.  So did the random bluetooth mouse problem.  So confused how w/o any chgs it will start to work.

Anyway, I have this laptop doing flips now.  Very happy w/ it.  Compiz rocks.

---

### Post by icest0rm on 2007-12-21
still not working for me on gutsy x86_64...had to use OSSv4 to get any sound, but it's a big pain to make it work on flash/firefox :(

---

### Post by MidianLies on 2007-12-21
Can anyone help me? I have installed both Gutsy and Feisty to a partition on my HP dv9000-CTO.  First I tried Gutsy, but it always stalled on the boot screen w/ the orange progress bar. Then I triey downgrading to Feisty, but the same problem. Any ideas?

AMD Turion 64 X2

---

### Post by Keyper7 on 2007-12-22
MidianLies, usually the first thing to try is using the noapic kernel parameter.

In the LiveCD initial menu, press F6. Then add "noapic" in the end of the line that appears and press enter.

---

### Post by kvonb on 2007-12-22
-

---

### Post by MidianLies on 2007-12-22
> **Keyper7 said:**
> MidianLies, usually the first thing to try is using the noapic kernel parameter.

In the LiveCD initial menu, press F6. Then add "noapic" in the end of the line that appears and press enter.

So, the LiveCD doesn't work for me. But I did the same thing you just mentioned with the AlternateCD, and its solved all my problems. Ubuntu is working perfectly. Thanks alot man! 

But I can't help but wonder, what exactly does typing noapic do?

---

### Post by Ripfox on 2007-12-24
Wow...I have it installed on a DV5000 and a DV6000 without a hitch. Must be one of the lucky ones. :confused:

---

### Post by bduvall3 on 2007-12-24
I'm using an older one as well (ze4600 series with total of 768mb RAM - 128mb shared to video; 640mb operating RAM) and I've been running Gutsy just fine. The only problem I've not been able to fix is that I can't get dual screen to work properly, and since I need to be able to use a projector for presentations, this is a problem. Xinerama just locks up my laptop, and I've yet to find a suitable workaround for the ATi Radeon Mobility IGP.

---

### Post by Revan on 2007-12-25
I installed Kubuntu Gutsy on my DV6695EL and almost everything worked out of the box. I only had to manually compile & install alsa 1.0.15 to get the sound working.

The only remaining issue is about the multimedia buttons which control volume... they act on the headphone channel and not on the PCM one, does anyone know how to fix this?

---

### Post by Myssei on 2007-12-27
I have HP Compaq nc4010, and run gutsy on it (fresh install on a formatted disc), despite the scary "designed for WinXP" sticker on it. Everything works OK so far, except for USB ports. It didn't recognize my Sandisk 256 memory stick, keyboard, nor my Creative Zen mp3 player (yeah, I know it'd be a separate issue anyway).

I have lsusb and libmtp (6). Both Hardware Info and lsusb see the ports, but not devices connected. The mp3 player charges when it's connected, so it doesn't seem to be a hardware issue. Does anyone have any suggestions about fixing this? Or should I try Feisty?

---

### Post by EXCiD3 on 2007-12-31
I would like to let everyone know that the Zen Kernel fixes important bugs related to the AMD based HP Laptops. I strongly encourage anyone interested in fixing these problems take a look at the Zen Kernel here: [http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

[B]Important Information: 
[/B]-Kernel fix for the nolapic issue...it's a patch that disables C1E on AMD machines, which is causing the kernel to incorrectly report lapic is broken. This allows us (with newer custom kernels like zen) to use High Res Timers and Dynamic Ticks. 
 
On kernels without this patch, reported to work on the dv9205us, without disabling lapic (even though it is broken without C1E disabled):
```
noisapnp iommu=off noirqdebug noapic pci=assign-busses
```
 The patch can be found here (may have to mod it to work depending on which kernel source you are using):
 [http://tinyurl.com/ytyhfe](http://tinyurl.com/ytyhfe)
 
This fix allows you to boot without using nolapic, fully enabling nolapic. If you have a kernel like Zen, you can use the features Dynamic Ticks and High Resolution timers, which should increase both speed and battery life. The boot parameters I posted allow you to do the same with older kernels without patching, without high resolution timers and dynamic ticks, as they are experimental features added in the newest bleeding edge kernels.

Much thanks to ilikenwf, Official Zen Kernel Maintainer!!!

---

### Post by CapPicard on 2008-01-02
I am using  an HP nc6230 laptop.  I run Gutsy and I've ran into no problems with it. Amazingly, even my SD card reader is working under it. I'm suspecting it's mosty the older laptops that are having issues, no?

When i booted gutsy from my usb stick, it took a long time (at least 5 minutes) to boot. I initially thought it was due to acpi/apic.  But, i let it go and the stick finally came up.    I just setup my stick with the live CD.

---

### Post by mosestruong on 2008-01-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136387](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136387) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm able to get suspend/hibernate to work on my HP Pavilion dv2308tx after installing the latest kernel. However, sound quality seem to be bad when using this kernel... still need to find out the reason for it.

Anyway, if you're interested in how to install the kernel, I've written a little howto at [http://www.truong.id.au/node/76](http://www.truong.id.au/node/76)

---

### Post by s3raphim on 2008-01-04
I am running Feisty on an HP dv2416us.  It works well BUT  wireless only work on the third boot after swtiching power sources, and when the computer wakes up from sleeping (either battery or AC) the mouse is invisible and the wireless has turned off.  How do you have your dv2108 configured scorp123?  My wireless is a broadcom 4310 and I got it running unsing ndiswrapper - but it only works on the third boot when booting with a different PS from last time.  Any thoughts?

---

### Post by Vladislav.mitov on 2008-01-06
Hi, 
I have dv6000 hp laptop with broadcom 4312 wi-fi and 7.10 installed. Most of the things are working but i need wi-fi. Sorry but i can't read all posts so can someone tell me is there some way to make my wi-fi working and if there isn't, what i must do to run wi-fi on 7.04
10x

---

### Post by exneo002 on 2008-01-06
hey my dad has an hp dv1550se and he only needs it till july what distro of linux should I use I want ubuntu ultime [what ever versions out] 8.04lts kubuntu,ubunt mythbuntu, or linuxmce 
and finally I havent tried fedora and fedora 9 sounds like its gonna be an earth shatering relese so will the hardware issuse effect this model anybody have it

---

### Post by oldsoundguy on 2008-01-06
google is your friend: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) or [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)).

Or you could buy a D-Link 520 or higher card and it will install almost automatically.

---

### Post by OnTheCoast on 2008-01-06
I have just read the responses about HP laptop problems and must say things have worked out very well. I have a HP Pavilion zv6000 series laptop that I installed 7.10 on.

I did find, that by using a hardwire LAN cable to install 7.10 and downloading updates and the restricted drivers needed for the graphics and wifi, that once the drivers had been activated I was able to unplug the LAN cable and run with the wireless.

I did however have the "No Video - Long Wait prior to log-in" problem.

This was fixed using the post suggesting the x-y res and vga=791.

Being that mine has a widescreen, I had to use xres=1280 and yres=1024.

As of this post everything is working - short start-up time, sound, wifi, video - everything.
I just hope it last!

Thanks to all involved with your suggestions and comments.

---

### Post by JayBee808 on 2008-01-07
I have a dv6700 on the way.  From what I can tell, most of the hardware in it will work with Gutsy.  The only thing I am concerned about is the hard drive issue that so many Ubu Laptops have been plagued by.  Are HP laptops susceptible to this?  Have any of you HP owners had to deal with this problem?

---

### Post by sowelie on 2008-01-07
I have :( I was forced to disable fsck on boot.  It was either that or always have the live cd on hand :(.  I also had a sound issue with my cousin's dv6000.  I was able to fix it though.  Interestingly enough all I did was re-install alsa-base and then run sudo modprobe snd and bang, he had sound.

---

### Post by lgambett on 2008-01-07
HP DV 6373a here, running perfectly Gutsy. Wireless, sound, video, webcam, all OK !

---

### Post by JayBee808 on 2008-01-07
> **sowelie said:**
> I have :( I was forced to disable fsck on boot.  It was either that or always have the live cd on hand :(.

What was the problem you were having?  How can you detect these hard drive issues?:(

---

### Post by sowelie on 2008-01-08
The problem was every x amount of boots (configurable) a hard disk check is run.  It would freeze around 20% or so every time the check happened.  If I booted off the live cd and ran the check manually it went fine.

---

### Post by chavanak on 2008-01-08
Running gusty for past couple of months on my dv6602au.

Initially ran into all sorts of problem, but now its working fine!!!!
Even the fingerprint reader is setup and working.
Gusty, atleast for me is causing no problems.


Btw ubuntu does not harm your hdd by default. If you enable the laptop mode, then ubuntu will use aggressive power management and causes disk failure. This is true for all recent laptops.

---

### Post by ApOgEEs on 2008-01-08
hi,

i'm using Ubuntu Gutsy 7.10 on HP Compaq nx9010. my problem is I got this message when i do

```
$ dmesg | grep DSDT
[    0.000000] ACPI: DSDT 2BF752B0, 6CB4 (r1    ATI MS2_1535  6040000 MSFT  100000E)
[   12.627024] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.693463] ACPI: EC: Look up EC in DSDT

```

and

```
$ cat /proc/acpi/battery/BAT1/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            384 mA
remaining capacity:      unknown
present voltage:         16640 mV

```

my battery notification says 0% and battery discharging time is currently unknown

I've been searching through this forum and didn't find any hints. can anyone help me on how can i fix this? please...

---

### Post by aldeby on 2008-01-09
Neither I had any problem with Gutsy and my dv6500 Intel Santa Rosa based laptop. I wrote  a tutorial concerning these laptops, if you want t have a look at it you can find it here: [http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/](http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/)

---

### Post by AnonCat on 2008-01-09
Gutsy works fine on my DV6000 laptop.  I can't use the headphone jack and had to add some parameters to use the video carb, but other than that, I haven't had a problem at all.

---

### Post by FriedChips on 2008-01-09
Gutsy AMD64 version running like butter on my dv2415nr. That is until my backlight switch died.... This is a common problem with hp laptops. The switch that tells the computer whether the lid is opened or closed craps out.. Only had it for 3 1/2 months before this happened. Luckily HP has a 1 year manufacturers warranty.. Anyway, Wireless, nVidia graphics, webcam, and litescribe all working great. No problems yet :) .. Actually just to add, the native broadcom drivers "almost" worked. They at least powered on my card so my wireless light was on ( a first for the native drivers ) but I couldn't get a network to connect... :(

---

### Post by EXCiD3 on 2008-01-09
[SIZE=-1]I would like everyone to know that I have created a new thread for testing Hardy 8.04 prerelease on HP and Compaq laptops. If you have tried or are going to try out a prerelease of Hardy, please post any information you have here: [http://ubuntuforums.org/showthread.php?t=660384](http://ubuntuforums.org/showthread.php?t=660384)[/SIZE]

---

### Post by tompratt0 on 2008-01-11
My hp nc8000 dosent even boot. it just comes up with random stuff that my linux-wise friend says is the OS not been able to run anything!

---

### Post by allforcarrie on 2008-01-11
my dv9334 works flawlessly.

---

### Post by scotchfx on 2008-01-12
I posted this on the "Absolute Beginners" but did not get much useful feedback... hoping there is more input to be had here.

I am considering making Ubuntu the primary OS for my HP NC8000 laptop; I've had installed as a secondary system (off a removable multibay drive) and my only reservations up until this point have been the difficulty configuring on/off multiple monitor support.

In considering Ubuntu as my primary I've a few questions for the community:

Firstly, I've read a couple threads in this forum advising HP laptop users to stick with Feisty (as opposed to upgrading to Gutsy) due to compatibility/installation issues with Gutsy on HP laptops...

[B]What is the status of Gutsy on older HP business laptops (particularly the NCxxxx variants)? 

I am using an HP NC8000, should I forgo Gutsy in favor of Fiesty?[/B]

Secondly, my home office setup consists of my laptop (as my primary workstation) and a docking station with a second monitor attached (for a desktop spanning). Monitor-wise there are two scenarios that I need Ubuntu to configure to automatically, the first is when I am using my laptop remotely I need it to configure to "single" monitor mode. For the second, in my office, I would like for my laptop to configure automatically to "dual" monitor mode (an extended desktop) when docked. This is easy to do in XP but I've had problems getting it to work under Feisty (involved manually editing an xconfig file)... I think this has partly to do with the ATI 9600 Mobility Graphics card that this rev of the HP laptops use as I know Nvidia cards are more robustly supported under Linux...

**In comparison to Feisty, has multiple monitor support improved at all in Gutsy (perhaps for older ATI 9600 cards such as my own)...? **

I am asking this question as improved dual monitor/spanning support is incentive for me to at least give Gutsy a shot.

Sorry for the long-winded questions, I would very much like to make Ubuntu my primary system and relegate XP to a removable "only if necessary" drive, but I need some insight into the issues above before I do...

Any advice would be much appreciated!

---

### Post by FriedChips on 2008-01-13
> **tompratt0 said:**
> My hp nc8000 dosent even boot. it just comes up with random stuff that my linux-wise friend says is the OS not been able to run anything!

@ scotchfx, looks like you should not go for gutsy....

---

### Post by EXCiD3 on 2008-01-13
> **scotchfx said:**
> **In comparison to Feisty, has multiple monitor support improved at all in Gutsy (perhaps for older ATI 9600 cards such as my own)...? **

I am asking this question as improved dual monitor/spanning support is incentive for me to at least give Gutsy a shot.

Sorry for the long-winded questions, I would very much like to make Ubuntu my primary system and relegate XP to a removable "only if necessary" drive, but I need some insight into the issues above before I do...

Any advice would be much appreciated!

Well, I was unable to configure Dual monitor with my Nvidia 7600 Go in Gutsy due to the changes. Works perfect in Feisty. However, I have never used the ATI configuration utility. This will work the same in Feisty as it does Gutsy, however Gutsy boast this "improved" support, it successfully **prevented** my dual monitor setup no matter how hard i tried, everything got reset to 800x600 **and** it would not allow me to use the nvidia driver and/or compiz... I still would recommend Feisty over Gutsy, however, since you can boot off the LiveCD and see what works and what doesnt, there is nothing stopping you from popping in a Gutsy LiveCD and seeing how well it works on your laptop. As mentioned before, NC8000 doesnt appear to have too much luck.

If you want, post your specs on the laptop and that might help find the problem causing it to improperly boot.

---

### Post by scotchfx on 2008-01-14
Thanks for the responses... I am still considering setting aside an afternoon and "attempting" a Gutsy install as all it will cost me is time.. beyond my sig there isn't much to say about my laptop but here are the specs (with a link to the HP stock specs) just to reiterate:

HP NC8000 / 1GB PC2700 DDR / PM765 2.1GHz processor
ATI Radeon Mobility 9600 128MB

[http://h18002.www1.hp.com/products/quickspecs/11786_div/11786_div.HTML](http://h18002.www1.hp.com/products/quickspecs/11786_div/11786_div.HTML)

The laptop has integrated wireless & bluetooth as well... if upgrading to Gutsy means losing Feisty's ability to automatically configure these peripherals that will also be a showstopper...

The only notable details about my laptop are that I've upgraded the proc to a PM765 (stock NC8000s max out at the PM 2.0GHz procs) and for my dual monitor configuration I am spanning to a 19in. Sceptre LCD monitor via my docking station (DC366B port replicator). I will be installing Ubuntu on a 100GB Hitachi 7k100 7200 rpm drive (another upgrade) and will probably clone my current XP installation to a Hitachi 7k60 drive for dual boot if needed (will cross this bridge when I get to it).

Under Feisty I was able to get dual monitor spanning to work, however it required manually editing an xconfig file (and restarting) and was thus something of a pain. My hope is that under Gutsy I will be able to setup some kind of automated profile (similar to XP)...

Does anyone here have any experience with Gutsy & ATI Radeon 9600 Mobility cards, specifically with regards to dual monitor configs?

---

### Post by fiprojects on 2008-01-15
I am amazed at the problems folks seem to be having - I come from an HP Unix background (am a contractor, not employee), I started with  SuSE linux years ago but was not a serious desktop user until finding Ubuntu. I love its ease of installation.

I just bought a dv9000 (more correctly dv9618ca is the model number which is different from the product name).  Ubuntu 7.10 worked pretty much out of the box - my biggest headache has been wifi but I got that sorted by contacting HP and getting directed towards the XP drivers (my machine came with vi$ta and even with 2gbyte of memory took up to 90seconds to boot).

My new ubuntu that I am writing this post on now has everything I could want... graphics, sound, wifi (thuogh no webcam, I've not tried to get that working but might do some day... never had a web cam that worked on linux).  I got the wifi working with ndiswrapper and version 5 of the broadcom driver. I am most happy with having Dreamweaver working using an old version of CrossOver i bought two or so years ago!

  If I can find a place to report my setup I will if it helps anyone...

---

### Post by FriedChips on 2008-01-15
> **fiprojects said:**
> I am amazed at the problems folks seem to be having - I come from an HP Unix background (am a contractor, not employee), I started with  SuSE linux years ago but was not a serious desktop user until finding Ubuntu. I love its ease of installation.

I just bought a dv9000 (more correctly dv9618ca is the model number which is different from the product name).  Ubuntu 7.10 worked pretty much out of the box - my biggest headache has been wifi but I got that sorted by contacting HP and getting directed towards the XP drivers (my machine came with vi$ta and even with 2gbyte of memory took up to 90seconds to boot).

My new ubuntu that I am writing this post on now has everything I could want... graphics, sound, wifi (thuogh no webcam, I've not tried to get that working but might do some day... never had a web cam that worked on linux).  I got the wifi working with ndiswrapper and version 5 of the broadcom driver. I am most happy with having Dreamweaver working using an old version of CrossOver i bought two or so years ago!

  If I can find a place to report my setup I will if it helps anyone...

The webcam on my hp works great with the "uvcvideo" driver. You will need to build it from source, but as long as you have kernel source and kernel headers installed that should be as easy as:
```
make
sudo make install
make clean
```

then use the v4l2 setting in ekiga :)

---

### Post by jbaerbock on 2008-01-15
Try Linux Mint 4.0 out. I have had multiple problems with Gutsy on my lappy (zv6000) in the past but Mint fixed most if not all the bugs so it runs flawlessly on mine.

---

### Post by scorp123 on 2008-01-15
> **scotchfx said:**
>  Under Feisty I was able to get dual monitor spanning to work, however it required manually editing an xconfig file Sorry for jumping in ... I have a dv2108ea with an Intel GMA950 card, so I am not sure how far my settings here apply to your laptop.

Gutsy has so called "XRandr" support built-in. Which means you can on-the-fly change stuff such as your screen resolution and monitor output without having to touch that config file (I did have to add some Intel-specific configuration ... For anyone interested, see here: [http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950) ).

My boss recently gave me one of these monster screens:
[http://www.sun.com/desktop/products/monitors/24lcd/](http://www.sun.com/desktop/products/monitors/24lcd/)

This thing is huge and it can do 1920 x 1200. 

So I wrote a couple of shell scripts (and I created icons for them on my desktop, so they're just one click away) that will switch to this huge external screen (and turn off my laptop's LCD panel), or turn off the external screen and switch back to my laptop's LCD, or create one huge virtual screen. So maybe you can use these scripts to give you an idea how you might do it on your system. It looks a bit complicated but once you played around with this and get the hang of the syntax it's really really easy!

This is the most important command: It will turn the laptop's LCD screen back on (if it's off) and reset the screen to the laptop's native resolution (1280 x 800 in my case; your's is probably higher, e.g. 1400 x 1050?): ```
#! /bin/bash
xrandr --output LVDS --mode 1280x800 --rate 60 --output VGA --off
``` ... So I made an icon for this one and placed it somewhere in the upper left corner, so I can always reach it again if I'd need to.

Then this one switches off the laptop's screen and instead gives me a 1920 x 1200 desktop on my shiny new 24" Sun LCD: ```
#! /bin/bash
xrandr --output LVDS --off --output VGA --mode 1920x1200 --rate 60 --pos 0x0
```

And this one places the two screens "on top" (in a virtual way) of each other. Please read the manual (man xrandr), there are other settings possible as well, e.g. have the laptop's LCD panel "on the left" and your external screen "on the right". I had to put mine "on top" of each other because of some silly limitations my Intel chipset currently seems to have (2048 x 2048 max. virtual screen size or you can make it bigger but then lose DRI support ...) . You having an ATI based card probably don't have that limitation, so you probably can place your screens "next to" each other (virtually). It's just a matter of changing the location keywords (e.g. "--left-of" instead of "--below"):
```
#! /bin/bash
xrandr --output LVDS --above VGA --mode 1280x800 --output VGA --below LVDS --mode 1920x1200 --rate 60 --pos 0x800
```

BTW, some explanations about the abbreviations:

[LIST]
[*]**VGA:** That's whatever is connected to your laptop's VGA connector.
[*]**LVDS:** seems to mean "Low-voltage differential signaling" and that's how your laptop's motherboard is talking to your laptop's LCD panel, via that signalling standard.[/LIST]

So just memorize that "LVDS" is your laptop's screen and that "VGA" here means whatever is connected on the external port ....  Then changing resolutions on-the-fly via the "xrandr" command is very very easy.

I tried with various external screens and it's really a cool feature they built into Gutsy.

For those absolutely insisting on doing this graphically (e.g. with a point and click GUI tool) I found this here: "URandr". You will have to download the package and install it. Once it's installed you'll find it in the "System > Preferences" menu.
[http://albertomilone.com/urandr.html](http://albertomilone.com/urandr.html)

Get this package:
[http://albertomilone.com/ubuntu/urandr/urandr_0.1+0ubuntu12-1_all.deb](http://albertomilone.com/ubuntu/urandr/urandr_0.1+0ubuntu12-1_all.deb)

---

### Post by Elmer Fudd on 2008-01-18
I upgraded to Gutzy when it came out. The install went flawlessly creating a dual boot (XPpro). Everything worked - and ran faster than anything in my XP boot. 
Then I loaded kde4 and the latest nvidia restricted drivers. Sound  and wireless  went away.. "lshw" shows them present but "unclaimed". I have been unsuccesful in getting the wireless and sound hardware "reclaimed".
If I run from a live CD everything works.

HP dv9000t dual core, 
82801G (ICH7 Family) High Definition Audio Controller,
PRO/Wireless 3945ABG Network Connection

---

### Post by jbaerbock on 2008-01-18
Yeah I finally got gutsy working after some trial and error. I'm not messing with kde4 untill Kubuntu comes out with Hardy. Not much different than what I have now anyway. Rather my system still work and wait a few months for the next Kubuntu.

---

### Post by EXCiD3 on 2008-01-18
> **jbaerbock said:**
> Yeah I finally got gutsy working after some trial and error. I'm not messing with kde4 untill Kubuntu comes out with Hardy. Not much different than what I have now anyway. Rather my system still work and wait a few months for the next Kubuntu.

I agree, I'm waiting until KDE4.1 is released as that release is going to be an actual full replacement of KDE3. Currently KDE4.0 is missing enough functionality that it is unusable for me.

---

### Post by vgrisham on 2008-01-18
I've got an HP Compaq NX6110, and Gutsy works like a charm on this laptop. Everything (including wireless and 3D rendering) just worked, out of the box. Gutsy is by far the most automatic and stable release of Ubuntu yet.

---

### Post by canthus13 on 2008-01-19
Wow.  What a statement.  I'm running Gutsy just fine on an HP dv6226cl.  I'd love to share how I managed it, but I'm not really sure... the only issues I had were solved by adding the noapic and nolapic boot options.  The wireless card worked fine with restricted drivers, and usb support works fine once you add the irqfixup boot option. If anyone wants any particular file dumps, ask me.  I'd be happy to post them.  Just tell me what you need.  (Where the file is located, what command outputs, etc...)

Wow.... I just checked, and apparently, even the remote is working fine. :)

---

### Post by edgecoug71 on 2008-01-19
I have 7.10 on my HP dv9000t laptop and the only thing that I have run into has been issues with the initial boot when you have to use noapic, but I have compiz-fusion, conky,  and AWN running on this machine have you read all the forums on issues with the HP laptops because I have no errors when I use my machine and everything works fine.

---

### Post by EXCiD3 on 2008-01-19
> **edgecoug71 said:**
> I have 7.10 on my HP dv9000t laptop and the only thing that I have run into has been issues with the initial boot when you have to use noapic, but I have compiz-fusion, conky,  and AWN running on this machine have you read all the forums on issues with the HP laptops because I have no errors when I use my machine and everything works fine.

Why are you using noapic on a dv9000t? Since the 't' models are intel based, there are next to no compatiiblity issues with these models. I have never needed to use ANY boot parameters on my dv9000t. The problems spring up with the AMD based laptops and some of the newer nvidia cards, etc. We lucked out and got the most compatible hp laptop :D

---

### Post by butsam on 2008-01-20
I have an HP Pavilion dv9000, with nVidia GeForce Go 6150, otherwise the standard load (1 GB RAM).

When I tried booting from Live CD, both from DVD and from CD, for version 7.10, I get all of the text-based start-up things registerring as "OK", but then the system hangs with a completely blank screen. I assume that means the video driver was not right.

So, I tried booting in safe mode, and I got the same problem.

Does going to 7.04 fix this problem? It seems to be more severe than what others here were experiencing... I can't even boot the LiveCD.

---

### Post by EXCiD3 on 2008-01-20
> **butsam said:**
> I have an HP Pavilion dv9000, with nVidia GeForce Go 6150, otherwise the standard load (1 GB RAM).

When I tried booting from Live CD, both from DVD and from CD, for version 7.10, I get all of the text-based start-up things registerring as "OK", but then the system hangs with a completely blank screen. I assume that means the video driver was not right.

So, I tried booting in safe mode, and I got the same problem.

Does going to 7.04 fix this problem? It seems to be more severe than what others here were experiencing... I can't even boot the LiveCD.

You can try it, however with a lot of the newer nvidia graphics cards, people are having many problems such as yours. I have not, and never will encourage people to use Gutsy. Try using Feisty and if that doesnt work you can always use the alternate cd to install, and then use Envy to install the graphics drivers. Gutsy broke a lot of things and has ruined the ease of installation for many users because they experience random and little documented problems. You could even try Hardy Heron Alpha 3, its what im currently running and it seems to be the most stable new release after feisty that you can get. It automatically setup my external monitor without ANY extra configuration. Gutsy prevented me from doing this and Feisty required me to configure it. Hardy Alpha 3 might even be your best bet. Its up to you.

---

### Post by spidermonkey on 2008-01-21
Well... I am not sure about DV9000 series but my DV2124TU is running better than its earlier occupant [ XP media center edition] . I got most of the things working out of the box without any  problem right after installation. Webcam works fine with ekiga [ with a tweak] . Compiz fusion, conky, AWN, Elisa media center all work fine. The only problem I see is the volume buttons . They work with a proper on screen display but the main volume is controlled PCM while these button operate on Master volume. Any body got a pointer to it..kindly post.  suspend function work with a small tweak  Well ... I am not sure why but the [Xorg bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969") reported on saturday didnt  break any of my application including amule and eclipse. :confused:

---

### Post by butsam on 2008-01-21
> **EXCiD3 said:**
> You can try it, however with a lot of the newer nvidia graphics cards, people are having many problems such as yours. I have not, and never will encourage people to use Gutsy. Try using Feisty and if that doesnt work you can always use the alternate cd to install, and then use Envy to install the graphics drivers. Gutsy broke a lot of things and has ruined the ease of installation for many users because they experience random and little documented problems. You could even try Hardy Heron Alpha 3, its what im currently running and it seems to be the most stable new release after feisty that you can get. It automatically setup my external monitor without ANY extra configuration. Gutsy prevented me from doing this and Feisty required me to configure it. Hardy Alpha 3 might even be your best bet. Its up to you.

Thanks for the help!

OK, I am going to show my newbieness now...I'm coming over from Fedora-land, Ubuntu is more user-friendly from what I hear, so the rest of my family will have an easier time with it.

Anyway, is there a scheduled release date for Hardy Heron? Sounds like Alpha 3 is pretty stable and the release may be just around the corner... If that is the case, I can simply wait a week or two to switch from Fedora to Ubuntu... If it's still a ways away though I may give 7.04 or the Alpha 3 a shot.

Thanks,

Sam

---

### Post by EXCiD3 on 2008-01-21
Hardy's official release date is set sometime in April 2008. Its a ways off however the Alpha is quite reliable. I'm not sure which would give you better support but either one is probably better than Gutsy.

I have always liked the ease of use with Ubuntu and with a large user base there is always tons of support.

---

### Post by sgbeamer on 2008-01-21
I am with you guys.  I have an 2 year old HP Pavilion 1000 laptop that has worked great since installing Dapper on it the day I bought it.  I have been through every upgrade without issue.  I upgraded to Gutsy last week.  My wireless network card says it's connecting but never gets an IP address.  I've done all the old tricks of turning off IPv6, etc and nothing.  It's disappointing that I will have to now have to try to uninstall Gutsy and go back to Fiesty.  I feel like I'm back in Microsoft land spending more time fixing things than actually using my PC.

---

### Post by EXCiD3 on 2008-01-21
Yeah sgbeamer i agree. Gutsy was a waste of time. There was absolutely NO reason for me to upgrade just like there is no reason for me to have a dual boot with Vista. XP -> Vista is about the equivalent of Feisty -> Gutsy. I highly recommend you try out Hardy if you want. Its good feedback for the developers the more users to test it out and report the bugs/instabilities. It seems to be more stable than Gutsy to me. Everything was automatically configured for me, however it was about the same on Feisty as i have an Intel based laptop. I was very surprised with the dual monitor configuration automatically being done for me without any help.

---

### Post by stanley82 on 2008-01-21
I got Feisty up on two amd 64 machines no problem.  Updated one to gutsy okay.  Decided to update  my old k6-2+ to 32 bit gutsy and well  I got the screen with the install icon but could not move the mouse.  I installed an old edgy disk okay.  Ian.

---

### Post by RudolfMDLT on 2008-01-22
I have an NC6000 - the only thing that I have found to not work is the WiFi button. On the plus side, with the previous version of Ubuntu, the touchpad would stop working after 15-20min. it's working flawlessly now + it has the bonus scroll bit on the right of the touchpad which the standard nc6000 shouldn't really have. Maybe I'm running different laptop's drivers?

---

### Post by dhysk on 2008-01-23
i have a hp Pavilion dv6000 series media addition.  So far Gusty works great.  All my cool touch buttons across the top work perfectly preconfigured. The media button even opens up music player. The Mic works haven't tried the webcam yet, not even sure if it came with software to use it realy.  Little nitnoide things with the touch pad scroll just stops but those problems seem to go WAY back in the forums, and when the second person logs on the visual effects go back to base setting sometimes, but all in all pretty happy,

I've been playing with other distros and the seller to me was i didnt have to use wpa_supplicant to connect to my router.  I'm sure i coulda found something myself but I also like the look aswell. Maybe i just got lucky but workes great for my HP, its even a refurbished one.

---

### Post by haiku88 on 2008-01-23
was very leery of upgrading my nx6310 after reading many horror stories, but gave it a try as I couldn't get a bluetooth USB adapter working right w/ Feisty....all is well so far, bluetooth and my BCM4311 wifi work fine and battry life seems about the same

---

### Post by firestormx37 on 2008-01-23
I have an HP dv5000 laptop.  I have had no problems with the upgrade to Gusty.  The only problem I have is that suspend will not work, but I had that problem with Feisty also.  Video card works fine including the use of Compiz.

---

### Post by GearJammer on 2008-01-23
ok, I have searched & searched, its been a couple of days now and still haven't been able to get this to work...

I recently get an HP dv2610us and have been able to get the nvidia drivers to work and have gotten the wireless to work, but I still can't get it to boot with out the CD.

I installed with the alternate CD and apparently currently need it in order to boot 
removed the splash, and if gives me a missing modules, devices: error /dev/disk/by-uuid/... does not exist
the by-uuid folder isn't there unless it actually boots

I am lost... and I am about to give up, I have tried to install feisty with out any luck and am about to give up completely and just reinstall xp or vista... any advice would be greatly appreciated

for what its worth this is not a dual boot

thanks

---

### Post by inverseroom on 2008-01-27
I've got a three-year-old Pavilion dv1000, and Gutsy is working quite well.  The only bug I haven't been able to stamp out is the wireless-won't-work-after-suspend one.  Suspend itself works.

Is Hardy supposed to be addressing this problem?  I can get the wireless back on without rebooting maybe 75% of the time, but it would be lovely if this could actually work reliably.

---

### Post by EXCiD3 on 2008-01-27
I doubt that this has been fixed in Hardy as of yet. Hopefully this issue will be addressed before the final release. Only way to find out is if they get people to test it. I recommend downloading Alpha 3 and making a small paritition to install it in. I personally find it much better than Gutsy and Feisty. i have been using it for the past 3 weeks and everything has worked perfect for the most part, however I havent tried suspend/hibernate yet. My startup/shutdown times are quick enough that i find it easier and more reliable to just shutdown instead.

---

### Post by butsam on 2008-01-27
It works for me, except the sound card. I have the Realtek Hi-Def Audio  that came with the dv9000. Anyone had success yet? I had fuzzy sound once upon a time, now I have no sound. I also get a strange message when starting up a program:

Couldn't open library: libX11.so

Sam

---

### Post by kbish on 2008-01-28
HP Compaq 6710s (Intel Core 2 Duo 2.00GHz /  2G RAM / 120G HDD)
Upgraded from Feisty.
All work fine except sound.

---

### Post by colecampbell666 on 2008-01-29
Will this cause problems on a 5 series laptop? (a zv5325ca)

---

### Post by EXCiD3 on 2008-01-29
> **colecampbell666 said:**
> Will this cause problems on a 5 series laptop? (a zv5325ca)
What hardware do you have?

---

### Post by colecampbell666 on 2008-01-31
Radeon 9000IGP, P4 3 Ghz, 80 Gb HDD, 383 Mb RAM.

EDIT: BroadCom Wireless that gets royally F**ked when you boot windows after installing Windows.

And Kubuntu doesn't work, as it doesn't on all of my PCs. (it hangs while downloading updates, and then won't open the updater) I'm going to try Ubuntu, if the hardware allows.

---

### Post by EXCiD3 on 2008-01-31
I have found Gnome to be more user friendly than KDE. Its all personal preference however.

Whats wrong with broadcom?

---

### Post by colecampbell666 on 2008-02-01
It doesn't work period in Ubuntu/Kubuntu; the restricted drivers don't work.

I like Gnome better too, but haven't found out how to enable 3+ desktops. I'm going to try with my desktop now that I updated the BIOS.

---

### Post by Geohevy on 2008-02-01
Will the Hardy Heron Alpha3 work on a dv6500?

---

### Post by EXCiD3 on 2008-02-01
> **Geohevy said:**
> Will the Hardy Heron Alpha3 work on a dv6500?

Yes it should. I would recommend you wait a day or two until the Alpha 4 release that was scheduled for release yesterday. Here is the download link whenever it becomes available. [http://cdimage.ubuntu.com/releases/hardy/alpha-4/](http://cdimage.ubuntu.com/releases/hardy/alpha-4/)

---

### Post by marildo on 2008-02-02
I finally could have a clean installation on my dv6220BR with no boot parameters using Hardy Heron Alpha 3.

---

### Post by EXCiD3 on 2008-02-02
Alpha 4 has officially been released. Download here: [http://cdimage.ubuntu.com/releases/hardy/alpha-4/](http://cdimage.ubuntu.com/releases/hardy/alpha-4/)

---

### Post by toben7l on 2008-02-03
as of right now, has anyone tried Gutsy on a dv9740/50/60us unit? thinking about getting one, and i want to take Windows hasta-la-Vista off as soon as I get it. seems like there's a little bit of hit and miss with the HP's and Gutsy. btw, it's the model that's got the nVidia 8600M vid card and an Intel Core 2 Duo cpu. any insight would be helpful. thanks!

---

### Post by brianh57 on 2008-02-03
I have a Compaq Presario 6000.  I'm sure there are some differences from the HP but the Compaq works great for me.  I have Intel graphics and wireless and a pretty standard 1280x800 screen so that may help.  I was very surprised by Gutsy when everything on my laptop worked right from the first boot.  Even the multimedia keys worked and the screen resolution was correct.  That was far more than I expected.  This is also the first time I've actually been able to put the 64-bit version on it and not been forced to go back to the 32-bit after a few days to get some piece of software I needed to run.

---

### Post by DMBryant on 2008-02-06
I've just installed Gutsy on an HP Compaq 8710w (Dual Core 2.45Ghz, 4Gb ram, 512mb Nvidia) and everything works perfectly. It detected the right resolution, sound is enabled, wifi works perfectly.  I think the only thing that doesn't work is the fingerprint scanner but I am not really surprised by that.  Absolutely nothing to complain about :)

---

### Post by #Reistlehr- on 2008-02-10
So originally i had a Dv9000z CTO, and it took some time, but i managed to get Gutsy to run perfect. Wireless worked with the restricted drivers, vid card ran great, sound was awesome. The motherboard died from overuse, and i got it replaced. I received a dv9700z. This is the worst laptop i have ever seen. Other than HP sending me the wrong replacement (specs not matched in newer model), Gutsy just doesnt like it. USpalsh doesnt work at all, so i completely disabled it. No need for noapic or acpi=off, in the bootline, whcih is good. Atfirst, nvidia-glx-new drivers need to be installed or you get a low compat vid error. Nothing to hard to fix. The wireless card is a whole other story. In Vista, which i already deleted, it says that its an Atheros AR5007EG, but Gutsy reports it as a 5006EG. On a 64-bit os, the wireless wont work since all the available drivers are 32-bit. mad-wifi doesn't work, nor does ndiswrapper. I tried using the 64-bit drivers from the hp site, but they are just the 32-bit with some extra crap, and ndiswrapper cannot utilize the resources. This isnt a problem since wired = faster, and im always plugged in. 

Bluetooth works oob. Dont use bluetooth so i disabled it.

All in all, if the usplash or the wireless arent a problem, it works great.

---

### Post by chavanak on 2008-02-12
Am facing no problems with gutsy except for two:
Fingerprint reader (Which i dont use much).
Load cycle count issue (I have used the ugly fix).

Everyother thing is fine!!!
 Btw am using dv6602au lappie

---

### Post by housam on 2008-02-14
Just for information . I've installed Feisty & Gutsy on two different partitions on my HP Compaq nx 7400 . Both are working flawlessly.

---

### Post by DaveRowell on 2008-02-14
You HP owners are not alone in this - my Toshiba 1805 won't start the X server no matter what I do after I updated a FRESH Xubuntu 7.04 installation!!!  I have been playing around with various distros and had decided to return to Xubuntu - installed 7.04 with no problem - updated everything - checked it out for a while - decided to "upgrade" to 7.10 - big mistake!  Video is a Trident CyberBlade/i1

Booting either the 2.6.22-14 kernel or the 2.6.20-15 one in graphical mode - the Xubuntu splash screen displays and the progress bar marches to completion - the screen goes black - there is a bit of drive activity - the machine locks-up - [ctrl] c not recognized - can't switch to a terminal - [ctrl][alt]del isn't recognized - have to power down.  Since I had a copy of the 7.04 xorg.conf file from this computer I replaced the new one (which wasn't much different) - exactly the same behavior.  The 2.6.22-14 won't even boot in recovery mode but 2.6.20-15 will.

Bah humbug ;-(

---

### Post by EXCiD3 on 2008-02-14
> **DaveRowell said:**
> You HP owners are not alone in this - my Toshiba 1805 won't start the X server no matter what I do after I updated a FRESH Xubuntu 7.04 installation!!!  I have been playing around with various distros and had decided to return to Xubuntu - installed 7.04 with no problem - updated everything - checked it out for a while - decided to "upgrade" to 7.10 - big mistake!  Video is a Trident CyberBlade/i1

Booting either the 2.6.22-14 kernel or the 2.6.20-15 one in graphical mode - the Xubuntu splash screen displays and the progress bar marches to completion - the screen goes black - there is a bit of drive activity - the machine locks-up - [ctrl] c not recognized - can't switch to a terminal - [ctrl][alt]del isn't recognized - have to power down.  Since I had a copy of the 7.04 xorg.conf file from this computer I replaced the new one (which wasn't much different) - exactly the same behavior.  The 2.6.22-14 won't even boot in recovery mode but 2.6.20-15 will.

Bah humbug ;-(

Have you tried using any boot parameters?

---

### Post by cdtech on 2008-02-14
[B]DV9608nr
NVIDIA GeForce Go 7150M
AMD Turion 64 X2 Dual-Core
Broadcom wlan
MCP67 High Def Audio
Gutsy 7.10 w/kernel 2.6.22-14-generic x86_64[/B]

I had to do some configuration and modifications to get everything right but all works great. I'm happy with my install. I used the "Alternate CD" for the install using a second drive of 250G. I've also used the "Gparted CD" to rearange the drive with no isses. 

The tools are there and sometimes someone has already made a patch for some issues, thats whats nice about an "Open Source OS" (such as GNU/Linux), you can taylor it to your own needs and wants. Sometimes you have to roll up your sleeves and roll your own kernel.

I'm running 64bit and wouldn't change it for the world. Backward compatibility for running 32-bit and most open-source software can easily be compiled for x86_64.

Gzip compression, RAM speed, and Kernel compilation performance are far better with 64. I can backup my entire system (compressed) much faster than 32 and less strain on my CPU. I can't find enough programs to run at one time to cause my system to lock up or lag. Multitasking is superior on my laptop now.

My 64 bit laptop is wonderfully fast at everything I&#8217;ve tried to do. If you do serious number crunching or serious multimedia work consider the 64 bit.

I've had my share of problems installing Ubuntu 64 on my laptop but nothing a little reading and configuring couldn't repair. Staple programs such as wifi, sound (aside from the headphone jack sense, which I posted a fix for [[COLOR="DarkRed"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=690942")) and graphics where all straight forward to configure, using others post here at Ubuntuforums and some common sense.

---

### Post by revol on 2008-02-14
My experience with Gutsy on HPC nx6325..bad!
1) Booting:
PCI: Cannot allocate resource region 0 of device 0000:00:14.2
MP-BIOS bug: 8254 > timer not connected to IO-APIC
--
The second error is the same of Feisty, so I added noapic to boot options.
2)bcm43_fwcutter, does not work. Really better ndiswrapper
3) Audio problems: even if I've done this ([http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325#Onboard_Sound](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325#Onboard_Sound)), my input audio crashes, now giving me this error on dmesg: hda-intel: Invalid position buffer, using LPIB read method instead. I can't use any application like Skype, etc.

I really think the most part of these problems are related to kernel linux, not to Ubuntu Gutsy! I tried different distros having the same troubles, since kernel 2.6.20 (Feisty Fawn)](*,). Bad news for who is waiting Hardy Heron: these troubles are alive!! always in kernel 2.6.24:frown:
I was waiting for this kernel, googling I found some discussion about these problems, but nothing...I tried Sidux with kernel 2.6.24 (Hardy kernel like) and every issue is not resolved...
Finally, I'm checking this page [http://h71028.www7.hp.com/enterprise/cache/363030-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/363030-0-0-0-121.html), concerning linux support from HP, but this page is unchanged since 2006. _I'LL NEVER BUY ANOTHER HP PRODUCT FOR THE REST OF MY LIFE! HP support for linux is a FAKE!_

---

### Post by BadPenguin86 on 2008-02-14
I am running Gutsy on an HP Dv6000. The problem that I am having is that the computer will randomly freeze. When playing audio, it skips the audio like a scratched cd, and nothing works, the mouse, <ctrl> <alt> <backspace>, nothing. Anyone know why this happens? Could it have something to do with the visual effects? Looking at the logs, the last thing that registered on them was something about ipv6 not present on my wireless. Doubt that could be it though. any clues?

---

### Post by cdtech on 2008-02-14
> **BadPenguin86 said:**
> I am running Gutsy on an HP Dv6000. The problem that I am having is that the computer will randomly freeze. When playing audio, it skips the audio like a scratched cd, and nothing works, the mouse, <ctrl> <alt> <backspace>, nothing. Anyone know why this happens? Could it have something to do with the visual effects? Looking at the logs, the last thing that registered on them was something about ipv6 not present on my wireless. Doubt that could be it though. any clues?

I would start at :
```
free
```
What graphics card do you use and the drivers?

If your running min ram then swap space is important, its the difference between the minimum virtual memory (that will prevent the system from crashing) and the amount of ram it has.

What keyboard layout are you using?

There are a lot of different things that could effect your issues, just take the smallest one and work on it. There are a lot of people here that have had the same problems that could help. You might find the fix to one problem could repair others as well.

---

### Post by Geohevy on 2008-02-14
Brand new install of 7.04 through the alternate CD completed successfully on an HP dv6500. But, when I go to login X Server fails to start, and when I try to get in through GRUB, I can't enter my password. Pressing keys does nothing.

Is there any way to fix this?

---

### Post by cdtech on 2008-02-14
> **Geohevy said:**
> Brand new install of 7.04 through the alternate CD completed successfully on an HP dv6500. But, when I go to login X Server fails to start, and when I try to get in through GRUB, I can't enter my password. Pressing keys does nothing.

Is there any way to fix this?

Normally if it fails to boot into X, it will take you to a command prompt. On a new install you should configure the hardware by:
```
sudo dpkg-reconfigure xserver-xorg
```
This will let you manually configure the hardware that is on your system.

Or you can or manualy edit the /etc/X11/xorg.conf and change the video driver to 'vesa'.

---

### Post by ahorriblemess on 2008-02-15
I just jumped to the first page and skipped to the last... I'm on a dv6704nr running Gutsy, I think it's working quite nicely. Everything works pretty well besides the headphone/speaker issue. Most fixes I've tried have just disabled my sound card completely, but otherwise, it's alright. I got my graphics card working wonderfully, I'm picking up all my neighbors WiFi signals (I don't have a wireless router, I haven't tried connected to theirs yet... I feel like that's frowned upon), remote control works, microphones work, DVD's play etc. 

Was this thread started closer to the initial release of Gutsy? I mean, aren't we urged to wait a few weeks after the release of a new version to allow time for bug fixes and all that?

---

### Post by Geohevy on 2008-02-15
> **cdtech said:**
> Normally if it fails to boot into X, it will take you to a command prompt. On a new install you should configure the hardware by:
```
sudo dpkg-reconfigure xserver-xorg
```
This will let you manually configure the hardware that is on your system.

Or you can or manualy edit the /etc/X11/xorg.conf and change the video driver to 'vesa'.

Hmmm... I tried your first suggestion, but I'm a little scared to do the second. I'm afraid it didn't help... Any other ideas? :(

---

### Post by ginnie6 on 2008-02-15
I got a new HP laptop last month and after reading all horror stories decided not to try gutsy. I wasn't happy with feisty so I've been struggling with vista. Yesterday I read some posts on gutsy actually running on hp laptops and decided to try it. Everything is running great. My broadcom card is recognized and would work but I'm not getting my network info right I think. I have had some random shutdown of programs but I think that has to do with the swap space I allocated. Vista for some reason would only let me shrink the hard drive 5gigs. If I can get wireless up and running vista is gone! Oh and I'm on an HP DV9610us.

---

### Post by BadPenguin86 on 2008-02-16
> **cdtech said:**
> 
What graphics card do you use and the drivers?

If your running min ram then swap space is important, its the difference between the minimum virtual memory (that will prevent the system from crashing) and the amount of ram it has.

What keyboard layout are you using?

There are a lot of different things that could effect your issues, just take the smallest one and work on it. There are a lot of people here that have had the same problems that could help. You might find the fix to one problem could repair others as well.

I have an Nvidia card with the restricted driver, 2 gig of ram with 1.5 gigs of swap, US Layout. The problem has went down after updating completely, but it still happens at times.

---

### Post by /home on 2008-02-16
I have a HP530.
Work's fine exape the build in Wifi(spent hours playing with ndiswrapper:confused:)
So i just use a usb wifi card:)

---

### Post by Snake16 on 2008-02-16
My box works great with Ubuntu Gutsy...after my first installation, the only thing that wont work was my broadcom bcm4312 rev.01 but i manage to fix it...and now, it works perfectly and right now im using it writing this post..anyway, dont give up..every problem has a solution..peace..

My box: HP Pavilion DV6016ea
            AMD Turion 64x2 1.6 GHz
            1 GB RAM
            64 MB Nvidia Geforce Go 7200 (256 MB shared)
            Broadcom wireless card BCM4312 rev.01

Edit: Sorry for not mentioning my graphics card and usb port...its working now...=)

---

### Post by n4zrnet on 2008-02-16
hi, all

its strange and sometimes its true that fiesty fawn on my hp dv6188ea had some issue's, it use to hang (less frequent), at times firefox would exit abruptly, then i formatted and installed gutsy 64 bit and now its been almost since the gutsy release so far so good working flawlessly. check the attached text file for more info.:)

---

### Post by johnc@crosslink.net on 2008-02-16
I've got a Compaq v6130us and Gutsy AMD64 works fine. Compiz using Nvidia's driver, sound, Broadcom w/ndiswrapper, working standby ...

Just had to compile a kernel, throw some modules in, and no problem.

---

### Post by stevepurkiss on 2008-02-17
Hi,

I'm getting random freezing on my HP dv6152eu laptop. I've spent weeks searching forums and trying various options but to no avail. I've switched off the restricted drivers for the NVIDIA which seems to make it crash less, but I'm still using the restricted drivers for the wireless.

I'm currently using the boot options nosmp and noapic, although I did see on the HP website that you're not supposed to use those options so slightly worried about that. I've tried things like iommu=off noirq debug and idle=poll but they don't seem to do anything.

Just wondering if there was other stuff I could try...

---

### Post by cdtech on 2008-02-17
> **stevepurkiss said:**
> Hi,

I'm getting random freezing on my HP dv6152eu laptop. I've spent weeks searching forums and trying various options but to no avail. I've switched off the restricted drivers for the NVIDIA which seems to make it crash less, but I'm still using the restricted drivers for the wireless.

I'm currently using the boot options nosmp and noapic, although I did see on the HP website that you're not supposed to use those options so slightly worried about that. I've tried things like iommu=off noirq debug and idle=poll but they don't seem to do anything.

Just wondering if there was other stuff I could try...

Are you running compiz (3d desktop)?
If you run:
```
free
```
What is your total RAM?
The reason I ask is that "Swap space" is the difference between the minimum virtual memory (that will prevent the system from crashing) and the amount of RAM you have.

---

### Post by zxman on 2008-02-18
This is my first linux install.  I'd like to use the GUI install on the Live CD. However, it doesn't matter if I use 7.04 or 7.10, the highest resolution I get is 800x600. The GUI install is larger than will fit on the screen.  There is no scroll bar to allow me to scroll down to the "Cancel", "Back" and "Forward" buttons.  I can size the install window larger, but not smaller.  I can install a newer NVIDIA driver, but that requires a reboot to take affect.  Since I'm booting from the Live CD, the driver changes are not saved and therefore lost.

I'm probably missing something simple.  Worst case, I'll use the Alternate CD, but would rather not.

HP Pavillion dv6707us Notebook
NVIDIA GeForce Go 7150M
1.9GHz AMD Athlon 64 X2 Dual-Core Mobile Technology TK-57

Thanks in advance.

---

### Post by stevepurkiss on 2008-02-18
> **cdtech said:**
> Are you running compiz (3d desktop)?
If you run:
```
free
```

What is your total RAM?
The reason I ask is that "Swap space" is the difference between the minimum virtual memory (that will prevent the system from crashing) and the amount of RAM you have.

Hi,

Thanks for your reply.

             total       used       free     shared    buffers     cached
Mem:       2062480     698088    1364392          0      82748     334352
-/+ buffers/cache:     280988    1781492
Swap:      4016208          0    4016208

I've 2Gb - tried it with the original 1Gb memory but still the same. 

Not using compiz - restricted NVIDIA turned off as that was making it crash more.

Haven't done any other customizations apart from the nosmp abd noapic boot options. Sometimes it will work for hours, sometimes it will crash 10 seconds after booting... 

Going to try enabling laptop mode as per [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059) see if that makes any difference...

---

### Post by stevepurkiss on 2008-02-18
> **stevepurkiss said:**
> 
Going to try enabling laptop mode as per [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059) see if that makes any difference...

Nope laptop mode doesn't make any difference, still freezing :(

---

### Post by stevepurkiss on 2008-02-18
> **stevepurkiss said:**
> Nope laptop mode doesn't make any difference, still freezing :(

hmmm... I've re-enabled the proprietary NVIDIA display drivers and it seems more stable now than before I had laptop mode. Hasn't frozen yet.... will report back if does.

---

### Post by cdtech on 2008-02-18
> **zxman said:**
> This is my first linux install.  I'd like to use the GUI install on the Live CD. However, it doesn't matter if I use 7.04 or 7.10, the highest resolution I get is 800x600. The GUI install is larger than will fit on the screen.  There is no scroll bar to allow me to scroll down to the "Cancel", "Back" and "Forward" buttons.  I can size the install window larger, but not smaller.  I can install a newer NVIDIA driver, but that requires a reboot to take affect.  Since I'm booting from the Live CD, the driver changes are not saved and therefore lost.

I'm probably missing something simple.  Worst case, I'll use the Alternate CD, but would rather not.

HP Pavillion dv6707us Notebook
NVIDIA GeForce Go 7150M
1.9GHz AMD Athlon 64 X2 Dual-Core Mobile Technology TK-57

Thanks in advance.
The "Alternate CD" is the way to go. You can use:
```
sudo dpkg-reconfigure xserver-xorg
```
To set up your hardware detection through Xorg after the install.

---

### Post by cdtech on 2008-02-18
> **stevepurkiss said:**
> Hi,

Thanks for your reply.

             total       used       free     shared    buffers     cached
Mem:       2062480     698088    1364392          0      82748     334352
-/+ buffers/cache:     280988    1781492
Swap:      4016208          0    4016208

I've 2Gb - tried it with the original 1Gb memory but still the same. 

Not using compiz - restricted NVIDIA turned off as that was making it crash more.

Haven't done any other customizations apart from the nosmp abd noapic boot options. Sometimes it will work for hours, sometimes it will crash 10 seconds after booting... 

Going to try enabling laptop mode as per [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059) see if that makes any difference...

I had the same problem. I had to go into the recovery mode to install my NVidia drivers.
```
sudo apt-get install nvidia-glx-new
```
I actually tried several, nvidia-glx, nvidia-glx-new, until I found the new to work for me. Now I get the NVidia splash screen and everything seems to work great now.

If you install one of the above it will remove the existing one automatically.

---

### Post by stevepurkiss on 2008-02-18
> **cdtech said:**
> I had the same problem. I had to go into the recovery mode to install my NVidia drivers.
```
sudo apt-get install nvidia-glx-new
```
I actually tried several, nvidia-glx, nvidia-glx-new, until I found the new to work for me. Now I get the NVidia splash screen and everything seems to work great now.

If you install one of the above it will remove the existing one automatically.

Thanks for your reply cdtech - fingers crossed at the moment as it hasn't crashed for a whole hour!!!

So, for anyone else who's got a HP dv6152eu, here's what's currently working for me:

boot options: add nosmp noapic to the entry in /boot/grub/menu.lst

Followed the instructions on [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059) for the webcam, touchpad, and laptop mode

Used the standard proprietary drivers provided in the system->administration->restricted drivers menu

---

### Post by cdtech on 2008-02-18
Good to hear its running for ya.
But when using the "noapic" boot parameter, an SMP kernel does not use the advanced features of the interrupt controller on multi processor machines. When using the "nosmp" parameter, an SMP kernel on a multi processor will operate in single processor mode, just so you know that.

---

### Post by stevepurkiss on 2008-02-18
> **cdtech said:**
> Good to hear its running for ya.
But when using the "noapic" boot parameter, an SMP kernel does not use the advanced features of the interrupt controller on multi processor machines. When using the "nosmp" parameter, an SMP kernel on a multi processor will operate in single processor mode, just so you know that.

Hi again,

The nosmp and noapic options are actually a hangover from previous versions of ubuntu where that seemed to do the trick. I've now taken those off and fingers crossed (again!) it's been up and running ok. Must be because I didn't have the laptop options on before. 

It did briefly flash a blank/black screen when I first booted up, but been ok so far...

---

### Post by cdtech on 2008-02-18
Just keep an eye on your log files. They'll tell you whats up.
```
System > Administration > System Log
or CLI:
gnome-system-log &
```
Good Luck!

---

### Post by stevepurkiss on 2008-02-18
> **cdtech said:**
> Just keep an eye on your log files. They'll tell you whats up.
```
System > Administration > System Log
or CLI:
gnome-system-log &
```
Good Luck!

Will do thx!

---

### Post by stevepurkiss on 2008-02-18
> **stevepurkiss said:**
> Will do thx!

OK, it's randomly black screening - sometimes just for a sec then comes back, then just hung once.

In the log I got this:

Feb 18 16:12:06 bluethunder kernel: [  180.660000] NVRM: Xid (0005:00): 6, PE0000 0700 ff3f5389 0000fac4 ff191d33 ff1f2035
Feb 18 16:12:06 bluethunder kernel: [  180.668000] NVRM: Xid (0005:00): 30,  L0 -> L0
Feb 18 16:12:06 bluethunder kernel: [  180.692000] NVRM: Xid (0005:00): 13, 0000 01016100 0000008a 00000404 ff000000 00004000
Feb 18 16:12:11 bluethunder kernel: [  186.420000] NVRM: Xid (0005:00): 6, PE0000 041c ff332939 0000fc60 ff000000 ff000000
Feb 18 16:12:30 bluethunder kernel: [  205.372000] NVRM: Xid (0005:00): 6, PE0000 05c8 ff0a0a0a 000077c8 00000000 03030303

---

### Post by RayArdia on 2008-02-18
Does this problem also apply to Packard Bell laptops, for I recently bought one for my wife (MX52-B-053D). It had pre-installed (Spanish) version of Vista Home basic which I have tried to swap for Gutsy and Feisty. Gutsy boots partway but stops on keyboard. Feisty hangs at same point in install then gives an error message MP-BIOS bug: 8254 timer not connected to APIC. As I have tried just about everything, including trying WinXP, I have probably got all sorts of gremlins lurking in there!
Has anyone got a clue as to what I can do now? :(

---

### Post by EXCiD3 on 2008-02-18
> **RayArdia said:**
> Does this problem also apply to Packard Bell laptops, for I recently bought one for my wife (MX52-B-053D). It had pre-installed (Spanish) version of Vista Home basic which I have tried to swap for Gutsy and Feisty. Gutsy boots partway but stops on keyboard. Feisty hangs at same point in install then gives an error message MP-BIOS bug: 8254 timer not connected to APIC. As I have tried just about everything, including trying WinXP, I have probably got all sorts of gremlins lurking in there!
Has anyone got a clue as to what I can do now? :(

Have you tried the noapic kernel boot parameters?

---

### Post by stevepurkiss on 2008-02-18
> **cdtech said:**
> Good to hear its running for ya.
But when using the "noapic" boot parameter, an SMP kernel does not use the advanced features of the interrupt controller on multi processor machines. When using the "nosmp" parameter, an SMP kernel on a multi processor will operate in single processor mode, just so you know that.

I've gone back to using nosmp noapic as it was freezing annoyingly. Provided they don't harm the machine then I'll have to live with it until I find any other solutions - the performance is fine as it's running a decent OS lol ;)

---

### Post by RayArdia on 2008-02-19
Please, a pointer in the direction of how I find out what noapic boot parameters are?:confused:

---

### Post by stevepurkiss on 2008-02-19
> **RayArdia said:**
> Please, a pointer in the direction of how I find out what noapic boot parameters are?:confused:

Hi - if you're asking what I think you're asking, then when you boot the computer and it says grub loading, press escape so you get to the menu of boot options. Press 'e' to edit the boot options of the one you normally select to boot up. 

Once you've pressed 'e', usually four lines come up - press the down arrow to get to the second one, press 'e' to edit that line, and at the end of the line (usually after the word 'splash') type 'noapic', then press enter to confirm then 'b' to boot.

If it's booted up already, you can add it permanently into the boot options by doing sudo gedit /boot/grub/menu.lst and add it to the appropriate boot option in the menu at the bottom of the file.

I'm using 'noapic' and 'nosmp' on mine so it doesn't freeze, but it's not ideal and not recommended by HP, but then they recommend windoze so what do they know lol ;)

Good luck... hth

---

### Post by RayArdia on 2008-02-19
Appreciate your help very much,
I know I've seen Grub loading at some point before, but have tried booting from both the (sent to me by Ubuntu) 7.10 .386 and the 64bit version but can't see grub loading no matter how hard I peer at the screen. Could you spare a little more help?
Ray

---

### Post by stevepurkiss on 2008-02-19
> **RayArdia said:**
> Appreciate your help very much,
I know I've seen Grub loading at some point before, but have tried booting from both the (sent to me by Ubuntu) 7.10 .386 and the 64bit version but can't see grub loading no matter how hard I peer at the screen. Could you spare a little more help?
Ray

Don't bother with the 64 bit version for now, there's lots of stuff which doesn't seem to work in it so stick to the 386 one.

If you're booting from a CD then doesn't it come up with a menu first? If so, then there should be a list of options at the bottom and one is something like edit options, press that, then that will get to the second stage of what I was talking about before where you press the down arrow then 'e' then add noapic then enter then 'b'...

---

### Post by stevepurkiss on 2008-02-19
> **stevepurkiss said:**
> If you're booting from a CD then doesn't it come up with a menu first? If so, then there should be a list of options at the bottom and one is something like edit options, press that, then that will get to the second stage of what I was talking about before where you press the down arrow then 'e' then add noapic then enter then 'b'...

OK.... I just tried it with my gutsy cd - when it comes up with the menu, press F6 Other Options, then the boot options are displayed so just type noapic then press enter. If that doesn't work try noapic nosmp like mine is, and if any work then edit the /boot/grub/menu.lst when it's installed on the machine so you don't have to do it every boot.

---

### Post by HTML-insane on 2008-02-19
That's not making much sense...
I've got a HP Pavilion ze2000 laptop, and X and all the programs in Kubuntu Gutsy work smooth as silk. The only problems I've got is using Compiz Fusion, and trying to allow the specific driver for my Graphics card (intel 85x), but it still has basic graphic card functions enabled...
Sound, Graphics, X... everything seems to work fine. It's just getting Compiz to work...
P.S. I've never used Compiz before, so it might just be me doing something wrong.

---

### Post by cdtech on 2008-02-19
Some computers have buggy code in their BIOS which prevents ACPI from functioning correctly (hence the noapic flag on boot). Thats why some would have problems and others with the same hardware and setup have no problems at all.

Microsoft's ASL compiler allows many of these errors and warnings to sneak by, as a result many OEM's write buggy code. Windows is very forgiving of bugs in the DSDT (Differentiated System Description Table) which get by Microsoft's compiler (not surprisingly).

You can tell whether your DSDT was compiled with the Microsoft compiler by the presence of "MSFT" in the DSDT line in dmesg, as below:
```
ACPI: FADT (v001 GBT AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
ACPI: MADT (v001 GBT AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff7080
ACPI: DSDT (v001 GBT AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
```
I've heard that some have luck with back dating their BIOS, or even updating.

If updating your BIOS has no effect, then recompiling your DSDT with edited fixes is the only method.

You can find step by step instructions on doing this or even find a fixed DSDT for your flavor of computer that someone else has modified using the links below.

Ref:
[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)
[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

---

### Post by stevepurkiss on 2008-02-19
> **cdtech said:**
> You can tell whether your DSDT was compiled with the Microsoft compiler by the presence of "MSFT" in the DSDT line in dmesg, as below:
```
ACPI: FADT (v001 GBT AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
ACPI: MADT (v001 GBT AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff7080
ACPI: DSDT (v001 GBT AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
```

Interesting - I got the following from a dmesg | grep MSFT

[    0.000000] ACPI: DSDT 7FF0BD5F, 8FB1 (r1 HP       MCP51M  6040000 MSFT  3000000)

So I'll be looking through those links sometime soon thanks!

...off to fry my laptop ;)

---

### Post by RayArdia on 2008-02-20
> **stevepurkiss said:**
> OK.... I just tried it with my gutsy cd - when it comes up with the menu, press F6 Other Options, then the boot options are displayed so just type noapic then press enter. If that doesn't work try noapic nosmp like mine is, and if any work then edit the /boot/grub/menu.lst when it's installed on the machine so you don't have to do it every boot.
Thanks for your patience Steve!
Tried all the above using the "genuine" Ubuntu 7,10 i386 version disk, first with noapic then with noapic nosmp. I both cases, after keying enter I end up with only a cursor top LH corner of the screen. No way out except to switch off.:(

---

### Post by RayArdia on 2008-02-21
> **cdtech said:**
> Some computers have buggy code in their BIOS which prevents ACPI from functioning correctly (hence the noapic flag on boot). .................
You can tell whether your DSDT was compiled with the Microsoft compiler by the presence of "MSFT" in the DSDT line in dmesg, as below:
[CODE]ACPI: FADT (v001 GBT AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
ACPI: MADT (v001 GBT AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff7080
ACPI: DSDT (v001 GBT AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000[/CODE........
Ref:
[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)
[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

Problem - can't do all that on the laptop (the one with the problem) because I can't get Ubuntu (or any other OS) to boot:confused:

---

### Post by cdtech on 2008-02-21
> **RayArdia said:**
> Problem - can't do all that on the laptop (the one with the problem) because I can't get Ubuntu (or any other OS) to boot:confused:

Does your computer go through POST? Can't you get into BIOS? Do you receive any beep codes?

---

### Post by Victormd on 2008-02-21
Ok, I'm trying to install Ubuntu on my wife's laptop and after install, Ubuntu won't boot. The laptop is an HP dv6000 series (I know there are issues) with Turion 64 X2 proc. Nvidia graphics, and broadcom wireless card. I tried to install Gutsy 32bits, 64bits and per this thread, feisty 32 bits (from live and alternate CD). In all cases, using the noapic allowed me to boot from the live CD. My current install is from Feisty Alternate CD 7.04. I was able to install, no problems, and I can get into the terminal. However, when I try to boot normally, it starts to boot and freezes up. Furthermore, I'm getting a PCI BUG #81[SOME NUMBERS] Found... Any suggestions???

---

### Post by tomihasa on 2008-02-22
I tried to install Ubuntu 7.10 to my 5000 series HP laptop (HP Pavilion dv5037EA), but the installation stopped at 15% and didn't tell me any reason what was wrong. Then I tried installing Ubuntu 7.04 and it told me something about my disk, and I found out the external USB hard drive wasn't formatted correctly. Eventually I was able to install Ubuntu 7.04 and then Ubuntu 7.10 to the disk (I wanted to check out do they both get installed). By the way, with my Fujitsu Siemens Amilo L7310GW laptop I wasn't able to install either Ubuntu at all, so I installed Mandriva instead.

---

### Post by RayArdia on 2008-02-22
> **cdtech said:**
> Does your computer go through POST? Can't you get into BIOS? Do you receive any beep codes?

Had to lookup POST, now wiser:) In answer; I assume so, because I can get into BIOS. I haven't heard any beep codes.
Ray

---

### Post by cdtech on 2008-02-22
> **RayArdia said:**
> Problem - can't do all that on the laptop (the one with the problem) because I can't get Ubuntu (or any other OS) to boot:confused:

> Had to lookup POST, now wiser In answer; I assume so, because I can get into BIOS. I haven't heard any beep codes.

I just asked that because you said nothing would boot. Can you get to a terminal using GRUB?

---

### Post by RayArdia on 2008-02-22
:confused:Ashamed to admit I don't know how.:(  Just cottoned on - do you mean Terminal on the computer I'm trying to boot, or this one, on which I'm running Ubuntu 7.10?

---

### Post by haemphyst on 2008-02-22
Well, I have a Compaq V6444US, and I don't really know what the differences are between the Compaq and the HP toys are, but I had (have) ZERO install or running issues.  Everything works perfectly...

Core Two Duo, 2GB, 250G drive.  Everything just got nailed, even the "extra" video setting in the desktop appearances works perfectly.  Maybe a Compaq laptop is where you need to look, rather than the HP.  I know...  for all intents and purposes, they are the same machines, but obviously, they AREN'T, if a fresh install works on on, but not the other!

---

### Post by Ayuthia on 2008-02-22
> **haemphyst said:**
> Well, I have a Compaq V6444US, and I don't really know what the differences are between the Compaq and the HP toys are, but I had (have) ZERO install or running issues.  Everything works perfectly...

Core Two Duo, 2GB, 250G drive.  Everything just got nailed, even the "extra" video setting in the desktop appearances works perfectly.  Maybe a Compaq laptop is where you need to look, rather than the HP.  I know...  for all intents and purposes, they are the same machines, but obviously, they AREN'T, if a fresh install works on on, but not the other!
Generally, the HP/Compaq laptops with the Intel hardware tend to work out of the box.  The ones with AMD/Nvidia/ATI/Broadcom/Atheros hardware that require some tinkering.

---

### Post by haemphyst on 2008-02-22
Good to know...  Thank you!

---

### Post by rocky909 on 2008-02-22
:KSI am a new comer in the gutsy Ubuntu world.Pls help me to install this os.I want to dual boot with VISTA ( I hate it but it came wt my laptop from bestbuy nd I need to use it untill I am familiar wt Linux world)

:guitar:**_My system_**- ***hp laptop dv 6736nr***
AMD Turion 64 x2 TL 60
2 GB RAM
Nvidia GeForce Go 7150M (shared)
15.4" WXGA High Def. Bright View Wide Screen Display (In the system I tried to find which model,it says only "PnP")
With webcam,Light Scribe 8X DVD drive

:confused:**_My problem while installing Ubuntu 7.10 (Plan to dual boot with VISTA)_**
I tried Ubuntu-7.10 thrice for last 4 days to make sure it works from 3 different cd nd source.(I had a genuine disk from Ubuntu which they sent me over mail-didnt work after a while,2nd & 3rd one one-downloaded from this site)
At first I configured the graphics to wide screen nd hp wide aspect. but later wen it was not installing then I did just as it said me to do  ..evertime when it comes to loading window after tht it kept me on nd on for almost 5 hrs..It said like this(Icant recall full)
Loading..Please wait..(at the top of the black nd white window,I waited each time like 2 hrs nd one time 5 hrs)Just below this it says with few line like this--
Ubuntu is a free operating sytem.It does not gurantee .....
then in the same window, it said me like this
If u want to get in as root pls enter command sudo nd lab la..( I didnt do nothing as I dont know any command.)
from this window I cant go anywhere as it kept me waiting nd waiting..I waited for 5 hrs at one point..

So frnds u hav any solution for this new comer to join in ur Ubuntu world..
I heartly thank your help and spending ur valuable time.

Rocky
NY,U.S.A

---

### Post by Victormd on 2008-02-22
did you try the alternate CD?
I had a bunch of issues installing on my wife's HP laptop. I couldn't boot into the live CD unless I hit F6 at the menu options and added "noapic" to the end of the line (before the --) then it installed fine, but I was never able to boot. I could only boot into the terminal... I tried Ubuntu 7.04 and 7.10, both 32 and 64 bits... Now I left it at Ubuntu 7.10 32 bits but had to add a bunch of comments to the boot menu (i.e. noapic nolapic irqpoll noirqdebug) using "e" to edit the grub menu before boot. Then after updating the system, no problem... just trying to install my wireless...

---

### Post by rocky909 on 2008-02-23
> **Victormd said:**
> did you try the alternate CD?
I had a bunch of issues installing on my wife's HP laptop. I couldn't boot into the live CD unless I hit F6 at the menu options and added "noapic" to the end of the line (before the --) then it installed fine, but I was never able to boot. I could only boot into the terminal... I tried Ubuntu 7.04 and 7.10, both 32 and 64 bits... Now I left it at Ubuntu 7.10 32 bits but had to add a bunch of comments to the boot menu (i.e. noapic nolapic irqpoll noirqdebug) using "e" to edit the grub menu before boot. Then after updating the system, no problem... just trying to install my wireless...

I downloaded from here twice- the 64 .
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
isn't it the one? I also had the main cd from ubuntu (7-10, 64 bit) posted to me by mail..I am sorry to ask u so lamen question..Is there any difference between alternate cd and these cd's?
Thank for spending your time to reply promptly.
Rocky

---

### Post by cdtech on 2008-02-23
> **rocky909 said:**
> I downloaded from here twice- the 64 .
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
isn't it the one? I also had the main cd from ubuntu (7-10, 64 bit) posted to me by mail..I am sorry to ask u so lamen question..Is there any difference between alternate cd and these cd's?
Thank for spending your time to reply promptly.
Rocky

You have to check the alternate cd box just below for the text based installer. That's the right page though.

---

### Post by rocky909 on 2008-02-23
> **cdtech said:**
> You have to check the alternate cd box just below for the text based installer. That's the right page though.

thanks cdtech

---

### Post by vigyani on 2008-02-24
I am using HP NX 6310 laptop with Ubuntu 7.10, everything works fine expect hibernate.

Actually on fresh install hibernate was working but suspend was not working. I updated the kernel to linux-image-2.6.22-14-generic 2.6.22-14.52, after this update hibernation does not work but suspend works.:confused:

Laptop has a Broadcom wireless module, it works fine with Ndiswrapper.

regards:)
Vig

---

### Post by Lizzy on 2008-02-24
I recently bought an HP G7030, installed Gutsy and i'm dissapointed. I whiped off Vista since i got a virus after only 3 days which made the box unbootable and the rescue CD was totaly useless. Now i'm stuck with Gutsy . Sound's not working properly (headsets not working/detected), graphics card not supported/blacklisted, wireless not working properly..aso... I hope the next release fixes all that stuff, cause Vista is NOT getting back on that laptop ever again. Would Feisty work on that Laptop i wonder?? Anyone who knows?
Cheers

---

### Post by calvin6 on 2008-02-24
ok i'm an ultra noob when it comes to linux. Decided to get my feet a little wet and give it a whirl with my brand new HP tx2000z. Sucks that I find out about HP problems NOW after installation lol. So these are my problems so far...

-can't enable video driver from restricted drivers. when I click enable, my error message is
    "The software source for this package nvidia-glx-new is not enabled"
    no idea what that means so if someone could help me with that, that would be awesome

-can't pick up wireless signal. googling around, i found a post that people had problems with the network manager and they recommended wicd. I downloaded that and am using that now. I don't think that the wireless is enabled. Don't know how to go about that

- These are the problems so far. I'm sure more will spring up as I go along. If someone could help me fix these, you can tell people you helped an oober noob with linux lol. thank you

btw, if it helps any, the only thing i see under restricted drivers is the Nvidia accelerated graphics driver

---

### Post by philven on 2008-02-24
I am using Gutsy on an HP zv5370 laptop.  It works well except the touchpad is way too sensitive and I can't get the sensitivity down.  I end up turning it off when I use Open Office.  Other than that everything works.  When I upgraded I thought I would lose the wireless connection, but it worked fine.  I had to make some adjustments in WCID but did not have to reinstall the Broadcom drivers or NDISWRAP.

Anyone know how to reduce sensitivity on the touchpad?

---

### Post by gizmoarena on 2008-02-24
I tried gusty and Mint 4.0 on my NC8000.
Both of them work nice EXCEPT the suspend and hibernation.
None of them is working on gusty or mint 4.0

Before installing restricted driver, closing lid doest response at all. after installation, closing lid turns of the display.

By the way, when using live CD, ubuntu takes a long time to show up its desktop. Mint doesnt have this problem.

I'm looking for a decent way of sleep and hibernate. 
I guess my BIOS or my ATI mobility is screwing this up :mad:

---

### Post by rocky909 on 2008-02-24
> **Lizzy said:**
> I recently bought an HP G7030, installed Gutsy and i'm dissapointed. I whiped off Vista since i got a virus after only 3 days which made the box unbootable and the rescue CD was totaly useless. Now i'm stuck with Gutsy . Sound's not working properly (headsets not working/detected), graphics card not supported/blacklisted, wireless not working properly..aso... I hope the next release fixes all that stuff, cause Vista is NOT getting back on that laptop ever again. Would Feisty work on that Laptop i wonder?? Anyone who knows?
Cheers

Hey Lizzy
I am facing the same prob like you..I wiped off the Vista..But still I have warranty...So I am gonna go to bestbuy nd they will fix it for me may be..I will try to make 3 drive ..One for vista...one backup..and leave 30gb for kbunutu 7.10...talk to your store from where u bought it..I think u also deleted the backup partion from where the vista restore's (if u use backup cd even,it requires that partion)..now I am also stuck like u..when i tried to get the vista installed after formatting by the XP cd , it says me that NTDLR  missing..press CTRL+ALT+DEL to restart...
try to talk to your store and get one backup cd...Hope you will find something out for you
Rocky

---

### Post by Ayuthia on 2008-02-25
> **philven said:**
> I am using Gutsy on an HP zv5370 laptop.  It works well except the touchpad is way too sensitive and I can't get the sensitivity down.  I end up turning it off when I use Open Office.  Other than that everything works.  When I upgraded I thought I would lose the wireless connection, but it worked fine.  I had to make some adjustments in WCID but did not have to reinstall the Broadcom drivers or NDISWRAP.

Anyone know how to reduce sensitivity on the touchpad?

Have you tried installing gsynaptics?  There should be a setting in there to control sensitivity.

---

### Post by Rickard on 2008-02-26
I have a HP dv6500
Installed Feisty and later upgraded to Gutsy.

Had some problems when installing, but after solving them I could upgrade to Gutsy, everything still works fine and I'm very happing switching from XP to Ubuntu since HP only provides drivers for Vista almost no hardware worked in XP but with Ubuntu Linux it works perfectly.

The first issue was that the X screen crashed "No X server found", (i had to pick Vesa-driver in program 'xdpkg-reconfigure xserver-xorg'). 

Second issue was wireless network, something I never got working the last time I tried Feisty, but now it worked when i installed the windows drivers with ndiswrapper after uninstalling the restricted Linux-drivers.

No big problems but it took a while to find the solutions. Perhaps there is a Wiki-page where users can post solutions for common problems?

---

### Post by tcpkid_82 on 2008-02-26
true XGL does not work but every thing else works for me though... i ordered free cd's thinking that it will work but better actually its just crap without XGL.. every thing works in the 7.04 release...:)

---

### Post by ruller on 2008-02-27
Hye guys, I'm new to the whole ubuntu forums, thing so can someone give me a hand? I was running a windows vista home premium, but then I got tired of it and Install gusty gibbon (ubuntu 7.10) on my whole hard drive. Now I want to install windows again and ubunt studio. 




Problem: Windows vista can only be installed on NTFS  partitions. How can I turn ext3 partitions into NTFS? 


Thanks, in advance

---

### Post by rocky909 on 2008-02-27
> **ruller said:**
> Hye guys, I'm new to the whole ubuntu forums, thing so can someone give me a hand? I was running a windows vista home premium, but then I got tired of it and Install gusty gibbon (ubuntu 7.10) on my whole hard drive. Now I want to install windows again and ubunt studio. 




Problem: Windows vista can only be installed on NTFS  partitions. How can I turn ext3 partitions into NTFS? 


Thanks, in advance

do u have any OEM disk (best if u have it) or recovary disk ready for emergency? I tried to install 64 bit ubuntu 7.10 nd ended up removing my vista and later i cant get it back as I didnt have the oem disk...My recovary disk also failed to restore my vista....later on,I changed my laptop after a long hassel..
read all the threads before u knw wat u r doing..
process to partion 
u need to go to vista's partion management..click to my computer(right click)..go to disk management..shrink HDD by keeping the size(wat u want to give to ur ubuntu)..keep this as unallocated...
then u can restart the pc by rebooting..when u go to partion make sure u give this unallocated partion to dear gutsy..
Let us know if we need any help..lets end the microsoft's imperialism together..
Cheers
Rocky

---

### Post by K.Mandla on 2008-02-28
I've unstickied this since it seems the caution against Gutsy on HP machines doesn't necessarily hold true any longer.

And as a side note, I have a zv6000 and Gutsy runs fine.

---

### Post by EXCiD3 on 2008-02-28
> **K.Mandla said:**
> I've unstickied this since it seems the caution against Gutsy on HP machines doesn't necessarily hold true any longer.

And as a side note, I have a zv6000 and Gutsy runs fine.

Ok thanks, i agree, it seems that most of the problems have been worked out and fixes are available.

---

### Post by HitRefresh on 2008-02-28
That is great to hear ppl have success with Gutsy on the HP laptop. I recently bought a HP dv6704nr. I'd like to install Gusty on it. I tried to boot from the Live CD and it seemed to work fine (yay!). 

Only thing is that the resolution seemed a bit off, the Gutsy screen was too big. Maybe because I need graphic drivers ? I was just hoping it wont look like that when I do the full install.

That leads me to my question: What is the next step in fully installing Gutsy on the HP laptop ? Is there a guide I can follow for this to get past issues and such ? I'm relatively a noobie in installing an OS. Any help in directing me would be appreciated.

---

### Post by EXCiD3 on 2008-02-28
> **HitRefresh said:**
> That is great to hear ppl have success with Gutsy on the HP laptop. I recently bought a HP dv6704nr. I'd like to install Gusty on it. I tried to boot from the Live CD and it seemed to work fine (yay!). 

Only thing is that the resolution seemed a bit off, the Gutsy screen was too big. Maybe because I need graphic drivers ? I was just hoping it wont look like that when I do the full install.

That leads me to my question: What is the next step in fully installing Gutsy on the HP laptop ? Is there a guide I can follow for this to get past issues and such ? I'm relatively a noobie in installing an OS. Any help in directing me would be appreciated.

Take a look at this tutorial: [http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)

Once hardy heron is released aldeby and I will be writing a new tutorial on how to install Hardy on HP and Compaq laptops. This will however be released in april sometime.

---

### Post by HitRefresh on 2008-02-29
Very impressive guide, IMHO. 

The laptop is not Intel-based, though. AMD64 Athlon. Someone else on the forums has given me some instructions for the AMD, so I'll probably combine those with your guide to hopefully get everything working. 

Thanks!

---

### Post by cdtech on 2008-02-29
> **HitRefresh said:**
> That is great to hear ppl have success with Gutsy on the HP laptop. I recently bought a HP dv6704nr. I'd like to install Gusty on it. I tried to boot from the Live CD and it seemed to work fine (yay!). 

Only thing is that the resolution seemed a bit off, the Gutsy screen was too big. Maybe because I need graphic drivers ? I was just hoping it wont look like that when I do the full install.

That leads me to my question: What is the next step in fully installing Gutsy on the HP laptop ? Is there a guide I can follow for this to get past issues and such ? I'm relatively a noobie in installing an OS. Any help in directing me would be appreciated.

I'm running an HP dv9608nr AMD64. Use the "Alternate CD". Once you have it installed you can use the "Restricted Drivers", which are not installed by default but are available through menu selection. I'm running Gutsy 7.10 with no problems, I've decided to wait on the Hardy due to instability issues. Besides, why fix what ain't broke.

I'm also using a separate hard drive for my install, keeping my Vista for web development testing and a few programs I can't use through GNU/Linux.

Good Luck......

---

### Post by HitRefresh on 2008-02-29
Yeah, I'd like to *sigh* keep Vista around. Eventually I'd like to be Vista-to-Ubuntu 100% 
Anyway, I was hoping to setup a dual-boot for now. There are many how-to's on how to go about it. Anyone use any that is pretty reliable or accurate ?

---

### Post by cdtech on 2008-02-29
> **HitRefresh said:**
> Yeah, I'd like to *sigh* keep Vista around. Eventually I'd like to be Vista-to-Ubuntu 100% 
Anyway, I was hoping to setup a dual-boot for now. There are many how-to's on how to go about it. Anyone use any that is pretty reliable or accurate ?

Here's a post about using Vista to resize your existing drive for Ubuntu.

[[COLOR="DarkRed"]Ubuntu and Vista[/COLOR]]("http://ubuntuforums.org/showthread.php?t=464425")

---

### Post by Kedaeus_Sendre on 2008-03-02
Hrmm, I'm running Gutsy (2.6.22-14-Generic Kernel) on a HP Pavillion DV6700 laptop with minor issues. Everything works though.

Using the generic kernel all I had to do was download the linux-backport-modules
to get my sound working. It doesn't work as intended (i.e. I use the quicklaunch volume control while using headphones and the sound starts coming out of my speakers until I re-insert my headphones)

However, upgrading to 2.6.22-14-rt sound ceases to work. I haven't figured this one out yet.

On the other hand everything else works well. Wireless, Nvidia drivers, Ethernet, USB.. they all work without downloading any further updates. 

I really wish I could get the 2.6.22-14-rt kernel working as my M-audio Mobile Pre is throwing out massive xruns in Jack regardless of the settings. It never had this problem on 7.04 (granted I was using a different computer when I had Fiesty).

I find it hard to believe that everyone is having so much trouble with their dv6000 series laptops.

*shrugs*

If you have a Toshiba steer clear of Ubuntu period. A buddy of my installed 7.04 on his laptop and he either gets sound, but no usb or ethernet/wireless accelerated graphics, or no sound and all of the previously stated fetures. It's weird.. I told him to do his research before he blew out Vista.. these are known bugs.. but he didn't listen.

-kedaeus

---

### Post by supernerd1991 on 2008-03-02
I am one of those ppl who work in a windows ubuntu cycle. I worked w/ windows for like 2 months, and now am switching back. I use a nc6120, I had to make the decision Kubuntu, Edu, Xu, or just plain Ubuntu. 6.06, 7.04, or 7.10. I ended up choosing 7.10 since it worked  awesome on my custom built system. 
everything was fine until i noticed that my lcd backlight does not turn off when the lid is closed and spent two days straight looking for a solution that i was able to comprehend. I'm not a beginner but im no where near an expert. So I give up and am downgrading to 7.04 or should i say upgrading to 7.04. And I still dont know how to use the infrared on my system. If i had hair i would pull it out. But ubnutu still rox.

---

### Post by mioemi2000 on 2008-03-03
[SIZE="5"]**HP Pavilion dv6000(6232) is fine with Gutsy**[/SIZE]
[http://ubuntuforums.org/showthread.php?t=661550&page=2](http://ubuntuforums.org/showthread.php?t=661550&page=2)

:KS:KS:KS:KS:KS:KS

---

### Post by stickx911 on 2008-03-03
> **Rapidsnow said:**
> Grr I wish I would have seen this before I upgraded. I am having fewer problems than you guys with a dv6000 but I have no sound. My nvidia drivers, compiz, multimedia buttons, and pretty much everything is working fine, but for some reason sound isn't. I had no problem when installing Feisty with anything except the broadcom chipset (which has now crapped out in my motherboard.) Well I will try to fix this, too late (i.e. lazy) to go back almost.

Same here. Everything is going good...except I have NO sound. I don't mind 90% of the time because I use this laptop at school, but it is still annoying.

---

### Post by SurferGTO on 2008-03-03
Im using an HP Pavilion DV2000 with 7.10 and it took me a while but i got everything working absolutely fine with the exception of my wireless. i cant grasp how to use the ndiswrapper albeit the use of several different guides

[http://ubuntuforums.org/showthread.php?p=4436163#post4436163](http://ubuntuforums.org/showthread.php?p=4436163#post4436163)

---

### Post by Pumalite on 2008-03-03
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by GregA on 2008-03-03
As info, for what it's worth, I just installed Gutsy Gibbon 7.10 on a Compaq Presario n2114us laptop.  This is my 3rd PC with Ubuntu, the other being an older HPA250N desktop, and a Lenovo 3000 N100 laptop.   On the HP desktop, and the Lenovo laptop, the installs went el-perfecto!   Everything either working or easy to setup via the Ubuntu wizards, helpers, etc.

On the Compaq Laptop, the live CD worked perfectly.   However, after the install completed, and the system requested a restart (to remove the Live CD), upon restart finish, I was presented with an "ncurses" type black screen with the grub menu options.   I selected the default kernel line, and then the system went to a solid black screen.    I tried several things and did get to a simplified "bash" environment, but being a newbie, didn't know what to input (startx was no-good as x was already running).

Anyway, I thought Gutsy was not going to work out on this laptop, but somehow, just trying key combos, I pressed "ALT+F3" - - and I got my graphical login screen, at the right resolution, and everything is working great.  

SO, in case this procedure may help someone else, here it is for those that want a slightly "non-standard" way to use Gutsy Gibbon on a Compaq Presario 2000 series laptop.

---

### Post by HitRefresh on 2008-03-03
Cool, thanks. 

  I'd like to have a partition for Vista and one for Ubuntu. I'd also like to be able to read/write files between them w/o re-booting. Do the somewhat standard dual-boot procedures cover this already ? Such as this popular one: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") 

Or is there something else I have to do ?

Currently, I have 160GB setup like this after doing a "Shrink Volume" on my C drive:

- C: (which includes Vista) = 96.82GB
- Unallocated space = 40.36GB
- Recovery partition = 11.87GB

I'm not sure what the optimal setup is and how to go about it, as I dont know if the dual-boot instructions cover it. If it does then it isn't obvious, at least to me.

Thanks.

---

### Post by GregA on 2008-03-04
I don't have Vista, but I've been told to use the Vista tools to shrink your hard-drive.  You can then create via a Live Linux CD such as Mepis (which has the "gparted" tool) - another primary partition formatted ext3.  The Ubuntu automated installer should pick up the available partition, and allow for a guided install.   Once installed, yes, you can view and copy your Windows drives, to a USB stick (which normally has a neutral FAT32 filesystem).   I understand the newest Linux distros can read/write to NTFS, but I haven't tried it, because for me these USB sticks just work so well.

---

### Post by HitRefresh on 2008-03-04
Thanks. Ok, I think I understand some more from this post and few others on what I need to do. I want to create 3 partitions from the "unallocated space" derived from doing the Vista "Shrink volume" which is 41GB total. The 3 partitions would be root, /home, and a swap partition. I guess all ext3.

I've seen some screenshots of when installing Gutsy, a screen for "Prepare Disk Space", and then I'd choose "Manual". After that I'm at a loss of what to do and how to create these 3 in a way that I don't lose Vista as well. Also what should the sizes be for them ?

Thanks for any help.

---

### Post by EXCiD3 on 2008-03-04
> **HitRefresh said:**
> Thanks. Ok, I think I understand some more from this post and few others on what I need to do. I want to create 3 partitions from the "unallocated space" derived from doing the Vista "Shrink volume" which is 41GB total. The 3 partitions would be root, /home, and a swap partition. I guess all ext3.

I've seen some screenshots of when installing Gutsy, a screen for "Prepare Disk Space", and then I'd choose "Manual". After that I'm at a loss of what to do and how to create these 3 in a way that I don't lose Vista as well. Also what should the sizes be for them ?

Thanks for any help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

THis shows you how to do manual partitioning with screenshots.

Swap should be equal to or double the size of you ram, and I would recommend at least 7gb for the root partition and the rest for /home.

---

### Post by Pumalite on 2008-03-04
> **HitRefresh said:**
> Cool, thanks. 

  I'd like to have a partition for Vista and one for Ubuntu. I'd also like to be able to read/write files between them w/o re-booting. Do the somewhat standard dual-boot procedures cover this already ? Such as this popular one: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") 

Or is there something else I have to do ?

Currently, I have 160GB setup like this after doing a "Shrink Volume" on my C drive:

- C: (which includes Vista) = 96.82GB
- Unallocated space = 40.36GB
- Recovery partition = 11.87GB

I'm not sure what the optimal setup is and how to go about it, as I dont know if the dual-boot instructions cover it. If it does then it isn't obvious, at least to me.

Thanks.

This is also a good one:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
(/swap has it's own format)

---

### Post by HitRefresh on 2008-03-05
Thanks, Excid3 and Pumalite.  I've read a bunch of how-to's and other material. I guess I like to understand what I'm doing. 

Pumalite - In the instructions you referred me to, in step 8, how do I know which partition has Vista on it ?  What's the indication to tell me "Oh that's Vista, I probably don't want to install on that one!" .  At least not yet :)

---

### Post by Pumalite on 2008-03-05
Format is nrfs. You can also run from Live CD Terminal:
sudo fdisk -lu
(It's usually in sda1)

---

### Post by HitRefresh on 2008-03-08
I wasn't sure since it was not included in those instructions, but how do I create the /home partition ? 

So the instructions say first create swap, then root ("/"), and thats it. Is creating /home the same process as root except using "/home" instead of "/" when creating a new partition ? 

I think that is my last bit of information I need, and I will begin install next. Thanks!

---

### Post by EXCiD3 on 2008-03-08
Yes you are exactly right HitRefresh. Just make sure that the mount point is /home. You can make this partition as large as you want and then have it remounted for ANY other installation of linux as /home and keep all your settings ;) Its really an amazing thing after all those backups of windows!

---

### Post by s_raghu20 on 2008-03-09
Hi Guys,

I dont feel like cross posting, but the problems on HP 6710b seem to have all been fixed with the continuous work put in by the Ubuntu team.

[Check this page]("http://techraghav.blogspot.com/2008/03/improved-gutsy-for-6710b.html")

hope it helps users of HP 6710b

cheers
raghav..

---

### Post by Llewxam on 2008-03-09
hey all.

i seem to be having the same front headphone jack problem. is there an alsa codec i have missing here i need to install or something?

---

### Post by Pumalite on 2008-03-09
What happens when you type:
alsamixer
In your Terminal?

---

### Post by Llewxam on 2008-03-09
i only get the master and pcm options displayed. labels read:

Card: HDA Nvidia 
Chip: Conexant ID 5051
then just the options of which device. none show a headset or headphone option. :confused:

---

### Post by Pumalite on 2008-03-09
Well, your card is recognized by the kernel, the module is loaded. You might be right. There is an alsa-driver 16. I couldn't get the link. I'll get back to you.

---

### Post by Llewxam on 2008-03-09
really appreciated.

---

### Post by Pumalite on 2008-03-09
Try this:
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)

---

### Post by Llewxam on 2008-03-09
k... mind refreshing my memory on how to compile and install it? haven't done that in a while.

---

### Post by Pumalite on 2008-03-09
Make sure you have build-essential:
sudo aptitude install build-essential
You might want to try this:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)
tar xjf alsa-driver-1.0.16.tar.bz2
tar xjf alsa-lib-1.0.16.tar.bz2
tar xjf alsa-utils-1.0.16.tar.bz2
cd alsa-driver-1.0.16
./configure --with-cards=hda-intel
make
sudo make install
cd ../alsa-lib-1.0.16
./configure
make
sudo make install
cd ../alsa-utils-1.016
./configure
make
sudo make install

added to the end of /etc/modprobe.d/alsa-base:
Code:

options snd-hda-intel model=auto

---

### Post by Llewxam on 2008-03-09
> added to the end of /etc/modprobe.d/alsa-base:
Code:

options snd-hda-intel model=auto

that last step kinda lost me... how do i add that?

---

### Post by Pumalite on 2008-03-09
gksudo gedit /etc/modprobe.d/alsa-base

---

### Post by Llewxam on 2008-03-09
well all done. need to restart or something? o.0 'cause i still don't see a hedphone option on alsa mixer.

---

### Post by Pumalite on 2008-03-09
Reboot and we'll see.

---

### Post by Llewxam on 2008-03-09
awesome. works. hehe was impatient. thanks man! you win a popcorn :popcorn:

...now to solve the opera and flash/video streaming issue -.-'

---

### Post by Pumalite on 2008-03-09
What do you mean? Give me a formal 'Thanks' then. 
You are welcome. Good luck.

---

### Post by Llewxam on 2008-03-09
hehe sorry it was just one of two issues and you actually helped 2 people, a friend and me. big huge formal thanks on behalf of the both of us. 
anyway the last and only issue i got is with opera and flash. i can't view youtube vids or any other website with streaming videos. got all the gstreamer codecs installed and it works perfectly on firefox and totem and vlc play all imaginable codecs. to value redundancy, all but opera.

---

### Post by Pumalite on 2008-03-09
Sorry. Can't help you with Opera. Some Opera fan will show up.

---

### Post by Llewxam on 2008-03-09
it's ok. eventually it'll be fixed. again really appreciate the help.

---

### Post by bluefox83 on 2008-03-09
i have the exact same sound card and i cannot get my headphones to work. I know it's possible because it worked once before, but i was stupid and tried to install the 63 bit version of gutsy and after discovering it doesn't work i came back to the 32 bit version, but alas, now i cannot get my speakers to mute when i put the headphones in, and i cannot find the jack sensor option anywhere.

---

### Post by HitRefresh on 2008-03-10
> **EXCiD3 said:**
> Yes you are exactly right HitRefresh. Just make sure that the mount point is /home. You can make this partition as large as you want and then have it remounted for ANY other installation of linux as /home and keep all your settings ;) Its really an amazing thing after all those backups of windows!


Ok, I'm giving it a try to install Gutsy on my HP DV6704nr. I select "Start or Install Ubuntu" and after a bunch of scrolling messages with OK's ... I get a dialog prompt pop-up saying "Could not find or detect screen or graphics card"... tried "Configure" option to select NVIDIA 7 series, as it is close to mine, but no workie, tried "Continue" but again no workie. I'm not sure what to do next, any help would be appreciated.

---

### Post by EXCiD3 on 2008-03-10
> **HitRefresh said:**
> Ok, I'm giving it a try to install Gutsy on my HP DV6704nr. I select "Start or Install Ubuntu" and after a bunch of scrolling messages with OK's ... I get a dialog prompt pop-up saying "Could not find or detect screen or graphics card"... tried "Configure" option to select NVIDIA 7 series, as it is close to mine, but no workie, tried "Continue" but again no workie. I'm not sure what to do next, any help would be appreciated.

Hmm, i have very little experience with Gutsy as I hate it with a passion. Feisty and Hardy are much better versions of ubuntu. The only thing i can think of is to try using the vesa or nv driver to get you into your desktop environment and then install the nvidia drivers. If that isnt going to work i would recommend using the alternate cd. Thats about all the advice i can give you on this. Maybe someone else has a better idea.

---

### Post by azbobs on 2008-03-11
Hello,

Just wanted to let everyone know that I to have a HP EZ345AV  HP PAVILION NOTEBOOK PC DV9000 laptop and my loaded just fine. I am running the nvidia 7600 and a intel 64 bit base. Just thought I would post and let everyone know. I was almost going to load the 7.04 since everyone is saying that there are the issues and more downloads available. Will try this versions for awhile and see if I start to have any  issues. I have this running as a dual boot with Vista ultimate. I am not using the grub loader. I am using the OS bios to boot from.

 I removed my drives sata drives before loading and thats what gave me issues. I finished the load of 7.10 and it worked great.The put the drives back in and noticed the primary drive the plastic 22 pin connector not fitting snug. I restarted and it said it could not find the operating system  I thought it must be the connector. I took the one of the scondary on the primary and the operating system worked fine. The bad thing is HP would not warranty the part and none of the local computer stores had it said I would have to buy this from HP. Cost me $50 to buy it, you have to buy the hard drive mounting kit which I did'nt need the mounting bracket, 4 screws and the 22 pin connector. That's was the only bad thing that happened to me. 

****Cheers,
azbobs

---

### Post by Dreamer Zero on 2008-03-12
i have a dv6704nr, 7.10 covered my laptop in fail, when i got the drivers for my Nvidia 7150M go installed(which was not a easy task for a noob), and started getting everything else setup, i started having intermittent network issues, couldn't get wireless to work (ar5007eg) and the wired connection would work at random most of the time getting a invaild IP address.

after trying a few other distros, i tried 8.04 beta 4 and everything got a lot easier, it installed the Nvidia drivers from the restricted hardware window without any issues, still having some issues with the wireless but it is working 50% of the time, wired connection works all the time, other than making my own stupid mistakes, 8.04 beta 6 (i reinstalled) is stable on my HP.

side note:the volume and mute buttons work, but the other media buttons do not work, but thats not an issue for me.

---

### Post by Helix. on 2008-03-12
For anyone with the fuzzy screen problem under ATI IGP 34x cards: [http://ubuntuforums.org/showthread.php?t=718000](http://ubuntuforums.org/showthread.php?t=718000)

---

### Post by tchazzard on 2008-03-13
Hello,

I installed Ubuntu 6.10 on an HP dc5220us laptop a week ago and immediately upgraded all the way to 7.10. The system ran fine until last evening. My wife mentioned that it took forever to shutdown when she was done using it. This morning it booted up to the login screen fine, but once you login, the mouse ceases to work and the system is otherwise unresponsive to the keyboard.

Can someone recommend the most appropriate version of Ubuntu for this model HP?

This model DV5000 uses the Intel Core Duo T2050 and the Intel Graphics Media Accelerator 950 for video.

TIA

---

### Post by magaltavor on 2008-03-14
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87) 

enjoy

---

### Post by Llewxam on 2008-03-14
well i am having a little issue with the ricoh media card reader. it's recognized when running lspci, i tried reading and following the many how to's around the forums, but nothing seems to resolve the issue that when i insert a card it won't load. the only type of card i'm trying to use are the pro duo (psp memory sticks) but i get nothing. :confused:
edit: this is what shows up with lspci: 
```
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by Pyro_Killer on 2008-03-14
I am having a problem on my dv9000 (dv9041ea) when I installed ubuntu on an usb hdd, I used the alternative x86 7.04, and it installed nicely, then i tried to boot it, but it didn't work, so I added the noapic, and it got to the screen with the orange bar, and it completed it, but then the screen whent black with side light, and the computer still glowing blue, but the usb hdd stopped jobing/orange light stopped.
Any suggestion?

---

### Post by Applegeek on 2008-03-17
My dv2470se didn't install at all with Gutsy - got hung up in "Low Graphics Mode" and crashed right after that confirmation screen.

Tried Hardy, and it almost all worked except I can't get broadcom wireless network to run at all...Everything else, surprisingly, seems to work.

---

### Post by sir4taye on 2008-03-17
Try booting from the live cd with boot: live noapic nolapic and see if your conflicts aren't eradicated. My Compaq f730us (nvidia chipset with onboard nvidia 6200 video also amd64x2) screems with the gutsy. The only thing I had to fiddle with is the broadcom through ndiswrapper. the proprietary broadcom wouldn't work for me. This apic lapic has to do with the way interupts are handled and may streamline the interoperability of your hardware.

---

### Post by j4ck455 on 2008-03-20
> **s57nev said:**
> What about nx7300. I happen to own one and I use it for work. That's why i can't afford using broken wireless or something like that. Anyone with same laptop ? 7.04 works like a charm. It uses ipw3945 module for wireless and has Intel Mobile 945GM graphic. 

Is it safe to upgrade yet ?Everything - except the microphone, works flawlessly on my nx7300, in 7.10, although it might just be the mic I'm using.

EDIT: I tested the headset's mic on another PC, and it is working there, I'm forced to conclude that the mic or sound levels are not working properly on my nx7300, how can I debug this?

---

### Post by mrfajita on 2008-03-20
on my compaq M2000 7.10 Gutsy runs with no problems at all...

---

### Post by iketheengineer on 2008-03-20
I have an hp dv9000 laptop with vista home premium, 2.2ghz amd dualcore,2gb ram,120gn,and 80gb hard drives. I had, I believe, fiesty on the 80gb hard drive. I upgraded to 7.1 online and couldn't make it work. I  have read on your forum that 7.1 isn't for hp9000 laptops. fiesty is better or at least it is suppose to bel. when I had fiesty on the laptop it would freeze up a lot. so much that I stopped using it altogether. I think i would like to go back to fiesty but before i do i would like to find a solution to the freeze up problem. Oh by the way I have nvidia geforce go 6150 graphics.  Any help that you can give me I will appreciate. I don't know about any other linux os's. I don't know if there is any other that would work better on my laptop or not. thank you in advance. one more thing, I am new to linux. been wanting to try it for a long time, but so far am disappointed.

---

### Post by sir4taye on 2008-03-21
Just wait for the 8.04 hardy heron to launch in early april. There are some things you could do though. When you start the live install cd the first screen that is usable has a countd down from thirty for auto start but the last option gets you a line to add boot paramiters. I've found that the apic and lapic functions give me freeze issues (only on select machines). try this boot: live noapic nolapic and see that the fresh install should scream high speed low maintenance.

---

### Post by TheForkOfJustice on 2008-03-21
64-bit Gutsy here on a Presario v2000 laptop.

Everything here works well except the usplash which doesn't seem to wish to appear on my widescreen and just seems to extend my boot time.

Anyone know where I can get a replacement if the default version doesn't have the correct size, thus causing usplash to fail on my system?  Is there another workaround?

---

### Post by MC_LA on 2008-03-24
on an IBM thinkpad, Gutsy is very** flacky**.  Things that don't involve hardware work well, everythings else is a crap shoot.  Dual monitors, webcams, USB devices all don't like Gutsy.  

This is my first experience with Ubuntu so I thought it was just that Ubuntu wasn't any good.  I was getting ready to switch back to MS until I heard there is hope in a new release.

---

### Post by Wobedraggled on 2008-03-24
Gutsy had problems on my nx9420, but they all got smoothed out.

Hardy is flawless so far.

---

### Post by navaburo on 2008-03-24
Gutsy works fine on my HP nw8440 laptop, with some minor exceptions:

1) Packet capture doesn't work with the stock ipw3945 driver.
2) Framebuffer terminal doesn't work.
3) Software suspend doesn't work (although I didn't expect it to).

If you have an nw8440, I say go for Gutsy.

---

### Post by EXCiD3 on 2008-03-24
> **navaburo said:**
> 1) Packet capture doesn't work with the stock ipw3945 driver.

You need the driver that supports packet injection if you plan on doing things like that such as cracking wifi. A distro such as backtrack 3 or wifiway is much better for these types of things anyways. After a little bit of googling im sure you can find out how to get the modified drivers. ;)

---

### Post by j4ck455 on 2008-03-24
> **j4ck455 said:**
> Everything - except the microphone, works flawlessly on my nx7300, in 7.10, although it might just be the mic I'm using.UPDATE:> **j4ck455 said:**
> EDIT: I have **updated the BIOS on my nx7300** from version F.0A to F.0B and then **to F.0C**, and the mic problem has disappeared, I did test after applying F.0B and the mic was working at that point. However, there is some doubt in my mind because I reset BIOS F.0A settings back to the defaults just before applying F.0B, I will see what happens after I fiddle with the BIOS settings to get them back to what they were.I have not tried Bluetooth nor an external monitor yet.

---

### Post by lemcott on 2008-03-24
actually, gutsy works fine on my hp dv9420us.
i had some problems installing (had to "noapic" before installation)

surprisingly, the thing you said is the only thing that would work, doesnt! i couldnt get my laptop to pic up wi-fi on ubuntu, but the Ethernet hook up works fine.

---

### Post by j4ck455 on 2008-03-24
Probably useless anecdotal info: I also initially struggled to get wifi going with my nx7300, but that was with SSID Broadcast disabled on my WRT54GL, after enabling SSID broadcast, I was able to get wifi going without a problem, and it has been working ever since I disabled SSID Broadcast again.

---

### Post by gxrrett on 2008-03-25
Should the new release of 8.04 be ok with an HP? I have a DV9000, and I'm looking to switch over to Ubuntu from Vista. Has anyone tried the Beta?

---

### Post by EXCiD3 on 2008-03-25
> **gxrrett said:**
> Should the new release of 8.04 be ok with an HP? I have a DV9000, and I'm looking to switch over to Ubuntu from Vista. Has anyone tried the Beta?
Ive been using it since Alpha 3 and have not had any major problems. Currently I am up-to-date with the beta and am only experiencing one major problem. My Intel HDA audio has stopped functioning. I havent done a fresh install with the beta (just kept updating Alpha 3) so this might be a cause of the problem. Sure wont hurt to try it! Lots of people have said its already better than Gutsy! :lolflag:

---

### Post by sir4taye on 2008-03-25
I did a clean install of the beta 8.04 from the 7.10. I had struggled to find a wifi workaround for 7.10 for a few weeks. Then I found the ndiswrapper with a blacklisting of sorts to get rid of conflicts. I have the 7.10 solution here:

http://ubuntuforums.org/showthread.php?t=697731&highlight=sir4taye&page=2

Now that I've done a fresh install of the 8.04 beta I was dismayed to find that my old 7.10 solution didn't work. But the glorious thing about this community driven movement is that it only took a few hours to find a solution that worked. And so... The Hardy 8.04 HP/Compaq/Broadcom solution is here:

1.) Remove the b43-fwcutter package if you have it installed, and get an ethernet cable ready. Connect the cable to your wireless router, and run

Code:
sudo apt-get ndiswrapper-common

sudo apt-get ndiswrapper-utils-1.9

sudo aptitude remove bcm43xx-fwcutter

sudo aptitude remove b43-fwcutter


then run this:

Code:

sudo gedit /etc/init.d/wirelessfix.sh

and paste this Quote into the textfile that opens:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

save and Close the textfile

Next, run this:

Code:

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

sudo update-rc.d wirelessfix.sh defaults

Restart and enjoy your wireless!

it may be required to run this in terminal one time and then restart again:

sudo modprobe -r b44
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44

---

### Post by teeleef on 2008-03-25
sir4taye,  thanks for you post.  I followed your instructions but no joy I'm afraid.

The wireless icon is searching the networks and my signal from the router is 95%.

My system is the dv9500 series.  No problems with 7.10 either.

I await further suggestions.


teeleef

---

### Post by gxrrett on 2008-03-25
All I have is the Gutsy cd. Where can I get Feisty at? Sorry to steer this off topic, but can someone shoot me a thread to dual boot Vista and Ubuntu? I'm still hesitant about leaving Vista all together. :? Thanks.

---

### Post by didli on 2008-03-25
Hi you all !
I own a HP dv9051ea , and was using Ubuntu Gutsy for some months. Some times ago I've posted right here, and was saying that despite minor annoyances, Gutsy was running fine ... until 2 weeks ago. This laptop seems totally KO for me right now : one day, after an nvidia driver update, the LCD panel begin to show glitches, horizontal red stripes, win$ & gutsy couldn't boot anymore and so on, more and more troubles ...  
It happens no matter what I'm trying, running bios, running win$, running gutsy ... 
The very strange part is that sometimes, I am able to boot win$ or gutsy when in graphic security mode (sorry don't know the english name of it), and after a few days, was even able to reinstall gutsy with 3d acceleration until ... it break all over again ...
'Seems to me the nvidia express card is down, but can't really tell, for I was able to use it once more before it broke.
Now I will not say a word against Gutsy, as I can't stop thinking that HP laptops are just plain crap...

---

### Post by EXCiD3 on 2008-03-25
> **didli said:**
> Hi you all !
I own a HP dv9051ea , and was using Ubuntu Gutsy for some months. Some times ago I've posted right here, and was saying that despite minor annoyances, Gutsy was running fine ... until 2 weeks ago. This laptop seems totally KO for me right now : one day, after an nvidia driver update, the LCD panel begin to show glitches, horizontal red stripes, win$ & gutsy couldn't boot anymore and so on, more and more troubles ...  
It happens no matter what I'm trying, running bios, running win$, running gutsy ... 
The very strange part is that sometimes, I am able to boot win$ or gutsy when in graphic security mode (sorry don't know the english name of it), and after a few days, was even able to reinstall gutsy with 3d acceleration until ... it break all over again ...
'Seems to me the nvidia express card is down, but can't really tell, for I was able to use it once more before it broke.
Now I will not say a word against Gutsy, as I can't stop thinking that HP laptops are just plain crap...

What video card do you have?

---

### Post by didli on 2008-03-25
Geforce Go7600 (pcie). Why ? Did you know something about this ?

---

### Post by EXCiD3 on 2008-03-25
> **didli said:**
> Geforce Go7600 (pcie). Why ? Did you know something about this ?

Was just wondering, the Nvidia 6150 seems to have lots of problems for some reason. How did you install the driver? Compile it, Envy or Restricted drivers manager?

---

### Post by didli on 2008-03-25
Restricted manger at first, then envy. Well I don't think it is a driver problem (I've tried a LOT of things with different fresh Ubuntu install) but i've heard that there are HP laptops which cannot use another nvidia driver version than the one installed with xp (DV9051EA came with xp media center). Don't even really know if it's true ...

---

### Post by EXCiD3 on 2008-03-25
Well for example my laptop Dv9000t nvidia 7600go (purchased christmas of 2006) must use the official HP drivers. downloading the drivers for Windows must be from HP as the drivers from Nvidia do not work. this might be a cause for all the difficulty people are experiencing, however my drivers have worked great, other than some VSync problems with Compiz that i cant fix.

Do you experience problems with the drivers in windows at all? It could very well be the custom graphics cards specifically from HP taht is causing your problem with Ubuntu. If you know the version of the driver you had that was working good until the update you could always download the old version and that instead of the most up-to-date driver.

---

### Post by AnoopKeni on 2008-04-09
I ran into big trouble with 7.10. That too even before installing, I was using Live CD and my Vista partition NTFS and FAT for merged. Check my post [http://ubuntuforums.org/showthread.php?p=4682646#post4682646]("http://ubuntuforums.org/showthread.php?p=4682646#post4682646") 

I am very disappointed with this release.

By the way I have a HP Pavilion dv9500tu Vista home premium laptop.

---

### Post by Lazy-buntu on 2008-04-09
I've got an HP Pavilion dv6308, I just started dual booting Gutsy on monday, and I have yet to get the wireless working. I started a thread: [http://ubuntuforums.org/showthread.php?t=748882&highlight=dual+boot+wireless](http://ubuntuforums.org/showthread.php?t=748882&highlight=dual+boot+wireless)

I don't know if this is an old thread or not, but what should I do? I haven't even started with the nvidia 6150 problems I know I will have.

Do I:

1. stick with gutsy
2. burn a feisty live cd and format the gutsy partition --> dual boot with feisty instead of with gutsy
3. or hardy heron beta

Vista hasn't given me any real problems, but it's a resource hog. I'm pretty new to linux, so I want a stable, effecient distro to dual boot with vista.

What features does feisty lack that gutsy has (if any)?

---

### Post by Pumalite on 2008-04-09
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

### Post by Man Man on 2008-04-10
HP dv2810us.  Never used linux before, and have been having massive issues with Gutsy since I installed it a few days ago.  The wireless does not work (and it feels like I've used every tutorial out there), there is no sound, and I have not even begun to deal with the Nvidia issue.  From the responses in this thread I get the impression that Hardy is more HP-friendly.  However, should I go with the 64 or the 32 bit version for my AMD Turion 64 X2 TL-60?  For some reason I've always had the impression that the 32 bit Gutsy was more stable then the 64 bit, so is this also the case with Hardy?

---

### Post by Pumalite on 2008-04-11
Both Hardy are great. Updates flawless so far. But, to your problem, maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by froot on 2008-04-11
Why does everyone have problems with their PCs? I have been running gutsy (7.10) since it was released and have had no mechanical breakdowns. I've got an Intel wireless card, working fine. My multimedia buttons work, as does my Nvidia graphics card. I've got a dv6000ea (Intel) series model.

---

### Post by EXCiD3 on 2008-04-11
> **froot said:**
> Why does everyone have problems with their PCs? I have been running gutsy (7.10) since it was released and have had no mechanical breakdowns. I've got an Intel wireless card, working fine. My multimedia buttons work, as does my Nvidia graphics card. I've got a dv6000ea (Intel) series model.

One of the big reasons people have trouble wtih their laptops is that the hardware, specifically the wireless and video cards are either custom made for HP or the hardware manufacturer does not officially support Linux. For example the nvidia cards included in most HP laptops must run the HP version of the driver (in windows). My 7600go requires me to get the driver from HP and I cannot install the official Nvidia driver (windows one).

---

### Post by cjsteele on 2008-07-10
BAH!  I've been using the nx9420 on 7.10 and upgraded without any significant issues to 8.04.  Its a matter of knowing how to get the thing to do what it needs to do.  That said, I'm not the kind of guy to say that without having already put my money where my mouth is... I've got a wiki page documenting what works and what doesn't work, and what you need to do to get it to work at [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420)

---

### Post by EXCiD3 on 2008-07-11
Thanks alot for taking the time to document everything, thats what helps new users the most! :D i sadly have not even gotten around to making a wiki page for mine, but i have written a PDF tutorial over the basics.

---

