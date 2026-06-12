---
title: "Win users Stop!!! Do not install UBUNtu YET"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by fdrake on 2012-12-24
Windows vista/7/8 users .....  Stop it!!
You want to install ubuntu maybe a dual boot? that's great. But don't try anything before making sure you have a win 7/8 installation cd. [COLOR="Red"]**You don't have the win installation cd**[/COLOR] but you have a recovery partition? [COLOR="Red"]WELL IT'S TIME YOU MAKE A RECOVERY DISK[/COLOR]!! before you attempt any installation/resizing and so on....  it seems that a lot of the ppl having issues with partitions in the forum do not have an installation/recovery disk of their system.  Make yourself a favor.

 Note: I am reffering to the windows version after xp! xp mbr can be rebuild with lillo and othe linux programs which makes it easy..

---

### Post by darkod on 2012-12-24
Vista/7/8 MBR can also be rebuilt with lilo in case it's installed in legacy bios mode (lots of todays win7 and win8 come in uefi mode).

The "windows MBR" is just simple code that fires off the partition with the boot flag on it, nothing more. Lilo can install generic MBR that does the same and it will work on any windows version except uefi.

But you are right, since computers today come without windows install media (thank MS for that) it's best to create a set of restore DVDs and then you can even delete the restore partition and use that space more efficiently instead of just sitting there.
You can also create backup with the built in windows tool, or any third party software you prefer, which can restore your system the way you had it, not the way the factory sent it. That's a much better option than the factory restore.

---

### Post by kurt18947 on 2012-12-24
I'm not sure if this is a good idea or bad but I installed windows, removed shovelware, installed updates (pretty fast in geologic time:p) then created an image and verified it.  If need be, I can restore to that point in about 30 minutes or less.

---

### Post by BBQdave on 2012-12-24
> **fdrake said:**
> Windows vista/7/8 users .....  Stop it!!
You want to install ubuntu maybe a dual boot? that's great. But don't try anything before making sure you have a win 7/8 installation cd. You don't have the installation cd but you have a recovery partition? [COLOR=Red]WELL IT'S TIME YOU MAKE A RECOVERY DISK[/COLOR]!!

I have a lot of friends and family using Win 7, asking me about installing Linux. It seems there is an auto update program that is installing software - then Win 7 is unable to reboot. It hangs in a reboot recovery mode forever. Whether it be personal or work computers, I have many frustrated people ready to ditch Win 7. Anyone else seeing this? And fdrake, a recovery disk may be a better solution. My Wife's personal notebook took 4 hours to recover boot. The work IT folks, are just re-installing Win 7 when this happens, so people can get back to using their computer. Everyone is shutting off Win 7 auto update - but it turns itself back on. I wonder fdrake, if their is not an increased interest in Ubuntu installs because people can not get their Win 7 machines to reboot, and thus unable to make a recovery disk - so the jump on loading Ubuntu. Perhaps a lot of assuming on my part, but it is becoming a big issue for work and play - those using Win 7.

---

### Post by memilanuk on 2012-12-24
I recently got a new laptop (ThinkPad T530) that came with Win7 Pro installed.  I purchased this particular machine with the intent of installing Linux on it (dual-boot) from the start, and its not my first rodeo with Linux either so I had clonezilla on a usb stick ready to go.

Pretty much as soon as I verified the machine would successfully power on and had finished the setup/ user login steps, I turned the machine off and took a disk image to a NAS on the home LAN.

Then I booted back into Win 7 and went through the update-reboot-update-reboot-rinse-lather-repeat cycle.  And the <bleep>ing auto-index cycle.  That one about had me ready to fling my new laptop across the room.  A brand new machine, and they (M$) set the thing to force an auto index of the file system right way - not scheduled for later at night, or as a background process, but right away, right when people might want to *use* their nice new machine, but have to instead suffer through it pretty much grinding to a halt as the indexing process eats all available system resources.  Nice...

After that I installed all the little apps that make life bearable, and cleaned out the odds-n-ends market-ware crap like Norton, followed by defragging the snot out of the disk.  And then another system image, and then created system recovery disks (four DVDs) also.

All the above is probably good practice to follow regardless of whether you plan on using Linux at all, or intend to wipe Windows off the hard drive entirely.  At least you have something to fall back on, something that works, either way.

Only *THEN* did I start playing with Linux on the machine, using live CDs at first to verify hardware compatibility.

A person may not have the network resources or a big enough spare/external drive to do a complete system image before attempting to install Linux, dual-boot or otherwise.  But those who don't even attempt to make recovery disks or anything, and then complain when things go wrong and they have a system that won't work right in Linux and *can't* be restored to Windows... don't get a lot of patience from me, sorry.

---

### Post by orb9220 on 2012-12-25
Yep ran into this constantly last 20 years fixing computers. 
People will not backup their so called "Critically Important..Can Not Afford to Lose" Data. 

And then get mad when I can't recover it for them. 
Or mad because to recover if possible is another $75-$100 for labor hours trying. 
When they could have bought a usb external and saved all that themselves.

Always Backup everything before sacrificing the Little Pixies to the Fires of Ubuntu!

---

### Post by Elfy on 2012-12-25
I resemble that remark :|

:)

---

### Post by grahammechanical on 2012-12-25
We might also add:

If you decide to remove/delete Microsoft Windows and replace it completely with Ubuntu, do not ask how to get Windows back because you have changed you mind. Don't remove Windows unless you can do a new installation of it.

---

### Post by orb9220 on 2012-12-25
Elfy don't worry we all resemble that. As even I forget or put-off doing it from time to time that came back and bit me in the backport :-)

Yep good point grahammechanical about knowing enough to save yourself. 
Way to many just start clicking things without a clue what they are doing. And refuse even to commit 10-20 mins a day learning something new about how their systems work. 

Or how important it is to have multiple backups of System OS critical disks available. And keep them in a spot where you can find them. Don't know how many times people squirreled them away and then have multiple brain farts trying to remember where they stashed them.
.

---

