---
title: "Re-Install of 9.10 Stops with Blinking Screen"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by JKLandes on 2010-04-03
Newbie alert - Newbie alert.... Ok, perhaps not a complete newbie (managed VMS and Windows for ~25 years), but the last time I used Unix was in the early 80's when the PC-XT was first released...
 
I have a new PC with NVIDIA 9600 card. It's running Vista Business (ugh!). The 500GB hard disk has Vista in one 250GB partition. I unstalled Ubunto 9.10 Desktop, having it take the rest of the hard drive as it's own partition, allowing it to set up the multi-boot GRUB and it was running fine until an auto-update changed my kernel. 
 
From the threads I see that the NVIDIA drivers aren't updated properly during the update. The result was, when booting, Ubuntu complains it could not find certain files, etc, and the X-server wouldn't load. 
 
I hadn't done much with Ubunto yet, still learning, so after unsuccessfully trying to fix it I decided I'd just re-install the original 9.10 on top of what I had. I booted from the install CD and selected Install. From there it got just beyond setting the time, when it's examining the hard disk, and it stops and the terminal screen just blinks. In fact, I noticed it blinks in a morse-code kinda way, blinking 7 times and then pausing and repeating, in case that's significant.
 
Ok, looks like I'm really hosed, so I look up how to remove Ubunto and find a posting that had me create a nifty bootable CD (BootIt from Terabyte), delete the extended partition where Ubuntu was loaded and update the MBR so it boots straight into Vista. It worked great: a power-up boot goes right to Vista - no GRUB.
 
[http://www.terabyteunlinkted.com/bootit-next-generation.htm](http://www.terabyteunlinkted.com/bootit-next-generation.htm)
 
Ok, so now I try to re-install Ubunto 9.10 32-Bit Desktop again from my bootable CD, select Install and I get to the same darn place, examining the hard drives, and I get the same problem I described above - it just stops and the terminal session just blinks.
 
Can someone shed some light on where I go from here?

---

### Post by BigSteve_G on 2010-04-03
9.10 caused display problems for me too on my laptop & after a lot of googleing I just ended up going with the simpler method (something that fixed a few issues on my main system too).

When you go to install, boot the live CD & select 'Compatibility mode' that way when you install it must use some different settings or some thing - anyways its worked for me on 2 seperate systems.

-Just a note as well if you try any other methods were by you install drivers yourself be careful as I did this but the driver was 1 model older then the one I needed & it killed the system.

---

### Post by JKLandes on 2010-04-04
Steve,

I found a "Minimal Graphics" or similar option that allowed Ubuntu to install, though it's running in a very low resolution mode. I'm guessing the mode caused it to skip trying to find an optimal driver set and I'll need to update/load the NVIDIA drivers. Since I have a functional system once again I'll need to teach myself how to properly back all this up and create a work flow for making updates without ending up like I did before. Thanks for your quick reply :)

---

### Post by JKLandes on 2010-04-04
I ended up reverting back to the VESA driver - could not get the NVIDIA driver (I have an NVIDIA 9600 GT) to work at any resolution better than 640x480, even after googeling for hours. Odd thing, tho... To get a decent resolution I had to edit the xorg.conf file and put a Modeline in for 1600x1200. While I don't actually get this resolution, I do get 1280x1024. Just in case anyone else wants the resulting file, I'll try to paste it in below....

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync    31-61
    VertRefresh    50-75
    Modeline "1600x1200" 155 1600 1656 1776 2048 1200 1202 1205 1263
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Depth    32
        Modes    "1600x1200"
    EndSubSection
EndSection

---

