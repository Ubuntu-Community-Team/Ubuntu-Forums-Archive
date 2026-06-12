---
title: "upgrade has hung!"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by okhowaboutthisusername on 2010-11-27
10.04 -> 10.10 network install

A dialog popped up stating "Modified Configuration File". When I clicked the select list of options it opened, but everything immediatly hung. I can still get the dock to pop up, and I can open the Applications, System, etc. menus (although any windows I open are not movable). But the upgrader windows are not responding in any way at all. To make things worse, a window I opened was in front of this dialog and, when I closed it, the dialog became completely blank.

Earlier, I came back to the computer to find that the ttf-something-or-other licence prompt had stopped everything. However, it was BEHIND the upgrader window. Luckily, I could still click the "agree" checkbox and hit return to allow things to proceed. This looks similar, except this window is front and centre and not responding (and now not showing anything, either).

Any advice? Unplug the box and download an ISO?

---

### Post by okhowaboutthisusername on 2010-11-27
Bonus Round:

Is it possible to "break into" another terminal session? I seem to recall there is a way. What I mean is, the upgrader can echo it progress in a built-in terminal window. While that's completely inaccessible, I can open a new terminal and see ps output. Is it possible to switch things such that I can give input to the upgrader's process from this new terminal?

---

### Post by okhowaboutthisusername on 2010-11-27
I figured out that what I was after to attach to an already-running process was gdb. However, fiddling with that wasn't working (er ... I couldn't figure it out). Then I took a closer look at the upgrade window's terminal:

```
GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.1/gobject/gsignal.c:3081: signal name `depressed' is invalid for instance `0x1be8480' at /usr/share/perl5/DebConf/FrontEnd/Gnome.pm line 120 <GEN0> line 8
```The last little bit may be incorrect as the upgrade window is immovable and the terminal opens to just below the bottom of the screen.

Anyway, what I did was kill the Perl process, which immediately caused a pop-up telling me that php5-cli couldn't be installed. I clicked OK and everything the upgrade on its way.

**UPDATE:**

I just looked over and saw another pop-up. Again, it was asking whether to replace php.ini (perhaps for the Apache module this time). Of course, I didn't touch the options select list and hit "forward". That seemed ok.

And, as I was typing that ... Another dialog, this one telling me the upgrade couldn't be installed, my system will be in an unusable state, blah, blah.

Wonderful. I'm hoping the msg is bogus. Time to reboot. And, perhaps, download an ISO.

---

### Post by okhowaboutthisusername on 2010-11-27
**Oh, for the love of ... !!!**

So, we left off at, "Your system is f*cked". I click "OK" and another window opens, this one looking like Anaconda ca. 1999, showing me the same options that crapped out on me the first time. I select the 1st option, to install the new config, and *voila*, another pop-up saying upgrade is complete! WTF?!Hold on while I re-boot ... mmm, looking good. Yup. Upgraded.

I'll file a bug in the morning.

---

### Post by garvinrick4 on 2010-11-27
I use in first code box sda5 change that to your sda# of your linux install. In a live cd (install cd and choose Try Ubuntu) open a terminal and copy and paste this code below:
Remember must use your sda# (just hit enter after copy and pasting in terminal) Get internet working in Live Cd:

```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt 


``````
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
apt-get -f install
``````
update-grub
``````
exit
```                      ```

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
  
```Now boot into grub menu and choose your Ubuntu install:

---

