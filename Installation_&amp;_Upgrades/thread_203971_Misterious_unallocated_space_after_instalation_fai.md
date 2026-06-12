---
title: "Misterious unallocated space after instalation failed"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by igrachev on 2006-06-26
Hello a wekk ago i decided to instal ubuntu 6.06 (on PC) so i went to the site dl it made a CD to boot from and start the instalation through the graffical instaler. I chosed to edit manually my partition table so i made enough space for the ext3 root partition and linux-swap swap one then filled in the rest of the info needed and started the instalation. But it stoped on 22% for a whole hour and i got no choise but click cancel. There was a ext3 partition with 1GB used space but no free space the free space it was suposed to include was still unallocated so i format the ext3 partition and made a new instalation at same way this time there was no problem with it so i now have the ubuntu but i still cant find a way to use these unalocated space i tryed through windows (XP) with acronis disk director but i couldnt resize ant partition to include this unalocated space. So did i permanently loose this space of my disk or there is a way (may be through linux) to have it back ?

---

### Post by rcarring on 2006-06-27
Its possible you have hit the four partitions limit.

If you try to create a fifth primary partition it won't work due to a limitation in the file allocation table. It's easy to get to four:

Primary boot windows
Primary boot ubuntu
Primary linux swap
Extended partition containing logical drives (maybe one big drive for /home)

You may have a hidden partition created by the computer manufacturer for diagnostics/rescue and this is what has thrown your partition schema out of the window.

Hope this info helps you.

---

