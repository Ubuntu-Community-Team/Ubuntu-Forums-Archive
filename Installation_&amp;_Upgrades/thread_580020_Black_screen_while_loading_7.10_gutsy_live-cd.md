---
title: "Black screen while loading 7.10 gutsy live-cd"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Kevf on 2007-10-18
I never had any install-probs with 6.06 or 7.04 (dual boot with xp)

But with 7.10  after I chose install from te menu my screen turns black and goes into standby modus.......

2.6 ghz
512 mb ram
ati radeon xpress 200 ( I know, I know)

and a bit frustrated

---

### Post by mattpker on 2007-10-18
Father had same issue, try going to more settings and running in other video modes. This is usually becuase it can't find or use the video drivers yet.

---

### Post by Skelet0n on 2007-10-18
got the same problem tried every option on the live cd, i really need help!

---

### Post by Kevf on 2007-10-18
But that's just stupid.... a newer version of Ubuntu doesn't work, where older versions did install properly...

---

### Post by Stemp on 2007-10-18
Switch to a console mode (ctrl+alt+F1), login and type this command :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure your X server.

Then back to to X (ctrl+alt+F7) and restart X (ctrl+alt+backspace)

---

### Post by strawman on 2007-10-18
read the release notes for gutsy, down at the bottom; it's to do with ati

---

### Post by ericesque on 2007-10-18
I had the same problem (ATI graphics on notebook) I just waited 5 or 6 min-- until I was pretty sure that the system would be to the desktop then hit the space bar or clicked the mouse.  One of which worked and everything was fine. 

I suppose a good way to know when you would be at the desktop is when the ROM access stopped for a while-- means nothing is loading.  

Still really odd that it does this.

---

### Post by Weezer on 2007-10-18
I'm having the same exact problem with my Lenovo T61p (nVidia card). When booting the disk normally to install, the screen simply goes black and the computer eventually goes to sleep. When booting in safe-graphics mode, an error message comes up telling me the display server has been shut down six times in 90 seconds. "It is likely that something bad is going on" (thanks for that vague message ;)).

I'm going to try running the commands posted above, but I'm going to go ahead and ask for advice on the chance that they don't help my situation. I would download 7.04 to make sure it is functional on this computer, as it was on my desktop, but it has been removed from the download page.

Thanks

---

### Post by NiklasC on 2007-10-18
I'm having the same problem too. Got an nVidia geforce 8500 GT, AMD Athlon64x2. Downloaded the release for AMD x64.

When booting the live cd, the screen goes blank and the computer seems to go to sleep after a few seconds, after selecting start/install in the menu.

Very annoying.

---

### Post by serfcx on 2007-10-18
Same thing here with Geforce 440.
Hitting reset on screen will get back display

---

### Post by Pnevma on 2007-10-18
Yep, same thing here.

Q6600 Core 2 Quad
IP35 Pro
XFX nVidia 8600GT

---

### Post by Weezer on 2007-10-18
So I tried running the lines to reconfigure xserver, but they didn't work. I can't even ctrl+alt+F1 to enter commands unless I load it in safe graphics mode and wait for it to fail six times.


I caught, "Failed to allocate mem resource #6:20000@f0000000 for 0000:0 ..." as the first line as it boots into Linux, but I thought this may just be a result of the boot disk rather than an actual partition.

It seems to fail whenever trying to start X server, as that's where it freezes up every time.

---

### Post by kurtfhouse on 2007-10-18
I get the same problem as well

I have an Nvidia 7600GS

Infact I have had the same problem with Tribes 3 and 4 aswell and had hoped this would be sorted by now. 

I did try installing 7.04 and upgrading to Gutsy which worked fine but then it was way too unstable so I gave up on it until final release.

It does seem stupid that an upgrade doesn't work and the old version boots fine :)

---

### Post by bliffle on 2007-10-18
When my gutsy torrent dl finishes in a few minutes i'll try the livecd on my new t60.

---

### Post by gahp on 2007-10-18
Same thing with AMD Turion 64 X2 TL-60, nVidia GeForce Go 6150.

And just delelted the 7.04 .iso:(

---

### Post by NiklasC on 2007-10-18
Well, if anyone wanna get the 7.04 ISO, it can be found here: 

[http://releases.ubuntu.com/feisty/]("http://releases.ubuntu.com/feisty/")

---

### Post by exploder on 2007-10-18
Bug reports were filed regarding this issue. I can not believe Gutsy final was released with such a major known problem! There will be massive posts about this!

---

### Post by newpants2003 on 2007-10-18
same here.
ATI xpress 1100  (200m)

---

### Post by Kevf on 2007-10-18
I got it working....!

I tried to install 7.10 for the fourth time and again in safe mode....this time everything worked fine! Dunno how I did it but at least it's installed :popcorn:

---

### Post by cx23 on 2007-10-18
ditto

C2D 6600 / 2RAM / P5B-E / GF8600GT + DFP SyncMaster 204B

The LiveCD starts without any problems - I can change language F2 , read F1 help. But after selecting and launching "Install" or "Install in save mode" LiveCD menu items my monitor just turns off

---

### Post by Falcorian on 2007-10-18
Same problem with an nVidia 8800 GTS 640, E6850, and some mobo who's name I don't remember right now... ;)

---

### Post by finnen on 2007-10-18
Same problem here:

HP Pavillion dv6305us
Amd Turion 64 X2 Mobile, 1.6 GHz
512 MB Ram
GeForce Go 6150

---

### Post by Falcorian on 2007-10-18
Further update:

Nothing I did would get a screen. No terminal, no adjustment of the monitor, no waiting for 5 minutes. Neither normal nor safemood worked.

---

### Post by Weezer on 2007-10-18
So is it a safe bet that if the live CD won't boot, that it's not a great idea to load the "Alternative" CD and directly install Ubuntu?

---

### Post by thewolf32 on 2007-10-18
EXACT same problem here! Help!!!!! TRibe 5 worked just fine, but the final release doesn't, after looading it just turns to stand-by mode. Help!!!!

EDIT: I think it's something with the new xorg 7.3, because this problem appeared when the beta release was released.

---

### Post by Bleak Outlook on 2007-10-18
bugger when i saw 3 pages of comments i was  "cool must have been sorted by now"
but alas no

i have the same issue trying to run the live cd 
i get a helpfull hint telling me optimal setting is 1280x1024 60hz
but trying that dont work

im running a 
dell dimension 9200
c2d E6400
radeon x1300 pro <-- the card is pants i know but with various jiggery pokery i was able run all the eye candy and such with the last edition 

it does seem strange that the latest offering would stumble at such an early point
when feisty fawn was a joy to set up (not counting the 2 days jiggery pokery with beryl)

oh well i guess i will return to this thread again(quite possibly every ten mins or so)

---

### Post by Falcorian on 2007-10-18
I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)

---

### Post by finnen on 2007-10-18
I got it to work!
I added this to the boot options (press F6 in the meny)

noapic irqpoll noirqdebug

Now I just have to get my broadcom wireless to work without any wired network avaiable :-k

edit: this was in safe mode

---

### Post by thewolf32 on 2007-10-18
Thanks, but it doesn't help me, i'm still stuck when starting the X. Neither methods (falcorian and finnen) helps.

---

### Post by Bleak Outlook on 2007-10-18
Falcorian & finnen
i have tried both your suggestions but still no joy

Falcorian i get alot more text your way and it looked hopeful 
but im guessing it was just showing me what it would normally do behind the splash screen?

i get to the line of text saying
running local boot scipts(/etc/rc.local)                                       [ok]
then the screen flashes i get told the optimal resolution is 1280 x 1024 60hz
then it just stops

it must something to do with the monitor/vga card but im a techno-tard so i guess im screwed till somebody spells it out for me

to top things off my printer has now run out of black ink so im gunna have to go all old skool and write stuff down..... 
just hope i can remember how to write stuff (its the pointy end that makes the text, right?)

---

### Post by hhpeter on 2007-10-18
this helped me add hit f6 and add :

noapic acpi=noirq nolapic
 
