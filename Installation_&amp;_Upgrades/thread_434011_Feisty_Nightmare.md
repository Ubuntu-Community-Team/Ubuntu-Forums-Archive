---
title: "Feisty Nightmare"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by tmwes on 2007-05-05
Specs:  Athlon 64 dual core, 4 gigs RAM, nvidia 7600 w/ 512, 2 320 gig SATA drives, two monitors (22" widescreen DVI, 17" lcd VGA)


Live CD boots up fine, every time.  Yesterday afternoon I installed Fiesty alone on one of the 320 gig drives (Vista is on the other), and everything went fine.  Small problem when updating (kept freezing on capplets-data?), but got that squared away.  Activated the restricted nvidia drivers so I could try out Desktop Effects....seemed to work fine.

Then I rebooted and the resolution was fine on the widescreen, but WAY off on the 17"..and the 17" had the main windows.  Everything was cut off, couldn't type into terminal (unless I did CTRL ALT f1).  Tried several things; long story short I ended up hosing X (uninstalled nvidia drivers before disabling compiz; so I was getting a white screen after I logged in).

Tried to figure this out for 2 hours last night; then just figured that since I was getting nowhere, I might as well just reinstall since there really wasn't anything customized yet.

LiveCD boots, start install, create partitions....and once the install starts, it freezes every time.  Never the same %; sometimes on copying, sometimes on installing....every time I've heard a 'beep', and the progress bar just stops, and everything is frozen...no mouse, no anything.

Before starting this post, I'm checking for errors on the CD(none detected yet; after the check cd, does it automatically boot into the livecd...I probably need it to go to save video mode) and also burning another one; so I'll update if that fixed the problem.  But this is the same CD I installed with last night with no problems...

---

### Post by tmwes on 2007-05-05
OK; ran the CD check 3 times (3rd time put the xforcevesa parameter in so I could see the screens) and the CD was fine every time.

Trying the install for the nth time right now, will make a running diary here:

1.  Well, that was quick.  It froze as soon as I doubleclicked on 'Install'.  Rebooting now.
1a.  booting the livecd in safe graphics mode...success.  Spare CD just finished burning; should this crash I'll try again with the new CD
2.  Install opens this time..(/ = 20480 mb, /home = 199997 mb, swap 4096 mb), created user, all 7 steps done...clicking 'Install'
3. 5%...partitions formatting...check
4. 15%/...scanning files...check
5. growing%...copying files....up to 24%....27%....35%...46%...and THERES the beep...mouse still moves, though...bar at 47%.  Don't hear the CD spinning anymore...bar not moving....usually after the beep, the mouse freezes too but it has not this time.

I can still click on dropdowns...browse....open other windows....but the install is still at 47%.

Since the whole thing isn't frozen, I'll leave it up and running pending instructions from here.  Have to go out for a while, but if I don't get any tips here, I'll try again from scratch with the new CD I just burned.

---

### Post by tmwes on 2007-05-05
oh; and it gets worse.

I restarted (soft reboot) and took the live cd now...now when it gets to Grub it says 'Error 15'.  So I can't even get into Vista on this machine.

Be back in a few hours to sort this out....*sigh*

---

### Post by tmwes on 2007-05-05
trying new CD...going to have it check the CD before it gets into safe graphics...

CD check OK; live cd boots...

Install starts...

same partition info as above (same sizes; formatting both)...

this time I get 'the ext3 file system creation in partition #3 of SCSI5 failed, and it is locked up.

Will try again by deleting partition table and starting from scratch.

---

### Post by tmwes on 2007-05-06
New attempt...last night downloaded 2 isos...the gparted live cd, and the alternate install.

Booted with gparted and completely redid the partitions of the drive I'm putting ubuntu on...

Going through the text install now...

rebooting...

Grub works; sees Vista...

adding noapic command line...

taking an AWFULLY long time to boot...3 bars in

gave up, rebooting into recovery mode...

got to command line; sudo X...have a gray screen with an 'X' as the cursor.

rebooting again...removing quiet splash from boot line...

SUCCESS!!

Now going to try updates, get dual screen to work properly, etc.

No idea what my problem could have been (only been dabbling in linux for a few weeks), but if anyone could chime in that would be great.  Hopefully this thread can help those with similar issues...

---

