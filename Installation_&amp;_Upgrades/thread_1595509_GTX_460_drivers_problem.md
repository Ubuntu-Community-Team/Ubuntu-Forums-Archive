---
title: "GTX 460 drivers problem"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by legionarius on 2010-10-13
Hello! I have just installed ubuntu 10.10 64 bit in dual boot with windows 7, but I got a big problem. After the installation of ubuntu 10.10 everything worked fine, untill I installed nvidia drivers suggested by ubuntu 10.10 (I clicked on the video card icon, and nvidia drivers have been downloaded and installed). After rebooting ubuntu 10.10, I tought everything was fine:
[[IMG]http://img510.imageshack.us/img510/2244/dscn1627k.th.jpg[/img]](http://img510.imageshack.us/i/dscn1627k.jpg/)

[](http://imageshack.us)

But after a few seconds I realized I had a big problem:
[[IMG]http://img214.imageshack.us/img214/9681/dscn1623h.th.jpg[/img]](http://img214.imageshack.us/i/dscn1623h.jpg/)

[](http://imageshack.us)

The screen had a strange red colour, and the mouse was surrounded by a square. I was able to move the mouse, but I was unable to click on icons. Or better I tryed to click on icons but nothing happened. I didn't know what to do, so I had to turn the power supply unit switch off.
I tryed to use ubuntu 10.10 many times, but everytime I enter into the os, after a few seconds I have that red screen problem:
[[IMG]http://img299.imageshack.us/img299/69/dscn1632j.th.jpg[/img]](http://img299.imageshack.us/i/dscn1632j.jpg/)

[](http://imageshack.us)

I think it could be a drivers problem, because before instaling nvidia drivers everything seemed to work fine on ubuntu 10.10.
Moreover I think the videocard is not broken because I tested it in windows, and I hadn't problems. I tryed to play a few games (Crysis Warhead for example), and the game experience was great.
Moreover I own the GTX 460 videocard from August, and the only time I had a problem was because of a drivers problem:
[[IMG]http://img413.imageshack.us/img413/840/dscn1621m.th.jpg[/img]](http://img413.imageshack.us/i/dscn1621m.jpg/)

[](http://imageshack.us)
It was clear that it was a drivers problem because the games had huge problems (5-6 fps), and after that red screen, I decided to reinstall the 258.96 drivers and I had no problems anymore.

Now I don't really know what to do, because in these conditions I cannot use ubuntu 10.10 because after a few seconds the red screen appears, and I'm forced to turn off the pc's power supply unit. So at the moment I'm using windows 7, hoping to solve this problem so I can use ubuntu 10.10 too :) 

In particular the video card name is "Gainward GTX 460 Golden Sample-Goes Like Hell 1 GB" The rest of my system specs are:
ENERMAX 525W MODU 82+ EMD525AWT *- *SEAGATE Barracuda 7200.12 500Gb SATA2 ST3500418AS *- *AMD Phenom II X4 945 4x512KB (3.0 GHz) 95W Deneb AM3 Box *- *ASUS M4A785TD-M EVO AM3 785G (GB-L/R/V/F/DDRIII) *- *CORSAIR XMS3 DDR3 4GB / 1600Mhz KIT CL8 New Classic *- *LG GH22NS50 RBBB 22x SATA bulk Black, GTX 460 glh *- * Samsung SyncMaster P2450H - LOGITECH X-230 - windows 7 ultimate edition 64 bit in dual boot with ubuntu 10.10



Thank you in advance. I hope we will be able to solve this problem :)

---

### Post by ratcheer on 2010-10-13
Nice system!

I am not sure what is wrong or how to fix it, but here is what I would do.

1) Go to the Additional Drivers applet and remove the video driver you installed. Reboot.

2) Add the x-swat PPA: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

3) Use your package manager (apt-get, aptitude, whatever) to update your software. Then, run Additional Drivers applet again to activate the Current (recommended) driver. This should update both the video driver and xorg to the PPA versions. Reboot, again.

If the above works, in the future you will only have to update and safe-upgrade with your package manager to get new driver upgrades. If it doesn't work, you should be no worse off than you are, now. I hope it works for you.

Tim

---

### Post by legionarius on 2010-10-13
Thank you very much for the reply ratcheer. I am really a beginner of ubuntu, so I hope I will be able to follow your intructions. I will let you know if I have been able to follow your instructions, and if I solve the problem.
Thank you again :)

---

### Post by legionarius on 2010-10-13
Ok ratcheer. I have followed some of your instructions, but I'd need a little bit of help since I'm not familiar with ubuntu. 
First of all I've followed the 1st step. Now that  video drivers have been removed, I am able to use ubuntu, and the red screen problem seems to be disappeared. Now I'm writing from ubuntu :)  The problem is I still ain't got video drivers.
To follow the next steps I have studied a bit since everything is new to me, but I'm not sure if I have done it in the right way. To add x-swat ppa I've written in the terminal "$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates" and I have received this answer:

enry@Italia:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[sudo] password for enry: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


I am not sure if I have committed errors. For me it's like trying to read chinese without knowing the language (btw I'm Italian).
Now I've tried to follow the 3rd step. I've clicked on "System - Admininstration - Synaptic Package Manager". Since I don't know the programs you have suggested me, I have installed the first one I found, aptitude. Or better I have clicked 2 times on it, and a new window has appeared, with a question: "mark additional required changes"?  I have clicked on "mark". And aptitude has became green on the packages list. After I've restared the system and I've written on the terminal "sudo aptitude update", but nothing has happened
enry@Italia:~$ sudo aptitude update
sudo: aptitude: command not found

