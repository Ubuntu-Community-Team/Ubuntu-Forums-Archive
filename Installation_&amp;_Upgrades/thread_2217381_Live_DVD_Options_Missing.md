---
title: "Live DVD Options Missing"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by Roger_Bradley on 2014-04-17
I am hoping to be able to install Ubuntu, or another distro if this  cannot be resolved, as a dual boot; but cannot even get to the live  desktop to try it out first.
When I boot the live DVD, Ubuntu 13.1, I do not get any options to change the graphics mode. When booting in non EFI I get a screen with what looks like keyboard, equals and another symbol at the bottom. Then a screen with 'Ubuntu' in the middle with progress spots underneath. Booting in EFI gets a text screen to install or try Ubuntu, but again no graphics options that I can find. 
After a short wait using either option I get a scrambled mess - which indicates there is a graphics driver issue. So it looks like I need to boot using a basic/safe graphics mode. OK, I've had this with other Linux live distros, but they offer graphics options on boot
How do I set the graphics options? I have tried all the 'F' keys without result.


ASUS P9X79 DeLuxe MB 
Intel i7 3930K 3.20GHz
X2 ATI Radeon HD 7950 3027MB-Crossfire connected
32GB RAM
Samsung 830 SSD - Win 7 Pro 64bit installed

---

### Post by Double.J on 2014-04-17
Hi there,

welcome to to forums!

Are you able to get to the menu by holding shift? If so you are able to get to the menu that looks like 
[QUOTE]ubuntu 
ubuntu(recovery)
memtest
boot from hard drive[/[QUOTE]
then you can usually add nomodeset to the boot parameters by pressing either E or tab.

Jj

---

### Post by Roger_Bradley on 2014-04-17
> **Double.J said:**
> Hi there,

welcome to to forums!

Are you able to get to the menu by holding shift? If so you are able to get to the menu that looks like 
[QUOTE]ubuntu 
ubuntu(recovery)
memtest
boot from hard drive[/[QUOTE]
then you can usually add nomodeset to the boot parameters by pressing either E or tab.

Jj

Well done, that did it! Many thanks. I managed to install Ubuntu onto a second HDD. Dual boot is working OK. However when I boot into Ubuntu the desktop is a garbled mess. There is a row of vertical icons at the left and a duplicate set about halfway across the screen. The toolbar across the top seems OK. The background is partially noise and random blocks. If I click on one of the icons a rectangular shape opens that is variously black, white or just garbled noise. So I can't access any settings, or anything else. I have to use the hard reset button on the PC to restart as the logout window is unreadable. Mouse cursor is working as it should. I have no idea where to go from here as I can't access anything meaningful. 
So unless someone has an answer that works I'm going to dump Ubuntu and try another distro.

---

### Post by Double.J on 2014-04-17
Hi there, sorry to hear the issue is persisting post install. 

Are you able to use the same nomodeset trick on the installed version? 

It seems to be a graphics card driver issue by the sound of it. Do you know which card you have? Ubuntu has to adhere to quite strict licensing rules with drivers. Do you know which graphics card you have? In my experience issues arise more commonly with nvidea cards. There's more info [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") 

You may be able to log out using ctrl+alt+del, then click on the ubuntu logo next to the login box and choose ubuntu 2d

finally if the desktop will not work at all, and nomodeset and ubuntu 2d do not work, try alt+ctrl+F1 to get to a terminal 

keep us updated! 

Jj

---

### Post by Roger_Bradley on 2014-04-17
Hi again

I tried ctrl-alt-del and it didn't work. All I get is a further garbled mess. The OS underneath appears to be working fine, I just need to be able to sort out this graphics issue. I have two ATI Radeon HD 7950's fitted, connected via a crossfire link. I tried the nomodeset option and all I got was a black screen and no desktop at all. I installed Fedora 20 a few days ago on the same hardware without any issues, other than having to set basic graphics mode just for the install. 
I've searched online for an answer without any leads.

---

### Post by Double.J on 2014-04-17
Hmm, 

i too have seen a few issues with this card and ubuntu. Does grahammechanical's post in [this]("http://ubuntuforums.org/showthread.php?t=2216215") thread help? (You may have to get to the terminal with the ctrl+alt+F1 method. To get back to desktop, alt+F7)

---

### Post by Roger_Bradley on 2014-04-17
I've just installed Mint 16 and encountered the same issue. Though there is a helpful post on their forums detailing how to get into the desktop using 'nomodeset xforcevesa' on the grub boot options. That enabled me to select and install the fglrx driver from the Mint Driver Manager. All that did was stop the xserver from even starting. Maybe I'll go and re-install Fedora 20, at least that worked. 
But more likely I'll stick with Windows only. After days wasted trying to even get past the first step, ie successfully installing the OS, it seems to me that Ubuntu and Linux are just too flaky.
My hardware isn't the latest, it isn't unusual. Yet I have to manually edit stuff just to get to a point where I can get a screen image that works! Before even starting to configure the installed OS.
Thanks again for your help

---

