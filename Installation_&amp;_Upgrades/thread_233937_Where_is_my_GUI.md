---
title: "Where is my GUI?"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by moogii on 2006-08-10
I've installed it and but when i start there is no GUI.

Why ? It just start then asks me login info.

I think it just switches to start to Rescue system mode instead KDE.r GNOME or whatever GUI ? Any way to recover it? 

May have to reinstall it again  I assume.

i could log in but what command do I have to fix this ?

---

### Post by Jagot on 2006-08-10
Does the command startx do anything?

Failing that, try running this command to see if you can configure the graphics:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by az on 2006-08-10
What cd did you use to install and how did you install?

What happens when you log into your computer using text mode and run

sudo apt-get install ubuntu-desktop
?

That will install the rest of the desktop system in case you made a mistake and only installed the base (text-only) system.

Alternatively, your graphics card may have been misconfigured.  That also can be fixed without re-installing.

---

### Post by moogii on 2006-08-11
Thank you guys .Quick respond .

I dont remember where I downloaded the iso,but I hope that wasn't the server edition with no GUI.I'm sure it was the 5.10

Anyway I downloaded new version. I'll give it a go then i'll see What'll happen '' Thank you

---

### Post by moogii on 2006-08-11
> **Jagot said:**
> Does the command startx do anything?

Failing that, try running this command to see if you can configure the graphics:

```
sudo dpkg-reconfigure xserver-xorg
```


hey I actually tried your suggestion .

it says Package 'xserver-xorg' is not installed and no info available

My PC is an old 1.. intel pentium 2. I tried the live CD .It was working good....
So shall I reinstall it ?

---

### Post by moogii on 2006-08-11
> **azz said:**
> What cd did you use to install and how did you install?

What happens when you log into your computer using text mode and run

sudo apt-get install ubuntu-desktop
?

That will install the rest of the desktop system in case you made a mistake and only installed the base (text-only) system.

Alternatively, your graphics card may have been misconfigured.  That also can be fixed without re-installing.



I found out what CD was (actually its a DVD )..
It is ubuntu 5.10....2.6.12-9-686

Is that the right CD for me? .My PC is very old ..:roll: 

Intel pentium II..

May be I need i586 or 386.I assume ..
by the way i tried your suggestion

it says dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem


ok ..So even I dloaded. tried to install the 6.10.

Unfortuntely it didnt recognise my display driver and it gives me 640x800 resolution which is not suitable my screen so I couldn't go throught install ..because it was too big I couldn't see the buttons on my screen ..

is there any way to install it without GUI.? text mode I mean..

---

### Post by christhemonkey on 2006-08-11
Try the Alternate install CD.

Is the new version of the old text style installer.

Did you try running sudo "dpkg --configure -a" (without the quotes)?

---

### Post by moogii on 2006-08-11
> **christhemonkey said:**
> Try the Alternate install CD.

Is the new version of the old text style installer.

Did you try running sudo "dpkg --configure -a" (without the quotes)?

I've just tried the suggestion .list of items executed here.

All lines started "Setting up....xxxxxxx..."

Then stops at the shell start $ sighn.

Then I reboot.. Then everyuthing is the same ...ubuntu loads

kind of 'ok' comfirmation texts ...Then no GUI ..Just shell logon 

  

Also I tried i386 ubuntu 6.06

It's kind of mess .There was no text mode .Had to run the CD as live CD order to install it.Have to run live CD first.then install within the runnig GUI ..No Direct Install .it's sucks

Thanks

---

### Post by az on 2006-08-11
> **moogii said:**
> I've just tried the suggestion .list of items executed here.

All lines started "Setting up....xxxxxxx..."

Then stops at the shell start $ sighn.

Then I reboot.. Then everyuthing is the same ...ubuntu loads

kind of 'ok' comfirmation texts ...Then no GUI ..Just shell logon 


That fixed the installed package probelms.  However, not all of the packages are installed.  You need to run

sudo apt-get install ubuntu-desktop

to install the remaining packages you need.



  > **moogii said:**
> 

Also I tried i386 ubuntu 6.06

It's kind of mess .There was no text mode .Had to run the CD as live CD order to install it.Have to run live CD first.then install within the runnig GUI ..No Direct Install .it's sucks

Thanks

It's actually a lot faster that way.

---

### Post by moogii on 2006-08-12
Mister AZZ.

I eventually installed it.You're awesome....;) ;) 

It was lot qiucker indeed. 

Now i'd like to uninstall it 

Not because of Ubuntu.. Trust me

because I'm unable to find display driver for it.matrox graphics PCI. (my screen resolution is too bad) 

ESS Audio driver as well......These are very old ...No driver for Unix system......


So I want install it on my laptop....


I need to know what command Do I use to Uninstall it safely from my hard drive ?

Cos I installed it alongside on my WINDOWS 2000..

Thanks your help and time ...

---

### Post by az on 2006-08-12
> **moogii said:**
> Mister AZZ.

I eventually installed it.You're awesome....;) ;) 

It was lot qiucker indeed. 

Now i'd like to uninstall it 

Not because of Ubuntu.. Trust me

because I'm unable to find display driver for it.matrox graphics PCI. (my screen resolution is too bad) 

By default, Ubuntu uses the maximum color depth.  If your card has something like 4 megs of ram, you end up with high color but low resolution.

Boot into recovery mode and run

dpkg-reconfigure xserver-xorg

and go through the config.  When you see color depth, pick 15-bit (or try 16-bit).  That should help

run

init 2
to get into the desktop from recovery mode.



> **moogii said:**
> 

ESS Audio driver as well......These are very old ...No driver for Unix system......

[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

sudo modprobe snd-es18xx
or try
snd-es1688
> **moogii said:**
> 
So I want install it on my laptop....


I need to know what command Do I use to Uninstall it safely from my hard drive ?

Cos I installed it alongside on my WINDOWS 2000..

Thanks your help and time ...

You can just boot the live cd, and delete the partition.  Then extend the windows partition back over the free space.  You will need to fix your mrb with the fixmbr windows tool.

---

### Post by moogii on 2006-08-12
Thank you .all your effort mate.

actually your suggestions are pretty accurate and simple.
.
I did all what you suggested.

Now I've installed it on my laptop which has 120 GB hard drive .So i dedicated 20 GB for UBUNTU.Works fine, I'd like to know how to compiling from the source..It's really pain .That was the reason I dumped my SuSE 2 years age .It seems UBUNTU more simle I hope 

I'm gonna start another treat about this issue later when i get time .

Thank you AZZ . 8) :wink:

---

