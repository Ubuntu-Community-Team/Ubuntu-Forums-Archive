---
title: "Hard Drive Not being recognized/seen during installation"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by residualbit on 2011-01-13
Hey all,

I've been a Ubuntu user since Warty and have recently run into a problem that has thrown me for a loop.

I have a fairly new Desktop, an HP 210y, that I would like to install Ubuntu on. I have tried everything I can think of and the issues I will describe below happen with 10.04 and 10.10.

Essentially, it seems like Ubuntu isn't seeing my hard drive during the install process. I started this endeavor having a full install of Windows 7 64 bit. After putting in the live cd, whether i tried to install or just boot, i would end up getting the  "(initramfs) Unable to find a medium containing a live file system" error from BusyBox. I then opted for a USB/Thumbdrive install attempt. This got me a little farther in that I was able to boot into a live session. Beyond that, when I tried to install, I would get to the part where the partition selection would be. I have always seen an option to 'Erase and use entire disk' with previous attempts on other PCs, but this took me to what I think is the manual partition editor, which was completely empty. When I tried to continue with the install, i got a 'no root filesystem is defined' error. In a last ditch effort, I used gparted to wipe out all existing (windows 7) partitions and I now have 1TB of unallocated space. Still no go. I'm sort of lost at this point. In the live session, i can see the hard drive fine, gparted sees it, can make changes to it, etc, but I can't install Ubuntu. I am running off the live usb now. Help!

-Nate

---

### Post by residualbit on 2011-01-14
I have linked a screen shot showing that a) gparted can see my 1tb drive's unallocated space, and b) step 4 in the install sees absolutely nothing. I am currently using 10.04 64bit from a live USB.

