---
title: "Installation Wine on Ubuntu with architecture aarch64"
date: 2019-07-09
forum: Installation &amp; Upgrades
---

### Post by generalghest on 2019-07-09
Hello. I am trying to install winehq on ubuntu 16.04.5 LTS.
[COLOR=#242729][FONT=Arial]I have arch64 architecture [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I was try to do all with instruction from [/FONT][/COLOR][askubuntu.com/questions/316025/…]("https://askubuntu.com/questions/316025/how-to-install-and-configure-wine")
[COLOR=#242729][FONT=Arial]sudo dpkg --add-architecture i386 
all is good
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]wget -nc [/FONT][/COLOR][dl.winehq.org/wine-builds/winehq.keyFile]("https://dl.winehq.org/wine-builds/winehq.keyFile")[COLOR=#242729][FONT=Arial] 
‘winehq.key’ already there; not retrieving. 
No problems here too

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]sudo apt-key add winehq.key OK[/FONT][/COLOR][COLOR=#242729][FONT=Arial] 

[/FONT][/COLOR]sudo apt-add-repository 'deb dl.winehq.org/wine-builds/ubuntu xenial main' 
(I take it from wiki winehq) 

[COLOR=#242729][FONT=Arial]sudo apt update

[/FONT][/COLOR]dextop@localhost:~$ sudo apt-get install winehq-stableReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
winehq-stable:i386 : Depends: wine-stable:i386 (= 4.0.1~xenial) but it 
is not going to be installed
E: Unable to correct problems, you have held broken packages

Could anyone help me with it. I already asked it on askubuntu ( [https://askubuntu.com/questions/1155255/how-to-install-wine-on-aarch-64](https://askubuntu.com/questions/1155255/how-to-install-wine-on-aarch-64) ).
Many thanks for helping.

---

### Post by CatKiller on 2019-07-09
Wine won't run on ARM. Well, you can run ARM Windows applications; there are a handful from Microsoft's Windows RT experiment.

Windows applications are almost entirely either i386 or AMD64. Wine is set up to run *those* on an i386 or AMD64 processor. To run them on your ARM processor you would first need to emulate an i386 or AMD64 processor on your ARM one using QEMU or similar, which will not be fast, and then run the whole software stack on that.

Basically, what you're trying to do you shouldn't try to do. You won't be able to run standard Windows applications in Linux on your ARM tablet.

---

### Post by generalghest on 2019-07-09
Which emulation of Windows is faster and more stable? 
Are exist better ways for running Microsoft Office? 
Can be Wine compiled for my system?

---

### Post by CatKiller on 2019-07-09
Using Google Docs or whatever Microsoft called their online version of Office is the sensible way for you to do Office things on your ARM tablet. Or LibreOffice if it's available for ARM (I have no idea).

Compiling Wine for ARM will still only mean that you can run ARM Windows programs. Wine is just a translation layer. It converts DirectX calls to OpenGL calls, and converts Windows file accesses into Linux file accesses. Your processor is not capable of running i386 or AMD64 instructions: it has a different [architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture).

---

### Post by generalghest on 2019-07-10
But even for windows rt exist microsoft office. LibreOffice not compatible with word fully, and the same about google dosc. Microsoft office online have limited functional and strange markup.
Also for arm is possible to install adobe applications. 
I still want to try install Wine. Please help with it.

---

### Post by CatKiller on 2019-07-10
I haven't used Wine directly in years, so I can't help you with that; I can only say that it won't do all that you want it to do.

[This](https://wiki.winehq.org/ARM64) is the page that describes the Aarch64 support that exists for Wine.

---

