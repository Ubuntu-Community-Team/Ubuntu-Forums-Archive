---
title: "Probelms following upgrade to 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Oscar_Islix on 2010-05-02
I have just upgraded to Ubuntu Lucid 10.4 and am now having several problems.

1.  The mouse and/or keyboard locks when I start up.  This can sort itself out without changing anything on the 3rd attempt.  As I have no mouse or keyboard all I can do is switch off the PC - not advisable I think

2.  Now I am trying to read a CD or DVD and I get the message "no medium found on /sr0"

Please can anyone help? I am reasonably computer literate but not very ubuntu literate so any help will be appreciated.

Many thanks

Oscar Islix

---

### Post by jplinderman on 2010-05-02
> **Oscar_Islix said:**
> I have just upgraded to Ubuntu Lucid 10.4 and am now having several problems.

1.  The mouse and/or keyboard locks when I start up.  This can sort itself out without changing anything on the 3rd attempt.  As I have no mouse or keyboard all I can do is switch off the PC - not advisable I think

2.  Now I am trying to read a CD or DVD and I get the message "no medium found on /sr0"

Please can anyone help? I am reasonably computer literate but not very ubuntu literate so any help will be appreciated.

Many thanks

Oscar Islix

I experienced a similar problem during numerous adventures with the install DVD.  Both my mouse and keyboard are connected via USB.  When I plugged in a serial mouse, I never had any problems with it.  The USB mouse was often, but not always, functional when the serial mouse was plugged in.  Before I tried the serial mouse, I starting doing circles with the mouse and bouncing up and down on the shift key while the DVD was loading, to ensure activity on the USB ports.  I think this improved the probability that the mouse and keyboard would be functional, but it's pure superstition, and I may be reading patterns into random events.  Try the serial mouse/keyboard, if that's an option.  -- jpl

---

### Post by sanderd17 on 2010-05-02
Could you try a fresh install? You don't have to install it (yet), just downloading the iso, making an usb stick and testing if the things you say here still happen.

If this goes all right than it's no problem with your computer, just a piece of software having problems to find and apply the settings you chose in the previous release.

---

### Post by Oscar_Islix on 2010-05-02
Thanks.  I'm using a serial mouse and keyboard so not sure about that.  And yes I do the same keep moving the mouse on startup to see if I can keep it going.

Any ideas on the cdrom problem?

---

### Post by sanderd17 on 2010-05-02
Kan you read the cd/dvd with Gparted? If so, how is the partition called?

---

### Post by leodp on 2010-05-06
Hi,
on this thread:
[http://ubuntuforums.org/showthread.php?t=1468165&highlight=lucid+keyboard&page=2](http://ubuntuforums.org/showthread.php?t=1468165&highlight=lucid+keyboard&page=2)
they suggest to turn off the ACPI at boot.
You can also check if it is working in recovery mode:
"Only thing that worked fine (at least i can type and use my mouse) is under ubuntu 10.04 recovery mode (choose option from grub menu when pc starts) and then from the options given choose low graphics mode just for this session."
Then edit grub menu

Alternatively try the other solutions posted here:
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/513932](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/513932)
-remove package mouseemu
-sudo dpkg-reconfigure console-setup
Your keyboard shouuld run if you boot into recovery mode, console only as root 

Send a feedback please, I also have the same issue. I'll check later.

Ciao, Leo

---

