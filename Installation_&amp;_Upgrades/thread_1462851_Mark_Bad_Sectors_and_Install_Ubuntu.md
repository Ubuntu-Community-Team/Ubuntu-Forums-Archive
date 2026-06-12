---
title: "Mark Bad Sectors and Install Ubuntu"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by arjunbajaj on 2010-04-26
[SIZE=2]Hey Guys,

I have an old hard disk in my computer - 250 GB - i have been using it since 2 years. Now it has some physical bad sectors. I have data on 2 partitions but i can remove that data also and i had windows on the primary partition before formatting the drive.

[/SIZE][SIZE=2][FONT=Courier New]**[SIZE=4]I want to mark the bad sectors of that hard disk and then install ubuntu 9.10 on it.[/SIZE]**[/FONT] i tried installing it but then it wasn't working properly. Is there any way to mark the bad sectors first and then install ubuntu on it....    [/SIZE]

:):confused::confused::confused:.....thnx.....:confused::confused::confused::)

---

### Post by thebigob on 2010-04-26
Sorry I cannot answer this question specifically however a possible solution would be to use the fsck command in order to repair the disk.

You can boot from a live cd and run the command in a terminal to hopefully repair the bad sectors

---

### Post by paulisdead on 2010-04-26
The drive manufacturer's testing tools might have a feature like that available.  You can typically find them on the site of whoever made the drive, in the form of a bootable ISO.  What you should do, is run the manufacturer's tests, and see if you get an error code from the drive.  If the drive is only 2 years old, it's probably in warranty.  With that error code you should be able to get an RMA and send it back to whoever made it for a replacement.

---

### Post by arjunbajaj on 2010-04-27
Thanks guys........I finally did it......I changed the drive sectors and installed ubuntu on sda2 and i managed to get ubuntu up and running on it........Now its giving me no errors.......thnx........:)

---

