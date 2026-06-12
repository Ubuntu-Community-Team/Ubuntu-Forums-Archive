---
title: "loading 64 bit ununtu over 32 bit ubuntu on dual boot win 7 setup"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by jmurphy510 on 2011-01-02
I have a windows 7 machine and installed ubuntu 10.4 32 bit in its own partition.  I want to replace the 32 bit ubuntu installation with a 64 bit installation.  I downloaded the 64 bit version, booted up on the install cd, and started the install.  I got as far as the partition set up before chickening out.  I was going to use the manual partition option, select the existing ubuntu partition, reformat, and install.  I chickened out because i was afraid that this would also reinstall the grub boot loader without the dual boot option disabling my ability to get into win 7.  How should i proceed so that i can replace the existing 32 bit ubuntu with a fresh 64 bit install and still be able to boot into win 7?

---

### Post by SnickerSnack on 2011-01-02
Well, how did you set up grub in the first place?  Was it while installing ubuntu the first time?

If I were you, I'd proceed as you were going to.  You should be able to configure grub during the install process.  It might even work if you told the install not to touch grub, but I'm not sure about that working correctly.

Also, it's a really good idea to have a separate partition for your home directory.  The main benefit is that in the future, you can install a new distro without touching /home.

---

### Post by jmurphy510 on 2011-01-02
When i originally installed the 32 bit version of 10.04, i used the "side by side" partitioning/install option in the install menu.  Since i would not be doing that again this time, my concern was that that this install would modify the existing "dual boot" grub configuration to only recognize the newly installed 64 bit ubuntu partition.

---

### Post by SnickerSnack on 2011-01-02
This might help you:

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by jmurphy510 on 2011-01-02
This looks like it is exactly what I was looking for.  I'll let you know how it goes.

---

