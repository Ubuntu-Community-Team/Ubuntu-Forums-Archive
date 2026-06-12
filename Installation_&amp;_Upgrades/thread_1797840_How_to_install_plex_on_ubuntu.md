---
title: "How to install plex on ubuntu"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Alan_Carslaw on 2011-07-05
Good Evening, I am new to this forum and require help from all you Ubuntu experts on how to install plex. I have installed plex and uncompressed into the Documents directory under /home/alancarslaw/Documents. When I cd to the directory which contains the start.sh script which apparently is the install script and try and run it with start.sh as I am already in the directory in which that is contained I get command not found. It will not allow me to run the install script  (start.sh)

Can someone please advise on how to install plex on Ubuntu?

I look forward to hearing from you all.

Thanks

Alan

---

### Post by antpruitt on 2011-11-04
I saw on the plex site a new repository had to be added and then you can install it from the apt-get command.  

I did so, but now i need to figure out how to get the desktop client to work with WINE (x64 11.10).

right now i've got nothing.  Hope I helped a little, but I'm still searching around for more help.

---

### Post by raja.genupula on 2011-11-04
> **Alan_Carslaw said:**
> Good Evening, I am new to this forum and require help from all you Ubuntu experts on how to install plex. I have installed plex and uncompressed into the Documents directory under /home/alancarslaw/Documents. When I cd to the directory which contains the start.sh script which apparently is the install script and try and run it with start.sh as I am already in the directory in which that is contained I get command not found. It will not allow me to run the install script  (start.sh)

Can someone please advise on how to install plex on Ubuntu?

I look forward to hearing from you all.

Thanks

Alan

do this in terminal

```
sudo chmod +x start.sh
```
```
./start.sh
```
All the best.

---

