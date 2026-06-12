---
title: "Need help loading 12.04 on Compaq laptop"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by Curbuntu on 2012-07-03
After standing off on the sidelines during 11.04 and 11.10, wondering how things were going to shake out, I have jumped into 12.04 with both feet.  Mark and the team have ***really*** pulled off an interface-design coup.  Kudos to all.  I have upgraded two machines to Ubuntu 12.04 and want to do our remaining four.

The problem I'm encountering is on a Compaq Presario R3399CL laptop (AMD 64 3200+ processor, 2 Gb RAM, 120 Gb HDD), which has been running 10.04 for almost two years.  I can't get the installation CD to boot.  I tried a different download (in case the file was corrupted) and tried burning a CD on a different machine.  No go.  I've tried booting from a USB drive.  Same story.  In each case, the boot process works part way through, then hangs.  I've even tried the alternative CD, which gets as far as the initial menu; but when I try to check the disk or test the memory from that menu, everything fails.

The machine seems to check out okay with other diagnostics, so I don't think it's a hardware issue.  Any guidance would be appreciated.

---

### Post by dino99 on 2012-07-03
add some boot option, like nomodeset or noacpi, see community/help

---

### Post by Curbuntu on 2012-07-03
> **dino99 said:**
> add some boot option, like nomodeset or noacpi, see community/help

Dino99 -- Are you talking about the options available on the alternative-install CD?

---

### Post by sudodus on 2012-07-03
Excuse me for intercepting this question, but I think the boot option issue is independent of installer, and if you need a boot option trying in a live session, you are likely to need it also in the installed system. See this link

[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

Good luck :-)

---

### Post by Curbuntu on 2012-07-03
Okay, I've read the pertinent page, but I'm not pretending I understand what the options do; that makes me hesitant to proceed, because it feels like "shooting in the dark."

Reading the page you linked to reminds me that of all our Ubuntu computers, this is the one machine that has never displayed a GRUB menu of any sort at boot up.  I don't know if that has any correlation to the problem at hand or not...

---

### Post by mastablasta on 2012-07-04
reading the page, reading... just read it. you will see that these options might help. especially nomodeset and acpi=off.
 
i never get grub displayed unless i make it display. why should it display?
 
what is your graphics card?

---

### Post by sudodus on 2012-07-04
> **Curbuntu said:**
> Okay, I've read the pertinent page, but I'm not pretending I understand what the options do; that makes me hesitant to proceed, because it feels like "shooting in the dark."

Reading the page you linked to reminds me that of all our Ubuntu computers, this is the one machine that has never displayed a GRUB menu of any sort at boot up.  I don't know if that has any correlation to the problem at hand or not...
I have tested linux distros hundreds of times. Only once, using the micro-linux distro DSL, I bricked a graphics card in an ancient computer, but that was not using boot options. I think you dare try :-)

---

### Post by Curbuntu on 2012-07-04
mastablasa & sudodus,

Thanks for your patience.  The video chip is an older nVidia GeForce4 440 Go 64 M(b), fwiw.

At this point, using the alternative-install CD (32 bit), I can set things like nomodeset and various permutations of acpi; but once I've escaped from the menu and hit Enter, the CD spins up, the screen goes blank, and that's the state in which things remain until I do a hard re-boot on the machine.

Perhaps this machine is too "old" to run 12.04?  Not knowing, I'd still like to keep trying until we're certain that's so.

---

### Post by mastablasta on 2012-07-04
Uf an old GPU. but should be supported by opensoruce drivers at least. important to note here that Ubuntu now uses 3D hardware acceleration by defaul. but you should at leats get some fall back session. you could try to search if there was a bug reported with that chip.
 
> **Curbuntu said:**
> 
At this point, using the alternative-install CD (32 bit), I can set things like nomodeset and various permutations of acpi; but once I've escaped from the menu and hit Enter, the CD spins up, the screen goes blank, and that's the state in which things remain until I do a hard re-boot on the machine.

 
Alternative CD is not a live CD (as far as i know). It just provides a text based installer. so it shouldn't boot to any OS. you need to get grub when you boot live CD.
 
