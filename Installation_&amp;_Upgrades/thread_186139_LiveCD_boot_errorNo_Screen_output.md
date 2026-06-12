---
title: "LiveCD boot error/No Screen output"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by PendragonUK on 2006-06-01
I think this may have been addressed in other post but I would like conformation...

Boot from 6.06 AMD64 CD, all looks normal. X starts, I hear the fanfare all looks OK then the screen flashes several times. The My LCD monitor gives me the "No Signal" message...

From what I have read on this forum and else where it's a nVidia driver problem.

I have read that what I need is to have it use VESA then install the nVidia drivers once it's all setup. Given that this is a known issue I'm fuming about this... OK I wont go off on one now I just want to get this sort ted But WTF!!!

As I'm not sure if the ctrl-alt-f1
sudo dpkg-reconfigure xserver-config
will work as my monitor is pissed at not receiving a signal it can handle I'm currently downloading the server version then going to try to install that then install the desktop on that with...
sudo apt-get install ubuntu-desktop

But is anyone can give me a boot command that forces VESA on the Live CD I will be happy. Also if you think I'm barking up the wrong tree and I'm wrong in my assumption that it's a nVidia problem then please let me know...

EDIT
Opps forgot system spec

AMD Semperon64 3400
2G RAM
nVidia 6800GT-256M
IDE Hardrives

---

### Post by spin2cool on 2006-06-01
Have you tried using the safe graphics mode when booting from the CD?  I was able to use that to install Dapper, and after install, my video card was detected just fine.

---

### Post by Zyzzyva100 on 2006-06-01
Not quite the same problem, but I get all the way through the install, and then at the login screen everything immeadiately locks up.  While I am using the i386 install disk, I am using a sempron64 too, as well as an nvidia card (6600).

Not sure what the problem is, but I have seen other people in the same situation.  I can't seem to login anyway in order to change the vesa mode, so I seem to be screwed.

---

### Post by PendragonUK on 2006-06-01
I installed the AMD63 Server it went well then atp-get the ubuntu-desktop, it all downloaded in around 25 mins. Unpacks OK then I get a "Kernel Panic" so I guess that's screwed up the install and had to re-boot.

I tried the i386 desktop in safe mode, it still wont boot the live CD did the same with the 64 version. nothing that has been suggested would appear to get the LiveCD to boot let alone install... I'm off to bed soon and very pissed off... **Why doesn't it just work!**

I'll have another look on the forum tomorrow for some hints, if that doesn't work it's back to Windows, call me an a couple of years when it works and I will give it another try!

---

### Post by PendragonUK on 2006-06-01
OK so I didn't go to bed straight away...

After some more reading I'm downloading the Alternate amd64

This should let me install to old fashioned way without having to use the LiveCD

My hope is that once it's installed and Xserver crashes I will be able to change to the vesa graphics then install the proper nVida drivers once it's all running.

I'm still pissed about this... how can I recommend ubuntu to people if it doesn't work for everyone!!! How tricky would have been to have it default to vesa and tell people how to install the right drivers for their graphics cards once it was all up and running... Or better still have the nVida drivers install properly in the first place!

This time I am really off to bed, I have work in the morning...

---

### Post by PendragonUK on 2006-06-02
I would love to know how common a problems are...

LiveCD will not boot
Problem nVidia driver setup.

Fresh install locks or with corupted graphics
Problem nVidia driver setup.

Was there really no one on the beta testing program with a nVidia 6600 or 6800 graphics card?? if there was did they have the same problems?

I have read at least 10 threads on the fourm from people having this or a very simalar problem.

Could one of the linux guru's on the forum right one of those nice how to's and make it sticky at the top of the forum. How to install Daper if you have an nVida graphics card...

---

### Post by PendragonUK on 2006-06-02
Nice to see loads of people trying to help Grrrrr....

OK I have installed from the Alt AMD64 CD it all seamed to go OK but crashes at the log on screen.

I will continue trying this until I get it !!!

