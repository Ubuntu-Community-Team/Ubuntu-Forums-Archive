---
title: "[SOLVED] Installing gutsy is a nigthmare: dark screen with 0 display at all"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by hurinth on 2008-03-25
[B][COLOR="Olive"]Ok this is the nightmare:
-Feisty Fawn AMD64 installed in disk 1 partition 3. OS up to date
-I insert Gutsy Live CD AMD64 in tray and restart system
-I choose to start or install ubuntu option AND: the kernel loads and then the monitor turns black, until it finally turns off, stand by mode
-The CD drive seems to be reading or something cuz it makes noises and the LED is lit
-The very same thing happens if:
[INDENT]   -I use DVI or VGA connection
   -I use a CRT or LCD monitor
   -I choose safe graphics mode
   -I choose whatever resolution with f4 key
   -If I use another copy from a friend with Gutsy i386
   -If I use my own copy of Gutsy i386[/INDENT]

-If I choose OEM installation in the ADM64 CD the screen eventually (after maybe 10 annoying min) shows a desktop. At first only the background color, then the wallpaper and a loading cursor, you know, the little circle?
-After that NOTHING!
-I keep waiting and waiting and no icon appears in the desktop, just nothing. No bars no nothing but wallpaper and cursor

Please someone with experience guide me here cuz I am fairly new at this linux world.
I might try to upgrade the Feisty F installation to Gutsy, but I don´t think that is always the best way to install Gutsy, specially because I am considering on beginning a project to migrate a simple network from windows to Ubuntu, around 12 machines, so I would like to understand why is it so hard to install this OS. 

System specifications (where I run the AMD64 CD):
AMD +5600 no overclocking
Asus Crosshair mobo
2GB Kingston Hyperx pc26400 1GB DIMMs
EVGA 8800GTS 320MB
2 Sata II Seagate drives non raided (1 for data 1 for system)

Thanks a lot[/COLOR][/B]

---

### Post by solaceinsilence9 on 2008-03-25
Have you tried just to run it from the LIVE CD instead of starting or installing it? It seemed like when I downloaded the live CD and burned it I had an option to just start from the CD. I almost sounds like the data clusters on the CD might be damaged. I would try another CD with the AMD 64 on it. Because you system is clearly not i386 because your AMD processor is a 64bit processor. So of course, the LIVEcd's with i386 will NOT work.

What are your other partitions? I noticed you said you had three? I dont think that your problem lies with the computer or the partitions itself, rather with the install CD. The reason I say this is because you said the kernel starts to load (from the CD) then that is when your problem occurs. Hope that helps.

---

### Post by phidia on 2008-03-25
Did you check the md5sum of the downloaded iso?
A x86 iso will run on either a 32 or 64 bit processor. 
An iso made specifically for a 64 bit processor (x86-64) will normally only work with 64 bit.

Also based on this: > I choose to start or install ubuntu option AND: the kernel loads and then the monitor turns black, until it finally turns off, stand by mode
-The CD drive seems to be reading or something cuz it makes noises and the LED is lit
The problem you're having is possibly that your video card/gpu isn't being recognized-what card are you using?
You can open a shell from the install environment (Alt+Ctrl+F1) and try to get a driver working for your card.
In the shell type sudo dpkg-reconfigure xserver-xorg but you will need to know your gpu and monitor specs.
If you know what video card you have you can go to the video and multimedia [forum]("http://ubuntuforums.org/forumdisplay.php?f=138").

---

### Post by hurinth on 2008-03-25
Thank you people for the support

My graphics c. is an EVGA 8800GTS

the md5sum is basically the option to check disc for errors ritgh? That one doesn't work either, the display is null after choosing it.

The other partitions are blank

The option to run the Live CD is the same as to install it. Once you run the live CD you double click the Install icon and begin. I can not see that far.

Checking the hardward compatibility...

Ne other idea what could be wrong?

---

### Post by forestpixie on 2008-03-25
You can check the md5sum in the command line from the feisty installation

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

These are the gutsy md5sums

ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

---

### Post by hurinth on 2008-03-26
[COLOR="Olive"][B]Ok I got my solution now

Basically this could be a layer 8 panic..... but the thing is that even though the live CD shuts the LCD off, after maybe 15 long minutes, pressing the space bar turns it on and displays the desktop. Beautiful sight by the way, Feisty upgrade over the network failed previously so... it was about time to find a fix

So in summary: the EVGA 8800GTS is supported, the Asus vw222 lcd monitor too, the only caveat is that Gutsy CD turns it off, and the CD stops reading. THATS BECAUSE THE DESKTOP IS WAITING ON YOU TO INSTALL!! click space bar and see the cholatish wallpaper appear.

Thanks all[/B][/COLOR]

---

### Post by IanW on 2008-03-26
Actually, it's a bug with the Nvidia driver. A workaround is to press F6 at the LiveCD menu & delete the words "quiet splash" from the end of the boot options shown.

Once you've installed, you can open a terminal and
```
gksu gedit /boot/grub/menu.lst
```
to remove the same words from the line beginning with the word "kernel".

I understand this is fixed in Hardy.

---

