---
title: "Fubar!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by OriginalGabriel on 2007-04-20
Wow, so ... I installed Feisty on an XP machine wanting a dual boot set up and despite everything having gone well during the install, I continually got an "Error 18" at boot up from GRUB.  Though it worked fine with previous installs of Ubuntu, somethings hosed with Feisty.

I dug around a bit and it seemed to be an issue with the fact that Thinkpads have the hidden partition with their own bootloader in order to access it.  Nothing I did would fix the problem and I was stuck with a non-op computer.  I tried using the restore CD's to format the drive and reinstall XP and restore the laptop to the default factory installs but, on reboot I got the GRUB error again.  I tried booting off the LiveCD and deleting all partitions except for the XP one and got the GRUB error again.  I tried using the restore CD's again since all other partitions were now gone and STILL got the GRUB error.

Now ... How the hell do I get rid of, or repair the MBR?  The CD's I have aren't the normal XP ones so I can't get into the console go that route ... Is there any means to do this via the LiveCD?

I'm a bit at a loss here.

---

### Post by jimrz on 2007-04-21
> **OriginalGabriel said:**
> Wow, so ... I installed Feisty on an XP machine wanting a dual boot set up and despite everything having gone well during the install, I continually got an "Error 18" at boot up from GRUB.  Though it worked fine with previous installs of Ubuntu, somethings hosed with Feisty.

I dug around a bit and it seemed to be an issue with the fact that Thinkpads have the hidden partition with their own bootloader in order to access it.  Nothing I did would fix the problem and I was stuck with a non-op computer.  I tried using the restore CD's to format the drive and reinstall XP and restore the laptop to the default factory installs but, on reboot I got the GRUB error again.  I tried booting off the LiveCD and deleting all partitions except for the XP one and got the GRUB error again.  I tried using the restore CD's again since all other partitions were now gone and STILL got the GRUB error.

Now ... How the hell do I get rid of, or repair the MBR?  The CD's I have aren't the normal XP ones so I can't get into the console go that route ... Is there any means to do this via the LiveCD?

I'm a bit at a loss here.

use your win cd to boot
choose recovery rather than install
the type "fixmbr" (without the quotes) 

this will restore your win bootloader and get your win working again. you will then need to (if you still want to) reinstall ubuntu, here is how I did feisty on my ThinkPads:

I just installed feisty on 2 Thinkpads using the "desktop" cd with no probs. T42 dual boot with xp - I chose "manual" partitioning and simply loaded feisty over my old dapper / + /home without touching either win or ibm partitions and grub gave no problems. my old 600x is fiesty only, so I guess it really does not apply here

---

### Post by OriginalGabriel on 2007-04-21
Unfortunately, Thinkpads don't come with the "normal" install CD but IBM's own rescue/recovery CD's which don't give access to the console so I can't run that.  I was going to go that route but I couldn't find anyone that had a "normal" XP cd.

I'm now running an old DoD hard drive scrubber to basically get my HD back to being completely blank.

As far as reinstalling, did you have the IBM hidden partition?  Everything that I've read points to the fact that since IBM has it's own bootloader on Thinkpads in order to be able to use the "Access IBM" button to access IBM's Rescue and Restore partition one needs to make a small (5mb) partition to load GRUB onto


> **jimrz said:**
> use your win cd to boot
choose recovery rather than install
the type "fixmbr" (without the quotes) 

this will restore your win bootloader and get your win working again. you will then need to (if you still want to) reinstall ubuntu, here is how I did feisty on my ThinkPads:

I just installed feisty on 2 Thinkpads using the "desktop" cd with no probs. T42 dual boot with xp - I chose "manual" partitioning and simply loaded feisty over my old dapper / + /home without touching either win or ibm partitions and grub gave no problems. my old 600x is fiesty only, so I guess it really does not apply here

---

### Post by jimrz on 2007-04-24
> **OriginalGabriel said:**
> Unfortunately, Thinkpads don't come with the "normal" install CD but IBM's own rescue/recovery CD's which don't give access to the console so I can't run that.  I was going to go that route but I couldn't find anyone that had a "normal" XP cd.

I'm now running an old DoD hard drive scrubber to basically get my HD back to being completely blank.

As far as reinstalling, did you have the IBM hidden partition?  Everything that I've read points to the fact that since IBM has it's own bootloader on Thinkpads in order to be able to use the "Access IBM" button to access IBM's Rescue and Restore partition one needs to make a small (5mb) partition to load GRUB onto

yeah, I still have the IBM recovery partition, though back when I first got the (even before loading ubuntu on it) windows tanked on me and the recovery partition did not do very well. I got a set of IBM recovery disks that did a better (though not perfect job of reinstalling win. so when installing breezy (and ever since, am using feisty now) I just loaded GRUB to the mbr, figuring that if i ever needed to re-do win again i would just use the recovery cd's for a fresh install, again.

---

### Post by OriginalGabriel on 2007-04-25
i initially installed feisty with grub going to the mbr but received a grub "error 18" and not even the ibm recovery cd's could fix it (i had to do a low level format that took 6 hours).  from everything i read, the "error 18" was due to the fact that thinkpads have their own bootloader.

> **jimrz said:**
> yeah, I still have the IBM recovery partition, though back when I first got the (even before loading ubuntu on it) windows tanked on me and the recovery partition did not do very well. I got a set of IBM recovery disks that did a better (though not perfect job of reinstalling win. so when installing breezy (and ever since, am using feisty now) I just loaded GRUB to the mbr, figuring that if i ever needed to re-do win again i would just use the recovery cd's for a fresh install, again.

---

