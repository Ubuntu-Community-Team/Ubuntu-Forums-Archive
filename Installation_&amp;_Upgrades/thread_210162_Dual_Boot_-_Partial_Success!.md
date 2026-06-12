---
title: "Dual Boot - Partial Success!"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-07-06
I finally got Dapper up and running on my XP system. Unfortunately I made a couple of changes simultaneously on the last try, so I'm not 100% sure what made the difference. Actually right now I can't get XP to boot without making the NTFS partition active, but I'm happy just to be able to run Dapper right now. Anyways, for those still having problems all I can do is post what I ended up doing to get this far:

1. I deleted all the non-windows partitions using partition magic. I wanted to let the ubuntu partitioner do all the partitioning on blank unused disk space.

2. I re-downloaded the alternate-iso and confirmed the md5 checksum on it. I was having inconsistent problems with the installer so I think I might have had a bad iso to begin with. From what I've read, that is not entirely unheard of. I burned the iso at 4x speed this time.

3. After the installer came up I changed the resolution of the installer to the native resolution of my lcd monitor. During one of my several previous install attempts, it was crashing at x-server-xorg configuration so I thought this might help (not sure if it did anything). 

4. The install proceeded completely. I told grub to install itself on the 2nd partition of the 1st drive (/dev/sda2). 

5. Upon rebooting, it did nothing (booted neither XP nor linux) so I used a rescue cd with qtparted on it to set the /dev/sda2 partition to be active (the ntfs partition was active).

6. Again rebooting it brought up the grub menu (hooray!) but it still had the grub parameters wrong so I corrected them to be (hd0,1) and ubuntu booted (double hooray!!)

7. However choosing XP from the Grub menu gives me an NTLOADR missing message. That'll be next on my hit list.

I'm a linux newbie so I'm not sure if any of the above is useful to anyone but hopefully someone might find something they haven't tried. And don't discount step 2. If you're getting inconsistent install failures like I was, then a bad iso file is as likely as anything else.

---

