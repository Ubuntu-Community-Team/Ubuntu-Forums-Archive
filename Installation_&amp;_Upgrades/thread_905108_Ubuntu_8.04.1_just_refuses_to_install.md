---
title: "Ubuntu 8.04.1 just refuses to install"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by johnrhance on 2008-08-30
Hello everyone. I have decided to start working with Linux. From what I understand, Ubuntu is the most user friendly so I plan on starting with Hardy Heron. I downloaded the .iso from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and burned it to a DVD using Alcohol 120%. I boot into the DVD and get a GUI menu. It asks if I want to boot into a Live CD mode, or install Ubuntu. Either option I choose brings me to a loading bar which loads for approximately 5 minutes. I tried turning ACPI off, but that didn't help. After the 5 minutes of loading, I get a bunch of numbers and text that continues on for well over an hour. Maybe I'm missing a step or I'm way off base here, but I could really use some help. Here are my computer's specs:

Intel Q6600 @ 3.0ghz
DFI Lanparty P35
4GBs Corsair XMS 800mhz
EVGA 9800GTX KO
Seagate 320GB 7200.11 HDD formatted to 5 different partitions
WD 160GB 7200 with just one partition

I would be very grateful if someone could possibly walk me through the install process or help troubleshoot this problem. Thank you.

---

### Post by Partyboi2 on 2008-08-30
Have you checked the cd for defects? You can do this by selecting the option at the main menu.

---

### Post by johnrhance on 2008-08-30
Yeah it passed the defect test. I'm currently in Vista x64. I went into the CD and clicked install. Then I took the disc out, and booted into Ubuntu. It said installing and all that, then rebooted again. I chose Ubuntu and it started to load this time at a different resolution. It would never get past the loading bar though. I tried recovery mode and it doesn't work either. I'll try it again and try to get you the exact error it is giving me.

---

### Post by Partyboi2 on 2008-08-30
When you are at the main menu press F6 and change the word splash to nosplash then press enter. This will remove the loading bar (splash screen) and might give some more info on where it is getting stuck.
Another thing you could also try is using the 32bit ubuntu iso instead if the 64bit if you aren't already.

---

### Post by johnrhance on 2008-08-30
Well guys, I don't know exactly what I did but I am now in Hardy Heron! How do I change my screen resolution to 1680x1050? The highest it is showing is 1280x1024. Thank you guys for the help so far.

---

### Post by Partyboi2 on 2008-08-30
You can try to change your screen resolution in  Screen Resolution (System>Preferences>Screen Resolution)

---

### Post by johnrhance on 2008-08-30
I found where to change it, but it doesn't let me change to anything about 1280x1024. Don't tell me I can't get it to my monitor's native res :(

---

### Post by Partyboi2 on 2008-08-30
Open a terminal (Applications>Accessories>Terminal) and type
```
gksudo displayconfig-gtk
``` and see if you can change the settings there.

---

### Post by johnrhance on 2008-08-30
I did that, but it didn't have the Nvidia 9 series drivers. I'm downloading them from Nvidia's site right now, hopefully that will be the fix. You guys are amazingly helpful. If my Linux experience keeps being this great I'll be uninstalling Vista in no time.

---

### Post by johnrhance on 2008-08-30
Ok, I got the Nvidia drivers now. The file extension is .run. How do I open that? I'm sorry for such dumb questions. I'll learn fast though.

---

### Post by Partyboi2 on 2008-08-30
Boot into recovery mode and install build-essential package
```
sudo apt-get install build-essential
``` then change into the directory where you download the nvidia driver file to. Assuming you downloaded to your Desktop you would change directory by typing
```
cd /home/username/Desktop
```* change username to your username
then  to run the install script
32bit
```
sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```or for 64bit
```
sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```then follow the prompts
afterwards type
```
startx
```or reboot

> I'm sorry for such dumb questions. I'll learn fast though.There's never a dumb question, just a learning process :)

---

### Post by johnrhance on 2008-08-30
Recovery mode won't boot, and now normal won't either. It has been giving me this problem intermittently since I installed and I don't know what is causing it. I go into recovery mode once, and it said something about dskg or dpkg I can't remember.

---

### Post by Partyboi2 on 2008-08-30
Did you install the 64bit ubuntu iso or the 32bit iso?

---

### Post by johnrhance on 2008-08-30
The x64 version.

---

### Post by Partyboi2 on 2008-08-30
I would suggest trying to install the intel x86 version.

---

### Post by johnrhance on 2008-08-30
I will try the x84 version if this doesn't work for me. I just took out my primary drive and installed an old PATA one that I had. I formatted it completely and installed Ubuntu from the DVD that I made. It seems to have worked just like it should. I'm in Ubuntu right now, and the only problem that I notice is the resolution. I'm going to run all the updates now and see if that helps.

---

### Post by johnrhance on 2008-08-30
> **Partyboi2 said:**
> Boot into recovery mode and install build-essential package
```
sudo apt-get install build-essential
``` then change into the directory where you download the nvidia driver file to. Assuming you downloaded to your Desktop you would change directory by typing
```
cd /home/username/Desktop
```* change username to your username
then  to run the install script
32bit
```
sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```or for 64bit
```
sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```then follow the prompts
afterwards type
```
startx
```or reboot

There's never a dumb question, just a learning process :)

Okay, I finally made it into root and isntalled the build-essential. When I tried to run the Nvidia drivers, it said I was in runlevel 1 and that would cause problems. It said to switch to runlevel 3 ('telinit 3') and then run the drivers. How do I switch to runlevel 3, and what exactly is a runlevel?

---

### Post by johnrhance on 2008-08-30
Oh and when I'm in root and type 'telinit 3' it just boots into normal mode and I end up back in Gnome. Is it saying I should run the drivers while I'm here instead of root?

---

### Post by cmat on 2008-08-30
In the future the safest way to install the video drivers I find is to use Envy.

Type into the terminal:

```
sudo apt-get install envyng-gtk
```

Then after it`s installed goto Applications - System Tools - Envy.

It features painfree installation of video drivers. I`m posting this because I`ve never managed to install the nvidia drivers without crashing my xserver.

---

### Post by johnrhance on 2008-08-30
I installed and ran EnvyNG. It worked really well, but the resolution still isn't right. I'm using 1600x1024 at 57hz, when it should be 1680x1050 at 60hz. 1680 isn't an option though. I installed the Nvidia 173.14.12 drivers. Thank you so much for helping me get this far though I greatly appreciate it.

EDIT: Nevermind that post, the 1680 option was in the NVidia X server options menu. I'm running at 1680x150 at 60hz now! It seems like the refresh is lower than it normally is, but I can deal with that.

I wonder what I should install or do now that I'm in here?

---

### Post by cmat on 2008-08-30
Isn`t nVidia`s configuration application installed on your system? It should have taken the place of Ubuntu`s default display configuration applet. Not to mention it provides a very robust set of options. Either in Applications - Other, or in System.

---

### Post by johnrhance on 2008-08-30
^ Are you referring the the Nvidia X Server Settings in the System menu? That's what I used to change my res to 1680.

---

### Post by cmat on 2008-08-30
Oh I didn't see your post edit.

---

### Post by johnrhance on 2008-08-30
Any of you guys have any experience with Wine or Steam? I'd like to play some Counter-Strike through Linux. I isntalled Wine and Steam, but when I try to launch a game I get a general error.

---

### Post by johnrhance on 2008-08-31
Well guys, I finally realized my problem. The reason it wouldn't install is because (I think) my HDD is SATA, not IDE.

---

