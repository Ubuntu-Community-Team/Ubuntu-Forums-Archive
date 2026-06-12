---
title: "[SOLVED] Wireless driver installation"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by rustyjr on 2008-02-06
I have a HP Pavilion ZE4500 intel celeron CPU 2.4 GHz 40 GB partitioned hard drive( 10GB unbuntu, 500M swap, and 29.5 GB windows XP) I tried to install Gutsy but couldn't see the screen to install from disk. After researching this I found that guty will not work on HP Laptops. So, I found Feisty and installed it. Now I'm trying to install the wireless card. It's a Blitzz BWP612B. I downloaded ndiswrapper to install the drivers but I don't know what I'm doing with it. I found a linux driver online for the wireless card but again I'm lost on how to install any of this stuff.

---

### Post by jan quark on 2008-02-06
ignore the prepare part
[https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64](https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64)

and feel free to ask if something goes awry...

---

### Post by rustyjr on 2008-02-06
I'm not sure if I have ndiswrapper installed yet. I'm having problems following where to put the files I open and I don't know any of the linux lingo. I'm new to this I just installed feisty last night. I got unbuntu from the Popular Machanic web page and decided to try it out. I don't want to get discuraged with it just yet. Just wish I could get this card to work. After extracting ndiswrapper-1.52 I see a install icon when I click on that it asks run in terminal, display, cancel, and run what do I do? after I extract the blitzz drives there are approx. 12 files and I don't know what to do with them. I wish I know someone locally that could show me what I'm doing wrong.

---

### Post by jan quark on 2008-02-06
so I guess you have another working internet connection?
thats not bad

download this file
ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb 

from this page

[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

it is a .deb package , to install it just double-click on it, it some sort of .exe file 

to navigate to the file you need, and you need the files with the ending    .inf   and    .sys

use the terminal

the terminal can be found in accessories > terminal

cd is the command to change the directory:

for instance my file is the folder   banana in the sub- folder  apple in the sub folder of the sub -folder monkey and the file is called jungle.inf

so the terminal command to get to folder would be

```

cd /banana/apple/monkey
```
now you are in the sub folder monkey

when you want to know which files are in this folder
you just run 

```
ls
```

and press enter. ls is the command to list many sorts of things...

ask for more advice...

---

### Post by rustyjr on 2008-02-06
First I woujld like to thank you for helping me with this. I followed your instuctions. When I clicked on that file I downloaded it stated to load then I got an error. " Error: Dependency is not satisfiable: libc6" What do I need to do from here?

---

### Post by bwtranch on 2008-02-06
First off, we need to get you started out right and get you some tools. Go to Synaptic and enable all the repositories. Then, fire up a terminal and run sudo apt-get update the sudo apt-get upgrade and the sudo apt-get install build-essential. This last one will ask for your install CD, so make sure you have that handy.

Oh yeah, the thing about Gutsy not running on a laptop is BS. Unix runs on anything. You just have to be smarter than the machine! Ha!:)

---

### Post by rustyjr on 2008-02-06
I'm working from another desktop with internet access. My laptop is right beside me. I've been transfering files via a jump drive.

---

### Post by bwtranch on 2008-02-06
Can you plug in the ethernet cable into the laptop? and then boot it? It may recognize eth0 and go online. Probably will.

---

### Post by rustyjr on 2008-02-06
Don't know haven't tried it. If I do that I loose my connection for my desktop.

---

### Post by rustyjr on 2008-02-06
ok I'm using the ubuntu machine with wired connection. now what?

---

### Post by rustyjr on 2008-02-07
I've updated with synaptic package manager. I've installed ndiswrapper and ndisgph or something like that. I followed the instructions on the ubuntu documentation page. when I do the ndiswrapper -l it says the driver is invalid.  Thanks again for any help.

---

### Post by rustyjr on 2008-02-07
I've come to the conclusion that I won't get this card working. I'll try again in  a couple of days and see if I can play with it.

---

