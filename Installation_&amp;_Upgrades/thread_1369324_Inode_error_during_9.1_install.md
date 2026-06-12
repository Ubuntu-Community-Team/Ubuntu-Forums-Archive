---
title: "Inode error during 9.1 install"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by Wizardknight on 2009-12-31
I am trying to install Ubuntu to a Samsung NP-Q1 tablet pc. Before the intall gui kicks in I am getting a:
EXT2-fs error (device loop1): ext2_lookup deleted inode reference 
error. :confused:
 
Does anyone have any knowlage about this error ?
Thanks.

---

### Post by Enrique101 on 2010-04-15
> **Wizardknight said:**
> I am trying to install Ubuntu to a Samsung NP-Q1 tablet pc. Before the intall gui kicks in I am getting a:
EXT2-fs error (device loop1): ext2_lookup deleted inode reference 
error. :confused:
 
Does anyone have any knowlage about this error ?
Thanks.

Just seen your post and you may wish to know that I am having exactly the same problem with my Q1 Tablet PC. It appears that 9.10 does not support it.

---

### Post by davethefan on 2010-05-18
I'm having the same trouble on an IBM Thinkpad X30 with v10.04 - I'm booting from an 8GB Transcend USB stick.

I have a 4gb casper partition that I had set up just right, mail accounts, software, settings etc - it locked up while trying to change a wallpaper.
When I restarted, the splash screen would hang and the system would not boot up.

I pressed Ctrl Alt and F1 to see what was going on and it is getting stuck on:
**ext2-fs error (device loop 1) ext2_lookup: deleted inode referenced 679791**
I've moved the casper-rw file to a subfolder on my memory stick, and reinstalled Ubuntu with a 1GB changes file.
If I swap the two around, ie put the 4GB filesystem in the root folder of the drive, it crashes, with the 1GB it doesn't..

Has anybody had any success with fixing this error?
Thanks

---

