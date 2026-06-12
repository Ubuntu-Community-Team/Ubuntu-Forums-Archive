---
title: "Ubuntu on tablet PC"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Mekon88 on 2008-03-17
Hi all
Im new to ubuntu but the more i use it the more i love it, I want to put gutsy gibbon on to my tablet PC as i think it will be a smoother OS than XP, its kinda low spec and ubuntu is alot more resource friendly!, the tablet is a Fujitsu Stylistic ST4120P, p3m 933mhz, 30gb hdd, 512mb ram.

Does anyone have experience with this series and ubuntu? its a lovely machine and i really want to put ubuntu on it, but if it doesnt work it was a REAL pain getting XP set up (have to install drivers in a set order or XP implodes, im not kidding!)

Thanks in advance for any help

---

### Post by dasunst3r on 2008-03-17
With respect to laptops in general, if you have an Intel wireless networking card, then you'll have a decent experience.  It would also be ideal if the tablet functionality was provided by Wacom.  In any case, burn a LiveCD and try it out -- it couldn't hurt!  Let us know your findings and we could work from there.

---

### Post by Peter09 on 2008-03-17
I have a Toshiba tablet PC. In general the functionality for the tablet is installed by default. If there is an issue its a lack of applications for the tablet.

PC

---

### Post by alenis on 2008-03-17
My Travelmate C100 works well, but:
a) I cannot use my wireless card;
b) there is a bug in X which causes serious troubles with SiliconMotion video adapters (see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/136853]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/136853")
I remember that Ubuntu 7.10 live CD worked well, but when I installed it the computer became unusable. I had to revert to 7.04, so be careful!

---

### Post by garwaymatt on 2008-03-17
I dont think the fujitsu's use wacom hardware, IIRC, they are based on a different technology, Passive. Do you need to use the pen, or can you just touch the screen?

The best thing to do would be to just give it a try, and see what works. Older hardware generally works well,  Have you considered Xubuntu, which runs quicker on that age of machine.

---

### Post by Mekon88 on 2008-03-17
its the 4120p, its a passive touchscreen, the wireless isnt an intel one, the original was a piece of sh1t so i replaced it with a nice atheros g+ card, lol old card was b 11mbps and didnt support anything except WEP and i use WPA so it got changed, i have atheros wireless in my main laptop and it wasnt toooo difficult to get working, ill try a live cd in a few mins... if i can get the bloody docking station to work properly, tablet is very reluctant to boot when docked for some reason :s

---

### Post by Mekon88 on 2008-03-17
oh god oh god oh god oh god


dear god im doomed


booted the live cd.....

it turned my screen into a barcode :S

which is slowing becoming just white :S

HELP!

im scared!!!

whats going on!!!

---

### Post by Peter09 on 2008-03-17
The Live CD doesn't touch your disk - so effectively nothing is happening.

PC

---

### Post by Mekon88 on 2008-03-17
sorry.... tis a lovely little thing... kinda panicked a bit there, im not simple i know that its clearly a display issue.... however ummm cant install linux or do anything of that sort without a working display....

---

### Post by Peter09 on 2008-03-17
How far into the boot process did it get?
PC

---

### Post by Mekon88 on 2008-03-17
[http://ubuntuforums.org/archive/index.php/t-589945.html](http://ubuntuforums.org/archive/index.php/t-589945.html)

this is the active version of my tablet he is talking about, the display driver should be the bit i need to sort the stylus bit isnt relevant, is there any way to do what he suggests about swapping to the i810 driver by some special command before the live CD boots?

---

### Post by Mekon88 on 2008-03-17
seemingly it got all the way, i say this because i left it for a few mins, then pressed the power button and it did a controlled switch off during which i saw the ubuntu logo followed by the usual "remove the disc from the tray and close it if present" stuff
it wasnt crashed

---

### Post by Peter09 on 2008-03-17
Try again, but when you get to the corrupt display do
<CTRL><ALT><F1>

and see if you can get a system prompt.

---

### Post by prshah on 2008-03-17
> **Mekon88 said:**
> Hi all
friendly!, the tablet is a Fujitsu Stylistic ST4120P, p3m 933mhz, 30gb hdd, 512mb ram.

Thanks in advance for any help

I have a fujitsu P5010 (not a tablit PC, but an ultraportable). Ubuntu works better on this than XP anyday! (Espcially the SmartBay Media Controller- for some reason, the XP drivers I have installed do not allow me to use the media card reader in explorer; I can only access it via the command prompt.)

Everything was flawlessly detected and installed; from my 10.4" widescreen default resolution to wireless to media card slot, modem, etc.

The specs for a P5010 are very similar.

Special note: Even the live CD worked flawlessly for me, detecting and activating everything. So maybe you should give it a go with the live CD, since specs wise both these are very similar.

---

### Post by Mekon88 on 2008-03-17
i shall have to go findify me a keyboard...

---

### Post by Mekon88 on 2008-03-17
keyboard connected, system is up? ctrl + alt + f1 does nothing :(

---

### Post by Peter09 on 2008-03-17
Mmmm... can you boot into safe graphics mode?

PC

---

### Post by Mekon88 on 2008-03-17
now trying it

---

### Post by Mekon88 on 2008-03-17
same barcode fading to white syndrome as normal mode :( tho this time i did hear sound , and doing ctrl alt f1 gave me some funk, followed by..... a command prompt! so this is a step in the right direction!

---

### Post by Peter09 on 2008-03-17
At the command prompt do the text below and try to set up your video card

```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Mekon88 on 2008-03-18
how would i get back into the graphic environment to try the new config?

---

### Post by Peter09 on 2008-03-18
```
startx
```

this should try to start the GUI.

PC

---

