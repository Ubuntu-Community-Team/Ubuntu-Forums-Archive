---
title: "Installation Nightmare"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by Lange on 2011-08-16
I'm stuck in an unusual position, and if anyone had ever answered some of these questions once asked on these forums before (as I found, alone, unanswered), I may not be stuck.
 
Here's my situation.
My HP Netbook crashed. The Windows XP system files corrupted and Windows absolutely will not run. I planned on using Ubuntu to recover it, and then install Ubuntu permanently to save it in the future. Before you ask, every other utility has failed on me. UBCD included, which did nothing but provide me with errors upon errors just trying to run it.
 
The netbook has no CD drive.
The only internet around is a wireless signal... my netbook has a broadcom wireless card that is never recognized. I'm using someone elses working laptop to connect online and get things I need, make boot devices, research for help, etc.
This laptop has barely any hard drive space. Currently it has 1 gb remaining for doing anything.
I have three flash memory devices:
2 gb SD card. My netbook refuses to recognize it as a boot device.
2 gb flash stick (that's actually an mp3 player). My netbook refuses to recognize it as a boot device.
512 mb flash stick. This DOES work as a boot device.
 
So far my 512 mb flash stick has run Damn Small Linux and Ubuntu Minimal on my netbook. Of course, both are useless because the netbook cannot access internet, nor does either OS recognize my wireless card. This flash stick is, obviously, too small for a regular Ubuntu installation or any other Linux distribution that can help (as far as I know).
 
So, in order for this to work, I have to be able to do one of the following:
 
Install Ubuntu from a different OS, like Damn Small Linux or something small enough to boot on my 512 mb stick. Ubuntu can be put on one of the other, larger devices, maybe to be accessed for installation. No idea how to do this, let alone safely.
 
Install Ubuntu Minimal OFFLINE. This question was asked multiple times on these forums and none were answered. Is there a way to run minimal, and use offline sources for the install?
 
Get the normal Ubuntu installer under 500 mb. Its overwhelmingly frustrating that I'm just barely unable to do this. I've read of Ubuntu Customization Kit, which ended up being lots of useless files and reams of gobbldegook. I've heard Ubuntu is packed with additional, nonrequisite software which makes it so large. Why can't there be a halfway version between normal and minimal?? Not everyone has internet and not everyone has a CD drive or large USB stick! Is there a way this can be accomplished? Does this version exist?
 
I have limited time and resources. Before you ask, no, I cannot afford a larger USB stick. I'm pinching pennies right now and there's nowhere near here that sells them anyway.
 
Can someone help me solve this nightmare?

---

### Post by smurphy_it on 2011-08-16
Welcome to the forums.  Before delving too deep into things here, some more information needs to be gathered first.

) You are going to have to provide some more information on your hardware.  What is the model of the HP Laptop.  What wireless card is it ?  Was the wireless card already in the netbook, or did you insert one (usb or pcmcia), and if so, we'll need info on that external wifi device.
2) I believe there is a "minimal netbook version of ubuntu".  I think they call it ubuntu one.

Typically, people use the "internet" with their devices.  Kind of stuck not being able to do things without it (or should I say, kind of limiting).

3) You can download some .iso's of LIVE CDs of linux, and then use netbootin to put them on your USB Flash drives.

4) Using the other machine, you should be able to download the "firmware" for your wireless card.  Then install it, and if all goes well, your internet will work.

---

### Post by Lange on 2011-08-16
> **smurphy_it said:**
> Welcome to the forums. Before delving too deep into things here, some more information needs to be gathered first.
 
) You are going to have to provide some more information on your hardware. What is the model of the HP Laptop. What wireless card is it ? Was the wireless card already in the netbook, or did you insert one (usb or pcmcia), and if so, we'll need info on that external wifi device.
2) I believe there is a "minimal netbook version of ubuntu". I think they call it ubuntu one.
 
Typically, people use the "internet" with their devices. Kind of stuck not being able to do things without it (or should I say, kind of limiting).
 
3) You can download some .iso's of LIVE CDs of linux, and then use netbootin to put them on your USB Flash drives.
 
4) Using the other machine, you should be able to download the "firmware" for your wireless card. Then install it, and if all goes well, your internet will work.
 
Thank you for a comprehensive response. I'll respond to each number.
 
1) The netbook is, specifically, an HP Mini 1101 FM906UT, using an Intel Atom N270 processor. I have no idea what the wireless card is specifically, its not specified anywhere. Just labelled Broadcom. And it came installed, its not an external device.
 
2) I've never come across Ubuntu One or heard of it. I'll go find that in a minute. Edit, I just did, and its not at all like that. Its some weird online services version that I don't believe relates to this in any way. Just because new technology is coming out crazy fast these days and every middle class American has a smart phone, does not mean everyone has reliable internet. Why such crucial software is now becoming entirely internet dependent with no alternatives is mind numbingly stupid.
 