I've checked again on the synaptic packages, and I've seen that aptitude is not green anymore (I remember it was green before rebooting). Honestly I'm not understanding a thing, even if I'm trying :/ 


ratcheer if you can, could you give me an helping hand? I'm sure I've made some mistakes because I am very inexperienced. I would need to know exactly what I have got to write in the terminal, or what steps I have got to follow, otherwise I'm sure I would commit other errors. By the way ubuntu 10.10 is really incredibly fast compared to windows 7. I'm really excited about it, but it's bad to do not have graphic drivers, when I have a very good video card.  So I'm really hoping to solve this problem with the help of this forum.

Thank you again, I'll check this posts for any suggestions to try to solve my problem :)

---

### Post by ratcheer on 2010-10-13
Are you running Ubuntu 10.10? If so, aptitude is no longer included in the default installation. You can either install aptitude with apt-get, or just use apt-get to update and safe-upgrade.

So, either:

sudo apt-get install aptitude
sudo aptitude update

OR

sudo apt-get update

Either way ends up accomplishing the same thing.

Tim

---

### Post by legionarius on 2010-10-14
Ok Tim. Thanks to your instructions I've installed aptitude, and I've run the update. Unfortunately after the updates, I've rebooted, I've selected system - administration - additional drivers, I've dowloaded and installed the drivers, but after rebooting, for the first 20 seconds everything worked fine, but suddenly the red screen appeared again. So now I've removed once again nvidia drivers :( 
Moreover when the update manager appeared, I've noticed that under "Other updates", there was nothing regarding nvidia drivers.
Other updates
tools for debugging intel graphic drivers
x.orf X server - AMD/ATI dispay driver wrapper
X.Org X server - AMD/ati Radeon display driver

Thank you anyway, at least we have tried to solve the problem. This is what I've done, and the replyes I've received from terminal:


enry@Italia:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libboost-iostreams1.42.0 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.42.0 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
0 upgraded, 7 newly installed, 0 to remove and 13 not upgraded.
Need to get 2,799kB of archives.
After this operation, 8,581kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main libboost-iostreams1.42.0 amd64 1.42.0-3ubuntu1 [59.3kB]
Get:2 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main libcwidget3 amd64 0.5.16-3ubuntu1 [310kB]
Get:3 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main aptitude amd64 0.6.3-2ubuntu4 [2,324kB]
Get:4 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main libsub-name-perl amd64 0.04-1build1 [10.7kB]
Get:5 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main libclass-accessor-perl all 0.34-1 [26.0kB]
Get:6 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main libio-string-perl all 1.08-2 [12.0kB]
Get:7 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main libparse-debianchangelog-perl all 1.1.1-2ubuntu2 [57.8kB]
Fetched 2,799kB in 5s (470kB/s)                       
Selecting previously deselected package libboost-iostreams1.42.0.
(Reading database ... 119712 files and directories currently installed.)
Unpacking libboost-iostreams1.42.0 (from .../libboost-iostreams1.42.0_1.42.0-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3ubuntu1_amd64.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.3-2ubuntu4_amd64.deb) ...
Selecting previously deselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.04-1build1_amd64.deb) ...
Selecting previously deselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously deselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously deselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.1.1-2ubuntu2_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.42.0 (1.42.0-3ubuntu1) ...
Setting up libcwidget3 (0.5.16-3ubuntu1) ...
Setting up aptitude (0.6.3-2ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.04-1build1) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.1.1-2ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place





