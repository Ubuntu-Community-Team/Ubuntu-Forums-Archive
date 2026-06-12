---
title: "New intrepid X needs critical fix"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forcecore on 2008-10-09
[http://ubuntuforums.org/showthread.php?p=5898494#post5898494](http://ubuntuforums.org/showthread.php?p=5898494#post5898494)
[http://ubuntuforums.org/showthread.php?p=5918077#post5918077](http://ubuntuforums.org/showthread.php?p=5918077#post5918077)

Both of these are affected with same X bug, every time i need specify driver then it works well so please fix X display driver loader sensor that it detects right display or loads vesa if no good drivers available.

I can confirm it affects 6 computers including my 2, it needs critical X graphics detector fix.

---

### Post by taavikko on 2008-10-09
You've reported those bugs?
You submitted enough information to triage those?

---

### Post by forcecore on 2008-10-09
in beginning i tried to submit but now there is no need because everyone can understand that X is little "drunk" that she cannot select driver automatically.

---

### Post by plun on 2008-10-09
I can confirm this and I have a ongoing bug about this.

But..  I must "poison" my PC to get it working again.

Something is broken with Jockey, detection and a driver install.

Also ABI versions for the kernel maybe ???

dmesg also looks strange.


A clean PC with just a broken install is needed for a new bug report.

---

### Post by forcecore on 2008-10-09
BTW even safe graphics mode do not work, safe graphics mode should use xorg.conf file that has driver set "vesa" to force load desktop whatever hardware is like Windows does in beginning.

Where i can see daily changelog when is fixed that xorg or that jokey clown thing.

---

### Post by plun on 2008-10-09
> **forcecore said:**
> BTW even safe graphics mode do not work, safe graphics mode should use xorg.conf file that has driver set "vesa" to force load desktop whatever hardware is like Windows does in beginning.

Where i can see daily changelog when is fixed that xorg or that jokey clown thing.

Well... "clown thing"...   have you filed any bugs about this ?

This is a "minefield" for a developer and they are just doing this great !!

We are also running a TEST version...it should be bugs !

---

### Post by forcecore on 2008-10-09
filed but developers changed status invalid because of no log.

---

### Post by RAOF on 2008-10-09
The correct response to which would be:
a) Saying so on Ubuntuforums
b) Reading the linked wiki page: [https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting) and attaching the information needed to fix your problem, or
c) Both (a) and (b)
?
:)

---

### Post by wgrant on 2008-10-09
> **forcecore said:**
> filed but developers changed status invalid because of no log.

Then provide the log and reopen the bug. We can't fix bugs where people give no information.

---

### Post by forcecore on 2008-10-09
i do not know how to log and solution is to: 1. fix graphic bug detection sysem 2. give option to load vesa driver 3. fix safe graphics mode to use vesa 4. if you are expert find computer that fails to load and send logs to developers.

Here is list of my tested computer errors:

1: Radeon 3870 - monitor did not accept signal-
2: SiS mirage 3+ - Gnome failsafe
3: Geforce 2 - Gnome failsafe
4: some very old intel chip - Blank screen
5: unknow chip - Gnome failsafe
6: stoneage 500mhz laptop - Gnome failsafe again

And all these bugs i fixed with:
cd /etc/X11
sudo nano xorg.conf

Section "Device"
Identifier "Configured Video Device"
Driver "vesa" (radeonhd was for 3870)

---

### Post by wgrant on 2008-10-09
> **forcecore said:**
> i do not know how to log and solution is to: 1. fix graphic bug detection sysem 2. give option to load vesa driver 3. fix safe graphics mode to use vesa 4. if you are expert find computer that fails to load and send logs to developers.