I have a hp desktop with atixpress200

---

### Post by jey18 on 2007-10-18
> **Falcorian said:**
> I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)


Thank you so much for this.

For those of you who do use this, I did this, it should show the desktop for a moment after a whole bunch of text (unquiet install) and then it will go black for a few moments. I thought I was screwed again but I moved my mouse and VIOLA I had it to the desktop and I was ready to install directly to the drive.

---

### Post by thewolf32 on 2007-10-18
> **hhpeter said:**
> this helped me add hit f6 and add :

noapic acpi=noirq nolapic
 
I have a hp desktop with atixpress200


Tried this, doesn't work for me.

---

### Post by Bleak Outlook on 2007-10-18
> **hhpeter said:**
> this helped me add hit f6 and add :

noapic acpi=noirq nolapic
 
I have a hp desktop with atixpress200

this got me to the same place
running local boot scripts (/ect/rc.local)                                 [ok]
screen flash - stuck

but with the added benefit of not recognizing any of my usb ports so no keyboard to exit out  :lolflag:

to all those that have got it to work though im pleased for you and not in the least bit bitter :)

to be honest it looks like im pulling another all nighter thanks yet again to the wonder that is linux

take care all
see you in another 10 mins lol

---

### Post by Falcorian on 2007-10-18
> **Bleak Outlook said:**
> Falcorian & finnen
i have tried both your suggestions but still no joy

Falcorian i get alot more text your way and it looked hopeful 
but im guessing it was just showing me what it would normally do behind the splash screen?

Right you are. ;) That's what removing the 'quite' option does...

However, I don't have a clue about fixing your problem, sorry. :(

---

### Post by Commander 598 on 2007-10-18
I believe I have discovered the fix for this issue. I first noticed it with the 7.10RC. After the loading screen, it went straight to a screen telling me something along the lines of "Analog: Can't Display This Mode" or somesuch. Can't remember the specifics but it happened in an identical fashion to all complaints here. Anyway, it sort of clued me into what it might be. 

Originally, I just shrugged my shoulders thinking it was a bad image and would be fixed when 7.10 was officially released. It wasn't. So, I disconnected the old VGA cables from my monitor and finally hooked up the DVI cables that I had meant to do six months ago. Problem solved, boots perfectly.

Hope this helped...

---

### Post by Bleak Outlook on 2007-10-18
> **Falcorian said:**
> Right you are. ;) That's what removing the 'quite' option does...

However, I don't have a clue about fixing your problem, sorry. :(

no worries mate
thanks for trying and im pleased you got it sorted for you and the others

i like linux, i like a challenge just didnt expect it to happen so soon 	:rolleyes:

---

### Post by cx23 on 2007-10-18
> **cx23 said:**
> ditto

C2D 6600 / 2RAM / P5B-E / GF8600GT + DFP SyncMaster 204B

The LiveCD starts without any problems - I can change language F2 , read F1 help. But after selecting and launching "Install" or "Install in safe mode" LiveCD menu items my monitor just turns off

OK. I managed to start the LiveCD amd64.

1) Selected Install safe video mode
2) F6 - for more options and
3) Edited the boot string - deleted xforcevesa and splash
4) Booted into the LiveCD system

---

### Post by yowshi on 2007-10-18
> **Weezer said:**
> So is it a safe bet that if the live CD won't boot, that it's not a great idea to load the "Alternative" CD and directly install Ubuntu?

actually thats not necessarily true. the feisty 64bit livecd never worked for me. but i managed to install feisty using the alternate CD and it worked perfectly. with the exception of the hassle of getting the nvidia drivers to work

---

### Post by Falcorian on 2007-10-18
> **Commander 598 said:**
> I believe I have discovered the fix for this issue. I first noticed it with the 7.10RC. After the loading screen, it went straight to a screen telling me something along the lines of "Analog: Can't Display This Mode" or somesuch. Can't remember the specifics but it happened in an identical fashion to all complaints here. Anyway, it sort of clued me into what it might be. 

Originally, I just shrugged my shoulders thinking it was a bad image and would be fixed when 7.10 was officially released. It wasn't. So, I disconnected the old VGA cables from my monitor and finally hooked up the DVI cables that I had meant to do six months ago. Problem solved, boots perfectly.

Hope this helped...

I used DVI and it happened to me. :(

---

### Post by imcompa on 2007-10-19
> **Falcorian said:**
> I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)

This worked for me

Nvidia 8800gts
quad core Q6600

but then it stops and i hit enter and it says

(initramfs) and I can't do anything.

3rd times a charm. I got it to work pretty ubuntu sounds and everything.