hmm... the latest image does include the PAE kernel, but your CPU should support it nicely. Try a lubuntu liveCD/USB (i think they have a bit modified kernel so it is more suitable for older computers. if it works you can then install Ubutnu (unity/gnome) dekstop on it. 
 
> 
Perhaps this machine is too "old" to run 12.04? Not knowing, I'd still like to keep trying until we're certain that's so.
 
no it's not too old. i have a desktop (with similar specs but stronger graphics card) and can run the latest versions just fine.
 
edit: as mentioned try a different desktop. it seems this card should later use proprietary driver to get 3d hardware acceleration. 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)
I also found a post about slow reposne using Kubuntu but it does seem it work there as well. so try Lubuntu/Xubuntu/Kubuntu to see if any of them works (suggest you use USB to try it out as it iwll save you a couple of CD, if you have trouble botoing from usb you can use plop boot manager).

---

### Post by Curbuntu on 2012-07-04
mastablasta,

The Lubuntu Live CD sounded like a good idea.  I downloaded the ISO, and checked it against MD5 and SHA256, so it's a known good copy.  The CD also passes its own menu-option self-check.

The CD boots successfully, obviously; but starting the "try" option causes the process to hang after a bit.  On a hard re-boot, I set nomodeset, acpi off, and, for good measure, removed *splash* and *quiet* from the command line.  That combo gave me a visual window on the place the process hangs up -- apparently right after the message which says:

```
Starting CUPS printing spooler/server    [OK]
```

I say, "right after" because nothing else appears.  From that point, the fan whines like the processor's working hard, but "nobody's home."

---

### Post by sudodus on 2012-07-04
Try also the

noapic
nolapic
edd=on

boot options.

If still no luck, try Knoppix live. After testing you can install it to an almost-debian system. Knoppix is known to be good at recognizing hardware for old as well as new computers.

[[COLOR="Red"]_ftp://ftp.uni-kl.de/pub/linux/knoppix/_[/COLOR]]("ftp://ftp.uni-kl.de/pub/linux/knoppix/")

---

### Post by Curbuntu on 2012-07-05
I tried the other boot exceptions you mentioned (along with removing *splash* and *quiet*).  The process always loads to a certain point (but never the *same* point) and then freezes.  The last attempt moved to the farthest point yet -- the line below the CUPS line mentioned previously:

```
Loading the saved-state of the serial devices...
```

On to Knoppix, I guess...

---

### Post by sudodus on 2012-07-05
> **Curbuntu said:**
> I tried the other boot exceptions you mentioned (along with removing *splash* and *quiet*).  The process always loads to a certain point (but never the *same* point) and then freezes.  The last attempt moved to the farthest point yet -- the line below the CUPS line mentioned previously:

```
Loading the saved-state of the serial devices...
```

On to Knoppix, I guess...
Yes, all linux distros 'belong to the same family'

Good luck :-)

---

### Post by sudodus on 2012-07-05
> **Curbuntu said:**
> I tried the other boot exceptions you mentioned (along with removing *splash* and *quiet*).  The process always loads to a certain point (but never the *same* point) and then freezes.  The last attempt moved to the farthest point yet -- the line below the CUPS line mentioned previously:

```
Loading the saved-state of the serial devices...
```

On to Knoppix, I guess...
Who knows what the installer is doing after 'Loading the saved-state of the serial devices...'?

---

### Post by Curbuntu on 2012-07-05
Well, Knoppix booted, started loading, got about halfway down the second screen to

```
Starting DRM and Framebuffer mode...
```

and then hung.  What on earth am I missing here?  It's usually so simple.

After-posting edit: After a reboot of Knoppix, I'm experimenting with the boot options under F2.  Currently I'm running MemTest.  The Knoppix DVD has v. 3.5a, which is running.  (MemTest 4.2, which comes on the Ubuntu CDs, would start and hang.)  Once this test is through, I'll start Knoppix with the "turn stuff off" boot mode and see what happens.

Assuming that works, and Knoppix works, what's the game plan?

---

### Post by sudodus on 2012-07-05
> **Curbuntu said:**
> Well, Knoppix booted, started loading, got about halfway down the second screen to