After this operation I've run the aptitude update


enry@Italia:~$ sudo aptitude update
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                   
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                               
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                   
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main Translation-en           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                        
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                       
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick Release
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates Release [27.2kB]           
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/main Sources    
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/multiverse amd64 Packages
Get:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/main Sources [5,772B]
Get:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/restricted Sources [14B]
Get:5 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/universe Sources [14B]    
Get:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/multiverse Sources [14B]  
Get:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/main amd64 Packages [16.7kB]
Get:8 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/restricted amd64 Packages [14B]
Get:9 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/universe amd64 Packages [3,987B]
Get:10 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages [14B]
Fetched 53.9kB in 3s (13.6kB/s) 









I was thinking, if instead of the nvidia drivers ubuntu suggests me to install, I install older drivers, could I solve the problem?  I would like to avoid giving up using ubuntu for this problem, because I am starting to love this os. But not having graphic drivers is really bad, so untill I sove this problem I'm forced to use windows 7 :/ If anybody has got any ideas to try to solve this problem I would be glad to try.
Thank you again for the support ratcheer

---

### Post by ratcheer on 2010-10-14
You're welcome. I wish this would have solved your problem. I would think that with your video card, the newest drivers would be the best ones to use. I also wish I could be sure that you actually had the xswat diiver and xorg installed, but I suppose it is too late for that.

Good luck.

Tim

---

### Post by ratcheer on 2010-10-14
PS - I see in your "aptitude update" listing, above, that it did pick up the xswat PPA. So, it appears that you did get the xswat stuff installed.

After you ran that update, you did go back to the System >> Additional Drivers applet and activate the Current Recommended driver, didn't you?

This is too weird if nVidia's latest driver doesn't work with the video card you have.

Tim

---

### Post by legionarius on 2010-10-14
Yeah after the update I activated the Current Recommended driver, but the problem has not been solved :/  It seems that your nVidia 9400GT 1GB makes a better job than my GTX 460!!
At this point I don't really know what to do. If I was in windows I would have tried older drivers to see if they work. But I don't know what to do to solve this problem in ubuntu.
Anyway thank you for the help, at least we've tried to solve this problem. I fear I would have to wait a lot to see a new nvidia drivers release for ubuntu. I will keep checking this thread to see if there are new ideas to solve this problem.

---

### Post by gorbalad on 2010-10-14
I have the same problems. installed 10.10, and when I selected the restricted nvidia driver for my 460, those strange effects happened. then I tried ratcheteers trick, but all it installed was not nvidia-related, just these 3:
tools for debugging intel graphic drivers
x.orf X server - AMD/ATI dispay driver wrapper
X.Org X server - AMD/ati Radeon display driver

without the restricted driver everything's working, but slowly.

I'll try now the latest download from nvidias homepage.

---

