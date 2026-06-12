---
title: "Blank display after booting"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by Sctmon on 2010-01-20
I was not sure if I should post this in the Absolute beginners section but here goes.

I am completely new to Liniux ie I know it exists but not much more and am trying to move over from Windows.
I tried unsucesfully to instal ubuntu 9.10 but was just met with a blank screen shortly after starting the install. Next time round I selected safe graphics mode by pressing F4 before installing and managed to get a bit further but could not get it to find the SATA drive to install onto.
Having read a load of stuff on the forum I swapped the SATA drive out for an IDE drive which was recognised and installed without any problems. I could then get it up and running and download install the nvidia driver - System -> Administration -> Hardware Drivers - to get the display working properly.

What I am trying to do it get it installed on my SATA drive which I managed to do using the alt text based installation and disabling the raid option during the installation. There was no safe graphics mode that I could opt for during the installation so although it has installed ok I just get a blank screen when the operating system boots.

I can select the recovery mode from the Grub menu then if I select Resume normal boot from the recovery menu I can log on at the command line.

Using the command line I have managed to manualy update :
sudo apt-get update
sudo apt-get upgrade
but I have not been able install the nvida drivers:

sudo apt-get install nvidia-settings
Seems to work ok!

wget -O NVIDIA-Linux-x86_64-pkg1.run [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Seems to download and save ok but...

sudo sh NVIDIA-Linux-x86_64-pkg1.run
just results in a load of errors :
cannot open !DOCTYPE: No such file
cannot open meta file:no such file

etc.........

In short is there a way to set some kind of safe graphics mode or do so during the alt text based install?

Please bear in mind I have no previous Linux experience so will probably need it spelled out to me...

:o

PS.  Asus m2n32-sli deluve mobo with Geforce 9600GT and 7800LE graphics cards installed

---

### Post by Sctmon on 2010-01-22
Is 9.10 a beta release? I managed to get 9.04 to install first time without any issues with the display or drives... well.. second attempt really but I can't blame the blob of marmite on the bottom the installation cd on anyone else.

---

