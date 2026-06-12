---
title: "Live CD freezes ... HP pavilion dv9000"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by kellere on 2006-10-08
Community,

  I wish this post was not so vague but I am
truly beside myself.  The latest 64bit dapper CD will
not load.  It get stuck in various places.
The farthest I can get is "intialing Enterprise
volume manager...".  

  The laptop I am using is rather new.
HP pavilion dv9000 with AMD 64x2 1.6 GHz chip.
Initially the cd often crapped out when probing
the pci but I found on the web that boot parameter:

pci=nommconf 

helps and it does.

Does the live cd dump a log that I can look at?

Any help would be great.
Thanks in advance.

-John

---

### Post by Agapo on 2006-10-12
There is some discussion going on here:
[http://ubuntuforums.org/showthread.php?t=235269&highlight=dv9000z](http://ubuntuforums.org/showthread.php?t=235269&highlight=dv9000z)

---

### Post by phefferan on 2006-10-14
I also have the HP dv9000z. I have tried both the 32bit and 64bit versions of Dapper 6.06. It seems to hang at the kernel loading. I have tried loading different parameters at boot without success. It does seem to hang consistently where it should be loading the kernel. I know the media is good because I have it loaded on a Latitude C840 with no errors.

Anyone have any ideas? I am a newbie but have used Linux a fair amount in the past five years.

---

### Post by phefferan on 2006-10-14
Okay, I did get it to load to the GUI. When I booted I selected the F6 key and put noapic between splash and -- <splash noapic-->. Now I'm looking into why the sound doesn't load consistently. Sometimes it works, but mostly not.

---

### Post by kellere on 2006-10-17
On my way...

  After taking the advice found in a parallel thread,
I added "noapic" and "nolapic" options to boot line 
and the live cd started.  I installed the ubuntu 
system and things seem 'fairly' normal.  Ethernet works
but as expected ubuntu can not see the wireless card.
Hopefully ndiswrapper will work for the wireless ethernet
as it did with my previous machine.

The display is low res but hopefully I can get a 
good xorg config file off of the web.

 -John

---

### Post by kellere on 2006-10-30
Xorg problem resolved,

Using the default vesa driver only offered 1024x800 resolution
which is criminal for such a nice display.  The standard
nvidia display drivers downloaded from nvidia did not work well.
The display was filled with lines.

The nvidia beta driver did work very well though.

driver:  NVIDIA-Linux-x86_64-1.0-9625-pkg2.run  from nvidia.com


How I got my display to work properly:

got to virtual terminal (ctrl -alt- f1)

killall gdm

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

sh NVIDIA-Linux-x86_64-1.0-9625-pkg2.run

add "1400x900" to xorg.conf mode lines.

gdm

-- Getting closer to a good system... the touch pad is 
still crazy sensitive and not very adjustable.

-John

---

### Post by elizleisndahizle on 2006-11-01
I have heard about the video problem from multiple people but not once have i had it on my dv9000z.  What video card do you have, mine is the 7600 maybe you've got a different one,

---

### Post by kellere on 2006-11-04
elizleisndahizle....

  lspci does not pic up the exact model of my
card but I remember getting the lower end 
model which was in the 6000's not the 7000's.

-J

---

### Post by joshw on 2006-12-07
> **kellere said:**
> pci=nommconf 

You're my new hero. I have a DV9008NR that was freezing as well. Adding acpi=off helped, but it killed the wireless and sound. This was the magic bullet that made everything work. Thanks for passing it along!

---

### Post by icuponq on 2007-05-19
I have the dv9000z customized from hp.com.
When I try to load the Live CD it freezes either after the when I try to startup Ubuntu in which case I get a black screen or during the startup where it just stays on a spot loading.  Any help would be nice.  Also I'm a complete newbie hence why I'm using the Live CD so please be as descriptive as possible.

---

### Post by johntuck on 2007-05-20
Ok this is my first post on this forum so be easy on me. I have tried to install Ubunto7 on my HP DV9005 Laptop and have the same problem with it. 
Here is what I have tried so far and what has happened
1) Live CD gives me a black screen - then freezes
2) I have tried the alternate install CD with which I can install Ubunto but when it comes to the boot loader I get the choice between Vista and Ubunto it won't boot into Ubunto - again black screen
3) I have tried to install Ubunto 6 and 7 live CD's on a black harddrive using this Laptop and get the same results - so I at least know it is not a Vista issue
4) I have tried a Knoppix live CD and got it to work with no problems whatsoever

Lastly I don't know what to do anymore and this forum is my last hope. I have Ubuntu running on my other laptop and it works perfect. I don't want to use another distro simple because I like Ubuntu, know it a little bit, and Vista is driving me crazy after just ONE Month of using it.

Please help since I am at the end of my rope.](*,)

---

### Post by d1337 on 2007-05-21
johntuck

Don't give up...I just picked up a HP Pavilion dv9320us Notebook today.  I _will_ make it work and will share what I find with you.

d1337
you have been warned

---

### Post by d1337 on 2007-05-22
Again...directed at johntuck

edit: cleaned up

Your mileage will likely vary as I have Ubuntu searched and googled plenty of info in regards to the hp DV9xxx series laptops.  Mine, in particular, is a DV9320us.  Just picked it up today and really thought "No worries...I'll have Ubuntu on it by the morning".  Well...it's only 11:00P, so I may make it right tonight.

I ran a Live CD on an intel based model before I bought mine.  It came up quick and grabbed the correct screen res (1440 X 900) without issue.  I am an AMD fan and figured it couldn't be much of a challenge.  An lspci of both machines reveal that there is alot of generic Intel hardware (duh!) on the Intel based machine and _alot_ of nVidia hardware in the AMD machine.

Using a Live Cd, I ran into the black screen issues that seem to be common place.  I found that hitting F6 for other options and throwing the following params at the boot helped
```
acpi=off noapic
```
this helped, but I also found that I needed to also add
```
pnpbios=off pci=nommconf
```
i would suggest trying any and/or all of these parameters until you can get it to boot.

I was able to boot, but had sound loop issues.  The only resolve to the sound loop was to move the mouse around...go figure.  The machine proceeded and let me do the install.  Once installed (and rebooted), I loaded the restricted nVidia drivers (said to get past the black screen issue).  Some more searching revealed that
```
noapic
```
was the only boot parameter that other folks needed.  I used vim to edit my /boot/grub/menu.lst to toast the other parameters and just left the noapic at the end.  Booted up and all seems well...good screen res with good fps (from glxgears).  All that seems to be left is my wireless...but that's another thread.

hope that helps somebody... 

d1337
you have been warned

---

### Post by johntuck on 2007-06-01
thanks for your help, however remember that I am blatant beginner so you need to give it to me a little easier and in a few more steps. I know I sound dumb but once I figure things out I can do them again with no probs. Also what install CD should I use the the live or alternate cd and what version the 64 bit or 32 bit - I am more of an Intel person. Thanks in advance for your help

---

