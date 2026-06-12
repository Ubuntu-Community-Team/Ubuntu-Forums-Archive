---
title: "can't install"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by three2 on 2014-03-20
hello 

thanks i advance for all replys.

i have xp and after april no longer being supported or updated so new OS.  i have been recommended by mate for ubuntu as my new OS and need help.

i have got the ubuntu lts on a usb drive.  

I have laptop running xp and powered it off and back on plug usb drive in press f!2 to boot menu. i select top option my usb drive to start installing ubuntu.  Then its try or install i click install ok, next 4.5 gig space, connected to net and ticked the 2 boxes.  Now is where it goes wrong.

i have only 2 options install ubuntu replacing windows xp or something else. there is no 3rd option run ubuntu with xp.

Please please help thanks with links and details thanks as im ok with p.c but not super clever.

once again thanks

---

### Post by Bashing-om on 2014-03-20
three2; Hi !

We do what we can .

this:
> 
next 4.5 gig space,

indicates to me that in the Windows you had made some space free (?) - and hey, that is not enough space to install ubuntu onto .
Anyway, I surmise that the install wizard perceives that unallocated space and thinks you have the situation under control and thus not showing the "install along side of" option (?).

At this point I see 2 options.
1. In Windows make a larger free space (defrag twice and then run Windows check disk utility) of say 30 gigs, and when installing ubuntu, choose the option "something else".
2. Forget about Windows XP (BAD BAD idea until you are comfortable with ubuntu) and choose the option "erase disk and install ubuntu" which will do that, and Windows is history !

We can look at that hard drive and see what other conclusions we can come to,

Boot the liveUSB -> "try ubuntu" mode ( a fully functioning operating system, by the way) and once booted to the desk top;
key combo ctl+alt+t activates a terminal. post pack the outputs of terminal command:
```

sudo fdisk -lu

```

we can
[INDENT][INDENT]do this
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-03-20
If this laptop had XP on it it is probably fairly old and may not run ubuntu with unity very well; you may do better with Xubuntu.

What hardware does it have?

---

### Post by three2 on 2014-03-21
Thanks for quick replys.  The laptop is 6 yrs old and I did try it before installing it. 

Think I found the problem the hard drive had xp on it and no partition.  I have now worked it out and put partition and it has installed.  

I have more problems now ill add them to here. 

How do u install drivers?.

I have a realtek wireless card and cannot connect to the net with ubuntu and its ok wired with ubuntu. Wireless and wired  both worked ok with xp. 

My laptop can display super vga 1280x800 resolution in xp but when run Ubuntu its alot lower and looks quite poor. 

Help Again

Thanks you

---

