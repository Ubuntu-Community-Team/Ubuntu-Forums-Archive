---
title: "Partitioning Problem"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by gubemton on 2007-10-24
I'm planning on dual-booting vista and ubuntu, so I shrunk my windows partition down, and now when starting up I get this message:

"Windows failed to start. A recent hardware or software change might be the cause.
File:\windows\system32\winload.exe
Status. 0Xc0000225"

What I did:
Reduced the windows partition to about 58 gb (made no other changes)
After that, made a 10gb ext3 partition for ubuntu
Made a linux-swap and fat32 partition after that

Any ideas on what the problem could be?

---

### Post by rsambuca on 2007-10-24
Did you shrink the partition with Vista's Disk Manager, or did you use another program?  If you didn't use the Vista Disk Manager, you may have to re-install Vista.

---

### Post by gubemton on 2007-10-24
I used SystemRescueCd.

I bought a computer with xp installed and got a vista upgrade cd. My upgrade cd isn't loaded (everything is the same when I start up with it in) and the xp recovery cd doesn't do anything either.

---

### Post by mivo on 2007-10-24
May not be related, but did you defrag the disk before resizing?

---

### Post by gubemton on 2007-10-24
No, which I'm regretting now.

But even if some of the data is corrupted I should be able to use my recovery cd, I have no idea why that's not working.

---

### Post by gubemton on 2007-10-24
So is it pretty much the defragging that's the issue? Or is there another potential problem?

If not, can I possibly legally download a fix?

Also, does anyone know why I can't use my recovery cd?

I'll reformat my hd if I have to, but that'll take AWHILE and I'm not sure how vista's drm will feel about me using the same serial again.

---

### Post by mivo on 2007-10-25
Vista will only properly boot if its partition starts at sector 2048. There appears to be a problem with some (older?) partitioning/resizing software that causes the Vista  partition to "drop" to sector 63, which then causes Vista to become unbootable. This was documented [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=379835"). I don't know the software you used to resize, so this may or may not be related. A way to fix this, **if** this is the cause, is described in the Red Hat 5 release notes:

> 
On a dual-boot system where Windows Vista&#8482; and Red Hat Enterprise Linux 5 are both installed on different partitions, Windows Vista cannot boot. This is because Windows Vista now aligns to a different sector of the DOS disklabel.

To address this, start by booting the Red Hat Enterprise Linux 5 media in rescue mode. Do not let it detect or mount file systems. Once it boots in rescue mode, follow these steps:

   1. Determine what your hard disk device is; normally, this is either /dev/sda or /dev/hda. To do this, use the command cat /proc/partitions at the prompt.
   2. Run fdisk on your hard disk device (for example, fdisk /dev/sda).
   3. Change the unit type to sectors using the u command. This is a crucial step in the process, as the default unit type is cylinders, and the following steps will not work if the unit type is cylinders.
   4. View the current partition table using the command p. The NTFS partition is listed first at a starting sector of 63. Take note of the ending sector, as you will need this later.
   5. Delete partition 1: to do this, type d, press Enter, type 1 and then press Enter. This does not delete the entire partition; it only removes the disk label entry.
   6. Create a new partition: to do this, type n, press Enter, type p and then press Enter. Specify the starting sector as 2048. For the ending sector, specify the value you took note of earlier (when you used the command p to view the partition table).
   7. Change the NTFS partition type to 7.
   8. Use the w command to write the partition table, then use q to quit.

At this point, it is recommended that you test first if Red Hat Enterprise Linux 5 boots properly. Once you have verified this, you can now try booting Windows Vista. During bootup, the system may warn you that the file system was not correctly unmounted. Let the system perform a file system check if it insists.


([Source]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/release-notes/RELEASE-NOTES-x86-en.html"))

Note here that I do not know if this is indeed your problem and whether this fix applies. I read about this in a German Linux book in a section about file systems and how to repair various issues, and it reminded me of your trouble. But since I do not use Vista and have no first hand experience whatsoever with how it boots, this is not more than an idea to look into. :)

---

### Post by FenwayFrank on 2008-02-02
Hi.. After resizing my partitions with LiveCD, I'm running into the same problem.  But the partition that has Vista already starts at sector 2048, so is there any other known cause for the error or some other way I can get it going?

Thx..

---

### Post by Partyboi2 on 2008-02-02
If you have a vista disk, try doing a repair with the vista cd

---

