---
title: "Major Gutsy Probs! Help Needed!"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by BnetTheAwesome on 2007-10-22
I upgraded my computer to Gutsy today and now it's worse than before. Tons of screen errors. Gnome isn't working right. Every time I start up it randomly goes through the loading text thing. I can't change my background because either a Gnome app is missing, or a non-Gnome app is running. I updated via the update manager, and it is messed up now. Slower than before. Any help would be appreciated.

---

### Post by BnetTheAwesome on 2007-10-22
Help Someone please. I have to be in failsafe. Normal isn't working at all. Please, someone help. Is there a package I need to get on synaptic? What do I need to do?

---

### Post by bruban on 2007-10-22
You haven't given me much to go on.

What type of computer do you have?

  - What components (cpu, video, monitor, etc)

How did you upgrade?

What version of Ubuntu did you have before you upgraded?

What version did you use to upgrade?

Do you take a backup of your data before upgrading? If not, how old is your backup?


Lets see where these answers take us...

---

### Post by BnetTheAwesome on 2007-10-22
Please help. I need help badly!

---

### Post by BnetTheAwesome on 2007-10-22
> **bruban said:**
> You haven't given me much to go on.

What type of computer do you have?

  - What components (cpu, video, monitor, etc)

(I'm sorry for not being tech savvy. All I know is that it is a Toshiba Satellite)

How did you upgrade?

(Update Manager. Not a terminal upgrade)

What version of Ubuntu did you have before you upgraded?

(Feisty)

What version did you use to upgrade?

(What do you mean what version? I guess the standard Gutsy)

Do you take a backup of your data before upgrading? If not, how old is your backup?

(No. My data isn't corrupted though. At least not in failsafe.)

Lets see where these answers take us...

Thanks for the help, or offer at least.

---

### Post by BnetTheAwesome on 2007-10-22
Anyone else?

Here is another thread where I got help to upgrade. Maybe the problem lies there:

[http://ubuntuforums.org/showthread.php?p=3592468#post3592468](http://ubuntuforums.org/showthread.php?p=3592468#post3592468)

---

### Post by bruban on 2007-10-22
OK. Sorry, but this is like walking through a mine field blind folded.

I'll try and help at least. Perhaps someone else can catch what I miss.


What do we know:

- Toshiba Satellite Laptop. Is this a fairly new laptop?

- you have upgraded to Gutsy from Feisty using the Update Manager.



Some more questions:

- Did you have any problems with the laptop and Ubuntu before upgrading?

- When you boot the laptop, you said that it is in Fail Safe mode. What error messages are you getting on screen?

- In Fail safe mode do you get a normal desktop displayed (ignoring the difference in screen resolution)?

---

### Post by bruban on 2007-10-22
> **BnetTheAwesome said:**
> Anyone else?

Here is another thread where I got help to upgrade. Maybe the problem lies there:

[http://ubuntuforums.org/showthread.php?p=3592468#post3592468](http://ubuntuforums.org/showthread.php?p=3592468#post3592468)





Did you follow the advise suggested before upgrading?

If so please post the contents of your /etc/apt/sources.list file.

---

### Post by BnetTheAwesome on 2007-10-22
> **bruban said:**
> OK. Sorry, but this is like walking through a mine field blind folded.

I'll try and help at least. Perhaps someone else can catch what I miss.


What do we know:

- Toshiba Satellite Laptop. Is this a fairly new laptop?

(No. A few years old)

- you have upgraded to Gutsy from Feisty using the Update Manager.



Some more questions:

- Did you have any problems with the laptop and Ubuntu before upgrading?

(Originally, I had problems with the upgrading for awhile. Once I had upgraded to Feisty via the update manager it worked perfectly. The only problem occurred occasionally when I would log in and the top and bottom menu bars where gone)  

- When you boot the laptop, you said that it is in Fail Safe mode. What error messages are you getting on screen?

(I log myself into failsafe because the login was screwy. I'll try to come back with the error message.)

- In Fail safe mode do you get a normal desktop displayed (ignoring the difference in screen resolution)?

(It works fine. But I want the other type to work too.)

Thanks for the help so far. I'm sorry I'm such a Linux Noob. I'm getting somewhat better.

---

### Post by BnetTheAwesome on 2007-10-22
> **bruban said:**
> Did you follow the advise suggested before upgrading?

If so please post the contents of your /etc/apt/sources.list file.

Yes. Here's the /etc/apt/sources.list.file

## All officially supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

 ## The source packages (only needed to recompile existing packages)
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

 ## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

 ## The source packages (only needed to recompile existing packages)
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

 #Beryl stuff

# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) gutsy main
# deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) gutsy main
# deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

# deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) gutsy eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) gutsy eyecandy

# deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

---

### Post by bruban on 2007-10-22
[Quote/]Thanks for the help so far. I'm sorry I'm such a Linux Noob. I'm getting somewhat better.[/QUOTE]



We all start that way.  Its good to see that you are persevering. Its the best way to learn.

---

### Post by bruban on 2007-10-22
Your apt sources are OK.

---

### Post by bruban on 2007-10-22
OK, now I would like you to give me the info that you have in the following sections of the file:

   /etc/X11/xorg.conf 


Sections:

- Device
- Monitor


An example of what may be included is below. Note that most PCs will be different dependent on the components that are in each PC.

Let me know what you have in your file.

Thanks,

Bruce:

==============

Section "Device"
        Identifier      "nVidia Corporation NV18 [GeForce4 MX 4000]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

=================================

---

### Post by BnetTheAwesome on 2007-10-22
It's now working in Gnome normal kinda. The internet is slow and has screen problems when I scroll.  And random black bars appear out of nowhere.

---

### Post by BnetTheAwesome on 2007-10-22
> **bruban said:**
> OK, now I would like you to give me the info that you have in the following sections of the file:

   /etc/X11/xorg.conf 


Sections:

- Device
- Monitor


An example of what may be included is below. Note that most PCs will be different dependent on the components that are in each PC.

Let me know what you have in your file.

Thanks,

Bruce:

==============

Section "Device"
        Identifier      "nVidia Corporation NV18 [GeForce4 MX 4000]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

=================================

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

---

### Post by bruban on 2007-10-22
Before we do anything, do you have an Ubuntu 7.10 Live CD? You may need to use it to get access to your laptop if we have a problem later on.

If not, download one from:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


- After burning the .iso to a cd, reboot with off  the LiveCD and test to make sure that it works OK.

- If your graphics work OK on the LiveCD boot, can you post the same two sections of the file:

etc/X11/xorg.conf


Sections:

- Device
- Monitor


thanks,

Bruce

---

### Post by BnetTheAwesome on 2007-10-22
> **bruban said:**
> Before we do anything, do you have an Ubuntu 7.10 Live CD? You may need to use it to get access to your laptop if we have a problem later on.

If not, download one from:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


- After burning the .iso to a cd, reboot with off  the LiveCD and test to make sure that it works OK.

- If your graphics work OK on the LiveCD boot, can you post the same two sections of the file:

etc/X11/xorg.conf


Sections:

- Device
- Monitor


thanks,

Bruce

I'll try to work on that, but I'm pretty busy.

Also, what's the difference between failsafe and normal. I'm running perfectly in failsafe. If there is any large downsides, tell me.

---

### Post by BnetTheAwesome on 2007-10-22
Another problem: Blender won't work.

I think some packages must have failed to install in the upgrade for the GUI.

---

### Post by bruban on 2007-10-23
Lets tackle one problem at a time.

Let me know when you have the results of the etc/X11/xorg.conf after booting from the LiveCD.

Bruce

---

### Post by BnetTheAwesome on 2007-10-23
I think I have a solution to it. I can do the Live CD but I don't think this could harm my computer and could be an easy fix. I remember when I first logged in and it messed up, various warning messages came up saying various GNOME programs could work or weren't downloaded correctly. I thought I had pressed a "Cancel" button at the time, but now I realize that it was a "Delete" button. If someone has all the GNOME additions in Gutsy, I can download them in Synaptic. Or at least check. It feels like an incomplete download and it is something wrong with the desktop environment.

---

### Post by bruban on 2007-10-23
This sheds a different light on things. I was assuming a graphics mis-config. There are several issues around at the moment that it could have related to.


If you continue like this you'll be chasing your tail for a long time with much frustration.


My advice to you is:

- backup any personal data to an external device.

- boot up via the 7.10 Live CD.

- Read the included doco on installing Ubuntu 7.10

- Install Ubuntu 7.10. formatting your Linux partitions as part of the process.

- Restore your personal data from the external device.


You should then have a nice stable installation of Ubuntu 7.10


Have fun

Bruce

---

### Post by BnetTheAwesome on 2007-10-24
UPDATE---

I got someone to look at my computer and we found out the error: a Driver problem.

Here is the instructions I followed:

"OK, this might take a bit. Lack of direct rendering seems to be a common problem, so it may just be a Gutsy bug that is unsolvable as of now, but I'll give it a shot.

Try all of these AFTER reading the entire e-mail; restart after each and tell me the results:

First of all, open a terminal and type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

In the Modules section of your xorg.conf, comment out the DRI line (put a # at the beginning of the line)
Re-enable DRI and change Driver "ati" to Driver "radeon"
Disable DRI again
Re-enable DRI and change Driver "radeon" to Driver "vesa"
Disable DRI again
Go to System->Administration->Restricted Drivers Manager and enable fglrx, ATI driver, or whatever they call it

It's somewhat likely that one of these will cause your X server to die completely, but that's not a problem. After boot, press Ctrl-Alt-F1 to go to a full-screen terminal. Then, type sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf. This will restore your computer to the original state."

I went up to the step re-enabling by DRI and changing the driver to vesa when I got this error when I booted up:

"[     11.035797] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait..."

I followed the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

It didn't really work for me so I went into failsafe and changed back to "ati" and it worked good again. I added "noapic" with no hyphens after "#defoptions=" and it still isn't helping the problem.

Any ideas? Also, to help me for future reference, can someone explain the following terms:

GRUB
APIC
BIOS
DRI
X server
Xorg.Conf
cp

---

### Post by BnetTheAwesome on 2007-10-25
Anyone have anything to add? What driver/xorg.conf problem do I have? What's the solution?

---

