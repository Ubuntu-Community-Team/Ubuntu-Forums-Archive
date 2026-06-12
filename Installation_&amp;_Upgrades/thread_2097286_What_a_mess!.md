---
title: "What a mess!"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2012-12-22
I've used Ubuntu for a number of years but have been away since about v10.  Installation used to be pretty darn straight forward but after trying every variation offered with 12.04-1 for half a day and getting nothing but a blinking cursor on a black screen, I give up.

---

### Post by darkod on 2012-12-22
That's usually video driver issue with nvidia. Try using nomodeset to boot the installation (or run live mode if that's what you are trying to do). You have more details here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

If you have any questions ask first. :)

---

### Post by deeppow on 2012-12-22
It isn't installed.  Blinking cursor and blank screen occur immediately after you tell it to install.

---

### Post by Bashing-om on 2012-12-22
deeppow; Hi !

By chance are you trying to install onto raid with the desk top installer ? The desktop installer does not have the tools available to cope with raid.
[INDENT][INDENT]just try'n to help <== BDQ
 
[/INDENT][/INDENT]

---

### Post by deeppow on 2012-12-22
I have a RAID array as part of my storage but I am not trying to install to it.

When it starts from the CD, I select the language then select the install option.  Then blinking cursor on black screen appears.  I guess it could be possible that it loses its mind due to the presents of the RAID.  ???

---

### Post by Bashing-om on 2012-12-22
deeppow;
Betcha that there is "metadata" for raid on that disk, and the desktop installer can not deal with it.
How 'bout downloading the server edition (mdraid tools) and install from that environment, or if raids no longer desired use the tools available with the server install disk to remove that "metadata"??

[INDENT]just my opinion <== BDQ

[/INDENT]

---

### Post by darkod on 2012-12-23
In most cases this is not a symptom of meta data. With meta data the installer should reach the partitioning stage, and in that step it doesn't show the disk that has the meta data as destination to install onto. But it doesn't stop right after you click Install.

I suggest you start with Try Ubuntu first and try to get into the live sesssion. If you can, there is Install icon on the desktop in there.

If you can't, using combinations of boot parameters can show you what is missing. I would try the nomodeset first, but the symptoms are different from the standard. I would give it a go still.

Also, try googling your exact model and see if the search turn out something. It might be the acpi option you need to use, like acpi=off, etc.

Usually this doesn't happen but unfortunately it seems there is some hardware bothering it.

One option you can try is the Alternate Install CD (different image). It still installs the same desktop OS but the installer is text based and it might work better than the GUI installer. However, you still have to note that even if the install goes fine in the text mode, you can still have some issues on first boot if the problem kicks in again.

PS EDIT: Googling a bit it seems acpi=off does help in some cases of blinking cursor. Use the link I posted earlier about adding boot parameters, and add acpi=off and try to boot in live session and install from there. I think acpi is mentioned in the link too.

---

### Post by deeppow on 2012-12-23
I had tried to use the live entry point for the same reasons you suggest but that ends the same way.

While it can be the RAID, Ubuntu has seen my RAID setup without problems since mid-2006 when it was created.

What about SSDs?  Win7Pro (main OS) and apps are on two separate SSDs, Intel 510 and Crucial M4 respectively.  These are SATA III.

---

### Post by darkod on 2012-12-23
Did you try the acpi=off as suggested in my PS EDIT in the last post (you might have not seen it since it was PS)?

SSDs should be just fine. I recently moved to a ssd and it works without a glitch. Further more, just yesterday I upgraded my board, cpu and memory, plugged the same ssd, and it fired away without even needing to touch anything.

And that includes graphics change since I moved from Athlon 4850e and board with integrated Radeon HD3200, to AMD A8-5600K which has integrated graphics in the cpu. Ubuntu worked right away.

It seems the default driver support is much better for ATI than Nvidia. Maybe Nvidia doesn't release the driver to the open source community, etc, can't explain it.

Even though you problem sounds more like the acpi than the graphics, I am mentioning this as ubuntu seems really resilient even to hardware changes and when already installed.
However, there is something that "doesn't match" in your system/board.

