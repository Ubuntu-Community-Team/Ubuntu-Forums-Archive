---
title: "Ubuntu 12.10 Desktop 64 bit Installer not recognizing Keyboard and Mouse"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by vinooj on 2013-02-04
Ubuntu 12.10 Desktop 64 bit Installer not recognizing Keyboard and Mouse

I just upgraded my motherboard ( Gigabyte 990FXA-UD3) and CPU ( AMD FX 8150 ) and Memory 16gb DDR3 on my computer that is running Ubuntu 10.04 32 bit LTS-the Lucid Lynx. Upgrade was easy and my system is back up and running including the Wireless Keyboard and Mouse ( Logitech MK300 ).

**Then I decided to upgrade the OS to Ubuntu 12.10 Desktop 64 bit. However during the install ( from ISO CD ) I was not able to get pass the Language selection screen as my keyboard and mouse is not recognized.**

Did some Googling and I found some suggestion to Turn on the Legacy USB support in Bios and I made sure it is enabled. As part of this process I realized the newer mother boards are running UEFI which I'm not very familiar with. So I'm running out of ideas to try.

Here are few highlight
[LIST]
[*]In Bios, keyboard and mouse is recognized correctly. 
[*]In my running system Ubuntu 10.04.32 I have no problem with keyboard and mouse
[*]Also tried using a wired USB keyboard and mouse with no success
[/LIST]

Any help would be appreciated.

---

### Post by mörgæs on 2013-02-05
How does 12.10 work in a live boot using wired keyboard and mouse?

---

### Post by vinooj on 2013-02-05
Same problem with USB wired keyboard and 12.10. Comes to the language setup screen and gets stuck there. 

**Update 02/05**
I tried using an old PS2 keyboard ( MB has 1 PS2 port) and now the installer seems to recognize the keyboard.  

At this point it looks like the issue has has something to do with USB and UEFI configuration.

Help!!!!

---

### Post by vinooj on 2013-02-06
[ATTACH]231101[/ATTACH]

Attached is my Bios screenshot. Do you see any issues with configuration?

---

### Post by mörgæs on 2013-02-07
I'm not sure it's about configuration, nor about UEFI. 

Some of my computers want a USB keyboard, some PS/2, and it has been like this for many years, also before introduction of UEFI. I have settled with that. 

Sorry I can't give a better answer. If you feel like digging deeper into the problem and maybe help solving it, best is to try the development release (13.04) and discuss the problem in the corresponding [forum]("http://ubuntuforums.org/forumdisplay.php?f=427"). People there can help you to bring the problem to the developers' attention.

---

### Post by vinooj on 2013-02-08
Appreciate your feedback mörgæs.

Lastly I tried installing a USB PCI card with no success. So I have decided to return my motherboard.

So my question is can anyone recommend a good AM3+ motherboard?

---

