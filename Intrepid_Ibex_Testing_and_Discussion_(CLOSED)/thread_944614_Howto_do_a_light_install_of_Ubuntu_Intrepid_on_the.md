---
title: "Howto do a light install of Ubuntu Intrepid on the Inspiron Mini"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by skroops on 2008-10-11
*I've found that it's hard to locate information on getting intrepid running on the Inspiron 910, so I've tried to put together the information I've gathered.  Please note that ubuntu 8.10 intrepid is unstable, unsupported software at this time.*
 
Intrepid runs a bit quicker than hardy, and in my experience increases battery life by 35%.  Also the new human theme looks great on the mini. (I had to lighten the dark brown color a bit for my tastes though)

If you're installing on the 8 or 4 GB flash drive, you will probably want to minimize the ubuntu fluff.  In order to get a reasonably small yet complete ubuntu up and running, you'll need to do a cli install.  You will need to either do a netboot, or set up a USB boot.

[SIZE=1][I]The latest netboot.tar.gz can be found [COLOR=DarkOrange][here]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/netboot.tar.gz")[/COLOR].
The latest mini.iso can be found [COLOR=DarkOrange][here]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso")[/COLOR]. (Use this if you don't have a big enough USB stick to fit the alternate ISO)
The alternate ISO can be found [COLOR=DarkOrange][here]("http://mirror.anl.gov/pub/ubuntu-iso/CDs/intrepid/ubuntu-8.10-beta-alternate-i386.iso")[/COLOR].

USB installer instructions can be found [COLOR=DarkOrange][here]("https://help.ubuntu.com/community/Installation/FromUSBStick")[/COLOR].
USB didn't work for me, so I followed the netboot install instructions.  You can find instructions for Windows [COLOR=DarkOrange][here]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")[/COLOR] (follow the Hoary Style section), and instructions for Ubuntu [COLOR=DarkOrange][here]("https://help.ubuntu.com/community/Installation/QuickNetboot")[/COLOR].
[/I][/SIZE][INDENT] 1.  After you've gotten the installer started, choose to install a CLI only installation by entering cli (then press enter) at the first prompt

2.  Proceed through the installation steps, but when you reach the disk partitioning section, choose to do a manual configuration.

3.  Delete all existing partitions.