### Post by mastablasta on 2014-03-21
copy this command into terminal and then post the output here using code (the # icon) tags to make it more readable:
lspci

the additional drivers are in software center ([http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)), but i am not sure realtek needs them. the above command should give out the GPU chip as well as the wireless chip ID. so we can help further.

---

### Post by three2 on 2014-03-21
thanks to all replys

i have now managed to get wireless working from the connect to hidden wireless network but resloution still poor.

On xp i could get 1280x800 but on ubuntu 1024x768.  i looked at my xp and its sis mirage 3 graphics and where it shows the screen display 1280x800 says super vga sis mirage graphics.

please help

thank u

---

### Post by Bashing-om on 2014-03-21
three2; Making good progress ;

To be up front, SIS graphics are problematic in linux in general.
May I suggest that this thread be closed, and open up a new thread in respect to the SIS graphics to obtain a wider view to those who have the knowledge and experience with the SIS graphics ?

Mark this thread solved: 1st post -> thread tools -

For a general introduction to the SIS graphics situation:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967) ##<-mega thread
[https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages) ##4 alternate drivers that MAY work
[http://ubuntuforums.org/showthread.php?t=2144455](http://ubuntuforums.org/showthread.php?t=2144455) ##some offered solutions
[http://ubuntuforums.org/showthread.php?t=2172375](http://ubuntuforums.org/showthread.php?t=2172375) ##making up and editing a config file, old hardware.

SIS graphics makes for a harsh introduction;
[INDENT][INDENT][INDENT]but, welcome to our world
[/INDENT][/INDENT][/INDENT]

---

### Post by three2 on 2014-03-21
thanks you. 

this ubuntu quite hard to work with. xp just just plug in and installs and windows 7,

ive downloaded some drivers for screen unzipped them for ubuntu and thats far as i got as i got a clue.

how do i install drivers?  its very technical ubuntu open up terminal and type commands in

---

### Post by Mark Phelps on 2014-03-21
> how do i install drivers? its very technical ubuntu open up terminal and type commands in 

Sorry, but that's HOW things are done in Linux distros.  The installer searches for, downloads, and installs the proper drivers as part of the initial setup.

Adding your own drivers after that can be a LOT of work -- not just sticking in a CD and running "setup", as in the MS Windows world.

Post #7 provided you the information on SiS drivers -- you need to follow the instructions in the links.

---

### Post by Bashing-om on 2014-03-21
three2; Hey.

Do not make this more difficult than it ain't.

As a general rule with drivers the kernel ( the heart of linux) will pick up on and install any needed drivers. albeit there are some cases where you must intervene and install drivers where you do not like the drivers the kernel picked, most notable are graphics and WIFI drivers.
Drivers for a screensaver should be included in that installation of the screensaver !

How do I say this ? In ubuntu your 1st source of applications is the software repository, any oft-used ap is available in the repository and the package manager will 'fetch" and install the desired application. No sweat. no fuss, no muss. Do some homework on "ubuntu Software Center" a front end for "dpkg" for managing the packages installed and installable on your system.
Most Helpful reading:
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Another "front end" to the "dpkg" system is "apt" - the terminal way -. for instance:
See what returns from Terminal command:
```

apt-cache search screensaver
apt-cache show gnome-screensaver ##as only one example of many

```
as another push up the 
[INDENT][INDENT][INDENT]learning curve
[/INDENT][/INDENT][/INDENT]

---

### Post by three2 on 2014-03-21
Thanks for all your help thinking bout going bk to windows.  I can't upgrade my current laptop maybe bit old.

I find Ubuntu very hard to use If u need anything its all bout typing commands in and seen thousands on the net

---

### Post by Bashing-om on 2014-03-21
three2; Hey

There is always that option to return to Windows.
All depends on what you want in an operating system, after all the computer is just a tool. And the tool fits the need.

We are always here to help you over any rough spot. 'buntu is a terrific point and click GUI system, but the true power of the operating system is realized through the command line. It will take some bit of time and effort on your part to learn this, or any other, operating system.


[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mastablasta on 2014-03-22
> **three2 said:**
> Thanks for all your help thinking bout going bk to windows.  I can't upgrade my current laptop maybe bit old.

I find Ubuntu very hard to use If u need anything its all bout typing commands in and seen thousands on the net

actually you don't have to type them you can copy and paste them. and you don't have to use commands. it's juts that you were trying out Ubuntu, while i use Kubuntu which has a completelly different user interface and different programs for identifying and displaying hardware. so there is not point in giving oyu directions how to open them since oyu do not have them as wlel as directions would be for a totaly different interface. 

however both use same commands, so if you see a tutorial with commands it will likely work in all versions od Debian based opreating systems such as Ubuntu, Kubuntu. Lubunut, Xubuntu, Bodhi linux, Debian, Chrunchbang, Kali, Backbox....

---

### Post by three2 on 2014-03-22
another install problem.

I had Ubuntu instslled it then said new version 12.10. so I downloaded, install packages and clean up. Then it rebooted and that's where it stopped. 

on reboot all I get us asking for cache data failed

assuming drive cache write through.

This goes on and on and still don't start. 

Help Thanks

---