### Post by gorbalad on 2010-10-14
yep, that worked. extremetuxracer ran with 400 fps on 1920x1200 with everything on maximum :)

---

### Post by legionarius on 2010-10-14
Great!! gorbalad you have solved your problem? I'm new to ubuntu, please could you tell me step by step what I can do to solve the problem? Thank you very much :)

---

### Post by legionarius on 2010-10-14
Ok I've tried to download Linux x64 (AMD64) display drivers from nvidia's site [http://www.nvidia.co.uk/object/linux-display-amd64-260.19.12-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-260.19.12-driver-uk.html)
But when I click on AGREE & DOWNLOAD button, instead of downloading the file, it opens up a window full of strange characters like these ones:   7L•’.Ý¿•Ší´Æ*³Ýú©¬¦aÍ¶VÞ—î7ºXukÈÚJóJ¬
Someone knows how can I download and install latest nvidia drivers from nvidia site?
[gorbalad]("http://ubuntuforums.org/member.php?u=1167165") you have solved downloading and installing those drivers? Thank you

---

### Post by cascade9 on 2010-10-14
OK, this is weird, I thought I had seen a similar thread. Post this on both so you can both see the others problem, maybe that will help your troubleshooting

[http://ubuntuforums.org/showthread.php?t=1596361](http://ubuntuforums.org/showthread.php?t=1596361)

---

### Post by gorbalad on 2010-10-15
@cascade9: thanks for linking!

@legionarius: downloading is easy, just do a rightclick on that button, and select 'save target as', or something like that.
The strange stuff you see is the full installation file, as your browser displays it (like it does with .txt or .html) instead of downloading it (like it would an executable file or something like that)

you could as well type ```
wget http://uk.download.nvidia.com/XFree86/Linux-x86_64/260.19.12/NVIDIA-Linux-x86_64-260.19.12.run
``` in a terminal

once you saved the file, you need to make sure it is executable ```
sudo chmod 777 NVIDIA-Linux-x86_64-260.19.12.run
``` (be sure to be in the directory where you did put that file)
the problem is, you can't run it while you run the gui, so you have to switch to a mode without gui: ```
sudo telinit 5
``` (be sure to have nothing unsaved open - if you don't have a second computer to look up these instructions, print them out) 

then login, and go to the directory where you did put that file (probably /home/legionarius or whatever) 'cd /home/legionarius'
and run the script as root: ```
sudo ./NVIDIA-Linux-x86_64-260.19.12.run
```follow it's instructions, then reboot: ```
sudo reboot
```now everything should be fine, until you install a newer kernel... but until then ubuntu hopefully provides a working NVIDIA-driver.

---

### Post by legionarius on 2010-10-15
[FONT=monospace]Thank you very much for the informations [/FONT]gorbalad! I'm trying to install them in this moment, even if I'm having some troubles (probably I'm making some mistakes.
After I downloading them in the desktop  (the directory is    /home/enry/Desktop ) I've written:
[FONT=monospace]
enry@Italia:~$ sudo chmod 777 NVIDIA-Linux-x86_64-260.19.12.run
[sudo] password for enry: 
chmod: cannot access `NVIDIA-Linux-x86_64-260.19.12.run': No such file or directory


What do you mean when you say:"[/FONT](be sure to be in the directory where you did put that file)"
I've simply opened the terminal and I've written "[FONT=monospace]sudo chmod 777 NVIDIA-Linux-x86_64-260.19.12.run"[/FONT]. I think I'm committing some mistakes.


And what does it means "run the script as root: "?


If I write sudo telinit 5 it says:
enry@Italia:~$ telinit 5
telinit: Need to be root


Thank you again :) 
[FONT=monospace]

[/FONT]

---

### Post by Soulcage on 2010-10-15
cd ~/Desktop          <- is what you forgot

Also I wonder if you ran all the commands after adding the x-swat repo.

sudo apt-get update
sudo apt-get upgrade

Then trying to install.

Assuming you installed right can you run sudo nvidia-settings and check the x server color correction section, select all channels and hit reset hardware defaults.

---

### Post by legionarius on 2010-10-15
Soulcage thank you for the reply :) 
cd ~/Desktop          <- is what you forgot

