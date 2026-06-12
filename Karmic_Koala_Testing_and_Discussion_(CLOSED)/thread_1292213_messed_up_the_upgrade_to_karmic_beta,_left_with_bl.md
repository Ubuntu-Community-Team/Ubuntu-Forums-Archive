---
title: "messed up the upgrade to karmic beta, left with blank screen and blinking cursor."
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kmaster228 on 2009-10-15
Hi all
yesterday i tried to update to karmic beta, it ran the distributional update command, started the upgrade. it went relitivley ok, so i left the comp on went to sleep, and in the morning i found that there was and error with the upgrade and it was finish but not all files could be downloaded, so i went to regular update manager, and a popup came asking to perform a partial distributional update, i clicked ok, a similair screen to the distribional one came up and started running.the partial upgrade ending in a minute, so went to update manager again and the same popup came for a partial upgrade, i closed it and went on to the regular update manager, there were alot of ticked updates, and some programs were unticked and i could not tick them, i installed things that way. then it told me to it had to restart some libraries and some programs related with those libraries had to be restarted, one of those programs were gdm, i clicked ok, then the screen restarted, and compiz was disabled and all my windows were weird and woudnt move and i could not get to a terminal. so i restarded to the computer, then i realized that i restarted in the middle of installing things, then when i booted back up, i was greeted with x errors and pulled to a root console, so i tried restarting the gdm, didnt work, then i tried re installing nvidia drivers, then it gave me the dpkg --configure -a error, so i ran that command and continued the installing the packages in root console, then i re tried gdm, and it worked, then i downloaded software center after reading a review, then upgraded some packages using that, then i tried update mangager again, it gave the same popup for a partial upgrade, i tried it again, it got to the installing packages part then gave me a dpkg error to do with open office something, it then closed. i then tried upgrade manager again, and closed the partial updgrade popup and installed some more ticked packages, but some of the packages again could not be ticked and were greyed out. so installed those. and got an error, but some of those packages were installed but not some others, i gave up and restarted my system and when i booted back in a was greeted with a black screen with a blinking cursor. i can type stuff in. no commands, i can get into a root terminal by typing ctrl+alt+delete, but after a few seconds of typing anything in, the computer restarts after the terminal gives some message, and thats my current problem, please help

---

### Post by dabl on 2009-10-15
When you boot it and it gets to the black screen, can you do Ctrl-Alt-F1 and get a login prompt?

If yes, log in there.  Then you probably need to stop GDM which is still trying to run.  Issue these (the first one might not work):

```
sudo /etc/init.d/gdm stop
```

```
sudo service gdm stop
```

Then do

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

When it is finished, you can try 

```
sudo service gdm start
```

This may or may not work -- it sounds like your system had a pretty rough experience and it's not possible to tell what all was damaged/misconfigured in the process that happened to it.

I don't know if your source list was correctly modified to add the karmic repositories or not -- if not, you might be better off to rescue your data, then make a Live or Alternate CD, and reinstall Karmic that way. 

Hope this helps!  :)

---

### Post by stlsaint on 2009-10-15
at the terminal can you access nautilus by typing:
```
nautilus
``` 
or have you tried re-installing the gnome DE by:
```
 apt-get install gnome-desktop 
```
or
```
apt-get install gnome-desktop-environment
```

if the above post nor this one works than yea you may want to consider backing up all data and doing a fresh install

---

### Post by kmaster228 on 2009-10-15
thank you very much, but when the blank screen with the blinking cursor appears, i can type, but not commands, and i can only get into a terminal by pressing ctrl+alt+del and i get into a terminal, but the system sends a restart signal as soon as i try typing commands. so i cant type any thing into a terminal, i have a live cd at hand and i have backed up my home directory, but i dont want to try a fresh install just yet. i had alot of packages and customizations on ubuntu that will take awhile to get back, im just wondering wheter i can restore my system, its probable just a missing package that causing it to work this way, if only i can get to a terminal, any advice on this?

---

### Post by dabl on 2009-10-15
Ctrl-Alt-Del is the hard reset command -- that is why it shuts down shortly after you press it.

I agree you need to get to a terminal, but I think you've got a hung X server blocking you.  Try Ctrl-Alt, Ctrl-Alt-Backspace, and Ctrl-Alt-F2, F3, etc.  If you can get a tty terminal, then you have a chance to rebuild the system.

At the cold boot, do you see a boot menu of any kind?  If you can tell when Grub is pausing, (after Stage 1 and before Stage 2), if you can press the Esc key you might get a chance to edit the kernel boot line.  If that is possible, then you want to backspace back to the "ro" and then add "single" so it will boot into Recovery Mode.

