---
title: "no partitionable media  were found, plz check whether hard disk is connected to cpu"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by trosmok on 2006-09-18
hello...
i was trying to install ubuntu 5.04 in my pc...with windows xp as other operating system....when the installation is in progress i was getting a msg that no partitionable disks were found on ur hard disk....plz connect it to cpu and then try again....its a repeatedly occuring problem....my hdd is sata and its 160gb...there r 4 partitions.....and out of which one drive is completely empty....all the partitions are NTFS type partitions....
now tell me guys...what can i do....to avoid this problem...tell me the solution guys...waiting for ur reply....
hope u'l get me one solution that works perfectly
thank u in advance
from shashank8-)

---

### Post by DougZ on 2006-09-18
Hoo boy have you ever opened a can of worms with this one. A lot of people are encountering the same issue.

From what I can gather the issue was introduced in the kernel(s) sometime around Flight 5 (not sure exactly when), and still exists in the Final Release. It seems to occur for all Debian based distos.

The Edgy kernel / install CD does not have this problem. What got fixed? Beats me I'm a total linux noob.

All of which does nothing to solve your problem, but at least maybe? point you in the right direction of finding a solution. If you do find one, I so want to know.

My next attempt will be:
  Install older version (say around flight 2)
  Upgrade all packages, except kernel
  Install edgy kernel
  Reboot and pray to the gods of geekdom it works

I'll let you know how it turns out.

---

### Post by randell6564 on 2006-09-18
> **trosmok said:**
> hello...
i was trying to install ubuntu 5.04 in my pc...with windows xp as other operating system....when the installation is in progress i was getting a msg that no partitionable disks were found on ur hard disk....plz connect it to cpu and then try again....its a repeatedly occuring problem....my hdd is sata and its 160gb...there r 4 partitions.....and out of which one drive is completely empty....all the partitions are NTFS type partitions....
now tell me guys...what can i do....to avoid this problem...tell me the solution guys...waiting for ur reply....
hope u'l get me one solution that works perfectly
thank u in advance
from shashank8-)

I would suggest that you get a hold of an Ubuntu 6.06 CD and try it!

S-ATA devices and Linux are still a bit tricky, but I think with each upgraded version of Ubuntu, it's becoming easier.

---

### Post by trosmok on 2006-09-20
k.... i will try this and let u know if i hav suceeded in installimg that or not....thnx dude

---

### Post by trosmok on 2006-09-23
as u told me to try installing 6.06... i hav tried installing ubuntu 6.06 and guess what, it was working and was working quite successfully...and this is whar=t i have done....i rebooted my pc with ubuntu 6.06 in my cd rom and then it started to to boot from cd....after some processes that were taking place...i got to see the live cd functioning in a 640x480 resolution and my monotor best suits 1024x780 coz its a 17 inches monitor....the problem is i cant get to see the install option located at the bottom of the screen coz the resolution is 640x480....and i cant install it coz i cant set the screen resolution in the preferences option in the live cd....what can i do to reset the screen resolution to 1024....instead of 640...
one more thing...i even adjusted the vga option present on the screen at the setup of ubuntu after reboot...by pressing f4...but that tooo doesnt solve my problem.....can anyone suggest me wat to do......
bye

---

### Post by randell6564 on 2006-09-23
> **trosmok said:**
> as u told me to try installing 6.06... i hav tried installing ubuntu 6.06 and guess what, it was working and was working quite successfully...and this is whar=t i have done....i rebooted my pc with ubuntu 6.06 in my cd rom and then it started to to boot from cd....after some processes that were taking place...i got to see the live cd functioning in a 640x480 resolution and my monotor best suits 1024x780 coz its a 17 inches monitor....the problem is i cant get to see the install option located at the bottom of the screen coz the resolution is 640x480....and i cant install it coz i cant set the screen resolution in the preferences option in the live cd....what can i do to reset the screen resolution to 1024....instead of 640...
one more thing...i even adjusted the vga option present on the screen at the setup of ubuntu after reboot...by pressing f4...but that tooo doesnt solve my problem.....can anyone suggest me wat to do......
bye
HI! Not sure that I'm following you here! You say that you are able to get to the desktop using the Live CD correct?  I'm not aware of any "install option located at the bottom of the screen". There should be an icon at the upper-left hand side of your screen that is the installation link.

I'm sure that your monitor looks best at "1024x780", but "640x480" should still produce a recognizable Desktop!

AND also.,you just said that it "was working, and working quite successfully", so I'm a bit confused!

---

### Post by trosmok on 2006-09-23
well...i will start from the beginning...
at first before running the live cd of 6.06, i went thru with the installation procedure of 6.06...and the things were happening the same way mentioned in the guide or say tutorials....and when the desktop of the 6.06 gets loaded on my monitor and the screen gets into 640x480 resolution which is not the thing happening to all other friends who installed 6.06 with the same cd i am having...and after the live cd gets loaded i get to see the install option on the screen and in preferences option present on the top of the screen i tried to set the screen resolution from 680 to 1024 resolution...but nothing happens when i try to adjust the resolution...i dont get to see other option other than 680 and a refresh rate of 60hertz....thats it....and after pressing install option on the upperleft side as u said...i get the option select language and i cant see the option present in the bottom part of the screen that is "FORWARD"....u know better than me y thats used for....
my first problem is that i am not able to change the screen resolution in the live cd and the other thing is when i adjust the screen resolution to 1024x768 it applies to that while undergoing the installation process and it suddenly jumps to 680x480 resolution and does not hav any effect to it...even after repeated attempts to change the resolution i fail to do so....guys i need help

---