I had to redo my partition and now it no longer works :(

---

### Post by Weezer on 2007-10-19
I don't suppose anyone has tried a fresh install on a Thinkpad laptop and overcome these problems?

---

### Post by haylocki on 2007-10-19
Hi, 

I have a Thinkpad T21 with a 1400x1050 resolution screen
I was able to boot my live cd using safe graphics mode, but the highest resolution available was 1280x1024.

When the installation to my hard drive finished and I rebooted I had the black screen problem.
Booting in recovery mode and typing "startx" produced a message saying not to use root, but the desktop loaded fine.

Exit from the desktop and, Bam! black screen and hard lockup.

Cured the problem by booting in recovery mode, then

nano -w /etc/X11/xorg.conf
 
and changed this section to this :

Section "Device"
	Identifier	"Generic Video Card"
#	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Driver "savage"
	Option "SWCursor" "on"
	Option "ShadowStatus" "on"
	Option "DMAMode" "Vertex"
	Option "DmaType" "PCI"
	Option "BusType" "PCI"
EndSection

Now works fine. Maybe you guys want to try editing the file and changing the driver to whatever chipset your graphics card is using. All the other options are just something to do with making it work on the T21.

And me too for having a working out of the box desktop in Feisty.

Has anyone done a dmesg from the command line ?

dmesg |grep agp

mine looks like this :

[   20.340000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.532000] agpgart: Detected an Intel 440BX Chipset.
[   20.536000] agpgart: AGP aperture is 64M @ 0xf8000000

Why does the kernel think I have a 440BX Chipset :confused:

Cheers Ian

---

### Post by NiklasC on 2007-10-19
Jeez, can't believe they released it with this very obvious bug. Someone in the beta-test must have had these issues, right?

And to top things of, Vista won´t let me shrink the NTFS partition to allow space for ubuntu. M$ puts a lot of the system files at the end of the partition, which prevents shrinking. So why the heck to they ship Vista with a tool for shrinking the partition?! I did find a workaround, but that includes intentionally screwing the Vista partition and then repairing it, which seems a bit risky. Worked like a charm with XP and Ubuntu 6.10, but now both the newer Windows and Ubuntu are a pain in the ***. :(

---

### Post by gregbzh on 2007-10-19
Same problem with nvidia 6200.  I can't even do a clean install.  I'd just moved back from PCLinuxOS all excited about Gutsy...bad move so far!

---

### Post by Davix on 2007-10-19
Same problem.

I got blank screen after installation, it tooks nearly 4 mins to boot, but by readig all the posts i realise that the laptop is going in sllep mode for some time then woke up...

T43 1,86 MHZ
ATI X300
2GB RAM

---

### Post by VimesUK on 2007-10-19
I know to expect a challenge when trying out linux but this time I too can't get past the black screen issue...

I have only tried the 64bit version of Ubuntu and Kubuntu 7.10

Intel E2180
4GB RAM
Gigabyte P35 chipset motherboard
8800GTS connected via DVI

... the quest continues, for a while anyway :(

---

### Post by studo77 on 2007-10-19
Yup. Had the black boot on 7.10 RC (ATI X1600:PCIe16, AMD62.3200+, AsRock Dual Sata-2) both 64bit and 32bit ver.
And as being new to Ubuntu i do not want to make the move to 7.10 64bit yet. It is a stopper for new users, a big one.

Got it all working fine on Feisty 32bit, so sticking put until someone has made a general  "How to"

---

### Post by PixelDJ on 2007-10-19
I had the same issue. (NVIDIA 8800GTX/ AMD64 3500+ / 2GB RAM)

I just chose safe graphic option, hit F6 and changed splash to nosplash. After waiting for a bit the text started scrolling and then there was a flash and the screen went blank again. I waited a few minutes and decided to give up, but I hit the space bar and the desktop showed up, so that's great.

Thanks for the help guys.

---

### Post by VimesUK on 2007-10-19
...well that must be the secret then....

nosplash and remove quiet and then....

hit the space bar :)

It seems to have worked for me. Now unless I bork up the formatting (I really hope that I do not mess up my partition that I want to keep) I hope that it installs, and reboots, fine... :D

NO luck :(

It allowed me to install the OS but now when it boots I get the message...

Kernal Alive    Kernal Direct Mapping Tables.....

a black screen and zero :(

---

### Post by matty_p60 on 2007-10-19
ive gone through this entire thread and none of the solutions have worked for me :confused:

Feisty also installed fine on my machine (although i had to run it with the "noapic" option)

Im using the 32bit version of Gutsy Gibon and my machine is:
Geforce 7900GTO x2 (SLI'd together)
AMD64 3200 (dual core)

Booting with the live cd, it gets to the running /etc/rc.local and im guessing as other ppl are suggesting here X fails to load as i can ctrl alt f6 and get shell access no probs

---

### Post by thewolf32 on 2007-10-19
Still no solution for me in all this thread... Canonical should have delayed Gutsy release a bit...

---

### Post by eTronicGaming on 2007-10-19
I followed the instructions on selecting safe graphics mode, pressing F6, and editing it to say nosplash instead of quiet splash.  I then change my xorg.conf file to read 'Option "LVDSBiosNative" "false"' under where it says vesa driver.  I then save, quit, and run startx.
Everything loads fine (well it starts off really slow, and then barely works), but I can get to the desktop... a very inactive one.  From there, the taskbars do not work and are not clickable, there's no wireless/battery/sound icon anymore, and the only thing that highlights when you mouseover is the two desktop icons... but when selecting one or right clicking, the computer/desktop freezes and I can't get anywhere.

BTW, I'm using an ATI Radeon graphics card with fglrx, but nothing seems to work on my Thinkpad T60p.

Any help?

---

### Post by Falcorian on 2007-10-19
> **VimesUK said:**
> ...well that must be the secret then....

nosplash and remove quiet and then....

hit the space bar :)

It seems to have worked for me. Now unless I bork up the formatting (I really hope that I do not mess up my partition that I want to keep) I hope that it installs, and reboots, fine... :D

NO luck :(

It allowed me to install the OS but now when it boots I get the message...

Kernal Alive    Kernal Direct Mapping Tables.....

a black screen and zero :(

You might have to edit your grub menu to have nosplash too... That's what I've had to do.

On your grub menu, before boot, hover over the Linux version you want to run, hit e, then go to the second line and hit e again. Scroll to the end, make splash nosplash, and remove quite. Hit enter, and then hit b to boot it.

Works for me. You can also set these options in your /boot/grub/menu.ist

---

### Post by md5hash on 2007-10-19
I never had a problem during the installation.. now everytime i logged in the screen goes blank for 15seconds then the desktop shows,, 

using nvidia 5500

---

### Post by xgener8or on 2007-10-19
I have a ATI X850XT and get a black screen during booting on DVI. If I connect VGA I can see the boot logos etc. Might be the same thing going on.

---

### Post by Saponsky09 on 2007-10-19
This bug is reported on the release notes (which I don't think anyone read) that appears when you install Gutsy. It says "please read before..." or something like that. For those of you that get a blank screen during the loging in splash... it is a bug in the splash screen that doesn't seem to detect the correct resolution.  I had the problem but after loging I kept moving the mouse until I get my gnome dekstop. Then I did:
```
sudo gedit /etc/usplash.conf
```
and it got the wrong resolution for my monitor. So I changed it to: 
```

x=1024
y=768

```
and now everything is working fine for me. I hope this solves the problem for you.

---

### Post by thewolf32 on 2007-10-19
No, it doens't, because I CAN'T SEE MY GNOME DESKTOP NO MATTER WHAT I DO!

And it's not a BLANK screen it's a BLACK screen.

---

### Post by kyrmia on 2007-10-19
> **serfcx said:**
> Same thing here with Geforce 440.
Hitting reset on screen will get back display

I am having the same problem with HP Pavilion tx1210, I tried the comands above but none of them worked. Anymore ideas?

Technical Details
Lightweight tablet PC with 180-degree swiveling 12.1-inch screen (WITHOUT TOUCHSCREEN) and integrated 1.3-megapixel WebCam
1.9 GHz AMD Turion 64 X2 TL-58 processor, 160 GB hard drive, 2 GB RAM (max), LightScribe DVD-/+RW drive
Connectivity: 3 USB, 1 FireWire, 1 VGA, 1 ExpressCard 34, 1 headphone, 2 microphone, 1 S/PDIF out, 5-in-1 memory card reader
Quad-mode Wi-Fi LAN (802.11a/b/g/n), 10/100 Ethernet, Nvidia GeForce Go 6150 video card with up to 287 MB shared memory
Pre-installed with Windows Vista Home Premium (with Media Center capabilities)

:lolflag:

---

### Post by Saponsky09 on 2007-10-19
are you booting with 'noapic' in you boot options? if not, try it and after the BLACK screen (sorry for the BLANK, pardon my grammar errors) wait a while for gnome to load completely and move your mouse, you should be able to see your desktop. If not, then maybe you need some more boot options enabled, and as for the Live CD I could not solve the problem until I installed it to my HD.

---

### Post by kyrmia on 2007-10-19
How do I get to NOAPIC boot option?
Thanks:guitar:

---

### Post by erqu1 on 2007-10-19
I am new to LINUX and to this forum. I am having a similar problem but with 7.04. My system, HP D530 P4 2.8 Ghz w 256 MB RAM seems to hang. Once I select Install the system seems to freeze but there is CD activity. I've tried several times with the same results. BTW my PC has 2 internal 40 GB disk and windows XP home addition on ID 0. I want to install ubuntu on ID1 and have a dual boot.

---

### Post by Ancheron on 2007-10-19
Just wanted to add my voice to the throng to report that I have the same problem as well. 

Besides, that, the symptoms are the same as previously posted. No additional information that I can give. 

T60P 
ATI Radeon FireGL v5250

---

### Post by Therion on 2007-10-19
Watching this thread with great anticipation because I have the same problem.  I can get to the desktop using the LiveCD, but to do that, I had to boot into Safe Graphics mode, edit /boot/grub/menu.lst with nosplash and removing quiet.  

From there I was able to do a complete install (with a full drive reformat).  Install exits cleanly.  After rebooting from the hard drive though, the black screen returns.  It **appears ** Gutsy is active, but I'm getting absolutely NO display on the monitor.

I can get to a command line, but from there I'm not sure what to do.  Trying to install the 64-bit version of Gutsy and I read somewhere that this issue ONLY affects the 64-bit version.  Just downloaded the 32-bit version of Gutsy and if no other solution is forthcoming might try installing that instead to see if it solves the problem.

Machine is a home build:

AMD-64 4200+ X2
nVidia 8800 GTS
2GB of Corsair RAM

---

### Post by gregbzh on 2007-10-19
I've had the same problem with the 32-bit version.  This is driving me crazy!:confused:

---

### Post by Lorenz on 2007-10-19
As I have a T60 and an ATI card as well I will wait for a solution before I upgrade...
Just wanted to check in and wish you guys good luck and hopefully a solution will come up soon!

---

### Post by Therion on 2007-10-19
> **gregbzh said:**
> 
I've had the same problem with the 32-bit version.  This is driving me crazy!:confused:
Thanks for letting me know.  You probably saved me some time and frustration.  And yes, this whole issue IS maddening.  

I'm convinced this is related to the display resolution since it seems everyone who's had this problem has resolved it by getting the default resolution down to 1024x768.  I'm pretty n00bish with all of this and I don't know to accomplish that from the command line I'm dumped to after using the Recovery Mode in the GRUB menu.

---

### Post by ullaspa on 2007-10-19
Hi,

The live CD worked fine for me. I'm getting the blank screens both during startup and shutdown using the 32-bit on a ATI 200M Radeon 9600 on Compaq nx6325. will watch this thread further. :)

---

### Post by gregbzh on 2007-10-19
> **Therion said:**
> Thanks for letting me know.  You probably saved me some time and frustration.  And yes, this whole issue IS maddening.  

I'm convinced this is related to the display resolution since it seems everyone who's had this problem has resolved it by getting the default resolution down to 1024x768.  I'm pretty n00bish with all of this and I don't know to accomplish that from the command line I'm dumped to after using the Recovery Mode in the GRUB menu.

I'm trying this at the moment.  You can change the resolution by pushing F4 when you are given the boot/install options.

Um, to be perfectly honest it's not doing a helluva lot here at the moment.

---

### Post by DeanFX on 2007-10-19
Possibly a dumb question, But I downloaded the 7.10 from the website...
But earlier in this topic I saw a link for a Fiesty Fury ver or something...is that different?

What is the "Gutsy live-cd"? Is that just the normal 7.10 download?

:lolflag: [http://www.bored-board.com](http://www.bored-board.com) :lolflag:

---

### Post by DeanFX on 2007-10-19
This is  boot option I see :file=/cdrom/preseed/ubuntu.seed boot=casper  initrd=/casper/initrd.gz quiet splash
Where do I get to edit or add "noapic" boot option??? please advise!!!!
:lolflag:

---

### Post by gregbzh on 2007-10-19
> **DeanFX said:**
> Possibly a dumb question, But I downloaded the 7.10 from the website...
But earlier in this topic I saw a link for a Fiesty Fury ver or something...is that different?

What is the "Gutsy live-cd"? Is that just the normal 7.10 download?

:lolflag: [http://www.bored-board.com](http://www.bored-board.com) :lolflag:

Yes.  You can use it as a live CD or install it to your hard drive.

Feisty Fawn is/was the previous release of Ubuntu (7.04).

---

### Post by tracer07 on 2007-10-19
> **DeanFX said:**
> This is  boot option I see :file=/cdrom/preseed/ubuntu.seed boot=casper  initrd=/casper/initrd.gz quiet splash
Where do I get to edit or add "noapic" boot option??? please advise!!!!
:lolflag:

at the end? :) 

:file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noapic

---

### Post by Therion on 2007-10-19
> **DeanFX said:**
> Possibly a dumb question, But I downloaded the 7.10 from the website...
But earlier in this topic I saw a link for a Fiesty Fury ver or something...is that different?
Feisty Fawn is Ubuntu version 7.04

> **DeanFX said:**
> What is the "Gutsy live-cd"? Is that just the normal 7.10 download?
The LiveCD is the normal download, yes.  It allows you to run Ubuntu (whatever version) straight off the bootable CD, no actual install required.  It does provide you with the *option* to install to the hard drive however.

Hope that helps.

---

### Post by kyrmia on 2007-10-19
> **tracer07 said:**
> at the end? :) 

:file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noapic
I got through now I can see the desktop with two icons Examples & Install.
Is there anything i need to do before i hit install?

---

### Post by gregbzh on 2007-10-19
Something really bizarre is going on here.  I now can't even install Feisty without it hanging during the installation.  My dual boot Vista starts no worries.

Sorry, think I've been put off Gutsy (more like Gusty).  Shocker!

---

### Post by DrStein on 2007-10-19
It worked pefect with 7.04. Now I've just started with the 7.10 CD (which integrity is fine) and screen gets fully coloured and computer goes stand by. Keyboard won't work.

Intel Corporation 82865G Integrated Graphics
Pentium 4 HT 2.4 GHZ

Can we have an official reply about this issues? Thanks.

---

### Post by kyrmia on 2007-10-19
> **Saponsky09 said:**
> are you booting with 'noapic' in you boot options? if not, try it and after the BLACK screen (sorry for the BLANK, pardon my grammar errors) wait a while for gnome to load completely and move your mouse, you should be able to see your desktop. If not, then maybe you need some more boot options enabled, and as for the Live CD I could not solve the problem until I installed it to my HD.
Thank you!!!!!!!!!!!!!!!!!!!!!!!
I used "noapic" boot option ":file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noapic"
wait as advised, when the CD finishen loading i moved the mouse and there was my desktop with two icons Examples & Install.
before installing is there any step or setup i need to do?

---

### Post by Therion on 2007-10-19
> **tracer07 said:**
> at the end? :) 

:file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noapic
Ummm... Just so I'm clear, is this line found in the /boot/grub/menu.lst file?  Is that what needs to be modified with the "noapic" option?  If not, could you explain how to get the correct file, please?

I'm willing to try anything to get "Gutless" up and running. 

Thanks!!

---

### Post by erqu1 on 2007-10-19
I replied earlier with a similar problem and I now able to install 7.04. The problem was resolved by installing in Graphics safe mode. Who would have “thung” it.

---

### Post by gregbzh on 2007-10-19
I'm trying the same thing with 7.04 in safe graphics mode.  It's doing the same thing and freezing with the blue line (I'm installing Kubuntu 7.04) 1/4 of the way through.  What's going on here?

---

### Post by finnen on 2007-10-19
Therion, I think you can do like this:

> **Falcorian said:**
> You might have to edit your grub menu to have nosplash too... That's what I've had to do.

On your grub menu, before boot, hover over the Linux version you want to run, hit e, then go to the second line and hit e again. Scroll to the end, make splash nosplash, and remove quite. Hit enter, and then hit b to boot it.

Works for me. You can also set these options in your /boot/grub/menu.ist

This way you should be able to get to that line and add noapic

---

### Post by Therion on 2007-10-19
> **finnen said:**
> Therion, I think you can do like this ... 
This way you should be able to get to that line and add noapic
Okay, thanks!

Just for anyone else it MIGHT help someone solved the black-screen issue by reconfiguring X:

```
sudo dpkg-reconfigure xserver-xorg
```

Not sure exactly WHAT they did (screen resolution???), but maybe once I'm there something will jump out at me.  I'm at work right now and all I can do at the moment is compile a list of possible fixes to try when I get home.

---

### Post by kyrmia on 2007-10-19
I am finally in the istalling screen:


_Vista & Ubuntu - Install Ubuntu - User Details _

On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

[http://apcmag.com/system/files/images/vista_ubuntu_12.article-width.jpg](http://apcmag.com/system/files/images/vista_ubuntu_12.article-width.jpg)

but on my laptop Windows Vista was not detected, If i go on istalling will I loose my WinVista???
:lolflag:

---

### Post by DrStein on 2007-10-19
> **DrStein said:**
> It worked pefect with 7.04. Now I've just started with the 7.10 CD (which integrity is fine) and screen gets fully coloured and computer goes stand by. Keyboard won't work.

Intel Corporation 82865G Integrated Graphics
Pentium 4 HT 2.4 GHZ

Can we have an official reply about this issues? Thanks.

I managed to install it. On the boot menu, higlight "Safe Graphics Mode" option, then hit F6 and press backspace so you remove "quiet splash --", and write "nosplash".
Press enter and this time will load succesfully.

Good luck!

---

### Post by VimesUK on 2007-10-19
> **Falcorian said:**
> You might have to edit your grub menu to have nosplash too... That's what I've had to do.

On your grub menu, before boot, hover over the Linux version you want to run, hit e, then go to the second line and hit e again. Scroll to the end, make splash nosplash, and remove quite. Hit enter, and then hit b to boot it.

Works for me. You can also set these options in your /boot/grub/menu.ist

Many thanks for that it worked a treat :)

---

### Post by thewolf32 on 2007-10-19
> **DrStein said:**
> I managed to install it. On the boot menu, higlight "Safe Graphics Mode" option, then hit F6 and press backspace so you remove "quiet splash --", and write "nosplash".
Press enter and this time will load succesfully.

Good luck!


It doesn't wotk for me, it just stays in sleep mode, it won't wake up!!!!

This is so f**king annoying!!!!!!!!

---

### Post by Weezer on 2007-10-19
Resolved!

At boot menu, select safe graphics mode
ctrl+alt+F1
"sudo dpkg-reconfigure -phigh xserver-xorg"
select "vesa"
X automatically tried to start a moment later (although I could have ctrl+alt+F7ed back, then ctrl+alt+backspace to do it manually)
Logged into safe mode Ubuntu.


Somewhat funny, though, is that the install window is bigger than the height of your screen in Safe Mode, so you can just barely click the "Next" buttons if you put your top and bottom toolbars on the left and right of the screen. 


Install... Works perfectly since I downloaded the nVidia driver. Now I just need to scavenge for eyecandy and not-emulators.

---

### Post by Saponsky09 on 2007-10-19
Ok I'll try to explain how to fix this for those installing over any HP dv9000 laptop... (worked perfectly for me)... 
*note* I'll explain for the installation only since I don't think you will get to see the effect using the Live CD.
1-Boot from the Live CD.
2-At boot option hit F6 and write: noapic, the press enter.
3-When you login you will hear the sounds from the splash screen but your screen will probably go black. * This is due to an error from the splash screen detecting the wrong screen resolution. Because it sets your vertical resolution too high.*
4-Wait a while (like 50secs to be sure) and move your mouse constantly, you should be able to see your gnome desktop. If you get some error saying something about your themes, just click ok.
5-Install Gutsy
6-You will get the same 'black screen problem when you boot up from installation. So just do the same as in step 4 and...
7-From the terminal (applications>accesories>terminal) type:
```
sudo gedit /etc/usplash.conf
```
and write: 
```

x = 1024
y = 768

```
8-Save and exit.
  Log out and log in again to check if it worked.
**This worked for my HP dv9000  so I don't know if this will work for everyone.

---

### Post by thewolf32 on 2007-10-19
NOTHING WORKS FO ME, the CD stops working after it goes black !!!!!!

---

### Post by Morkalin on 2007-10-19
> **thewolf32 said:**
> NOTHING WORKS FO ME, the CD stops working after it goes black !!!!!!

Can you please have a look at my thread about this:

[http://ubuntuforums.org/showthread.php?t=581730](http://ubuntuforums.org/showthread.php?t=581730)

I have put together all of the Ati "blank screen" solutions that I have found so far into one thread.  This is for those who have tried "everything".  Hopefully we can get some attention on that one for those with the CD stopping / "persistent sleep mode" problem.

Regards,
Morkalin

---

### Post by imcompa on 2007-10-19
> **gregbzh said:**
> Something really bizarre is going on here.  I now can't even install Feisty without it hanging during the installation.  My dual boot Vista starts no worries.

Sorry, think I've been put off Gutsy (more like Gusty).  Shocker!

Same thing happens to me. If I use any of those work arounds it freezes during installation. One time it worked, but I had to resize the partitions in windows, and now it won't work.

I think I know what was wrong, I was leaving the -- at the end when changing "quiet spash --" to "nosplash" i left the -- on the end. we'll see...

---

### Post by xastxast on 2007-10-19
None of these worked for me Amd x2 4000 o/b ati 1200

---

### Post by imcompa on 2007-10-19
At the start up of the cd scroll down to the second option "Start in safe mode" hit f6 while it is highlighted and scroll to the end of the text box that apears
delete: ```
quiet splash --
```
and replace it with:```
nosplash
```
hit enter.
wait a while for ubuntu to start up. You should see text, then it should go blank and you'll hear the ubuntu start-up sound. (My monitor said Incorrect Resolution please change it to etc etc) Now 
hit **crt-alt-BACKSPACE**. This shuts down the xserver (gui). The terminal should come up.

Type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
select the correct driver, mine was vesa (For nvidia 8800gts) hit enter.
then select the correct resolution(s) and hit **SPACEBAR** to add it.
Then hit enter.

type: ```
startx
```

Wala.

---

### Post by thewolf32 on 2007-10-19
I don't even hear ubuntu's startup sound

---

### Post by imcompa on 2007-10-19
> **thewolf32 said:**
> I don't even hear ubuntu's startup sound

speakers on? the soudn doesn't matter, just that your screen goes black and you can hit crt-alt-f6 which will bring you to terminal

---

### Post by haylocki on 2007-10-19
> **Therion said:**
> I'm convinced this is related to the display resolution since it seems everyone who's had this problem has resolved it by getting the default resolution down to 1024x768.  I'm pretty n00bish with all of this and I don't know to accomplish that from the command line I'm dumped to after using the Recovery Mode in the GRUB menu.

Here's a way :


type :

cd /etc/X11
cp xorg.conf xorg.conf.old
nano -w xorg.conf

Now scroll down to the where you see a line that says "Section Screen"

you should see a line that says default depth.

mine says : "DefaultDepth    16"

under this line insert :

        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection


Note, the number after Depth should be the same as the number after DefaultDepth.

type :
<CTRL> x to exit
press y to save
then enter for the default filename

now try typing :

startx

you should get a message complaining about using x as a root user, but ignore that and see if you can see the desktop.
If this works reboot and your desktop should be working.

if you want to change your xorg.conf file back :

reboot to recovery mode again.
cd /etc/X11
cp xorg.conf.old xorg.conf

HTH

Ian

---

### Post by thewolf32 on 2007-10-19
> **imcompa said:**
> speakers on? the soudn doesn't matter, just that your screen goes black and you can hit crt-alt-f6 which will bring you to terminal

Yes speakers on, when it reaches the GDM, it just shuts down but the system is still on, like if it were sleeping, and the CD slowly stops spinning in my drive (i can hear it). No matter what I do will bring the terminal.

I need serious help!!!!

---

### Post by Morkalin on 2007-10-19
Hi Ian,

Definitely not a resolution problem for me - I tried that already.

Regards,
Wayne

---

### Post by thewolf32 on 2007-10-19
Is this happening in Kubuntu and Xubuntu?

---

### Post by Rush_ht on 2007-10-19
> **Falcorian said:**
> I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)

this worked for me to get to run Live_CD

---

### Post by Morkalin on 2007-10-19
> **thewolf32 said:**
> Is this happening in Kubuntu and Xubuntu?

I haven't tried personally and I dont' have the bandwidth to try the others unfortunately.

Regards,
Wayne

---

### Post by 64Guitars on 2007-10-19
I get the black screen after booting from the 7.10 Live CD too. But I found that it's just putting my monitor into power-saving mode. If I move the mouse, the screen wakes up and all is well thereafter.

---

### Post by Morkalin on 2007-10-19
Moving mouse and space-bar doesn't work for me either.  Also tried connecting an external monitor - no go.

Regards,
Wayne

---

### Post by kyrmia on 2007-10-19
on the CD boot screen select F6 (boot options) you will see ":file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash--"
remove the last two dashes and type "noapic"
It should look like this ":file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noapic"
press enter
when the CD stops loading , move the mouse you should see the desktot with two Icons "examples & install" click install and follow the screens..........
goodluck.
:guitar:

---

### Post by Morkalin on 2007-10-20
> **kyrmia said:**
> on the CD boot screen select F6 (boot options) you will see ":file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash--"
remove the last two dashes and type "noapic"
It should look like this ":file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noapic"
press enter
when the CD stops loading , move the mouse you should see the desktot with two Icons "examples & install" click install and follow the screens..........
goodluck.
:guitar:

Doesn't work for me :-(

Regards,
Wayne

---

### Post by thewolf32 on 2007-10-20
Doesn't work for me either!

---

### Post by QuimNuss on 2007-10-20
My problem WAS that every time I touched anything on the screens & graphics i got a black screen on restart.

That was solved by doing what you were telling with a little modification:

> 
| On your grub menu, before boot, hover over the Linux version you want to run, hit e, then go to the second line and hit e again. Scroll to the end, make splash nosplash, and remove quite. Hit
| enter, and then hit b to boot it.
|
| Works for me. You can also set these options in your /boot/grub/menu.ist


that is replace "quite splash" to "nosplash"

that made I got stuck on the "running local boot scripts (/etc/rc.local)"

but if you press enter you can log in and then make:

sudo dpkg-reconfigure xserver-xorg -plow

that rui bernardo suggested on another thread (thanks!). Follow his steps and voilà! everything back to normal.

> Try to reboot to Rescue mode. If the problem still continues, press Alt+Ctrl+F1, login and then try

sudo dpkg-reconfigure xserver-xorg -plow

Accept all default answers, but the driver and resolution. I don't know if the vmware graphical driver is included in Ubuntu, but if it isn't, select vesa. For resolution, try to enable lower ones (1024x768). Maybe this helps.

Then try to start again Gnome with

sudo /etc/init.d/gdm restart


apparently it keeps swithching the screen resolution to the wrong one. But if I edited it directly by
sudo nano -w /etc/usplash.conf
it didn't work.

thanks everyone!

(absolute n00b on linux, learning everyday since 1)

---

### Post by xastxast on 2007-10-20
This worked for me thanx imcompa 
> At the start up of the cd scroll down to the second option "Start in safe mode" hit f6 while it is highlighted and scroll to the end of the text box that apears
delete:
Code:

quiet splash --

and replace it with:
Code:

nosplash

hit enter.
wait a while for ubuntu to start up. You should see text, then it should go blank and you'll hear the ubuntu start-up sound. (My monitor said Incorrect Resolution please change it to etc etc) Now
hit crt-alt-BACKSPACE. This shuts down the xserver (gui). The terminal should come up.

Type:
Code:

sudo dpkg-reconfigure -phigh xserver-xorg

select the correct driver, mine was vesa (For nvidia 8800gts) hit enter.
then select the correct resolution(s) and hit SPACEBAR to add it.
Then hit enter.

type:
Code:

startx

Wala.

---

### Post by sypher7 on 2007-10-20
Hi all,

I too had this problem, but was able to overcome it. It turns out, SLI was the culprit. I have two Nvidia Geforce Go 7900 GS cards. 

I would boot up the live CD and after a while, when it would get to the part where the login manager should load, it simply gave me a blank screen.

Since I was still able to CTRL-ALT-F1 and drop to the console, this is what I did to resolve the problem (note: I did not change *any* boot parameters, so none of the F6 craziness at the boot screen):

1) Select "Start Ubuntu or Installation"
2) Waited for a bit... eventually I got some text and then the blank screen where the GDM login manager should be
3) CTRL-ALT-F1 to switch to the console
4) lspci

At this point look for your video cards. You will notice the lines with your video cards have some numbers at the beginning of the line. For example, mine looked like this:

06:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
07:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)

The "06:00.0" and "07:00.0" are the important parts here.

5) sudo vim /etc/X11/xorg.conf
(or whatever your editor of choice is)

6) go down and find a line in the video card section that looks similar to this:

        BusID           "PCI:6:0:0"

