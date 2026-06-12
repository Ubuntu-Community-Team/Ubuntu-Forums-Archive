---
title: "Dual Botting Ubuntu/Kubuntu"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by AlEmerald on 2007-08-06
hello everybody new member it's a great forum and a great OS :guitar:  i have i request i love trying new things and i have used red hat then Ubuntu was released and i have been using that for a while and now it time to try something new so i have decided to to try [COLOR="RoyalBlue"]kubuntu[/COLOR] but i love my [COLOR="Wheat"]Ubuntu[/COLOR] so i was wondering if there was somebody could help by posting a  walkthrough on how to dual boot [COLOR="Wheat"]Ubuntu[/COLOR]/[COLOR="RoyalBlue"]Kubuntu[/COLOR] :confused: thanks in advance any help is appreciated
[FONT="Georgia"]
Best Regards Alex :)  [/FONT]

---

### Post by 505 on 2007-08-06
This is very easy, and you don't need dual boot for that. Open a terminal and type
```
sudo aptitude install kubuntu-desktop
```
It will now install a lot of things. After that, reboot. You will now see the 'default' Gnome login screen. Click the options -> sessions button and select KDE. Type your username/password and you have KDE. Best of all, for all shared programs, your settings are the same as under Gnome.

/Edit: changed apt-get in aptitude. It handles dependencies better if you try to uninstall Kubuntu

---

### Post by deejross on 2007-08-09
Actually I'm curious about this for a different reason. I want to dual boot Ubuntu Feisty and Kubuntu Gusty so I can test out the new Alpha release. This is a situation where you NEED to dual-boot, because no one wants to hose their system in case the Alpha does a crash and burn.

---

### Post by louieb on 2007-08-09
> **deejross said:**
> I want to dual boot Ubuntu Feisty and Kubuntu Gusty so I can test out the new Alpha release. 
Its just a matter of making a partition for the test distro, install it, and configuring GRUB to boot the test distro. Good stuff on how to that at [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by LeeU on 2007-09-29
> **505 said:**
> This is very easy, and you don't need dual boot for that. Open a terminal and type
```
sudo aptitude install kubuntu-desktop
```
It will now install a lot of things. After that, reboot. You will now see the 'default' Gnome login screen. Click the options -> sessions button and select KDE. Type your username/password and you have KDE. Best of all, for all shared programs, your settings are the same as under Gnome. /Edit: changed apt-get in aptitude. It handles dependencies better if you try to uninstall Kubuntu

Just one question: I have an automatic login. How would I get to it that way?

---

