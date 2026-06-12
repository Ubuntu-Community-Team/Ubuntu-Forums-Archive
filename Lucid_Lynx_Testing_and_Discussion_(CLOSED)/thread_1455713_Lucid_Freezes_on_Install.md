---
title: "Lucid Freezes on Install"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by balaram on 2010-04-16
Lucid ISO 32-bit and 64-bit will allow choice of language then freeze when attempting to do the following step. Freezes on screen that shows five dots. Dots take turns blinking on and off for a couple of minutes before complete freeze.

I've removed a second network card, the proprietary LAN is enabled. Only other card installed is a Nvidia video, no point installing if I can't use it.

System is built on MSI board, AMD-64 bit CPU, 4 gig ram, SATA drive.
Presently running Karmic have used other Ubuntu versions on this computer in past with no problems. 

CD's are good because they'll install on a another computer I'm using.

Any suggestions?
I'm wondering if I should just wait until the final release, although I assume I'll still have the same problem.

---

### Post by thomasaaron on 2010-04-16
Have you tried using a USB flash drive to install? That happened to me recently, and it turned out my dvd drive was on the verge of failing.

---

### Post by balaram on 2010-04-16
Haven't tried USB. Will give it a shot ASAP, possibly tonight, will post result. Thanks for the suggestion.

---

### Post by dE_logics on 2010-04-16
Ensure to report a bug if this problem persists.

Double check the burnt image...the iso md5 and reburn the image.

---

### Post by Memory.Dump on 2010-04-16
I having the exact same issue, I have had 2 images downloaded and burned from 2 different computers and it does the exact same thing to me, I have swapped out my DVD drive as well, not sure where to report bugs though just hitting this sit for the first time (in a very long while)

---

### Post by balaram on 2010-04-17
Tried USB drive installation, same result. Freezes at beginning of install when 5 blinking dots appear on the screen beneath the word "ubuntu."

Tried option "without installing" and "Install Ubuntu," same result.

---

### Post by ukblacknight on 2010-04-17
I tried installing it on my friends laptop, and another friend is trying to install it right now on his PC - both having the same problem of it hanging with the dots.

My friends laptop was a Dell Inspiron, but I couldn't tell you the model number.  My other friends PC is a Dell Dimension 3000.

---

### Post by azagaros on 2010-04-17
The suggest I would make is when the dots going across the screen, hit f6 and let it get to another screen.  If you get the f6 menu to come up select no mode option.  

It chooses a different way to come bring up the screen.  If you have ATI graphics, which this problem has been most evident with you need to do this.

I will not say that this will make the system work after you get it installed thought, which was the problem I saw.

---

### Post by ronparent on 2010-04-17
The final release may or may not fix the problem. Of my four AMD 64 machines only my laptop loads the cd with no problem. I've broght the other three up only after playing with the kernal boot option. Depending on your MB bios it may be any one or more of the following <F6> options - noapic nolapic nodmraid nomodest. You can test them in any combination by hitting <F6> at the menu screen and using the up/down arrow to move to one and selecting it with the space bar. Also then edit the boot line to remove the quiet and splash options. Then boot your menu selction.

Two of mycomputer win't boot without X'ing ou the apic lapic option. My AMD 64 X4 machine won't boot unless I X out dmraid, delete splash from the boot line and disconnect one monitor (explicitly the secondary one!?)). I know - lots of fun :). Have fun.

---

### Post by ukblacknight on 2010-04-17
I'll tell my friend - he's currently chatting to me on msn because the failed 10.04 install has removed his 9.10 install, even though he never attempted to do the actual install!  He's now without a system, and still can't get the install or LiveCD to do anything.  Needless to say, it's pretty much screwed his system!

---

### Post by twisted_steel on 2010-04-17
If your freeze happens to be related to a graphics issue (like mine), hit a key during the initial display of the Ubuntu screen to view the options.  Hit F6 and remove "quiet splash" from the boot lines.

Here is some more info: [http://ubuntuforums.org/showthread.php?t=1446000&page=2](http://ubuntuforums.org/showthread.php?t=1446000&page=2)

I had to use Alt+SysReq+K to kill plymouth or X or whatever during the initial boot into the new system and also every other boot until I replaced the graphics driver with the official one from Nvidia.  Until I did that, it would do the same thing and freeze once all dots were displayed.

---

### Post by balaram on 2010-04-17
I got Lucid to install, both the 32-bit and 64-bit version.

1.) Hit the F6 key the moment the first Ubuntu screen appeared.
2.) Language selection screen then came up and I chose English.
3.) After I chose the English language the screen went black, no dots appeared. Now here's the weird part; nothing appeared to be happening for about 10 minutes after that.
Blank screen and no hard drive activity, well at least my HDD power light wasn't flashing, and the CD Drive never lit up either. It appeared that the install had frozen. However after approximately 10 minutes of inactivity the CD Drive lit up and started reading again. Then the HDD lights came on and before long my monitor was displaying the Ubuntu desktop.
4.) I was now booted into the Live version of Lucid. I wanted a full install so I clicked  the "install" icon that appears on the Live version Desktop and the hard drive installation began running as you would expect it too. Lucid installed with no problems at all after that...all is 
well.

If you think the install has frozen, wait at least 10 minutes after you last notice any activity. Perhaps it's actually running without showing any outward signs of life.

---

### Post by ronparent on 2010-04-18
Glad it worked out for you. I may try the wait myself since it looks like my one machine isn't going to work out otherwise. Once you get past the initial install issue you will probably lovee the system. Good luck.

---

