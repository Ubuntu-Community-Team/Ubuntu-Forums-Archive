---
title: "boot &quot;failure&quot; on pavillion g6x, clearly a problem with the video card"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by ijason on 2012-05-26
greetings. 

i have recently bought a pavillion g6x, with the Radeon 7450m video card. it came infected with windows7, and i mean to correct that. but i have run into trouble with ubuntu. 

i can boot off the usb stick, and i get the blinking " _ " cursor in the upper left hand corner for a moment, and then the screen goes out. if i let it sit long enough, it will finish booting, but still nothing on the screen. caps lock light works, etc. 

i can get Mint Linux working fine, but i'd like to give kubuntu a try and am thinking i just need to make some adjustments to the boot sequence to change something with how the video card is being handled. 

suggestions greatly appreciated :)

---

### Post by jadtech on 2012-05-26
I installed on a  hp pavillion G6 notebook a few weeks ago right out of the box  from dvd boot up installed ubuntu  installed the wireless and video card  runs like a champ

how ever frist thing I did have to do before ubuntu install was bios update then I had to go in to bio and fix the boot order to boot dvd and usb then hard drive then network ..

to be honest I have never really used  windows that came installed on the drive just sits there waiting  I have been using ubuntu on 60gb of the hard drive ...

---

### Post by ijason on 2012-05-27
thank you for your reply.

does your laptop have the same radeon video card mine does, or does it have the intel video card? i have not tried a bios update, but my boot order is not the problem.

---

### Post by ijason on 2012-06-06
well! i found a solution in another thread - although it didn't show up under any of my search terms :(

i'll go ahead and fill in the process so that any other pavillion user with the same video card and my same problem may find the answer here :)

boot off the cd/usb, and in the menu that shows up at the very beginning highlight the "boot normally" option. hit TAB instead of enter, to get access to the command line that will be used to boot your machine. 

in that command line, replace the word 'splash' with 'nomodeset'. then hit enter and hopefully everything will boot up for you like it did me!

---

