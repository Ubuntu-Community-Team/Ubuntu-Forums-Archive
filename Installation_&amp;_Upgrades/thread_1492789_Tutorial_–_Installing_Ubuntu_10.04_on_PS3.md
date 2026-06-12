---
title: "Tutorial – Installing Ubuntu 10.04 on PS3"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by phanboi on 2010-05-25
[U][B][http://phanboi.wordpress.com/2010/05/25/tutorial-ubuntu-10-04-ps3/](http://phanboi.wordpress.com/2010/05/25/tutorial-ubuntu-10-04-ps3/)



[/B][/U]                 [COLOR=#ff0000]*NOTE:  THIS IS A MODIFIED VERSION OF A TUTORIAL FOUND**[HERE]("http://psubuntu.com/wiki/InstallationInstructions/")*. I AM NOT RESONSIBLE FOR ANY DAMAGE DONE  TO YOUR PS3[/COLOR]
[COLOR=#ff0000]
[/COLOR]
 *These instructions were only tested on a 40GB ps3 phat running  firmware 3.15 NOT connected to the internet and I can personally confirm  this works*

 *There are more accurate guides available for those who want to  install [7.10]("http://psubuntu.com/wiki/InstallGutsy") or [8.04]("http://psubuntu.com/wiki/InstallHardy"). Following this  guide will probably be fine, but for more details follow those links!*




  [CENTER][[IMG]http://phanboi.files.wordpress.com/2010/05/iy.png?w=434&h=98[/IMG]]("http://phanboi.files.wordpress.com/2010/05/iy.png")[/CENTER]
 





**Guide to installing Ubuntu 10.04 on the PS3**

 *_Many people installing  Ubuntu 10.04 on there PS3 have been encountering mounting problems where  after a successful installation of Ubuntu, the system boots up only to  detect no drives with linux installed. Hence this guide is to help those  that are stuck on installing this._*


[CENTER]*_[[IMG]http://img443.imageshack.us/img443/6666/20100503145326.jpg[/IMG]]("http://ubuntuforums.org/showthread.php?t=1470902")_*
[/CENTER]


 The PS3 has a unique feature that allows you to install a third-party  operating system on the console. Because of its popularity and ease of  use, Ubuntu Linux is a good choice. By installing Ubuntu, your  PlayStation 3 becomes much more than just a game console. You can use it  as a home computer (running desktop applications), a web- or file  server, play media files, and run applications like Firefox, Open office  and multimedia tools.
 

Installing Ubuntu 10.04 on the PS3 will take several hours (3-4 for  me). The process involves three steps:
 
[LIST=1]
[*]Formatting PS3 to run Linux
[*]Installing Ubuntu
[*]Setting up your PS Ubuntu installation
[/LIST]
 [B]
Set up your PS3 to run Linux[/B]

You have to format your PS3 hard drive to install Ubuntu. You will  probably want to back up your save games! You will also need to let go  of some 10GB of disk space.

**What you need**
 
[LIST]
[*]A  PS3 Phat with firmware      3.15 or lower (I am assuming you have  firmware 3.15)
[*]This [COLOR=RoyalBlue][Ubuntu       version ]("http://cdimage.ubuntu.com/ports/daily/current/lucid-alternate-powerpc+ps3.iso")[/COLOR][for the PS3 burnt to a CD <-- Link]("http://cdimage.ubuntu.com/ports/daily/current/lucid-alternate-powerpc+ps3.iso")
[*]A USB keyboard and mouse
[*]A USB stick
[*]Petitboot v0.2 [COLOR=RoyalBlue][here]("http://ozlabs.org/%7Ejk/projects/petitboot/downloads/bin-0.2/otheros.bld")[/COLOR]  – alt. [COLOR=RoyalBlue][here]("http://www.mediafire.com/?oqmytmmzwtt")[/COLOR][ <-- Link]("http://www.mediafire.com/?oqmytmmzwtt")
[*]Petitboot older version [COLOR=RoyalBlue][here]("http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-petitboot/otheros.bld")[/COLOR]  – alt. [COLOR=RoyalBlue][here]("http://www.mediafire.com/?e2zaiylzuln")[/COLOR][ <-- Link]("http://www.mediafire.com/?e2zaiylzuln")
[/LIST]
 
**Formatting the PS3 hard disk**

 **The first thing you need to do is to format the PS3s hard  disk to make room for a second operating system (called Other OS). Your  user profiles and account information will remain on the XMB, but  remember to back up any saved games or media files you want to restore  after formatting the PS3 using a USB stick or an external hard disk.  Your game saves are located under Game > Saved Data Utility.**

 All downloaded games you paid for can be downloaded again without  having to pay for them. They’ll be in your account history in the PS  Store.
 
[LIST]
[*]Go to [System Settings] > [Format Utility].
[*]Select “Format Hard Disk” and click [Yes].
[*]Choose [Custom] and [Allot 10GB to the Other OS].
[*]Select [Quick Format] and confirm with [Yes].
[/LIST]
 Formatting will take a few seconds. Press X to restart the system.
 

Log in (you need to hit the PS button on your controller if it’s  deactivated after restart).
 
**Installing Other OS**

 The first step of this part of the installation is to install  petitboot v0.2. Download the file with the link provided (it should be  named “otheros.bld”
 
[LIST]
[*]Copy it to your USB stick in the folder; /PS3/otheros/
[*]Remove any discs from the PS3
[/LIST]
 
[LIST]
[*]Connect the USB into the PS3
[*]Go to [System Settings] > [Install Other OS]
[*]Go to [System Settings] > [Default System]
[*]Select “Other OS” and hit “Yes” to restart the      system
[*]Take out your USB and insert your keyboard and mouse
[/LIST]
 Note: If you get an error message that says “No applicable installer  was found” this means that either the file was not found or that your  external USB device was not detected (to check this you can open the  music or video section in the XMB, the device should be listed there).


 [B]
Loading the installer[/B]

This is where the otheros.bld we downloaded and installed first show up.  You should see a nice little interface on the screen. If not then press the number 0, 1, 2, or 3 to cycle between screen  resolutions until you are able to see petitboot on the screen.


 
Below is a list of functions for petitboot

Up, Down, Left, Right   –   Navigate between boot options
 Enter   –   Select boot option
 Delete / Backspace   -  Boot to PS3 XMB
 0     -    Safe
 1     -   Switch to 720p mode
 2     -    Switch to 1080i mode
 3     -    Switch to 1080p mode
 Alt+F1   -   Switch to text console
 Alt+F2   -   Switch back to GUI


 
Moving on, insert the Ubuntu CD which you burnt into the  PS3. It might take a minute before the CD icon shows up, if it doesn’t  after a while then try switching in between resolution modes, and when  it does, click the icon and choose “install”(should be the first option  on the disc). 
**Installing the base system**

 Once you’ve chosen install, a very basic screen should appear. Follow  through the step by step installation.
 
[LIST]
[*]First choose a language for the installation process
[*]Then your geographical location
[*]The system can try to determine your keyboard or you can choose it       from a list.
[*]The CD ROM is scanned, and additional term paper components are       loaded.
[*]If your PS3 is connected to the internet via cable, choose eth0:       Ethernet. Its better not to set up your wireless network here, unless  you      use WEP. Otherwise choose wireless and leave everything blank  and      continue. Skip the errors and then choose ‘do not setup an  internet connection      at this time’
[*]Disks and hardware is detected. If asked if you want to Activate       Serial ATA RAID devices just choose **yes **(anyone know  why?). (I was      never asked, so this part is really unnecessary)
[*]When asked how to partition the disks, choose “Guided – use       entire disk” (meaning the 10.7GB you formatted from the XMB in step       1)
[*]On the overview screen, hit “Finish partitioning and write changes       to disk”. If asked to confirm, choose yes.
[*]The partition is formatted and base system installed. It should       take about 10 minutes.
[*]Set up your user information (full name, username and password       twice), and choose whether you would like to create a private encrypted       directory for your user.
[*]Unless you’re using a proxy, leave the HTTP proxy information field       blank (just hit enter). (I was never asked this part. So again,       unnecessary)
[*]The system will start installing software. It might appear to hang  at      certain points, but just give the installer time and it will  move on. The      process will take a few hours (2-3 for me).
[*]System clock – Yes to UTC.
[/LIST]
 

The installation is done! The CD will automatically eject itself, but  you have to manually take it out of its slot (if you don’t, the PS3  will load it upon reboot). Then hit enter to continue after taking out  the disc to boot into reboot into petitboot.


 You will see nothing in petitboot. DO NOT PANIC!


 Petitboot doesn’t support ext4, so we’re going to have to install the  older version of petitboot.
 
[LIST]
[*]Press the delete/backspace button on the keyboard to boot into the  PS3 XMB
[*]Download the older version of petitboot from the link given and  replace the newer version with the older version on your USB
[*]Unplug the mouse or keyboard and insert the USB
[/LIST]
 
[LIST]
[*]Go to      [System Settings] > [Install Other OS]
[*]Go to      [System Settings] > [Default System]
[*]Select      “Other OS” and hit “Yes” to restart the system
[/LIST]
 

  Now you should be greeted not with a GUI but a command like interface  with 5 or so options. These options are pretty straightforward, so select the first option  (linux~) to boot into Ubuntu. Once greeted by the Ubuntu login screen, enter the user name and  password you chose during installation.
 

Congratulations! You should now have a working Ubuntu Operating  System installed on your PlayStation 3.
 

Move on to [Setup  PSUbuntu]("http://psubuntu.com/wiki/SetupPSUbuntu") for tips on how to configure the screen resolution and  making the OS run more smoothly.
 

Hopefully this helps people having trouble

 phanboi.

---

### Post by andibuntu on 2010-05-31
Good that you wrote it, though my experiences were slightly different - in my scenario (install most of it on an external HDD), most install methods would fail me badly. Petitboot did not work nicely either.

However - now that you are done - what is your experience with the repositories? Most packages I am trying to install are lacking a dependency that is not installable (because it is not present). e.g. do you see zlib1g-dev anywhere?
This renders most of the OS distribution completely useless for me.

I am considering to start over with Gentoo since it is more built in the spirit of building the code there unless someone can state something positive regarding what to do with those missing dependencies. (And no - I do NOT want to find all the sources myself, resolve the dependencies and compile them myself that is why we have a distribution with a great package manager...)

---

### Post by 1nsomn1ak on 2011-12-18
> **andibuntu said:**
> (And no - I do NOT want to find all the sources myself, resolve the dependencies and compile them myself that is why we have a distribution with a great package manager...)

First off I know I'm resurrecting a 1 year old post, but c'mon your going to go through all the trouble of installing a linux OS on a PS3 and your to lazy to resolve the dependencies yourself? Think of it as a challenge, a personal quest, have fun with it. When I find something interesting, I love to figure out how to make it work myself. That makes it all the more satisfying and rewarding when you succeed.

---

### Post by Idlewild1888 on 2012-09-24
Hello everyone.
 
I've been doing a lot of reading recently on installing Ubuntu on the PS3. I know I'm a little bit late on joining the action but I was wondering if it is still possible to make this happen? From what I have read, those pesky people over at Sony took away the 'install other OS' function in one of their firmware updates. Does this mean there is no way at all to get Linux running on my console? I would really like to have a play at getting it up and running but as far as I can see, once you are past a certain firmware version (which I am) there doesn't seem to be much info on if this is still possible or not. I did find a few tutorials that were based on installing it while running a CFW version but I am out of luck with that too as I cannot downgrade my OFW back to 3.55 without breaking out the soldering iron, which just ins't going to happen.

Apologies for coming to the table a bit late on this one, however, if any of you could point me in the right direction for getting this installed on my PS3 with up to dat firmware then I'd really appreciate it.
 
Cheers guys!
 
Dan

---

