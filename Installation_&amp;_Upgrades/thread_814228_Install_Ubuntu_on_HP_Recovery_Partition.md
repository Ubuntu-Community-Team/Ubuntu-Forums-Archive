---
title: "Install Ubuntu on HP Recovery Partition"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by paintandswim09 on 2008-05-31
I plan to install Ubuntu 8.04 on my sister's HP DV6000 laptop, but due to anxiety from my sister and dad, I want to be sure that everything runs smoothly. I would like to (nuke the Vista partition) leave the Vista partition as it is, so I was wondering, does anyone know how it would work out to change the 7gb NTFS HP Recovery partition to a 7gb / ext3 partion?

I also plan to relocate /home to the Documents folder on the Vista partition, and add an ext3 file system extension to Windows.

Btw, her computer is faster on VPN on my laptop running from a LiveCD than Vista is on the machine itself running from the HD! :lolflag:

---

### Post by abhiroopb on 2008-05-31
Why do you want to change the filesystem of the recovery partition? In fact I'm quite sure this isn't possible. You could do one of 3 things. 

1. Erase everything (Vista partition and recovery partition) and install Ubuntu
2. Pop in the LiveCD, use the free space left on your sisters HD and format that free space (which would currently be NTFS for VISTA) for ubuntu - not touching the recovery partition.
3. Erase the recovery partition and install ubuntu using some of that space.

NB: You'll need a couple of GB for swap space for linux as well.

I just deleted the recovery partition of my HP, since I burnt a dual layer recovery DVD which I can just use if I ever want to put my original HP settings back on it.

Does this help?

---

### Post by oilchangeguy on 2008-05-31
> **paintandswim09 said:**
> I plan to install Ubuntu 8.04 on my sister's HP DV6000 laptop, but due to anxiety from my sister and dad, I want to be sure that everything runs smoothly. I would like to (nuke the Vista partition) leave the Vista partition as it is, so I was wondering, does anyone know how it would work out to change the 7gb NTFS HP Recovery partition to a 7gb / ext3 partion?

I also plan to relocate /home to the Documents folder on the Vista partition, and add an ext3 file system extension to Windows.

Btw, her computer is faster on VPN on my laptop running from a LiveCD than Vista is on the machine itself running from the HD! :lolflag:

do not touch the recovery partition. if you have problems with windows you will not be able to reinstall it.

---

### Post by abhiroopb on 2008-05-31
> **oilchangeguy said:**
> do not touch the recovery partition. if you have problems with windows you will not be able to reinstall it.

Just to point out like I said, I needed the extra 7gb of my laptop so I burnt the recovery DVD (which you can do by going to the start menu) and deleted the recovery partition. If I ever (touch wood) need to go back to Windows then I can just use the CD, this way I get the extra 7GB AND I can recover the original HP install! :)

---

### Post by paintandswim09 on 2008-05-31
That's likely what I will do... Where did you get the swap space? I think I might be able to squeeze a gig or two out of the main partition, but that is one area that I am fairly inexperienced in. If I shrink that partition by a gig or two, do I risk corrupting parts of the existing main NTFS partition?

---

### Post by abhiroopb on 2008-05-31
There is always a risk, but unlikely anything will happen.

What is the FULL hard drive size? I can advise youf rom there...

---

