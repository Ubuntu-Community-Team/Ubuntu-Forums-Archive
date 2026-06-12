---
title: "Ubuntu install on a Windows XP machine - A few questions"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by dareys on 2011-06-04
Greetings,

I have been trying Ubuntu 11.0.4 for a few days without actually installing it. on my machine. So far, I have discovered that most of my existing Windows files on disk are still accessible from the booted Ubuntu OS, that all my devices are functioning and that I can open all files them which is great (*.txt, *.doc, *.pdf, etc).

My question is:

If instead of launching the Ubuntu for test purposes, I actually go with the full install on the box, will it reformat the hard drive, install and wipe out all of my files? It would be great if the install did not delete all files.

Regards,

Jean-Pierre

---

### Post by Quackers on 2011-06-04
Ubuntu will not delete anything (well 11.04 won't).
As a safety precaution you should confirm that not more than 3 primary partitions already exist on your hard drive, and that there is some free space on the hard drive for Ubuntu to install into (not free space within a partition).
If this is the case you can install Ubuntu using the "install alongside" option in the installer.

---

### Post by Thewhistlingwind on 2011-06-04
Be sure to test your hardware too before installing.

But yes, what was said above about covers it.

If you want a separate /home partition, make sure you have no more then two partitions already installed.

---

### Post by dareys on 2011-06-05
> **Quackers said:**
> Ubuntu will not delete anything (well 11.04 won't).
As a safety precaution you should confirm that not more than 3 primary partitions already exist on your hard drive, and that there is some free space on the hard drive for Ubuntu to install into (not free space within a partition).
If this is the case you can install Ubuntu using the "install alongside" option in the installer.
Fellows,

Thank you for the responses to my question. I have a couple of follow up questions.

1. I believe that my machine has three partitions on it.. Can you please confirm how to verify this? 
2. Exactly what part of the hardware should I test? Standard memory and disk?
3. If I only have two partitions on the box, is the consensus that I should create a third one for the /home partition?

Thank ya' ll!

Jean-Pierre

---

### Post by Quackers on 2011-06-05
If you have used the live desktop then it seems that you have tested the main hardware items already.
If you go into Windows and click Start then right-click on Computer and select "Manage" then in the new window in the left pane select Disk Management a new window will open up. This will give details of your current partition layout. The important thing is to check that no more than 3 primary partitions exist already (including any recovery partition).

---

### Post by underquark on 2011-06-05
On a typical Windows machine you should only have one or two partitions.  You might have a Recovery partition and you'll have the typical messed up Windows partition with fragments of files everywhere.


1] Boot into Windows

Delete anything you don't need
Back up important data
Disable the Windows swapfile
Defragment the hard disk (to shufffle all the fragmented files to the "front" of the drive and leave space at the end)
Shut Down Windows

2] Boot using the Live CD (or USB)

Use Gparted to see what partitions you have
Shrink the main Windows partition (just how far you shrink it depends on disk size and how much more stuff such as games and other applications you think you might want to load onto Windows in the future).


3] Install ubuntu choosing to install alongside Windows.  Forget separate partitions for /home etc. and just let it do it automatically, including creating a swap partition.  Once you get to know your way around ubuntu later you can think about separate /home, /var, /usr partitions etc. IF you need to.


4] Re-boot back into Windows to check that it still works and to re-enable the Windows swapfile

5] Re-boot into ubuntu and enjoy

---

