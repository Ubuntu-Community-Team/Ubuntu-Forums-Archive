---
title: "Problems with booting Ubuntu"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by kiwusek on 2007-01-03
I downloaded a DVD version of Ubuntu 6.10 and I try booting from it. It brings me to a screen where it tells me my PC is reading the data to boot (it fails) and sends me off to Caldera DR-DOS. After checking various hardware components I am allowed to use DOS commands. First thing I do is navigate to drive D: (my DVD RW drive) from here I type "START" and it says that DOS cannot load this (because it is DOS). 

Believing that my BIOS is not set to Boot from disc I Restart my PC and attempt to enter BIOS only to find myself being thrown back to where it tells it is reading data to boot. Failing like usual it sends me to WINDOWS XP. This attempt to access my BIOS was without the Ubuntu disc inserted. 

I am using a FAT32 Hard drive along with Windows XP Home Edition :(

Any help is much appreciated especially on trying to access my BIOS

Thanks

---

### Post by bernied on 2007-01-03
This is curious - doesn't sound like an official ubuntu release to me.
Where did you get it?

As for accessing your bios, this is specific to the bios, it is sometimes <ESC> sometimes one of the F keys, or the Delete key - Maybe delete is most common.

Usually you get about 1 second to read it on the screen though, during bootup.

Or maybe you can find a manual - online if you haven't got a paper one.

---

### Post by kiwusek on 2007-01-03
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

That is the place from which I downloaded the version I was talking about. I you scroll down it will have the download of 6.10 the one which I got. Also it is the i386 version.

---

### Post by bernied on 2007-01-03
I apologise - I somehow thought they only did cds, not dvds. Foolish me, I have one myself.

So do you think the dvd is booting? Does it make a good spinning noise at startup?
Have you managed to access your bios settings?

---

### Post by kiwusek on 2007-01-03
It makes no noise. I have accessed my BIOS at the beginning of summer 06 when I formated my PC and installed XP. To do this I accessed my BIOS through the F12 key and set it to boot from disk. I am not sure what is quite wrong. Should I format my PC and try to make a clean install?

I am not sure if it is booting, but when I am in Caldera DR-DOS (I didn't even know I had Caldera!) I type in "D:" to access the drive and then type "START" I receive the message that it is something that DOS can't read. I had the same thing with XP but then made my PC from the disk and it worked perfectly. Now the problem is I can't make it boot from the disc! I can't get to BIOS for some reason.

Thanks for the help so far!

---

### Post by bernied on 2007-01-03
It sounds like the dvd is not booting at all. I suggest that you go into your bios settings and change the boot order so that it tries to boot the dvd first, then the hard-drive.

You will not be able to start the live-cd from DOS. The live-cd is a complete operating system, which neither DOS nor Windows will be able to start. It needs to be started by the BIOS boot process.

---

### Post by bernied on 2007-01-03
Sorry, are you saying that the F12 key is not working for accessing the bios settings? Have you tried either holding it down as you start the machine, or pressing it repeatedly as you start the machine?

---

### Post by kiwusek on 2007-01-03
I was pressing it down repeatedly.  I tried a variety of other keys such as DEL, F10, F1, F2 all being pressed down repeatedly.

---

### Post by kiwusek on 2007-01-03
OKay I held down the F12 key and still the same problem...

The thing that was trying to boot something was

INTEL (R) Boot 


*after a while*

No Boot file name received

---

### Post by riven0 on 2007-01-03
*scractches head* Very strange. Have you tried escape? That works for me on my laptop.

---

### Post by kiwusek on 2007-01-04
I haven't tried escape though... I think I just might format my entire drive. Then I will try and install it. 

Wow it didn't even want to boot from my Windows XP CD! I am really perplexed. The thing that shows up is the INTEL (R) BOOT AGENT

:confused: :confused: 

Thanks for the help so far!

---

### Post by kiwusek on 2007-01-04
It tried ESCAPE and still no go... :(

I am thinking of formatting my entire Hard Drive and trying to see if it will work then...

I really have no idea what is happening.

---

