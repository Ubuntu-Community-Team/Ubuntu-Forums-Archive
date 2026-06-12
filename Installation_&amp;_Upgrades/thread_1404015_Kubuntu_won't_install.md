---
title: "Kubuntu won't install"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by tlinux on 2010-02-10
I can't get Kubuntu to install. I put the disk in the drive and the Kubuntu Menu is displayed. I selected the Demo and Full Installation option. This sent me to another menu that asked if I wanted to reboot now or later. I chose now but instead of rebooting it went back to the Kubuntu menu. I then went to the start menu and selected Restart. When the computer restarted it didn't recognize the Kubuntu disc .

I'm running Windows 7 in a 64-bit machine.

What to do?

Thanks!

---

### Post by toona on 2010-02-11
I've no idea! I have the same issue; check out my thread [http://ubuntuforums.org/showthread.php?t=1403807](http://ubuntuforums.org/showthread.php?t=1403807) (also no replies, like you). 

I'm beginning to think there's a problem with kubuntu iso images!

---

### Post by wojox on 2010-02-11
Here's what I use. Never fails. Download the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD). Pick the right version (32 or 64). Burn and boot from cd-rom. When it loads to the terminal enter "install". About half way through taskel will pop up. Use you arrow keys to scroll down to kubuntu-desktop. Press the spacebar to select and tab then enter. Let it finish and presto.

---

### Post by toona on 2010-02-11
Thanx for the link!

I solved my problem by using 3buntu,  [http://iso.linux.hr/3buntu/3buntu-9.10-desktop-i386.iso  ]("http://iso.linux.hr/3buntu/3buntu-9.10-desktop-i386.iso")

3buntu is a Croatian compilation which contains ubuntu, kubuntu and xubuntu. The intro menu is in Croatian but everything else is in English, so there should be no problem! If you decide to use it, PM me if you need a translation, although you should easily figure it out on your own (you'll see "kubuntu" ;) ).

Cheers!

---

### Post by tlinux on 2010-02-11
I tried both of the above recommendations but couldn't get either of them to run. I was able to download and burn the iso files to a disc, but nothing happened when I restarted the computer.

---

### Post by devvmh on 2010-02-21
So, I'm not exactly sure what the problem is, but just be aware you can install xubuntu or plain old ubuntu if those iso's are better. Then once that's installed you can just run

sudo apt-get install kubuntu-desktop

and I think you'll be kubuntuized. It wastes some harddrive space, but you'll have it installed. I know I'm having some trouble with Kubuntu's install disk right now.

---

