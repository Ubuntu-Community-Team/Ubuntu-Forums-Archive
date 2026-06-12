---
title: "ndiswrapper install problems for 10.04"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by ahaa on 2010-06-21
Hey all,

I have looked everywhere for different ways to install   for Ubuntu 10.04 but I have found on specific guide of that version of Ubuntu. So I downloaded the most recent file off of sourceforge but I all I did was just uncompress the file because I didn't know what to do.

Then I found information on to install the software through the synaptic package manager and I found the ndisgtk file, marked it for installation and apply the changes but it told me to essentially insert my ubuntu install disk but with a longer name so I put in my install disk but it didn't continue so it didn't go any farther with the install (The CD name mentioned was different than the actually cd name)

So I did this in terminal and the same thing with the package manager happened here as well. The misnamed CD was asked for again.

Besides the name of the CD, the path that it was looking for was valid and the file it was looking for was there as well. 

I'm baffled and don't know where to turn to next to get this program installed. I'm new to Ubuntu and don't know my way around yet. I would like to stay with Ubuntu but I can't if I can't get internet on the system. FYI I can't have a wired connection for this computer. Anyone out there that can help me, because I really need it at this point.

[EDIT] if this helps i'm using a gateway with a 950 MHz processor with 512 MB of RAM. Again I looked everywhere and every process I did didn't work and now I don't know where to turn to now

---

### Post by labinnsw on 2010-06-23
> **ahaa said:**
> Hey all,

I have looked everywhere for different ways to install   for Ubuntu 10.04 but I have found on specific guide of that version of Ubuntu. So I downloaded the most recent file off of sourceforge but I all I did was just uncompress the file because I didn't know what to do.

Then I found information on to install the software through the synaptic package manager and I found the ndisgtk file, marked it for installation and apply the changes but it told me to essentially insert my ubuntu install disk but with a longer name so I put in my install disk but it didn't continue so it didn't go any farther with the install (The CD name mentioned was different than the actually cd name)

So I did this in terminal and the same thing with the package manager happened here as well. The misnamed CD was asked for again.

Besides the name of the CD, the path that it was looking for was valid and the file it was looking for was there as well. 

I'm baffled and don't know where to turn to next to get this program installed. I'm new to Ubuntu and don't know my way around yet. I would like to stay with Ubuntu but I can't if I can't get internet on the system. FYI I can't have a wired connection for this computer. Anyone out there that can help me, because I really need it at this point.

[EDIT] if this helps i'm using a gateway with a 950 MHz processor with 512 MB of RAM. Again I looked everywhere and every process I did didn't work and now I don't know where to turn to now

You will need to install 3 packages.
ndisgtk
ndiswrapper-utils-1.9
ndiswrapper-common

Insert the disc (any Ubuntu disc but preferably Lucid Lynx)
Search the disc using the search term "ndis"
You should find all 3 packages. Double click (or click) to install each package.

or

Copy all the packages to a directory
cd to the directory
Use the command below to install the packages```
sudo dpkg -i --force-all *.deb
```

---

