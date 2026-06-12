---
title: "Ps3 Installation Success Poll"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Onay on 2007-10-21
Here's just a quick poll, mainly for myself, but also for anyone who wants to know if Ubuntu works on Ps3, or if people just want to let out steam on how they wasted their time trying to get it to work.

Feel free to explain your answer.

---

### Post by Cyberbian on 2007-10-21
Ok Here goes. Below is a link to PS3Ubuntu forums where there is a great discussion of how to overcome the teeney tiney desktop area issue during and after install

[http://psubuntu.com/forum/viewtopic.php?t=13&postdays=0&postorder=asc&start=15&sid=07f3620a0]("http://psubuntu.com/forum/viewtopic.php?t=13&postdays=0&postorder=asc&start=15&sid=07f3620a0")

Basically a chunk of a line in the /etc/kboot.conf is missing

ABOUT THE OPTIONS_______________________
Video mode ID: 
0:automode 
YUV 60Hz 1:480i 2:480p 3:720p 4:1080i 5:1080p 
YUV 50Hz 6:576i 7:576p 8:720p 9:1080i 10:1080p 
RGB 60Hz 33:480i 34:480p 35:720p 36:1080i 37:1080p 
RGB 50Hz 38:576i 39:576p 40:720p 41:1080i 42:1080p 
VESA 11:WXGA 12:SXGA 13:WUXGA 

full screen mode: <video mode ID> + 128 
dither ON mode : <video mode ID> + 2048 
 
full screen mode 5:1080p + 128 = 133

[http://ps3wiki.qj.net/index.php/PS3_Video_Mode](http://ps3wiki.qj.net/index.php/PS3_Video_Mode)
__________________________________________



THE LINE IS BELOW: THE "VIDEO=" begins the missing chunk.

                                                                              KEEP THE NUMBER IN THE ORIGINAL OR REINSTALL!
 ....................................................................|..........................................|
 ...................................................................\/.........................................\/
linux='/boot/vmlinux initrd=/boot/initrd.img root=UUID=xxxxxxxxxxxxxxxxxxxxxxx video=ps3fb:mode:133 quiet splash'


OK so after a massive amount of time wrestling that with a final successful outcome thanks to that forum above:

I cannot get my bluetooth keyboard or my wifi internet connections to work. They certainly do not work as advertised. 
I will keep wrestling with them, Maybe we can work through this.


For the Bluetooth issue I have the NEW ps3 logitech bluetooth keyboard.

They end the identifier/name of the device used in communications with (TM) and the brackets apparently frig up the syntax during the communicaitons to Linux. I had the same experience with Yellowdog and Ubuntu. 

I had the wireless working previously with Yellowdog. 4.2

_________________
Ubuntu, It justworks  

The line over is a vinculum meaning NOT on your PS3 yet. 
I honestly look forward to the day it does!

---

### Post by canyon on 2007-11-23
well, you asked for it....

I had yellowdog installed on the ps3, and didn't like it at all. As i had fiesty, then gusty on a pc, i went for it on the ps3 as well.

I wasn't sure about the status of Gutsy on PS3, so I installed Fiesty from the live CD. Got it installed eventually, but i hit on the "15% guided partitioning" bug first; then the install stuck at 59% due to a corrupt CD. 

Tried again with a new live CD, and manual partitioning and got Fiesty up and running.
Strangely, there is an icon in the "system tray" at the top right of the screen that says my network isn't working, but it obviously was as I could access the internet and did all of the updates.

Then - disaster:....
I went to (I think) System > Administration > "Add Software", or "software Manager" and found an item in the list that gave me the option to update to Gutsy: So I pressed the button. It downloaded over 900 files and installed them, and all seemed OK. Eventually I was told to restart (I think it was just another icon in the "System Tray"). The restart got me back to the kboot prompt: I pressed ENTER, and got the message:
Loading kernal with initrd...success.
Boot
_

And that's it - totally locked up, no way out - I have to turn off at the mains to get anything back.

I don't have enough expertise to type in some magic spells at kboot to get around this, so I either give up, or start again from scratch with another gutsy alterate CD. and keep my fingers crossed.

CONS: I've spent 2 days on it and it doesn't work.

PROS (relative to Yellowdog):
1) The PS3 was running on a wired network, as we couldn't get the wireless to connect. Yellowdog just wouldn't let me use the wired network, but automatically used the wireless.
2) Couldn't get better than 756 resolution with Yellowdog. Ubuntu gave me 1080p out of the box (I've got a 1080p TV)
3) Yellowdog had very restricted depositories, and I couldn't get updates by adding others, so i could never install the software I wanted.
4) Gnome is sooo much better that Yellowdog's "Enlightenment".

So, it's Ubuntu for me, if I can get it working. But what a struggle

---

