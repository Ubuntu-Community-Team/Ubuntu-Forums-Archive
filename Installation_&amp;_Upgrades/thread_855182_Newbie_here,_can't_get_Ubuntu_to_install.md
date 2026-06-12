---
title: "Newbie here, can't get Ubuntu to install"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Desidarius on 2008-07-10
Here's the situation, I've got a dell Inspiron E1705 and I meant to resize my windows partition and make the left over space a linux partition to play with since I never got a windows disk (dell never sent one and my laptop is a few years old now). During the resizing I suddenly got an error and to make a long story short, I'm now stuck using linux. The problem is I have an Ubuntu 7.10 disk, but I can't get it to install (I'm currently using Sabayon linux which was the only distro I had a live cd for that detected everything and worked from install). I can't even get the Ubuntu live cd to run. Every time I get past the start screen I choose install or run and I end up having a black screen with a black screen with a section that has a bunch of tiny squares or short angled lines so I know it has something to do with the graphics, but I can't find any sort of graphics options to change. Safe graphics mode had no effect and beyond that I'm not really sure what to do.I'm not sure how to find it in Sabayon, but I believe the graphics card I have is an ATI mobility radeon x1400. I still want to use Ubuntu, but I don't know what I can do to get Ubuntu to install or if I should start getting used to Sabayon.

---

### Post by G33 on 2008-07-10
Hey i just posted the same question, im getting the same rubbish at the top of my screen. Ive been able to successfully run off the live CD using safe mode. After that, not sure.

---

### Post by Desidarius on 2008-07-12
Still can't get it to work. I've looked through the help options and none of the ones listed (the one that says some dell computers may need it, and the one that said to use if you have graphics problems (the vga=771 one)). The farthest I could get this time is some error right around after gnome something starts to load (I wrote it down, but I forgot to bring it with me(I can't connect to the open wireless near my place, I have to use the free wireless at a coffee shop several blocks away)). I'm hoping there is some boot argument somewhere that would work if I just knew where it was. The only other thing I've been able to tell is that the highest settings any linux distro I've tried will work with (Sabayon, Knoppix, Puppy linux) is 1024x768 which is kind of annoying since I have a wide screen. I also noticed when I try using Knoppix I get the same graphics trouble when it's at the "starting X Windows" message and then after a few tries it switches to starting Xorg and then it works. I'm not sure if that reveals anything more about my situation or not, but hopefully there is someone out there who can help me out.

---

### Post by upchucky on 2008-07-12
you both need knoppix and supergrub.

knoppix will let you mount all partitions and then you can edit the files needed to fix the xorg file for screens.

the above can be done with the live cd you used to do install but knoppix is easier. (in my opinion) because it can also repair windows files too.

advanced supergrub will repair windows and linux bootloaders.

---

