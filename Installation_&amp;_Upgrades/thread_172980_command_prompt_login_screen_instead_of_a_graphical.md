---
title: "command prompt login screen instead of a graphical login!?"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by johnathan on 2006-05-09
According to the installation documentation, I'm supposed to be taken to a graphical login for ubuntu....

Instead, after configuring the base system I am getting a login screen similar to a windows command prompt... After logging in, i can't get to a desktop and I don't know what to do....

I used the default installation but I still get the screen.

I was wondering if anyone has a solution for this problem....

Thanks

---

### Post by bowsercake on 2006-05-09
I've had something similar happen to me on an older laptop.  I tihnk it happened in Ubuntu and in some other distros.  See if you can do an "expert" installation.  Its one of the options when installing I think.  Then make sure that you set the screen resolution correctly.  800x600 should work on pretty much everything.  It's possible that your screen resolution is set too high and Ubuntu can't display it.  I think that's what happened to me before.

---

### Post by scooper on 2006-05-09
Hard to tell exactly what's going on from a distance.  Are you getting 3-5 slow screen flashes (login prompt - blank - login prompt - blank ...)?  That would be a typical symptom of the X video driver refusing to start.  The best place to start is by looking at/and or posting the X log, /var/log/Xorg.0.log.  I think errors are lines with EE in them.  You could do something like:

grep \(EE\) /var/log/Xorg.0.log

You may need to be more thorough about reading the log to get the info you need.

If you got a new kernel and you have a proprietary video driver you may not have an automated process in place for updating the video driver when the kernel updates.  If so, try repeating whatever step(s) you took to get the video going originally.

Hope this at least gives you a starting point.

Cheers,
Steve

---

### Post by Monster_user on 2006-05-09
[QUOTE=scooper]grep \(EE\) /var/log/Xorg.0.log[/QUOTE]
Take carefull note of the spaces in that line. They are difficult to see, and many new users make the mistake of overlooking the spaces.

**grep**
Is the name of the program, it is basically a "search filter".

**\(EE\)**
Denotes the text to be filtered. In this case, only text that begins with "(EE)" will be shown.

**/var/log/Xorg.0.log**
Is the "Path" and the name of the file to be searched. It is the  'Xorg.0.log' text file, in the 'log' folder, which is in the 'var' folder, in the '/' or root. '/' being similiar to a 'C:\' drive in Windows.

/ -> var -> log -> Xorg.0.log

"grep\(EE\)/var/log/Xorg.0.log" will not work.

[b]It would be easier to check that file, using a Live CD. A version of Linux that boots from the CD. Ubuntu has LiveCD installers. Knoppix is the most famous by far. When you boot the LiveCD, look for the drive on the desktop, and click on it. You will have to double-click in Ubuntu. This will "Mount" the drive, and open it in the File Manager.

Then double-click the 'var' folder. In the 'var' folder, find '**Xorg.0.log**', and '**dmesg**'. Open them with a Text Editor, and search for Errors. Copy both of those to another disk, or post the results here. 

-------------------------------------------------------------------------------------------------------

Ignore what the previous poster said about kernels, and driver updates.

You could try getting online, if you use a LAN/Ethernet connection, and upgrading.

After you log in, try the following commands, and report the results.

**startx**
**gdm**
**synaptic**

**sudo apt-get update**
**sudo apt-get dist-upgrade**

---

### Post by sinkxdie on 2006-05-09
I think he just needs to type startx.
And isnt synaptic a graphical program, it wouldn't work at the "line"

---

### Post by johnathan on 2006-05-09
[QUOTE=bowsercake]I've had something similar happen to me on an older laptop.  I tihnk it happened in Ubuntu and in some other distros.  See if you can do an "expert" installation.  Its one of the options when installing I think.  Then make sure that you set the screen resolution correctly.  800x600 should work on pretty much everything.  It's possible that your screen resolution is set too high and Ubuntu can't display it.  I think that's what happened to me before.[/QUOTE]

If I reinstall ubuntu in expert, which options would I use for the mode..

Thanks

---

### Post by az on 2006-05-09
[QUOTE=johnathan]If I reinstall ubuntu in expert, which options would I use for the mode..

Thanks[/QUOTE]
Just boot into recovery mode (in the grub menu - press escape if you don't see it when you boot)

From recovery mode run

dpkg-reconfigure xserver-xorg

and at the end of the configuration selections, you will be prompted for monitor settings.

Then run

init 2

to get into the desktop.


If that doesn't work, go back and at the driver part, select "vesa" instead of what is the default.

---

### Post by johnathan on 2006-05-09
[QUOTE=azz]Just boot into recovery mode (in the grub menu - press escape if you don't see it when you boot)

From recovery mode run

dpkg-reconfigure xserver-xorg

and at the end of the configuration selections, you will be prompted for monitor settings.

Then run

init 2

to get into the desktop.


If that doesn't work, go back and at the driver part, select "vesa" instead of what is the default.[/QUOTE]

Didn't work...... I still got the command prompt like screen.

Ill install ubuntu in expert mode

---

### Post by az on 2006-05-10
[QUOTE=johnathan]
Ill install ubuntu in expert mode[/QUOTE]

You don't want to do that, and it won't fix your problem.


What happens when you run

sudo apt-get -f install

and then

sudo apt-get install ubuntu-desktop

from recovery mode?

---

