---
title: "Can Xubuntu be installed over Ubuntu?"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by Tom1942 on 2006-08-22
I've successfully installed Ubuntu 6.06 LTS using a live cd on a hand me down pc.  

CPU: Intel Pentium II, 400mhz
Mobo: Intel 82440BX
HD: 120 gb
RAM: 192 mb

Ubuntu was installed as the only OS on the hard drive in one large partition.

I knew Ubuntu might be slow on this old pc but I wanted to see for myself, just how slow.  In my opinion, for me, too painfully slow.  Therefore, I would like to try installing Xubuntu to replace the Ubuntu.  

I found instructions for installing Xubuntu using the Ubuntu live cd but I am too new to linux to try that.  [[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu) - Installing XFCE on Ubuntu.]

I would like to use an Xubuntu 6.06 live cd and just run the installation as if none had been done before.  Will this work?  Will Xubuntu overwrite the Ubuntu install and leave me with a pc with just Xubuntu installed on it?

I have not completely finished the Ubuntu install, that is, for example I did not get the wireless adapter working yet, so I don't have an internet connection, and I have not yet tried just connecting an ethernet cable to it - just in case an internet connection is required before I try to run an Xubuntu install.

Is this a bad idea, or if I try it will it work?

Thanks in advance.

---

### Post by catlett on 2006-08-22
[https://wiki.ubuntu.com/Xubuntu/Releases?action=show&redirect=XubuntuReleases](https://wiki.ubuntu.com/Xubuntu/Releases?action=show&redirect=XubuntuReleases) Just download and burn the iso to disk and install. Just select the option "use entire disk" for the installation. The installer will format the drive and partition it into 2 partitions (a swap(virtual memory) and an ext3 for the OS) . This will erase any data on the drive, i.e. ubuntu and you will have xubuntu for your only OS when it is done

---

### Post by nolesfan on 2006-08-22
I know this won't help much, but there is a way to install Xubuntu directly over an Ubuntu installation. I actually did it a few weeks ago from instructions I found by random luck. It's all command line, but really straight forward. Just google it and try it out. If nothing else, you will learn command-line which is great in Ubuntu.

---

### Post by Tom1942 on 2006-08-23
Well, the install of Xubuntu went well.  Xubuntu found the wireless pci adpater and I was able to surf the net, going to several web sites to be sure it was working.

I changed monitor resolution, renamed the computer, and did several other things, including just running one or two apps to see they did run.

I then shut down everything, took out the Xubuntu live cd and then re-started the pc after going into the bios and changing the boot sequence from **CD-ROM, C, A** to **C, CDROM, A**.  It appears that C was not recognized because I got the error message:
"Boot from CD-Rom - Failure"
"Disk boot failure, insert system disk and press enter."
I am inferring that the boot up passed right by the C drive and tried the CD-ROM, which failed because there was no disk there.

When I put the Live CD back into the pc it wanted to do another install, which I didn't want to do if all that was going to happen was the same thing.

My theory is that either nothing was saved to the hard drive (Xubuntu just ran from the cd and nothing was saved, or the bios is not recognizing the hard drive as "C".

Would appreciate any thoughts or ideas.:confused:

---

### Post by K.Mandla on 2006-08-23
You might try the alternate (install) CD. If you know you just want to overwrite what's on the drive, the install CD is a bit less finicky and works just as well. It's just not as "pretty."

And if you want, you can leave your BIOS settings to CD-ROM, C, A, and so long as there isn't a bootable CD in the CD-ROM, it should work fine. Saves a step, anyways.

---

### Post by catlett on 2006-08-23
"Running" the live cd and installing are 2 different things. It sounds like you just ran the live cd. The start of a live cd will have a few questions about hardware etc but it isn't installing to your hard drive. It is just configuring the live session. A live session is when the OS runs off the cd instead of the hard drive. Because it is the cd that is holding the OS, you cannot save anything from the live session. When the session is over that is it. Your hard drive is unchanged and if you run it again, you start fresh.

I could be mistaken though. Did you run the installation after you booted into the xubuntu live sessins desktop? Once you booted into the live session, there should have been an icon on the desktop titiled "install". This is a screenshot of how the desktop looks when you boot into the live cd and get to the desktop. [http://shots.osdir.com/slideshows/slideshow.php?release=660&slide=4&title=xubuntu+6.06+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=660&slide=4&title=xubuntu+6.06+screenshots)
You need to double click on the install icon. Did you do that? If you did then the installaiton would have ran. It would have asked about your hard drive and the method of installation you wanted etc. If you didn't run the install, then boot back into it and select the "install" icon.

If you did run the install, what error do you get when you rebooted?

---

### Post by Tom1942 on 2006-08-24
Catlett:
Thanks.  You were right.  When I first tried to install ubuntu I clicked on the install icon on the desktop but it went to a black screen, frozen as best I could tell.  Being new to linux, I thought I must have done something wrong.  The next time I tried install I pressed F6 when given that chance and then enter and the install seemed to be working.  

Well, knowing that using the install icon was the right way to go, I've done that and now seem to have a proper initial install, in that I was asked the series of questions and all indications are things were saved to the hard drive.  At the completion of the install I was told to reboot after making sure the cdrom was removed, which I did and the pc rebooted to Xubuntu.

The wireless pci adapter was recognized, I input the correct encryption key for my router, and I was able to connect to the WWW.  

However, when I try to change display settings (monitor resolution) I am taken to the userid and password popup, have to sign in again, and the resolution remains unchanged.  Also, there are only 4 choices, default and 3 nnnXnnn choices.  When I only ran the live cd, there were many choices for changing the resolution.  I'm not sure why this is happening.  :confused: 

When using Firefox and trying to go to an https:// page a pop up appears with "Alert me whenever I submit information that is not encrypted." checkbox.  I check not to warn me of this anymore but it continues to warn me with the check box unchecked. :confused: 

I wanted to write this message using Firefox on the Xubuntu pc, but when I tried to log in this forum page I was told 3 times that my userid or password was not correct but I carefully typed everything the 2nd and 3rd times.  I was not already logged in on this windows pc I am using now, so I am confused as to why the problem using the xubuntu pc.  :confused: 

Any ideas or tips would be appreciated.

---

### Post by catlett on 2006-08-24
You can reconfigure the x server with this comand ```
sudo dpkg-reconfigure xserver-xorg
``` This will go through detecttion of your monitor video card etc. You can usually select defaults. The only thing to try6 and find out is the "horizontal" and "vertical" refrezh rates for your monitor. You want to select advanced when configuring the monitor and enter this manually. You can usually get specs from your monitor's website. Or just google any model # on your monitor.
One other thing to do. When it gives you a list of resolutions to enable. Select all of them (you select by pressing the space bar and using the arrow key to move down) When you select all of them it sets a default option that all resolutions possible wil be available to you.
Try the epiphany browser to see if that gives you an error. It is based on firefox's engine. It is actually a good browser to run on xubuntu because it uses less resources than firefox.
```
sudo apt-get install epiphany-browser
```

Also take a look at the xubuntu guide. It may have some things you need to enable. [https://help.ubuntu.com/xubuntu/desktopguide/C/index.html](https://help.ubuntu.com/xubuntu/desktopguide/C/index.html)

Post any errors you get.

---

### Post by nolesfan on 2006-08-24
Okay, I know I'm too late, but here is what I was talking about a few nights ago: apt-get install xubuntu

---

### Post by catlett on 2006-08-24
> **nolesfan said:**
> Okay, I know I'm too late, but here is what I was talking about a few nights ago: apt-get install xubuntu

Just so people do not get confused the command is ```
apt-get install xubuntu-desktop
``` But you should really use aptitude instead of apt-get. It tracks the dependencies better and will remove all dependencies if removal is ever needed. Apt-get will leave dependencies that do nothing on your system.

Ubuntu, Kubuntu and Xubutnu all have the same ubuntu server base, they just have different window managers. 
Ubuntu's is gnome
Kubuntu's is kde
Xubuntu's is xfce

You can install all the window managers if you want. You just use the "options" at the login to select the "session". The sessions are listed by window manager. So select xfce session for xubuintu or gnome session for ubuntu.

You can install any version of ubuntu. (kubuntu, ubuntu, xubuntu or edubuntu) and then install the other window managers from the command line. They are installed with "meta-packages". The commands for the sake of information are 
```
sudo aptitude install ubuntu-desktop
```For ubuntu/gnome
```
sudo aptitude install kubuntu-desktop
```For kubuntu/kde
```
sudo aptitude install xubuntu-desktop
```For xubuntu/xfce
```
sudo aptitude install edubuntu-desktop 
```For edubuntu which is the educstional based version of ubuntu. I am pretty sure it runs gnome but I am not sure. It's packages are all educational based. It isnb't intended as a home computer desktop but as a student/teacher setup.

---

