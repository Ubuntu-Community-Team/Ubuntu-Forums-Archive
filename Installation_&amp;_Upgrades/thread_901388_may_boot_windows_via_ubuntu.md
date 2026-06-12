---
title: "may boot windows via ubuntu"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by navaneethan on 2008-08-26
Friends i have updated my RAm 1GB ..and then i need to install windows xp and i have already ubuntu hardy ..XP doesn't install it shows the error "INVALID PARTION TABLE " 
May i chance to keep the files to XP via ubuntu?....
which file important for booting ubuntu?
please suggest some solutions.....

---

### Post by xravexheavenx on 2008-08-26
Well, M$ wants you to use their product and no others so they do not have a partition resizing function.  So, but up gparted and resize your ubuntu partition, create an NTFS in the free space and install there.  Of course, at that point you will run into MBR issues since M$ overrights any MBR.  Look up dual booting to get around that.  I have worked around that before but cannot remember for the life of me.

---

### Post by Sef on 2008-08-26
Put XP on your first partition or you may have problems dual booting.

> Well, M$ wants you to use their product and no others so they do not have a partition resizing function. So, but up gparted and resize your ubuntu partition, create an NTFS in the free space and install there. Of course, at that point you will run into MBR issues since M$ overrights any MBR. Look up dual booting to get around that. I have worked around that before but cannot remember for the life of me.


Download [URL="http://supergrub.forjamari.linex.org/"]Super
Boot Disk[/URL].

---

