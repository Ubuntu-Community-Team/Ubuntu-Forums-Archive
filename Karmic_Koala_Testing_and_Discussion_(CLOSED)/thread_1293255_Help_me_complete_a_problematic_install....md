---
title: "Help me complete a problematic install..."
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-10-16
Here's the problem.  Downloaded and burned the BETA iso.  Works fine in 3 of my machines, but halts with a black screen on one of them.

The machine in question is an older ASUS A7V 600x board with an nVidia 8x AGP 6100 card.  It's got an AMD 2600+, 512MB memory, Seagate Barracuda SATA drive.

This machine runs Jaunty flawlessly quick, but I can't install Karmic.  I tested my install disc on several machines and it checks out fine.

I THINK it's probably a graphics issue (I don't know why I think this, I just do).

Any help would be greatly appreciated.

TIA

---

### Post by Don1500 on 2009-10-16
> **crjackson said:**
> Here's the problem.  Downloaded and burned the BETA iso.  Works fine in 3 of my machines, but halts with a black screen on one of them.

The machine in question is an older ASUS A7V 600x board with an nVidia 8x AGP 6100 card.  It's got an [SIZE="4"]**AMD 2600+**[/SIZE], 512MB memory, Seagate Barracuda SATA drive.

This machine runs Jaunty flawlessly quick, but I can't install Karmic.  I tested my install disc on several machines and it checks out fine.

I THINK it's probably a graphics issue (I don't know why I think this, I just do).

Any help would be greatly appreciated.

TIA
This is *probably* your problem. Do a search for AMD drivers and you'll see that this one is no longer supported. You'll also find out how to work around it. You probably won't have all the compiz functions you want, but it can be made to work.

---

### Post by VMC on 2009-10-16
> **crjackson said:**
> ... but halts with a black screen on one of them.

... but I can't install Karmic.  I tested my install disc on several machines and it checks out fine.

I THINK it's probably a graphics issue (I don't know why I think this, I just do).
TIA
I'm assuming the media check passed. You boot up using the livecd and at what point does it just present a black screen?

Have you tried the F6 options and tried using maybe nomodeset, or acpi=off?

Just in case Don't suggestion doesn't work out.

---

### Post by crjackson on 2009-10-16
> **VMC said:**
> I'm assuming the media check passed. You boot up using the livecd and at what point does it just present a black screen?

Have you tried the F6 options and tried using maybe nomodeset, or acpi=off?

Just in case Don't suggestion doesn't work out.

I haven't tried this since I've not had to use it since 7.04 I forgot how :)

I'll do this tomorrow and see what gives..

Oh, yes it passed media check. I downloaded / burned 3 different CD's all with the same result.  I also booted on different systems and they ran fine.

Jaunty runs fine on this machine, but when booting from a Live CD, it has to go to Low Graphics mode.  After the install, I activate the nVidia drives and no more low graphics.  It's perfect at that point.

EDIT:

The liveCD boots, I select language, I select the option to run the liveCD desktop without altering the system.  
The DVD drive starts loading files, I get the white UBUNTU emblem on the center of the screen.  Then as files continue loading the screen goes blank.  The drive continues to load files for quite a long time.  This finally the drive stops reading, the screen is blank and it stays that way for 30 minutes until I press the reset button.

---

### Post by crjackson on 2009-10-16
> **Don1500 said:**
> This is *probably* your problem. Do a search for AMD drivers and you'll see that this one is no longer supported. You'll also find out how to work around it. You probably won't have all the compiz functions you want, but it can be made to work.

Okay, I give up.  I did a google search and didn't find anything as indicated.

This system works perfectly with Jaunty and has full compiz functions.  It's very snappy with Jaunty.  What is it that now makes it incompatible in your estimation?

Can you give me a link to the information?

Thanks...

---

### Post by crjackson on 2009-10-16
> **Don1500 said:**
> This is *probably* your problem. Do a search for AMD drivers and you'll see that this one is no longer supported. You'll also find out how to work around it. You probably won't have all the compiz functions you want, but it can be made to work.

It just dawned on me.  Are you referring to the graphics card?  The 2600+ is an AMD CPU (Socket A).  I think you are referring to an ATI HD 2600 video card.

---

### Post by ranch hand on 2009-10-17
I would format your partitions with a Jaunty LiveCD so you can format to ext4.  Make a / and a /home partition.  Make a note of where they are.

Reboot to your Karmic LiveCD and instead of going to the desktop choose "install Ubuntu" in the menu.  Install the bugger.  If it does have the same problem we will worry about that then.

---

### Post by VMC on 2009-10-17
I just notice that you show two different optical drives. Is it too difficult to swap or best to remove one then try. If that fails swap out with the second drive. I know it sounds like work but worth it if you find your answer.

