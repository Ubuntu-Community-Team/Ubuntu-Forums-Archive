---
title: "Install partitioner only sees one SCSI drive? Where'd the other disks go?"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by SubGothius on 2007-05-05
**[COLOR="Red"]EDIT: Apparently this issue is not specific to SCSI nor PPC alone, as it also affected the respondent below on an x86/IDE system.[/color]**

I have three SCSI disks in my "OldWorld" PowerPC Mac, and I would like to spread my Feisty filesystem across two of them, as I had done quite easily when installing Edgy -- putting my / and /boot on one disk, and my /home, /tmp and swap on the other disk (shared with Mac file storage in its own partition).

However, the Feisty netboot installer is only showing one SCSI disk (the largest one, 9GB at ID:2 aka /dev/sdc) available in the partitioner; is there any way to make it see my other disks?  Some "expert" mode or F-key alternate console trick, perhaps?

FWIW, all drives show up perfectly fine in MacOS, as they did in Edgy during install and afterwards.  I'm really impressed so far by how much better the Feisty installer detects my HW and displays properly (Edgy had some ugly display issues), so I have high hopes in its potential for overall superiority over Edgy... if I can just get my partitions the way I want!

---

### Post by SubGothius on 2007-05-05
UPDATE: I finally discovered the "priority=low" kernel argument to engage Expert mode... and the install partitioner still only offers me the one, same drive to partition. Anyone?  Bueller? :-k

---

### Post by SubGothius on 2007-05-06
Still no takers on this one, eh?

It occurred to me that I could just partition my / and /boot on the one drive that shows up in the installer partitioner, then add the other partitions post-install...  except I wanted / and /boot on the *other* drive that isn't showing up during installation, and I only want /home, /tmp and swap on the drive that is available for install.
](*,)

---

### Post by vHaB on 2007-05-07
Having the same problem on an x86.

Strange thing is, I don't have ANY SCSI disks.  I have 3 IDE ones.  I am installing over a Fedora System, and one entire 160 drive is partitioned as /home.  That's the ONE drive I don't want to touch, ut it's the ONE drive that Ubuntu detects!

That drive is hdb under Fedora.  I want to install to the drive that is hda.

Anyone?

---

### Post by SubGothius on 2007-05-07
Good to know (erm, I *think*...?) that it's not exclusively a SCSI/PPC issue, since it's also happening on your IDE/x86 rig; perhaps this means there's a general solution, or at least a general bug we might report?  Is your 160GB IDE slave the biggest drive on your box?  I'm suspecting perhaps Feisty somehow prefers to install itself to the largest drive available, so it won't make any other drive available during install partitioning?

By this point, I'm wondering if I'll have to try physically unplugging the one drive it's recognizing, just to see if it recognizes the other drive that way, but that seems like such a kludge way to do it.  Surely the install partitioner can be made to recognize ALL drives present, since it worked that way installing Egdy? :roll:

---

### Post by SubGothius on 2007-05-08
Say, one question for ye, vHaB -- which type of installer were you using?  The netboot installer like I used, or one of the other methods (Live CD, Alternate CD, or .iso file on HD)?  Just wondering if this issue might be specific to the netboot installer or not...

---

### Post by SubGothius on 2007-05-13
By now I suspect my issue and vHaB's may be unrelated (rather than a general drive-detection issue), so I have taken this discussion [over here to the Apple PPC Users category](http://ubuntuforums.org/showthread.php?p=2650357).

By all means, if anyone has a notion why my Feisty system, now installed on the one disk available to me in the installer, is STILL limiting me to this one disk -- an Ultra SCSI Wide Seagate w/ an adapter to my built-in Fast SCSI-2 bus -- and why it might be detecting and then promptly offlining all my other SCSI2 devices during boot, please reply in that other thread.

---

