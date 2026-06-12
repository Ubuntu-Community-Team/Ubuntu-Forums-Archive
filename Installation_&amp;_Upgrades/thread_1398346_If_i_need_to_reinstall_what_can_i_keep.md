---
title: "If i need to reinstall what can i keep?"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by GuyZerO on 2010-02-04
[http://ubuntuforums.org/showthread.php?t=1396978](http://ubuntuforums.org/showthread.php?t=1396978)

it seems that all i can do is reinstall. im just curious what i can save and what i wont be able to

and how do i go about reinstalling correctly so as to not have that same error.

and also i have a windows partition that i would like to keep if possible so i would rather not format... 

any help would be appreciated. grazie folks

---

### Post by pkm4o93 on 2010-02-04
Im not sure how you broke it,im new to chmod and chown etc   **Do you have a seperate home partition?**  If so carefully do a manual partitioning when installing and choose to mount as /home and DONT FORMAT. Id reccomend backing up to another drive if you are new. I use puppylinux often for this type of thing.  It may be sensible after installing to backup /  [http://www.ibm.com/developerworks/linux/library/l-roadmap8/](http://www.ibm.com/developerworks/linux/library/l-roadmap8/)

---

### Post by oldfred on 2010-02-04
If you do not have a separate /home backup everything in /home including the hidden files and folders, that will save most of your configurations. I like to occasionally export all the programs I have installed to make sure I can easily reinstall. 

dpkg --get-selections | grep -v deinstall > ubuntu-files
You may still be able to chroot into your system to list the packages.

---