Or you could attach the logs [as described](https://wiki.ubuntu.com/X/Reporting), so we can fix it without awful workarounds. That's the best and likely easiest way to do things.

---

### Post by cariboo on 2008-10-09
Just as a point of interest, all log files are in /var/log.

Jim

---

### Post by plun on 2008-10-10
Well, I understand that all users just wants a working PC.


Maybe OT but this is a **real "clown thing"**.

[http://connect.microsoft.com/](http://connect.microsoft.com/)


If you ever been involved in MS testing this is just a dream with a living community and all bugs are open for everyone.


andrewsomething's sticky thread is also a great start point

[http://ubuntuforums.org/showthread.php?t=896777](http://ubuntuforums.org/showthread.php?t=896777)


Good Luck !

---

### Post by wgrant on 2008-10-10
> **plun said:**
> Well, I understand that all users just wants a working PC.

Yes, and we do too. But we can't fix problems where the only information we have is "X is broken".

---

### Post by plun on 2008-10-10
> **wgrant said:**
> Yes, and we do too. But we can't fix problems where the only information we have is "X is broken".

Yup...

OT

Maybe we also needs more automagic tools for bugs...

"Apport" for hardware, I have seen several QA dicussions about this.

Something for Jaunty...:)

---

### Post by forcecore on 2008-10-10
do ubuntu saves logs automatically in /var/log if not i cannot save if i do not have display in beginning?

---

### Post by ronacc on 2008-10-10
the logs are saved automaticly , you might want to take a look at /home/<you>/.xsession-errors   also .

---

### Post by forcecore on 2008-10-10
ok i try to save logs from desktop after i select xorg driver manually but what log files do you require? from var/log folder or xsession-errors

Developers should atleast fix safe graphics mode to use Driver "vesa" or this option is pointless.

---

### Post by nanog on 2008-10-10
The relevant section from the link wgrant provided above:

(Please click on the link -- there is alot of additional information on how to report these types of bugs.) 

 
X crash, lockup, freeze, exit, or doesn't start/shutdown
	

Detailed description of problem

Get a full backtrace (X/Backtracing)

List any versions you tried that did not have this issue

Steps to reproduce

How complete is the X failure?
+ Does ctrl+alt+f1 take you to a console?
+ Does ctrl+alt+backspace restart X?
+ Does mouse pointer still move?
+ Does the keyboard LED come on when hitting the CAPSLOCK key? + Can you ssh into the system from another computer?

/var/log/Xorg.0.log

/var/log/Xorg.0.log.old

~/.xsession-errors

---

### Post by forcecore on 2008-10-10
now here is my try to send 2 pc logs, if they fail then i am out of mind, i cannot get other logs because friens computers is in city far away but i assume all is affected by chip detector bug. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-chips/+bug/272814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-chips/+bug/272814)

---

### Post by mindwarp on 2008-10-10
I am suffering from this too, and I can't get my logs off because my nics are intel nics which are now blacklisted.  Joy.

---

### Post by forcecore on 2008-10-10
this is network card probmem but i had video display problem. btw it should be fixed now in daily releases.

---

### Post by UbuWu on 2008-10-10
> **plun said:**
> 
Maybe we also needs more automagic tools for bugs...

"Apport" for hardware, I have seen several QA dicussions about this.

Something for Jaunty...:)

Some automagic already exists, running:

ubuntu-bug xorg

Will file a bug on X for you and automatically include the most useful log files.

---

### Post by UbuWu on 2008-10-10
> **mindwarp said:**
> I am suffering from this too, and I can't get my logs off because my nics are intel nics which are now blacklisted.  Joy.

The e1000e driver is no longer blacklisted, this has been fixed (I think you need this one?). It might be hard to get the updates though without a working network connection. You could download a daily cd of the text installer, you can use that as a source in synaptic.

---

### Post by forcecore on 2008-10-16
Can anyone tell where i can find detailed bug progress of this, daily live 15 is still that bug. btw safe graphics mode do not work too with daily 15.

---

### Post by dentharg on 2008-10-16
Well, I've installed Intrepid Kubuntu yesterday. 

Indeed it had problems with detecting driver. So what I did?

sudo apt-get into the works:
remove all nvidia related stuff (nvidia-177-glx, nvidia-177-kernel-source, etc).
remove dkms (!!!)
install dkms
install nvidia-177-glx, nvidia-177-kernel-source

put nvidia driver by hand into xorg.conf

chmod 777 /dev/nvidiactl

Works perfectly now.

---

### Post by caryb on 2008-10-16
My Kubuntu after todays update only displays black screen after kdm logon screen.


Cary

---

### Post by forcecore on 2008-10-16
i am doing that hand entering too but in lot of computers it is annoyng and even safe graphics mide do not work too, someone atleast should fix safe graphics mode that it enters Driver "vesa" in xorg.conf

---

### Post by caryb on 2008-10-17
I have fixed mine of sorts! I had to torn off the eye candy:confused: Anyhow the fix was on the Kubuntu forums [http://kubuntuforums.net/forums/index.php?topic=3096859.msg150246#msg150246]("http://kubuntuforums.net/forums/index.php?topic=3096859.msg150246#msg150246")


Cary

---

### Post by inportb on 2008-10-17
That thread also suggested using XRender instead of OpenGL for applying eyecandy :) (though I don't think Compiz can do anything using XRender ;p )

---

### Post by forcecore on 2008-10-19
this topic is not related to compiz and effects it is related to this bug that is serious erros detecting display and safe graphics mode is not working too:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-chips/+bug/272814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-chips/+bug/272814)

---

### Post by forcecore on 2008-10-24
Still that radeon bug exist in RC but atleast now esprimo v5535 shows that gnome low graphics mode but it will continue successfully to desktop and THANKS alot Ubuntu development team that you have fixed safe graphics mode, now it will load successfully my radeon desktop too.

THANKS once more again.

---

