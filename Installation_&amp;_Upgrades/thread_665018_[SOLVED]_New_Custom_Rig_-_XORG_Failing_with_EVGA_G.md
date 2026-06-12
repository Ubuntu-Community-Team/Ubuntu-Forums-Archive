---
title: "[SOLVED] New Custom Rig - XORG Failing with EVGA GeForce 8800GT?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by petgraveyard on 2008-01-11
Hello,

I tried to install Ubuntu 7.10 on my new custom rig using the LiveCD first.  After the CD graphically let me know that I was going to run in low graphics mode and I hit "continue," the install just hung up on "starting local system something something" and hung there for over 30 minutes while I rocked out on DDR.

I then tried the alternate disk.  It installed, and I booted the first time.  Success (minus graphics).  I could install the graphics driver later, I thought.  I had to shut down and move the case because I had it on the floor, where I couldn't hook up my ethernet cable.  I moved the case and started it up again.  Lo and behold, I got an error message from XORG saying that it couldn't start.  I tried again, same thing.  The server output said something like too many failures or something.  Weird.

Does anyone know what I can do to get this baby working??

---

### Post by PmDematagoda on 2008-01-11
Boot Ubuntu in Recovery Mode. Then execute:-
```
sudo apt-get install nvidia-glx-new
```
After that is complete, execute:-
```
sudo nvidia-settings --config enable
```
After you have done that, execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
And select the driver as Nvidia and any other options you may want, after reconfiguration is complete, execute:-
```
startx
```

---

### Post by papatrpt89 on 2008-01-11
I am in this exact same boat, though I haven't tried installing ubuntu yet (friend's pc).  I have had a little bit of experience dealing with this kind of thing before.  Please post back with how this works for you!

I started a little howto about this topic at [http://ubuntuforums.org/showthread.php?p=4119312](http://ubuntuforums.org/showthread.php?p=4119312) if you are curious/this doesn't work for you.

Good luck!

---

### Post by petgraveyard on 2008-01-11
I have tried BOTH of your suggestions.  I get these errors when starting X:

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration

What should I do?  I installed the latest drivers from the NVIDIA site and applied them using the automatic reconfiguring tool NVIDIA has and I get errors...this doesn't make sense??

---

### Post by papatrpt89 on 2008-01-12
I don't quite know what to say, my thoughts are try uninstalling the driver, and things that relate to it, using a sudo apt-get search nvidia, and remove things that are related.  Then, try again?  I was thinking maybe they were conflicting...

Other than that, some people have suggested automatix.  And once I get access to that PC, I will post back with whats going on.

Sorry I couldn't be of more help!

---

### Post by PmDematagoda on 2008-01-12
First remove the Nvidia package using:-
```
sudo apt-get remove nvidia-glx-new
```
Then download the Nvidia installer using:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run
```
Execute:-
```
ls
```
to find the name of the downloaded file and execute it(Replace "filename" with the name of the Nvidia installer):-
```
sudo sh filename
```
After that is complete, run:-
```
sudo dpkg-reconfigure xserver-xorg
```
And try:-
```
startx
```

---

### Post by petgraveyard on 2008-01-12
That latest bit still fails to work...I still get an error when starting to try to use this driver...it always says that it can't initialize the device...

---

### Post by PmDematagoda on 2008-01-12
Could you post the result of:-
```
lspci
```
also, what bus address did you specify your VGA card to be at when you were reconfiguring the X-Server?

---

### Post by petgraveyard on 2008-01-12
> **PmDematagoda said:**
> Could you post the result of:-
```
lspci
```
also, what bus address did you specify your VGA card to be at when you were reconfiguring the X-Server?

Here's the output:

```

zach@nirvana:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

I believe the bus address was the second one on that list, 00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02).  I kept whatever was the default when I was configging X.  Should it be something else?I see the nVidia Unknown device, I'll give it a shot with that and report back ;).

