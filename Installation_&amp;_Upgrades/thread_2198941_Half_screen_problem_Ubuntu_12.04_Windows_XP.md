---
title: "Half screen problem Ubuntu 12.04 Windows XP"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by panthers65 on 2014-01-11
I'm trying to revive a very old desktop computer, it's slower than dirt and runs like crap on XP, even after clearing off everything I could. I had success getting an old laptop to work by installing ubuntu on it, but I"m having some trouble with this desktop.

Problem is whenever I try to book from the CD I made it runs all the way through to the "install or try ubuntu" fine, but the screen turns pixilated, the bottom half is some pink-ish tech jargon, and the mouse on the top part just appears as horizontal lines. 

I've tried several things, removing nvidia driver(came back the driver isn't installed, so not removed) 

I have tried both 12.04 and 13.10 and both come have similar results. Since my laptop installed with no bugs, I have no knowledge of troubleshooting or working with Ubuntu (I just found out how to enter the "command prompt" by pressing [ctrl] [alt] [F1]

Screen looks fine in both Bios, and when I remove the CD and boot Windows XP, so I know it's not a hardware issue. Can anyone help me diagnose this problem via dumbed down language?

tried to do a xorg.conf, and it says command couldn't be found.

edit: also I"ve read about the **gma500_gfx**[COLOR=#333333][FONT=Ubuntu Beta]. driver here ([/FONT][/COLOR][https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Live_.28Desktop.29_CD](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Live_.28Desktop.29_CD)) but honestly can't figure out where to go to download it, so I don't believe I've tried that yet.

---

### Post by fantab on 2014-01-11
[QUOTE=https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Live_.28Desktop.29_CD_12.04]The default Ubuntu 12.04 kernel works, but requires a  custom boot option. Without that option, you will either get a black  screen or distortions, such as top half of the screen only. 

[LIST=1]
[*]Switch to a console - Ctrl-Alt-F1 
[*]Restart X with 'sudo service lightdm restart' 
[/LIST]
That should bring you back to a functional graphical desktop, so that you can proceed testing or installing. [/QUOTE]

You should give it a try...

I used to have PC with gma500...but it ran Fedora-Xfce on it, and I had to do nothing more than install the distro.

Since what you have is "very old desktop computer", you should try Xubuntu, if your hardware is low in specs.

---

### Post by panthers65 on 2014-01-11
Thanks, tried that again, system doesn't seem to do anything after typing in "sudo service lightdm restart" just sits there with a flashing dash. 

also, managed to see one of the errors while loading, states "starting load fallback graphics devices [fail]"  if that tells you anything.

---

### Post by mikewhatever on 2014-01-11
Sounds like that desktop machine is too old for Ubuntu - remember, Windows XP was released in 2001. 
You probably don't have the specs, so, no point asking, but perhaps you could make it work with [Puppy linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm") or [Slitaz]("http://www.slitaz.org/en/"). There is even a release of Puppy that's based on 12.04.

PS: There is no chance whatsoever, that an old desktop has Intel's GMA500.

---

### Post by panthers65 on 2014-01-11
Bummer, Thanks for the info though.

Comp was built in 2004 by a local computer shop for a local business. 
S3 Graphics ProSavage DDR
Pentium 4 CPU 2.8 GHZ
2 gb ram

---

### Post by mikewhatever on 2014-01-11
Thanks, these are actually decent specs. My second guess is - the GPU can't handle Ubuntu's 3d requirements. Try Xubuntu instead.

---

### Post by steeldriver on 2014-01-11
I think all the *buntus will likely have issues with S3 cards - some suggestions here --> [http://ubuntuforums.org/showthread.php?t=2128715&page=3](http://ubuntuforums.org/showthread.php?t=2128715&page=3)

---

### Post by panthers65 on 2014-01-13
> **mikewhatever said:**
> Sounds like that desktop machine is too old for Ubuntu - remember, Windows XP was released in 2001. 
You probably don't have the specs, so, no point asking, but perhaps you could make it work with [Puppy linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm") or [Slitaz]("http://www.slitaz.org/en/"). There is even a release of Puppy that's based on 12.04.

PS: There is no chance whatsoever, that an old desktop has Intel's GMA500.


Thanks for the recommendation, I put puppy-linux on the machine and spent most the weekend figuring it out(actually the install itself was cake-walk, trying to figure out how to use the system). My first push into Linux was about a month ago with Ubuntu, so I'm definitely still trying to figure out and distinguish from Windows. This desktop is for my wife to do photo editing on with Gimp and my last project is just trying to get it organized so she can easily save her pictures from her camera to a folder on the desktop and then again to the NAS drive to backup. Trying to set it up so it is as close to windows file system as possible.

---

