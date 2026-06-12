---
title: "Shifting home directory advice"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by drahmad on 2008-02-09
Hi and thanks. I've just installed Edubuntu for the first time on the following hdd configuration:

10Gb HDD ext3 "Guided" installation (use all 10Gb)
20Gb HDD NTFS - where I stored all my personal files/documents when running under Windows

Unless you would advise against it, I would like to have all my files saved onto the 20Gb hdd in case in future I want to much around with the OS and install again or another distro, etc.

Is that achieved by moving my /home directory to the 20Gb hdd? If so, how do I do this please?

Also, should I change the file system of the 20Gb hdd to ext3 or something else? Or leave it as NTFS?

I currently have no requirement to share these drives on my home network but it may be something I look at later. Therefore it would be nice to think ahead and allow these to be accessible to Windows computers over the network.

Thanks in advance.

Edit: P.S. I am actually happy to completely reinstall everything so can this be setup during the installation process (ie. assigning home directory to the other physical hard drive).

---

### Post by Partyboi2 on 2008-02-09
[Here]("http://www.psychocats.net/ubuntu/separatehome") is a how-to move your home folder to its own partition.
You can install a small program for windows that allows you to see ext partitions from [here]("http://fs-driver.org/")

---

### Post by drahmad on 2008-02-09
I am not fully understanding the logic of the commands on that page - if I did a reinstall is there any way of getting Edubuntu to use my 20Gb HDD (once reformatted to ext3) to put the /home directory there in the first place?

---

### Post by Partyboi2 on 2008-02-09
When you use the installer choose to do the partitions manually and then on the 10 gig drive create a /swap (only needs to be around twice the size of your ram, unless you have more then 2gig) 
and a /root ext3 (where the system files are kept) 
then on the 20gig drive 
your /home ext3 as big as you like (your settings, doc's, videos etc)

---

### Post by drahmad on 2008-02-10
Ok thanks. I'm ditching Windows altogether so I'll get the 20Gb hdd backed up with intention of a 10+20Gb ext3 install, with system files on 10 and peresonal stuff on the 20. I've heard this makes it great when you decide to install a different distribution.

P.S. I didn't get a reply to another thread about Edubuntu "young themes for young children" - you don't happen to know anything about that do you?

[http://ubuntuforums.org/showthread.php?t=692423](http://ubuntuforums.org/showthread.php?t=692423)

---

### Post by Partyboi2 on 2008-02-10
Sorry, I haven't used edubuntu, so not probably going to be much help for your theme problem.

---

