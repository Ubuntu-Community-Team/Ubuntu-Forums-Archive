---
title: "trouble installing ubuntu"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by speighty118 on 2012-05-14
Hi,

Well basically my windows 7 system crashed a few days ago so i
went to use my system repair disk and i then realised half way through doing a fresh install of win 7 that i remembered i didnt burn the disk correctly so then my laptop wouldnt boot at all anymore i have had lots of trouble in the past with this laptop so i wanted to put ubuntu on it seen as it is free and i dont have the money to get it repaired at first ubuntu installed correctly but kept freezing and things so to cut a long story short i have been trying to reinstall ubuntu ever since (formatting the HDD with boot n nuke i think it is) formatting it through the live CD (disk utility) and just basically trying everything but it still kept freezing at the wireless screen during the installation so i decided to try another distro XUBUNTU but that also froze on the wireless page on the installation so i was advised to try the alternate ISO which i did and everything was going fine until it froze on 47% on the partitioning section, and i also forgot to mention that when i tried formatting the HDD on boot and nuke it also failed... i have run tests on the HDD but there are no errors and nothing wrong with it?

what can i do?

---

### Post by speighty118 on 2012-05-14
Hi,

Well basically my windows 7 system crashed a few days ago so i
went to use my system repair disk and i then realised half way through doing a fresh install of win 7 that i remembered i didnt burn the disk correctly so then my laptop wouldnt boot at all anymore i have had lots of trouble in the past with this laptop so i wanted to put ubuntu on it seen as it is free and i dont have the money to get it repaired at first ubuntu installed correctly but kept freezing and things so to cut a long story short i have been trying to reinstall ubuntu ever since (formatting the HDD with boot n nuke i think it is) formatting it through the live CD (disk utility) and just basically trying everything but it still kept freezing at the wireless screen during the installation so i decided to try another distro XUBUNTU but that also froze on the wireless page on the installation so i was advised to try the alternate ISO which i did and everything was going fine until it froze on 47% on the partitioning section, and i also forgot to mention that when i tried formatting the HDD on boot and nuke it also failed... i have run tests on the HDD but there are no errors and nothing wrong with it?

what can i do?

---

### Post by kc1di on 2012-05-14
almost sounds like it could be a problem with bad ram stick. 
try running a memory test and see what happens. if it is bad you'll have to replace the ram.  Or at least try removing it and re-installing it.
Just a thought.

---

### Post by darkod on 2012-05-14
You mentioned wireless screen many times, did you try not to connect it to internet during the install? It has everything needed on the cd, no need for internet during installation.

Also, the problems with the laptop might be hardware related so ubuntu might have issues too.

---

### Post by speighty118 on 2012-05-14
I have tried installing with and without wireless yes
and what could the hardware issue be?

---

### Post by darkod on 2012-05-14
Not sure, you said you had lots of trouble without further info, so you know with what you had trouble.

What wireless card does it have, Broadcom?

I think there is some bug with Broadcom.

PS. Without trying to install, can you boot with the cd and load the live mode (Try Ubuntu)? Does it load the desktop correctly?

---

### Post by speighty118 on 2012-05-14
sorry im really not sure what wireless card it has
my laptop is a advent modena m100

and i can go into live mode on ubuntu and xubuntu without any
problems...

---

### Post by speighty118 on 2012-05-14
the mem test came back fine this is blowing my mind i have
tried everything :(

---

### Post by darkod on 2012-05-14
In live mode, if you run in terminal:
lspci

It will list all PCI devices including the wi-fi card manufacturer and model. Then you can google if there are any issues with this card and ubuntu.

---

### Post by lisati on 2012-05-14
Threads merged. 

Please do not create multiple threads for the same problem, it dilutes the community's ability to help.

---

### Post by stevei2x on 2012-05-14
I got the latest version of Ubuntu installed but when I run it, it says the resolution needs to be changed. I can't even get to the command prompt. I'm dual booting an old Acer with XP. With XP the resolution is fine at 1028 X 1024 but when I boot to Ubuntu, it appears to be 640 x 480.

---

### Post by kc1di on 2012-05-15
> **stevei2x said:**
> I got the latest version of Ubuntu installed but when I run it, it says the resolution needs to be changed. I can't even get to the command prompt. I'm dual booting an old Acer with XP. With XP the resolution is fine at 1028 X 1024 but when I boot to Ubuntu, it appears to be 640 x 480.
First you should start a seperate thread for this problem because it is not the same problem this thread started with. 

Secondly we need much more information to help you. 
What video card is the box using.
if you could go to a terminal and type 
```
lspci
``` note 1 is a Lower case L not #1.
and post the results it would be helpful.

---

### Post by darkod on 2012-05-15
Did you install or activate any video drivers?

Limited resolution is usually because of missing driver so it works by default in a low resolution. The same happens in windows especially XP until you add the driver.

Look around to activate any video drivers it might offer. In the latest version I am not sure where the option is exactly, was it in Hardware or similar.

You can open the Dashboard and search for Hardware in the search line.

---