and change the BusID to that of your OTHER card:

        BusID           "PCI:7:0:0"

save the file and exit.

7) CTRL-ALT-F7 to get back to the X terminal.
8) CTRL-ALT-Backspace to force it to quit (it will restart automatically with your changes to the config file).
9) voila.

I can't guarantee that this will work for you, but it did for me. It only applies to those of you experiencing this problem that have TWO video cards (i.e. an SLI setup). It seems that there might be varying reasons for this "blank/black screen of doom" issue, so be sure to try some of the other suggestions in this thread as well.

---

### Post by thewolf32 on 2007-10-20
For me it's not a blank screen, it's a black screen

---

### Post by bjfrankcn on 2007-10-21
> **Kevf said:**
> I never had any install-probs with 6.06 or 7.04 (dual boot with xp)

But with 7.10  after I chose install from te menu my screen turns black and goes into standby modus.......

2.6 ghz
512 mb ram
ati radeon xpress 200 ( I know, I know)

and a bit frustrated

I just found a solution: When your screen turns black, you can press CTL + ALT + F1. After that, Ubuntu 7.10 boot quite well.

---

### Post by dongbin1717 on 2007-10-21
same problem on my Thinkpad T61p 6457AB4

Intel C2D T7500
2G DDRII 667
NV Quadro FX 570M 256M VRAM
160G HDD
1920*1200 15.4' LCD

