---
title: "Skewed display with Kubuntu Edgy Install"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by Schwa on 2006-12-16
I am attempting to install Kubuntu 6.10 Edgy Eft on an Asus Z96J laptop with an ati X1600 video card.  When the cd attempts to start kdm, the graphics are skewed beyond recognition: the cursor appears to be a thin diagonal line and moving it side-to-side causes it to procede upwards or downwards at and angle and then wrap around to the other side of the screen.  This happens regardless of whether or not the 'safe graphics' install mode is selected.

Has anyone else had this problem and is anyone aware of any solutions?  Is there any other information that I can provide that will help me diagnose this?

---

### Post by taurus on 2006-12-16
Try using the alternate CD to install it on your machine...

---

### Post by mrfuzzemz on 2007-01-04
I have the same laptop and I've gotten around this with the standard live/install cd.  I believe it is a problem with the basic driver used and this laptop having a wide screen display (beautiful resolution, by the way). Here's a way to get around it:

When booting up you can select boot options before "Start or Install (k)Ubuntu." Do this and remove any incident of "quiet" from this line.  

When it loads the display it will give you the shifted pixel problem.  Do ctrl+alt+F1.  This should give you a shell.

type in (not the $):

$ sudo dpkg-reconfigure xserver-xorg

Have it attempt to autodetect and all of that. Be sure to select the VESA driver.  Do the default for everything else.  

Once it is all done do ctrl+alt+F7.  This may should give you the messy pixels again.  

Then do ctrl+alt+backspace.  This kills the x-server and reloads it.  Things should go nicely from there.  

Once you are all installed you can install the ati driver (fglrx) and enjoy full resolution.

Hope this helps anyone with this notebook!

---

### Post by jhunter on 2007-03-04
I've tried installing the regular ISO, and the steps above didn't work (the screen turned to garbage instead of getting a prompt.  I then installed the OEM version instead, which allowed me to try the steps you gave mrfuzzemz, but after pressing Ctrl+Alt+Backspace, the display is still skewed.

AMD Athlon 64 X2 4200+
ATI X1600PRO Vid
ASUS M2N-E Mobo

---

### Post by taurus on 2007-03-04
When you ran 

```
sudo dpkg-reconfigure xserver-xorg
```
did you pick **vesa** as the driver for your graphic card?

---

### Post by jhunter on 2007-03-04
I did.

---

### Post by mrfuzzemz on 2007-03-04
Did you *only* have the 1024x768 resolution selected?

---

### Post by TheOne0908 on 2007-03-04
I am having the same problem.  I have nvidia sli with two 7800GT's with an AMD Processor.  I currently have windows installed on my machine and have partitioned a second drive in my machine for the Ubuntu install.  I have enough ram 2GB's to meet the requirements.  I have checked the disk and reburned it slower twice.  The menu to install the os pops-up, I say install ubuntu, but it hangs just before entering the desktop on the splash screen.  The pixels go crazy.  I was wondering how to I do an alternate install, if that is the only way to install the os on my machine.  I am currrently using the 386.iso install.  Does the alternate install work like the normal .iso by booting from the disk?

---

### Post by mrfuzzemz on 2007-03-04
I've not dealt with nvidia cards in sli, but the alternate method is a separate cd you must download.  It is a text based installation.

---

### Post by jhunter on 2007-03-04
> **mrfuzzemz said:**
> Did you *only* have the 1024x768 resolution selected?

Ah, that fixed it.  Thanks.

---

### Post by mrfuzzemz on 2007-03-05
Good to hear. Enjoy!

---

