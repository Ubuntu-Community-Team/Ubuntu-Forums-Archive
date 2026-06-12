---
title: "Black Screen AFTER installing ubuntu 8.10"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by lazy_bones1987 on 2008-11-28
Hey Everyone, 
I'm a fairly new linux user and I seem to have a problem with ubuntu 8.10 after installing it.

Well firstly, Here are my specs:

Acer Aspire 5710
Intel Centrino Duo 2.0Ghz
1 Gb ram
ATI Radeon HD 2300 (128mb)
140 GB HDD

and I'm running vista (Home Premium) 32 bit at the moment as my primary OS. 

To make sure everything was working fine before i could do a dual installation, i ran the live cd and it worked like a charm.
Everything works fine in the live cd....the internet, sound, graphic drivers (even the special effects seemed to be work fine)

I thought wow...after having a bitter experience with Ubuntu 8.04 and 7.10 (I couldnt install those at all coz of driver issues and stuff) I thought this is it!

So I used the wubi installer to install ubuntu in my D drive (I didnt wanna use C just to be safe as the primary OS is installed there). Gave it a healthy space of 15 gb. Finished the installation and the rebooted.

I went inside Ubuntu which started doing its installation and copying of files and stuff. So far so good.....

And then once it finished its installation and copying of files (100 %), the screen went blank and i see a cursor blinking. I thought maybe its restarting and thats why it must be doing this.

I wait for nearly 10 mins and nothings happening except for the cursor blinking on the black screen. I press the caps lock key to see if anything is processing. Nope. So i manually shut it down and then load ubuntu.

It loads like 20-30%....rests for a while....and then it loads a bit (not completley)....after that it takes me to a command line asking me for my password and username.

 I enter those correctly. But it doesnt get me into the main GUI screen yet.

It shows me a lot of the this error msg:
-bash: /dev/null:Permission denied

 I'm still in command line (or terminal to be precise). So i use 'startx' (something which i learned from my csci labs :) ) to start a new session. It showed signs of starting a new session (i can see the mouse pointer and stuff) and then poof....back to the command line again!

So I shut it down and load it again in recovery mode. It shows signs of the same symptoms in the splash screen (going very slow after 20-30 % ) and then this time, before i'm asked for my username and password in the command line, it shows a lot of warnings: fake daemon running (or something like that) and i cant even use startx!

So i didnt know what to do, uninstalled ubuntu and did a fresh installation (wubi and in the same D drive). Reboot. Install and copy files 100% and then a blank screen again with the dreaded cursor blinking. I still wait for about 10 mins and nothing yet happens. So I manually shut it down (again) and then load ubuntu and unsurprisingly i have the same problem as what i described before....doesnt load properly and i'm not able to come out of the terminal.


Can anyone please please help me with this problem?

---

### Post by the lush on 2008-12-03
Well, you may have found a solution by now, but if not, try searching for ATI Blank Screen (or words to similar effect). For some reason 8.10 uses a new xorg file  that completely arses up ATI graphics. There are lots of threads about this problem. You might find a solution, or like me you may just have to wait for 9.04 whilst checking in from time to time to see if a new installer is available.

Good luck.

---

### Post by saul11 on 2009-03-07
I have the same problem, also using wubi and ubuntu 8.10, posted at [http://ubuntuforums.org/showthread.php?p=6853471#post6853471](http://ubuntuforums.org/showthread.php?p=6853471#post6853471)

Gone try the xorg.conf midifications now...

---