---

### Post by athletics on 2007-10-21
I have Ati graphics card. To install Ubuntu I had to use the Alternate Install CD in text mode. Then I needed to boot in Rescue Mode and edit /etc/X11/xorg.conf to replace ati with vesa

Section "Device"
   ...
   Driver "vesa"
   ...
EndSection

---

### Post by matty_p60 on 2007-10-21
ive tried vesa and nv (as i assume that stands for nvidia) and restarted X using ctrl alt backspace.. still a black screen :(

Does the fact i have 2 graphics cards set up in SLI mode mean i need to do anything differently? I am still only using 1 monitor tho

---

### Post by arafel65 on 2007-10-21
I just added "noapic" to the boot option "F6" to get things going, after installation, i get the same blank screen. 

So i edit my kernel entry from grub by adding **noapic** and it boots succesfully.

After booting i edit /boot/grub/menu.lst and **noapi**c to the end of the kernel statements to make it permanent.

@finnen You will need a wired network so that you can enable and download restricted drivers, that is how i got my broadcom wireless going. Everything runs well so far.

Here are my laptop specs:
HP Pavilion dv6331eu
AMD Turion64 X2 TL-56 @1.8GHz
2 GB Ram
Nvidia Geforce Go 7200
160 GB HDD

I hope this helps.

---

### Post by VictorOdin on 2007-10-21
Does the same thing to me.

QX6800
Nvidia 8800GTX
4GB Ram
1TB Drive

---

### Post by SledgeHammer_999 on 2007-10-21
I have a similar to your problem but not exactly the same. I posted it here [http://ubuntuforums.org/showthread.php?t=585047](http://ubuntuforums.org/showthread.php?t=585047)

---

### Post by sean222 on 2007-10-22
> **Falcorian said:**
> I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)

Yay! Thanks **Falcorian**! I too was experiencing the blank screen after the initial LiveCD menu. Now I'm posting this from the LiveCD using your method! Don't know why or how it works but it does!

I hope after my install now...that I don't get this prob again :(

[I]EDIT: Ok, just installed from the LiveCD, upon restarting...blank screen again. But with my little Ubuntu knowledge I edited the grub boot line to once again remove QUIET and add NOSPLASH. Then edited my grub menu.lst once in Ubuntu to make it permanent until someone finds the problem. I'll keep my eye open for it, but if anyone knows, post it please!

I assume the problem has something to do with the [ Graphics card, DVI Connection, and the Graphical Splash screen ][/I]

-------------------
My Specs that gave the blank screen
InteL C2D E6750
Gigabyte DS3L
4GB PC2-8500 Mushkin
Dell 2407 LCD w/DVI Connection
eVGA 8800GTX
Raptor X HD

---

### Post by bernardobraga on 2007-10-22
hey guys,I managed to solve the issue following these tips:
> **Falcorian said:**
> I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)
I created a tutorial topic so we could share successful attempts, I named it "Avoiding black screen on ubuntu 7.10 installation" but it is still waiting for administration approval
Falcorian, I forgot to give you credit for the tip, if the tutorial ever gets validated, I'll edit it so it does give you credit.
Just one more thing: I think Falcorian meant "Remove the word **quiet** at the end", that's what I did and it worked. Just pointed out cause it caused a little confusion for me =]
thanks for the help.
bernardo.

