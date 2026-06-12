---
title: "Dual-boot Compaq CQ56 laptop"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by algrossi on 2011-12-28
I have successfully installed Ubuntu on a Dell laptop, with Windows XP in a dual boot environment. It was my first attempt and learned a lot in the process. My Dell is slowly dying (bad disk), but I have a Compaq CQ56 laptop and want to install Ubuntu in a dual boot config.
It already has 4 partitions on it so it is somewhat of a challenge:
System partition 199 Mb
C: Windows 7 281 Gb
RECOVERY Partition 17Gb
HP_TOOLS 103 Mb

I managed to shrink the C: partition to 251 Gb to give me the room I need for Ubuntu.
How I am unable to format the new partition because the system does not have enough MBR

What do I do at this point?

---

### Post by Quackers on 2011-12-28
Others in your situation have deleted the HP TOOLS partition and created an extended partition in the space created by shrinking the C: drive.
This extended partition effectively becomes your fourth primary partition and can hold as many logical partitions as you want- more or less.

---

### Post by algrossi on 2011-12-28
Good call - and thank you for the quick reply.
I was wondering whether I would ever need that little HP Tools partition, and I did the following:
Delete the HP partition
Move the Restore partition next to the C: drive partition
Create the root Ubuntu partition
Create a Swap partition for Ubuntu
Format the new partitions for Ubuntu
Installed Ubuntu and it ran first try
...and the rest is history.

The whole process took me less than three hours and I am up and running with the original Windows 7 installation, with Ubuntu in the smaller partition (dual booting).
Thank you again;
Al;

---

### Post by Quackers on 2011-12-28
Glad to hear that :-)
If you ever need the diagnostic tools which were in the HP TOOLS partition I believe they are available separately from the HP website.

On another note, have you already made the Windows recovery dvd's? I hope so! Moving your recovery partition may or may not have gone well and if you haven't already made your recovery dvd's the option to make them may not now work. It's something that should be checked.

---

