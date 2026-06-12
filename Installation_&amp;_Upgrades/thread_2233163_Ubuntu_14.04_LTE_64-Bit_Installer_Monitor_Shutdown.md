---
title: "Ubuntu 14.04 LTE 64-Bit Installer Monitor Shutdown"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by waterlubber on 2014-07-06
I just finished building my new computer, and popped in my recently installed 64-bit disc and an old PATA drive connected on IDE, (it worked, I could access a busted Windows OS). The installer showed the little guy next to a keyboard on the purple background, then showed the Ubuntu loading screen. A terminal window, white on black, displayed various things initializing successfully. Finally, jut before something would happen, the video output from the computer blanked out. I removed the PATA drive, then proceeded to hookup a SATA one from my laptop running Ubuntu 32-bit. The computer booted an ran fine. I browsed around and shut it down. I tried the install disc again, same result. Finally, I tried ANOTHER SATA drive running 64-bit Windows. Same result! I tried disconnecting the graphics card and running the blue cable, (VGA, I think? The blue one with pins in it) directly into my motherboard, an it still didn't work. Messed in my bios. Kinda upset right now.

Graphics Card: EVGA GeForce 8400 GS
MotherBoard: Gigabyte AM3+ Motherboard
I'm relatively new to Ubuntu (like 6 or so months)

SOLVED!!!
I reburned a new CD after diskchecking and booting into nomodest. Thanks all who helped!!!

---

### Post by grahammechanical on 2014-07-06
The Ubuntu live session uses an open source video driver that apparently is not doing too well in detecting the video modes of the monitor.

1) at the first purple screen (with the icons of a keyboard and a human) press Enter
2) at the select Language screen select the language (default is English) and press Enter
3) at the underlying screen with the options to Try Ubuntu - Install Ubuntu press F6
4) at the bottom right of the screen a small menu will appear. Select nomodest and press Enter
5) press Esc to get back to the Try Ubuntu - Install Ubuntu screen and Try Ubuntu should be selected - press Enter.

See how that goes. Sometimes we need a combination of those F6 options to get a live session or an install session running. 

Regards.

---

### Post by waterlubber on 2014-07-06
Thanks! I was wondering how to get to the menu, I'll try tomorrow because I need to sleep.

---

### Post by Bucky Ball on 2014-07-06
> **grahammechanical said:**
> 
4) at the bottom right of the screen a small menu will appear. Select nomodest and press Enter


grahammechanical means 'Select nomodeset ...' ;)

---

### Post by waterlubber on 2014-07-07
Alright, I selected nomodest and booted that way. I got a rather bland white text: "Ubuntu 14.04" on the famous purple screen of doom...there were only 4 dots. The screen then changed to white text on black background with yellow dots, and the monitor blinked out but was still recieving a signal. The weird black andyyellow screen came back and the monitor went absolutly nuts, as if it was a dirty connection (I checked. :P) and some log text was showing by the loading screen. Then, after another crazy blink, I got the dreaded single blinking cursor of doom. CTRL + ALT + F1 got me into a rudimentary terminal. most commands work. What do I do now? I read the sticky and I haven't a clue what any of that means...i know what grub is, but that's about it. Also, CTRL+ALT+F7 takes me back to the blinking underscore screen.

---

### Post by waterlubber on 2014-07-07
Will it be possible/safe if I install ubuntu on another computer by inserting a hard disk and the CD, running the process, and then putting the hard disk back into the new computer?

---

### Post by waterlubber on 2014-07-07
!!! Just ran DiskCheck from the ENTER Man Menu, it found errors in one file. Going to reburn, maybe that will fix it.

---

### Post by Bucky Ball on 2014-07-07
You have marked this as solved. How did you fix? Please share.

Incidentally, you sound like you're almost there. When you hit that screen with the cursor after boot, was it a login in cursor asking you to login?

---

### Post by waterlubber on 2014-09-13
Oh, my disk was corrupted. Sorry, just recheck this post now.

---