Hopefully someone may find my trials of some help and the rant at least amusing...

---

### Post by doobit on 2006-06-02
I'm having many lockup problems during and after install as well. I'm going to use a system rescue CD later tonight to make new partitions and start over. Everything seemed to install correctly the first time, but then it failed to shutdown and locked up during the process so I had to do a hard shutdown. After that I started having all kinds of problems, and I couldn't even  get the live CD to run right.

---

### Post by Caraibes on 2006-06-02
I am having display problems too ! (ubuntu 6.06)

I have an ATI Radeon 7000 video card, and a Dell LCD 18¨ monitor...

My problem is that the live-cd boots, but the display is flickering very much !...

I would be interested to load vesa drivers as well, to solve that...

I tried to boot in safe graphical moce... no help...

However I installed successfully Xubuntu 6.06 in another PC, with a 15¨CRT monitor, and an integrated Via chipset for the video...

---

### Post by PendragonUK on 2006-06-03
I'm in a world of pain with this...
So far I have tried...
6.06 i386 Desktop - Wont boot so can't install
6.06 amd64 Desktop - wont boot so can't install
6.06 alt amd65 - will boot Kernel panic on second stage of install
6.06 Server amd64 -installs fine kernel panic when installing desktop
I thought I would go back to 5.10 then upgrade
5.10 i386 crashes on second stage
5.10 amd64 kernel panic on second stage

Currently downloading 6.06 alt i386, I have a nice collection of beer mats...
Thank God for bittorrent and a fast internet connection... I'm starting to think that ubuntu hates me... Meantime I have a couple of other things to try once I can get this installed. Thanks to the guys that have taken the trouble to post solutions to the Xserver/nVidia/ATI problems. If I can get to that stage I will give them a try...

I do have a couple of other distros on disk... SUSE and Fedora it's just the ubuntu is where it's at...

---

### Post by PendragonUK on 2006-06-03
OK a little more success, but only a little...

6.06 alt i386 Boots, and installs Woot! I have tried changing it to vesa using

dpkg-reconfigure xserver-xorg

even tryed VGA... still nothing Grrrrr

Tried editing the xorg.conf still no luck... and it is down to luck because I don't know what I'm doing but following the suggestions on the forum. Well thanks to all of the help so far. 

I have one other thing to try, ([http://lunapark6.com](http://lunapark6.com))
Install the i386 server version (vesa by defult) then... 

sudo apt-get install ubuntu-desktop

Now I tried this with the amd64 version but by my trail and error (big on the error!!) my system doesnt like the amd64 version. Every time I have tried it I get Kernel Panics (I think I know how that feels)

This is the last iso image that I can download and try on my system!

---

### Post by Lil_Eagle on 2006-06-03
You might want to consider alltering the menu.lst in /boot/grub and add a parameter.  Make it look like this:

```
title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash [COLOR="Red"]vga=791[/COLOR]
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot
```

the key is the VGA=791 which forces the display into a standard resolution.  It seems that a lot of monitors can't handle the default resolution that this kernel uses.  You of course need to make sure you replace the 686's to the right version, and check that the root= points to your root partition.

I ran into this same problem with many different distros that use the same kernel, or anything newer than 2.6.15.  It could also be related to the buggy Xorg 7.0  Breezy used 6.9 and 7.0 is not stable yet.

Good luck.

---

### Post by PendragonUK on 2006-10-22
OK have this sorted now, so for anyone reading this thread looking for answers here is the solution...

The issue boils down to the LCD monitors response to an incorrect input. Unlike a CRT that will try to show what it's given, with a fuzzy or distorted image. The LCD simply shows nothing more than the default "No signal" message.

After installing the nVidia drivers you have to edit the xorg.conf file with the correct info about your monitor, Horizontal and Vertical.

Then you must specify the correct refresh rate for each resolution at each colour depth you are going to use.

There are several Howto's out there about nVidia drivers it's just that this problem is limited to a handful of cheap LCD monitors.

---