Thanks for sticking with me by the way!

---

### Post by PmDematagoda on 2008-01-12
> I kept whatever was the default when I was configging X. Should it be something else?I see the nVidia Unknown device, I'll give it a shot with that and report back.
Good luck, I hope it works:).

> Thanks for sticking with me by the way!
It is nothing:), I stuck with worse cases before;).

---

### Post by petgraveyard on 2008-01-12
> **PmDematagoda said:**
> Good luck, I hope it works:).


It is nothing:), I stuck with worse cases before;).

Alright, I went into recovery mode and I tried it.  I installed the NVIDIA driver and I reconfigured X.  I then started x and I saw the NVIDIA logo on the screen, then there were a bunch of dots all over the place and a window that said that I should be running as root, so I hit cancel, rebooted, and started up in regular mode...it said I had to load in low-graphics mode...now I'm stuck in 800x600 vesa, whereas I had 1280x1024 before...

Shouldn't the nvidia logo mean I did it right???

Please help me!!!

---

### Post by PmDematagoda on 2008-01-12
Try:-
```
sudo dpkg-reconfigure xserver-xorg
```
again. When you reach the notice about fail-safe, press Ctrl+Alt+F1, then execute:-
```
sudo /etc/init.d/gdm stop
```
run the code to reconfigure the X-Server and then restart GDM using:-
```
sudo /etc/init.d/gdm start
```

---

### Post by petgraveyard on 2008-01-12
> **PmDematagoda said:**
> Try:-
```
sudo dpkg-reconfigure xserver-xorg
```
again. When you reach the notice about fail-safe, press Ctrl+Alt+F1, then execute:-
```
sudo /etc/init.d/gdm stop
```
run the code to reconfigure the X-Server and then restart GDM using:-
```
sudo /etc/init.d/gdm start
```

Sir, you're going to get a lot of thanks when this is all over...

OK, so while I was still in the session I went to the terminal and reconfigured xorg, then I rebooted.  It gave me the fail-safe message again, then I hit Control alt f1 and I stopped GDM.  I reconfigged Xorg again and then I started GDM.  Then I hit Control alt f7 to start my windowed session again...I think that's what you're supposed to do?  Anyway, when I did that I got hit with the fail-safe message again.  I hit continue and I'm back in the same boat again.  Did I do anything wrong?

---

### Post by PmDematagoda on 2008-01-12
Try another thing, when you get to the fail-safe message, change to a different tty(Using Ctrl+Alt+F*) and stop GDM. Then move to the root directory using:-
```
cd /root
```
list the folder contents and rerun the Nvidia installer again.

After the install is done, execute:-
```
sudo /etc/init.d/gdm start
```

---

### Post by petgraveyard on 2008-01-12
> **PmDematagoda said:**
> Try another thing, when you get to the fail-safe message, change to a different tty(Using Ctrl+Alt+F*) and stop GDM. Then move to the root directory using:-
```
cd /root
```
list the folder contents and rerun the Nvidia installer again.

After the install is done, execute:-
```
sudo /etc/init.d/gdm start
```

I'm getting hung up on running the Nvidia installer because it says an instance of Xorg is running...is there any way to stop Xorg so I can run the installer with the GDM stopped?

---

### Post by PmDematagoda on 2008-01-12
Do:-
```
sudo killall Xorg
```

---

### Post by petgraveyard on 2008-01-12
> **PmDematagoda said:**
> Do:-
```
sudo killall Xorg
```

The killall didn't work...it said no process killed.  I went back to the graphical tty and logged in, then took a look at the system monitor.  x-something-manager was still there, as was xorg, so I took note of the process IDs and went into another TTY and formally "sudo kill"ed them.  GDM was shut down and then I loaded the driver file, even though I could still access the graphical tty...

