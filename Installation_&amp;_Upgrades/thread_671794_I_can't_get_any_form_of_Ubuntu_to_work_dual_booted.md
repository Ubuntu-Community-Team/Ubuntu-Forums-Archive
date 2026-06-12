---
title: "I can't get any form of Ubuntu to work dual booted"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Sergeantfour on 2008-01-18
I started with Wubi because it looked so easy...didn't get past the install phase.  I received the popular "x server graphical interface failure" message.  Looked that up and while everything posted said to switch things to vesa so it would work - it didn't.

So I tried the Live CD itself.  I get to the screen where you can choose what to boot, and messed around with the F6 boot option portion after trying to start Ubuntu and having my monitor go to sleep as I glare at it (nothing worked, but that's because I know zilch about what I'm doing).

I'm running a AMD 6400+ dual core, 8GB RAM, 2x8500 gt, 500gb WD HDD, Vista Ultimate 64, and I don't know what to do.  I've been trolling forums looking for solutions to try, have actually done some, and am in the exact same place where I started.  I want Ubuntu but I might have to give up.

Please make any suggestions as if you were talking to an idiotic 3 year old that isn't sure what the difference between a monitor and a sandbox is, and thanks in advance for trying.

---

### Post by jleaker01z on 2008-01-18
Geez dude...with a system like that have you considered just using a virtual machine?

Thats some SERIOUS hardware ;)

---

### Post by Sergeantfour on 2008-01-18
See, you just made the mistake of assuming I know what a virtual machine is.  I'm a dummy.

I'm actually in a little over my head, I have one of those gadgets that tells me how much memory vista is hogging and I haven't seen the thing pop over 35% yet.  And I constantly run into issues where I don't know if I should treat programs like 32 or 64 bit food.  That could very well be contributing to my current issue.

---

### Post by smartboyathome on 2008-01-18
I don't know a lot about graphic cards, but maybe X is getting confused because you have 2 of them?

---

### Post by jleaker01z on 2008-01-18
Ah ok...well do you want Vista as your 'main' OS or Ubuntu?

A virtual machine is something created by a program such as VirtualBox or VMWare that allows you to install another OS within another OS.  In effect, your 2nd OS will run within a window on your desktop.

---

### Post by Craigus on 2008-01-18
> after trying to start Ubuntu and having my monitor go to sleep as I glare at it

May we have a more detailed description of what happens ?

---

### Post by Sergeantfour on 2008-01-18
I feel safer with Vista, but want to learn to use Ubuntu and maybe switch later.  Is that possible?

---

### Post by smartboyathome on 2008-01-18
> **jleaker01z said:**
> Ah ok...well do you want Vista as your 'main' OS or Ubuntu?

A virtual machine is something created by a program such as VirtualBox or VMWare that allows you to install another OS within another OS.  In effect, your 2nd OS will run within a window on your desktop.

The disadvandage of a virtual machine is that you don't get all the effects and don't get to play 3D games.

---

### Post by smartboyathome on 2008-01-18
> **Sergeantfour said:**
> I feel safer with Vista, but want to learn to use Ubuntu and maybe switch later.  Is that possible?

It is definately possible through dual-booting (where you have more than one OS on your drive).

---

### Post by jleaker01z on 2008-01-18
> **Sergeantfour said:**
> I feel safer with Vista, but want to learn to use Ubuntu and maybe switch later.  Is that possible?

Sounds like a virtual machine is right up your alley then.  It does have a few restrictions to it, as noted above, but to 'try out' Ubuntu it would probably be easier and also make it less likely you will mess up your Windows installation.  Check out VirtualBox.  They have a Windows version, although I dont know if its Vista compatible.

All you would need to do, would be to install VirtualBox (or another Vista compatible virtual machine manager).  Follow the directions for creating your virtual machine, insert the Ubuntu CD into the drive, then click the button that starts the Virtual Machine.  (Start in VirtualBox, Power On in VMWare).  The virtual machine will then 'boot up' and should find your bootable Ubuntu CD and you will be off and running.

---

### Post by Sergeantfour on 2008-01-18
> **Craigus said:**
> May we have a more detailed description of what happens ?

I click the "Start or Install Ubuntu" off of the live screen, see the Ubuntu orange horizontal line scroll across the screen, and then my monitor goes to sleep.  When I changed the F6 code at end to "noapic nolapic pci=noapci apci=off" the monitor stayed on, but the screen just stayed black.

---

### Post by jleaker01z on 2008-01-18
Thats one advantage of a virtual machine.  Your host OS (Vista) would handle graphics drivers and such and may eliminate that problem.  

Or you can download the 'alternate' cd which uses a text based installer, if you want a dual boot.

---

### Post by Sergeantfour on 2008-01-18
I downloaded and set up the virtual machine, Ubuntu is downloading, and the situational update will be coming in....about 15 minutes.

---

### Post by jleaker01z on 2008-01-18
Check your virtual machine manager...you may be able to point it directly to the ISO file and not have to burn it to a CD.  How to do this should be documented, although it was fairly straightforward in VirtualBox .

---

### Post by smartboyathome on 2008-01-18
> **Sergeantfour said:**
> I click the "Start or Install Ubuntu" off of the live screen, see the Ubuntu orange horizontal line scroll across the screen, and then my monitor goes to sleep.  When I changed the F6 code at end to "noapic nolapic pci=noapci apci=off" the monitor stayed on, but the screen just stayed black.

Sounds like ubuntu doesn't like your dual graphics drivers (as stated above). I don't think that it will like it.

---

### Post by Sergeantfour on 2008-01-19
I now have it running on Virtualbox, but it doesn't look like I'll be able to tweak the graphical interfaces.  And I really would like to dual-boot eventually and am worried about the alternate installation mostly with regards to the text-based partitioning.

---

### Post by Sergeantfour on 2008-01-19
I have ubuntu installed in VirtualBox and thought I had the alternate cd installed correctly, but it rebooted after the installation (on my real box, not the virtual one) the monitor turned off again.  There HAS to be some way to get around this!

---

### Post by Craigus on 2008-01-20
Well, there is this issue:

[http://ubuntuforums.org/showthread.php?t=588671]("http://ubuntuforums.org/showthread.php?t=588671")

Having said that, I have seen a couple of posters mention that they were using two nvidia cards in SLI with Gutsy, so I am a bit confuzzled about this.

---

### Post by Sergeantfour on 2008-01-21
Thanks for the link!  I hope that it eventually gets fixed?  Is that my only option?

---

