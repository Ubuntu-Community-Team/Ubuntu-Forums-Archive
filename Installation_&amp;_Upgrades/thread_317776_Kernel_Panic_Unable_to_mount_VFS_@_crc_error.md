---
title: "Kernel Panic: Unable to mount VFS @ crc error"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Antmannz on 2006-12-12
Clean installation of Edgy gives kernel panic: unable to mount vfs and crc errors:

New system:
Asus M2NPV-MX (Nvidea 6150 chipset),
Athlon X2 5200+,
1Gb RAM,
320Gb Seagate SATA,
DVD Writer (IDE 0)

The story goes:
I began trying to install Edgy 64-bit off a LiveCD that had been used successfully with a previous installation on another machine, but immediately ran into problems with a kernel panic error: unable to mount vfs. No problem, I thought, I'll just reboot and try again, I must have missed something.
Reboot, and immediately hit a "crc error. System halted --" message. Strange.
Log on here from another PC and search for posts with these errors. Most posts state that the cd must be bad, download and burn another. So this is what I do ... twice, because I keep running into the same problem.
After reading through [this]("http://ubuntuforums.org/showthread.php?t=186115") massive thread, and trying almost all suggestions, I was still no further ahead.
Oddly each CD would exhibit the same behaviour: the setup would began OK once, until it hit the 'unable to mount vfs' error, and then I'd get crc errors on successive reboots.
I did begin to wonder perhaps that the LiveCD was trying to write back to IDE0 and being attached to a writer, was forcing a burn, thereby destroying the disc. But no.
I couldn't even run the "Check disc for errors" option, because it would never load that far.
A memory test showed no signs of problems.

Extremely frustrated, a day later I began an install of Win2K. Lo and behold I get memory address errors. A bad RAM stick was causing the problem.
It seems that on initial boot, the cd would be read into RAM, but the vfs mount error was occurring due to the bad stick. Then on subsequent reboots, **the system did not re-read the cd, but rather just kept using the cached instructions in the RAM** - thereby generating the crc errors. The only way to clear the RAM was a switch-off at the wall.

Heartened by this discovery, I installed a new RAM stick, and grabbed the Ubuntu CDs I had previously burnt - all were good.
BUT, now I was getting install hangs at the point where the mouse (PS2) is detected. ARGGHH!!! :evil: Make another search of the posts here. Replace mouse with no further effect.
I then boot with no mouse attached, this time the install hangs at parallel port detection. Another search of this site and Google, and it looks as though the install is actually hanging while trying to find the hard drive. ](*,) 

My resolution: Give up in disgust and install Win2K; I have a working OS inside 20 minutes.

<rant>
For starters, I've been in the IT industry for approx. 10 years and while I've done plenty of Win installs, I've only installed Ubuntu twice recently (both successfully), so class myself as a Linux noob. Having said that, I have more IT type problem-solving skills than your average Joe.

In my travels on this site I saw a post stating that the above problems are why Linux will never make it as a mainstream OS, and I have to agree.
In particular, Ubuntu is currently being held up as the poster child for Linux, but problems such as those I ran into above, I class as show-stoppers.
For starters, no matter how new a piece of hardware is, it should still be able to be detected. SATA hard drives and controllers are not particularly new, and yet the LiveCD could not detect the one on this board.
Even if we accept that the hardware is new; how come a version of Knoppix circa 2003 could detect and read it, and Windows 2000 could detect, read and install on it with no  problems - Windows 2000; from the time when SATA drives were barely invented.

What really grates me is people who state that one should look more closely when purchasing hardware to make sure it is compatible with Linux. I can accept that, however, **this particular board has Linux drivers on the accompanying CD**. Yes, Linux drivers come with it, and are ready and waiting to be loaded.
BUT YOU CANNOT LOAD THEM, BECAUSE THE LIVECD GIVES YOU NO OPPORTUNITY TO DO SO.
It just hangs if it cannot find a piece of hardware that it will talk nicely to.

I could have plugged in an IDE HDD, installed onto that, installed the drivers, and then imaged the IDE HDD onto the SATA drive. Like that would have been fun!! After a day and a half, I no longer had the patience to do so.

It's unlikely that I'll try an Ubuntu install again on this machine; at least until Fiesty is released, and probably not even then.
</rant>

So what can be learned from this?? If any of the developers have got this far, I would recommend a time-out on hardware detection; if the system cannot detect a piece of hardware inside 10 minutes, force it to move on. Also give the option of loading drivers other than those on the LiveCD; plenty of people now have over 512Mb RAM, that should be sufficient to get a LiveCD running (with hardware detection bypass), then allow driver installation, then install that lot to hard disk.
Perhaps also look at Knoppix, to see how they handle hardware detection.
Also, it would be great if the LiveCD actually told you what it was doing **before** it started doing it. (Yes, I was using the text mode installation). The current issue is that you get told what the installation has done, but not what it is doing; therefore users are probably currently trying to resolve installation hangs with incorrect resolutions, and are only hitting on the correct solution randomly.

Thanks (and congratulation) for reading this far, you must have much more patience and fortitude than I did in the last couple of days.  :)

---

