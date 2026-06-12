---
title: "Install went wrong ???"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by GrandVizier on 2006-02-18
hej
I got my cds from shipit yesterday and have been working almost non stop trying to get linux fully running 
it started with errors from the begining of the install and it took many retries to get a full boot
the problem now is that I somehow managed not to get Gnome installed - I tried several commands from the terminal
```
sudo apt-get install gnome
sudo apt-get -f install 
sudo apt-get install ubuntu-desktop
```
and I either get 
**E: couldn't find package**
or an error related to **gnome-terminal-data**

i tried commenting out the first line in the /etc/apt/sources.list and then uncommmenting the lines for online updates, but my network connection doesn't seem to be set up properly - and unfortunately being new to linux the only commands I know are ifconfig & ping - worse still is that everything appears correct in the output for ifconfig

i should also point out that all the disks I recieved failed the md5sum in both my cd & dvd drives - odder still is that when trying to use the live disc all I get is a blank brown screen

---

### Post by aysiu on 2006-02-19
[QUOTE=GrandVizier]
i should also point out that all the disks I recieved failed the md5sum in both my cd & dvd drives[/QUOTE] That sounds like the problem right there. Yes, I know they're ShipIt CDs, but even those can be bum CDs, too, even though [most people don't seem to agree that that's the case](http://www.ubuntuforums.org/showthread.php?t=113925).

---