Anyway, I ran the installer then I told it not to replace my xorg config, then used startx and started x.  Sure enough, it seems that I've got the right driver installed now.  It's at the desired resolution and I've got compiz (well, "destop effects") running now.  When I try to access "screens and graphics" it says "Failed to run displayconfig-gtk as user root.  Unable to copy the user's Xauthorization file." so I can't really change anything.

So, can I expect this change to be reflected when I reboot the system?  Also, is this it?  Is the driver loaded?  Am I good?

---

### Post by PmDematagoda on 2008-01-12
Open Nautilus and go to /etc/X11, then copy the xorg.conf file as a backup. Then post the result of this:-
```
ls -la ~
```

---

### Post by petgraveyard on 2008-01-12
> **PmDematagoda said:**
> Open Nautilus and go to /etc/X11, then copy the xorg.conf file as a backup. Then post the result of this:-
```
ls -la ~
```

Here's the output:

```

zach@nirvana:~$ ls -la ~
total 17944
drwxr-xr-x 35 zach zach     4096 2008-01-12 23:51 .
drwxr-xr-x  3 root root     4096 2008-01-11 23:03 ..
drwx------  3 zach zach     4096 2008-01-12 13:12 .adobe
-rw-------  1 zach zach     1089 2008-01-12 23:08 .bash_history
-rw-r--r--  1 zach zach      220 2008-01-11 23:03 .bash_logout
-rw-r--r--  1 zach zach     2298 2008-01-11 23:03 .bashrc
drwxr-xr-x  3 zach zach     4096 2008-01-11 23:05 .cache
drwxr-xr-x  5 zach zach     4096 2008-01-12 23:25 .config
drwxr-xr-x  2 zach zach     4096 2008-01-12 23:52 Desktop
-rw-------  1 zach zach       28 2008-01-12 23:22 .dmrc
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:05 Documents
drwxr-xr-x  4 zach zach     4096 2008-01-12 23:51 .emerald
-rw-r--r--  1 root root      309 2008-01-11 23:14 enable
-rw-------  1 zach zach       16 2008-01-11 23:06 .esd_auth
drwxr-xr-x  7 zach zach     4096 2008-01-12 23:23 .evolution
lrwxrwxrwx  1 zach zach       26 2008-01-11 23:03 Examples -> /usr/share/example-content
drwx------  4 zach zach     4096 2008-01-12 23:22 .gconf
drwx------  2 zach zach     4096 2008-01-12 23:52 .gconfd
-rw-r-----  1 zach zach        0 2008-01-12 21:59 .gksu.lock
drwxr-xr-x  3 zach zach     4096 2008-01-11 23:05 .gnome
drwx------ 10 zach zach     4096 2008-01-12 23:15 .gnome2
drwx------  2 zach zach     4096 2008-01-11 23:05 .gnome2_private
drwxr-xr-x  2 zach zach     4096 2008-01-12 21:54 .gstreamer-0.10
-rw-r--r--  1 zach zach      104 2008-01-12 23:25 .gtk-bookmarks
-rw-r--r--  1 zach zach       86 2008-01-11 23:05 .gtkrc-1.2-gnome2
-rw-------  1 zach zach     1614 2008-01-12 23:25 .ICEauthority
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:14 .icons
drwxr-xr-x  3 zach zach     4096 2008-01-12 13:11 .java
drwxr-xr-x  3 zach zach     4096 2008-01-11 23:05 .local
drwx------  3 zach zach     4096 2008-01-12 13:12 .macromedia
drwx------  3 zach zach     4096 2008-01-11 23:05 .metacity
drwx------  4 zach zach     4096 2008-01-12 13:12 .mozilla
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:05 Music
drwxr-xr-x  3 zach zach     4096 2008-01-12 23:15 .nautilus
-rw-r--r--  1 zach zach    94208 2008-01-12 22:40 nautilus-debug-log.txt
-rw-r--r--  1 zach zach 17548957 2007-12-20 11:42 NVIDIA-Linux-x86-169.07-pkg1.run
-rw-r--r--  1 zach zach     1134 2008-01-12 23:41 .nvidia-settings-rc
drwx------  3 zach zach     4096 2008-01-12 22:40 .openoffice.org2
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:05 Pictures
-rw-r--r--  1 zach zach      566 2008-01-11 23:03 .profile
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:05 Public
drwx------  5 zach zach     4096 2008-01-12 23:01 .purple
-rw-------  1 zach zach      603 2008-01-12 22:40 .recently-used
-rw-r--r--  1 zach zach     2869 2008-01-12 23:51 .recently-used.xbel
-rw-------  1 zach zach       52 2008-01-11 23:42 .serverauth.20826
-rw-------  1 zach zach       52 2008-01-12 12:38 .serverauth.21780
-rw-------  1 zach zach       52 2008-01-12 23:25 .serverauth.7360
drwxr-xr-x  3 zach zach     4096 2008-01-12 23:45 .subversion
-rw-r--r--  1 zach zach        0 2008-01-11 23:06 .sudo_as_admin_successful
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:05 Templates
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:14 .themes
drwx------  3 zach zach     4096 2008-01-11 23:14 .thumbnails
drwx------  2 zach zach     4096 2008-01-12 13:14 .Trash
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:46 .update-manager-core
drwx------  2 zach zach     4096 2008-01-12 18:18 .update-notifier
drwxr-xr-x  2 zach zach     4096 2008-01-11 23:05 Videos
-rw-------  1 root root        0 2008-01-12 21:56 .Xauthority
-rw-------  2 zach zach        0 2008-01-12 23:25 .Xauthority-c
-rw-------  2 zach zach        0 2008-01-12 23:25 .Xauthority-l
-rw-------  1 zach zach   484682 2008-01-12 23:51 .xsession-errors

```

