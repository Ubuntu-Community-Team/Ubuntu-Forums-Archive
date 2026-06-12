---
title: "xorg.conf"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dbyjazz on 2009-10-25
Using 9.10 and I need to manually change my screen resolution like so..

```
Subsection "Display"
    Depth 24
    Modes "1280x768"
    Virtual 1280 768
EndSubsection
```

my current resolution is at 1600x1200

I've tried:

gksudo gedit /etc/X11/xorg.conf

dpkg-reconfigure xserver-xorg

sudo dpkg-reconfigure -phigh xserver-xorg

Is there any other way I can change my screen resolution manually? I have to do it that way because in 9.04 when I would try it through Display Preferences the screen would go crazy and I would have to do a full re-installation of Ubuntu.

-Thanks in advance

---

### Post by VMC on 2009-10-25
Have you tried just "System> Preferences >Display", and altering the Resolution?

---

### Post by kansasnoob on 2009-10-25
There is no xorg.conf now.

I've been lucky with that, not so much with sound.

Sort of feels like Sid!

---

### Post by dbyjazz on 2009-10-25
> **VMC said:**
> Have you tried just "System> Preferences >Display", and altering the Resolution?

Like I said, when I tried it that way in 9.04 it would completely screw up and I would have to do a full re-installation. I'm looking for all the options I have before I try that again.

---

### Post by autocrosser on 2009-10-25
I need a custom xorg.conf because I use SLI nVidia cards & Xorg can't configure them yet....So I'm including my xorg.conf for you to look at. The new system configures everything on the fly--so you only need to have the things you don't want auto-config.

Just remove the .txt from the end & edit it the way you want--put it in the normal place---/etc/X11

---

### Post by dbyjazz on 2009-10-25
> **autocrosser said:**
> I need a custom xorg.conf because I use SLI nVidia cards & Xorg can't configure them yet....So I'm including my xorg.conf for you to look at. The new system configures everything on the fly--so you only need to have the things you don't want auto-config.

Just remove the .txt from the end & edit it the way you want--put it in the normal place---/etc/X11

so when I open xorg.conf in terminal the the editor comes up I just need to paste that in there and change anything I need to and everything will go smoothly?

---

### Post by autocrosser on 2009-10-25
Delete what you don't need & paste in what you do...then reboot---worst case you don't have a X start--if that happens, reboot with a LiveCD & mount your Karmic partition--go in as root & delete or move the created file & then reboot your system....

---

### Post by dbyjazz on 2009-10-25
> **autocrosser said:**
> Delete what you don't need & paste in what you do...then reboot---worst case you don't have a X start--if that happens, reboot with a LiveCD & mount your Karmic partition--go in as root & delete or move the created file & then reboot your system....

well the problem is I don't know what I need because there is nothing in the file. It actually doesn't exist I believe. I tried just typing my screen resolutions like I did in my first post and it pretty much wiped everything for some reason and I had to re-install.

---

### Post by Longinus00 on 2009-10-25
Have you tried changing screen resolutions in a live cd? See if you get the crash there? Why do you get a crash anyway? What sort of hardware are we talking about exactly? You can also use xrandr to change resolutions.

---

### Post by NRDNick on 2009-10-25
```
Section "Monitor"
	Identifier	"Monitor0"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1920x1200" "1680x1050"	"1600x1200" "1440x900" "1280x1024" "1024x768"
	EndSubSection
EndSection
```

copy this part to your xorg.conf and take out the other resolutions and put in the one you want the same way it is shown there. "1280x768" Save the file and close it/the editor. Then log out and back in to test it out. If it doesn't work you can always do as autocrosser suggested and boot into a live CD. But I find it easier to just boot into a shell by selecting the recover kernel entry in GRUB. Once in a shell you can just ```
sudo nano /etc/X11/xorg.conf
``` 

I agree that you should at least give the gui menu a try before trying to edit your xorg.conf file. Also which drivers/video card are you using?

Edit: Yea I agree that bug sounds odd, I can't see why you would have needed to completely reinstall the OS. Other than sheer frustration of course . . .

---

### Post by Yumi on 2009-10-25
To my understanding Karmic has no xorg.conf any more. 

The xorg.conf only exists when you install nVidia drivers. Only with the nVidia drivers is it required. But then, System - Administration - Display does not work, instead there is a menu item NVidia XServer Settings for this. And only with the NVidia driver can you edit the xorg.conf.

In my view the question is **how to add screen resolutions to the new, non nVidia and non xorg.conf methode employed in Karmic**.

Michael

---

### Post by dbyjazz on 2009-10-25
are you sure this will work? Because the guys in launchpad say xorg.conf doesn't even exist

I also tried xrandr and it bugged out again and I rebooted. Thankfully, unlike in 9.04 the screen wasn't wacked out when I logged back in.

---

### Post by NRDNick on 2009-10-25
Yes xorg.conf isn't necessary in karmic unless you need to do some customizing to your X server. Like setting up dual monitors or turning off the proprietary Nvidia splash screen.

Can you tell us what hardware and drivers you are using please? This will help us help you. Also have you tried using the display settings GUI to set your resolution yet? It's the one under System/Preferences/Display.

---

### Post by dbyjazz on 2009-10-25
K when I tried changing the resolution like that the screen freaked out and I have to reinstall..

but here are my specs

Processor: Intel Celeron M Processor 370
Operates at 1.5 GHz, 1 MB L2 Cache
and 400 MHz FSB

Memory: 512 MB DDR2

Video: S3 Graphics UniChrome Pro IGP
As much as 64 MB shared VRAM

Hard Drive: 60 GB HDD, 4200 RPM

---

### Post by autocrosser on 2009-10-25
Look--why don't you try this:```
#Custom Xorg

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Subsection "Display"
                          Depth 24
                          Modes "1280x768"
                          Virtual 1280 768
        EndSubsection
