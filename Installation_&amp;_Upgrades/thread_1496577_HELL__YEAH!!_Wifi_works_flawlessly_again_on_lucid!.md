---
title: "HELL **** YEAH!! Wifi works flawlessly again on lucid!!!"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by linuxd00 on 2010-05-29
Sorry for the header but my joy is so endless!!! after quite a year of suffering with more than poor wifi performance (to the point that i wanted to buy a nother laptop just to fix it) i got rid of my wifi probems.

(mods feel free to change title... i wont)

forthe problem see here: [http://ubuntuforums.org/showthread.php?t=1495857](http://ubuntuforums.org/showthread.php?t=1495857)

Solution:

Turn out my laptop uses the Atheroschip... for which ubuntu by default installs the free (free as in crappy) Atheros driver. Solution was to install the MadWifi driver. Which is made specially for atheros chips.

Problem was that the downloadable version is from 2008 and its source code is too old for lucids kernel.. so it wont compile. You have to download the latest code from SVN... its very easy and panless!!

these commands solved everything:

(Optional if you dont have SVN already)

```
sudo apt-get install subversion
```

Install dependencies 
(assuming you didnt compile nothing on your system yet)
(assuming you have x86system)


```
sudo apt-get update && sudo aptitude install linux-headers-386 build-essential
```

then download madwifi:

```
svn checkout http://madwifi-project.org/svn/madwifi/trunk madwifi
```
go into the downloaded directory
```
cd madwifi/
```
compile and afterwards install the driver
```
make

sudo make install

```

activate the driver (this might be optional the install guide said to do it?)
```
sudo modprobe ath_pci
```

then the last step: Go to System->Administration->Hardware Drivers

Madwifi should be there.. activate it using the "activate button"... i rebooted... and greatness came to me.

the old driver would totally slow down up to freeze my system... now i have full DSL speed again. 

thanks  madwifi!!! THAAAAAAAANKSSS!!!!! :D

---

