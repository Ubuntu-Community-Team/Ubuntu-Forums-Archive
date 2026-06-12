---
title: "Creating a Partition and Dual Booting"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by lazyrussian on 2006-07-05
I've gone back and fortt between xp and kubuntu for a few months on two different computers.

Now I want to make a dual boot on my laptop for the upcoming fall semester in college (university does not support wireless for non-mac/non-windows OS)

I need to know the easiest (and free) way to make a parition on my 25 gig laptop and if giving the partition 7-10 gigs of space is enough? - This partition will be linux (windows is already installed).

After installation of kubuntu (or before), how do I enable the computer to let me dual boot?

I've read a few things in the forums but nothng concrete enough to help me, or maybe I haven't found the right threads.

Thanks in advance!

---

### Post by Ubuntist on 2006-07-05
Installing (K)Ubuntu will automatically result in a screen appearing after you switch on your computer in which you are asked which operating system you want.  25 GB of disk does sound a little bit tight for a dual-boot system, though.  How much free space do you have now?

---

### Post by aysiu on 2006-07-05
If XP is NTFS (which it probably is), all its contents will be read-only in Ubuntu.

Many people set up a shared FAT32 partition (which both operating systems can natively read from and write to), but Ubuntist is right--25 GB is pretty tight for a dual-boot.

7 GB would be plenty for Ubuntu (my installation has Ubuntu, Kubuntu, and Xubuntu and other programs, and it's only 3.5 GB), but the shared partition is the problem.

I'd read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by lazyrussian on 2006-07-05
So, tell e if I understand this correctly. All I have to do is put in the (K)ubuntu CD I got in the mail and run the automatic install and then I'll automatically be able to dual boot between windows and linux?

Windows is using maybe 5 gigs (photoshop, dreamweaver, flash8, gaim, ftp program, maxthon, opera, IE7, firefox, and a few other programs - all the multimedia is on a different computer).

---

### Post by aysiu on 2006-07-05
Close.

All you have to do is **back up your important data**, read [this installation guide](http://www.psychocats.net/ubuntu/installing.html), and then pop the CD in and it'll automatically set up a dual-boot... as long as you set up your partitions correctly.

---

### Post by lazyrussian on 2006-07-05
most of the data I need (aside from programs mentioned above) is backed up on  another computer.

The only thng I don't want to happen is to have to reinstall the adobe programs and etc...

---

### Post by aysiu on 2006-07-05
Do you have some kind of ghosting program, then--Norton Ghost, for example?

I'd say if you know what you're doing, there's about a 99% chance that everything will go fine, and nothing on your Windows partition will be damaged.

If you don't know what you're doing, that probably drops to around 60%, which is not the kind of chance I would take.

Oh, and I forgot to mention in the last post that you should defragment your Windows drive before doing anything.

---

### Post by lazyrussian on 2006-07-05
I already did that.
I looked at the tutorial you posted a few posts above.

I think I'm going to re-size my IDE1.

This will allow me to install kubuntu and dual boot, correct?

One more question (thanks so much for all the help so far).

Say I want to install a program later on strictly for windows or strictly for linux, I can do that right? When I install Kubuntu, the re-sized partition will not stop me from installing programs on my C:\ drive (win xp), correct?

Thanks so much!

---

### Post by aysiu on 2006-07-05
You will have to be booted into Windows XP to install a program in Windows. Likewise, you will have to be booted into Kubuntu to install a program in Kubuntu.

You can't install a Kubuntu program from Windows or a Windows program from Kubuntu.

---

### Post by lazyrussian on 2006-07-05
gotcha
I couldn't think of another way to word my question - sorry if it sounded funny., but otherwise you answered my question.

thanks again!

---

