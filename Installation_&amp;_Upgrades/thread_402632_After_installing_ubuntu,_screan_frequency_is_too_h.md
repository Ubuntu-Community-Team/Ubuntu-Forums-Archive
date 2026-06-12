---
title: "After installing ubuntu, screan frequency is too high to see desktop"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by wolfeedarkfang on 2007-04-06
I gota say this is about the hardest to install linux distribution i've ever seen. I've ran into several blockades along the way but this one is the only one i could not fix. When i fully install and reboot the PC, and choose ubuntu from the select, it loads up, but once it gets into the actual ubuntu desktop scene, the frequency of the environment is too high for my monitor. I searched about this and all i can find is info about editing my config through the command console. Since i cannot even see my desktop i have absolutely no idea how to go about that. Is there some sort of safe mode startup that loads everything at minimal? If not, then i need to find something similar to ubuntu to use, but with less of a hassle.

---

### Post by spin2cool on 2007-04-06
You can boot into recovery mode from GRUB, then use a command line editor like nano to edit your xorg.conf.   Alternately, hitting Alt+Ctrl+F1 should get you to a command line once you've booted up.

---

### Post by genecaldwell on 2007-04-06
we need people to start reporting this as a bug. Using work arounds just does not solve the problem. Here are links to others with this same problem. This appears to be a refresh rate issue with LCD flat panel displays, NOT a screen resolution issue. I believe that the refresh rate is being set to 46hz for your LCD, which is limited to 60hz. I installed Ubuntu in VMWare to confirm this and it clearly shows the refresh rate to be 46hz. editing the xorg.conf will not do any good as I have tried this many times, all to no avail.
[http://ubuntuforums.org/showthread.php?t=378556](http://ubuntuforums.org/showthread.php?t=378556)
[http://ubuntuforums.org/showthread.php?t=402118](http://ubuntuforums.org/showthread.php?t=402118)

and I have reported this as a problem here at launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/103530](https://bugs.launchpad.net/ubuntu/+bug/103530)

---

### Post by wolfeedarkfang on 2007-04-06
Thanks for the replies. I'm new to linux, but I've tried other distributions that worked, yet my friends say those suck in comparative to this one. The other ones i tried seamed to work fine. I'm not sure how I'm supposed to edit the xorg.conf if i cannot see the desktop, but thanks for telling me the command to open the console. If i can go at this blindy i will be lucky. When i load up in recovery mode it does the same thing. I think the boot screen needs to allow us to select our own refresh rate and screen resolution. My KDS CRT Monitor does not support any refresh rates lower then 60 from what i seen through windows. It boggles me how If the default refresh rate is that low, how is anyone able to get this to work?

> **spin2cool said:**
> You can boot into recovery mode from GRUB, then use a command line editor like nano to edit your xorg.conf.

I was able to get Nano to open through the recovery mode. Can someone give me the path for xorg.conf? i tried /etc/X11/xorg.conf like one of the guides said, but it said file not found.

---

### Post by hashimoto on 2007-04-06
The problem very likely lies in the recognition of your display. Some of them are not reporting correctly the refresh rates etc. to the system so they can not be configured correctly. I've had my share of these and the following has always helped me.

Dig out the technical data of your monitor (supported resolutions, vertical & horizontal refresh rates etc.) You will need this data soon.

Boot to safe mode and you should have root privileges.

Run the following commands:

```
cd /etc/X11
cp xorg.xconf xorg.conf.backup
```
This will copy your original xorg.conf to xorg.conf.backup
Then ```
dpkg-reconfigure xserver-xorg
```
This will start a text based program to configure your xserver. Answer all the questions and if you don't know the right answer use the defaults. 
At some point you will have an option to select "advanced". Do that and fill in the data of your monitor (refresh rates) and select the correct resolutions from the list with space bar. After completing the wizard reboot. ```
shutdown -r
``` should do that. You should now (hopefully) have a working x-server.

---

### Post by wolfeedarkfang on 2007-04-06
I'm having problems with those too. when i type...
```
cd /etc/X11
cp xorg.xconf xorg.conf.backup
```

it says "cp: target `backup' is not a directory"

when i type...
```
dpkg-reconfigure xserver-xorg
```
it says "Package xserver.xorg' is not installed and no info is available."

Personally i don't think i have the server edition of ubuntu. O.o Nore do i need it. I'm using the installation from setup-ubuntu-full.exe.

When i type "dir" in the X11 directory it shows the following files and directories...

X | Xsession.d | app-defaults | fonts | xinit | Xresources |Xsession.options | cursers |gdm | xkb | Xsession | Xwrapper.config | default-display-manager | rgb.txt

---

### Post by hashimoto on 2007-04-06
Sorry, my bad. Should be:
```
cp xorg.conf xorg.conf.backup
```

Somehow the latter error indicates that you don't have xserver installed at all. Which version did you install? Did you start your installation by clicking and icon on the desktop? Did the live-cd run correctly and did you get into gnome?

If you didn't have a desktop to start installation from you may have installed a server version... 
In that case install ubuntu-desktop in the safe mode by running ```
apt-get install ubuntu-desktop
```

---

### Post by wolfeedarkfang on 2007-04-06
It was the one from here. [http://omattos.co.uk/setup-ubuntu.exe](http://omattos.co.uk/setup-ubuntu.exe)

I tried using the beta one called wubi, but it was even worse off then this because it wouldn't even start up.

i don't think it's the server edition because when i ran that command it said "ubuntu-desktop is already at the newest version".

---

### Post by genecaldwell on 2007-04-06
I have also tried to change the refresh rate by editing the xorg.conf file and it has never worked once. there seems to be something going on in X that is causing this problem. I have re-installed so many times now trying to get any display at all that I can now do it with my eyes closed.

I have already posted links below showing that others are having the very same problem and that the alternate install CD does not work either, booting into recovery mode and editing xorg.conf does not seem to produce any results for me...I have managed to get the resolution to change to anything I want, but upon rebooting after making the change, the monitor always produces an input error stating that the signal is not a valid input value.

---

### Post by Ken in Seattle on 2007-04-06
does the live cd work? If not the default resolution/ refresh/scanrate  is just not in the range of your monitor.

I have a 9" rackmount monitor that did the same thing. I had to put another monitor on it to do the install. I edited the xorg.conf file and saved it with the details for the 9", and wrote an alias for the one line command to cp the bak to the running file and reboot. I had to do it a couple of times before getting it right.

I have had others that would lock in 640-480 mode.

Each time, correcting the display section of the Xorg.conf file with the actual factory values did the trick. In one case the value in the xorg DB for the monitor was listed wrong on the site.

Luckily my LCD screens worked fine on install

---

### Post by wolfeedarkfang on 2007-04-06
I might as well just buy a second hard drive and install knoppix on it... I never had any problems with knoppix. I was kinda hoping to get ubuntu to work so my friend and  i would have matching systems and able to work with each other easier, but eh... It seams to install perfectly on his PC, yet he can't install knoppx. So it's kinda weird lol...

---

### Post by hashimoto on 2007-04-07
> **wolfeedarkfang said:**
> It was the one from here. [http://omattos.co.uk/setup-ubuntu.exe](http://omattos.co.uk/setup-ubuntu.exe)


I have no idea what you have installed. Maybe the "windows-installer" that I remember reading about some time ago? Could be beta. 

My proposal is that you download the official iso disc image, check the md5sum and burn the  image to the cdrom. Then boot from that cd (it is a live cd at the same time) and install by clicking the icon on the desktop. Quite painless.

Iso can be found here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

