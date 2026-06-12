---
title: "Ubuntu Partitioner Does Not Detect Windows"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by narehart on 2007-07-01
Hey everybody, I've been trying to install a dual boot of windows xp pro and ubuntu feisty fawn for the past couple of days.  The first time I installed xp first creating a partition in it's options then manually created partitions when I installed Ubuntu.  After rebooting I recieved the message "operating system error".  After being able to find any specific thread about this error with ubuntu I read that it could be caused by not properly formatting the drive (quick format) so I did that and reinstalled xp.  Now I am trying to reinstall Ubuntu but the setup partitioner doesn't recognize my xp partition.  If somebody could offer me a solution or maybe even just the cause of this problem it would be greatly appreciated.  Thanks in advance.

---

### Post by Gremlinzzz on 2007-07-01
install windows create a partition for ubuntu  delete partition created for ubuntu making it free space when asked choose- largest continuos free space.thats it i dual booted xp ubuntu and vista ubuntu works every time.

---

### Post by narehart on 2007-07-01
Update... I tried running gparted to resize the windows partition so I could manually install ubuntu and it told me to check the file system for errors.  I think I might be having these issues because of a bad hard drive ( I found it in a computer in the trash ).  If thats the case I'll just reinstall on my SATA.

---

### Post by narehart on 2007-07-01
I tried checking the windows file system with the disk check utility installed in windows but it didn't find any errors.  I am going to reinstall on my SATA.  If you don't hear back from me I'm happily dual booting.

---

### Post by narehart on 2007-07-02
Okay well I finally figured out what was going on here.  Apparently there is little known problem with GRUB when it comes to installing a dual boot on a system with both IDE and SATA drives.  From what I've read GRUB will change the hard drive assignment numbers around resulting in errors upon booting up.  I'm going to unplug my SATA and see if I can complete my dual boot that way.  I'll keep you updated.

---

### Post by narehart on 2007-07-02
Yep that was it alright.  Unplugged the SATA and GRUB installed normally giving me a dual boot XP/Ubuntu IDE drive.  Now I want to know if I can plug my SATA back in without screwing everything up again.  If not I have 250gb going to waste... any help?

---

### Post by louieb on 2007-07-02
Who knows?  Just interested in what happens when you plug the sata drive back in.

---

### Post by Pumalite on 2007-07-02
Me too. I-m getting ready to test a mixture of IDE and SATA drives in a new box.

---