---

### Post by OmahaZ on 2007-10-22
I experienced the blackscreen with the 100.14.19 driver which is installed default by restricted manager. A solution that works fine with me is to use the 9639 driver installed and configured "manually" in terminal.

 Works fine - no crashes no lagging no problem (Nvidia GO 7200 / AMD 64 / Gutsy 386)

As far as I know this is a Nvidia driver problem. The 100.14.23 beta is available from the Nvidia site and as far as I've heard, this driver solves the problem. I'll guess it will become available from the repos as soon as the final is released.....

---

### Post by atari05 on 2007-10-22
> **finnen said:**
> I got it to work!
I added this to the boot options (press F6 in the meny)

noapic irqpoll noirqdebug

Now I just have to get my broadcom wireless to work without any wired network avaiable :-k

edit: this was in safe mode


I got a compaq v6000 and the

"noapic irqpoll noirqdebug"

trick got the live cd to boot, I did make sure to use safe mode graphics so I don't know if its regular startup or not

---

### Post by matty_p60 on 2007-10-23
> **OmahaZ said:**
> I experienced the blackscreen with the 100.14.19 driver which is installed default by restricted manager. A solution that works fine with me is to use the 9639 driver installed and configured "manually" in terminal.

 Works fine - no crashes no lagging no problem (Nvidia GO 7200 / AMD 64 / Gutsy 386)