---

### Post by mc4man on 2009-10-17
If you haven't got this sorted by one means or another you could for the cost of a cd or two try the daily build or daily alternate cd (just used the daily D. on my laptop, went well, also very little  updating to do.

daily Desktop
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

daily alt.cd
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by crjackson on 2009-10-17
> **ranch hand said:**
> I would format your partitions with a Jaunty LiveCD so you can format to ext4.  Make a / and a /home partition.  Make a note of where they are.

Reboot to your Karmic LiveCD and instead of going to the desktop choose "install Ubuntu" in the menu.  Install the bugger.  If it does have the same problem we will worry about that then.

I tried that already.

The final release installed fine.

---

### Post by crjackson on 2009-10-17
> **VMC said:**
> I just notice that you show two different optical drives. Is it too difficult to swap or best to remove one then try. If that fails swap out with the second drive. I know it sounds like work but worth it if you find your answer.

You're looking at my profile signature rather than the system in the first post.  It's a different machine.

The machine in question only has 1 optical driver (pioneer DVD/CD ROM - Reader only).  It also only has one hard drive as described above.

---

### Post by crjackson on 2009-10-17
> **mc4man said:**
> If you haven't got this sorted by one means or another you could for the cost of a cd or two try the daily build or daily alternate cd (just used the daily D. on my laptop, went well, also very little  updating to do.

daily Desktop
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

daily alt.cd
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

I'll do this today.  Thanks for the links...

---

### Post by crjackson on 2009-10-17
> **VMC said:**
> I'm assuming the media check passed. You boot up using the livecd and at what point does it just present a black screen?

Have you tried the F6 options and tried using maybe nomodeset, or acpi=off?

Just in case Don't suggestion doesn't work out.

This didn't work.  Ubuntu emblem goes off the screen, then some text about setting up crypto disks or some such.

Then screen goes blank, drive stops and it just sits there.

Computer isn't LOCKED up though, because Ctrl+Alt+del shuts down Ubuntu and ejects the disc.  It prompts for the Enter key to reboot at that point and it works too...

---

### Post by crjackson on 2009-10-17
Tried the daily build, same problem.

However when I go directly to the install instead of booting to a desktop trial, the scrolling text says...

aufs au-xino_write:404:localchooser:xorg[########] IO, Error write failed

This pops up about every 2 seconds with 3 variations of the same error.

Any more ideas...

---

### Post by crjackson on 2009-10-17
Okay, so it turns out it IS the video card.  I installed an old GeForce2 card and the install proceeds normally.  

However when I install the 6100A card which works well in Jaunty, I can't boot Karmic.

Does anyone know how I can boot this thing with just the regular vesa generic driver and then perhaps try to install the restricted driver for the 6100A?

I'm getting closer but I don't want to be stuck with this GF2 card just so I can run Karmic.

---

### Post by happyhamster on 2009-10-17
Perhaps your problem is related to:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444824](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444824)
(even though that report is for an ATI card).

---

### Post by happyhamster on 2009-10-17
BTW, looks like our avatars are ready to fight each other... :D

---

### Post by ranch hand on 2009-10-17
So, you are installed?

If so rummage around in the files, if you can boot the LiveCD.  Check your /etc/X11/xorg.conf file.  If it exsites, rename the bugger by adding .OLD to the end of it.  It will no longer be used/// but be available if we need it.

Try to boot.

If it is not there you could try this.  Here is a copy of my file from when we were not able to boot because of the ATI card problem;
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
        Driver          "vesa"
        Option            "DRI" "0"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```
Just make the file and put this in it.  I have no idea if it will work.

With the card you have in there I think you have that file and all of us with ATI cards pretty much don't.  Well that isn't true but a lot of cards (my Radeon 2400 HD Pro for one) are not supported well.  I would try it on the generic and see if it works but I would try to pull the sucker and do away with the file if you have an ATI video controller.

---

### Post by crjackson on 2009-10-18
> **happyhamster said:**
> Perhaps your problem is related to:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444824](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444824)
(even though that report is for an ATI card).

Well, I tried setting the spread spectrum setting up to 256 as the bug report for the ATI card suggested and got no joy there.

I changed video cards to a OLD GF2 and did the install.  However upon putting back the newer 6100A card, I can't boot again.

---

### Post by crjackson on 2009-10-18
> **ranch hand said:**
> So, you are installed?

If so rummage around in the files, if you can boot the LiveCD.  Check your /etc/X11/xorg.conf file.  If it exsites, rename the bugger by adding .OLD to the end of it.  It will no longer be used/// but be available if we need it.

Try to boot.

If it is not there you could try this.  Here is a copy of my file from when we were not able to boot because of the ATI card problem;
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
        Driver          "vesa"
        Option            "DRI" "0"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```