4.  Create one partition the entire size of your drive.  (I tried to create an encrypted volume, but it wouldn't boot.  Let me know if you try and it works.)
You will need to set it bootable, with / as the mount point, and it is frequently recommended that you choose the ext2 file system to minimize writes.  I use ext3.

5.  When you choose finish, you will get a nag screen about not having swap space.  A netbook shouldn't need swap space, so just choose No.  If you really think you need swap space, you'll need to go back and create a swap partition somewhere between 50% and 200% of your RAM size, leaning towards the smaller side.  Using swap space will significantly increase the number of writes to that partition, which might cause it wear out faster than the rest of your disk'
[/INDENT][INDENT] 6.  After completing the installation, you should have your cli system up and running.  Log in and type these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo aptitude install ubuntu-desktop --without-recommends
```**Notice that the last line is aptitude, not apt-get.  This will allow you to completely remove the package later if you decide it's more than you need.  Also, the --without-recommends option will get a good looking ubuntu running, and allow to choose which applications you want.
[/INDENT]This will get a healthy intrepid installed, without any additional programs, and should take up around 1.5 GB.  After this, you will likely need some additional packages to make your system useful, such as *firefox *or *abiword*.  For many of these packages I would recommend that you install with aptitude with the &#8211;without-recommends option.  This will minimize disk usage, at the expense of some functionality.  If you decide later that you need the additional functionality you can just do a normal install.
 

 [B]Compatibility Modifications:
[/B]  Wi-fi with WEP and WPA works out-of-the-box. Unfortunately a lot of things don't work at this stage of intrepid, so you will have to do a few simple hacks to get everything working.  Considering that most of the 910's components are the same between different configurations, these hacks should work for most systems.
 

 **Sound**[INDENT]  In order to get sound working, you'll need to do the following:
 Open up a terminal and type
 ```
sudo apt-get mv /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.fresh
``` This will make a backup of alsa-base so that you can revert if necessary.


 Then, you need to create a new file as sudo called /etc/modprobe.d/alsa-base and copy only this into the file
 ```
options snd slots=snd-hda-intel 
 alias snd-card-0 snd-hda-intel 
 options snd-hda-intel model=dell
``` When you restart, you'll need to double-click your speaker icon and raise the Speaker volume to 100%, and you're sound will work.  Before you restart however, there's a few more things we can do.   


[/INDENT]**Touchpad**[INDENT]  For some reason, the touchpad has some wacky button emulations configured by default.  Intrepid isn't using xorg.conf to configure mouse settings any more, so you'll need to use xinput to configure settings.  To disable click emulation, enter
 ```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 8 0 0 0 0 1 2 3 
``` I couldn't get this command to &#8220;stick&#8221; through a reboot, so I've added it to System > Preferences > Sessions.


 Another thing I'd like to do is disable the touchpad during typing.  I haven't figured out how to enable SHMConfig without xorg.conf though.

[/INDENT]**Suspend/Hibernate**
 Neither of these worked out-of-the-box.  I've been able to get both of them working, but not at the same time.  From what I've gathered, this is because you can't specify to use ubuntu's sleep for suspend while using uswsusp for hibernation, and this is the only combination that seems like it would work.  Hibernation takes a long time to go down, but starts up very quickly.  It's also much more complicated to get working.  Suspend is very quick both ways but still drains battery power.[INDENT]
 To enable **suspend**, remove the package uswsusp.
 ```
sudo apt-get remove uswsusp
``` Suspend should now work.  You'll still have the option for hibernate, but it won't work.
[/INDENT][INDENT]  To enable **hibernation**, make sure that package uswsusp is installed.  You'll need to create a swap file (if you have a swap partition and uswsusp, hibernate should already work)  Replace the count argument with 50% - 100% of your ram size.  uswsusp will compress your ram's data so it is very unlikely you will need 100% of the size of you ram, but if you want to be sure then do so.
 ```
sudo dd if=/dev/zero of=/.hibernate bs=1048576 count=1024 
 sudo mkswap /.hibernate
``` Then, you will need to add this line to your fstab:
 ```
/.hibernate   swap  swap    noauto,defaults 0       0 
``` Notice the noauto option, this will keep the swap from being automatically enabled.
 Now turn swap on
 ```
sudo swapon /.hibernate
``` Hibernate should now work, test it and then do *sudo swapoff /.hibernate*.


 Now create a file */usr/lib/pm-utils/sleep.d/20swapctl* with the following text
 ```
#!/bin/bash 
 case "$1" in 
   hibernate|suspend) 
     swapon /.hibernate 
     ;; 
   thaw|resume) 
     swapoff /.hibernate 
     ;; 
   *) 
     ;; 
 esac 
  
``` This will automatically activate and deactivate your swap file before and after hibernation.  By the way, one advantage of doing it this way rather than creating a swap partition is that you can delete this file if you suddenly find you need the space, then recreate it later with the first two commands.
[/INDENT]**Ethernet**[INDENT]  My ethernet was just acting funny out-of-the-box.  To get it to play nice with nm-applet, I had to do two things.


 1.  Set it to be managed by nm-applet.  Edit the file */etc/NetworkManager/nm-system-settings.conf* and change the line under *[ifupdown]* to *managed=true*


 2.  Edit */etc/network/interfaces* and comment out the eth0 lines like this
 ```
# The primary network interface 
 #auto eth0 
 #iface eth0 inet dhcp 
  
``` After restarting, you're ethernet should be recognized by network manager as 'Auto eth0' and work properly.
[/INDENT][I]
 I haven't tested the webcam, so if anyone has information on that please share.  Other than that, this should have solved any glaring issues.  If anyone has anything to contribute please let me know![/I]

---

### Post by micke4 on 2008-10-11
I think so I have found that locate information intrepid running very quick than hardy, but my experience mostly people looks great mini. But ubuntu is very inspired but not running because unsupported software this time.

 [Crystal Meth](http://www.crystalrecovery.com)

---

