---
title: "No OS at all after 6.10 install!"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by jave on 2006-11-13
Recently I purchased a new Dual Core Pentium PC with a 250GB SATA2 hard-drive.  After installing XP and creating an empty 40GB partition for other OSes such as Ubuntu, I also installed a 250GB PATA hard-drive which I took out from my old PowerMac G4.

Today I decided to and install Ubuntu 6.10.  Initially everything went fine, including the use of the Partitioner, which actually recognised my SATA2 hard-drive. (My previous attempt at installing 6.06 did not.)  I let the Partioner install Ubuntu on the largest free space on the SATA2 drive (ie the empty 40GB partition) and I also selected Grub to install on /dev/sda (instead of /dev/hdc).  Again everything went fine, except near the end of the installation, where it died with an fatal error stating that Grub failed to install correctly (I didn't take note of the error messages).  So I exited the installation and then rebooted.  Now I knew I would have some trouble booting up, especially since Grub failed to install correctly.  When it did boot up, all I got was "GRUB" in the top left corner of the monitor and a flashing cursor.  "No problem" I thought, "I'll run FIXMBR from my XP install disk".  I did this and... nothing.  I still get the word "GRUB" and a flashing cursor. :(

I've searched this forum for problems similar to mine, and I've found some threads which give instructions as to reinstalling Grub from the live/install CD.  I haven't tried these yet, but I soon will and see how it goes.  But before I do, I just want to  make one clear statement.  When installing a secondary OS, a user should expect that if the install fails, they can still boot up their machine with the primary OS and have it back to how it was before the attempted installation.  This was not so in my case.  I can understand errors during an installation, at times they are unavoidable.  But to leave a machine which won't boot up at all is just not on. :mad:

---

