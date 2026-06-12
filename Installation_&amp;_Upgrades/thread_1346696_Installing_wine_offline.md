---
title: "Installing wine offline"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by samg34 on 2009-12-05
I need to install wine through removable disk drive

I got a dual boot Ubuntu 9.10
I use an wireless motherboard-extension to get internet to my desktop because i can't get a long enough Ethernet cable
The installation CD for it uses a .exe
Wine isn't on my Ubuntu 9.10 so i can't unpack it
On winehq.com the instructions require you to have internet connection

on the other side of the dual boot, i have a windows machine with a an internet connection because windows can native-ly read .exe

I need to get wine onto a CD in windows and transfer it to the other side of the disk partition

---

### Post by zvacet on 2009-12-05
> I use an wireless motherboard-extension to get internet to my desktop

Does it mean that you have internet working in Ubuntu?If yes,then under system<admin>software sources (or repositories) check all under ubuntu software (except source) and under updates tab check first two.Reload.Now you should be able to install wine from synaptic.If you really need to download wine from <windows side then go [here]("http://packages.ubuntu.com/karmic/wine") and download all packages marked with red ball as a green and blue ones.After that scroll to the bottom of page and choose architecture and download wine.Put all packages into the folder and put folder on cd/usb.From there put that folder in your home directory in Ubuntu and go to the applications>accessories>terminal and type ( let say that you named folder with wine and its dependencies as folwin)

```
cd folwin
```

```
sudo dpkg -i *deb
```

---

### Post by samg34 on 2009-12-06
To recap
I have no Ubuntu internet, but i have windows internet
I go [a href=http://packages.ubuntu.com/karmic/wine]here[/a]
I click i386 (i am running Ubuntu on x86)
Now i am here [http://packages.ubuntu.com/karmic/wine](http://packages.ubuntu.com/karmic/wine)
i go to a mirror download wine and put the .deb file on a CD
I go to Ubuntu and on terminal type the code
right

---

### Post by samg34 on 2009-12-07
Linux can't sense my windows CD
If a make a CD in linux and try to add wine to it, windows says its unwritable!!!
I will try again with USBs

---

### Post by samg34 on 2009-12-08
USBs are much more multi-platform
They can I can transfer files now yay!!!

---

### Post by samg34 on 2010-05-16
I got wine offline, but i recomend going out and getting an etherenet extender or a really long cable. Saving 10$ is not worth the kind of effort i put into that

---

