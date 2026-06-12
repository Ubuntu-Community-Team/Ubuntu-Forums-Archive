---
title: "Not booting after 13.10-&gt;14.04 upgrade (full disk encryption)"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by G988 on 2014-04-19
Here's what I did:
1. Original installation was Kubuntu 13.10 choosing the full disk encryption option
2. Prior to upgrade I took a full disk backup with Redo (redobackup.org)
3. Upgraded 13.10 to 14.04 - left the PC as it said it would take over an hour.  When I returned approx 2 hours later there was just a desktop wallpaper (not mine, I assume 14.04's default) but it seemed to be frozen. No mouse pointer, no windows. So rest the PC, but there were a lot of errors scrolling up the screen.  Clearly something catastrophic happend with the upgrade so....
4. Restored full disk backup with Redo.  So I should now be back to my 13.10 installation but it won't boot.  The PC goes through its normal BIOS screen and then resets going to the BIOS screen again, reset, bios, reset, bios.  It keeps in this loop forever.  So there's no grub error or any other error message to report here.

As I took a full disk backup with Redo it is supposed to include the MBR, so I was expecting the restore to work.  I've also tried the first Redo backup I took of this setup back in November, it's a backup I know I've restored in the past to test the restore process and it worked back then, but now it gives the same BIOS-reset loop problem.  Has something become corrupted that isn't included in the backups? Perhaps I haven't been backing up quite as much as I thought.

Where I am now:   13.10 has been restored to the point just before the upgrade.  I tried the Boot Repair Disk ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) which didn't seem to make any difference.  Here's a report immediately after the restore, [http://paste.ubuntu.com/7284658/](http://paste.ubuntu.com/7284658/), and report when I asked it to perform it's "Recommended repair", [http://paste.ubuntu.com/7284793/](http://paste.ubuntu.com/7284793/).  It warns me at startup "/boot detected. Please check the options" but I don't see any options that obviously need changing, although I'm no expert on boot configs so I could be missing something others will think is obvious.  

If I choose the "Restore MBR" option it refuses to work because it complains about the encrypted file system and wants me to decrypt it first.  That sounds like a big job (particularly to get it re-encrypted again afterwards) but I'm not  convinced this is the right path to go because the reports suggest there is an MBR.  With my novice's eye, the only thing in the reports that look suspicious to me is it says "core.img is at this location and looks in partition 94 for ." whereas other examples I've seen on this forum say it's looking for something other than ".", I think "/grub" was one example I saw.

Any ideas on what to try next appreciated.

---

