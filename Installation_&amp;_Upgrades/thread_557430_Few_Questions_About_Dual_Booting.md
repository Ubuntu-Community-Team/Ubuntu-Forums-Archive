---
title: "Few Questions About Dual Booting"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Kevin92 on 2007-09-22
Hello,

I have a laptop with Windows XP and wanted to dual boot it with Ubuntu.  I already downloaded the Live CD and everything seems to be running fine. Before I install it, I have a few questions.

1. How much space should I set aside for Ubuntu? I have a 80 GB HDD with 2 partitions.  One is my main partition and the other is a 6 GB recovery partition.

2. I've read in a few places that installing GRUB into the MBR can cause problems.  What is the safest way to boot these different OS's?

3. I'm going to back everything up and make restore discs before I start, but just how safe is the whole procedure? Most of the time does this work without problems?

4. I defragged my HDD a few times, but I still seem to have a blue area towards the right hand side on the defragmenter. If I shrink this partition, what would happen to the data that is in this area? Is there any way to move it closer to the rest of the data?

Thanks in advance.:)

---

### Post by Pumalite on 2007-09-22
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Kevin92 on 2007-09-22
Thanks for the response.  I've also heard something about the Wubi installer.  This sounds like a safer, easier alternative to partitioning.  Is there a reason not to use Wubi?

---

### Post by Pumalite on 2007-09-22
I don't know anything about wubi, but I've heard is for 'scare cats' and kids.

---

### Post by rhb on 2007-09-22
I saw your post, and was interested to learn about the existence of Wubi.  The biggest problem I see with it is that it is still in beta.  I believe that when mature, Wubi (or something very similar) will be the migration path of choice for most Windows users.

 One of the techniques Microsoft has used to discourage changing the OS has been to encourage the building of machines with only one partition, and with no simple way for the novice user to reorganize it into multiple partitions.  Wubi directly addresses that, and should become a good first step toward OS installation for novice computer users.

 While messing with partitions is touchy, I believe that the ubuntu partition resizing tools are mature and reliable, and that you are well-prepared to take that step.  If you feel Wubi has a good enough track record, it would be a good alternative and again I believe the risk is small.  One advantage of using Wubi is that you won't need to decide right now how much disk space to commit to ubuntu.

When you finally do get ready to repartition, I would recommend checking the status of the ntfs file system driver in ubuntu.  I know on my system (I run Dapper) it is not reliable for writing.  Eventually, you should be able to repartition your disk with one (or more) Windows-only partition, some Linux-only partitions, and a big shared ntfs partition.  How big you make the shared partition may depend on how reliably you feel the two OS's can share the space.

---

### Post by rsambuca on 2007-09-22
I would recommend the shared partition as ext3, since it is a much hardier filesystem than ntfs.  Windows can use ext3 with the [FS driver]("http://www.fs-driver.org/").  If you have everything backed up, I would go ahead and shrink that XP partition down using the [gParted liveCD]("http://gparted.sourceforge.net/").

Then install ubuntu and it should detect your XP and give you the choice at bootup.

---

### Post by Kevin92 on 2007-09-22
Alright guys, thanks for all the help. :) One last thing.  Do you recommend I install GRUB to the MBR?  I've heard it can lead to problems.  If theres another way that you thinks better, post it here please.  Also, what would I do if the MBR did get messed up?

---

### Post by rsambuca on 2007-09-22
I use grub to chose between OS's at bootup, and it has always served me well.  It tends to work quite easily the first time when only one hard drive is involved, such as in your case.  It can sometimes get a little bit 'finicky' to set up when multi-drives are in your rig.

---

### Post by Kevin92 on 2007-09-22
Okay, great.  And if something did go wrong and the MBR became corrupt, is there anything I could do besides reformat and start over?

---

### Post by rsambuca on 2007-09-22
If you have the XP install discs, or even an old Windows 98 disc, all you need to do is boot from it, enter the recover mode and enter 

fixmbr

at the command line.  This will restore the XP bootloader to it's original form.

---

### Post by Kevin92 on 2007-09-22
Okay.  My computer did not come with an XP disc.  Instead it came with just a recovery partition on my HDD.  However, I do have the install disc that came with another computer of mine.  Will this disc work, or are they system specific discs? Thanks again.

---

### Post by rsambuca on 2007-09-22
Those recovery discs suck.  I received them with my machine as well!  In any event, the short answer to your question is no, they cannot be used to just restore the mbr.

You can use the [super grub disc]("http://supergrub.forjamari.linex.org/") to either fix grub or restore the Windows mbr if things go wrong.

Man, it is nice to see someone thinking *ahead* for a change!  Way to go!

---

### Post by glotz on 2007-09-22
hehehee!

---

### Post by Kevin92 on 2007-09-22
Alright, I'll download Super GRUB just in case.  Now I have just one more question (hopefully.)  I defragged my HDD a few times, but on the right side (towards the end of the drive) there seems to be a blue area (contiguous files) that won't seem to move no matter how much I defrag.  Now, when I resize this drive, won't this data become corrupted because it is at the end of the drive?  If not, I'm ready to install.  If it will be a problem, is there any way to move it closer to the beginning of the drive?

---

### Post by rsambuca on 2007-09-22
It should be OK as long as it isn't the green coloured stuff.

---

### Post by Kevin92 on 2007-09-23
Alright I'm installing now.  The installer seems to be hanging at 74%.  It's been there for about 25 minutes.  What should I do?

---

### Post by rsambuca on 2007-09-23
Dagnabbit!   If it really is hung, there probably isn't a lot you can do, other than to start the installation over again.  I might suggest the alternate CD as well.

---

### Post by Kevin92 on 2007-09-23
Alright, I put the Live CD back in and checked the disc for errors.  It found an error, so I'm downloading it again.  So this should be an easy fix.

---

### Post by glotz on 2007-09-23
It's always good to check for defects before installing. The install could well have worked and then later you'd just experienced strange problems.

---

### Post by Pumalite on 2007-09-23
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Leed on 2007-09-23
If Grub really hangs in the MBR, you can easily replace it by reinstalling Linux with a LiveCD. If it really doesn't want to work, you can still use LILO which comes with most Linux Distros. 

The MBR is only needed to tell the computer which part of the HDD to boot from, if it breaks, the partitions still all have their own File-Allocation-Tables. 

But don't worry that much, Grub is really nice, so far I found it to be the best Boot loader I've ever seen.

---

### Post by glotz on 2007-09-23
[QUOTE=Leed]Grub is really nice, so far I found it to be the best Boot loader I've ever seen.[/QUOTE]Agreed.

---

### Post by Pumalite on 2007-09-23
+1

---

### Post by Kevin92 on 2007-09-23
That was my only problem, the disc had errors.  I downloaded it again, burned a new disc, and it installed perfectly.  Thanks guys.

---

### Post by Pumalite on 2007-09-23
Glad you made it work!

---