[http://img217.imageshack.us/img217/2870/screenshottv.png](http://img217.imageshack.us/img217/2870/screenshottv.png)

---

### Post by nuclearwasted on 2011-01-14
Try tinkering in the bios.

---

### Post by Quackers on 2011-01-14
How many primary partitions were on the drive?

---

### Post by Rubi1200 on 2011-01-14
Few things to look at:

1. check that BIOS is capable of seeing the drive; a lot of older BIOS can only see the first 137GB

2. read this: [http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

3. check there is no RAID metadata on the drive: [http://www.uluga.ubuntuforums.org/showpost.php?p=9447593&postcount=3](http://www.uluga.ubuntuforums.org/showpost.php?p=9447593&postcount=3)

4. also look here: [http://ubuntuforums.org/showpost.php?p=9464066&postcount=3](http://ubuntuforums.org/showpost.php?p=9464066&postcount=3)

---

### Post by Hydrosis on 2011-01-14
You need to format it to a file system type.  Unallocated means unallocated!


[IMG]http://gparted.sourceforge.net/screens/gparted_7_big.png[/IMG]

---

### Post by SqRt7744 on 2011-01-14
I had a similar problem until I did the following:

Downloaded the *alternate* install cd & created a usb stick with the "Startup Disk Creator" tool (System->administration->Startup Disk Creator). Don't use unetbootin, it won't work. When you get to the partition setup step you should be able to see everything properly. If this doesn't work for you, post back.

---

### Post by residualbit on 2011-01-14
Apparently there was RAID meta data. I ran this ```
sudo dmraid -r -E /dev/sda
``` and removed it. I will try to reboot and let you know. One question though, I have linked a screen from my bios. In the advanced settings, the only thing that jumped out at me was the sata controller mode. It was set to RAID, but gives the option for IDE or AHCI as well. Should I change it?

[http://img715.imageshack.us/i/img20110114010435.jpg/](http://img715.imageshack.us/i/img20110114010435.jpg/)

---

### Post by Rubi1200 on 2011-01-14
Yes, you need to change it to IDE mode. 

Was the drive part of a RAID array previously?
No matter, we have seen this before and removing the metadata usually clears up any issues.

---

### Post by residualbit on 2011-01-14
Removing the meta data got seems to get me to where i need to be in the install in that the drive is being seen and I have the ability to erase and use entire disk. I'll reboot one more time and change the controller mode to IDE. It was never setup with RAID. It's a prebuilt HP desktop that was purchased from Best Buy, so I have no idea why it would have had those setting be default...weird. Thanks for all the help!

---

### Post by Rubi1200 on 2011-01-14
Let me know what happens and if changing to IDE is also okay.

Regarding the metadata; what can I say? It is odd, I agree.

---

### Post by residualbit on 2011-01-14
Pardon my ignorance, but I will admit that I am not too familiar with advanced motherboard and bios options/configurations. Is there any downside to having it set in IDE vs. RAID vs. AHCI?

---

### Post by cascade9 on 2011-01-14
Yes, there is. IDE mode disables NCQ (native command queing) so there is a performance hit. AHCI is the way to go.

---

### Post by Rubi1200 on 2011-01-14
> **cascade9 said:**
> Yes, there is. IDE mode disables NCQ (native command queing) so there is a performance hit. AHCI is the way to go.
Thanks for the clarification; it's appreciated.

---

### Post by cascade9 on 2011-01-14
I did a little digging, it seems that system uses a foxconn H-RS880-uATX motherboard. I cant find detailed specs, the best I could find was here- 

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c01925486&product=4007354#N299](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c01925486&product=4007354#N299)

It doesnt specify which southbridge they used, but since its a AMD 785G chipset it should be using the SB600, SB700, SB710 or SB750 southbridge. I havent tried using the SB700 or SB750 southbridge, but I have used the SB 600 and I'm currently on SB710. Both worked fine with AHCI, I'd think that your setup should as well.  

If it doesnt and you can only use IDE, its not a huge difference between IDE and AHCI. Its bigger than the benchmarking/testing on the net could lead you to believe (as NCQ is most useful when under heavy read/write loads, and that isnt a situation that most benchmarks use), but its not worth getting overly worried about. 

> **Rubi1200 said:**
> Thanks for the clarification; it's appreciated.

No problem ;)

---

### Post by residualbit on 2011-01-14
Hey Guys,

The install went well, but I did run into one minor issue on reboot (and every boot.) See linked image:

[http://img703.imageshack.us/i/img20110114090757.jpg/](http://img703.imageshack.us/i/img20110114090757.jpg/)

If it type exit at the initramfs prompt, it boots right into Ubuntu with no problems almost immediately. Weird. I haven't really had any time to tinker with it as I had to go to work, but if anyone has seen this or has any ideas, let me know and I will give them a try when I get home.

Thanks.

---

### Post by Rubi1200 on 2011-01-14
What graphics card do you have installed?

---

### Post by residualbit on 2011-01-14
It's an ATI 5450, but now that I think about it, there was a restricted driver available. When I get home, I'll install that and any updates. After that, I'll let you know if there are still any lingering issues.

---

### Post by Rubi1200 on 2011-01-14
Sounds like a good plan; let me know how it goes.

---

### Post by residualbit on 2011-01-14
no luck. I am still having the same thing (see my image link above) after installing all updates and restricted drivers. I actually had to type exit at the initramfs prompt about 10 times to get it to move along.

---

### Post by residualbit on 2011-01-14
I've done a little digging. On a side note, it appears that part of my initial troubles with installing from a cd are because my disk drive isn't supported by ubuntu yet.

Anyway, as far as the boot issue after install, it looks like this may be due to me installing from a flash drive. I noticed that when I was booting, I wasn't seeing anything about grub. On a whim, I stuck the thumb drive back in and tried to boot as normal. Grub popped up as I am used to, i picked the first option (forget what it was) and that eventually got me to the same 'gave up waiting for root device' error pictured a few posts up. Baby steps.

It seems to me that installing from the flash drive possibly didn't actually copy over all necessary boot files?

---

### Post by residualbit on 2011-01-15
The initial, title problem has been solved. I have created a new thread for the new issue(s):

[http://ubuntuforums.org/showthread.php?p=10359327#post10359327](http://ubuntuforums.org/showthread.php?p=10359327#post10359327)

Thanks for all of your help!

---