As far as I know this is a Nvidia driver problem. The 100.14.23 beta is available from the Nvidia site and as far as I've heard, this driver solves the problem. I'll guess it will become available from the repos as soon as the final is released.....

Could you elaborate on this? how do u download and install a new driver if ur booting from the live cd and cant see the desktop?

None of the other solutions here have worked for me (AMD64, Nvidia 7900GTO x2, Gutsy 32bit version)

---

### Post by DoomCypher on 2007-10-23
Well, I've tried the "sudo dpkg-reconfigure -phigh xserver-xorg" command in safe mode, but says that battery.ko is missing [fatal]

EDIT: Ok, nosplash and removing quiet did the job for the Live CD. I'll try installing and then rebooting. I'm still getting the battery.ko stuff tho.

---

### Post by sipickles on 2007-10-23
I'm also suffering: AMD Turion64 GeForce 7300 Go, ASUS laptop, with widescreen


I've tried ALL these variations. No good.Booting the live CD hangs at the lines to do with APCI.

I've tried 32bit, 64 bit, alternative, all MD5s okay, CD okay, all command line options described here.....

I've nearly lost interest in ubuntu. Shame.

Strangely, the latest Mandriva release has a similar problem :confused:

---

### Post by DoomCypher on 2007-10-23
> **sipickles said:**
> I'm also suffering: AMD Turion64 GeForce 7300 Go, ASUS laptop, with widescreen


I've tried ALL these variations. No good.Booting the live CD hangs at the lines to do with APCI.

I've tried 32bit, 64 bit, alternative, all MD5s okay, CD okay, all command line options described here.....

I've nearly lost interest in ubuntu. Shame.

Strangely, the latest Mandriva release has a similar problem :confused:

I had to remove the ACPI features in my BIOS to make Ubuntu work.

Concerning the problem with the blank screen, it's easy:

* remove quiet and change splash to nosplash in the live cd boot menu (need to press f6)
* when it finishes installing, and then it restarts, press esc while loading grub
* do nano /boot/grub/menu.lst
* and remove quiet and change splash to nosplash again, where the default selection is.
* ctrl+o to save and enjoy ubuntu 7.10

Someone should sticky this IMO, 13 pages of the same problem...

---

### Post by CryptSphinx on 2007-10-24
Ok, 
(using a amd64, radionx1300, nvidia ??)
changed the resolution to lowest possible and boot option to nosplash.

now 63% into installation and all looks ok.......

---

### Post by sipickles on 2007-10-24
> **DoomCypher said:**
> I had to remove the ACPI features in my BIOS to make Ubuntu work.

Concerning the problem with the blank screen, it's easy:

* remove quiet and change splash to nosplash in the live cd boot menu (need to press f6)
* when it finishes installing, and then it restarts, press esc while loading grub


Unfortunately, my BIOS is the simplest I've ever seen, with no access to any ACPI features :(

Removing quiet and changing splash to nosplash has no effect - hangs at 'ACPI Interpreter Enabled'

---

### Post by hyliker on 2007-10-24
maybe you can try to install startupmanager to fix the usplash problem.

1.install startupmanger
$ sudo apt-ge install startupmanager
2.after finish installation. then you can change boot setting for usplash.
$ sudo startupmanager

try above you will fix some problem you meet.

---

### Post by sipickles on 2007-10-24
I only have windows on my laptop... with an empty ext3 drive waiting for ubuntu!

---

### Post by sipickles on 2007-10-24
I'd like to congratulate the developers of openSuse 10.3.

Downloaded and seamlessly installed in less than one hour, even on the Linux Unfriendly ASUS A6000 laptop,

All thanks to the option: 'Installation - ACPI Disabled'

Perhaps one for the Ubuntu wishlist?

---

### Post by Mavtech on 2007-10-25
> **DoomCypher said:**
> I had to remove the ACPI features in my BIOS to make Ubuntu work.

Concerning the problem with the blank screen, it's easy:

* remove quiet and change splash to nosplash in the live cd boot menu (need to press f6)
* when it finishes installing, and then it restarts, press esc while loading grub
* do nano /boot/grub/menu.lst
* and remove quiet and change splash to nosplash again, where the default selection is.
* ctrl+o to save and enjoy ubuntu 7.10

Someone should sticky this IMO, 13 pages of the same problem...

Sweet.  This worked for me.  Thanks!  The only thing I had to change was the 3rd part (do nano) because I am dual booting.  So, edited the menu list from recovery mode and then reboot.  I am now on the desktop.

---

### Post by lucas42 on 2007-10-26
> **thewolf32 said:**
> Is this happening in Kubuntu and Xubuntu?

I'm having the same problem using kUbuntu.  I haven't tried normal ubuntu.  I have a Geforce 7300LE graphics card and a really old monitor.

---