EndSection

Section "ServerFlags"
    Option            "DontZap"    "False"
EndSection
```And see what it will do. All this "fluff" in this thread should be like this:

1. Xorg now configs "on the fly"--UNLESS there is a xorg.conf in /etc/X11
2. IF there is one--Xorg will use the values defined

And post your Xorg.0.log if it is not working

---

### Post by dbyjazz on 2009-10-25
> **autocrosser said:**
> Look--why don't you try this:```
#Custom Xorg

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Subsection "Display"
                          Depth 24
                          Modes "1280x768"
                          Virtual 1280 768
        EndSubsection
EndSection

Section "ServerFlags"
    Option            "DontZap"    "False"
EndSection
```And see what it will do. All this "fluff" in this thread should be like this:

1. Xorg now configs "on the fly"--UNLESS there is a xorg.conf in /etc/X11
2. IF there is one--Xorg will use the values defined

And post your Xorg.0.log if it is not working

I hope this works because last time I just tried adding in the subsection with my preferred display and when I rebooted it was doing something weird. Just a black screen and white text. Almost like Terminal 'derek@derek-laptop ~$' and it would let me type.

---

### Post by autocrosser on 2009-10-25
Like I said--if you have a non-working Xorg--just reboot with a LiveCD (easiest way to edit), mount your Karmic install & move or delete the created xorg.conf--that returns you to square-one....Then MAKE SURE you copy the CURRENT xorg.0.log BEFORE you reboot again--I would need to see it to find your problem.

As for "subsection"---you MUST follow xorg editing convention---section  then subsection---endsubsection then endsection

---

### Post by dbyjazz on 2009-10-25
> **autocrosser said:**
> Like I said--if you have a non-working Xorg--just reboot with a LiveCD (easiest way to edit), mount your Karmic install & move or delete the created xorg.conf--that returns you to square-one....Then MAKE SURE you copy the CURRENT xorg.0.log BEFORE you reboot again--I would need to see it to find your problem.

As for "subsection"---you MUST follow xorg editing convention---section  then subsection---endsubsection then endsection

ok sweet. sorry how do you boot with a LiveCD?

---

### Post by autocrosser on 2009-10-25
Make sure that "boot with CD" is first in your BIOS & if Xorg b0rks--boot the Live & when you get to desktop, open a Terminal--type "mkdir /media/a" (without quotes)--then "mount /dev/sda1 /media/a" (sub your "real" partition that has Karmic installed if sda1 is not it)--then nav to /etc/X11 & rename or delete the xorg.conf--remember--you might need to sudo for these commands....after that & before you reboot--grab the Xorg.0.log from /var/log & post it here.

---

### Post by dbyjazz on 2009-10-25
> **autocrosser said:**
> Make sure that "boot with CD" is first in your BIOS & if Xorg b0rks--boot the Live & when you get to desktop, open a Terminal--type "mkdir /media/a" (without quotes)--then "mount /dev/sda1 /media/a" (sub your "real" partition that has Karmic installed if sda1 is not it)--then nav to /etc/X11 & rename or delete the xorg.conf--remember--you might need to sudo for these commands....after that & before you reboot--grab the Xorg.0.log from /var/log & post it here.

oh my gosh man it worked!!! :D thank you so much. If I could I'd give you a cookie lol

---

### Post by nanog on 2009-10-25
dbyjazz, please file a bug.

---

### Post by dbyjazz on 2009-10-25
> **nanog said:**
> dbyjazz, please file a bug.

I already did last night to Touchpad and they said it isn't a bug so they filed it as a question.

---

### Post by autocrosser on 2009-10-25
> **dbyjazz said:**
> oh my gosh man it worked!!! :D thank you so much. If I could I'd give you a cookie lol

That is what happens when you follow the steps ;)   I've been working with xorg from the start & xfree86 before that---about 10/11 years now. You should file a report on Launchpad & include your xorg.0.log with it--the new Xorg is not failing very often, but when it does--the results are not good.

---

### Post by dbyjazz on 2009-10-25
> **autocrosser said:**
> That is what happens when you follow the steps ;)   I've been working with xorg from the start & xfree86 before that---about 10/11 years now. You should file a report on Launchpad & include your xorg.0.log with it--the new Xorg is not failing very often, but when it does--the results are not good.

ok sweet thanks again! you know your stuff quite well.;-)

---

### Post by dino99 on 2009-10-25
mine, which detect all the resolution:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by autocrosser on 2009-10-25
Yes--that was the old default that was phased out about half-way thru development---when did you install or are you using a upgraded Jaunty?

And dbyjazz--it's all in a days work--you're welcome.

---

### Post by Longinus00 on 2009-10-25
> **dbyjazz said:**
> I already did last night to Touchpad and they said it isn't a bug so they filed it as a question.

You shouldn't file a bug asking how to make a xorg.conf. Your bug should be something to the extent of "changing resolutions makes computer unbootable". File it against the xorg s3 driver.

---

