---
title: "Organizing partitions"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-09-02
ATM I have the following partition scheme:
```
1. / --Reiserfs V3 --19GB
2. /swap   --ubuntu swappart --1GB(I know TOO MUCH)
3. NTFS    --windows resides --140GB(waaaay to much)
```

1. I was thinking of creating an EXT2 20MB partition just for my /boot.
What are the cons/pros? And how would this be accomplished since am worried about the changes /dev/hda? numbers.

2. ATM the NTFS partition is about 140GB. But am going to resize it since am gonna copy all of my files to /home. And thus am considering creating a new partition of 100GB  just for my /home, to ease the reinstallation process and such.
So I was thinking of putting my ACRONIS DISK DIRECTOR CD in drive and then shrink NTFS to create a 100GB REISERFS partition! Afterwards boot to UBUNTU and move everything from /home to the newly created partition. Afterwards I would add the following in /etc/fstab:
```
/dev/hda?	/home reiserfs	noatime	0 1
```
Would this be correct procedure for point 2?

Here's a screnny of what I would do in ACRONIS:
[ATTACH]15189[/ATTACH]
What do U think?
btw. Bear in mind that I still have to clean the NTFS partition

---

