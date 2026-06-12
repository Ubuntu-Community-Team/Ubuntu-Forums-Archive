---
title: "Operating system not found"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by cyd2 on 2016-02-20
Hi all,

I'm trying to install ubuntu 14.04 64-bit on a laptop. The installation seems to be successful, but the only thing I'm getting when I boot the laptop from drive is a black screen with a message: "Operating system not found". I've tried several hard drives and they all give the same message, so it seems like something is just able to point to the right place while booting, but I can't find out what. I've tried several things, among which running boot-repair and pointing grub to the ubuntu installation manually.

I'm now trying to investigate the boot info log created by boot-repair, which is stored at: [http://paste.ubuntu.com/15143099/](http://paste.ubuntu.com/15143099/)
But I just don't have the knowledge to see what is out of order here. The sdb device is the ubuntu live usb I've used to install ubuntu with.

Any help is much appreciated.

---

### Post by Bashing-om on 2016-02-20
cyd2; Hello;

Looks good to me, should workie .
But, you are under a mis-apprehension in that the system does see that hard drive as 'sda' ( -s-erial -d-evice one - that 'a' says 1st) . and the output reads that ubuntu is installed to the 1st partition of said device, and the boot code is properly installed at the start of this disk .
You are running Intel for graphics and a driver ( i915 ) is loaded. Intel is well supported, and generally always just works !

OK, so we try and boot this box. Be aware that as only one instance of an operating system is installed, by default a boot menu will not be displayed and we tell the system we want that boot menu .
Reboot to bios setup, and set in bios to boot the hard drive as 1st boot priority; continue the reboot process and as soon as the bios screen clears depress a shift key to get grub's ( GRand Unified Bootloader ) attention. Do you now boot to the grub boot menu ?
Yes ? what results when you press the enter key to start the ubuntu operating system at the selected default option ?
Yes ? What results with -> advanced options and select a "recovery" kernel ?
No? Then we need to find out why you are not booting up to the grub boot menu !

[INDENT][INDENT]It ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by cyd2 on 2016-02-20
Thanks Bashing-om!

I could not get into grub with the shift key, so I used the boot-repair another couple of times to first install the grub legacy and after that to upgrade it to the latest version (not sure if the legacy step was necessary). After that it suddenly just worked!

This saves me the need to buy a new laptop =)

---

### Post by Bashing-om on 2016-02-20
cyd2; Good deal ...

The end result is what is the thing of importance. Glad you are up and running.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

That said, you do not have to be a stranger.

[INDENT][INDENT][INDENT]drop in here anytime
[/INDENT][/INDENT][/INDENT]

---

