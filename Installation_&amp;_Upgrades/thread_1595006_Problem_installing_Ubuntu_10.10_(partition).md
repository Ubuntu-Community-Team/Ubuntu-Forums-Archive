---
title: "Problem installing Ubuntu 10.10 (partition)"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by rausuar on 2010-10-12
I'm using a Dell 1464 laptop using Windows 7 Home Premium 64 bits, I have downloaded Ubuntu 10.10 x64 normal installation.  However, when I get to the part of the partition, it shows me the entire disk as one device, I mean, it doesn't show the different partitions I have in the disk; because of that, I have been unable to install Ubuntu.

Is this a bug? how can I solvee this? thanks!

---

### Post by otherethe on 2010-10-12
If you have'nt installed linux on that system as of yet and this is your frist install you will need to resize it to make another

---

### Post by mrcreativity on 2010-10-12
I have exactly the same problem with my 32bit ubuntu installation and I have 10.04 installed and running already.

Someone told me its a problem with my partition table and gave me a work around i havent tried yet.

---

### Post by rausuar on 2010-10-13
> **mrcreativity said:**
> I have exactly the same problem with my 32bit ubuntu installation and I have 10.04 installed and running already.

Someone told me its a problem with my partition table and gave me a work around i havent tried yet.

Thanks, I already checked your posts and I have seen the solution!

---

### Post by Mark Phelps on 2010-10-13
For your sake, I hope "the solution" involves using only the Win7 Disk Management utility to shrink the Win7 OS, and NOT using the Ubuntu installer to do that.  The latter runs the risk of corrupting the Win7 OS partition and rendering it unbootable.

BEFORE you do anything else, you should boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will become vital later if you encounter problems with booting Win7 after your dual-boot setup.

---

### Post by dhysk on 2010-10-13
This seems to be a very common problem with this installer.  I also had this problem because of the way my swap partition was.  I deleted that partition and I was able to install normally.

On another note I know that when vista was still new it was better to use vista's partition manager to seperate the disk othewise Ubuntu would mess up the MBR... I found this out to late and was able to repair it with an old XP disk ;).  So basically I would use the win 7 partitioner first.

---

### Post by rausuar on 2010-10-13
> **Mark Phelps said:**
> For your sake, I hope "the solution" involves using only the Win7 Disk Management utility to shrink the Win7 OS, and NOT using the Ubuntu installer to do that.  The latter runs the risk of corrupting the Win7 OS partition and rendering it unbootable.

BEFORE you do anything else, you should boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will become vital later if you encounter problems with booting Win7 after your dual-boot setup.

Yes, thanks, since a while ago I have a Win 7 Repair Disk, and I have learned how to recover the win 7 MBR, just in case I need it (there is a command line in windows 7 recovery terminal).  To be sincere with you, I have this problem since I had a computer with Vista, I will continue trying to install Ubuntu 10.10, but this problem should be dealt by Ubuntu, due that this happens with most actual laptops.

---

### Post by oldfred on 2010-10-13
Most laptops today have 2 partitions used by windows, a recovery partition that is just a image of your hard drive and a vendor utility partition. That uses all 4 partitions allowed under MBR/msdos systems. No installer can deal with that. You have to decide what to delete. It is a subtle way to prevent any other installs.

---

### Post by rausuar on 2010-10-13
> **oldfred said:**
> Most laptops today have 2 partitions used by windows, a recovery partition that is just a image of your hard drive and a vendor utility partition. That uses all 4 partitions allowed under MBR/msdos systems. No installer can deal with that. You have to decide what to delete. It is a subtle way to prevent any other installs.

Thanks!

---

