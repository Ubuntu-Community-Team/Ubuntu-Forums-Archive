---
title: "new hard drive installed, cant load Ubuntu"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by wastew on 2006-11-01
Having an old Compaq Presaro 1200, intel celeron 700mhz, 60mb ram I gave that to my father in law for email and light internet. 
The original 10gig hard drive went out, it would not recognize an operating system (win me) at start up. 
Replaced it with a new 60gig. Not having an operating system, figured this is a great time to use Linux.
After I replaced the hard drive, started it up with the Ubuntu 6.10 disc, the menu comes up ok, so I select the first choice of - start or install Ubuntu.
It loads the kernel, then scrolls through various driver loads settings and checks for a short time and states the f
adding live cd users 
….(other stuff that I wasn’t able to write quick enough)
setting host name
Setting up keyboard
Configuring x
Then the screen with those graphics goes away. The cursor goes up to top left in what looks like a DOS screen.
Then I no longer hear the cd running after about 15min, and the cursor still blinking-and will not do anything further.
I ran the memory test for about 1.5 hr, and never showed any error
Press escape nothing happens at all
Being new to this all, I’m sure I ‘m doing something wrong. Any ideas?

---

### Post by NetworkGuy on 2006-11-01
My first thought on this is:  Can your old Presario 1200's BIOS support a 60GB drive? 

If so, you may want to try using the alternate install CD.   This will install Ubuntu directly without having to go through the live cd startup.

---

### Post by confused57 on 2006-11-01
With only 60 mb ram, you wouldn't be able to run Dapper or Xubuntu...you probably need at least 256 mb(128 mb may be enough).
If you have an internet connection, you could do a server install with the alternate cd, and do a minimal install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

You'd need at least 256 mb ram to even run the desktop live cd.

---

### Post by wastew on 2006-11-02
thanks for the input

looking at the shops around here, 60gig was the smallest to be found, I was told, by where I bought it, it would be ok, and it does recognize it when it was going through the partition process as noted below

you make a good point about the memory, I knew it was short, and trying to get by on the cheap-I added an additional 256mb into the available slot last night. It is rated for a max 320mb, per info at the Compaq site. Snapped it in and rebooted it a few times, but it still reads as 60mb. I did the memory check on the cd and it also noted 60mb. 
So some reason, it isn’t recognizing the additional memory.

I down loaded the alternate install cd, and installed per the walk through at 
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
Without an internet connection, since this computer only had dial up (certainly I expect to change that soon)
It does the install under low memory
I did not partition as he outlined, since there is no other operating system on this new hard drive. I instead selected  - Erase entire disk: ID1 master (hda) – 60 GB ST9681

It seems to finish the install ok, ejects the cd and asks me to reboot
It restarts, and checks almost everything off as ok, except there are two error lines as noted below after the following

*Starting basic networking… (ok)
*Starting kernel event manager…(ok)
*Loading hardware drivers…
17179591.236000 vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! – upgrade BIOS or use force=1
17179591.280000 via686a 0000:00:07.4: base address not set – upgrade BIOS or use force_addr=0xaddr

*Starting PCMCIA services…(ok)
*Loading manual drivers… (ok)
*Checking root file system… 
/dev/hda1: clean, 19381/7307264 files, 333121/14609101 blocks

*Checking all filesystem…(ok)
*Configuring network interfaces…(ok)
*INIT: Entering runlevel: 2
*Loading ACPI modules… (ok)
*Starting ACPI services… (ok)
*Starting system log… (ok)
*Starting kernel log… (ok)
*Running local boot scripts (/etc/rc.local)  (ok)

Unbuntu 6.06.1 LTS unbuntu ttyl

I login and password ok, then I don’t know what to do with the next

username@hostname:~$_

so I guess my two prime concerns are how do I start the operating system from here, and why is the memory not showing up right?

Thanks for any help

---

### Post by confused57 on 2006-11-02
Assuming the new memory is compatible with your mobo, maybe you could switch the memory cards around, possibly putting the higher mb memory card first.

You must have done the server install...I don't know how to get dialup working from the console, in fact, it's difficult from the GUI, depending on your dialup modem.

If you can get all your memory recognized, you could do an install of the complete OS with the alternate cd.

Sorry, but I can't help you with the error messages...I'm sure there's someone with more experience who will be able to.  Good luck.

---

### Post by wastew on 2006-11-03
i was able to load Xunbuntu alternate install, and i now have an operating system - YEA!
i'm guessing Unbuntu wouldn't load because of the short memory - 
so now i'm off to figure out why the memory upgrade isnt being recognized
thanks

---

