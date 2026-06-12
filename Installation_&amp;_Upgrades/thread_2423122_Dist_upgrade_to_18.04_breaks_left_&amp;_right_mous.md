---
title: "Dist upgrade to 18.04 breaks left &amp; right mouse clicks and shortcut keys"
date: 2019-07-17
forum: Installation &amp; Upgrades
---

### Post by ajana on 2019-07-17
Thank you in advance to anyone who reads this and offers any suggestions that might help.
I have been working for close to 3 days to find a solution and not being a   'power user' I have no real way of getting around without the mouse.
We use this machine to run 2 businesses and are basically dead in the water =(
      
We upgraded our Dell Precision M6800 from ubuntu 17.? to 18.04.2
Now I can't click anything left or right click on either the touchpad or wireless mouse.
      
When the ubuntu login screen pops up, mouse clicks work fine, but as soon as I have logged in they stop.
      
If I press CTRL + ALT + F1, the login screen reappears and mouse clicks work again, but as soon as I log in again, they stop.
      
CTRL + ALT + T  does not work to open a terminal.
      
ALT + F2  does not work to open a quick terminal command box.
      
Basically I can't get to a terminal window =(
      
After many hours of frustration trying many different things I walked   away for some time, when I came back the screen saver (black screen) had   activated, and when I woke it up, then I discovered both these  shortcut key commands to open a terminal worked, but still no mouse  clicks.
Rebooting the computer repeats the same issues, so I have to wait at   least 10mins for the screen saver to activate to enable the shortcut   keys to open a terminal.
      
The laptop is in a dock that feeds 2 external monitors and a wired keyboard.
I disconnected it from the dock and rebooted so it was just running the laptop's own hardware, no change.
I have tried many other suggestions from the forums including (not necessarily in this order):

    1.)
Did software update to ensure any more changes available are applied.
      
2.)
ALT + CTRL + F6
Sign in
ALT + CTRL + F7
      
3.)
ALT + CTRL + F1
ALT + CTRL + F8
ALT + CTRL + F7
      
4.)
sudo ubuntu-drivers autoinstall
      
5.)
Switched my video drivers from nouveau to nvidia & updated drivers to recommended 418
      
6.)
sudo apt-get install --reinstall inputattach
      
7.)
sudo apt-get --purge autoremove xserver-xorg-input-all && sudo apt-get install xserver-xorg-input-all
      
8.)
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
      
Did a reboot after trying each suggestion, no change.
      
There have been no hardware changes or software programs added before the dist upgrade.
      
The machine has 16GB of RAM and has a nvidia Quadro K4100M video card.
      
I am a terminal novice so happy to try commands to get more info but will need the full command please.
      
Hoping someone will be able to help, thanks in advance to anyone with some suggestions.

---

### Post by ajana on 2019-07-17
Have since also tried...
  

 9.)
sudo apt-get update && sudo apt-get --auto-remove purge  xserver-xorg-input-synaptics && sudo apt-get install  xserver-xorg-input-libinput
 
10.)
Removed the nvidia video drivers and set it back to nouveau with:
   sudo apt install nouveau-firmware
   sudo apt purge nvidia-driver-418
   sudo apt autoremove
   sudo apt install xserver-xorg-video-nouveau

