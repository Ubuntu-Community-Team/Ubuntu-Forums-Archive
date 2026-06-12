---
title: "Screen freezes at &quot;Checking battery status..&quot; at startup of 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by kebabbaro on 2011-10-15
Hello, I just installed for the 2nd time Ubuntu 11.10 from a USB stick, the first time choosing the "show login screen" option this time choosing "login automatically" but the result is the same: at restart after installlation is complete the screen freezes at "Checking battery status.." execution. 

Tried to CTRL+ALT+F1, login and sudo restart lightDM but that put me back to the frozen screen with the same reading "Checking battery status.."

The machine is an ASUS M51Sn, and starting from version 9.04 I never had any issue installing Ubuntu before.

Any help please :(

---

### Post by garvinrick4 on 2011-10-15
Try these in tty of your choice. ctrl/alt/F1 thru F6   (ctrl/alt/F7 gets back to X when running)
```
sudo apt-get install --reinstall lightdm
``````
sudo start lightdm
```if needed
```
sudo /etc/init.d/lightdm restart
```Need to have lightdm running is it now? Lightdm took over for GDM.

---

### Post by kebabbaro on 2011-10-15
> **garvinrick4 said:**
> Try these in tty of your choice. ctrl/alt/F1 thru F6   (ctrl/alt/F7 gets back to X when running)
```
sudo apt-get install --reinstall lightdm
``````
sudo start lightdm
```if needed
```
sudo /etc/init.d/lightdm restart
```Need to have lightdm running is it now? Lightdm took over for GDM.
Lightdm is up and running, according to what I read on the screen: before the line "checking battery status" there are many lines, one of which states "starting lightdm                                        [OK]"

BTW I tried to install Ubuntu 11.10 in a virtual machine with Virtual Box 4-1 and it actually worked: now I have 11.10 installed but only as a VM :-|

---

### Post by dino99 on 2011-10-15
check your sources.list and set ONLY genuine repos (comment out everything else, if any), then: clean/autoclean/autoremove/update/dist-upgrade/ and finally

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

---

### Post by kebabbaro on 2011-10-16
No i don't want to make a distribution upgrade but a clean install.

BTW I think this is a kernel problem, not an Ubuntu one, so i will just stay with my working installation of 11.04 until this is fixed.

Just been taught that when a system works, it is good practice not to change it, is it not?

---

### Post by kebabbaro on 2011-10-16
Upd8: at grub prompt, choosing previous linux version then linux-3.0 I can access the lightdm screen, then if i log in as my username, after some black screen i am brought back to the login screen, but if a login as guest I can finally get to startup Ubuntu 11.10.  In short: now I can use Ubuntu 11.10 only as a guest.  Not exactly problem solved but still, at least I can startup the system.

---

### Post by andho on 2011-10-16
Same thing happens for me.

sudo dpkg-reconfigure -phigh -a

did not work.

I ran `sudo lightdm -d` and got the following:

```
** (lightdm:3512): DEBUG: Logging to /var/log/lightdm/lightdm.log
** (lightdm:3512): DEBUG: Starting Light Display Manager 1.0.1, UID=0 PID=3512
** (lightdm:3512): DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
** (lightdm:3512): DEBUG: Using D-Bus name org.freedesktop.DisplayManager
** (lightdm:3512): DEBUG: Registered seat module xlocal
** (lightdm:3512): DEBUG: Registered seat module xremote
** (lightdm:3512): DEBUG: Adding default seat
** (lightdm:3512): DEBUG: Starting seat
** (lightdm:3512): DEBUG: Starting new display for greeter
** (lightdm:3512): DEBUG: Starting local X display
** (lightdm:3512): DEBUG: Using VT 7
** (lightdm:3512): DEBUG: Activating VT 7
** (lightdm:3512): DEBUG: Logging to /var/log/lightdm/x-1.log
** (lightdm:3512): DEBUG: Writing X server authority to /var/run/lightdm/root/:1
** (lightdm:3512): DEBUG: Launching X Server
** (lightdm:3512): DEBUG: Launching process 3517: /usr/bin/X :1 -auth /var/run/lightdm/root/:1 -nolisten tcp vt7 -novtswitch
** (lightdm:3512): DEBUG: Waiting for ready signal from X server :1
** (lightdm:3512): DEBUG: Acquired bus name
** (lightdm:3512): DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
** (lightdm:3512): DEBUG: Got signal 10 from process 3517
** (lightdm:3512): DEBUG: Got signal from X server :1
** (lightdm:3512): DEBUG: Connecting to XServer :1
** (lightdm:3512): DEBUG: Starting greeter session
** (lightdm:3512): DEBUG: pam_start("lightdm-autologin", "lightdm") -> (0x1c8aeb0, 0)
** (lightdm:3512): DEBUG: Starting session lightdm-gtk-greeter as user lightdm logging to /var/log/lightdm/x-1-greeter.log
** (lightdm:3512): DEBUG: Failed to load session file /usr/share/xgreeters/lightdm-gtk-greeter.desktop: No such file or directory:
** (lightdm:3512): DEBUG: Failed to start greeter
** (lightdm:3512): DEBUG: Stopping display
** (lightdm:3512): DEBUG: Sending signal 15 to process 3517
** (lightdm:3512): DEBUG: Process 3517 exited with return value 0
** (lightdm:3512): DEBUG: X server stopped
** (lightdm:3512): DEBUG: Removing X server authority /var/run/lightdm/root/:1
** (lightdm:3512): DEBUG: Releasing VT 7
** (lightdm:3512): DEBUG: Display server stopped
** (lightdm:3512): DEBUG: Display stopped
** (lightdm:3512): DEBUG: Stopping X local seat, failed to start a display
** (lightdm:3512): DEBUG: Stopping seat
** (lightdm:3512): DEBUG: Seat stopped
** (lightdm:3512): DEBUG: Stopping lightdm, required seat has stopped
** (lightdm:3512): DEBUG: Stopping display manager
** (lightdm:3512): DEBUG: Display manager stopped
** (lightdm:3512): DEBUG: Stopping Light Display Manager
```

---

### Post by dmp1ce on 2011-10-17
> **andho said:**
> Same thing happens for me.

sudo dpkg-reconfigure -phigh -a

did not work.

I ran `sudo lightdm -d` and got the following:

```
** (lightdm:3512): DEBUG: Logging to /var/log/lightdm/lightdm.log
** (lightdm:3512): DEBUG: Starting Light Display Manager 1.0.1, UID=0 PID=3512
** (lightdm:3512): DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
** (lightdm:3512): DEBUG: Using D-Bus name org.freedesktop.DisplayManager
** (lightdm:3512): DEBUG: Registered seat module xlocal
** (lightdm:3512): DEBUG: Registered seat module xremote
** (lightdm:3512): DEBUG: Adding default seat
** (lightdm:3512): DEBUG: Starting seat
** (lightdm:3512): DEBUG: Starting new display for greeter
** (lightdm:3512): DEBUG: Starting local X display
** (lightdm:3512): DEBUG: Using VT 7
** (lightdm:3512): DEBUG: Activating VT 7
** (lightdm:3512): DEBUG: Logging to /var/log/lightdm/x-1.log
** (lightdm:3512): DEBUG: Writing X server authority to /var/run/lightdm/root/:1
** (lightdm:3512): DEBUG: Launching X Server
** (lightdm:3512): DEBUG: Launching process 3517: /usr/bin/X :1 -auth /var/run/lightdm/root/:1 -nolisten tcp vt7 -novtswitch
** (lightdm:3512): DEBUG: Waiting for ready signal from X server :1
** (lightdm:3512): DEBUG: Acquired bus name
** (lightdm:3512): DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
** (lightdm:3512): DEBUG: Got signal 10 from process 3517
** (lightdm:3512): DEBUG: Got signal from X server :1
** (lightdm:3512): DEBUG: Connecting to XServer :1
** (lightdm:3512): DEBUG: Starting greeter session
** (lightdm:3512): DEBUG: pam_start("lightdm-autologin", "lightdm") -> (0x1c8aeb0, 0)
** (lightdm:3512): DEBUG: Starting session lightdm-gtk-greeter as user lightdm logging to /var/log/lightdm/x-1-greeter.log
** (lightdm:3512): DEBUG: Failed to load session file /usr/share/xgreeters/lightdm-gtk-greeter.desktop: No such file or directory:
** (lightdm:3512): DEBUG: Failed to start greeter
** (lightdm:3512): DEBUG: Stopping display
** (lightdm:3512): DEBUG: Sending signal 15 to process 3517
** (lightdm:3512): DEBUG: Process 3517 exited with return value 0
** (lightdm:3512): DEBUG: X server stopped
** (lightdm:3512): DEBUG: Removing X server authority /var/run/lightdm/root/:1
** (lightdm:3512): DEBUG: Releasing VT 7
** (lightdm:3512): DEBUG: Display server stopped
** (lightdm:3512): DEBUG: Display stopped
** (lightdm:3512): DEBUG: Stopping X local seat, failed to start a display
** (lightdm:3512): DEBUG: Stopping seat
** (lightdm:3512): DEBUG: Seat stopped
** (lightdm:3512): DEBUG: Stopping lightdm, required seat has stopped
** (lightdm:3512): DEBUG: Stopping display manager
** (lightdm:3512): DEBUG: Display manager stopped
** (lightdm:3512): DEBUG: Stopping Light Display Manager
```

I had the exact same problem and the bug has already been reported here: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/816809](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/816809)

