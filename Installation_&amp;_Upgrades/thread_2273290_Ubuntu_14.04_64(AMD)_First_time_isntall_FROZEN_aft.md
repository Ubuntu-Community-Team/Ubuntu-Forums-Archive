---
title: "Ubuntu 14.04 64(AMD) First time isntall FROZEN after login"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by Cody_Potter on 2015-04-11
[SIZE=7][B][COLOR=#00ff00][SOLVED][/COLOR]
[/B][/SIZE]

Im here because everything i searched online as a fix will not fix this im a new ubuntu user or atleast trying to this was my first time ever downloading ubuntu, i installed ubuntu 14.04 64 AMD from a dvd silly me decided to just delete everything and stick with ubuntu as the only OS. Well i got it all done did the install while connected to the internet but when i restart my computer i get to the login screen type my password and then i never see the side bar with the programs and my mouse disapears and i cant do anything. But right now im writing this help message from loading UBUNTU safe mode and as long as im in safe mode i can do anything. 

I searched tons of things online trying to fix this i tried going into safe mode and changing the graphixs driver to my nvidia driver then rebooted and still nothing.

I tried doing a few of the CNTRL + ALT + F2 sudo stuff i saw from a installation guide on reinstalling desktop,nvidia drivers,unity and a few other things.

Also when i went into safe mode and changed my driver to NVIDIA it has multiple ones to pick did i maybe pick the wrong one here are all the options.

Nvidia legacy binary driver-version 304.125 from nvidia-3040updates(propriatary) THEN

Nvidia legacy binary driver-version 304.125 from nvidia-304(PROPRATARY) THEN

Nvidia legacy binary driver-version 304.125 from nvidia-304(PROPRATARY-TESTED)


Also before ubuntu loads this message shows up on the screen
[0.218299]pnp 00:04: Cant evaluate_CRS:12298 and then
[0.536296] ACPI: [package] has zero elements (fffff.....)

Here are my computer specs
Ubuntu 14.04 LTS 64(AMD)
MEMORY: 2.7GiB
PROCESSOR: AMD Sempron(tm) 140 Processor
GRAPHICS: Vesa:MCP61-MCP61-85 .... NVIDIA GeForce 6150SE NForce 430 GPU
OS TYPE: 64-Bit
DISK:312.0 GB

PLEASE HELP IVE BEEN STUCK FOR 3 days trying EVERYTHING HUMANY POSSIBLE I DONT KNOW WHAT TO DO :(


[SIZE=4][B][COLOR=#00ff00]
> **9d9 said:**
> this is probably a nvidia issue
boot again in recovery mode, activate the network, select the terminal, then:

sudo apt-get purge nvidia*

this will let 'nouveau' graphic driver be the default one. At that time,  reboot in normal mode .  You might get a working system, then later you  will be safer to test again nvidia in case you feel better with it (but  'nouveau' works well nowadays)

OMG OMG OMG I don't know why this worked but this got me going....i  found this EXACT FIX from another website and i did it 4-5 times and it  never worked i think because he had 4-5 different things to do before  typing 

sudo apt-get purge nvidia*

but doing that and that only it worked!!!!

THANK YOU GUYS SO SO SO SO SO MUCH!!!!![/COLOR][/B][/SIZE]

---

### Post by dino99 on 2015-04-12
this is probably a nvidia issue
boot again in recovery mode, activate the network, select the terminal, then:

sudo apt-get purge nvidia*

this will let 'nouveau' graphic driver be the default one. At that time, reboot in normal mode .  You might get a working system, then later you will be safer to test again nvidia in case you feel better with it (but 'nouveau' works well nowadays)

---

### Post by Bucky Ball on 2015-04-12
You might also try booting the machine, getting to the kernel options/grub menu (reboot and hit shift after the manufacturer splash if you don't get one), highlight the kernel you want to boot, but hit 'e' to edit it instead of return.

Look for the kernel line that ends in 'quiet splash' or and combination of one or both of those words. After a space, add 'nomodeset', so it looks like 'quiet splash nomodeset'. Follow the instructions at the bottom of the screen to save changes and boot. Any different?

If that fixes, we can make the nomodeset option permanent. If the noveau drivers suggested previously work for you, then you could happily stick with that. Good luck. ;)

---

### Post by Cody_Potter on 2015-04-12
> **9d9 said:**
> this is probably a nvidia issue
boot again in recovery mode, activate the network, select the terminal, then:

sudo apt-get purge nvidia*

this will let 'nouveau' graphic driver be the default one. At that time, reboot in normal mode .  You might get a working system, then later you will be safer to test again nvidia in case you feel better with it (but 'nouveau' works well nowadays)

OMG OMG OMG I don't know why this worked but this got me going....i found this EXACT FIX from another website and i did it 4-5 times and it never worked i think because he had 4-5 different things to do before typing 

sudo apt-get purge nvidia*

but doing that and that only it worked!!!!

THANK YOU GUYS SO SO SO SO SO MUCH!!!!!

---

### Post by Bucky Ball on 2015-04-13
Glad it's fixed. Please mark the thread as solved using the second link in my signature. ;)

---

