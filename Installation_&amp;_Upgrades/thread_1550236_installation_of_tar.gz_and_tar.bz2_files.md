---
title: "installation of tar.gz and tar.bz2 files"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by kalebka55 on 2010-08-10
hiya...  so let me explain my problem...

I accidentally removed my network manager (gnome) from my system (via synaptic) and hence have not been able to have access to the internet to reinstall the packages.  I have experimented with many commands (with help from others) in terminal with little success.

What I now did was downloaded a 'NetworkManager-0.8.0.999.tar.gz' file and a 'NetworkManager-0.8.1.tar.bz2' file (from a different comp) and have placed them onto my desktop.  I have read the INSTALL instructions within and it is a tad complex for me as I am new to Linux.
I understand I have to extract the files and compile them into a new folder (I think I would choose a file in the /home directory)- how would I go about doing this?
Following this, I need to './configure' or 'make' or 'make install' the files :roll:- ...

Basically, I need HELP here.  If I seem a little bit of a novice ****- i apologize but its true!

Appreciation all round for anyone reading and helping!!!

---

### Post by jarviser on 2010-08-11
Problem is if you had not already installed "Build Essentials" from Synaptic then you can't do the compile and build work, so that's a load more software to try and shoe-horn in.

For newbs and experienced alike, sometimes when you get in a mess like this it's easier to reinstall Ubuntu from the CD and start again. 

I was also interested in 0.8.1 as the installed version is 0.8 but there again the new version may not work on 10.04 anyway so there's another risk factor in going the way you suggest.

---

### Post by kalebka55 on 2010-08-11
Thanks Jarviser, maybe reinstallation of ubuntu may be my final (and wiser) option.... but in reply to your response, I have gone into Synaptic manager and checked that I do indeed have the build essentials package (or at least the informational package with 2/3 others).  To bypass the problem, is there no way I can administrate the net connection via terminal?  I have now extracted the files onto my desktop..ready and waiting for further instructions.  

Thanks again Jarviser!

---

### Post by jarviser on 2010-08-11
I tried to download 0.8.1 but it will not extract for me so can't offer specific help.

If there are install instructions, just copy each line of command (Ctrl+C)and in a terminal session paste (Shift+Ctrl+V)  and hit enter after each paste and it should install as described.

---

### Post by robert shearer on 2010-08-11
> I accidentally removed my network manager (gnome) from my system (via synaptic) and hence have not been able to have access to the internet to reinstall the packages

So did you do a 'Mark for complete removal.' or just a 'Mark for removal." in Synaptic ?.

If the former then look at Keryx for a way of downloading packages on another machine.
[http://keryxproject.org/](http://keryxproject.org/)

If the latter then the package is still in your apt-cache and is reinstallable **without** having to download.
Open Synaptic, search for the package and then 'Mark for installation' and it should install from the cache.

---

### Post by kalebka55 on 2010-08-11
> **robert shearer said:**
> So did you do a 'Mark for complete removal.' or just a 'Mark for removal." in Synaptic ?.

If the former then look at Keryx for a way of downloading packages on another machine.
[http://keryxproject.org/](http://keryxproject.org/)

If the latter then the package is still in your apt-cache and is reinstallable **without** having to download.
Open Synaptic, search for the package and then 'Mark for installation' and it should install from the cache.


Cheers Rob, but unfortuently  the reinstallation did not work.  Im still receiving the message that it cannot connect to achive.ubuntu.org.  Still requiring connection I assume.... is there a terminal command maybe?  have tried a few recommendations from other people but I cannot fully remember if a cache command was included.  Thanks though!

---

### Post by kalebka55 on 2010-08-11
> **jarviser said:**
> I tried to download 0.8.1 but it will not extract for me so can't offer specific help.

If there are install instructions, just copy each line of command (Ctrl+C)and in a terminal session paste (Shift+Ctrl+V)  and hit enter after each paste and it should install as described.
Will give it a shot but instructions are more in a story format rather than 'do this'  then 'this', etc. (i hope you know what i mean).  but its worth a try. will post a [solved] if successful otherwise, reinstallation here i come. Thanks

---

### Post by jocko on 2010-08-11
To build something from source you need:
1. Tools for compiling (covered by the dependencies of the build-essentials package)
2. Development headers for ALL the libraries needed by the program you want to build.

Even if you have build-essential, I doubt you have every development header you need.

Check if the packages are still in your /var/cache/apt/archives and install from there (unless you have cleared the downloaded packages yourself, they are still there):
Run this in a terminal:
```
cd /var/cache/apt/archives
sudo dpkg -i network-manager*.deb
```Otherwise, download the .deb files (you need four different packages, from [here]("http://packages.ubuntu.com/lucid/network-manager"), [here]("http://packages.ubuntu.com/lucid/network-manager-gnome"), [here]("http://packages.ubuntu.com/lucid/network-manager-pptp-gnome") and [here]("http://packages.ubuntu.com/lucid/network-manager-pptp")) instead of trying to build it from source.

---

### Post by kalebka55 on 2010-08-11
> **jocko said:**
> To build something from source you need:
1. Tools for compiling (covered by the dependencies of the build-essentials package)
2. Development headers for ALL the libraries needed by the program you want to build.

Even if you have build-essential, I doubt you have every development header you need.

Check if the packages are still in your /var/cache/apt/archives and install from there (unless you have cleared the downloaded packages yourself, they are still there):
Run this in a terminal:
```
cd /var/cache/apt/archives
sudo dpkg -i network-manager*.deb
```Otherwise, download the .deb files (you need four different packages, from [here]("http://packages.ubuntu.com/lucid/network-manager"), [here]("http://packages.ubuntu.com/lucid/network-manager-gnome"), [here]("http://packages.ubuntu.com/lucid/network-manager-pptp-gnome") and [here]("http://packages.ubuntu.com/lucid/network-manager-pptp")) instead of trying to build it from source.


JOCKO....thank you, thank you, thank you and thank you!!
So, initially, packages were not in my cache. was slightly perturbed. Then downloaded all the files you suggested... all good...but then one of the files did not want to install-  the problem was that i was missing the 'libgnome-bluetooth7" file to which the uninstallable file required. All done and connected.  

Wish i could buy you a beer or something...am very very grateful!! Good Job.\\:D/8-)=D>

---

### Post by jocko on 2010-08-12
> **kalebka55 said:**
> Wish i could buy you a beer or something...am very very grateful!! Good Job.\\:D/8-)=D>
You are very welcome!

---

