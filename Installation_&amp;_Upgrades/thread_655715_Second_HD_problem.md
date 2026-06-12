---
title: "Second HD problem"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by dvfreelancer on 2008-01-01
I have Ubuntu Gutsy running on a machine and want to add a second 300 Gig HD.  

This machine does not have a floppy or working CDROM (one is on the way).  

When I try to start gParted it hangs.  I have to start it with:

sudo gparted /dev/hdc

When I try to create a new partition it will only let me create a 12 GB partition.  Whether I try Primary or Extended...12 GB.  

I need step by step instructions to format the whole drive.  Historically I've plugged the drive into a Windows box, formatted it as FAT32 and put it back in the Linux box but I'm determined to do it right.  

Am a little surprised it's so difficult.  You'd think this would be a simple operation.

---

### Post by Pumalite on 2008-01-01
What are your specs? Have you updated your BIOS?

---

### Post by dvfreelancer on 2008-01-01
I'm not sure how to update my BIOS.  If you're asking if I disabled the floppy in the bios, yes I did.  

Although calling up the device manager to get the hardware specs, I did notice the second hard drive is being detected as MASTER.  Would that explain why it seems to be insisting on a primary partition?  

I'll reset the jumper on the drive and check it again.

---

### Post by torgrot on 2008-01-02
What kind of drives are they, SATA or IDE?  If they are IDE and on the same cable they shouldn't both be master.  If the first drive is set to cable select then both drives need to be cable select, otherwise one should be master and on should be slave.  SATA drives are a different story.

torgrot

---

### Post by dvfreelancer on 2008-01-02
They're IDE drives on separate cables.  Is there any way to tell Unbuntu to just format an entire drive?  Make this...thing...ext3 for as big as it will go?

---

### Post by torgrot on 2008-01-02
Put both drives on one cable.  You don't want the CDROM when you get it to share a cable with a hard drive.  It will slow it way down.  Then try using gpared again.  It should allow you to partition and format the drive.  How old is this computer?  Does the BIOS see all of the drive?  Tell us your specs and we can help you.

torgrot

---

### Post by dvfreelancer on 2008-02-10
I absolutely hate admitting I made such a dumb mistake but the problem was user error.  I pulled the drive out of an old PIII I was using as network storage.  This thing is stuffed with drives and I grabbed the wrong one.  

The reason nothing would see it as anything more than a 12 gig drive is because...

...it was a 12 gig drive.  ](*,) :oops: #-o

---

### Post by vaalbygaardsvej on 2008-02-10
heh. explaines it i guess.. but.. erh congrats on the solution:)

---

