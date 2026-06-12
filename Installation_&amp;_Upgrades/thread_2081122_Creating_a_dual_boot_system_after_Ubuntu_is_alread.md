---
title: "Creating a dual boot system after Ubuntu is already installed"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by linux_trojan on 2012-11-06
I am trying to dual boot windows XP.  I had to use gparted to make room for my /home to be transfered to another partition, I also changed it to a logical partition.  Where  my /home was, I have formatted it using gparted to ntfs and made it bootable; however the windows cd cannot find any windows partition.  I formatted the primary partition as ntfs and bootable.  Why doesnt windows see the ntfs partition?

---

### Post by carl4926 on 2012-11-06
I have seen this before

I think I deleted the partition and left free space
then

My solution is to use the XP installer partitioner to re-format the space

Be careful

---

### Post by carl4926 on 2012-11-06
> **carl4926 said:**
> I have seen this before

I think I deleted the partition and left free space
then

My solution is to use the XP installer partitioner to re-format the space

Be careful

Or maybe I made it FAT32 and then formatted it to ntfs
try that

---

### Post by linux_trojan on 2012-11-06
thanks for the reply.  I tried both suggestions and none worked.  This is happening to all my computers (3) ever since I went totally DELL back in 2008.  Sometimes I wonder if DELL secretly put something in the bios to cause this.  I really dont know but I am in a bad place now if I cant get this windows installed.  Please help.

---

### Post by oldfred on 2012-11-06
Is your new NTFS a primary partition formatted NTFS with the boot flag? It has to be primary or sda1 thru sda4.

---

### Post by linux_trojan on 2012-11-06
> **linux_trojan said:**
> I am trying to dual boot windows XP.  I had to use gparted to make room for my /home to be transfered to another partition, I also changed it to a logical partition.  Where  my /home was, I have formatted it using gparted to ntfs and made it bootable; however the windows cd cannot find any windows partition.  I formatted the primary partition as ntfs and bootable.  Why doesnt windows see the ntfs partition?

Thanks for this post.  Yes, originally the partition was logical but then I moved my /home to the logical, and put the NTFS on the hda3 partition, primary.  I used Gparted to do all this, I also made it bootable using Gparted.  

I have a separate windows box also.  Is it possible to copy that windows over using an iso?  I am really suck.

---

### Post by oldfred on 2012-11-06
No, Windows is licensed for one computer only.

---

### Post by linux_trojan on 2012-11-06
If there is a way to copy windows from on box to another box, I promise I will delete one copy.  So how do you do it?

---

### Post by linux_trojan on 2012-11-07
I went ahead and just blanked the entire hard drive:  I wrote "0"s over the entire hard drive.  Then I tried to format the drive using NTFS, Fat32, even Fat16 and Windows XP will still not see the drive.  I am open to any wild solution at this point.  I do have XP on another computer but I have never completely used linux on that computer either.  Anyways, any suggestions would be welcome

---

### Post by carl4926 on 2012-11-07
But the XP setup starts?

Check the BIOS setting for AHCI settings and make sure it's in Compatibility Mode

---

### Post by linux_trojan on 2012-11-07
I went into the BIOS and found something called SATA Operaton, and it had two options AHCI and ATA but I dont see anything for AHCI Settings.  Could you give a little more info?

And yes XP set up starts but when I tell it to start the install, it says it cant find any windows partitions.

---

### Post by carl4926 on 2012-11-07
Just try the ATA setting

---

### Post by linux_trojan on 2012-11-07
OMG I think it worked.  For the first time I made it to the EULA, it didnt say "cant find windows partitions blah blah blah".  I dont have time right now to investigate further but making it to the EULA is a big step forward.  Next I gotta do all my partitions for dual boot:  Linux, NTFS, Swap, etc, then install windows, then install linux.  Lotta work to do but I got other stuff to do right now.  In any case, thanks for your help, looks like its fixed.

---

### Post by carl4926 on 2012-11-07
> **linux_trojan said:**
> OMG I think it worked.  For the first time I made it to the EULA, it didnt say "cant find windows partitions blah blah blah".  I dont have time right now to investigate further but making it to the EULA is a big step forward.  Next I gotta do all my partitions for dual boot:  Linux, NTFS, Swap, etc, then install windows, then install linux.  Lotta work to do but I got other stuff to do right now.  In any case, thanks for your help, looks like its fixed.
Sorted eh
Good

---

