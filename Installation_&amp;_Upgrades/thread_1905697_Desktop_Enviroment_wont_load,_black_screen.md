---
title: "Desktop Enviroment wont load, black screen"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by cep3431 on 2012-01-07
I started a thread and was told to post another here the link to the thread:[http://ubuntuforums.org/showthread.php?p=11593532](http://ubuntuforums.org/showthread.php?p=11593532)

"I have a Dell Inspiron 2500, It had Windows ME on it and ran fine. I  Upgraded the ram from 64mb to 192mb it ran faster but i wanted linux so i  tried to boot the xubuntu live cd it went to a black screen and didnt  change even when i left it for a few hours. I installed xubuntu via  alternate install cd and install went fine, when i booted it it it went  to a black screen and an "X"  (like a cursor)showed up for a second. I  can get to the terminal by pressing ALT+F2 and get to a login.  I dont  have high speed internet at home so im going to try to install lubuntu  when i get home. I think it might be a graphics issue but i dont know  where to start."

"Today I tried to install lubuntu but the same thing happened. I want to  install mythbuntu I know i will have to upgrade the ram but i want to  make sure I can get a *buntu to install."

As I said i think it is a graphics issue. I have installed xubuntu on a Dell Latitude with 128mb of ram it was slow but worked. Thanks!

P.S. I am kind of new to the fourms I think there is a way to move my thread but i dont know how.

---

### Post by serge_o on 2012-01-07
I can confirm that I saw the same behaviour on old hardware with less than 192 RAM and it was related to bad graphic cards. However, I did not solve the issue for myself, I just dropped it...

the question is whether it would be possible to resolve at all for you (without making major changes to ubuntu).

maybe debian 3 sarge would work better?

> **cep3431 said:**
> I started a thread and was told to post another here the link to the thread:[http://ubuntuforums.org/showthread.php?p=11593532](http://ubuntuforums.org/showthread.php?p=11593532)

"I have a Dell Inspiron 2500, It had Windows ME on it and ran fine. I  Upgraded the ram from 64mb to 192mb it ran faster but i wanted linux so i  tried to boot the xubuntu live cd it went to a black screen and didnt  change even when i left it for a few hours. I installed xubuntu via  alternate install cd and install went fine, when i booted it it it went  to a black screen and an "X"  (like a cursor)showed up for a second. I  can get to the terminal by pressing ALT+F2 and get to a login.  I dont  have high speed internet at home so im going to try to install lubuntu  when i get home. I think it might be a graphics issue but i dont know  where to start."

"Today I tried to install lubuntu but the same thing happened. I want to  install mythbuntu I know i will have to upgrade the ram but i want to  make sure I can get a *buntu to install."

As I said i think it is a graphics issue. I have installed xubuntu on a Dell Latitude with 128mb of ram it was slow but worked. Thanks!

P.S. I am kind of new to the fourms I think there is a way to move my thread but i dont know how.

---

### Post by cep3431 on 2012-01-07
I just tried DSL and it worked fine. I still want to use a *buntu. I may have to try debian.

---

### Post by Toz on 2012-01-07
When you boot the Xubuntu live cd, at the screen where it asks you to run or install, press F6 and select the nomodeset option. Then continue with the boot.

---

### Post by MAFoElffen on 2012-01-08
> **cep3431 said:**
> I just tried DSL and it worked fine. I still want to use a *buntu. I may have to try debian.
Here's the skinny on your hardware...

Intel Pentium III or celeron CPU
Intel i815 Video GPU
2 x SoDIMM meory slots that came w/ 64MB but will support 256MB SoDimms 
. . 2 x 256MB maxed it out at 512MB.

Ubuntu needs 758MB minimum to bring up the desktop. Ubuntu says 1GB minimum.  Even though your video will only display 2D graphics, booting and effectively running Ubuntu would not be possible with your hardware... 

Xubuntu runs great in 512MB. Lubuntu runs good in 384MB. I've brought both up in 192MB, but the desktop screen washes out and there is quite a lag when it runs out of memory. It sometimes locks up, because of running out of memory.  Adjusting the swap partition size didn't make up for not having enough memory.

So with what you have at present / today, that leaves you with a fine running Ubuntu derivative, Puppy Linux.  The one I use for low memory hardware is the Puppy version based on Ubuntu Lynx (10.04 LTS).

If you maxed your memory to 512MB, then you have more options.  The one thing to be aware with your graphics if your do upgrade your RAM and want to try a full sized distro... If you do need to used a kernel boot option, rather than "nomodeset", use "i815.modeset=0"

---

