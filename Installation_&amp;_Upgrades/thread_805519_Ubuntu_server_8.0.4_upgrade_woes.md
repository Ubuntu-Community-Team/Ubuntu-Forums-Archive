---
title: "Ubuntu server 8.0.4 upgrade woes"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by superdave8000 on 2008-05-24
I brought my server up from 7.0.4 to 8.0.4 tonight, and much is broken. I did the upgrades in two steps (7.0.4>7.1.0>8.0.4) via the do-release-upgrade tool. The upgrade to 7.1.0 worked fine; my samba shares even mapped through to my md array. However, the second phase blew a lot away...

For starters, I found that it changed my sd* device enumerations (or fstab); it wasn't mounting the right root drive, therefore nothing else was mounting, and I ended up at a maintenance prompt. My root drive is now at /sdb1, and I think it used to be /sda1. I went into fstab and changed the device UUID to "/dev/sdb1", which I thought wouldn't work (I couldn't get the UUID because vol_id wouldn't recognize the volume). This did work, however, at least to boot the OS. 

When I got to the console login, "login:", I typed root (CR). It said "bash: root: command not found". It then went to a "hostname#" prompt... weird, right? If I type a command, it gives me "login incorrect" and goes back to "login:"! I've tried many variations of input, but it always results in "incorrect login", and never runs a command. 

So I tried putty, which got me in. From what I could see, most basic stuff was running fine... except for samba and the md array. And another spare drive... I didn't bother to check anything else, because these few services are all I really need from the box. With the drives not mounting, and the fact that vol_id still can't find the UUIDs of anything but /dev/sdb1, it worries me that the drives might be affected.

I've searched around, but can't find much about this... except I think I heard something about upgrading the drives fixing someone's server 8.0.4 upgrade problems. I don't think that covers it all, though - for example, my fstab is a bit mutilated from re-enumeration (and missing UUIDs - I tried re-inserting them manually after the system was able to give me the UUID, but this broke the root mount, and I had to revert to using "/dev/sdb1" instead of the UUID)

So finally, here are my questions:
1. Is there some sort of quick-cure that might fix all of these symptoms? I mean, is there something simple I'm missing or not trying? 
2. Should I look into downgrading? I can't find ANYTHING on how to do this with Ubuntu server 8.0.4.
3. Is there a way to install (from CD) 7.1.0 over the top of the 8.0.4 install? I'm guessing this might help to keep all my apps and configs running with no repairs needed...
4. Should I just bail on this install, and start fresh? This involves a decent chunk of work, but I at least get to grab all of my config data first (assuming USB or scp works, I guess).
5. Is there much chance that my other drives got hosed? Does 8.0.4 change anything in the partitions? I would guess that it's simply having trouble with the drive drivers...
6. Is there anything I need to be careful of if I transplant this md array (RAID1, 500GB sata) to another install? Just being careful on this one...


Thanks for reading all of this - I imagine that not many people will be able or willing to reply, but anything that anyone can toss out might help. 

-Dave

---

### Post by Witling on 2008-05-24
My experience with 8.04 has been that when I try to login as root graphically I get the message "Up yours, Shorty. You can't log into root this way." I'm quite a newbie but I can't say that I care for machine or software system that doesn't let me do what I want.  No doubt there's a way around this but it isn't obvious.

---