The resolution is to install the lightdm-gtk-greeter package:

```
sudo apt-get install lightdm-gtk-greeter
```

---

### Post by atentik on 2011-10-18
Got the same problem and none of the suggested solutions work for me.

---

### Post by Owkkuri on 2011-10-20
Installing the lightdm-gtk-greeter package worked for me.

---

### Post by twostar on 2011-10-22
nothing seemed to work until i got my autologin disabled. It's not pretty, the login is ugly but this is a mythtv box so it doesn't login very often. 

I had to edit my /etc/gdm/gdm.conf-custom file to remove the autologin and i'm using gdm to login from the steps earlier in this thread.

---

### Post by MAFoElffen on 2011-10-22
> **kebabbaro said:**
> Hello, I just installed for the 2nd time Ubuntu 11.10 from a USB stick, the first time choosing the "show login screen" option this time choosing "login automatically" but the result is the same: at restart after installlation is complete the screen freezes at "Checking battery status.." execution. 

Tried to CTRL+ALT+F1, login and sudo restart lightDM but that put me back to the frozen screen with the same reading "Checking battery status.."

The machine is an ASUS M51Sn, and starting from version 9.04 I never had any issue installing Ubuntu before.

Any help please :(
Please back up for a second...

About the same time that tty1 is displaying the "Checking for System 5 Compatibility" message to the "Checking Battery Status" Message, it starts up Xorg and hits the graphics drivers.  Yes, some people are having issues with Lightdm... but most of the time, when it borks at either of these messages, its usually a graphics issue.

Please post the results of
```

lspci -vnn | grep VGA

```And Please post the /var/log/xorg.0.log

EDIT-- 
Fresh intslall right? At boot, hold down the shift key until the boot menu comes up. > Press "e" to put it into an edit mode. > Arrow down to the line that starts with "linux". > Right Arrow after the test "quiet splash" and before "vt.handoff=7". > Insert the test "nomodeset"  (You have a NVidia GeoForce 9500 GS.) > Press <cntrl><x> to boot.

It should boot into your desktop. Once there, click on your user_name at the upper right of screen > System Settings > Additional Drivers > Install your driver (nvidia-current)  

Shutdown/Reboot to test. If that works, never mind about posting the log.

---

### Post by sp4c3313v470r on 2011-10-22
> **MAFoElffen said:**
> Please back up for a second...

About the same time that tty1 is displaying the "Checking for System 5 Compatibility" message to the "Checking Battery Status" Message, it starts up Xorg and hits the graphics drivers.  Yes, some people are having issues with Lightdm... but most of the time, when it borks at either of these messages, its usually a graphics issue.

Please post the results of
```

lspci -vnn | grep VGA

```And Please post the /var/log/xorg.0.log

EDIT-- 
Fresh intslall right? At boot, hold down the shift key until the boot menu comes up. > Press "e" to put it into an edit mode. > Arrow down to the line that starts with "linux". > Right Arrow after the test "quiet splash" and before "vt.handoff=7". > Insert the test "nomodeset"  (You have a NVidia GeoForce 9500 GS.) > Press <cntrl><x> to boot.

It should boot into your desktop. Once there, click on your user_name at the upper right of screen > System Settings > Additional Drivers > Install your driver (nvidia-current)  

Shutdown/Reboot to test. If that works, never mind about posting the log.

adding test nomodeset did not work for me.:( When i type "lspci -vnn  |  grep VGA" I get 02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200M G] (rev a2) (prog-if 00 [VGA controller]) 

how do i do the /var/log/xorg.0.log thing?

---

### Post by MAFoElffen on 2011-10-22
> **sp4c3313v470r said:**
> adding test nomodeset did not work for me.:( When i type "lspci -vnn  |  grep VGA" I get 02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200M G] (rev a2) (prog-if 00 [VGA controller]) 

how do i do the /var/log/xorg.0.log thing?
How are you doing the CLI conmands on this?  On the sys during boot?  (mounted to the system) If so, at CLI
```

sudo apt-get update
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-current
sudo apt-get upgrade
sudo reboot

```If not then...

Are you able to boot a LiveCD?  From a LiveCD > Try without Installing... > Wait > At Desktop select the home icon (2d down) > At nautilus window, look to the left window, top, you will see the other filesystems. Select the filesysetm that you installed to...

Manuveer to /var/log/ > Right click on xorg.0.log > right-click > select open with text editor... > Select all > Copy.  Then open a browser and post it here.

If the LiveCD didn't boot- On boot the 1st screen is black w/ the person/keyboard icon at the bottom > press escape > that boots a lot graphic displayed language selction screen. Press escape. > That will end up at the Advanced Install Menu. > Press <F6>. That will bring up a dropdown boot options menu. > Arrow down to "nomodeset" and press the keyboard to select. > Press escape to exit that menu while saving the selection > Try without Installing.

I''l stop there for now...

---

### Post by sp4c3313v470r on 2011-10-22
Wow thanks!!! updating nvidia worked!!! I have been searching for the past day or so for a solution to this problem. After a ton of commands and tricks, TWO fresh installs no one seemed to have a fix.  This was my first post on this forum. I thank you again. Please direct others to this thread, this seems to be a common problem with a simple solution.

---

### Post by jonshado on 2011-10-24
Yup. The steps to reinstall nvidia drivers worked. Thanks!

---

### Post by azzid on 2011-11-11
Same problem.
Fresh install, never been able to boot into x.
Must use nomodeset to be able to boot at all.
Have tried 'apt-get install lightdm-gtk-greeter'. Does not work.
Does not have nvidia graphics card.

```

$ lspci -vnn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:964a] (prog-if 00 [VGA controller])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64

```

---

### Post by franktokc on 2011-11-12
> **MAFoElffen said:**
> How are you doing the CLI conmands on this?  On the sys during boot?  (mounted to the system) If so, at CLI
```

sudo apt-get update
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-current
sudo apt-get upgrade
sudo reboot

```If not then...

Are you able to boot a LiveCD?  From a LiveCD > Try without Installing... > Wait > At Desktop select the home icon (2d down) > At nautilus window, look to the left window, top, you will see the other filesystems. Select the filesysetm that you installed to...

Manuveer to /var/log/ > Right click on xorg.0.log > right-click > select open with text editor... > Select all > Copy.  Then open a browser and post it here.

If the LiveCD didn't boot- On boot the 1st screen is black w/ the person/keyboard icon at the bottom > press escape > that boots a lot graphic displayed language selction screen. Press escape. > That will end up at the Advanced Install Menu. > Press <F6>. That will bring up a dropdown boot options menu. > Arrow down to "nomodeset" and press the keyboard to select. > Press escape to exit that menu while saving the selection > Try without Installing.

I''l stop there for now...
The above code (sudo...) worked for me. You deserve a medal!:KS

---

### Post by Dubbayoo on 2011-11-17
I am having the same issue now, although I have a Radeon 6870 card. I am able to switch consoles and start lightdm manually just fine. Can this battery check be disabled? I don't have a laptop.

---

### Post by azzid on 2011-11-18
> **Dubbayoo said:**
> I am having the same issue now, although I have a Radeon 6870 card. I am able to switch consoles and start lightdm manually just fine. Can this battery check be disabled? I don't have a laptop.

The battery check is fine, it is what happens after that is the problem.

---

### Post by Dubbayoo on 2011-11-22
So what is the fix for people that don't have nividia cards? The lightdm-gtk-greeter was not it.

I can easily switch to a different screen and start lightdm successfully but obviously that isn't a long term solution. can I add a line to a startup script that does "start lightdm"? even though it's already in existence somewhere.

---

### Post by Tamale on 2012-02-06
I have the same problem, dell M6600 AMD firepro M8900.

Restarting / starting lightdm doesn't help me, neither does re-installing the graphics drivers.

I'm really frustrated that ubuntu has gotten consistently LESS reliable than it was when I first started using it regularly 6 years ago.

---

### Post by tradeJmark on 2012-02-16
after you get lightdm running, go into system preferences and disable autologin.

---

