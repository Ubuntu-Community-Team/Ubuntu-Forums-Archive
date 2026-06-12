---
title: "After upgrade to 13.04: all programs gone and home directory dissociated"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by archimboldi2 on 2013-08-07
Hello,

I just upgraded from 12.04 to 13.04 using an USB key. Shortly before finishing the process an error occured, reporting something like "program recovery failed". Now the system boots normally but not only seem all previously installed programs to be gone, but also my "old" home directory has been moved to the "media" directory and is no longer associated with the "places" in the file manager. If there is a way of recovery for these two issues, I'd be glad if someone pointed me towards it. Do I simply need to copy my old home folder to the new "home" directory? Do I have to reinstall all applications? And what about all the former settings etc., might they be lost?

Any help appreciated!

Thanks!

---

### Post by prookie on 2013-08-08
Hi,

  I'm not an expert, but if you see /home directory only in /media that means that it is now located on your bootable USB. Check in terminal your directories with ls command.

  Be careful when playing with upgrades and installations in Linux. Always back-up your important files.

  Good luck,
  pRookie

---

### Post by Boab1993 on 2013-08-08
Hi all, 

Ubuntu instantly associates any folder called 'home' under root(i.e. "/") as the home folder. 

So yes your correct, by deleting the current home folder and replacing it with your old home folder you should be fine.
As for passwords and login details, i think they might need to be edited.

Its actually a quick fix to get rid of an encrypted home folder!

But pRookie is right, backing up whilst tweaking with any linux install is important, you can loose everything, its happened to me more than once, i now have 3 dropbox accounts just for that purpose.

Hope this helps

---