Ehm but where I have got to write down the directory? I haven't written it anywhere. I'm trying to follow gorbalad instructions but I not understanding how to make it :/ 
For example I open the terminal and what I have got to write first?

What I have done is to open the terminal and to write: "enry@Italia:~$ sudo chmod 777 NVIDIA-Linux-x86_64-260.19.12.run", but it says: "chmod: cannot access `NVIDIA-Linux-x86_64-260.19.12.run': No such file or directory"

ps: sorry if I am not able to follow instructions :/  Unfortunatly I'm not familiar at all with ubuntu :(

---

### Post by Soulcage on 2010-10-15
If you want to follow his instructions of installing what you got from nvidia's site you need to make sure to uninstall the other version you installed. Then it would be:

sudo chmod 777 ~/Desktop/NVIDIA-Linux-x86_64-260.19.12.run
sudo telinit 5
cd ~/Desktop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run
sudo reboot

I'm not sure what some of these do though. I just installed whats in the ppa though im using lucid atm.
Like I use "chmod +x ~/Desktop/NVIDIA-Linux-x86_64-260.19.12.run" to make it executable.

---

### Post by legionarius on 2010-10-15
ok now I try

EDIT:
enry@Italia:~$ sudo chmod 777 ~/Desktop/NVIDIA-Linux-x86_64-260.19.12.run
[sudo] password for enry: 
enry@Italia:~$ telinit 5
telinit: Need to be root
enry@Italia:~$ cd ~/Desktop
enry@Italia:~/Desktop$ sudo./NVIDIA-Linux-x86_64-260.19.12.run
bash: sudo./NVIDIA-Linux-x86_64-260.19.12.run: No such file or directory
enry@Italia:~/Desktop$ sudo ./NVIDIA-Linux-X86_64-260.19.12.run
sudo: ./NVIDIA-Linux-X86_64-260.19.12.run: command not found

OK found the error. In the last line I wrote X instead of x. Now a new windows has appeared :)

---

### Post by legionarius on 2010-10-15
Ups I clicked quote instead of edit.
Anyway a new problem has appeared. Now after:"sudo ./NVIDIA-Linux-x86_64-260.19.12.run" it opens up a new windows that says:


"ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com")."

In particular this is what the terminal says me:
enry@Italia:~/Desktop$ sudo ./NVIDIA-Linux-x86_64-260.19.12.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 260.19.12...................................................................................................................................
Received signal SIGINT; aborting.
Signal caught, cleaning up
enry@Italia:~/Desktop$

---

### Post by Soulcage on 2010-10-15
You must run ```
sudo telinit 5
``` before you run the file. Assuming this does what that guy claimed.

---

### Post by gorbalad on 2010-10-15
when you downloaded the file from nvidia's homepage, you saved it on your harddisk, which is organised in folders. one of these folders contains the downloaded file, probably /home/enry/Desktop 

if you want to do anything with that file you have to be in the folder. changing folders is done with cd, i.e. ```
cd /home/enry/Desktop
```

running as root:
for security reasons, there are different users on all unix machines. normal users (i.e. enry on your machine) aren't allowed to do everything (which means e.g. that malware run by them can't do as much harm). so, if you want to change things on your system, you have to switch to another user, with full rights. this user is usually called root (quite similar to administrator on windows machines). if you type sudo in front of a command, you run that command as root (and be asked for your password).


 I hope this helps...

---

### Post by legionarius on 2010-10-15
The problem is that when I write telinit 5, the terminal says me I "need to be root", By the way I ignore how "to be root"
enry@Italia:~$ telinit 5
telinit: Need to be root

EDIT: we've posted at the same time gorbalad. Now I read your post, trying to solve the problem :) Anyway guys thank you so much for all the patience you're having with me :)

---

