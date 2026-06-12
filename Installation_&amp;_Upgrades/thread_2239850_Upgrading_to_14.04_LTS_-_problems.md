---
title: "Upgrading to 14.04 LTS - problems"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by sarahfoxnz on 2014-08-16
Help. 

(I've got 2 PC's - one was Ubuntu 12.04 LTS, this PC is WIN8. )

Today i spent a few hours upgrading my ubuntu machine & now i can't get anything to go... 

a) i *can* log in.  & it appears to be logging me in,  however i then get any / all of these screens

a) fuzzy patterns over the screen,
b) the left-side menu comes up OK with a fuzzy screen in the middle
c) what looks like  a normal screen..

However i have little / no mouse actions..

Please help.

what is the MINIMUM commands i can do in the command screen in order to verify / re-check the 14.04 LTS install.. ?

So far, i am not even sure i can get into the command screen - but i'll try.

I do NOT have an install disk.

---

### Post by sarahfoxnz on 2014-08-16
Control-Alt-T  does not work (command prompt)

---

### Post by ajgreeny on 2014-08-16
> **sarahfoxnz said:**
> Control-Alt-T  does not work (command prompt)
That is the shortcut to get a gnome-terminal so if you have no unity DE running properly, that will not work either.

Use Ctrl+Alt+F1 to get to a tty command line where you can login.
However it will be helpful to know what hardware you have, particularly the graphic card, as it sounds as if you no longer have the correct graphic driver and may need simply to install the correct one again for your card.

---

### Post by grahammechanical on 2014-08-16
At the Grub boot menu select Advanced Options for Ubuntu. Open that sub-menu and select Recovery Mode. At the Recovery Menu select Resume. That may get you to a desktop using a fall back open source video driver. If you get to a working desktop go to System Settings>Software and Updates>Additional Drivers tab. Allow the utility time to find some drivers and experiment. You may find the open source video driver sufficient.

We can also get to System Settings by right clicking the desktop background and selecting Change Desktop Background.

Regards.

---

### Post by sarahfoxnz on 2014-08-16
> **ajgreeny said:**
> That is the shortcut to get a gnome-terminal so if you have no unity DE running properly, that will not work either.

Use Ctrl+Alt+F1 to get to a tty command line where you can login.
However it will be helpful to know what hardware you have, particularly the graphic card, as it sounds as if you no longer have the correct graphic driver and may need simply to install the correct one again for your card.


OK, at the main login screen (seems to be working OK, i *CAN* do Control-alt-F1, and get a terminal key.

What keys / commands do i enter to get / know what graphics card I have ? 

PS1 :- I am not dvanced / knowledgable about useful / advanced terminal commands...

PS2:- When i do boot up (before the usual login screen,i get a list of files not found / directory not found.

PS3 :- Before i upgraded., the actual PC is a bit old, but Linux performed as expected, just a tiny bit slower than my new PC

---

### Post by sarahfoxnz on 2014-08-16
> **grahammechanical said:**
> 
At the Grub boot menu select Advanced Options for Ubuntu. 


Is this the screen where i put in my password ? I've looked & cannot find "advanced options". 

> **grahammechanical said:**
> 
Open that sub-menu and select Recovery Mode. At the Recovery Menu select Resume. That may get you to a desktop using a fall back open source video driver. If you get to a working desktop go to System Settings>Software and Updates>Additional Drivers tab. Allow the utility time to find some drivers and experiment. You may find the open source video driver sufficient.

We can also get to System Settings by right clicking the desktop background and selecting Change Desktop Background.

Regards.

I will do that - if i can get into it..

EDIT :- I've now logged in, but the screen / graphics is very weird - I CANT do control-alt-F1

---

### Post by ajgreeny on 2014-08-16
> **sarahfoxnz said:**
> Is this the screen where i put in my password ? I've looked & cannot find "advanced options". 



I will do that - if i can get into it..

EDIT :- I've now logged in, but the screen / graphics is very weird - I CANT do control-alt-F1
You need to choose Advanced options from the grub menu, but perhaps you have now realised that and got into recovery mode?
Once you get to a command line run command ```
lspci
``` and you'll get output with a line that shows something like
```
**00:02.0 VGA compatible controller:** *Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)*
```though the part I show in italics will probably differ from mine; that is the bit we need to know.

---

### Post by palmgrower on 2014-08-16
Apparently your upgrade didn't go well with your hardware. My ubuntu upgrades have often been problematic and again with this 14.04 upgrade. I have given up and am doing a fresh install.

---

### Post by sarahfoxnz on 2014-08-16
I can't copy-n-paste - but

LSPCI :-

O0:Od:O VGA Compatible controller: NVIDIA Corporation C61 [GeForce 7025 /nForce 630a] (rev a2)


(I do not know if the start part are zero's or capital O's )

EDIT:-

> 
sudo lshw -C video
No talloc stackframe at../source3/param/loadparam.c:4864, leaking memory


(theres more in that quote but i can't copy-n-paste - that line seems to be important)

---

### Post by yancek on 2014-08-16
If you are able to login and have the panel on the left, click on the System Settings icon (the gear/wrench icon) and if you get that window open, click on Software & Upgrades and there should be a tab for Additional drivers.  Let it run and select the recommended driver.  If you don't see the System Settings icon in the left panel, type unity-control-center in the terminal (you might need to prefix the command with sudo) and see if that opens System Settings.  If you don't get it, I imagine there is a way to access from the terminal but I don't know it.

---

### Post by sarahfoxnz on 2014-08-16
my main issue so far / currently (when i get logged in)

1) i cant see my mouse at all.. or

2) if my mouse is visable - my mouse moves at a snails pace and/or 10000' miles an hour - VERY hard to get it over a specific place on the screen.

(i took 30+minutes but i did manage to change my graphics driver - but its still the wrong one.)

Any advise on tty command line - to search for / upgrade my graphics driver (assume i have no idea which one to use) 
I also assume my mouse probs are related to graphic drivers.

my screen looks ok now  but no mouse :)

---

### Post by ubfan1 on 2014-08-17
At the ctrl-alt-F1 terminal, type sudo apt-get update , then type sudo apt-get install nvidia-current
That should get the appropriate nvidia drivers for your video chip.  Switch back to the GUI with Ctrl-F7  (note, no Alt to switch when not in the GUI) and see if things are better.  Try to reboot if not.  See if the nvidia driver got loaded with the lsmod command (nvidia should be listed in the output).

---

### Post by sarahfoxnz on 2014-08-17
I think its fixed

found  a google search - found apt-get update, apt-get upgrade, & a few other commands - Ive rebooted & my linux box seems to be going. However it took a long time to be OK.

It also still has a number of "file not found" errors on bootup - but i can't read it before the main login screen comes up.

My main issue seems to be fixed - but is there a way to 'log' the boot-up errors??

EDIt - ALL FIXED. removed my mouse, inserted it again, & rebooted..  (only issue is the missing files, but once i'm in, it seems fine)

---

### Post by claracc on 2014-08-17
Please, as you got fixed your problem, mark the thread as solved with "thread tools" menu in the right upper part of the page.

Thanks.

---

