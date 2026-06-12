---
title: "Freeing up HD space for upgrade"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Edward The Bonobo on 2007-05-21
I have Edgy installed and up-to-date on a 4G HD.  This HD only has Ubuntu on it, a few small files on the desktop, and maybe some extra packages (but not many).  It has 890MB free.

When I try to upgrade to Feisty, I'm being told it needs more space - presumably for temp files? - although the total system requirement for Ubuntu is 2GB.

Can anyone think what might be taking up the extra space, how I can find out. how to get rid of it, etc.  I've already deleted the wastebasket and run apt-get clean.

Thanks

---

### Post by Borzo on 2007-05-21
have you tried to clean apt's downloaded files with 
sudo apt-get clean ?

that would be my first step :)

---

### Post by Edward The Bonobo on 2007-05-21
Yes, I've done that.

I'm wondering if there's anywhere I'm likely to have a lot of unnecessary files.

---

### Post by Borzo on 2007-05-21
old kernels... browser's cache, downloaded files...garbage in /home directories ...

---