---

### Post by petgraveyard on 2008-01-12
And I'm trying to start emerald...I installed compizfusion as per [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) , then I installed emerald to get some themes, and when I try to type in emerald it says:
```

emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

```

---

### Post by PmDematagoda on 2008-01-13
Try:-
```
emerald --replace
```

Your Xsession files look to be in order, try rebooting your PC again.

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> Try:-
```
emerald --replace
```

Your Xsession files look to be in order, try rebooting your PC again.

AGGGGGGGG!!!!!!

I rebooted my system and I got the fail-safe message again!!! What am I doing wrong????

I'm using the VESA drivers still too...on 800x600...

---

### Post by PmDematagoda on 2008-01-13
First make a backup of the current xorg.conf:-
```
cp /etc/X11/xorg.conf ~/xorgbroken.conf

```
then kill GDM, replace the xorg.conf with the backup one:-
```
sudo cp /etc/X11/xorg.conf backupxorg.conf
```
and start GDM again.

If that works, we can move on to the next thing.

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> First make a backup of the current xorg.conf:-
```
cp /etc/X11/xorg.conf ~/xorgbroken.conf

```
then kill GDM, replace the xorg.conf with the backup one:-
```
sudo cp /etc/X11/xorg.conf backupxorg.conf
```
and start GDM again.

If that works, we can move on to the next thing.

Alright, that didn't work.  When I restarted GDM I got errors saying something like the kernel that was installed didn't match the driver or something (not the Linux kernel, it's that kernel thing the driver installer downloads and installs when it's installing).  I think it's kernel module, but not 100% sure.  I wanted to give you a log, but /var/log/Xorg.0.log has different data than what I got, which means it wasn't from that time.

What's this kernel module or whatever and how do I get the right one working?

---

### Post by PmDematagoda on 2008-01-13
Rerun the Nvidia installer again, but this time, say no when the installer is going to download the kernel, instead let it compile it's own kernel, that should to the trick.

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> Rerun the Nvidia installer again, but this time, say no when the installer is going to download the kernel, instead let it compile it's own kernel, that should to the trick.

