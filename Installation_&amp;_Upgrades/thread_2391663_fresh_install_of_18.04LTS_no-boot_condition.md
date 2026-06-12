---
title: "fresh install of 18.04LTS no-boot condition"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by egiles on 2018-05-11
Hello there, quick summary of my issue. I've been messing around with a living room media computer using ubuntu the past month or so and I originally had ubuntu 17 installed (no windows) and it was running fine. When 18 came out i did a fresh install from usb (same as 17, did not install alongside or upgrade. fresh install) and i cannot get it to boot to desktop environment on its own. it freezes during the ubuntu logo/loading screen right after the mouse appears. If i let it sit the montior eventually loses its input. I suspect the issue lies somewhere in the graphics side of things but i just can't figure it out. I can boot to desktop environment no problem if i go through rescue mode (shift at startup, from HDD). Does anyone have any ideas? I'm an advanced user (electrical enginner) but I'm fairly new to Linux in general so please tell me the info you need and how to get it to streamline this process. I've already tried repairing grub and ive even gone as far as putting in a win7 disc and repairing to get rid of grub altogether and fresh installing 18 again to no avail. Let me know what you need.

Edit: I haven't tried "killing" the HDD for a 100% fresh install but as i said before, I strongly believe my issue is graphical. Could the fact that when booting desktop from rescue mode I can't even get my display's natural resolution be a hint? I've also tried 2 different monitors as well. I believe its an internal hardware issue.

Edit2: I also haven't tried fresh installing 17 and upgrading from there. I kinda wanted to just go the fresh-install route (it really makes me feel better ;) ) so any suggestions on that are appreciated too

Edit3: system specs export from hardinfo: [https://files.fm/u/bk9tdvwe](https://files.fm/u/bk9tdvwe)

---

### Post by yancek on 2018-05-11
I believe the rescue mode has the nomodeset parameter on the kernel line in grub.  Try settings or software and updates and look for an option for additional drivers to install.l

---

### Post by egiles on 2018-05-11
> **yancek said:**
> I believe the rescue mode has the nomodeset  parameter on the kernel line in grub.  Try settings or software and  updates and look for an option for additional drivers to  install.l

I should have mentioned that I've already  checked for updates. And just to make sure we're on the same page, I'm  on desktop by "continuing with boot" from rescue mode. and yes I've also tried the repair options there. I did update OP with system specs if  you wanna check that out tho

---

### Post by dino99 on 2018-05-12
Open a tty console (ctrl+alt+F?), run 'journalctl -b > journal.txt' and post that output please.

---

### Post by garvinrick4 on 2018-05-12
Try this: Might work if need nomodeset at boot. If doesn't work just remove nomodeset and save and do update-grub.
Post if doesnt work and will tell you how to get card and driver in use to post. Lots of graphic cards and driver members to give you answers.
If you would rather just post the card and drivers and get help please do that. Just giving you a shot at booting properly. If you need nomodeset
this will change config file to set it everytime you boot. 
#open text editor to edit etc/default/grub 
 >  	 		 			 			 				sudo gedit /etc/default/grub 			 		

 	
 

#add "nomodeset" to line GRUB_CMDLINE_LINUX

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
_GRUB_CMDLINE_LINUX="nomodeset"_
#hit save button in upper right hand corner of text editor.
#in terminal run this command to save in grub config must run update-grub anytime want to save new config
 >  	 		 			 			 				sudo update-grub 			 		

 	
 


---

### Post by garvinrick4 on 2018-05-12
#use this in terminal to get Graphics card and driver to copy and paste in a post if previous post does not work for you.
> lspci -vnn | grep VGA -A 12

---

### Post by egiles on 2018-05-12
> **dino99 said:**
> Open a tty console (ctrl+alt+F?), run 'journalctl -b > journal.txt' and post that output please.

[https://files.fm/u/98w24y8s](https://files.fm/u/98w24y8s)

edit: quick fyi too guys tty changed in 17, terminal starts at f3. f1 is login screen and f2 is your desktop environment
> **garvinrick4 said:**
> Try this: Might work if need nomodeset at boot. If doesn't work just remove nomodeset and save and do update-grub.
Post if doesnt work and will tell you how to get card and driver in use to post. Lots of graphic cards and driver members to give you answers.
If you would rather just post the card and drivers and get help please do that. Just giving you a shot at booting properly. If you need nomodeset
this will change config file to set it everytime you boot. 
#open text editor to edit etc/default/grub 
 
#add "nomodeset" to line GRUB_CMDLINE_LINUX

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
_GRUB_CMDLINE_LINUX="nomodeset"_
#hit save button in upper right hand corner of text editor.
#in terminal run this command to save in grub config must run update-grub anytime want to save new config

> **garvinrick4 said:**
> #use this in terminal to get Graphics card and driver to copy and paste if previous post does not work for you.

I will try this after I eat, thank you

---

### Post by egiles on 2018-05-12
> **garvinrick4 said:**
> Try this: Might work if need nomodeset at boot. If doesn't work just remove nomodeset and save and do update-grub.
Post if doesnt work and will tell you how to get card and driver in use to post. Lots of graphic cards and driver members to give you answers.
If you would rather just post the card and drivers and get help please do that. Just giving you a shot at booting properly. If you need nomodeset
this will change config file to set it everytime you boot. 
#open text editor to edit etc/default/grub 
 
#add "nomodeset" to line GRUB_CMDLINE_LINUX

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
_GRUB_CMDLINE_LINUX="nomodeset"_
#hit save button in upper right hand corner of text editor.
#in terminal run this command to save in grub config must run update-grub anytime want to save new config

This did work, however can you explain what that nomodeset is doing exactly? is that kind of a bandaid fix? Should I do the driver thing anyway? I'm still not able to display to the screen's natural resolution (1366x768)

Edit: I googled the first question ;) however, the second two remain asked

---

### Post by egiles on 2018-05-12
> **garvinrick4 said:**
> #use this in terminal to get Graphics card and driver to copy and paste in a post if previous post does not work for you.

Card:

[QUOTE=egilesgfxcard]00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company 82G33/G31 Express Integrated Graphics Controller [103c:2a78]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at f400 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fd800000 (32-bit, non-prefetchable) [size=1M]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: i915

00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: Hewlett-Packard Company NM10/ICH7 Family High Definition Audio Controller [103c:2a78][/QUOTE]

---

### Post by garvinrick4 on 2018-05-12
Nomodeset stops the driver from loading from kernal and you do lose the video cards resolution .
It does use the same driver i use so I will check it out and be back to you. Hopefully
there will be a fix and most likely seems like a common card and driver set nothing proprietary.

---

### Post by garvinrick4 on 2018-05-12
Have not found a fix for your intel card and i915 driver will look more will do my best to find fix.
Hopefully someone who knows the fix will post in this thread. Be a bit patient and use the nomodeset 
for time being.

---

