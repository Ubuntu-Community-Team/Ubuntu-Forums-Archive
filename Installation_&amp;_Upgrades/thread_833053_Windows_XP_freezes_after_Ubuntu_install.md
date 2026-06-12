---
title: "Windows XP freezes after Ubuntu install"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by QmQ on 2008-06-18
Hi

I hope this is the correct subforum for this topic.


I have an old (P3 800MHz, 320MB RAM) laptop on which I was running XP for a few years with on problems. I've decided to install Ubuntu 8.04 there as I've always been quite fond of this distro (using it on a different computer). I resized my HDD using GParted LiveCD and got 13GB for Ubuntu. After the process I have booted XP with not a single problem (to check if all's well). So, happy that everything is fine I rebooted with Ubuntu CD and installed the OS. Also here everything went OK - I now have a working Ubuntu system with the newest updates and all the fluffy stuff. However a problem arose - XP stopped working and I still do need it.

In GRUB after selecting XP the normal loading screen shows up. That's the one with the blue 'moving bar' in the middle, below the XP logo, black background.
And after a while the bar freezes and the computer is dead :(

I've tried Safe Mode (which works) and running scandisk and such but still the same - halt upon loading.


I've searched this forum and googled a bit but with no good result. It looks like a XP+Ubuntu issue for before installing Ubuntu everything was fine. Also the fact that Safe Mode works indicates that XP is "quite" OK.

Any ideas how to revive my XP?


Best regards,
QmQ

---

### Post by mostlyGood on 2009-08-25
I have the same issue. My computer freezes a couple minutes after booting XP. I can launch programs but inevitably it freezes and will not take any mouse or keyboard input.

I have also had a couple motherboard freezes before booting into grub.

In 2.5 years the computer has never done this but it started about a week after I installed Ubuntu.

Ubuntu and XP are on separate drives and I have cloned and replaced the XP drive and get the same result.

Ubuntu just works.

ANY ADVISE?

---

### Post by Mark Phelps on 2009-08-26
There's no apparent reason why installing Ubuntu, or any other Linux distro, should suddenly cause problems with XP -- even though you both are experiencing that.

Since both machines work when booting into safe mode, about the only thing you can do at this time is the following:
1) Open a command window and enter "msconfig"
2) When that opens, go to the startup tab
3) Disable ALL the startup entries, reboot -- regular mode
4) If the machine no longer hangs, it's one of the startup entries doing it.  To figure out which one, you'll have to repeat these steps, re-enabling one entry at a time and rebooting.

Yeah, it's tedious, but without any error messages, it's the only way to see if it's a startup entry problem and which one.

---

### Post by Neill78 on 2009-11-12
I am experiencing a similar problem. I have had Hardy on my PC for about a year now with no problems, but since upgrading to Intrepid (through the Upgrade Manager) the other day Windows has suddenly started freezing up. I haven't changed anything else in my XP setup.

I notice that XP is likely to freeze immediately after finishing boot up if I have Restarted from Ubuntu. If I Shut Down from Ubuntu XP doesn't seem to lock up.

I will mess around with msconfig and see what I can do.

---

### Post by wilee-nilee on 2009-11-12
So with a MS system and the infections that it is exposed to basically because most are written to run in a MS setup. There are many trojans, malware, rootkits, and viri...etc that are designed to disable key functions so that they can do their dirty work. As Mark Phelps suggested there is no cause and effect with the Ubuntu install, there is something wrong with the XP. You have several options here, you can reinstall the XP and have a clean system, hopefully without any rootkits stuff,or you can run a repair mode. Also you can and this is what I would do is get some of the better AV scanners and have the system scanned with them and see if you have infections that your regular AV software is missing, here are two that I use that can be installed and run while your live versions of a AV program runs. These two find stuff that McAfee and Norton both either miss or M/N have been disabled by a infection.
[http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
Choose the free version and update the data base when installed and whenever you scan, and always do a full scan.
Here is a excellent disc cleaner just watch out for the registry authentication portion, like any scanner whether for infections or registry you want to look at whats being removed.
[http://www.ccleaner.com/](http://www.ccleaner.com/)
If you don't have a live running scanner Avast has a fee home version that is very good, and you can have avast and the two others.
[http://www.avast.com/eng/avast_4_home.html](http://www.avast.com/eng/avast_4_home.html)

I would suspect infections and or hardware problems as well as inherent program problems, but if it was me I would back up the XP you want to save and scan it with these clean it up or reinstall or repair.
MS also has it's own AV software that is free and can be run along side all the ones mentioned in this post.
[http://www.microsoft.com/Security_Essentials/](http://www.microsoft.com/Security_Essentials/)

Last of all always run XP or any MS software in everyday use as a limited account, the administrative is for updating and adding software and controlling networking and should not be used on the net otherwise, unless fully protected, which is hardly possible.

the freeze ups may be as simple as as to much auto-saved files that can be cleaned with the built in disc cleaner or the one I post the link to, and having the browser clean out stuff upon closure, to prevent the auto save stuff. So this along with possible infections and a borked setup leaves a lot of variables. Of course there is the defraging that should be done as well.

---

### Post by mostlyGood on 2010-02-17
Apparently my issue was the motherboard. The problem continued with a fresh install of XP. Not sure exactly what could have caused it but I am suspicious that Ubuntu may have had something to do with it. Maybe somehow overheated the chipset or something? I am not accusing because I don't know enough to have any certainty I just find the timing very coincidental.
 
Something else that is interesting is that the board only frooze before going into Grub or after running XP. It never froze in Ubuntu. 
 
Anyway, I replaced the motherboard "XFX nForce 680i LT" with "Asus P5N-T Deluxe Motherboard - NVIDIA nForce 780i" and have gotten everything worked out.

---

