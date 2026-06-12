---
title: "Fujitsu Lifebook C 6571 installation issues"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by mgmmitch9 on 2007-12-01
Hello all,

I am a complete novice when it comes to Ubuntu and Linux/Unix for that matter.  I just recently installed ubuntu 7.10 on my old Dell Dimension 8100 which went quite smoothly.  I recently picked up a Fujitsu Lifebook C 6571 with intentions of installing ubuntu on it, since i've loved what ive experienced on the dell so far.  Unfortunately, after inserting the live cd and getting it to boot into live mode i can hear the intro to the ubuntu music, but the screen is a wash of orange, red, white, etc mosaic of colors.  I have searched the forums but have been very confused as to what to do to fix this issue.  

As I said, I am new at this and I do much better in GUI than in the shell, so if code is going to be needed to solve my issue I need any help to be very basic and explained (sorry ).  I'm assuming the problem is a hardware issue related to the onboard video card? (but i'm not even sure how to check what the video card is...again sorry)  

If anyone can provide me with assistance, on a very basic and explained level...or very specific directions that I can follow, i'd appreciate it.  Thanks in advance!

---

### Post by Pumalite on 2007-12-01
'Maximum Memory: 192MB ~~256MB'
If the above is true, you need to install:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by mgmmitch9 on 2007-12-01
Well I'm not sure if you mean that's an error message that comes up or if it's related to the video card on the laptop.  The RAM is 512 and processor 1.3 ghz so i don't think that's the issue, and no error messages come up, the screen just goes garbled colors...but i will try using 7.04 and see what happens.   Thanks!

---

### Post by Pumalite on 2007-12-01
They are the specs I got from Google:

C6544, C6547, C6556, C6557, C6571, C6577
Fujitsu LifeBook C6537, C6544, C6547, C6556, C6557, C6571, C6577
# System Type:Fujitsu LifeBook C Series C-6537, C-6544, C-6547, C-6556, C-6557 , C-6571, C-6577 Laptop CPU: PIII 500MHz ~~ 750MHz +
# Standard Memory: 64MB ~~ 128MB (soldered)
# Maximum Memory: 192MB ~~256MB
# # of Memory Slots: 1

---

### Post by mgmmitch9 on 2007-12-01
Well now i feel like a complete idiot...I mistyped the laptop type...it is a Fujitsu Lifebook C-7651...i must be dyslexic or something...sorry for the misinformation...any suggestions for the C-7651 that i have?  I have been unable to find the video card type and think that may have something to do with the issue.  512 mb 1.3 ghz   intel pentium III  ...thanks!

---

### Post by Pumalite on 2007-12-01
You probably have a graphics problem. Try the Alternate CD.

---

### Post by mgmmitch9 on 2007-12-01
Here are the full specs just in case:   And thanks for the suggestion, i'll give the alternate CD a whirl.

Processor  	 Intel Pentium III-M 1.3 GHz
Data Bus Speed 	133 MHz
Chipset Type 	Intel 830MG
Specs Group :: Storage
Floppy Drive 	3.5" 1.44 MB floppy - integrated
Hard Drive 	40 GB
Specs Group :: Display
Display Type 	15" TFT active matrix integrated
Max Resolution 	1024 x 768 ( XGA )
Color Support 	24-bit (16.7 million colors)
Graphics Processor / Vendor  	 Intel Extreme Graphics - AGP 4x
Video Memory 	Shared video memory (UMA)
Supported Display Graphics 	VGA (640x480), XGA (1024x768), SVGA (800x600), SXGA (1280x1024), UXGA (1600x1200)
Video Output Supported 	NTSC, PAL
RAM: 512

---

### Post by Pumalite on 2007-12-01
You are OK. to go.

---

### Post by mgmmitch9 on 2007-12-02
Ok, so i finally got the alternate CD to install, but now when it boots from the HD it takes a while to load...the computer says something about unsplash: going to 1600x1200 mode...then i get a black screen for a good minute.  Next I get a pop up that says Ubuntu is running in low resolution and that it could not detect my graphics card.  It asks me to configure it myself.  The screen then becomes a blur of colors again and eventually washes away even that pop up.  I also was unable to use the mouse pad or keyboard to respond to the message.  Again, I am a complete novice so i have no idea what to do here.  Any specific directions that i could follow would be greatly appreciated.  Thanks so much for taking the time to help!

---

### Post by Pumalite on 2007-12-02
Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by mgmmitch9 on 2007-12-03
Ok, I reconfigured the xorg as stated and used the Vesa driver...i left the other options as default unless i knew the exact answers to each question.  Unfortunately after i typed : startx   i got a black screen for a few moments and then again the garbled mish mash of colored pixels.  Any further suggestions to get this bad boy up and running?  Thanks again for your patience and assistance.

---

### Post by Pumalite on 2007-12-03
Try with a different Monitor.

---

### Post by mgmmitch9 on 2007-12-03
I hooked up the laptop to my Dell Dimension 8100 monitor and it works perfectly on there.  Where do i go from here?

---

### Post by Pumalite on 2007-12-03
You are stuck with a laptop that needs an external Monitor, unless when you configure the xserver you made a mistake. In that case, try different settings for Monitor or 'Display'. Consult your Manual for your laptop's display and maybe you can configure with the exact settings that you need.

---

### Post by mgmmitch9 on 2007-12-04
I have video!  I had to use the i810 driver and allocate 48000 kb to shared video memory.  Also set the monitor type as a Fujitsu-Siemans Internal...don't know what did it, but one of those changed settings got me up and running.  Now the only issue i have is with the track pad...for some reason it is very sensitive and will select items or drag items when i'm using the track pad only (not even touching either of the 2 click buttons or the middle wheel slider)  Any suggestions for this issue?  Thanks again so much for helping me get this sucker up and running.

---

