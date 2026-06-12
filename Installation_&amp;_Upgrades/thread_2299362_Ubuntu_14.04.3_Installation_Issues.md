---
title: "Ubuntu 14.04.3 Installation Issues"
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by brandon39 on 2015-10-17
[COLOR=#111111][FONT=Ubuntu]Hello, hoping to get some help here... I've installed Ubuntu 12.04 Server on an old Lenovo/IBM machine that I have, and have had it up & running successfully for quite some time. My daughter needs a workstation for homework now, though, so I wanted to completely wipe this drive & do a fresh install of 14.04.3 Desktop. I booted the Live CD with minimal issues, but it hangs on the purple Ubuntu screen & doesn't seem to be doing anything. I never get to the point of it even asking me for any input. I read that pushing Alt+F2 would give some kind of verbose output, so here's what I'm seeing when I do that:
[/FONT][/COLOR]
[82117.099733] ata2.00: cmd a0/00:00:00:00:fc/00:00:00:00:00/a0 tag 0 pio 65536 in
[82117.099733]          res 58/00:02:00:00:60/00:00:00:00:00/a0 Emask 0x6 (timeout)
[82117.106728] ata2.00: status: {DRDY DRQ }
[82160.104046] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[COLOR=#111111][FONT=Ubuntu]
This has been showing up repeatedly, through several attempts to install. My research online has lead me to believe that this could be an HDD issue? I swapped another drive into the machine just to test, and the same errors showed up. It seems like it could also be a BIOS issue, and I've played with a few of those settings as well. A few of the other errors I've seen at different time while trying to install are as follows:[/FONT][/COLOR]

[82416.297068] blk_update_request: I/O error, dev sr0, sector 334224
MP-BIOS bug: 8254 timer not connected to IO-APIC
ACPI PPC Probe failed. Starting version 219
[COLOR=#111111][FONT=Ubuntu]
The latter two show up at the very beginning of the Ubuntu boot process... I also see intermittent messages about various tasks being blocked:

[/FONT][/COLOR]INFO: task *** blocked for more than 120 seconds.[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
After several attempts, I have now reached a point (by letting it run overnight to see what happens) where I actually seem to have a grub command line... any advice? Can someone help me finish this installation?[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-10-17
brandon39; Hi ! Welcome to the forum.

Does the " installed Ubuntu 12.04 Server on an old Lenovo/IBM machine" equate to raid arrays ? The desktop install does not have the tools to cope with raid.
```

sudo wipefs /dev/sda

```
 Note that you should not just trust me that that command is safe (even though it is), you should run "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets. <- No,(meta data was removed) my return:
> 
 wipefs: WARNING: /dev/sdb: appears to contain 'dos' partition table
 
where I had formally removed the raid meta data form my drive(s) .

[INDENT][INDENT]raid being but
[INDENT][INDENT][INDENT]one possibility
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-10-17
Does the Ubuntu live session load to a working desktop? From your post it is not clear if it does. If you are getting these errors from trying to run the live session you may need to run one or some of the F6 boot options such as nomodeset. In this wiki page go to the heading Changing the CDs Default Boot Options and look for section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The Ubuntu live session and the installed desktop session will have different needs than the Ubuntu server. I am thinking, video driver and monitor video settings. You do not give us the hardware specifications of that old Lenovo/IBM machine. They might give a further clue.

Regards.


[URL="https://help.ubuntu.com/community/BootOptions"]

[/URL]

---

### Post by brandon39 on 2015-10-18
Hello to you both, and thanks for the quick replies! There's no RAID on this machine... just two independent drives. They're actually on separate IDE cables (machine is from before SATA) due to length of cables & spacing inside the tower. Primary drive - which is the one that currently has Ubuntu Server 12.04 - is master (and only) on one cable, the secondary drive (the one I recently added for this installation) is the slave on the same IDE cable with the optical drive.

Sorry for forgetting to include my machine specs - a noob mistake of me, and my apologies... I'm running an old P4 at ~2.4Ghz, about a gig & a half of RAM (single channel since the memory sticks don't match), and the tower itself is a Lenovo NetVista 8310-47u. To answer your other question, no I can't even get the 'Ubuntu preview' or live session from the disc. I've tried all of the following command line installation args:

all_generic_ide=1 pci=nommconf pci=noacpi ide=nodma acpi=off noapic nolapic noacpi nomodeset

I know several of these seem redundant, I just wasn't sure which of them would work & which wouldn't... if I enter an invalid command, will it disqualify the entire install? Or would it roll forward with whichever version of these commands are syntactically correct?

---

### Post by Bucky Ball on 2015-10-18
Welcome. Continuing on from grahammechanical: When you get that purple screen, can you hit a key and get to the 'Try Ubuntu' options, etc.? If you can, then hit F6 and choose nomodeset. Continue.

If you can get to those options anyway, try the 'nomodeset' option first. That is the most common issue: graphics.

---

### Post by brandon39 on 2015-10-19
> **Bashing-om said:**
> brandon39; Hi ! Welcome to the forum.

Does the " installed Ubuntu 12.04 Server on an old Lenovo/IBM machine" equate to raid arrays ? The desktop install does not have the tools to cope with raid.
```

sudo wipefs /dev/sda

```
 Note that you should not just trust me that that command is safe (even though it is), you should run "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets. <- No,(meta data was removed) my return:
 
where I had formally removed the raid meta data form my drive(s) .
[INDENT][INDENT]raid being but[INDENT][INDENT][INDENT]one possibility
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Haven't seen any replies on this over the weekend, so wondering if maybe I need quotes in my replies... [COLOR=#000000]There's no RAID on this machine, just two independent drives. They're actually on separate IDE cables (machine is from before SATA) due to length of cables & spacing inside the tower. Primary drive - which is the one that currently has Ubuntu Server 12.04 - is master (and only) on one cable, the secondary drive (the one I recently added for this installation) is the slave on the same IDE cable with the optical drive. Any other ideas?[/COLOR]

> **grahammechanical said:**
> Does the Ubuntu live session load to a working desktop? From your post it is not clear if it does. If you are getting these errors from trying to run the live session you may need to run one or some of the F6 boot options such as nomodeset. In this wiki page go to the heading Changing the CDs Default Boot Options and look for section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The Ubuntu live session and the installed desktop session will have different needs than the Ubuntu server. I am thinking, video driver and monitor video settings. You do not give us the hardware specifications of that old Lenovo/IBM machine. They might give a further clue.

Regards.


[URL="https://help.ubuntu.com/community/BootOptions"]

[/URL]

[COLOR=#000000]Sorry for forgetting to include my machine specs - a noob mistake of me, and my apologies... I'm running an old P4 at ~2.4Ghz, about a gig & a half of RAM (single channel since the memory sticks don't match), and the tower itself is a Lenovo NetVista 8310-47u. To answer your other question, no I can't even get the 'Ubuntu preview' or live session from the disc. I've tried all of the following command line installation args:[/COLOR]

[COLOR=#000000]all_generic_ide=1 pci=nommconf pci=noacpi ide=nodma acpi=off noapic nolapic noacpi nomodeset[/COLOR]

[COLOR=#000000]I know several of these seem redundant, I just wasn't sure which of them would work & which wouldn't... if I enter an invalid command, will it disqualify the entire install? Or would it roll forward with whichever version of these commands are syntactically correct?[/COLOR]

> **Bucky Ball said:**
> Welcome. Continuing on from grahammechanical: When you get that purple screen, can you hit a key and get to the 'Try Ubuntu' options, etc.? If you can, then hit F6 and choose nomodeset. Continue.

If you can get to those options anyway, try the 'nomodeset' option first. That is the most common issue: graphics.

Hi, sure I've taken your suggestion & tried nomodeset... when I hit enter to 'Try Ubuntu', it shows:

    ..MP-BIOS bug: 8254 timer not connected to IO-APIC
    [COLOR=#000000]ACPI PPC probe failed.

Then continues with the ata2.00 output sequence that I wrote in the original post... these messages continuously show up in sequence. Also intermittently seeing:

    blk_update_request: I/O error, dev sr0, sector 263688
    SQUASHFS error: squashfs_read_data failed to read block 0x7c996e5
[/COLOR]

---

### Post by Bashing-om on 2015-10-19
brandon39; Hey ..

Still here, and still scratching my head what to do. I have a thought.
As this is a p4 - are all p4's - pae, sse and sse2 capable ?
14.04 Lubuntu has support for non-pae:
And as you are skimpy on ram ...

How about we try and boot (L)ubuntu in a live environment ( try ubuntu )

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Verify the .iso download - and the burn :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Let's see if a simpler 'buntu will boot .

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by brandon39 on 2015-10-19
> **Bashing-om said:**
> brandon39; Hey ..

Still here, and still scratching my head what to do. I have a thought.
As this is a p4 - are all p4's - pae, sse and sse2 capable ?
14.04 Lubuntu has support for non-pae:
And as you are skimpy on ram ...

How about we try and boot (L)ubuntu in a live environment ( try ubuntu )

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Verify the .iso download - and the burn :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Let's see if a simpler 'buntu will boot .
[INDENT][INDENT]just a thought
[/INDENT]
[/INDENT]


Thanks for your feedback - I had wondered if it might be a resource issue too. I don't know anything about pae or sse... did a quick google & it looks like an Intel technology? As far as whether my p4 is compatible, I don't know. I don't see anything like that in the BIOS anywhere though. I'd rather stick with Ubuntu if possible, even if I have to go back a few versions. Think maybe I should give that a shot? I just know Ubuntu is one of the larger & more common distros, so would prefer to stick with that for support, etc. Also, and especially, since my daughter will be using this box, I know that Ubuntu has a beautiful interface - I want to make it as easy as possible for her.

If rolling back, how far would you think I'd have to go? I did check the minimum system requirements before trying to install & it didn't look like it would be an issue... as we all know, sometimes minimum specs are off by a bit. :)

---

### Post by Bucky Ball on 2015-10-19
Your P4 should be fine, but with those specs, Lubuntu or perhaps Xubuntu for you (or perhaps Mate). I have a P4 running Xubuntu faultlessly (but I have upgraded to 4Gb of RAM). If you want Ubuntu, up the RAM.

Going back to an unsupported version of Ubuntu is a bad idea and leaves you pretty much on your own. You don't want to use an EOL release online as there are no updates to the system, apps, or, importantly, security. I wouldn't go there, but up to you. Unsupported versions are unsupported by Canonical and the forums. You may get a bit of help here, but no-one uses dead releases so ... 

Good luck. :)

---

### Post by mörgæs on 2015-10-20
> **Bashing-om said:**
> 
Are all p4's pae, sse and sse2 capable ?


Yes. 
In the very few examples where an old processor does not support one of those we will get an explicit error message.

---

### Post by brandon39 on 2015-10-20
> **Bucky Ball said:**
> Your P4 should be fine, but with those specs, Lubuntu or perhaps Xubuntu for you (or perhaps Mate). I have a P4 running Xubuntu faultlessly (but I have upgraded to 4Gb of RAM). If you want Ubuntu, up the RAM.

Going back to an unsupported version of Ubuntu is a bad idea and leaves you pretty much on your own. You don't want to use an EOL release online as there are no updates to the system, apps, or, importantly, security. I wouldn't go there, but up to you. Unsupported versions are unsupported by Canonical and the forums. You may get a bit of help here, but no-one uses dead releases so ... 

Good luck. :)

Ok that sounds good, I'm downloading Lubuntu now. Really strange, I tried installing Ubuntu 12.04 Desktop, let it sit overnight, and when I came back to it I see:

General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@ubuntu:~#

This is concerning - the HDDs should be fine (or so I hope), I'll give Lubuntu a shot & hope it goes well. I suppose the Server versions are less hardware intensive? I would have thought they would require more since they're built for serving several clients, but I guess without the GUI maybe this balances out?

---

### Post by Bashing-om on 2015-10-20
brandon39; Welp;

Let's boot up (L)ubuntu .. in "try ubuntu" mode and see how that goes.
It takes a lot more resources to run a GUI, than that of a file server.

Let's reduce to simplest terms
[INDENT][INDENT][INDENT]see what we can do
[/INDENT][/INDENT][/INDENT]

---

### Post by brandon39 on 2015-10-20
> **Bashing-om said:**
> brandon39; Welp;

Let's boot up (L)ubuntu .. in "try ubuntu" mode and see how that goes.
It takes a lot more resources to run a GUI, than that of a file server.

Let's reduce to simplest terms[INDENT][INDENT][INDENT]see what we can do
[/INDENT]
[/INDENT]
[/INDENT]


Ok so I have Lubuntu 14.04.3 Desktop in the DVD drive now... it first gives me an error about fd0 failure (I do have a floppy drive on this machine, but selected optical drive for boot). Then it brings me to the following:

-----------------------------------------------------------------------------------------------------------------------------
GNU GRUB version 1.99-21ubuntu3.9

(I need to select from this menu)
Ubuntu, with Linux 3.2.0-59-generic-pae
Ubuntu, with Linux 3.2.0-59-generic-pae (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

Use the [up] and [down] keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command-line.
-----------------------------------------------------------------------------------------------------------------------------

I'm sure we're all familiar with this menu - I know I've seen it before. It seems to be the menu that would always load when I would start my Ubuntu Server version. The DVD shouldn't bring me here should it? I'm wondering if it's not getting what it needs from the disc, and defaulting to an HDD boot?

---

### Post by mörgæs on 2015-10-20
14.04.3 should have a 3.13 kernel or newer. What you posted looks more like 12.04.

---

### Post by brandon39 on 2015-10-20
Yeah... I'm losing my mind over here. Now I can't even get it to boot from the CD/DVD drive. It's just defaulting to the Ubuntu Server 12.04 installation that I already have installed on the HDD. Not sure what to do - wondering about some BIOS settings... ugh, I just want Ubuntu! lol

---

### Post by Bashing-om on 2015-10-20
brandon39; Hey ;

Booting to the hard drive, with the DVD set as 1st boot priority, indicates there is no valid boot code on the DVD. Bios is looking for boot code, and not finding it on the DVD is defaulting to the hard drive .

You are burning to a DVD, yes ? As a CD is too small to contain the install image .
Did you verify the .iso file download ( md5sum  ) and burn at a low speed ?

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by brandon39 on 2015-10-20
> **Bashing-om said:**
> brandon39; Hey ;

Booting to the hard drive, with the DVD set as 1st boot priority, indicates there is no valid boot code on the DVD. Bios is looking for boot code, and not finding it on the DVD is defaulting to the hard drive .

You are burning to a DVD, yes ? As a CD is too small to contain the install image .
Did you verify the .iso file download ( md5sum  ) and burn at a low speed ?
[INDENT][INDENT]gotta be a reason
[/INDENT]
[/INDENT]


Thanks for your reply - yes, burnt to a DVD. I was able to verify the md5sum, and it seems to check out. I inserted the disc into my laptop, and everything looks right there too (autorun, wubi, all present...) I didn't modify the burn speed, guess I could give that a shot. Now would be the time for the optical drive to go out right? So frustrated!

---

### Post by Bashing-om on 2015-10-20
brandon39; Hummm ...

Got another box handy, see if that liveDVD boots in a different system ?

Sometimes it is hard to see a tree through the frustration - 
[INDENT][INDENT]for all the forest
[/INDENT][/INDENT]

---

### Post by brandon39 on 2015-10-20
Sure, I can grab my Windows Server & try booting that disc... FYI, when loading the DVD now I'm seeing the following:

-----------------------------------------------------------------------------------------------------------------------------
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: [prompt]
-----------------------------------------------------------------------------------------------------------------------------

I even re-burned the disc with verification & at the slowest speed possible to ensure proper burning... then also tried booting one of my old ubuntu (not lubuntu) discs just to be sure the drive itself wasn't the problem - it booted to the purple screen just fine. I'll try the WinServ & post back.

Lubuntu disc works fine on my Dell PowerEdge 830... Ubuntu disc works fine on the original Lenovo machine. Doesn't seem to be an issue with the actual CD/DVD drive since the other Live CD works on that machine, and doesn't seem to be an issue with this Lubuntu disc since it works fine on another machine. Any ideas from anyone? I'm stumped.

---

### Post by Bashing-om on 2015-10-20
brandon39; Well ......

How bout:
Boot the liveDVD of Lubuntu:
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works in the live environment we can make it work in the install !..
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter

[INDENT][INDENT]ad a way forward
[/INDENT][/INDENT]

---

### Post by brandon39 on 2015-10-20
I'll try that when I can get the liveDVD to load... it won't load right now though on that Lenovo box. Any other ideas on what I can do to get it to load?

---

### Post by Bashing-om on 2015-10-20
brandon39; Yuk .

Nope, as:
the DVD will boot on other systems ;
other DVDs will boot in this box ;
not even booting to the splash in this box ;

All I can come up with presently is try a different brand DVD, see what then happens when attempting to boot from it ?

I too would like to be enlightened on the happenstance .

[INDENT][INDENT]just goes to show
[/INDENT][/INDENT]

---

### Post by mörgæs on 2015-10-20
Booting from CD is more reliable than DVD.
Have you tried the [minimal ISO]("http://cdimage.ubuntu.com/lubuntu/daily/pending/")?

---

### Post by yawanathan_israel2 on 2015-10-23
Hello,

I have been reading your issue, and something I would like to suggest.

1. Check the cables to your dvd, if possible replace them.
2. If you have your dvd slaved to a hard drive, Can you separate them? 
3. If possible replace the dvd drive with another one and see if you get the same error.
4. Can you update the bios on the motherboard?
5. Also if possible change out the ram.

Sometimes you have to get down to the common denominator and find the root cause. Only then will you be able to resolve the issue.  It may seem silly, but I believe the issues could be
A. The age of the system
B. Hardware could be bad
C. Motherboard bios and chipset may be too old?

I would definitely start with changing the DVD drive and separating it from the hard drive if it is slaved. It may not resolve the issue, but it would at least take that out of the loop of being a issue.

As a last resort, Burn a copy of one of these and see if they have issues installing, at the very least it would rule out hardware issues. PCLINUXOS, Linux Mint, SolydXK or even Fedora.

Thanks
Yawanathan

---

### Post by Bashing-om on 2015-10-24
brandon39; Hey .....

A request to know how it is going . so long as it is your desire to have 'buntu, we will not leave you high and dry.
We will finger out something.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

