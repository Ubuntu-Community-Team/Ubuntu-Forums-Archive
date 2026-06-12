---
title: "blank screen"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by Cubedout on 2007-11-10
hi im trying to install 7.10 64bit onto my pc. ill select start of install ubuntu and it will do all the loading screens. altho when they are done the screen jsut goes blank. 

i tried again with a 7.04 standard disk and exactly the same thing happend. 

ive been running windows on my pc for quite a long time. so i cant remmeber if i had it on my current pc or my previous pc. ive only rly had it on my laptop recently. but what could be causing it to do this?

---

### Post by Cubedout on 2007-11-10
ok little update.. ive now got a little flashing comand line style line.. this is after the loading screen. and here its jsut stays

---

### Post by weblordpepe on 2007-11-10
facinating. I wonder if the video driver or something doesnt work with your hardware? What happens if you select safe-video mode? I think there's that option from the menu.

---

### Post by Cubedout on 2007-11-10
ive pretty much tried them all. i even took out the splash screen to see what it sed b4 it happens but its jsut like where its finished on the load bar. after its loaded all the stuffs... 

it will oad on my laptop but not the pc. 

the pc is

amd 64 x2  running at 2010mhz
2gb ram
nvidia gt6600 pci-e 128mb

altho i mite rip out some pci cards and see what happens.. i reply again in a minit

---

### Post by Cubedout on 2007-11-10
hmm that didnt quite work.. meh

i have no agp slots to try any of my other gfx cards in :( so im pretty stuffed with trying aother card

---

### Post by Cubedout on 2007-11-11
just got into a console tried aload of things with xfeconfig... or somet along those lines.... 

still havent got it working.. i managed to install suse linux, so i know some stuff will run. although rly i would like ubuntu.

---

### Post by Cubedout on 2007-11-11
another update... was up allnight tring to get this to work, ive downloaded the alt version but still nothing . ive changed gfx settings and isntalled nvid drivers from the console. but still i get a blank screen

---

### Post by Pumalite on 2007-11-11
What about this:

Ctrl+Alt+F1 to get command line, then:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by Cubedout on 2007-11-11
```
Fatal server error:
Server is already active for display 0
             if this server is no longer running, remove /tmp/.X0-lock
             and start again
```

thats what i get after typeing startx

---

### Post by Pumalite on 2007-11-11
After getting the command line:

sudo /etc/init.d/gdm stop
Then run the command I gave you.

---

### Post by Cubedout on 2007-11-11
```
sudo: /ect/init.d: command not found
```

---

### Post by Cubedout on 2007-11-11
i tried that using the live cd and this time it did work.. altho i still cant startx doe the same reason as before and still i have a black screen..

also i jsut noticed a typo.. going bk to try again

---

### Post by Cubedout on 2007-11-11
rite ok.. did it all as sed.. but im bk to stage 1 again. black screen

---

### Post by Pumalite on 2007-11-11
Cannot do it with the Live CD. Have to do it all at the blank screen.

---

### Post by Cubedout on 2007-11-11
ignore the live cd. im bk using whats installed on my pc. did everything said and it jsut takes me bk to the blank screen

---

### Post by Cubedout on 2007-11-11
ive done it!!"!£"!$£%£$£!!

and it only took 24 hours.. i can go to bed now :guitar:

a little thing came up in the console saying about an error accessing pci:4:0:0 so i thought hold on... reloaded paused at boot and looked... my display is at 5:0:0.... damit lol 24 hours for that :S

---

### Post by Pumalite on 2007-11-11
Good for you. It illustrates the need of posting very complete, detailed error messages.

---

### Post by VgForce on 2007-11-12
i have the same problem. so i guess i have to wait it out :confused:

---

### Post by Pumalite on 2007-11-12
You don't have to wait. Post detailed problem with error message if any in a new thread.

---