3) Uh, ok, and what good would that do?
 
4) I haven't the faintest idea how to do this, for what, in what order, what OS, you kind of left that part dry.
 
Again thank you for a healthy reply. This is going somewhere now.

---

### Post by PapaGary on 2011-08-16
> **Lange said:**
> Why such crucial software is now becoming entirely internet dependent with no alternatives is mind numbingly stupid.
How else do you think it should be done?

By mail?

---

### Post by Lange on 2011-08-16
> **PapaGary said:**
> How else do you think it should be done?
 
By mail?
 
For example, a package that can be run on computers that don't have internet. In this case, Ubuntu Minimal accessing the data from, say, a separate storage device, instead of solely relying on an internet connection.
Nothing pisses me off more than going across town for internet, getting a software installer for use on my offline computer, only to return home and, after running it, discover its a web installer.

---

### Post by smurphy_it on 2011-08-16
```
1) The netbook is, specifically, an HP Mini 1101 FM906UT
```

That should hopefully give us enough information to figure out what kind of wifi device you have.  If not, then you might have to run linux (dsl) from your 512MB flash drive, and then in a terminal type out some commands, and post the output here.  Example:  
```
lspci | grep [Nn]etwork
```


```
3) You can download some .iso's of LIVE CDs of linux, and then use netbootin to put them on your USB Flash drives.
```
```
3) Uh, ok, and what good would that do?
```

You can download a LIVE CD of Ubuntu, Damn Small Linux, and a bunch of other linux live Distro's.  Using unetbootin you can then put that "linux live environment" to run off your 512MB flash drive.  That way you can get into linux and copy your "data" from the crashed XP partition over to your external storage.  If i'm reading this right, you only have a max of 4GB via 2 USB flash drives, so hopefully you don't have over 4GB of data to transfer.

```
I'm using someone elses working laptop to connect online and get things I need, make boot devices, research for help, etc.
```

This is what I was referring to for #4.  Using this laptop with a working internet connection to download the firmware for your wifi device.  Shouldn't matter what O/S is on it.  Once the firmware has been identified which you need, you can download it from the web on that laptop, and copy it to one of your 2 GB flash drives.

---

### Post by smurphy_it on 2011-08-16
Sorry bad info on my part, it's not Ubuntu one.  It's Ubuntu Netbook remix.  Various versions available since Ubuntu 8.04.

According to a wiki page, it is no longer a seperate item starting with Ubuntu 10.10.

Beginning with version 10.10, Ubuntu Netbook Edition used the Unity desktop as its desktop interface. The classic netbook interface was available in Ubuntu's software repositories as an option.
Because Ubuntu's desktop edition has moved to the same Unity interface as the netbook edition, starting with Ubuntu 11.04, the netbook edition has been merged into the desktop edition.[1]

---

### Post by Lange on 2011-08-16
That helps somewhat. Damn Small Linux cannot reach my Windows Partition, or my C drive at all.
Furthermore the actual personal data I have is over 60 gb so that's not feasible lol. I need to repair Windows, which I know how to do, if Ubuntu would just work.
 
Also, say I get the firmware. What am I supposed to do with it once I have it?
 
I have to leave for a while. I might have this solved later, if someone is able to lend me a larger usb stick. Thanks for the support so far. I'll check back here when I can.

---

### Post by smurphy_it on 2011-08-16
Well if you have 60GB of data, you're going to need something large enough to put your data on (even if it's just temporary).

with Damn-Small Linux running, I'm surprised you couldn't get it to mount your local hard drive.  In the cli (Command-Line Interface) aka terminal, you should be able to mount the drive.  However, if you don't have any means of transferring the files elsewhere it's a moot point.  You could run the "lspci | grep [Nn]etwork" command while you are in there and post the info here to aide in determining the type of wifi device, and more importantly, which firmware to get.

If you had ubuntu running as a live environment (for example), and you previously downloaded the firmware as a .deb file, you could install it with ```
sudo dpkg -i firmware-downloaded-file.deb
```

Then after doing a "sudo modprobe firmware-name" you could get the wireless device working.


If you have access to another computer (network wise with 60+GB free) then once your wireless device is functional, you could backup the files to that network location.  IMO an external USB hard drive would probably be the way to go.

---

### Post by spcwingo on 2011-08-16
For data recovery you could also try Puppy.  If I'm not mistaken, it includes Broadcom firmware by default.  It is also loosely based on Ubuntu (Puppy 5 onwards).  Here is a link to the Puppy site:

[http://puppylinux.org]("http://puppylinux.org")

---

