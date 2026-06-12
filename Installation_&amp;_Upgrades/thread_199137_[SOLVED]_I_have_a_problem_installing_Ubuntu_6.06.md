---
title: "[SOLVED] I have a problem installing Ubuntu 6.06"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by RonB123123 on 2006-06-18
I made a bootable CD and put Linux on it. Then I made sure my BIOS settings were to boot from my CD. I inserted the CD, and rebooted. The Ubuntu logo didn't show up, and it showed up with the A drive and told me I can use only 4 commands. Something like.. /lend=on and 3 other miscellaneous options. 

I asked my friend, and he said there is a problem with swab space. I don't have another partition for Ubuntu, because I heard you can do that in the Ubuntu install, automatically. Could anyone help? Thanks.

~Ron ](*,)

Edit: Here is a picture of what comes up. [Picture Link](http://img74.imageshack.us/img74/1504/ubuntunotworking3sp.gif)

---

### Post by th3james on 2006-06-18
Well, the A drive is usually the floppy drive, did you definately set it to boot from CD, not floppy? Could a provde more detail on what exactly it says when it tells you you are only allowed 4 commands.

It doesn't sound like a problem with swap space, 'cause if your not seeing the ubuntu logo, it don't think it would have started looking for partitions yet.

---

### Post by RonB123123 on 2006-06-18
Alright, I inserted the Ubuntu CD again and rebooted and I wrote down what it said. I went to BIOS settings, and then booted from my DVD RW where the CD was inserted. I made this picture of what I saw in the DOS mode.

[Picture Link](http://img74.imageshack.us/img74/1504/ubuntunotworking3sp.gif)

Edit: Last time when I installed Linux, I made a partition before I installed it. And I made the partition Z or something, and then I inserted the CD and rebooted and eventually installed. It worked well last time, should I do the same again?

---

### Post by hashimoto on 2006-06-18
Reading your first post made me wonder how you really burned the iso image on the disc. Make sure you burn it as an "image" (look for someting like that in your burning software). That will do the trick. No need to set special flags for bootable etc.

Before installin, make sure to do a backup of your windows data (assuming you have windows installed), defragment it and then boot to linux install. AFAIK, the installation should be able to resize the partitions. Alternatively you can make your windows partition smaller (with some partitioning software) before starting installation and installing then on the free space.

---

### Post by RonB123123 on 2006-06-18
Oh that reminds me. I downloaded Ubuntu 6.06 from a torrent because otherwise I would have to wait 3-5 hours to download it. So it could have been burned wrong or the files could have been corrupted. Thank you very much for all your help.

---

