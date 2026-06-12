---
title: "TestDisk Destroyed My Laptop Not Even On To BIOS level ?"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by jetwong98 on 2013-05-12
With reference to this [http://ubuntuforums.org/showthread.php?t=2144073](http://ubuntuforums.org/showthread.php?t=2144073) , I downloaded Testdisk 6.13 on ubuntu 12.04.2 liveusb to fix the hard disk. After extracting, I double clicked the testdisk_static and 2 other executables, nothing showed nor worked, I clicked them again a few times, still nothing happened. However, I found the whole ubuntu environment was becoming lagging after clicking the testdisk_static and 2 other executables though nothing appeared. I then clicked restart. 

My laptop didn't show the BIOS screen anymore, just blank and beep then turned off by itself. I unplugged the battery, power cable, pressed down the power button and tried to on, the BIOS screen still didn't show, just blank screen, after 4 seconds after the CD Drive light was gone and beep sound, the laptop turned off by itself. I doubt if the TestDisk_Static and 2 other executables could damage the BIOS ? Motherboard ? Chip ? I clicked them many times but nothing prompted, just noticed the system was getting lagging & slower. After restart, my laptop didn't boot with BIOS screen anymore, just blank screen and turned off after a beep & after the CD Drive light. Now I deeply regret that I shouldn't install ubuntu in a rush screwing up everything, earlier WINXP and now the whole laptop is sacrificed :(

---

### Post by tgalati4 on 2013-05-12
First, *testdisk* is in the repositories.  So, with a proper network connection (wired) you simply open a terminal:

```
sudo apt-get install testdisk
man testdisk
man photorec
```

Live DVD or USB session will only keep *testdisk* around until you reboot--everything is in RAM and disappears at shutdown.

The file that you downloaded may have been a Windows executable or something else.  Since you didn't have a proper* testdisk* install, I doubt that it your problem.  The fact that your computer won't boot to BIOS could mean that there is a power supply problem or button-battery problem.  A leaky or corroded battery on the motherboard can cause a short which draws too much power causing the power supply into safety shutdown.

Of course, it could be something completely different.  If you remove your harddrive from the laptop and it still won't POST (power-on self test) or go into BIOS, then you know there is something else going on.  Many hardware problems look like harddisk or software problems.

I presume that you were having trouble with this machine before downloading* testdisk*.  It's easy to pin the blame on a piece of software without knowing what is going on.

What is the make and model of the machine?  How old is it?  Will it boot without the main battery?

If the data is important, remove the disk, put it in a USB enclosure and work on it from another, more reliable machine, preferably one running linux.

---

### Post by oldfred on 2013-05-12
Power down in the middle of something is one of the worst things you can do to a system. It almost always corrupts file system and you have to run chkdsk from a Windows repairCD if in Windows or e2fsck if in Linux ext2, 3 or 4 file system.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Some laptops do get locked up and need a full power down or cold boot. But with a battery, then on a laptop that is hard to do.
      
 Total cold boot with laptop
Laptop full power reset. post #4 hold power on switch after removing battery
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by Old_Grey_Wolf on 2013-05-12
> **jetwong98 said:**
> ...my laptop didn't boot with BIOS screen anymore, just blank screen and turned off after a beep & after the CD Drive light. ...

Those beeps mean something. Google the model of computer you have and beep codes, such as, "Dell N4110 beep codes". Then read what the beeps mean. It may help you identify the problem. I've had keyboard controllers, memory, etc., go bad and used the beep code to identify the problem.

---

### Post by darkod on 2013-05-12
It's too late now, but just for future reference to point out that testdisk is not a GUI program. Instead of double clicking on it, you should have opened it by opening terminal and executing:
```
cd /path_to_testdisk
sudo testdisk_static
```

Or maybe the second line should have been sudo ./testdisk_static. I confuse them.

Installing it with apt-get should also work as mentioned above.

---

### Post by Old_Grey_Wolf on 2013-05-12
> **darkod said:**
> 
Or maybe the second line should have been sudo ./testdisk_static. I confuse them.

I am pretty sure it is sudo ./testdisk_static.

---

### Post by steeldriver on 2013-05-12
One of my old Thinkpads sometimes gets in a state where it won't even power to BIOS/POST - I have found that physically removing and refitting the battery will revive it

---

### Post by jetwong98 on 2013-05-12
Tried unplugging the battery and hold down the power button for 1 minute without power supply, problems still persist. Just left it overnight without power & baterry and tried again today, still the same. I doubt if I used the wrong testdisk linux version 1.63 [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) which might not be suitable for ubuntu 12.04.2, that's why nothing appeared when I clicked them but maybe some processes started working behind without my knowledge as I noticed the system was getting slower. 

Right after restart from the ubuntu liveusb, my laptop would never POST, every time after the HDD light & CD Drive light went off, it will turn off but auto turn on again itself and then stays off after CD Drive light. I'm sure the testdisk executables might have been running behind though nothing appeared after clicking them, if not the system wouldn't be getting slower.

Something wrong with screws at the bottom cover, I couldn't unscrew some of the screws to reseat the RAM, CMOS, HARD DISK, I could only unplugged the battery which is not screwed.

Later I found the testdisk 1.63 is running on older version of linux kernel 2.6 but ubuntu 12.04.2 is running linux kernel 3.X, could this be the possibility of damage ? I heard some softwares could damage the hardware by causing ultra loads of irrational read-write operations to the hard disk as well as heating up the CPU operations and etc, I doubt if the testdisk 1.63 executables were doing something similar behind damaging the board / Chip / BIOS, for sure my laptop won't suddenly not turn to POST.

---

### Post by darkod on 2013-05-13
In some extreme situations hardware may get damaged when forcing a shutdown (like you had to do). Or you might have had a problem even earlier and that's why the repartitioning of the installer failed.

As for running testdisk, again, it clearly says that on Linux you do it on the command line, not with double-clicking. That's only for windows.
[COLOR=#000000][FONT=sans-serif]> Under Unix/Linux/BSD, you need to be root to run TestDisk (ie. [/FONT][/COLOR]sudo testdisk-6.13/testdisk_static[COLOR=#000000][FONT=sans-serif])

Testdisk is compatible with 12.04, there is no problem running it in live mode. You only tried to start it on a wrong way, and further on forcing the laptop to shut down might have added to the problems. Which might have existed even before that.

Did you try starting the laptop without the hdd?[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-05-13
Are the bottom case screws messed up because of previous servicing on this laptop?  Perhaps there really is a hardware problem.  Case screws sometimes have glue on them to prevent them from falling out.  Use a fine file to file down a screwdriver so you get a sharp edge on the blade.  That will help remove those pesky screws.

---

