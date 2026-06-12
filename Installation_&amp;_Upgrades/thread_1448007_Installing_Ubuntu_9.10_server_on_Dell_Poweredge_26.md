---
title: "Installing Ubuntu 9.10 server on Dell Poweredge 2600 error"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by asakura797 on 2010-04-06
Ok, basicaly I want to install Ubuntu 9.10 server edition onto a Dell Poweredge 2600. I do all the necessary things change boot sequence etc. However when I put the disk in it says 'No Boot device detected' and won't install it. The disk does work as I tried it on my own PC. When I put in the Dell Open Mange Assistant that runs with no problems. The only problem is when selecting the Server OS the option isn't there for the Ubuntu 9.10. All the other OS you need to pay for and enter a product code. Has any one got any help with installing Ubuntu 9.10 onto the Poweredge 2600? Thanks in advance!

---

### Post by dstew on 2010-04-06
If the Ubuntu CD boots in another computer, and another bootable CD (I assume the Dell Open Manage Assistant is a bootable CD) works in the Poweredge, there is no obvious explanation, like a BIOS setting, or a bad CD. One possible explanation is that the disk is burned weakly, and your other computer's CD-ROM drive can read it, but the Poweredge CD-ROM drive cannot. Sometimes the thin CD-ROM drives in servers are a little touchy. You might try cleaning the Poweredge CD-ROM lens, or burning another CD at low speed, like 4x. It is a puzzling problem.

Maybe there is a BIOS setting, like a security measure, that will let a Dell CD boot, but not a "homemade" CD. Have you tried other Ubuntu CDs in the Dell? Just guessing...

---

### Post by tgalati4 on 2010-04-06
I've installed hardy server on a dell poweredge 1750--older hardware.

Perhaps you need to initialize your disks via the RAID controller first.  Try going into the BIOS (or RAID BIOS Control-S or something similar) and make sure that you have your drives set up the way you want--RAID configuration, hotswap, whatever.  Once that is done, then put in the CD and run the "Check CD for errors" to make sure your CD drive can read the entire disk.  Server CDROM drives tend to get dirty because of the massive airflow of server machines.

---

### Post by asakura797 on 2010-04-07
I managed to resolve the issue. I was stupidly using DVD-R which it doesn't support. SO gone back to CD-RW. I'll have to get an optical drive for it that supports DVDs. Cheers for the help though.

---

### Post by tgalati4 on 2010-04-07
You had us going there for a minute. Your machine pulled an April Fool's joke on you.

---

### Post by asakura797 on 2010-04-08
I know! I guess even computers like to mock us :P

---

### Post by xX_Q_Xx on 2010-04-20
Sorry to re-live this issue. I was hoping someone here might be able to help. I had the same problem. Tried it on a couple different machines. I ended  up re-burning the live CD and it finally worked. However, now I am  running into an issue where my Ubuntu (9.10 Desktop edition) does not  recognize a partition which consists of 6 drives in RAID 5. 

It is installed on a partition (2 drives in RAID 1) on a Dell Poweredge  2600 and there is a RAID card managing the hardware RAID. The same RAID  card also manages the other 6 drives in RAID 5. Ubuntu boots fine, but  it does not see the 2nd partition.

From what I have been reading, Ubuntu doesn't work well with hardware  RAIDs. Is this accurate? Is there a work around for this? Can someone  please point me to some documentation which may help me with this?  Thanks a bunch!

~Q~

---

