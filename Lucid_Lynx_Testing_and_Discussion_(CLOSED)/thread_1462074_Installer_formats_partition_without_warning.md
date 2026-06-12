---
title: "Installer formats partition without warning"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Berniebln on 2010-04-25
Hello,

I had Karmic on my pc, with "/" on one partition and "/home/" on another. Both were ext3. Furthermore, I had a huge ext3 data partition mounted to /media/Data.

I wanted to upgrade from Karmic to Lucid by formatting my root partition, installing the system there and after mounting my home-partition into "/home/" again.

Using this procedure, I successfully upgraded from Jacky to Karmic.

This time, I was doing it again, and then, knowing just a little about ext3 and ext4, I thought "Why not mounting the ext3 home partition as ext4?" On Wikipedia, I read that even if not converting to ext4, one can can have littel performance boosts. Well, don't know if it's correct, but that's what I thought :)

So, I chose "Use partition xxx as '/home/', as ext4 partition, without formatting."

I'm pretty sure I didn't check the "format" checkbox, but I'm not sure if it was set automatically by the installer after I pushed okay (even if it was, one could easily oversee that, since the status check box of items in the partition list which are not selected is hardly to see, just a note about the accessibility :))

Well, what happened then was that it formatted my home partition with ext4, leaving it blank after, with no data on it any more. I guess that is the time when one is paid back the time invested into setting up a good backup script :P

Still, I think users should be warned, like "You are changing the type of the filesystem for this partition and therefore, the filesystem will be formatted and all data will be lost." Even if it that might be clear for e.g. ntfs -> ext3, I think this message should always appear when data gets lost.

Bernhard

---

### Post by KrazyPenguin on 2010-04-25
Manually setting up partitions during installation is for more advanced users.  It says that during installation.

It also tells which partitions will be formatted and asks if you wish to continue.

Also, you missed the 3 most important things to do before messing with partitions and installing a new o/s.

1) BACK UP
2) BACK UP
3) BACK UP

Good luck!!!!

---

### Post by rjcroy on 2010-04-25
This might have happened because you selected the ext4 filesystem when the existing filesystem was ext3. Even though you did not select format the program might have been programmed to format if the type of filesystem was changed.

---

### Post by Berniebln on 2010-04-25
> **rjcroy said:**
> This might have happened because you selected the ext4 filesystem when the existing filesystem was ext3. Even though you did not select format the program might have been programmed to format if the type of filesystem was changed.

I guess that is what happened, but I think there should be a hint in this case that you DO NOT check the format box...

@ KrazyPenguin: I did Backups and I do have all my data back. I'm just suggesting that there should be a warning.

Bernhard

---