---

### Post by kmaster228 on 2009-10-16
im not sure if it is the same, but i have a recovery mode option below my usual kernel choice on grub, eg, if the defualt boot option is ubuntu 9.04 kernel ...15 then there is a recovery mode boot option just below. i tried that, it goes into verbose mode, says something about upstart error and a failed init.

---

### Post by kmaster228 on 2009-10-16
bump: please help, i really would like to recover my computer.
if no one has ideas for saving the system, then any tips for a fresh karmic beta live cd install? i can backup any files on the system through a live cd, i aldready backuped home folder. but any other tips? ive never done a fresh install before so can someone give me step by step instructions?

---

### Post by adder1972 on 2009-10-16
Do you run a nvidia graphics card? If so, check this forum for help.

Have you tried the recovery boot mode?  There are several options there.  I would start by just trying to get to a command line. 

You also mention a error message.  Please post it. Perhaps we can help you further along.

---

### Post by DougieFresh4U on 2009-10-16
Why are you doing 'partial update/upgrade'?

---

### Post by kmaster228 on 2009-10-16
@dougiefresh4u
i was trying a full upgrade to karmic beta from jaunty, it failed, then i tried a patial upgrade serveral times, read my first post for the whole story.
 @adder1972
yes i do have a nvidia graphics card, were u trying to give a link? there seems to be no link.
and ok let me try getting the error message
```

Boot from (hd0,4) ext3 e4585597-953b-4b87-997d-ec33c3957cf9
Starting up ...
19+0 records in
19+0 records out
kinit:name_to_dev_t(/dev/disk/by-uuid/8e2b5701/8e2b5701-acd2-478d-bda6-cd27e269b3db
kinit: No resume image, doing normal boot...
usplash: No usable theme found for 1280x1024
screen init failed

```
then there is just a blinking cursor, and i can only get to a terminal if i type in ctrl+alt+del, but only for a few seconds
and i can acess grub menu

---

### Post by sdowney717 on 2009-10-16
from grub boot to recovery console. if computer gives you a screen with an option to fix packages do that, otherwise try what the first responders suggested.

i had a problem after an update and this fixed my isue. it was an nvidia kernel issue.

also at console you can try sudo aptitude update, sudo aptitude upgrade or sudo aptitude dist-upgrade

---

### Post by adder1972 on 2009-10-16
Perhaps it is the 185-kernel-issue.  I was not able to restart after my upgrade (from 9.04). Had to install the 173-kernel-module, and things were OK again.

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1288302](http://ubuntuforums.org/showthread.php?t=1288302)


HTH


PS! Also, I had to boot in via the recovery menu option, I think.  Otherwise it was impossible to get any work done (flashing screen).

---

### Post by kansasnoob on 2009-10-16
I'd try starting in recovery mode. If the boot menu is hidden, which is common if you have only one operating system installed, and if this was an upgrade from Jaunty running legacy grub you should be able to view the boot menu by pressing the ESC key just after the system screen passes, whereas if it's a fresh install running grub2 you'll need to press the Shift key to display the menu.

Once you get the boot menu to show up you should see a recovery mode for each installed kernel, so choose to boot into recovery mode for the latest kernel, and let it run watching for text describing possible errors or problems. Make notes, being able to fully describe a problem is very helpful on the forums.

When recovery mode is finished you'll be dropped to a screen with several options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I'd choose netroot which is a shell w/networking and try to run the following commands (please make notes of any errors):

```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
sudo apt-get -f install
```

The latter in particular may recommend running other commands, and given you're situation I'd just do so. Then just:

```
sudo reboot
```

And see what happens. If it still fails I'd boot back into recovery mode and this time try xfix.

Also, do you have a Live CD? Any Ubuntu live CD should work, it needn't be a Karmic disc. If so it would probably be easier to work from the Live CD and mount and chroot the installation so you can copy-n-paste info to and from terminal.

---

### Post by kmaster228 on 2009-10-17
thanks alot for the response, but the problem is i can get into the legacy grub menu, i can edit boot options, i can go into recovery mode, but when i enter recovery mode, the screen goes verbose, and scrolls through alot of information very fast, and then im not given those recovery options, im just given a blinking cursor. and not even a terminal, i cannot commands into the terminal. i can however boot into a live cd.

im not sure if it was a nvidia problem, i am not certain, i may be wrong, but some of the things the person described in the tread u gave me do not apply to me, like he could get into a CLI i cannot.

my main problem here is i do not have a CLI to access

---

