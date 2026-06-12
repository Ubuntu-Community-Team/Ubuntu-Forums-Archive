---
title: "And The Winner Is ..."
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-07-01
Don't ask me, I didn't know there was a contest going on.  But let me.04xplain just a triffle.

I somehow clobbered the install of 10.04 on the first partiton of my laptop drive.  I mean it was trashed, so that efforts to boot to it were essentially dead on arrival.  That's DOA for some of you out there.

Reinstall did not go anywhere, always coming back to the same hash, because I was trying to salvage what I had under /home.  I finally tried a route that I hoped would copy m essential files elsewhere, then opted to first wipe /home,, then do a reinstall with no format.  The idea was to see if theproblem actually related to /home or its contents.  Apparently not, same messed up mess, to it was something outside of /home that also got left behind if you opted not to do a reformat before install.

I've worked around this issue for days, and have another tread going about this.  But here is the really wierd part, the part that seemed to call for a new thread entirely.

There is an unbelievable amount of difference found between the contents of /etc/fstab with the previous installs and the new /etc/fstab that the new install produces.  For instance, look at the line for proc and the options selected for it.  Then on any reinstall, the installer adds another swap partition for each partition that was flagged as not to be used, but there it is anyway.  I mean these partitions were not to be used, but that is what it did anyway.

And as a clincher,the new version of /ewtc/fstab has no entry in it for the CDROM drive.

I mean, what the heck is going on here?  You might not note these little things if you did not have a reason for visiting /etc/fstab. mostly because things seem to pretty much be the same, but this is way out of line.  I rewrote all the entries in /etc/fstab to comply with what had been there in the old version, and it works as I hoped it would, but this just does not make any sense to me.

---

### Post by steveneddy on 2010-07-01
10.03 is out already?

Goin' to 7-11 for hot dogs! Anyone else coming?

---

### Post by oldefoxx on 2010-07-03
Sorry about the typo. Working this keyboard with the touchpad so close at hand is tough, and keeping an outlook for certain errors means I am likely to miss others.

Another problem looks like it showed up.  I wanted to copy a VDIs folder from my replaced hard drive to the new drive, this holding a couple of VDIs in it, and only one of the files inside copied.  No reason why the other was ignored or dropped.  Seems I've run up against this problem several times.

I've another desktop on hand, and a decision about which Ubuntu to use to replace Vista with.  I've enough drive space to go with one version now, and later to use another to get Vista off.  Were 10.04 LTS in better shape, it would seem the best choice.  But right now it looks like 9.04 is my best pick, because of the weird things coming to light with 10.04.  That, and the fact that instaqlling 9.04 before 10.04 works better from the angle of which version of grub gets used.  It would seem that grub 2 follows onto earlier grub versions better than trying to move from grub 2 back.  And the move back is what happens if installing 9.04 on a machine with 10.04 already installed, even if in a different partition or drive.

Besides, I need to get PS/2 mouse and keyboard to connect and work through USB ports, which is all that this PC has, and that turns out to be a lot trickier than expected.  I have several ways to do the hookup, and by elimination, I think I have one that might last a bit.

Noted on another thread. or actually several threads, 10.04 seems to have a problem with HID, meaning working a mouse and keyboard through USB isn't going to work unless you have HID on board.

Not sure what might be involved, but there are curious lacks, or apparent lacks, when working with Ubuntu.  For instance, how much RAM is installed.  What USB devices are attached, and whether accessible or not.  seems strange to have to turn off and on a USB device that is already attached and powered up, or disconnect and reconnect just to get the system to mount it.

Not thrilled with not having GUI usable by root or su either.  Lots of times the best you can do is use chmod or chown when needed through the terminal, then use user access to the GUI to do what should be simple jobs.

You know, something that the Windows world has done for a long time that might make sense in a situation like this.  In a single user, at home environment. you have to do everything, so why not have it arranged to do just that?  With Windows, there is a Home version you see, which means some wraps are off.  For business and academic roles, why even let the user be su?  That is what the staff there are for.  If you want a user to have su powers from time to time, then set a unique password for that user and just for that purpose.
This would be more the Professional version.

I think a problem with today's Ubuntu is tht it is trying to straddle the fence that stands between the two sides, and neither side can be entirely happy with the result.

---

### Post by hansdown on 2010-07-03
Hi oldefoxx.

Could it be the difference in The file systems?

EXT3> EXT4?

[https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Compatibility](https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Compatibility)

---