---

### Post by deeppow on 2012-12-23
Ya, tried both acpi=off and nomodeset, doesn't help.

---

### Post by Open and Sourced on 2012-12-23
Well I had that case when I was experimenting with the machine. The main cause was me being blundered to the fact that python runs much the applications in the terminal. 

No worries, just look at your meta data settings, and be sure to install some kind of driver. 

Nividia is a great one.

---

### Post by deeppow on 2012-12-24
It has taken me a day to recover from the mess Ubuntu made of my HDs and SSDs during the blink cursor on the black screen time.  Fixing problems wasn't that hard except I had no idea what was done and where it was done.

When 40% or more of the graphics cards are Nvidia, what genius decided to cause all the problems when installing Ubuntu with those running a Nvidia card? I really don't care how big a pain the a$$ Nvidia is with its drivers.  Trying to thin out the user ranks I assume.  I'm of a mind to trash Ubuntu, maybe in a few days I'll try again.  

How do I look for meta data and what to do with it?

---

### Post by Bashing-om on 2012-12-24
deeppow;
> How do I look for meta data and what to do with it?I have never gone hunting for the meta data. Software raid tools are in the package "dmraid"
those tools are available in the server editions of ubuntu. Another possibility is to install just that package
```
 sudo apt-get install dmraid
```instructions:
```
man dmraid
``` and run this terminal command:
```
 sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
```to remove the "meta data"[INDENT][INDENT]still try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by darkod on 2012-12-25
Actually, software raid is the mdadm package, not dmraid. And dmraid is included on the live cd, you don't need to add it.

For fakeraid (bios raid) it's usually dmraid that is used. But be very careful with your existing raid array (disks). If you run the dmraid command on those disks, they will be dropped from the array.

Otherwise, the command is as stated:
sudo dmraid -Er /dev/sdX

I am confused about one thing. Earlier you said the install process stops right after you hit Install (the blinking cursor appears). Do you mean immediately at the start on the main menu where it shows Try Ubuntu and Install Ubuntu?
Because if the process stops right after you hit install, I don't see how it could do any "mess" on your disks since the install process never even started. After you hit Install you have a number of options to select and only then it actually starts.

For nvidia usually nomodeset does the trick but you said you already tried that. And unfortunately, the linux community can't have control over what nvidia does with their drivers. Even though you say it doesn't interest you, the developers can't do what is not permitted for them, right?

Have you tried installing from the alternate cd? I'm not sure I mentioned it.

---

### Post by deeppow on 2012-12-26
> **darkod said:**
> I am confused about one thing. Earlier you said the install process stops right after you hit Install (the blinking cursor appears). Do you mean immediately at the start on the main menu where it shows Try Ubuntu and Install Ubuntu?

A second to two after telling it to install, I get black screen and blinking cursor.  I left the machine setting for a while and obviously it did something even though it didn't show any activity.

Trying to install with nomodeset doesn't help.  Nor does acpi=off. Nor do both at the same time.

---

### Post by Bashing-om on 2012-12-26
deeppow;

Not much I can add to darkod's advise. 
I would look at the disk from Gparted (live CD), see what partitions are present on that disk. Then try as darkod advises with the alternate install disk - text based installer - and iirc f2 gives an interactive interface and f4 are the install messages.

[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by deeppow on 2012-12-26
OK, took all drives (RAID and other SSDs) except the one SSD that has windows 7 on it to install a dual boot.  Plugged that SSD into both the SATA III port and then the SATA II port.  Always the same problem.

---

### Post by Bashing-om on 2012-12-26
deeppow;
Just a thought, as it is an SSD, is "Intel Smart Resonse Technology" A factor ?
These links may shed some light on the sloppyation.

[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2076602](http://ubuntuforums.org/showthread.php?t=2076602)
[INDENT][INDENT]i Just hope this helps <== BDQ

[/INDENT][/INDENT]

---

### Post by deeppow on 2012-12-26
That has high potential since I'm using IST tech.  In my case it isn't for RAID but allows SSD caching for each SSD to speed up their R/W's.

I'll take a look, thanks.

---

