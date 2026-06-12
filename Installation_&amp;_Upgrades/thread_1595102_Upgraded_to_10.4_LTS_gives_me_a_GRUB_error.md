---
title: "Upgraded to 10.4 LTS gives me a GRUB error"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2010-10-12
I finally upgraded my EeePC from 9.10 to 10.04, well I wanted to.

My Ubuntu installation is on /sdc (SD card)

During the upgrade I went to sleep (9 hours) and when I came back my mouse (bluetooth) did not work anymore.

After finishing the upgrade it rebooted.
My screen shows now:

> GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue>

What am I going to do to fix that?

---

### Post by drs305 on 2010-10-12
Take a look at this thread I wrote it up last night. Don't overlook the first options before going to the grub rescue section.

[Grub Rescue Mode Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

Since you are the original poster you can ask questions here if needed, or in the other thread - your choice.  ;-)

---

### Post by ELMIT on 2010-10-13
I came one step further!!! I purged grub2 grub-pc and reinstalled it.

Now I can boot and come to the graphical desktop in beautiful black (!) with a white (grey) bottom bar, which includes day and time and the power button.

On the upper right part is a message:
Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator.

But this guy (me) has no clue what to do yet.

I tried in another terminal to install gnome-power-manager which went successfully, but after rebooting I end here again.


FYI:
It is an EeePC, where I have installed and now upgraded the system on the SD card (/dev/sdc).
Using Grub to boot from Asus Linux works fine too.
On the graphical terminal I can do nothing, but on the other text terminal I have access, even to the network.

I used already sudo apt-get update which found me some language packages to update. 


Any idea how to fix that?

---

### Post by ELMIT on 2010-10-13
Read some other messages and tried:

* boot from older kernel
* two quickly messages: cannot mount unknown to /dev 
* see the bottom bar with language / keybpard and session selection

* Login screen appears
* Again the warning about the Gnome power manager

* logged in
* Message appears:
   A program is still running
   Unknown
   Not responding

   [Lock Screen] [Cancel] [Logout Anyway]

I choose [Logout Anyway]

* login screen disappears, Error box disappears
* Screen flashes white/brownwith a brighter box in the upper left corner where I can recognize two arrows (up and down)


So what am I going to try next?

---

### Post by ELMIT on 2010-10-13
latest status:
I changed the /etc/default/grub file the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xxxx"

where I tried xxxx as

xforcevesa
i915.modeset=1
i915.modeset=0
nomodeset

but nothing gave me more than the black screen.
I tried both sudo update-grub and sudo update-grub2

Has anybody an idea what to try next?

---

### Post by drs305 on 2010-10-13
If you don't get any responses in this thread, since you solved your Grub problem you might want to open a new thread with a title concerning your current problem.

While a kernel option in the grub config line may be the solution, the people who know the solution are more likely users knowledgeable about Gnome Power Manager and the desktop issue. Some readers who know a lot about our current issue won't read a thread with a title about Grub, and the number of responses may also cause others to bypass the thread.

I'll follow your posts and offer solutions if I think of something.

---

### Post by ELMIT on 2010-10-13
what is the difference of update-grub and update-grub2 ?

---

### Post by oldfred on 2010-10-13
None.

Actually I drilled down and checked when it first came up and update grub2 just calls update-grub. 

#!/bin/sh -e
exec update-grub "$@"

And update-grub just calls another mkconfig:

#!/bin/sh -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"


In another directory on grub legacy is aother grub-update for grub legacy.

---

