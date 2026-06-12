---
title: "Problems installing on an A7V880 System"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by LadFromWales85 on 2006-12-12
After the flawless installation on my main rig (NF4, X1900XTX), I decided to install Ubuntu on another of my PC's used by the family.

Asus A7V880 Mobo, VIA KT880 Chipset
ATi 9800Pro GFX
2x512MB Kingston RAM
Using onboard Marvel Yukon NIC (which works during install)
Using onboard Realtek sound

The system has a single IDE hard drive, which had two NTFS partitions, with 15GB or so unused at the end.  I ran the 'alternate' cd to install as the system didn't like starting X correctly with the Live cd (ATI card).  At the partition screen, I elected to let it partition for me.  It created another primary partition for /, and a logical partition, in which a swap was created.  Carried on with the installation to the end.  Grub saw the XP, I confirmed it correct, the installation completed etc.

Upon booting, Grub attempted to start, but it give me an Error 18.  Had a look round, and found that the error is something to do with the BIOS not being able to boot filesystems on partitions more than a certain amount up the drive.

As far as the XP cd was concerned, the whole drive was nuked, seeing it as 'Unknown' 75500MB free or something like that.  Downloaded a Knoppix Live CD, booted it in Fail-Safe mode, which allowed X to startup fine.  It was nice enough to see my Windows partitions, so I chucked what I needed to keep on a samba share on another PC, and nuked the drive with Darik's Boot & Nuke.

All fine so far, I put XP in, 15GB partition, created a 40GB NTFS once Xp was installed, that went fine.  At this point, I booted from the Ubuntu Alternate again, this time electing to partition manually.  I created a Logical partition, and put both the ext3 / and swap in there, making them hda5 and hda6.  Install went fine, it saw XP etc.

Now, Grub loads up fine, and gives me a bootlist.  If I boot into Ubuntu, I get the X doesn't display because I have an ATi card issue.  If I attempt to boot into XP, I'll see the XP loading screen for about half a second, and the PC reboots.  This even happens if I select safe mode, it just reboots a few seconds in.

It's safe to say that the users of this PC are now saying 'Linux sux' and 'Linux broke my pc, i hate Linux', so until they can get into Windows, they aren't going to like Linux :( They like their Sims 2 games :(

So, the question that comes out of all the above, is how can I get my Ubuntu installation to fire up X without any problems, and how can I get my XP installation to boot without resetting itself.

Thanks for any help you can give me :D

---

### Post by LadFromWales85 on 2006-12-12
Apologies for bumping if it isn't allowed this early :)

My thread seems to have vanished down several pages now, though I am sure there are people that do drill down a few pages to answer queries, I am eager to get my machine back to form :)

I've found that I cannot use the Windows Recovery Console to run chkdsk/fixboot/fixmbr.  At the point where it asks for the admin pass, it says it's incorrect.  It did the same thing before I nuked the drive and reinstalled earlier today.  It will not accept a blank password, or the password I set for admin.

Just ran the XP setup cd and proceeded to the point where you specify an install location.  The installer says 'Setup cannot access this disk', but it knows how large it is.  

I've come across some similar threads, but nothing that seems to pinpoint the problem and fix it.

It does sound as though it's the motherboard causing this issue, but I'd love a workaround, as I'd like the pc to be able to boot both Windows and *buntu.

Ideas anyone? :D

---

