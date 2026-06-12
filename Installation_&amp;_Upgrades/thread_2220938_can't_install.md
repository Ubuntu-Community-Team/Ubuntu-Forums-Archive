---
title: "can't install"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Hamdaan_Hassan on 2014-04-30
when i try to install ubuntu in my pc it's just loading ubuntu 14.04 . when i press the esc button it showing there's an error . i tried to install with my usb stick . other pc s can install but its not wokin to my pc :( ... :'(

---

### Post by kc1di on 2014-04-30
could you give us a little more information to go on? 
for starters what make and model is your computer, How much ram What video card are you using?

That information would help us help you get it going.  

I suspect it's a video card problem you might want to try booting it with the nomodset parameter. 
you can do that by hitting the left shift key when ubuntu begins to boot, go to f6 and select nomodeset from the menu hit esc key then enter.

---

### Post by Hamdaan_Hassan on 2014-04-30
Intel pentium 4 cpu 2.40 GHz , 1.50 GB ram , 64 on board VGA .

---

### Post by mörgæs on 2014-04-30
For this hardware Lubuntu is a better choice.

---

### Post by kc1di on 2014-04-30
would have to agree with mörgæs  Lubuntu would be a better choice for you hardware.
I doubt that your video card is new enough to boot unity , it requires 3d. 
Try Lubuntu

---

### Post by Hamdaan_Hassan on 2014-04-30
How to install VGA drivers in ubuntu 14.04 ?  my resolution is very big i can't increase the resolution i think i have to install the drivers .  please help me .

---

### Post by frank18 on 2014-04-30
> **Hamdaan_Hassan said:**
> How to install VGA drivers in ubuntu 14.04 ?  my resolution is very big i can't increase the resolution i think i have to install the drivers .  please help me .

try to see if you have additional drivers,you can open software&Updates center and click where it sais additional drivers.
or  if you have ATI AMD video card could type this in terminal,  

apt-get update
apt-get install fglrx fglrx-amdcccle fglrx-dev

or


sudo apt-get install fglrx-control

---

### Post by mörgæs on 2014-04-30
Threads merged. Please open only one thread per subject.

For a 64 MB card there are no additional AMD drivers. You need to post all hardware details, especially about the graphics card, in order to get better help.

---

