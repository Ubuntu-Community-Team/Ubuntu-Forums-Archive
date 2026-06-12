---
title: "Upgraded to Kubuntu Noble: partition is always full"
date: 2024-04-25
forum: Installation &amp; Upgrades
---

### Post by MarcoPau on 2024-04-25
Hi there, have just uograded and thou I keep purging packages, cleaning apt cache and such, partition stays full.

Is there anything I could do?

Can't even install small utility apps for cleaning, but I assume they won't do much.

Is this a known bug? Got any hint?

Thanks a bunch!

---

### Post by Bashing-om on 2024-04-25
MarcoPau; Hello

Show us how things look:
post back the outputs of terminal commands:
```

df -h
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.

[INDENT]6 pounds of sugar in a 5 pound sack ?[/INDENT]

---

### Post by Rubi1200 on 2024-04-25
Have you checked whether the logs are filling up?

For example: 
```
du -h /var/log

```

---

### Post by MarcoPau on 2024-04-29
Hey guys, thanks for helping out!

Found out it was Thunderbird that was creating a new huge profile directory, since I have quite many email boxes being downloaded. TB has been "migrated" to snap with Ubuntu Noble and it changed a few things messing this up. 

Fixed it by erasing the content of xxxxxx.deafult directory and pasting the old yyyyyyyyy.default content in there.

I also found out there is a huge thunderbird ZIP file in there, anybody knows what it is about? 

Cheers everybody!

---

