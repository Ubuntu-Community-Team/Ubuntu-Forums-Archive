---
title: "Can't install Ubuntu"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by Mr.Money on 2011-06-27
HI, i'm trying to install ubuntu on my windows 7 computer as my main os. I followed instructions on ubuntu website and created a cd, i put the cd in the computer, restarted the computer and then i see ubuntu logo and it shows like it's loading, after a few minutes all i get it's a bunch of squares on the screen, it looks like my video card is bad, but it's not because everything works fine whe i boot windows 7

---

### Post by Quackers on 2011-06-27
Welcome to UF.
It seems you may have a small graphics problem. What graphics card are you using?
If it's Nvidia or ATI try the nomodeset boot option and see if the live desktop will appear.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by garvinrick4 on 2011-06-27
#Tell users what type of Video card you have and this will give it a bump up to the front.
I do not have this trouble but it can be the nomodeset option at boot:

#nomodeset from Ubuntu:

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. 
While this is a major step forward for the graphics architecture in 
Ubuntu, in some rare cases KMS will prevent your 
video output from working correctly, or from working at all. 
If you need to disable KMS, you can do so by booting with the nomodeset option:

##To do so when you see the 3 items at the bottom of Ubuntu splash screen hit any key at all
and some menu items on bottom of screen hit F6 and then choose nomodeset and then continue to boot.

#Worth a shot to see if helps you.

---

### Post by garvinrick4 on 2011-06-27
Good Day Quackers seemed to be typing same time as you, same salution enjoy your day.

---

### Post by Quackers on 2011-06-27
Good evening to you too garvinrick4 :-)
We've got to stop meeting like this :wink:

---

### Post by Mr.Money on 2011-06-27
thanks for the quick reply. I did some reading in the forums and found out that i needed to go into nomodset, i did and now i'm installing as we speak. One more question, after installing ubuntu do i have to go back and uncheck nomodset and will the graphics work fine? Sorry , i forgot to mention it's an Nvidia

---

### Post by Quackers on 2011-06-27
Further down the page in the link I gave you earlier it explains what you need to do.
On first boot you need to use nomodeset again, but the method is different this time. The nomodeset boot option is a one time only deal at this stage.
If you then install video drivers you may or may not need to use it again. 
If you do need to use it after you can make the change permanent by editing a file (explained in the link), but you probably won't need to.

---

### Post by Mr.Money on 2011-06-27
thanks dude, sorry for the noob question but this is the first time installing ubuntu, i got tire of windows so i decided to try something new. i'll let you know how it goes when i'm done installing ubuntu.

---

### Post by Quackers on 2011-06-27
No problem. We all asked no0b questions at one time :wink: 
Actually, I still do!

---

### Post by Mr.Money on 2011-06-27
thanks a lot for help, i was able to make it run but i don't know if it's because i'm new to linux or installing programs is not easy? for example, i do a lot of movie streaming to my ps3 and linux is not compatible with tversity, so i searched and found mediatomb but is not too simple to install it and make it run

---

### Post by Quackers on 2011-06-28
Always look in synaptic package manager first, to see if the program you want is available there. It may not be, but if it is it's a lot easier to install.
Other installation instructions can be found around here or with google.

---

### Post by mastablasta on 2011-06-28
use software center or synaptic package manager (for even mor esoftware). you search for programme through them and if you find it then you just mark it for install or simply click install.
 
if programme is not there then the easiest way is to Find a PPA or .deb file (kind of like windows .exe installer files).
 
if this is still not an option then you will need to build from source. and usually there are install instructions within the .tar file (which is kind of like zip only more compressed).

---

### Post by Mr.Money on 2011-06-28
Thanks. Is synaptic already installed on linux?
yesterday i installed arround 10 different softwares and 7 out of those 10 were a pain to install, I had open something called terminal and type different commands in order to install the program. So far i like linux, it's fast but installing some programs could be a lil complicated

---