I let it download the kernel the last time, but it said it could not and I think it compiled its own kernel.  I'll go again though, and see what it does.

---

### Post by petgraveyard on 2008-01-13
> **petgraveyard said:**
> I let it download the kernel the last time, but it said it could not and I think it compiled its own kernel.  I'll go again though, and see what it does.

I reinstalled in recovery mode and it did not work at all.  Still getting the fail-safe.  I'm getting really desperate and frustrated here...how did I get it to work that one time??

---

### Post by PmDematagoda on 2008-01-13
I believe you would have to configure the X-Server after installing the driver. Also, post the result of:-
```
cat /etc/lsb-release
```
and 
```
uname -a
```

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> I believe you would have to configure the X-Server after installing the driver. Also, post the result of:-
```
cat /etc/lsb-release
```
and 
```
uname -a
```

OK, so I went into tty3, I shut down the GDM and x session manager's process, then I reinstalled the nvidia driver and had it compile its own kernel module...then I reconfigured X and I started up GDM again...I saw the nvidia logo and everything worked...but then I rebooted and the fail-safe message popped up!  I honestly don't know WHAT is going on right now!!!

Those outputs:
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

```

Linux nirvana 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

```

---

### Post by PmDematagoda on 2008-01-13
Ok, now try this:-
```
sudo apt-get purge nvidia-glx-new
```
then
```
sudo apt-get purge nvidia-glx
```
after those two are complete, do:-
```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```
Then rerun the installer again, and then do:-
```
sudo dpkg-reconfigure xserver-xorg
```
and try running GDM again.

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> Ok, now try this:-
```
sudo apt-get purge nvidia-glx-new
```
then
```
sudo apt-get purge nvidia-glx
```
after those two are complete, do:-
```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```
Then rerun the installer again, and then do:-
```
sudo dpkg-reconfigure xserver-xorg
```
and try running GDM again.

Neither of those packages were installed, and that folder wasn't present...running GDM again yields the same result...

---

### Post by PmDematagoda on 2008-01-13
Allright, I am running out of ideas right now, try this:-
```
sudo rm /etc/init.d/nvidia-* 
```
```
sudo nano /etc/default/linux-restricted-modules-common
```
Then add this to the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```

After that is done, rerun the installer, reconfigure the X-Server and try starting GDM again.

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> Allright, I am running out of ideas right now, try this:-
```
sudo rm /etc/init.d/nvidia-* 
```
```
sudo nano /etc/default/linux-restricted-modules-common
```
Then add this to the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```

After that is done, rerun the installer, reconfigure the X-Server and try starting GDM again.

OH MY GOSH!  Sir, you are a genius!  That last bit of code must have worked, because I rebooted and the driver is still there - I still see the NVIDIA logo!  You are a lifesaver!

Thank you sooooooooooooo much!

Really, you didn't need to spend your time helping me like this, that was VERY nice of you to do for me.  I know it's the weekend and this is your free time, so it's really great that you took the time out to help me.  From my part of the world to yours, THANK YOU!!

---

### Post by PmDematagoda on 2008-01-13
I am truly glad it worked.

I hope you have a great time on Ubuntu.

> Really, you didn't need to spend your time helping me like this
It is what I do because I want to do it, it is no trouble at all:).

> THANK YOU!! 
You are very much welcome:).

Also could you mark this thread solved by pressing Thread Tools>Mark Thread as solved, it can help others who have the same problem as you did.

---

### Post by petgraveyard on 2008-01-13
> **PmDematagoda said:**
> I am truly glad it worked.

I hope you have a great time on Ubuntu.


It is what I do because I want to do it, it is no trouble at all:).


You are very much welcome:).

Also could you mark this thread solved by pressing Thread Tools>Mark Thread as solved, it can help others who have the same problem as you did.

Alright, I guess we're squared away!  And it's really great that you do this for people like me who don't know what we're doing ;).  Time to finish my homework and enjoy a DVD (Snakes on a Plane :popcorn:)...on my computer!  I love Ubuntu ;)

