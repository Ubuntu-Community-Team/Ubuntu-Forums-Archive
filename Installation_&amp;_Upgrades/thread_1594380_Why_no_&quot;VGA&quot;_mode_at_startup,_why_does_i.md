---
title: "Why no &quot;VGA&quot; mode at startup, why does it use drivers it should know wont work"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by melvb on 2010-10-12
Sorry if this seems a bit of a rant but there is now another new version Of Ubuntu that STILL does not address the fundamentals of running on a range of hardware that is fine for Windows.

This has caused me a problem since 8.04 (7.10 is the last version I have run sort of successfully without having to jump through VGA driver hoops but I did have to jump through wireless drivers hoops and didnt solve them).

I know VGA drivers seem to be a massive problem for Linux, but there does not seem to be a way to solve it.  How do you install other drivers when the default drivers dont work - why is there no VGA mode option at boot time like (dare I say it) Windows. Why does it load with VGA drivers it knows wont work (and if it does not know, why does it not know, Windows does). I have tried the live CD on a laptop (old ATI mobile graphics) and a PC with NVidia 6800 both give me black screens with a mouse pointer. Earlier versions of Ubuntu give me various results from tiny images multiple times to psycodelic stripes. The laptop runs WinXP fine, and Win7 in VGA mode.  The PC runs WinXP and Win7 perfectly with Aero (incidentally Win7 is faster).

I am a Windows programmer/customer support technician with 22 years of PC experience (started as a hardware technician) all of it enduser facing so know their capabilities (or lack of).  I keep trying to dabble in Linux but dont get very far in the little time I have (family) so I dont have hours of spare time to solve problems that should not exist).  I know I can google and can find various commandline ways to force other drivers on (but only after I have installed it - and the live CD is meant to be a trial), what hope is there for the novice you are trying to encourage. It seems from the many blogs and forums my experiences are far from rare.

Maybe I am missing some startup option but Ubuntu has done its best to hide them.  The funny little icon at the bottom meaning to press a key to get some startup options, and noapci, nomodeset, etc are of course terms that even the most novice of users would understand arent they!

Maybe if you have the latest dogs bo**ocks hardware Ubuntu will work (I and most of the people I know dont, especially not our business users) but Linux is "advertised" as being better than Windows because it is able to run on older and less able hardware, however I cant even get it to run on Harware that is more than able to run Windows 7.  I have never yet failed to get a picture when installing Windows - any version, any PC of minimum spec for the version. It may only be 640*480 4 colour but at least I can see to sort it out, with Ubuntu you're truely "in the dark".

My years of enduser experience tells me that the CD will of hit the bottom of the bin before Windows has got back to the desktop, for people who fail to see a working (even if limited) desktop when trying the live CD.

Tell me I am doing it all wrong and simple by doing .... it will work on anything.

Mel

---

### Post by andrewthomas on 2010-10-12
Have you tried the drivers straight from nvidia?
It seems that your card is supported.
64-bit
[http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/index.html)
32-bit
[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.04/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.04/README/index.html)

---

### Post by melvb on 2010-10-12
You miss my point, I know if I Google around I can find an answer ultimately, but your average enduser cant.

How do I install the driver when running the Live CD trial which is not installed, and have a completely black screen apart from a mouse pointer.

Remmeber Ubuntu is aimed at the masses who have little computer experience. I know lots of people who could install any version of Windows and end up with a working desktop (maybe not optimum but working). Very few of those people could solve this one, and would not even install Ubuntu if the Live CD didnt "work".

---

### Post by melvb on 2010-10-12
Just tried the live CD on a NEC Powermate and the monitor just goes to out of range.

Surely there must be a way to force a basic VGA mode just so I can see the screen!

Do I need to buy the latest hardware to try this out, if so what video adapter do I need to get guarantee it will display a screen.

---

### Post by union two levers on 2010-10-12
hi there, i am an ordinary bloke with very limited,self taught computer experience...haven't even ever used a spread sheet but i use linux because i get alot of stuff for free basically. Having exactly the same problems as you, what i can't understand is why installation of a new release is so hit and miss, i am using 10.04 at the moment...9.10 was a complete disaster and i have been using it since 6.06 ...some releases work and some don't on essentially the same equipment.You obviously seem to have a great deal of knowledge ...i don't and i think i represent an awful lot of ordinary users out there....if you want fun try to print photos via f-spot.

---

