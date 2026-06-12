---
title: "Installing virtualbox - what to install in synaptic"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by whiffy badger on 2008-08-20
I've tried getting virtualbox to work in Hardy Heron but without joy.  I'm using .19 kernel.  What are the correct packages to install?

---

### Post by Potatoj316 on 2008-08-20
type this command in the terminal and it will take care of everything
```
sudo aptitude install virtualbox
```
it will actually install the virtualbox-ose package and its dependencies

---

### Post by tuxxy on 2008-08-20
Search for virtualbox in synaptic or type this in terminal

```
sudo aptitude install virtualbox
```

---

### Post by whiffy badger on 2008-08-20
Many thanks to both of you. I've done what you said and I get:

[HTML]newton@newton-laptop:~$ sudo aptitude install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Note: selecting "virtualbox-ose" instead of the
      virtual package "virtualbox"
The following packages are BROKEN:
  virtualbox-ose 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6366kB of archives. After unpacking 20.7MB will be used.
The following packages have unmet dependencies:
  virtualbox-ose: Depends: libxalan110 but it is not installable
                  Depends: libxerces27 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libxalan110 [1.10-3.1 (hardy, now)]
libxerces27 [2.7.0-5 (hardy, now)]

Score is 28

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libxalan110 libxerces27 
The following NEW packages will be installed:
  libxalan110 libxerces27 virtualbox-ose 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8997kB of archives. After unpacking 29.8MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libxerces27.
(Reading database ... 144179 files and directories currently installed.)
Unpacking libxerces27 (from .../libxerces27_2.7.0-5_i386.deb) ...
Selecting previously deselected package libxalan110.
Unpacking libxalan110 (from .../libxalan110_1.10-3.1_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.6-dfsg-6ubuntu1_i386.deb) ...
Setting up libxerces27 (2.7.0-5) ...

Setting up libxalan110 (1.10-3.1) ...

Setting up virtualbox-ose (1.5.6-dfsg-6ubuntu1) ...
 * Starting VirtualBox host networking...                                [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
newton@newton-laptop:~$ 

[/HTML]

The bit where it says "No suitable module for running kernel found."  Does that mean this won't work?

---

### Post by mattduckman on 2008-08-22
if you start up VirtualBox, i think it'll give you a command to compile the vbox module. i think the command is
```
sudo /etc/init.d/vboxdrv setup
```

---

