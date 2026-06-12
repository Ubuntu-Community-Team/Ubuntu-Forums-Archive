---
title: "Install problem 6.10"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by BrutalUK on 2007-04-06
I've used Ubuntu in the past on older computers but I have recently tried to install it on my new computer that i have just built.

But all goes well during installation until the Ubuntu boot screen comes up with the bar moving along. After that the screen goes blank then it comes back on with vertical lines. I can hear music in the background but the display is corupted. Have tried it in safe mode and because i have a athlon 64 x2 I've also tried that version, but with the same problem. My gfx card is a geforce 6600GT on a Asus M2M-E motherboard. I have searched the postings for help but i cant figure them out. I'm just running Ubuntu as a 'live' disk so make sure all my hardware works first.

---

### Post by xi_Slick_ix on 2007-04-06
Not to get your hopes up by replying, but i have a similar issue - (6.10 Edgy)

I am basically seeing the same crap on my screen  :confused: 

Hardware:
---Processor: AMD Athlon 3000 - 64bit - Single Core Architecture
---Graphics: Nvidia 6600 (256MB RAM) - 8x AGP - Dual DVI out
---Motherboard: LanParty UT NF3 250GB
---RAM: 1.3GB (rounded) of SD-DDR 400mhz (PC 3200)
---CD-ROM: 2 Super Multi DVD Rewriters, 1 is Lite On, other is LG w/ lightscribe
---Mouse: Logitech Wireless (transmits on low frequency radio - not BlueTooth)

Two other potentially minor issues:1 was on the Live version of Ubuntu, before i could ever get that to work i had to configure the VGA to 1024 x 768 x 32bit (color), and it still never quite looked right while loading up.

#2 - once i got onto the Live disc, for the most part Ubuntu looked fine w/ the exception of one particular annoyance - I could not see the mouse (arrow) on screen.  Made it a pain in the *** to Navigate.. mouse functioned fine, but had no image.  Ubuntu did recognize the mouse in the hardware listings.

Anyway if anyone can give me some tips on how to resolve this it would be greatly appreciated.  If i don't hear anything w/in the next week I'll probably try the 32bit version of of 6.10.  

-Thanks again

---

### Post by wpshooter on 2007-04-06
From what I read on these forums, I don't think the 64bit is ready for prime time.

If it were me, I would immediately (if not sooner) get the 32 bit and install that baby.

Good luck.

---

### Post by zvacet on 2007-04-07
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bulldog on 2007-04-07
Use the command which zvacet stated and install drivers for the graphics.

---

### Post by BrutalUK on 2007-04-07
> **zvacet said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

Thanks for that but how do i actually use that command? I guess looking at other posts i do it while the boot screen is up and press crtl+alt+f1 so it goes into text mode, that correct??

Sorry for being a pain but I'm more an XP/Vista techy but i want to learn more about linux systems.

All help much appreciated!:)

---

### Post by bulldog on 2007-04-07
If you can't get it to the GUI,just use the console [text mode]
To install drivers for the graphics```
sudo aptitude install nvidia-glx
```

It is possible you haven't installed the restricted modules either.
Just type in console ```
uname -a
``` to see which kernel you use.
You'll get some thing like "Linux AMD64 2.6.20-14-generic #2 SMP Mon Apr 2 20:37:49 UTC 2007 i686 GNU/Linux
bulldog@AMD64:~$ "
Now to install the restricted modules```
sudo aptitude install linux-restricted-modules-2.6.20-14-generic
``` use your kernel instead of course in this command.
If you installed the restricted modules and the graphics driver reboot and see what happens.
If things won't work,look in your xorg.conf if the nvidia drivers are enabled```
sudo nano /etc/X11/xorg.conf
``` in console,and change in the driver section your 'nv' into 'nvidia' if this isn't done already.
Exit nano by Ctrl-x and save the file.
Reboot and try again.

---

### Post by BrutalUK on 2007-04-07
Right I have tried both zvacet & bulldogs suggestions but neither seem to work for me. The first one using sudo dpkg-reconfigure xserver-xorg works ok until i get to the section for colour quality eg 8, 16, 24 bit where it just hangs and pressing the keyboard makes bleeping noises.

Second suggestion by bulldog again first command works ok and says its updated the nvidia driver etc and uname -a works and brings up the kernel as said, but after that when i try to install the restricted modules it just freezes!

I've also looking into the sudo nano /etc/X11/xorg.conf and according to that my video has been picked up and it shows all the resolutions etc. But when i try to change the NV to Nvidia and save it again it just freezes.

I guess these instructions dont work on the live cd disk as how is it going to be able to save the changes when u have to reboot????

---

### Post by BrutalUK on 2007-04-09
Since no one has replied I thought I'd try the alternative version instead, but I haven't tried it yet. Going back on whats been said i thought I'd try it on my old P3 system....and suprise it worked first time.

I know 7.04 is a beta but do u think the graphics problem is now sorted or does anyone else who runs a Geforce 6600GT confirm this?

---

### Post by bulldog on 2007-04-09
Well I didn't understand you're using the live cd.:) 

And no, you can't install anything using the live cd,just install ubuntu and reboot.
You'll get the same problems,but try the given advice again,and it should work.

---

### Post by BrutalUK on 2007-04-09
> **bulldog said:**
> Well I didn't understand you're using the live cd.:) 

And no, you can't install anything using the live cd,just install ubuntu and reboot.
You'll get the same problems,but try the given advice again,and it should work.

Sorry about that bulldog..i thought i did mention it but anyway after posting my earlier reply I burnt off 7.04 and suprise it worked first time, actually writing this reply via feisty fawn. At first the graphics got corrupted like 6.10 but after the screen went blank and came back on it all worked.

If i do install i will make good use of your posts.

Thanks again for your help:)

---