Just make the file and put this in it.  I have no idea if it will work.

With the card you have in there I think you have that file and all of us with ATI cards pretty much don't.  Well that isn't true but a lot of cards (my Radeon 2400 HD Pro for one) are not supported well.  I would try it on the generic and see if it works but I would try to pull the sucker and do away with the file if you have an ATI video controller.

Well, I tried for hours today and resulted in no luck.  I had to get something working so I re-installed Jaunty which works well.  I'd really love to run Karmic on this machine but I don't think it's going to happen anytime soon.

---

### Post by ranch hand on 2009-10-18
I would keep trying the builds.  The support for more video is probably one thing not frozen.

If you try the RC and it doesn't work I would be discouraged but they will be updating this pretty heavily for the first month or so, I bet.

---

### Post by TheFinePrint on 2009-10-18
I have the same issue on a Dell Inspiron with nVidia graphics.

It ran Intrepid fine, and also no problems with the beta live CD.  However after installing Karmic it simply won't show anything but black screen once the white on black Ubuntu splash goes away.

I can log in to the second terminal with Ctrl+Alt+F2.

I managed to work around the issue:
Log in to second terminal.
$ sudo killall X11
$ startx

This will start a working X-session, but anything that required elevated privileges fails.  Not good enough;

$ sudo apt-get install xdm
In the old fashioned list select xdm to manage the X-sessions.  Reboot.

Now it works as intended, albeit with an ugly log-in window.

---

### Post by crjackson on 2009-10-18
> **TheFinePrint said:**
> I have the same issue on a Dell Inspiron with nVidia graphics.

It ran Intrepid fine, and also no problems with the beta live CD.  However after installing Karmic it simply won't show anything but black screen once the white on black Ubuntu splash goes away.

I can log in to the second terminal with Ctrl+Alt+F2.

I managed to work around the issue:
Log in to second terminal.
$ sudo killall X11
$ startx

This will start a working X-session, but anything that required elevated privileges fails.  Not good enough;

$ sudo apt-get install xdm
In the old fashioned list select xdm to manage the X-sessions.  Reboot.

Now it works as intended, albeit with an ugly log-in window.

so where in your estimation does the problem lie specifically?

---

### Post by crjackson on 2009-10-18
Wow, I can't play video files anymore now.  I have much better luck installing the alpha build and getting updates.

I'm almost ready to throw in the towel on karmic.  I'm having no luck at all.

---

### Post by TheFinePrint on 2009-10-18
> **crjackson said:**
> so where in your estimation does the problem lie specifically?

I think it's GDM-related, since XDM works.

However I also noted that the splash screen is different on my computer with the installed build, compared to that of the live CD.  Only the live-CD has the glowing bar in the splash screen.


I can't help with your video-issues though, I have handed over the affected computer to its owner.

---

### Post by fooman on 2009-10-18
crjackson,  just to let you know...i am having the exact same issue with black screen after the white ubuntu logo and the crypto drives things.  my video card is 8800gt.
i have tried 3 different cds and numerous tries on some usb sticks...all with same results.  tried a couple of daily builds as well as the regular beta .iso.   i figured its graphics related (tried safe graphics mode during install - same results),  but just haven't bothered trying a different card. 
been searching here and google for answers...nothing so far.:(

still using jaunty here.

---

### Post by crjackson on 2009-10-18
> **fooman said:**
> crjackson,  just to let you know...i am having the exact same issue with black screen after the white ubuntu logo and the crypto drives things.  my video card is 8800gt.
i have tried 3 different cds and numerous tries on some usb sticks...all with same results.  tried a couple of daily builds as well as the regular beta .iso.   i figured its graphics related (tried safe graphics mode during install - same results),  but just haven't bothered trying a different card. 
been searching here and google for answers...nothing so far.:(

still using jaunty here.

Thanks for the info, having mostly nVidia cards this was the last thing I expected.  I hope someone fixes this before the release, or at least finds a decent work around.

---

### Post by fooman on 2009-10-22
hey crjackson,  glad to report that i am posting this from the just released karmic-rc cd.  :)

finally....it works!  =D>

...off to install it now.

---

### Post by crjackson on 2009-10-22
> **fooman said:**
> hey crjackson,  glad to report that i am posting this from the just released karmic-rc cd.  :)

finally....it works!  =D>

...off to install it now.

Cool.  I'll download it right now and give it another spin on that machine.

Thanks for the tip.

---

### Post by crjackson on 2009-10-22
Sadly, the RC didn't work any better on that machine.  Looks like I'll be locked into Jaunty until someone figures out how to make this work.

---

### Post by crjackson on 2009-10-26
Any more ideas on this one?  I'd really love to put karmic on that machine.

---

