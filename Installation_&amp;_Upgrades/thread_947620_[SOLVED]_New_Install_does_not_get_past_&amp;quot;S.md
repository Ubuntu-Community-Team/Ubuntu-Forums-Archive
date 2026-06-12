---
title: "[SOLVED] New Install does not get past &amp;quot;Starting up ...&amp;quot;"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by phowells on 2008-10-14
Hello All,

I am trying to install Ubuntu 8.04 LTS Desktop Edition from CD onto an old PC.

Processor:Intel Celeron 1GHz
Ram:384MB
Chipset:VIA 82c693A/596B
Video Card:Viper V770 16MB
HDD:Seagate Barracuda 7200.10 320GB

When the install is completed and I try to reboot the machine it gets stuck on the "Starting Up ..." screen.

I would really appreciate any help or suggestions.

Thanks
Paul

---

### Post by ^NeoPhyt3^ on 2008-10-14
Please Look up the UBUNTU requirements it needs atleast 384 MB RAM for CD installation.Thats why u wont be able to install 

:-(

---

### Post by phowells on 2008-10-14
Thanks for your reply.  I do have 384MB of RAM, not 320MB.  I have corrected my post.  

To clarify, the install completes successfully.  The initial boot fails as it does not get past the "Starting up ..." screen.

---

### Post by ^NeoPhyt3^ on 2008-10-14
Good For You I am failing in installation too .. :(

---

### Post by lukydude on 2008-10-14
> **phowells said:**
> Thanks for your reply.  I do have 384MB of RAM, not 320MB.  I have corrected my post.  

To clarify, the install completes successfully.  The initial boot fails as it does not get past the "Starting up ..." screen.

the actual ubuntu is 512mb after install, I reccomend kubuntu for pcs like yours ;)

---

### Post by wpshooter on 2008-10-14
Try installing using the safe graphics mode.

If that does not work then try installing from the ALTERNATE (text based) CD version.

---

### Post by lukydude on 2008-10-14
> **wpshooter said:**
> Try installing using the safe graphics mode.

If that does not work then try installing from the ALTERNATE (text based) CD version.

If he's new to ubuntu he might not be able to use text based (commands code etc)

---

### Post by phowells on 2008-10-14
I have tried booting in safe mode but I encounter the same problem.  I will try installing from the Alternate CD.

The official documentation suggests that my hardware is sufficient to run Ubuntu 8.04

Quote:

Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 
700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 
A network or Internet connection

---

### Post by wpshooter on 2008-10-14
> **lukydude said:**
> If he's new to ubuntu he might not be able to use text based (commands code etc)

ALTERNATE cd installation does not require much more skill (if any) more than installing from the DESKTOP/live CD version.  All they have to do is go thru it a few times and they will be an old pro.

Make sure that you always check the integrity of your Ubuntu CD by running the verification function which is found on the initial Ubuntu boot screen menu.

---

### Post by robert shearer on 2008-10-14
> **phowells said:**
> Hello All,

I am trying to install Ubuntu 8.04 LTS Desktop Edition from CD onto an old PC.

Processor:Intel Celeron 1GHz
Ram:384MB
Chipset:VIA 82c693A/596B
Video Card:Viper V770 16MB
HDD:Seagate Barracuda 7200.10 320GB

When the install is completed and I try to reboot the machine it gets stuck on the "Starting Up ..." screen.

I would really appreciate any help or suggestions.

Thanks
Paul
Hi phowells,

I have a machine near to yours, same processor and graphics card, but twice the Ram, so do persevere. 512Mb would be better though.

You do not mention Windows at all so I am assuming that this is a clean Ubuntu install you want to make on an older computer??

The size of hard drive would indicate that you have put together some components for this purpose.??? I am assuming again.

When I did this I had to check the bios to see that the drive was recognised and configured correctly.
Had to eyeball the jumpers on the drive for correct placement too.(Got it wrong twice!)

I was recycling an old drive and installing Ubuntu ONLY so I wiped the drive first.
There seemed to be something in the MBR that wasn"t being overwritten during a normal install (left over Windows virus?) that prevented booting but a full disc wipe fixed it.

---

### Post by phowells on 2008-10-14
I am confident in the MB settings and the hard drive is being recognized correctly.

I am beginning to suspect that this may be a video card problem since there have been a lot of complaints about this card in the forum. 

The hard drive used to have XP installed when it was in a different machine so maybe I need to wipe the MBR.  How can this be accomplished?

---

### Post by robert shearer on 2008-10-14
> **phowells said:**
> I am confident in the MB settings and the hard drive is being recognized correctly.

I am beginning to suspect that this may be a video card problem since there have been a lot of complaints about this card in the forum. 

The hard drive used to have XP installed when it was in a different machine so maybe I need to wipe the MBR.  How can this be accomplished?

When you run the live cd is the graphics card working? If so it should work from an install.
Does your mobo have onboard graphics option you could test?
What happens when you boot the install? 
 Does it freeze leaving the 'Starting up' text showing or does it go to a blank screen.

Load the live Ubuntu cd and select System=>Administration=>Partition editor and see if there is an option to erase/format your disc.

I use Paragon hard disk manager which has a Linux option to wipe .

---

### Post by phowells on 2008-10-14
The graphics card works for the install but this may be because it is using default drivers and not the drivers specific to the card which are used once it is installed.  There is no onboard graphics card on this mobo.  When I boot the install it freezes on the "Starting up ..." text.  I think the cursor continues to flash but it is stuck there for hours before I restart.

I will try the partition editor.

---

### Post by robert shearer on 2008-10-14
Can you loan a graphics card out of another machine to test??

Reinstalling using the alternate cd (and checking its integrity first) as suggested  by others seems the next step.

---

### Post by phowells on 2008-10-14
> **robert shearer said:**
> Can you loan a graphics card out of another machine to test??

Reinstalling using the alternate cd (and checking its integrity first) as suggested  by others seems the next step.

I have another AGP card I am going to try but it may not work because it is a 1.5v card and the V770 is a 3.3v card.

---

### Post by phowells on 2008-10-17
I replaced the Viper V770 AGP card with a 64MB Geforce4 MX440 AGP card I had lying about.  I reinstalled and was able to boot without any problems.  The default settings or driver for the V770 must prevent Ubuntu from booting.

Problem solved.  Thanks for your help.

---

### Post by robert shearer on 2008-10-18
> **phowells said:**
> I replaced the Viper V770 AGP card with a 64MB Geforce4 MX440 AGP card I had lying about.  I reinstalled and was able to boot without any problems.  The default settings or driver for the V770 must prevent Ubuntu from booting.

Problem solved.  Thanks for your help.

Great to hear this!.
We must have old equipment convergence as my other test machine is a P3 with 64MB Geforce4 MX440 AGP card.!

You should now mark this thread as solved- see here for how to...
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

so that others can benefit from your discoveries.

You may also be interested in the beginners links and primers here....
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Welcome and Happy Experimenting.:)

---

