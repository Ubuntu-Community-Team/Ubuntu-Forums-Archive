---
title: "Help please!! Black screen on boot with 7.04"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by enderokc on 2007-04-21
ok someone please help me out. I have an NVIDIA 8800GTS video card. and when I select ubuntu to boot, it goes to a blank screen and hangs. 

Now when I boot with ubuntu (recovery mode) and type in "startx" or "telinit 3" it boots up just fine. and I have installed the nvidia drivers and they work just fine that way.

but it just wont boot when i select to boot the "normal" ubuntu!! this is very frustrating since I am very new to linux.

PLEASE HELP

---

### Post by paintballtommy on 2007-04-21
im having the exact same problem as this fellow here.  when i boot to recovery and go startx it boots fine otherwise it just says kernl is live and then my monitor turns off and i get a blank screen.

---

### Post by enderokc on 2007-04-21
anybody???

---

### Post by Hobbes on 2007-04-21
I was having this problem on my laptop, and the solution was to add the following line to xorg.conf:
 Option "IgnoreDisplayDevices" "CRT"

This may not help first poster since it sounds like desktop problem, but maybe some who check this thread.  If you can go to a terminal (by pressing ctl-alt-f1 at black screen), try tail /var/log/Xorg.0.log and see what it says.

Good Luck!

---

### Post by drunknmunky on 2007-04-22
I was having the same issue. When i got to the options to hit start I hit f4 set a resolution 1024x768. and then when the screen went blank i hit the ctrl+alt+f1 and the screen came right up.

I have an 8800gts video card as well.

---

### Post by bontux on 2007-04-22
I'm having the exact same problem as enderokc, but with an ati x800 pro. Does the line: Option "IgnoreDisplayDevices" "CRT" go under the video card section in the xorg.conf file? I've placed it there and it does not resolve the issue.

---

### Post by Poirot on 2007-04-22
I have what I think is the same problem.

I have a Club3D x800rx card.

When I try the Live CD I get the usual menu but when I select the usual boot option the signal to my monitor stops. My monitor is an LG Flatron slim, it just goes into power saving mode.

I will try recovery mode.

---

### Post by enderokc on 2007-04-22
Wow alot of people seem to have this issue. I hope there is a fix for this soon. 

I know have all the drivers correctly installed for mu 8800GTS and I also have my dual monitors working as well. but I still cant boot up normally!!! its driving me crazy!!

---

### Post by bontux on 2007-04-22
Okay, let me clear things up a bit. I am having this problem when I'm trying to boot an installed fiesty fawn from the hard drive, not the CD. 

Poirot, in the live CD's menu, press F4 and select your monitors native resolution. Then try running the install. I had the same problem with the live CD, and once I selected my monitor's native resolution, it worked fine. However, If you do get it installed, I fear you will end up with the same problem as I am in. (don't know for sure though)

---

### Post by enderokc on 2007-04-22
my problem is when trying to boot from the HD as well. not the live CD.

---

### Post by enderokc on 2007-04-22
bump.

---

### Post by AWBbox on 2007-04-22
I've just burned my first ubuntu iso (7.04), i'm trying to install to a new, blank hard drive. I'm running an Nvidia 680i chipset based motherboard and an 8800 GTX. Any attempt to install off the disk results in a black screen. And if i wait long enough, the display drops out all together. I'd really like to start using and learning about Ubuntu but if I can't get past this stage I don't know what i'll do :(

Please help.

---

### Post by RawMustard on 2007-04-22
I had to press F4 when given the install options on either cd, live or alt and select 1280x1024 and then I got a screen so I could install Ubuntu.  Once installation was finished, I had to add vga=795 to my grub kernel parameters or I would get a blank screen at boot time.  I'm sure it shouldn't be this way, but it's got me up and running at least.  Heres a list of valid vga settings

```
 
Colours  640x400  640x480  800x600  1024x768  1152x864  1280x1024  1400x1050 1600x1200
4  bits	    ? 	     ?      0x302   	? 	  ? 	    ?          ?         ?
8  bits	  0x300    0x301    0x303     0x305     0x161     0x307        ?       0x31C
15 bits     ?      0x310    0x313     0x316     0x162     0x319      0x340     0x31D
16 bits     ?      0x311    0x314     0x317     0x163     0x31A      0x341     0x31E
24 bits     ?      0x312    0x315     0x318       ?       0x31B      0x342     0x31F
32 bits     ?        ?        ?         ?       0x164       ?          ?         ?

```

Choose the one that best suits your monitor.  HTH

---

### Post by enderokc on 2007-04-22
how do you change the grub kernel parameters?? and my monitor has 1680x1050 resolution.

---

### Post by enderokc on 2007-04-22
nevermind I figured it out. THANKS!!! THAT WORKED!!!!!!! 

for everone else. do this:
bring up a terminal
type sudo nano /boot/grub/menu.lst

then after all the comments you will see the menu items for the grub boot loader
find the first one "Ubuntu, kernel 2.6.20-15-generic"

and add this at the end of the kernel line

vga=795

ctrl+o to save

reboot and it should work. it did for me!!

---

### Post by bbzbryce on 2007-04-22
That's exactly what I wrote here:
[http://ubuntuforums.org/showpost.php?p=2495909&postcount=3](http://ubuntuforums.org/showpost.php?p=2495909&postcount=3)

Try to search before posting, you might get an answer quicker.

---

### Post by bontux on 2007-04-23
yup, vga=795 worked for me. thanks!

---