### Post by legionarius on 2010-10-15
> **Soulcage said:**
> If you want to follow his instructions of installing what you got from nvidia's site you need to make sure to uninstall the other version you installed. Then it would be:

sudo chmod 777 ~/Desktop/NVIDIA-Linux-x86_64-260.19.12.run
sudo telinit 5
cd ~/Desktop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run
sudo reboot



Ok I've tried again to follow these instructions. Everything is fine, until I write " sudo ./NVIDIA-Linux-x86_64-260.19.12.run".Something happens and after it appears a small window that says me:

"NVIDIA Accelerated Graphics Driver for Linux-x86_64 (260.19.12)

 ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").

                                       OK  

 NVIDIA Software Installer for Unix/Linux                      www.nvidia.com"



This is what terminal says me:
enry@Italia:~$ sudo chmod 777 ~/Desktop/NVIDIA-Linux-x86_64-260.19.12.run
enry@Italia:~$ sudo telinit 5
enry@Italia:~$ cd ~/Desktop
enry@Italia:~/Desktop$ sudo./NVIDIA-Linux-x86_64-260.19.12.run
bash: sudo./NVIDIA-Linux-x86_64-260.19.12.run: No such file or directory
enry@Italia:~/Desktop$ sudo ./NVIDIA-Linux-x86_64-260.19.12.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 260.19.12...................................................................................................................................


and after this that window appears

---

### Post by realzippy on 2010-10-15
...have you blacklisted the nouveau driver formerly?

---

### Post by legionarius on 2010-10-15
> **realzippy said:**
> ...have you blacklisted the nouveau driver formerly?

No. I would not even know how to blacklist them. The window that appers saying ERROR: You appear to be running an X server .. etc  has got a sky-blue color

---

### Post by realzippy on 2010-10-15
use
```
sudo service gdm stop
```
instead of
```
sudo telinit 5
```

(have to log out and log in at shell before..)

..but after this works,you will run in the "nouveau not blacklisted problem"

Why do you install the driver manually?

---

### Post by legionarius on 2010-10-15
> **realzippy said:**
> use
```
sudo servive gdm stop
```instead of
```
sudo telinit 5
```(have to log out and log in at shell before..)

..but after this works,you will run in the "nouveau not blacklisted problem"

Why do you install the driver manually?


I will try to write 
sudo servive gdm stop  to see what happens :) Thank you for the suggestion.

Why do I try to install the driver manually? I don't really know. Honestly the only thing I care is to solve this display driver problem. To make it I need to install the drivers. Now I don't really care how to install them, I care only to install them. So the installation mode is not important to me. The important thing is to install them :)  But since I am really not familiar with ubuntu, I don't even know a way to install these drivers, so I am following the instructions of this post trying to solve the problem. Thanks everyone again for the support. And sorry for my bad english :) I try writing 
sudo servive gdm stop and I let you know if I solve in this way.

---

### Post by gorbalad on 2010-10-15
I think it's best if I try to explain again from the very beginning.

copy the following instructions to a terminal window, one after the other, press enter after every one:

