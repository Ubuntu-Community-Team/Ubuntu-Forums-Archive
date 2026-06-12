---
title: "synaptic never searches"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by thevikas on 2008-11-26
Hi,

My problem is that when i open synaptic package manager on my fresh ubuntu8.10, it comes out with 2 or mostly no search results. I search for apache and it gave me 2 resaults, none of those were there apache server or even close. it never found any package titled or description with php. so therefore, im having big trouble to get package names. 

second problem is how to search a package using command line apt-get. once i do know the package name, i download it using command line cause synaptic does not search anything.

Please help,
thanks.
vikas

---

### Post by mikewhatever on 2008-11-26
sudo apt-cache search package-name

Warning: you'll get a ton of packages for apache. :)

---

### Post by prshah on 2008-11-26
> **thevikas said:**
> 
My problem is that when i open synaptic package manager on my fresh ubuntu8.10, it comes out with 2 or mostly no search results. 

second problem is how to search a package using command line apt-get.


You have to enable other repositores including multiverse, universe etc. You can do this by System-Administration-Software Sources, and check (tick) options for main, universe, restricted, multiverse, then click close. You will not be asked to refresh the package list by downloading package name and availability details from the Internet. If you click OK (or Yes? Reload?) it will reload the details of available packages, and now your add/remove will give you a lot more hits.

You can use tab-completion to get package names to use with apt-get commandline. Tab-completion will tell the computer to fill in appropriate choices. Eg, if you want to install xserver-xorg-video-intel, you can use tab completion as follows: (Note: [tab] means "press the Tab key")```

sudo apt-get -s install xserv[tab]
#at this point, the above xserv will automatically expand to xserver, type in the rest as below
sudo apt-get -s install xserver-xorg-video-in[tab]
#now -in will expand to -intel
sudo apt-get -s install xserver-xorg-video-intel[tab][tab]
#now you will get a list of names beginning with the above letters
sudo apt-get -s install xserver-xorg-video-intel
xserver-xorg-video-intel              xserver-xorg-video-intel-modesetting
xserver-xorg-video-intel-dbg        
sudo apt-get -s install xserver-xorg-video-intel
```

Tab completion works for filenames, directories, modules, devices, etc etc in an intelligent fashion; Eg, if you are using modprobe, tab completion will list modules and not filenames, and so on.

Experiment with it for it to become clear.

---

