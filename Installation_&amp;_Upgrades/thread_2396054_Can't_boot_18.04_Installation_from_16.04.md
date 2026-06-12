---
title: "Can't boot 18.04 Installation from 16.04"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by helesteu on 2018-07-10
I recently got a problem with Windows and I figured I should move to Ubuntu, I had this DVD with Ubuntu 16.04, it barely works to get on internet, Ubuntu Software doesn't respond and everything, so I got my friend burn a DVD with 18.04 for me, everything fine but when tried to install, as usuall, boot menu and when selecting Asus (my CD-ROM) it says something like I didn't introduce the media something, if necessary, I'll post a picture. Besides the CD-ROM there are 2 other options named Ubuntu, both boots me to the actual one. So I looked again in the tutorial on how to install it and it says that I should simply insert the DVD and restart, I did that but it just boots normally.
I already had 18.04 a while ago and I know it works on my pc.
Thx for help.

---

### Post by Frogs Hair on 2018-07-10
Hello and Welcome

> [COLOR=#000000] I should simply insert the DVD and restart, I did that but it just boots normally.[/COLOR]
[COLOR=#000000]I already had 18.04 a while ago and I know it works on my pc.[/COLOR]

Depending on the computer , you may have set it to boot from DVD in the bios or boot screen. There is usually a key that needs to be pressed during boot to access this. Some info about your system may be helpful.

---

### Post by helesteu on 2018-07-10
> **Frogs Hair said:**
> Hello and Welcome



Depending on the computer , you may have set it to boot from DVD in the bios or boot screen. There is usually a key that needs to be pressed during boot to access this. Some info about your system may be helpful.

I have a ASRock motherboard and I press on f11 for boot menu.

I took a picture of my boot menu and one of UEFI menu.

[https://s8.postimg.cc/gdlcu3zfp/20180710_220458.jpg](https://s8.postimg.cc/gdlcu3zfp/20180710_220458.jpg)
[https://s8.postimg.cc/3m76ns551/20180710_220346.jpg](https://s8.postimg.cc/3m76ns551/20180710_220346.jpg)

---

### Post by oldfred on 2018-07-10
You can attach screen shots or reduced size photos to forum with paperclip icon in Forum's advanced editor.
       Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Many new UEFI allow screenshots from within UEFI, but you have to save to a FAT32 formatted partition as FAT32 is all that UEFI knows.

Make sure you are not using any asmedia ports, even for DVD.

Have you updated UEFI from Asrock? 
But note that update will reset many of the settings you have changed. I used to take photos with BIOS. My one motherboard gives a nice list of UEFI settings changed when exiting. Or I save screen shots, so I can easily redo all the UEFI settings I change.

This has been common on all Asrock system.
      Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)

---

### Post by helesteu on 2018-07-10
> **oldfred said:**
> 
Have you updated UEFI from Asrock? 

I didn't do any settings or updates on this motherboard, I bought it recently.

As I figure until now, the CD-ROM cannot read my DVD somehow, even tho, in Ubuntu I can access the DVD with it's installation files.
So if it does read it, why doesn't run?

I made a photo of selecting CD-ROM in boot menu.
[https://s8.postimg.cc/okhxze4lh/20180710_224314.jpg](https://s8.postimg.cc/okhxze4lh/20180710_224314.jpg)

---

### Post by oldfred on 2018-07-10
How did you create DVD?
You do not copy ISO to DVD as then it is not bootable. You have to use tools that extract it and make it bootable.
I used to use DVDs, but burned so many coasters (bad burns) that I now only use flash drives.

       Write image or burn image not copy ISO as one large file to flash or DVD.
[https://tutorials.ubuntu.com/](https://tutorials.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/USB](https://help.ubuntu.com/community/USB) Installation Media
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://askubuntu.com/questions/674441/what-is-the-proper-way-of-creating-installation-media-from-ubuntu-iso](https://askubuntu.com/questions/674441/what-is-the-proper-way-of-creating-installation-media-from-ubuntu-iso) 
            Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by helesteu on 2018-07-10
> **oldfred said:**
> How did you create DVD?
You do not copy ISO to DVD as then it is not bootable. You have to use tools that extract it and make it bootable.
I used to use DVDs, but burned so many coasters (bad burns) that I now only use flash drives.

       Write image or burn image not copy ISO as one large file to flash or DVD.


I burned before some versions of Ubuntu, but because I couldn't get the software to do it myself from Ubuntu Sofware or anywhere else I asked a friend, and as I didn't watch him, he might made a mistake.

Thank you for spending time helping me, I'll try the links and assist him tommorow, good that my hardware's not the problem.

---

