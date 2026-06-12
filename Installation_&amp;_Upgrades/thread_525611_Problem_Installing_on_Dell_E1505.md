---
title: "Problem Installing on Dell E1505"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by hani1400 on 2007-08-14
Hi
Im trying to install Ubuntu 7.04 on my Dell Inspiron E1505 with ATI Radeon x1400 Graphic Card.

But i cant boot into the CD version to start installation because it gives me an error about the X Server, i cant remember exactly what the error says but it is something about not being able to start X server because of the graphics.

I pressed F4 and tried several resolutions but none worked.
Thanks

---

### Post by arijarot on 2007-08-14
try "start ubuntu in safe graphics mode"

---

### Post by hani1400 on 2007-08-14
Thanks. I tried that already and it didnt help.

---

### Post by merlinus on 2007-08-14
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.  And it will not be prey to video card problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by hani1400 on 2007-08-17
I installed with the text only mode, then when i went to boot up it gives me the same error and then this error:

> [xxx.xxxxxx] bcm43xx!
Error: microcode"bcm43xx-microcode5.fw" not available or load failed.

This error keeps popping up over and over and the x's in my example are numbers which change everytime.

---

### Post by merlinus on 2007-08-17
Did you try Recovery Mode from the opening menu?  That should get you to a command line where you can then reconfigure the x-server.

-merlin

---

### Post by Arthur Archnix on 2007-08-17
Don't worry about the bcm error. That's just your wireless card which will need some more tweaking. If you can install to text mode only, and have another computer handy, you can get your video going in short order.

For starters, in text mode, then when it kicks you into the terminal after failing, run startx and post the errors here. Also post the output of lspci. 
```
startx
lspci
```

---

### Post by hani1400 on 2007-08-17
The Errors i get when starting x server are:
> x_warning_process set to priority -1 instead of requested priority 0

*[in between this is some info like version and release date etc.]*

No screens found
XIO_ fatal IO error 104 (connection reset by peer) on x server "_0.0"
After 0 requests (0 known processed) with 0 events remaining

I tried to reconfigure the x server and manually change the resolution but i wasnt sure about the horizontal and vertical sync range and it didnt work.
When i bought the Dell E1505 i upgraded the screen and i think the screen i have is 15.4 inch Wide Screen XGA Display with TrueLife.

---

### Post by hani1400 on 2007-08-17
In x server configuration, when you choose to auto detect it says 

> no x server known for your video hardware
there is either no video hardware installed on this machine or the discover program was unable to determine which x server is appropriate for the video hardware. This could be due to incomplete information in the discoveries hardware database, or because your video hardware is not supported by available x servers.

---

### Post by Arthur Archnix on 2007-08-17
Ok, and show us what this does:
```
lspci
```
Oh, and give the exact name and model of your monitor.

---

### Post by Praill on 2007-08-17
This is a confirmed [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853") with the new 2.6 kernel.

The fix is to install with the alternate CD, boot into recovery mode, and execute the following:
```

sudo apt-get install xorg-driver-fglrx

```
Then you can either do one of two things. If you know your way around the xorg.conf file you can manually change the device section to use the fglrx driver instead of vesa.

If you don't... then run:
```

sudo dpkg-reconfigure xserver-xorg

```
The first question will be what driver to use, make sure you select fglrx. For all other questions you can give the default answer.

Afterwards you should have a working GUI but may not have direct rendering (I didn't and I have the same laptop with the same card). The easiest and fastest solution is to download a program called [envy]("http://albertomilone.com/nvidia_scripts1.html"). It is a nice GUI on a great script that manually installs the proprietary drivers and configures your xorg for you.

Good Luck!

---

### Post by hani1400 on 2007-08-17
The lspci gives me the following:

> PCI bridge_intel corperation 82801 mobile PCI bridge (rev e1)
ISA bridge_corperation 82801gbm (ich7-m) lpc interface bridge (rev 01)
smbus_intel corperation 82801g (ich7 family) smbus controller (rev 01)
vga compatible controller_ati technology inc radeon mobility x1400
generic system peripheral [0805] _ricoh co ltd r5c822 sd/sdio/mmc/ms/mspro host adapter (rev19)
system peripheral_ricoh co ltd unknown device 0843 (rev 01)
system peripheral_ricoh co ltd xD-picture card controller (rev 05)
network controller_broadcom coperation dell wireless 1390 wlan mini-pci card (rev 01)

Looks like there is stuff off the screen at the top which i cant see and i cant scroll up, so i hope this is everything.

**Praill** I tried your suggestion and it told me > "couldn't find package xorg-driver-fglrx" im in root@ubuntu_~#

---

### Post by Arthur Archnix on 2007-08-18
First of all, I'm not sure what you mean you're in root. Just log on with your normal username and password. There's no need to be root to do this. Then try:
```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
startx 
```

Edit: Should sudo aticonfig --initial be preferably be gksudo? How does aticonfig do its work?

---

### Post by hani1400 on 2007-08-18
I dont sign in at all, im doing this from the recovery console and it boots straight to **root@ubuntu_~#**

The first command you gave me gives lots of 
> failed to fetch [http://.](http://.)..
then 
> reading package lists... done.
E_ some index files failed to download, they have been ignored, or old ones used instead

Your second one:
> E_ couldnt find package xorg-driver-fglrx

Third one doesnt do anything.

Fourth one
> ATIconfig_ command not found

Im not sure what you meant by this last bit?
> Edit: Should sudo aticonfig --initial be preferably be gksudo? How does aticonfig do its work?

---

### Post by Arthur Archnix on 2007-08-19
Hmm... I'm not experienced with recovery console. So you reboot the computer, and in grub you choose recovery mode?

It sounds like by doing that you're not able to connect to the internet. Ok, let's try this. We're going to remove your graphical login, so that you only boot to the terminal. We can reinstall later if we get things going nicely.
```
sudo apt-get remove gdm
```
now reboot and start normally, that is, don't start recovery console. Then, I need you to uncomment any repositories you find in your sources.list. A comment is a #, and when you see it in front of a deb line that means its not being updated. So remove the # in front of the deb. Then save and close. The command to get you there is:
```
gksudo gedit /etc/apt/sources.list
```
At this point, you should be able to go to my post above and do the commands without problems.
If everything works, let's put the GDM back in there with a:
```
sudo apt-get install gdm
```

Edit: You do have an internet connection on this computer right?

---

### Post by hani1400 on 2007-08-19
Thanks a lot for all your help, i figured out i needed a wired connection and i was trying to use the wireless  LOL
Your first set of commands did the trick.

> sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
startx

---

### Post by johnn1949 on 2007-08-20
It's probably cheating but check this out.

[www.mylittleubuntuguide.com](www.mylittleubuntuguide.com)

installs ubuntu, ati graphics, beryl and more.  written for E1505/6400

---

### Post by johnn1949 on 2007-08-20
step one on 

[http://www.mylittleubuntuguide.com/live-cd/](http://www.mylittleubuntuguide.com/live-cd/)

is the iso file.

---

