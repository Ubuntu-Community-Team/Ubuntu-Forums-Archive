---
title: "Cannot install Ubuntu on a Sony Vaio desktop"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by bratman91 on 2011-02-09
I am trying to install Ubuntu 10.10 on a Sony Vaio RX456DS Desktop (2001 vintage) which currently has Windows ME installed. As far as I can see, the Ubuntu disk is sound and the PC boots up from it. However, the initial screen looks very plain (no colours, text badly placed, not at all like the Welcome screen I expected) and if I select "Install" or "Try", I get a Ubuntu logo in the centre of the screen with 5 small red dots that progress from left to right, and then repeat this. Nothing else happens, even after a long time. Also, the initial screen has two more options - "Check the disc" and "Test the Memory" (or something similar). Can anyone suggest what, if anything, I should try now?

---

### Post by Quackers on 2011-02-09
Welcome to Ubuntu and UF.
I would first try selecting the "check the disc for errors" option, just to make sure the disc is ok.
You don't say which graphics card you are using. As this seems it could be a graphics issue, that info would help.
There are boot prompt options which might help.

---

### Post by amsterdamharu on 2011-02-09
Can you select "try ubuntu" and see if there is any output when you press control + alt + F1 or F2,F3 ...?

---

### Post by coffeecat on 2011-02-09
Two things come to mind as possibilites: insufficient RAM for the live session and an old, problematic video chipset. So - how much RAM do you have and what is the video? Also, please post some specifications. Have you posted the model number correctly? I tried googling "RX456DS" and I got only one hit - this thread! Which is good for google since you created the thread only minutes ago.

---

### Post by bratman91 on 2011-02-09
Sorry, I mistyped the model number  - it is a PCV-RX465DS. It has, according to the sticker on the front of the tower, "Cutting-edge graphics, Nvidia Geforce2 MX and 32 MB VRAM@, Pentium 4 1.4 Ghz processor, 128Mb PC-800 RDRAM". Does this help?

---

### Post by Quackers on 2011-02-09
I think the ram may be a bit low. As I understand it the recommended minimum is 256MB. There may be other versions that might work (I think lubuntu is one). See what the others think :wink:

---

### Post by bratman91 on 2011-02-09
> **amsterdamharu said:**
> Can you select "try ubuntu" and see if there is any output when you press control + alt + F1 or F2,F3 ...?
 
 
The keys you mention do not result in anything. However, when I pressed ESC, I got a black screen with text indicating that something was being loaded. I got a full screen of this but it seemed to get stuck on this line:
 
Enabling additional executable binary formats binfmt-support

---

### Post by P4man on 2011-02-09
128 MB is not (nearly) enough to run Ubuntu.
You might want to try another distro like slitaz, puppylinux or any other super light weight distro.

---

### Post by bratman91 on 2011-02-09
> **P4man said:**
> 128 MB is not (nearly) enough to run Ubuntu.
You might want to try another distro like slitaz, puppylinux or any other super light weight distro.
 
 
OK, many thanks for that advice - I honestly hadn't considered that the RAM would be too little. Would 512Mb be sufficient as the Sony can be expanded to that (assuming I could get the RAM - the PC is getting on in years and Sony tend to be very parochial with their hardware)

---

### Post by Quackers on 2011-02-09
Yes, that would be much better (but 1GB would be even better :-) ). The ram sticks should be available without any problem, but make sure you buy the right type/size etc.

---

### Post by P4man on 2011-02-09
> **bratman91 said:**
> OK, many thanks for that advice - I honestly hadn't considered that the RAM would be too little. Would 512Mb be sufficient as the Sony can be expanded to that (assuming I could get the RAM - the PC is getting on in years and Sony tend to be very parochial with their hardware)

That PC has Rambus RDRAM, which was rare and very expensive at the time, and I suspect will be very hard to find today. Well, you can try. Dont be shocked when you see the prices though, you might be better off replacing the entire box, especially since 512 Mb is only borderline enough for ubuntu.

If you dont want to spend money, have a look at those lightweight distro's. they are quite useable even with just 128 Mb.

---

### Post by Quackers on 2011-02-09
Aha! I stand corrected :-)
I assumed it would have been sdram - but evidently not! You know what they say about assumption!

---

### Post by bratman91 on 2011-02-09
> **Quackers said:**
> Yes, that would be much better (but 1GB would be even better :-) ). The ram sticks should be available without any problem, but make sure you buy the right type/size etc.

 I am not sure that the Sony can be expanded above 512MB. The sticker on the front of the tower says "128Mb expandable to 512MB" - I don't know why.

---

### Post by coffeecat on 2011-02-09
In point of fact 512MB is enough to run Ubuntu quite comfortably - I have a Vaio laptop with only 512MB RAM and I used it to run various versions of Ubuntu, and other distros, over several years. It will still happily run Maverick from the live CD, and the live session needs more RAM than a hard drive install. Having said that it sounds as though extra RAM is going to be prohibitively expensive, so a lightweight distro as has been suggested would be advisable.

---

### Post by P4man on 2011-02-09
Prices dont seem that bad after all. First hit on google:
[http://www.memorystock.com/memory/SonyVAIOPCVRX465DS.html](http://www.memorystock.com/memory/SonyVAIOPCVRX465DS.html)

They also claim you can go up 1 GB, using 4x256Mb modules. Its quite possible at the time the machine was bought these modules didnt exist yet, hence the sticker saying it supports up to 512 Mb (using 4x128 MB modules which did exist back then).

Mind you: its entirely possible something else wont work with ubuntu on that machine, given its age. Particularly the videocard could be a problem. Id think twice before spending any money on upgrading it.

---

