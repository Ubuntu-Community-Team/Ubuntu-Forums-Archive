---
title: "Error 22?"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by dashome on 2008-08-02
Long story short I got a new hard drive to store recorded tv shows etc. Something got messed up with the MBR so I reinstalled the windows version :( of the mbr. Now I want my Ubuntu back :) in dual boot. I just tried to format my old Ubuntu partitions and start over. I kept my old /Home around in the case I needed to format without losing my docs. So I manually assigned my partitions and installation was smooth.

When I rebooted grub came up and looked normal, but no matter what option I hit in the Ubuntu part, I got "err0r 22: partition does not exist"

When I hit vista loader, I got "Bootmgr is missing press ctrl+alt+delete to restart"

How do I fix this?:confused:

Any help is appreciated and I am somewhat of a noob.

Thanks ahead of time!v:)

---

### Post by Partyboi2 on 2008-08-02
Try reinstall grub, See [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") or [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") on how to do.

---

### Post by dashome on 2008-08-04
I successfully completed the instructions, however that did not help the issue. I tried reinstalling vista's boot manager so I could at least have part of my computer working to no avail as well. any more ideas?

---

### Post by dashome on 2008-08-04
I hate my life. It was because my master hd had to be moved into the 2nd hd slot on my mobo. No bios changes fixed my issue. Thanks for the help!

---

### Post by zxscooby on 2008-08-04
You can access grubs command line interface by pressing c at the grub menu.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
This guide has a section on using the command line in grub 
to investigate your disks, partitions, and grub menu.

---

### Post by zxscooby on 2008-08-04
> **dashome said:**
> I hate my life. It was because my master hd had to be moved into the 2nd hd slot on my mobo. No bios changes fixed my issue. Thanks for the help!

lol that happened to me once. congratz!

---