### Post by jtbalt on 2007-10-27
I could not get 7.10 live CD to boot - just kept getting the black/blank screen which appeared to be resolution related.  The box is a Compaq 6400NX with an S3 video driver (it's old but it works).  Anyway, here's what worked for me:

1.  Boot from the CD using the first (default) menu option for Start/Install LIve CD (I did not have to make any changes/additions by pressing F6).

2.  When the screen went blank (my monitor clicks when the resolution changes) press CTRL+ALT+F1 to get a command prompt (I had to press it a few times before the command prompt came up).

3.  At the command prompt type      sudo dpkg-reconfigure -phigh xserver-xorg
  *remember to add a space between reconfigure and -phigh*

When the configure screen comes up I chose 1024x768 and pressed the spacebar to select that resolution, then pressed "enter" to confirm the selection and save the changes, and it dropped me back to a command prompt.

4.  I then pressed CTRL+ALT+F7 (I'm not sure if this is necessary but that's what I did)

5.  I then pressed CTRL+ALT+BACKSPACE and found myself at the login screen with the liveCD desktop displayed.   I waited until the prompt timed out (did not enter a username or password - could probably have just pressed "enter")

6.  Installed 7.10 from there. So far so good.  I wish you all well.

John

---

### Post by lucas42 on 2007-10-27
I managed to fix the problem on my computer by deleting xorg.conf.  Then I installed from the live cd ad everything works.  Although I thought xorg.conf was quite an important file - my computer runs fine without it.

---

### Post by legends2k on 2007-10-27
In case, for any of you guys, a previous version of Ubuntu is working fine, and have problems installing Gutsy coz of the monitor/resolution thingy. Follow these steps:

1. Copying the older version's xorg.conf to a pendrive(USB)
2. reboot with the Gutsy LiveCD, choose SafeMode and press F6. Remove "quiet splash --" and add "nosplash". Press Enter
3. Now after it does the verbose part of loading, once the blank screen comes up, wait till the cd disc and hdd read indication to subside
4. Press CTRL + ALT + F1. Now the terminal screen should come. Now replace /etc/X11/xorg.conf with the older xorg.conf file (backup) in your USBDrive which wolud have got mounted in /media/
e.g. sudo cp xorg.conf /etc/X11/
5. Now press CTRL + ALT + BACKSPACE (or) CTRL + ALT + F7 and CTRL + ALT + BACKSPACE
6. You should now see the login screen of Gutsy's LiveCD Boot!

---

### Post by fizz on 2007-10-28
I was having the blank screen problem. Was able to boot to Gutsy Live with the nosplah and removing quiet too. I installed, but it didn't appear to update my MBR so grub doesn't load.. So needless to say it wont boot gutsy install..

AMD 64 X2 3gig
2 gig ram
nvidia 8800 gts
Sata Hard drive..

---

### Post by Franko30 on 2007-10-28
Hello there,

I had the problem of black screen (monitor goes to powersave mode) after installation from the Alternate CD, too. 

According to hardware information, my system has an Intel mobile 943/940 GML Express Integrated Graphics Controller.

I changed to Terminal 1 via

CTRL+ALT+F1

and used nano to change the driver form "Intel" to "i810" in the

/etc/X11/xorg.conf

and then

sudo /etc/init.d/gdm restart

gave me a login screen and a working desktop.

It even survived a reboot, so I guess that for me the problem ist solved.

**But I'm also really wondering why such a bug made it into the final version...**

Cheers

Franko30

---

### Post by tt_jensen on 2007-10-28
> **Saponsky09 said:**
> Ok I'll try to explain how to fix this for those installing over any HP dv9000 laptop... (worked perfectly for me)... 
*note* I'll explain for the installation only since I don't think you will get to see the effect using the Live CD.
1-Boot from the Live CD.
2-At boot option hit F6 and write: noapic, the press enter.
3-When you login you will hear the sounds from the splash screen but your screen will probably go black. * This is due to an error from the splash screen detecting the wrong screen resolution. Because it sets your vertical resolution too high.*
4-Wait a while (like 50secs to be sure) and move your mouse constantly, you should be able to see your gnome desktop. If you get some error saying something about your themes, just click ok.
5-Install Gutsy
6-You will get the same 'black screen problem when you boot up from installation. So just do the same as in step 4 and...
7-From the terminal (applications>accesories>terminal) type:
```
sudo gedit /etc/usplash.conf
```
and write: 
```

x = 1024
y = 768

```
8-Save and exit.
  Log out and log in again to check if it worked.
**This worked for my HP dv9000  so I don't know if this will work for everyone.

I installed AMD64 version of 7.10 on my HP DV9000 from the live CD by giving the following command after pressing F6 in addition to the original commands:
noapic irqpoll noirqdebug
This fixed the black screen problems, and the installation went on without any problem..
:guitar:

---

### Post by Pat_Primate on 2007-10-29
I've finally fixed this sucky lil problem on my machine - the problem that almost sent me away from Ubuntu/Debian/Mint OSes.

So, if your like me and have tried a number of the other 'solutions' to no avail, then try this deceptively simple one that worked for me

At the livecd grub boot screen where you get to choose what to load, press F4 and select the appropriate resolution for your monitor. I have a Acer AL2223W 22" monitor with a default resolution of 1680 X 1050 - so I picked the 1680 x 1050 x 32 option in F4 and booted with the standard 'load or install Ubuntu/Linux Mint' option and everything worked fine - with the exception that my screen did blank for a second, but this happened after I had already seen the cursor appear (which had never happened before) so I just wiggled the mouse and the screen woke up again.

I'm so happy that I can finally enjoy Gutsy/Daryna,

Thanks everyone, and good luck to those still struggling with this problem,

Pat

---

### Post by sipickles on 2007-10-30
What would you recommend for a wide format monitor, native resolution 1280x800? This option is not available in the F4 list?

Not sure this would help me much anyway. I know my problem is ACPI related, since non-quiet boot always freezes on the ACPI sections.

Unfortunately, 'noapic nolapic" etc doesn't help, neither does 'please=for-gods-sake-work' :)

To install openSuse, I had to choose the 'ACPI disabled' option, which added 'acpi=off' to the openSuse command line. I even tried this in Ubuntu. Perhaps unsurprisingly, no effect.

---

### Post by Eriol_Ancalagon on 2007-10-30
I was able to get in via the nosplash thing, and had to do it on reboot.

Is there even a bug report for this?  The config for me seemed correct, yet this was happening.  nosplash remedied it, but still, wondering what the deal is here.

---

### Post by nightdog21 on 2007-10-31
I own an asus a6 kt notebook and experienced the same problems at installing any king of linux
Seems that the problem appears when anything is conected on the USB
For example i had my USB mouse connected and got the blank/black screen thing.
Try unplugging all USB devices and then see how it works.

 I hope it does... If not, good luck finding another resolution to this issue!

---

### Post by whistlerspa on 2007-10-31
I'm running 7.10 desktop  - not live and a while ago everything went black on boot  - even the normal boot up bios etc settings. 

Only came right after I connected the monitor to another desktop and then back again.

Running ATI 9600 pro (with restricted drivers). this is totally bizarre - never struck anything remotely like it.

---

### Post by sipickles on 2007-11-01
I'd like to say a big THANK YOU to nightdog21, also running a ASUS A6 series....

Unplugging my USB mouse fixed the boot issue! I can't believe it was so simple! Shame I've got to remember to unplug the mouse everytime I start or reboot!


Thanks Nightdog, I owe you a :popcorn:


Now to try to get the wireless working..... :confused:

---

### Post by desmo on 2007-11-03
On my work HP laptop I successfully ran and installed gutsy without any problems at all. OK, lets get a new work station and install it there:

Damn, I ran into this graphics issue promptly! I have tried all tips from this thread without to much sucess. It has excactly the same apperance as all you guys in this thread. The screen goes black and then nothing. By ctrl+alt+F7 and ctrl+alt+backspace you can get a fast "flash" of how the screen is looking (out of sync a couple of 100ms). ubuntu is running in the background. But you just cant see anything...anoying!

The only advance I have managed to get is by running and setting up the "sudo dpkg-reconfigure xserver-xorg" in the terminal. After setting up X in the terminal I hit ctrl+alt+F7 and then ctr+alt+backspace and then something new hapends:  first a cross representing the mouse apears, and then a message: "Ubuntu is running in a low performance graphics mode. Do you want to set it up?"
I hit "yes" and I will enter a graphical interface where I can set up my screen and graphics card.
 In this graphics card dialouge I can browse thorough different boards can not find my specific but the best is probablly >GeForce 6 series< (?) or >GeForce2 Integrated< (?) (I tried them both)
After this selection + a selection of my resoulution of my LCD widescreen 1280x768 is marked and I hit yes. The screen is then back to the black color. If I hit ctrl+alt+F9 I can se that "loading GNU display manager" is running and not finishing.Anyone got any tips from here?

Great thanks in advance for help!



My machine:

ASUS Motherboard M2N-MX SE
Chipset: NVIDIA nForce430/GeForce6100
AMD 64

---

### Post by MikeDK on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=512059&highlight=dv9000]("http://ubuntuforums.org/showthread.php?t=512059&highlight=dv9000")

try using this HOWTO it helps a lot

Kind Regards MikeDK

This HOWTO-link only for HP DV series users i think..

---

### Post by elgeeko on 2007-11-20
same problem here...
trying to boot from a amd64 live cd.
comp:
e6300
nvidia gts 8600

---

### Post by fiqy_z on 2007-12-01
yeah you're right. It can't find the vga drivers.
Try this :

    * On computers with Dell Recovery Partitions: Manual Install might not work in the liveCD installer. To fix this issue: "apt purge ubiquity; apt clean; apt install ubiquity" then perform the installation and restore the sources.list from the liveCD to the installed system.

    * On some hardware with ATI/nVidia cards: If the liveCD boots all the way to Gnome but hangs and just shows the mouse pointer and eventually the wallpaper, restart the liveCD, press F6 and change the options "quiet splash --" with "nosplash noapic noacpi --".



*"I LOVE INDONESIA"*

---

### Post by loldawson on 2008-04-01
> **Falcorian said:**
> I got the CD to boot to the desktop as follows:

1) Highlight safe mode
2) Hit F6
3) Remove the word quite at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)

Cheers! Worked fine after this :KS

---

