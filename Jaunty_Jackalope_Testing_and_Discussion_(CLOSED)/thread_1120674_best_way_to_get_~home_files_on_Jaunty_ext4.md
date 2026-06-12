---
title: "best way to get ~home files on Jaunty ext4?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Ascenti0n on 2009-04-09
I put this in a thread in Community Cafe section, but think it is buried and I wont get help, so I figured this would be the best place to get advice.

I don't have a separate home partition right now, and I'm interested in using ext4 with Jaunty, can I just backup my home file, creating a home partition during install of 9.04, then simply restore my home folder/files into the new home partition?

---

### Post by Polygon on 2009-04-09
yeah, you can just backup your home folder and restore it after you have reinstalled.

i would use a method that saves permissions however....that means using tar + gz / bz2....or at least backing up to a drive that is formatted with ext3 or something...bad things will happen if your permissions are lost =p

---

### Post by Ascenti0n on 2009-04-09
What I be safe if I backed up the home folder to a CD-r?

---

### Post by Polygon on 2009-04-09
if you do that you need to archive your files/home folder to a .tar.bz2 or a .tar.gz archive, because the CDFS filesystem will not preserve permissions.

---