```

cd ~/Desktop
wget http://uk.download.nvidia.com/XFree86/Linux-x86_64/260.19.12/NVIDIA-Linux-x86_64-260.19.12.run 
sudo chmod 777 NVIDIA-Linux-x86_64-260.19.12.run



```**make sure you have these instructions (on another computer, on paper, whatever - you will not have your browser for the next steps!**

close all open windows except a single terminal
then run ```
sudo telinit 5
```this should switch off the graphical interface, and send you to a text-only login screen.
after you logged in, type:
```
cd ~/Desktop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run

```follow the instructions.
then type
```
sudo reboot
```

---

### Post by gorbalad on 2010-10-15
realzippy: I did not have any 'nouveau not blacklisted problem'...
the manual install was the only way I managed to make my 460 work, seemingly because all other drivers do not correctly support it. (maybe it is because my 460, as well as legionarius' 460 are both overclocked, and the older drivers only work with the regular 460?)

---

### Post by realzippy on 2010-10-15
@legionarius

When you install the nvidia driver manually,you have to repeat this every time there is a kernel update,also you have to blacklist nouveau (the now running "free" nvidia driver)before you install.
Is there no driver offered in System/administration/hardware drivers?

Which ubuntu version do you run?

---

### Post by realzippy on 2010-10-15
> **gorbalad said:**
> realzippy: I did not have any 'nouveau not blacklisted problem'...
the manual install was the only way I managed to make my 460 work, seemingly because all other drivers do not correctly support it. (maybe it is because my 460, as well as legionarius' 460 are both overclocked, and the older drivers only work with the regular 460?)

Normally you had to blacklist nouveau.Nvidia driver says (when nouveau not blacklisted):
*The Nouveau kernel driver is currently in use by your system. This driver is incompatible with the NVIDIA driver and must be disabled before proceeding. Please consult the NVIDIA driver README and your linux distributions documentation for details on how to correctly disable the Nouveau kernel driver.*

Anyway,legionarius will see if this happens.

When you add the xswat ppa to your sources,you get the *same* (260.xx) driver with
System/administration/HardwareDrivers.
(nvidia-current)

---

### Post by legionarius on 2010-10-15
Ok thank you very much guys. Probably we have solved the problem. I have just installed the drivers, so now I am inside ubuntu, hoping that everything works fine, and that the red screen will not appear anymore :) 
Ok to reply the question: realzippy I run Ubuntu 10.10 the AMD 64 bit version.
After writing [FONT=monospace]"sudo servive gdm stop"[/FONT], the screen became black, and I wrote the rest of the instructions:
cd ~/Desktop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run

After the last instruction a new window has appeared, saying if I wanted to accept the Nvidia conditions. I clicked on Accept button.
After a message saying:
The distribution-provided pre-installscript failed! Continue installation anyway?

At this point I feared the installation would have failed. Instead I clicked on Yes, and the installation continued.

After it asked me install Nvidia's 32 bit compatibility Open GL libraries?
I clicked yes.

After the drivers have been installed I wrote sudo reboot, and now I'm inside ubuntu, and I see the full screen (so it seems the drivers have been installed successfully).

Thank you agan very much

---

### Post by realzippy on 2010-10-15
Fine.
Remember,if there is a kernel update,you have to repeat the driver installation.

---

### Post by legionarius on 2010-10-15
Another thing I've been asked was if " would you like to run the  nvidia-xconfig to automatically updateyour x-conf file so that nvidia  x-driverswill be used when you restart X? Any pre-existing X  configuration file  will be backed up".
I answered Yes. I hope I made the right choice, because I really didn't  know what it was talking about. Anyway the red screen has not appeared  yet, and this makes me think we have definitly solved the problem.  Thanks again with all my heart. You have been wonderful guys!!

"Remember,if there is a kernel update,you have to repeat the driver installation."
In this case I think I would be better to print the instructions somewhere, so I can be prepared in case of kernel updates! Anyway if the kernel wants to update I will be advised? But the Kernel updates even inside of the same ubuntu version? Or it updates only when I will update ubuntu 10.10 into the next version?

---

### Post by realzippy on 2010-10-15
..kernel updates are not related to the ubuntu version.

Have a look here:

[http://ubuntuforums.org/showpost.php?p=9924694&postcount=1401](http://ubuntuforums.org/showpost.php?p=9924694&postcount=1401)

If you do this,you will have nothing to do when there is a kernel update.

---

### Post by gorbalad on 2010-10-15
realzippy: that is what I tried before, but it did not work at all. 1 package for intel, and 2 for AMD/ATI gpus were installed, but how could that help with an nvidia problem?

---

### Post by legionarius on 2010-10-15
Ok I've followed your instructions, in this way I will not risk to have problems when the kernel is updated :) 
This is what the terminal show me:

enry@Italia:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[sudo] password for enry: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
enry@Italia:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick Release.gpg               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                   
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates Release                      
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/main Sources    
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Reading package lists... Done
enry@Italia:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
enry@Italia:~$ sudo ldconfig
enry@Italia:~$ 



Ok. Is it ok now? Thank you again very much!

---

### Post by realzippy on 2010-10-15
> **gorbalad said:**
> realzippy: that is what I tried before, but it did not work at all. 1 package for intel, and 2 for AMD/ATI gpus were installed, but how could that help with an nvidia problem?



Nothing is installed when adding the xswat ppa;the packages are only *available* for install...  (added to software sources)

if you have a look at [xswat]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"),you will see they also have the nvidia-driver beneath the ATI/Intel stuff.

---

### Post by realzippy on 2010-10-15
@ legionarius
[I]Ok. Is it ok now? Thank you again very much!
[/I]


go to 
System/Administration/AdditionalDrivers

is "nvidia-current" marked as in use?

---

### Post by gorbalad on 2010-10-15
nvidia offers 260.19.12 but xswat has just the 260.19.06! The difference between those two might be a bugfix for the 460...

---

### Post by realzippy on 2010-10-15
> **gorbalad said:**
> nvidia offers 260.19.12 but xswat has just the 260.19.06! The difference between those two might be a bugfix for the 460...

Yep,You are right,did not notice that.

---

### Post by gorbalad on 2010-10-15
My plan was to revert to xswat as soon as they have the 260.19.12 or newer.

---

### Post by legionarius on 2010-10-15
> **realzippy said:**
> @ legionarius
[I]Ok. Is it ok now? Thank you again very much!
[/I]


go to 
System/Administration/AdditionalDrivers

is "nvidia-current" marked as in use?

No, it is not marked as in use. When I click on "Additional Drivers" I read "This driver is not activated". There is a button "Activate", and under this button there is another one "Close".
Anyway in this moment I'm looking at a full-hd move, and I see it in a perfect way. I've tried different videos, and after I've installed the drivers everything is great. So I think that the drivers are working great. The difference between now (drivers installed), and before (drivers not installed) is huge, so I don't know why it is written that the driver is not activated, when everything seems to work great now.

---

### Post by gorbalad on 2010-10-15
you installed another driver (via my instructions), but the one provided by ubuntu/xswat is deactivated, so it is displayed as such.

---

### Post by legionarius on 2010-10-15
> **gorbalad said:**
> you installed another driver (via my instructions), but the one provided by ubuntu/xswat is deactivated, so it is displayed as such.
Perfect! The important is that everything works fine now! Thank you again [ratcheer]("http://ubuntuforums.org/member.php?u=848769") [cascade9 ]("http://ubuntuforums.org/member.php?u=890788")[gorbalad ]("http://ubuntuforums.org/member.php?u=1167165")[Soulcage and ]("http://ubuntuforums.org/member.php?u=642662")[realzippy.  ]("http://ubuntuforums.org/member.php?u=216523")Compared to windows 7, ubuntu 10.10 seems so much faster, that it's like if it would run on a raid of solid state drivers (without spending money!)  I'm really happy about it. I think I will continue to use windows for games, but Ubuntu 10.10 for everything else I can run on Ubuntu :)

---

### Post by realzippy on 2010-10-15
*I think I will continue to use windows for games, but Ubuntu 10.10 for everything else I can run on Ubuntu *

Yeah,that is what I do for 3 years now.
I hate booting windows meanwhile....
Do not forget to let the "muscles" of your powerful card "play";means,
nice compiz-setup with 16x Antialiasing,8xAnisotroping Filter,Sync to Vblanc....and a nice equirectangular skydome backround in 6000x3000 pixels.
PM me when needing advice for this.

---

### Post by gorbalad on 2010-10-18
Now Xswat has the 260.19.12 driver as well, so I switched back. I hope I'll now get updates automatically.

---

### Post by gorbalad on 2010-11-18
Be sure to have the manually-installed driver de-installed, otherwise X will not start after the first upgrade (e.g. the currently-available 260.19.21).

---