```
Starting DRM and Framebuffer mode...
```Once this test is through, I'll start Knoppix with the "turn stuff off" boot mode and see what happens.

Assuming that works, and Knoppix works, what's the game plan?
If you are happy with Knoppix (running live) you can install it applying the same boot options.

Otherwise start to think what hardware might cause trouble. One way to scan the hardware is
***hardinfo***, can be installed with ```
sudo apt-get install hardinfo
``` another is ```
gksudo lshw | less
``` or if you prefer to save it to a file ```
sudo lshw > lshw.txt
``` and post the content.

---

### Post by Curbuntu on 2012-07-05
I wish I had better news to report (like I'd suddenly acquired a working brain), but even with all the boot parameters set (even *nodma*), Knoppix is still hanging at

```
Staring DRM and Framebuffer mode...
```

How is it that this machine boots Ubuntu 10.04 from its hard drive every day, but can't load other versions of Linux from CD or USB drive?

---

### Post by Curbuntu on 2012-07-05
Just saw your new post (after my "I wish I had better news" post), and I will get that info up here soon.  Thanks for hanging in here with me!

---

### Post by Curbuntu on 2012-07-05
I'm assuming that since the *lshw* output is almost 400 lines that I should attach the output file (which I have done), rather than tie up screen real estate in this thread.  

I'm prohibited from attaching the output from *hardinfo*, since it's an *.html* file (security precaution, I'm sure); but I can get that to you if necessary.  I suppose I could change the extension to .txt and you could change it back to .html.

BTW, thanks for the tip on the **hardinfo** utility -- quite useful!

---

### Post by sudodus on 2012-07-05
> **Curbuntu said:**
> I wish I had better news to report (like I'd suddenly acquired a working brain), but even with all the boot parameters set (even *nodma*), Knoppix is still hanging at

```
Staring DRM and Framebuffer mode...
```

How is it that this machine boots Ubuntu 10.04 from its hard drive every day, but can't load other versions of Linux from CD or USB drive?

Ubuntu 10.04 will receive updates until April 2013, so you have plenty of time to find something that will work ;-) but honesty I don't know. Something that works is not supposed to be dropped in newer versions of the operating system. Since there is time, ***maybe you can enroll in the testing of the coming version 12.10 (and give feedback to the developers from your computer)***. The testing is at alpha stage now. It will continue via beta and release candidate until it will be release in October.

- Is it possible to enter the BIOS menus and try to switch some hardware off (for example wifi or firewire or pcmcia)? Just to test if the computer will boot.

- Can you check if the memory is OK (run memtest from the grub menu)?

---

### Post by joe needs help on 2012-07-05
I'm having a similar problem with a Compaq laptop that is older than yours.    My work around was to upgrade from 11.10 to 12.04.  12.04 boots and runs fine from the hard drive, but the live/install cd won't boot.   Both the 10.04 and 11.10 live/install cd's boot and run fine.   

I tried the Alternate install cd, and the install went fine, but then 12.04 wouldn't boot from the hdd after the install.   It hung just like the install cd.

What's different about my case it that I did boot and 'try' 12.04 from the live cd twice before trying to install it.   I'm contemplating updating the BIOS, but the conservative part of me says as long as 12.04 is running, don't mess with it.

Please post your fix if you get the cd to boot.

My thread:  [http://ubuntuforums.org/showthread.php?t=2014933](http://ubuntuforums.org/showthread.php?t=2014933)

Joe

---

### Post by sudodus on 2012-07-05
> **joe needs help said:**
> ...My work around was to upgrade from 11.10 to 12.04.  12.04 boots and runs fine from the hard drive, but the live/install cd won't boot ...

Interesting :KS

This may be something to test in your computer too (upgrading from 11.10 to 12.04) *Curbuntu*, or to wait until later this month (July), when we expect to get an offer to upgrade from 10.04 LTS to 12.04 LTS, and test upgrading. But since upgrading between versions is a high-risk project, make sure you have a ***good backup before starting***.

---

### Post by Curbuntu on 2012-07-05
> **sudodus said:**
> 
- Is it possible to enter the BIOS menus and try to switch some hardware off (for example wifi or firewire or pcmcia)? Just to test if the computer will boot.

I wish that were possible.  This PhoenixBIOS is one of the most "user friendly" BIOSes I've ever encountered -- and in that statement, "user friendly" should be translated as "all users are idiots, so give them VERY few options to change if they happen to stumble into the BIOS settings."

> **sudodus said:**
> 
- Can you check if the memory is OK (run memtest from the grub menu)?

MemTest 3.5a (running off the Knoppix DVD) came up with a clean bill of health.

> **sudodus said:**
> 
Ubuntu 10.04 will receive updates until April 2013, so you have plenty of time to find something that will work 

Actually, I HATE to "fix it if it ain't broke"; the trouble is, I have two 10.10 systems (both desktops) that I need to upgrade (no more updates!), plus my main 10.04 laptop (newer than the problem unit).  All machines have /home on a separate partition (and they're backed up with CrashPlan).  But this "problem" laptop was meant to be the "canary in the mine," so to speak.  I tried installing 12.04 to / on a similarly partitioned drive (on yet another machine) a while back, and the Unity interface came out the worse for it.  In the end, I slicked the whole hard drive, repartitioned, and everything worked fine from that point.  (There was no data to restore on that one, other than what DropBox would do automatically.)  

I'm trying to figure out how to install 12.04 to the root partition with nothing missing and no personal data files lost.  This was the machine on which I hoped to experiment, as it is "only" my backup machine.  The more important ones are daily production machines ("his" and "hers") and a 10.10 desktop functioning as Banshee music server (also "hers"!).

---

### Post by Curbuntu on 2012-07-05
> **sudodus said:**
> This may be something to test in your computer too (upgrading from 11.10 to 12.04) *Curbuntu*, or to wait until later this month (July), when we expect to get an offer to upgrade from 10.04 LTS to 12.04 LTS, and test upgrading. But since upgrading between versions is a high-risk project, make sure you have a ***good backup before starting***.

I had thought about the tortuous route of upgrading 10.04 --> 10.10 --> 11.04 --> 11.10 --> 12.04; but to think I could get through even the first two hops, much less all four, stretches my credulity to the breaking point.

I was unaware of the July 10.04 --> 12.04 experiment.  If I might be borking my system anyway, I might as well wait and do it for a good cause.  (Although I had hoped to complete this project before I commence traveling again.)  Where do I "sign up" to get a notification of the upgrade test?

As for backups -- between CrashPlan, Ubuntu-1, and DropBox, we've got that more than covered.

---

### Post by Curbuntu on 2012-07-05
I don't know if the information is worth anything, but I thought I'd experiment this afternoon to see at what distro the Live CD ceased working on this laptop.  The answer -- **10.04.3** is the last one that works.  Following that, no other distro  -- 10.10, 11.04, 11.10, and 12.04 -- gets as far as the "try it or install it" menu.  They all hang up as the "progress bar" (or "progress dots," I guess) works away.  

I wonder -- what changed on the live CD after 10.04?

---

### Post by sudodus on 2012-07-05
> **Curbuntu said:**
> ...
I was unaware of the July 10.04 --> 12.04 experiment.  If I might be borking my system anyway, I might as well wait and do it for a good cause.  (Although I had hoped to complete this project before I commence traveling again.)  Where do I "sign up" to get a notification of the upgrade test?

The previous 8.04 --> 10.04 LTS upgrade worked nicely for me with Ubuntu and Kubuntu on different computers. I expect this new one to be well debugged when offered. And I expect it to be offered automatically in the update manager. Not run automatically, only offered as an available option to click on ;-)
> 
As for backups -- between CrashPlan, Ubuntu-1, and DropBox, we've got that more than covered.
At least, we don't need to worry about that :-)

     -o-

I had expected that Knoppix would have succeeded. Some months ago I tested and installed Knoppix 6.4.4 into an ancient Compaq desktop (tower) with a 400 MHz CPU and 192 MB ram and an old RAGE graphics card. The result is a working 'almost-debian' system that is working quite well (slow of course, but it works). After
```
sudo apt-get update
sudo apt-get upgrade
```
it still works nicely.

I suggest that you pick some other light-weight distros and test them live now (I think live testing is available), since you will have less time later on.

- Linux Mint 'standard edition' and debian
- #! (CrunchBang)
- Puppy
- Debian Stable (not fancy, but stable, most debian-based desktop systems are based on Debian Testing)

Maybe you can also consider

- Fedora
- OpenSUSE
- MEPIS

But the complete list is long ...
[[COLOR="Red"]_http://en.wikipedia.org/wiki/List_of_live_CDs_[/COLOR]]("http://en.wikipedia.org/wiki/List_of_live_CDs")

---

### Post by sudodus on 2012-07-05
It is possible to move an installed Ubuntu system from one computer to another if you have not installed any proprietary drivers.

So actually an installed system can be as portable as a 'live CD or USB' system. You can clone it between hard drives, flash drives and it makes no difference if the drives are internal or external (USB, eSATA).

If your problem is with the installer, not the installed system (because you never get there), this might work:

1. Install Lubuntu to another computer or to a USB drive (HDD or pendrive). If you install to USB, disconnect the internal drive. Avoid proprietary drivers.

2. Clone the system if necessary until you can try to boot your Compaq Presario R3399CL laptop from USB or internal HDD.

---

### Post by joe needs help on 2012-07-11
I posted to this thread a bit earlier with a similar problem that I finally solved and thought it might help Curbuntu.  Here's what I posted to my thread:

Finally got the cd to fully boot so I could do a clean install of 12.04.

What fixed it:

Booted 12.04 from the hdd.
Turned off the wifi with the switch on the laptop.  Before I turned it off, the indicator light was on and I had a working wifi connection.
Re-booted with the cd.  All went well.

How I figured it out:

I changed the boot options and deleted the last part of the command line about quiet boot so I could watch (sort of, the text scrolls by pretty fast at times) the boot progress for problems.  I was able to catch an error about needing a file that I recognized that the wifi adapter uses.  Another 1 - 2 pages of text scrolled by after that error before a "Panic" error appeared and the pc hung.  Assuming the wifi adapter was the culprit I re-booted and went into the BIOS settings and disabled the wifi adaptor.  The cd still wouldn't boot.  I rebooted and went back into the BIOS setup and re-enabled the wifi adaptor.  The only other thing I could think of to do was turn off the wifi with the switch as mentioned above, while 12.04 was running from the hdd.  Don't know why shutting it off that way worked when disabling via the BIOS didn't.

Hope this helps someone else.

Joe

---

### Post by Curbuntu on 2012-07-12
Hey, Joe --

Thanks for the suggestions, which I have tried to implement.  Unfortunately, this laptop's BIOS is so "dumbed down" that it doesn't have options for anything other than basic-basic functions.  Toggling WiFi in the BIOS is not an option.  Although it does make me wonder -- the physical WiFi toggle switch died ages ago.  Up until now, it hasn't mattered, because I could toggle WiFi from within Ubuntu.  Could this broken switch be part of the problem?  Eh, probably not, but I"m grasping at straws at this point.

Speaking of the BIOS, the laptop was upgraded to the F.35 version ages ago, and HP hasn't issued any further updates since 2005.

---

### Post by joe needs help on 2012-07-13
Curbuntu,

I just want to emphasize that an error message during the boot process is what helped me solve my problem.  But, it appeared at least one page before the last line of text and wasn't visible when the screen stopped scrolling and the pc hung.  I spotted the error message but wasn't able to read the whole thing before the screen started scrolling again.  So, I rebooted and took a photo of the screen to capture the message.  There is probably a way to scroll back up the screen, or save the text, or step through the boot process, but I don't know how.

The message told me I was missing two files.  If I knew how to add those files to the .iso file before burning the cd, the cd may have booted.  I'd be willing to try if someone posted a link on how to do that.  But, that was the problem with my machine, and we don't know what's wrong with yours.

There was another error message at the end of the text when the pc hung.  It was a Panic Error of some kind (I don't remember now).  But, it didn't point towards the wifi adapter.  At least not to a newbie like me.

My advice is to somehow read all of the text that is displayed during the boot process and see if there are any clues other than what appears at the end.

Hope this makes sense.

Good luck - Joe

---

