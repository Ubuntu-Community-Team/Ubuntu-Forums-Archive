---
title: "Upgrading from Flight 5 to Beta 1"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by Kruncher on 2006-04-22
A little while ago, I installed Ubuntu on the same hard drive as Windows was installed.

I have my 120GB partitioned this way:
18.63GB for windows /media/windows (NTFS)
486.34MB for swap
23.28GB / (EXT3)
23.28GB /home (EXT3)
46.12GB /media/shared (FAT32)

How can I upgrade JUST / with the new Dapper Beta 1, I don't want to lose any data on the other partitions.

From my memory, the ubuntu partitoner step formats every partition.

Any help would be great, thanks.

P.S. this can be using either the live or the install cd (tho I would prefer instructions for the live version as that's the disk I have burnt.)

---

### Post by Killeroid on 2006-04-22
hey,I think yo can do so easily from the command line "gksudo -manager -d"  More info can be found in the ubunt wiki.(mch help,I know)

---

### Post by Kruncher on 2006-04-22
Yes, I know about that method.

I can't do it that way because I have 56K :(

I can download the cd and burn it at work tho, so that is what I'm going from.

---

### Post by Sef on 2006-04-26
> From my memory, the ubuntu partitoner step formats every partition.

Not true.  When I reinstall Ubuntu, I just delete and reinstall the root and swap partitions.  The others I leave alone.  (Note: sometimes, just deleting the root partition will work just fine.)

---

### Post by openmind on 2006-04-26
Just my opinion, not looking for flames or anything, but I would wait for Tthe release on June 1st. The Beta is a step backward from flight 6 in many areas, (Printing, Samba, WiFi). Hopefully it'll all be fixed by june 1st.

---

### Post by Sef on 2006-04-26
> The Beta is a step backward from flight 6 in many areas....

From a security stand point, the Beta is more secure.

---

