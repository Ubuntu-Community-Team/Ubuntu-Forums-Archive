---
title: "Help with Ubuntu 11.04 graphics on ATI 6740M"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by oaat on 2011-06-21
[SIZE=1]Hello Everyone,

I searched a bit and still was unable to get a proper solution for this.

Hardware:[/SIZE][SIZE=1][B]
HP Pavilion dv7t Quad Edition series[/B][/SIZE]
 ATI Radeon HD 6470M graphics 

What I have tried with Ubuntu 11.04, 64bit:

1. Installing the binary driver using "additional drivers" gives exactly the same issue as:
[http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m](http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m)

2. Using the open source driver:
- only 60 FPS on glxgears
- more important, the laptop does not start properly every time (sometimes it just gives blank screen on boot with no response, I have to reboot it a few times).

Moreover, sleep does not work properly, I got around that by disabling sleep =(

When I use Ubuntu 10.04, the screen resolution is terribly low and I can't seem to fix it either.


What do you recommend that I do?

---

### Post by pmoprimo on 2011-08-25
exact same problems here.

hp pavilion dv7 with ATI Radeon 6740M.

---

### Post by fkorbel on 2011-09-21
same problems here with dv7. i have tested Fedora 15 with gnome shell and it is same story. new kernel 2.6.40 in fedora boots 3 minutes and old one does not boot at all. plymouth is big issue. 

let me know, if you have solved it.

---

### Post by gilbertoalbino on 2011-09-29
Same here on Dell Inspiron 15R.
Hope somebody could help with a solution for the most correct way to install AMD Radeon™ HD 6470M 64-bit on Ubuntu.
I've downloaded the driver from ATI website, the installation was all correct but when running:

```
sudo aticonfig --initial -f 
```

it throws the message:
```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2
```

and when running :

```
fglrxinfo
```

it throws the error:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

All my experiences with Linux are frustrated when talking about graphic cards. That's so disgusting... there is no effective working driver for linux the most distribution always lack support for one or another thing.
What is Linux for? For troubleshooting only? Gosh I feel like wasting my time believing that Linux could be usefull for more then using Firefox or reading emails!!!

Hope somebody could help installing my graphi card... on the contrary I'll have to wait who knows how much time for a better Linux distribution with more supported hardware.

---

### Post by MAFoElffen on 2011-09-29
> **gilbertoalbino said:**
> Same here on Dell Inspiron 15R.
Hope somebody could help with a solution for the most correct way to install AMD Radeon&#8482; HD 6470M 64-bit on Ubuntu.

Hope somebody could help installing my graphi card...
For all who are having troubles on this, please follow the instructions in post #[**334**]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334") (<--Follow Link) of my Graphics Resolution Stick. Ask if you have any questions.

---

### Post by gilbertoalbino on 2011-09-30
> **MAFoElffen said:**
> For all who are having troubles on this, please follow the instructions in post #[**334**]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334") (<--Follow Link) of my Graphics Resolution Stick. Ask if you have any questions.

I've followed all the steps in the above post.
But when I run 
```
fglrxinfo
```
it returns the same error before mentioned as well.

When I try to run the AMD Catalyst Control Panel
it says an initialization error is found.
```

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver apropriate for your AMD hardware, or configure using aticonfig.
``` 

I can't understand... really... I can't.
What a pain in the neck!

---

### Post by MAFoElffen on 2011-09-30
> **gilbertoalbino said:**
> 
What a pain in the neck!
And you unitsalled all radeon drivers beforehand right?

Please post your /var/log/Xorg.0.log

EDIT-- In the meantime, Catalyst 11.9 was just released (2 days ago) and has issues in Ubuntu. Try to Uninstall it and Install the last Catalyst 11.8 driver[B].

[/B]

---