---

### Post by PmDematagoda on 2008-01-13
> **petgraveyard said:**
> Alright, I guess we're squared away!  And it's really great that you do this for people like me who don't know what we're doing ;).  Time to finish my homework and enjoy a DVD (Snakes on a Plane :popcorn:)...on my computer!  I love Ubuntu ;)

I wish you good luck with our homework and hope that you enjoy your movie, and if you ever have any question about Ubuntu, do not hesitate to look to the forum:).

---

### Post by papatrpt89 on 2008-01-13
And I thank you as well.  I will be plunging into this problem myself, sometime soon.  I'm sure this thread will be *INCREDIBLY* useful.  Thanks for all the time and effort that you put in!

---

### Post by jmvaz on 2008-01-14
Hey there!
I'm having the exact same problem installing my 8800GT on Ubuntu 7.10.
I managed to do it the other day, but the fan speed wouldn't slow down, despite de temp was about 40º.
Anyways, I tried this method and couldn't get any results (still with vesa). Perhaps I'm doing something wrong. could someone post a step by step how to?I guess Im missing something!

Thanks a lot ;)

---

### Post by PmDematagoda on 2008-01-14
The fan speed issue is something to do with the Nvidia driver itself. Unfortunately there does not seem to be fix released as of yet, so you would have to revert back to the older Nvidia driver.

---

### Post by jmvaz on 2008-01-14
and how do I do that?I'm now using 169.07. which installer should I use?

---

### Post by PmDematagoda on 2008-01-14
Unfortunately I do not think that you could find the previous driver on the Nvidia web site. I am not sure myself, you could wait for someone else to clarify this.

---

### Post by jmvaz on 2008-01-14
hm, ok!
Thank you anyway. You've been helpful :)

---

### Post by Culexian on 2008-01-17
Excellent thread, I've now successfully managed to get the new Nvidia driver working thanks to this thread. I'm not certain exactly what did it, but it looks like removing all traces of the previous one helped a lot.

---

### Post by peppertarts on 2008-01-18
> **PmDematagoda said:**
> Allright, I am running out of ideas right now, try this:-
```
sudo rm /etc/init.d/nvidia-* 
```
```
sudo nano /etc/default/linux-restricted-modules-common
```
Then add this to the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```

After that is done, rerun the installer, reconfigure the X-Server and try starting GDM again.

Hey PmDematagoda, I ran into the same problem with a Sparkle 8800GT and your solution worked for me too :grin: Many thanks.

---

### Post by GTengineer on 2008-03-07
> **PmDematagoda said:**
> Allright, I am running out of ideas right now, try this:-
```
sudo rm /etc/init.d/nvidia-* 
```
```
sudo nano /etc/default/linux-restricted-modules-common
```
Then add this to the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```

After that is done, rerun the installer, reconfigure the X-Server and try starting GDM again.

First of all many thanks PmDematagoda, this (sort of) worked for me. However I had to in addition remove the Ubuntu splash screen. For some reason it will not work when it is enabled but otherwise it boots perfectly fine.

I guess it is not a big deal but I would like to figure out how to get the splash screen back up. If anyone has any ideas what could be causing the splash screen to hang please let me know.

Thanks!
GT

---

### Post by SuperAndy on 2008-04-21
I am getting a 8800GTS in the next few days, and will be going for this in Hardy. I am hoping this has been fixed for tyhe hardy release, but if not, it seems simply like a case of manually disabling the nv driver. Should be ok, I will shout with what happens.

---

### Post by SuperAndy on 2008-04-24
just to clarify, this card is well and truly nailed in ubuntu. after having the ati open source driver installed for my own card, i simply booted into ubuntu, and it loaded the desktop first time. i then enabled desktop effects, it installed the nvidia driver automatically, and on reboot i had a lightning fast compiz setup. so much easier than in vista :D

---

