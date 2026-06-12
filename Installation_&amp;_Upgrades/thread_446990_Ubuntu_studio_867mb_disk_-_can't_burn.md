---
title: "Ubuntu studio 867mb disk - can't burn"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by zob on 2007-05-17
Hi

I'm looking forward to trying the new Ubuntu Studio. So today I downloaded the image, checked the md5sum. Until here everything went fine. As you probably now the Ubuntu Studio image has a bit unhandy size - 867 MB. So I went for a DVD, started op Nero 6 - burn image file...
However Nero 6 told me to feed it a CD. I made the swap. Now Nero complained that the size of the image was to big for my CD.
So conclusion. In Nero (windows xp), I can't burn the image. I tried alcohol 120, which was able to burn it to DVD, but left me with a malfunctioning copy. It can't be read in windows. It does boot though, but it only gets me to somewhere where it says that the CD!! (though it's a DVD) can't be mounted.

Anyone got a clue?? Please?? (I've got few DVD's left)

---

### Post by atlfalcons866 on 2007-05-17
is it an iso image

---

### Post by zob on 2007-05-17
Yes it is.

---

### Post by atlfalcons866 on 2007-05-17
try this from [http://www.ubuntustudio.com/downloads](http://www.ubuntustudio.com/downloads)


Ubuntu Studio Repo

Here's how to get access to our repo.

From a terminal run these 2 commands:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Packages in our repo:

    * ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
    * ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
    * ubuntustudio-desktop - Makes up our base desktop install.
    * ubuntustudio-audio - Ubuntu Studio audio package
    * ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
    * ubuntustudio-graphics - Ubuntu Studio graphics package
    * ubuntustudio-video - Ubuntu Studio video package
    * ubuntustudio-artwork - UbuntuStudio themes and artwork
    * ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
    * ubuntustudio-icon-theme - UbuntuStudio Icon theme
    * ubuntustudio-look - Ubuntustudio look (metapackage)
    * ubuntustudio-session-splashes - Ubuntu Studio Session splashes
    * ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
    * ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
    * ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
    * ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
    * usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
    * wired - Audio creation free software for Linux

---

### Post by zob on 2007-05-17
So you suggest that I just "upgrade" my ubuntu with the repos from ubuntu studio?
Thanks. I probably will.
But someone must have tried to burn ubuntu studio to a CD/DVD. What media did you burn it on? What program? Did anyone try Nero under windows?

---

### Post by Snoose on 2007-05-17
I burned it with CloneCD's (under WinXP) trial version to a DVD... works fine.

---

### Post by zob on 2007-05-18
Thanks. I'm might give that a try. Though I might also just stick to the idea of adding repos. I guess it's more or less the same result.

---

### Post by madman91 on 2007-05-19
This might be a little offtopic. But are those packages 32bit only?

---

### Post by stereo3D on 2007-05-19
I burned the DVD with Nero on a Windows Vista machine. Burned onto a DVD+R disc.
These are dumb questions but...  if you were using the "Smart" user friendly interface did you select DVD at the top center menu? Did you select to burn an image (ISO)? 

I know you probably made the right selections in Nero. :)

---

### Post by zob on 2007-05-20
Hi Stereo3D.
Yes, I checked that. I never found out what I was doing wrong. But now I've installed a regular Ubuntu, and I plan to ad the Ubuntu Studio repos soon. However, though we don't have to solve that here, next problem now seems to be to make my EMU 0404 sound card work. But I can see in productionforums.com that someone is working on it. So maybe soon.

And madman91.
Yeah. It's 32 bit. If you want a linux DAW (which at least could be one of the reasons that you're interested) and if you want in 64 bit, you could have a look at this [http://64studio.com/](http://64studio.com/) though imo ubuntu studio looks better.

---

### Post by madman91 on 2007-05-20
> **zob said:**
> Hi Stereo3D.


And madman91.
Yeah. It's 32 bit. If you want a linux DAW (which at least could be one of the reasons that you're interested) and if you want in 64 bit, you could have a look at this [http://64studio.com/](http://64studio.com/) though imo ubuntu studio looks better.

Actually I just wanted the purrrttty backgrounds and login screen :)

---

### Post by dizzyheadmusic on 2007-05-22
I had success with InfraRecorder: [http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

---

### Post by mr.mattoid on 2007-05-23
Had the same problem burning the ISO to DVD.
Snoose is right, Zob, CDClone did the job.

---

### Post by thomasyen on 2007-07-27
Hello,

After some testing, these were my results(on Windows XP):

Nero 6.3.1.26: Requested that I put in a CD-R instead of DVD
Alcohol 120%: Requested that I put in a CD-R instead of DVD
InfraRecorder: Crashes when I try to burn disk
CDClone: Works perfectly!

Conclusion: Use CDClone (although it only has 21 days of trial)

---

