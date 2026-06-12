---
title: "Just uprgrade from 7.10 and have a few problems"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by linkunderscore on 2008-06-13
The first problem is pretty important. My USB wireless adapter isn't working properly under Hardy. 

It worked fine under 7.10 (i actually downloaded all of the updates for hardy with it), but in 8.04 it does not work. Its a Belkin Wireless G USB Network Adapter. I can probably find the exact model if that would be more helpful--i still have the box for it... thoguh i can't seem to find a model number anywhere on it. 

When it restarted after upgrading the reboot hung up because of the adapter--when i unplugged it, it booted up fine. Once it was booted I could plug it in and it would pick it up and actually connect to my wireless network. It would connect, but I couldn't connect to any sites. I connected to the router (192.168.1.1) once and it actually let me connect to google ONCE then it sorta stopped working. Stays connected but without net connection. 

I tried everything I could think of to no avail (manual config/unplugging the router/unplug the usb adapter/rebooted(which actually booted fine the next couple of times even with the adapter still pluged in). What else can I try? 

My other issue involves my movies. All of my movies have F'd up color. It looks like I am watching the movies with inverted colors (ie people look blue 0. It does this with .avi, mp4, mpeg, and wmv. I have a 8800GT vid card if that makes a difference.

---

### Post by linkunderscore on 2008-06-13
Got my wireless problem solved:

> **james_vanb said:**
> I have Belkin F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin F5D7050, v. 3000 with rt73 driver. Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

^^ that works 


Now...lets figure out my movie issue.

---

