---
title: "Trying to install Ubuntu 7.04 with unsupported ati graphics"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by atsab on 2007-09-12
Hi all, i was just wondering if anyone can help me with my problem.
im trying to install Ubuntu 7.04 32bit on my new laptop

processor: AMD Turion 64 X2 tL-56 1.80GHz
RAM:2gig
Gfx: ATI Mobility Radeon HD 2600

i choose the start and install option when the cd has booted, and everything goes ok.
After for a few minuets im told that Ubuntu cant start the gnome display manager and leaves me at the command prompt.

I did some digging arround on the problem and i think its because ATI has poor relations with the open source community, my ATI hardware probably isnt supported.  My question is how can i get my unsupported card to work so i can continue with my installation?

---

### Post by dgtldaydrmr on 2007-09-12
I had a very similar problem.
Are you using the live CD to install?
I couldn't get that disc to work right on my laptop.

Try the alt install CD.
Also if it boots with no video like a blank screen after install and first reboot... 
The following worked for me:

[http://ubuntuforums.org/showthread.php?t=549213](http://ubuntuforums.org/showthread.php?t=549213)

---

### Post by atsab on 2007-09-12
Thanks for the help,
 il give the alt install a go now and let you know the results

---

### Post by atsab on 2007-09-12
Ok iv installed Ubuntu 7.04 using the alt cd, but the Gnome display manager still fails to start. 

i then tried "sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver; then: startx"

and still it fails to start with this error:

Caught signal 11. server aborting 
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" 
after 0 requests (0 known processed) with 0 events remaining.

Can anyone offer any more ideas on what i could try to get my gnome display manager up and running?

---

### Post by Pumalite on 2007-09-12
Are you able to install the whole system and then only the xserver fails?

---

### Post by sloggerkhan on 2007-09-12
You should try the new ati driver. [http://ati.amd.com/support/drivers/linux/linux-radeonhdd.html](http://ati.amd.com/support/drivers/linux/linux-radeonhdd.html)

I think without that driver your card pretty much won't work.

I'd download the file, right click on it and make it executable, and then open a terminal in the same directory and do a 
$sudo ./ati-driver-installl....
Once it installs,
then reboot and do a
$sudo dpkg-reconfigure xserver-xorg
if your gui doesn't load.

---

### Post by atsab on 2007-09-13
Thanks for the help guys, 
i am able to install the whole system it is only the xserver that fails to load.
iv downloaded the new ati drivers on a different  pc and transfered it to my usb memory stick, to use with my laptop.
Now the only problem i have is how do i mount the usb stick from the command line so i can access the driver?

---

### Post by Pumalite on 2007-09-13
You could also try:
sudo apt-get update
sudo apt-get install xorg-driver-fglrx

---

### Post by atsab on 2007-09-13
Ok i managed to mount the usb stick and install the latest ati drivers, i started the xserver and all i got was a blank screen?? i wasn't able to get to the command line by pressing Ctrl+Alt+F1 which i found a bit strange.
So i reinstalled ubuntu and again i had the same problem, gnome display managaer couldnt load, so again i mounted the usb drive and copied the ati driver installer to my system and installed it.

 This time after the install i didn't restart i just ran sudo dpkg-reconfigure xserver-xorg command, the program ran and i selected all the default choices but when it came to choosing the monitor the screen once again went blank and i wasn't able to get to the command line.
Is the problem that my laptop`s monitor isn't suported or am i doing somthing else wrong,
can any one help please

---

### Post by Pumalite on 2007-09-13
Did you try my method of installation?. Because, according to Synaptic, that particular driver is supposed to support your card.
You also need to install:
sudo apt-get install linux-restricted-modules-2.6.20.5-16,29 ( or whatever is appropriate to your kernel
If you want a GUI:
sudo apt-get install restricted-manager

---

### Post by atsab on 2007-09-13
Hey Pumalite, 
i decided not to try the "sudo apt-get update" as i figured i would have to connected to the internet for this to work, and i have no idea how to set up my wireless connection via the command line. Could you point me in the right direction to do this and i will try your method of install
thanks for your help

---

### Post by Pumalite on 2007-09-13
In any installation is better to be wired to a LAN or such, preferably through a router that gives you DHCP ( instant connection!!) Later you can configure your wireless.

---

### Post by sloggerkhan on 2007-09-13
I want to make sure these are the steps you've taken:
Install feisty.
Get new ati driver.
Navigate to its directory.
sudo ./ATIDRIVER NAME (Version 8.41.7+)
reboot
sudo dpkg-reconfigure xserver xorg
choose the fglrx driver.
run: $sudo aticonfig --initial
.$startx or reboot

You are then left with a BLACK screen, as opposed to being dropped back to a command line?

If this is the case (and if you have a laptop) it's possible the the display is defaulting to an external monitor instead of the LCD, and you will need to either hook up an external display to switch which screen is in use, or manualy specify it in xorg.conf.

If GDM is still dying with errors, then it's a different matter.

---

### Post by enchesss on 2007-09-17
Hi - there is a similar issue with my hd2600 pro

highly annoying because i have tried to install drivers every way described in forums but to no evail.

could it be that the drivers need a 64 bit installation of fiesty? - for them to work? i doubt it but how can i check if my installation is 32 or 64 bit - i cant remember the cd i used

when downloading the ati linux drivers from amd it give you a choice between 32 and 64 bit but the drivers are the same 64 bit drivers.

i have my 9600 pro working fine because it is on a kubuntu 64 bit system.

---

### Post by atsab on 2007-09-17
Hi again,
ok i finally got the xserver to load,
i had to wait till I could get to my university and use there wired connection
i used the alt cd to install
then when i was dropped to the command line because xserver wouldn't load, I logged in and altered the /etc/apt/apt.conf file so that it would use my university's http proxy
now i had a working connection
so i did as Pumalite suggested:
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
 and then startx
the xserver failed to load again

so i tried
sudo apt-get install linux-restricted-modules-2.6.20-15-386 
then startx
the xserver failed to load again

next i mounted my usb drive with the latest ati drivers on and installed those 
and tried startx again and this time the xsever loaded fine

So i think in short if any one else has the same problem 
install by alt cd on wired connection
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-2.6.20-15-386 
./ati-driver-installer-8.41.7-x86_64.run
startx

Thanks every one for your help

---

### Post by Pumalite on 2007-09-17
Glad you got it working!

---

