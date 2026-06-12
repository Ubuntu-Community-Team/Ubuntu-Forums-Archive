---
title: "Ubuntu 10.04 (64bits) boots sometimes but most often it doesn't"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by LuchenB on 2010-09-23
Hi there! First timer on these forums and looking for some help. After searching the web and these forums i couldn't find something that ressembles my problem so hope i can find a solution here!

**Short Version**

The problem i have is that after sucessfully installing Ubuntu 10.04 (64bits) when i start my PC and i get to grub2 and select Ubuntu it will get stuck at a blank screen with only an "_" flickering on the top of the screen. 
At first i thought "Hey, maybe it just takes a while to boot" but after letting it sit there for about 20 minutes and nothing happening i decided to restart my PC. And then the same thing happened like 5 times. BUT on the 6th try it booted sucessfully! And everything was working perfectly but as soon as i restarted my PC i would encounter the same problem.

**Details**

I should probably mention that i had the exact same problen on the install process. I tried with a CD i had burned the image on and it would show me install options (Try and install, install, etc.) But when i selected either one of those i would get the "_" flickering and nothing ever happening. Then i tried it with a DVD thinking that the CD was the issue. Same thing.
After that i tried with a USB drive and i would get the same exact problem, but on the retry on the USB drive the planets aligned in such a way that i actually got the Virtual Ubuntu loaded from my USB drive. 

So it installed sucessfully and when i restarted it i got to GRUB and selected Linux and the "_" would start showing and nothing ever happens. On the <random number> of restarts it actually launched and it picked up my audio, video cards, other NTFS drives, etc.
But when i restarted i would get the problem again.

I even went trough the whole install process AGAIN (getting it to read from the USB flash drive, starting on Ubuntu) and still no consistent results. Though on the second install it didn't pick up my audio hardware nor my other NTFS drives until the second restart where i was able to use Ubuntu normally. I even upgraded what it told me to upgrade. (now i have two "different" versions of ubuntu on grub, each with it's own safe mode only different by a .24 and a .25 on their names) and right after upgrading and restarting it booted immediately. But after that i'm getting the same issue over and over again.


**SPECS**

[LIST]
[*]AMD Phenom II x4 940 3.00 GHz Processor
[*]4GB RAM
[*]GeForce GTX 275 1GB Video Card
[*]FoxConn Destroyer MotherBoard
[*]Windows 7 Professional (64bits) as second OS
[/LIST]

I don't know if this of any importance but also on grub when i press "E" to edit on the Ubuntu partition before the usual "Set root='(hd0,3)' it says
"record fail
insmod ext2"

Any help with this issue will be greatly appreciated.

---

### Post by lechien73 on 2010-09-23
Welcome to the forums, first of all!

I had read somewhere that you could work around this by adding a rootdelay.

You could try the following:

[LIST]
[*]In the Grub menu, press **E** to edit the Linux entry.
[*]Find the line which ends with the words **quiet splash**
[*]At the end of this line, add a space and type: **rootdelay=60**
[*]Press Ctrl-X to reboot.
[/LIST]

When you reboot the machine, give it a few minutes if it appears to freeze. The parameter we have supplied introduces a delay into the process.

If that works ok for you, then let me know and we can make it permanent. The "record fail" and "insmod ext2" lines are perfectly normal and nothing to worry about.

Sorry that's all I have to offer - I'm sure others will also be able to chip in :)

---

### Post by efflandt on 2010-09-23
Or while editing the linux boot parameters in grub, you might try deleting the words **quiet splash**, so you can see boot messages, which might reveal where it hangs.

Are you using default video drivers, did you activate the nvidia proprietary drivers in Hardware Drivers, or did you install nvidia drivers some other way?  I had no problems with geforce GT220 using either the default nouveau driver, or nvidia driver activated using Hardware Drivers?

---

### Post by LuchenB on 2010-09-23
First of all, thanks for the help. I'm gonna try both methods suggested above right now.

> **efflandt said:**
> 
Are you using default video drivers, did you activate the nvidia proprietary drivers in Hardware Drivers, or did you install nvidia drivers some other way?  I had no problems with geforce GT220 using either the default nouveau driver, or nvidia driver activated using Hardware Drivers?

I activated the nvidia proprietary drivers on the first sucessful boot. But i was having issues before and after doing so so i'm not sure it related.

---

### Post by LuchenB on 2010-09-23
Ok, so i think i've figures out what the issue is. These are the screens that i normally go trough everytime i want to start on Ubuntu.




Screen 1:
[IMG]http://i682.photobucket.com/albums/vv184/Luchen_/P1030166.jpg?t=1285274515[/IMG]

Screen 2:
[IMG]http://i682.photobucket.com/albums/vv184/Luchen_/P1030167.jpg?t=1285274520[/IMG]


Screen 3:
[IMG]http://i682.photobucket.com/albums/vv184/Luchen_/P1030165.jpg?t=1285274507[/IMG]


Now as you can see everything is pretty normal until you get to screen #3. And i think it's because for some reason processor 3 doesn't respond and it fails to boot.
When i get Ubuntu to sucessfully boot i couldn't even get to see the messages on deatil because they passed so fast, but when it doesn't boot it just gets stuck on screen 3.

(Posting from UBUNTU :D)

---

### Post by LuchenB on 2010-09-23
A quick update. I just sucessfully booted into Ubuntu again and what happened there was that neither processor 1 or 2 were responding but when it got to processor 3 it started regulary.

---

### Post by lechien73 on 2010-09-24
That gives a bit more info - good suggestion, efflandt.

I did a bit of digging to see what could be causing the "not responding" messages for the processor, and found that people were suggesting any of the following:

1. A USB hub or controller

You could try changing your USB controller settings in the BIOS to "Low" and unplug non-essential USB devices.

2. BIOS problem

Updating the BIOS may help. What version BIOS do you have? The downloads page at [www.foxconnchannel.com](www.foxconnchannel.com) might help you.

3. Boot with the 'noapic' parameter

You could try adding the word **noapic** instead of the words **quiet splash**

Hopefully we're narrowing down the problem :)

---

### Post by LuchenB on 2010-09-24
Well recently i didn't have it getting stuck anymore. But that was only on like 5 sucesfull boots.

I upgraded my BIOS recently so i doubt that's the issue. Though i do have a bunch of USB crap connected to my HUB. I shall experiment somemore, but i would rather not touching the BIOS just in case it would affect WIN7 performance.

---

### Post by LuchenB on 2010-09-26
I'm not sure if i should call this fixed yet but since i unplugged a bunch of USB stuff from my hub i've been getting sucessful boots every time (Though i've only booted around 10 times).

So here is what i have plugged in trough a USB hub:
A GENIUS Usb Mouse (really really old one)
A Genius PC Tablet
And the wireless dongle for the XBOX 360 controller.

Apparet from that i have a USB printer that's connected directly to my PC.

Hope it helps anyone else out there!

---