problem still persists =(

---

### Post by ajana on 2019-07-18
Please help! almost 3 days solid working on this trying anything I can find or think of.
Our business is at the mercy of getting this machine usable again.

Latest information...

I ran:
[FONT=courier new] [COLOR=#696969]xinput -list[/COLOR][/FONT]
it said my mouse is: id=11

then I ran:
[COLOR=#696969][FONT=courier new] xinput -test 11[/FONT][/COLOR]
Then I clicked left, middle & right buttons, it showed:
[COLOR=#696969][FONT=courier new]button press 1
button release 1
button press 2
button release 2
button press 3
button release 3
[/FONT][/COLOR]
Seems the clicks are registering.

Also another odd behavior I observed:
if I go: CTRL + ALT + F1 to take me back to the login screen, I then log in (and as mentioned all the mouse clicks work fine there so I can even click the login button!), but when I come back to the desktop, I can see a mouse pointer on 2 of the 3 screens. Only one moves as I move the mouse, and the other one disapears once the moving pointer enters the screen with the fixed pointer.

2 things both trying to display the mouse pointer?

---

### Post by ajana on 2019-07-18
I noticed there were still some nvidia drivers hanging around, so I have now completely removed the nvidia drivers with:
[COLOR=#696969][FONT=courier new]sudo apt-get purge nvidia-*
sudo apt-get purge nvidia*[/FONT][/COLOR]
and reinstalled back to the nouveau drivers.

I also completely removed the libinput drivers and reinstalled the synaptic drivers.
Then I had no keyboard or mouse at all =(
Managed to reboot and open a console at the login screen and reinstalled the libinput drivers to get my keyboard and mouse move back, phew!

Still no mouse clicks or shortcut keys (until 10mins later the screen saver comes up, then when back at desktop I get just the shortcut keys back).

Help! Anyone out there?

---

### Post by ajana on 2019-07-19
Other things I have since tried...

Fix Broken Ubuntu OS...
[COLOR=#696969][FONT=courier new]$ sudo rm /var/lib/apt/lists/lock
$ sudo rm /var/lib/dpkg/lock
$ sudo rm /var/lib/dpkg/lock-frontend
$ sudo dpkg --configure -a
$ sudo apt clean
$ sudo apt update --fix-missing
$ sudo apt install -f
$ sudo dpkg --configure -a
$ sudo apt upgrade
$ sudo apt dist-upgrade[/FONT][/COLOR]

Old trick some people found worked...
[COLOR=#696969][FONT=courier new]$ sudo metacity --replace[/FONT][/COLOR]
(said it wasn't installed anyway)

Remove any fragments of unity desktop...
[COLOR=#696969][FONT=courier new]$ sudo apt purge unity-session unity
$ sudo apt autoremove[/FONT][/COLOR]

Remove old version of gnome-tweak-tool...
[COLOR=#696969][FONT=courier new]$ sudo apt-get purge --auto-remove gnome-tweak-tool[/FONT][/COLOR]
(said it wasn't installed anyway)

Still no mouse clicks and broken shortcut keys =(

---

### Post by ajana on 2019-07-19
Ok, 4 days later this worked!!!

  Force reset of all gnome settings
[COLOR=#696969][FONT=courier new]$ dconf reset -f /org/gnome/[/FONT][/COLOR]  

I have lost all my customisations and have some work to do to get  things back to how they used to be, but at least I didn't have to do a  fresh install and lose all the many programs we have installed and setup  over the last year or 2.

I have been slowly re-instating the customisations one by one to see what breaks it. Seems this is the culprit:
 Tweaks > Extensions > Workspaces to Dock
So I will likely not be able to use multi-workspaces. Looks like it has broken mouse clicks etc for others too...
[https://github.com/passingthru67/workspaces-to-dock/issues/134](https://github.com/passingthru67/workspaces-to-dock/issues/134)

---

### Post by tonygerber on 2019-10-01
Not sure if this will help others, but I had the same problem with a stock standard corded mouse on 18.04.   All of the workarounds listed in this thread were tried and failed to fix the issue.
Finally stumbled across the solution ... at least in my case.
I had the mouse connected to my laptop (HP 14s-dk0020) via a USB hub.  Removing the mouse from the hub and plugging it into the laptop chassis directly fixed the problem.  It was that simple.

The very same mouse and USB hub worked perfectly fine on my previous (older) HP laptop running 14.04, fwiw.

> **ajana said:**
> Ok, 4 days later this worked!!!

  Force reset of all gnome settings
[COLOR=#696969][FONT=courier new]$ dconf reset -f /org/gnome/[/FONT][/COLOR]  

I have lost all my customisations and have some work to do to get  things back to how they used to be, but at least I didn't have to do a  fresh install and lose all the many programs we have installed and setup  over the last year or 2.

I have been slowly re-instating the customisations one by one to see what breaks it. Seems this is the culprit:
 Tweaks > Extensions > Workspaces to Dock
So I will likely not be able to use multi-workspaces. Looks like it has broken mouse clicks etc for others too...
[https://github.com/passingthru67/workspaces-to-dock/issues/134](https://github.com/passingthru67/workspaces-to-dock/issues/134)

---

