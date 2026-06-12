---
title: "Partitioning"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by djw on 2006-07-08
I'm in the livecd right now getting ready to partition the rest of hd for the install.  It is currently giving me a message that I can't make more then 4 primary partitions.  But when I try to create a extended partiton that option is not availible. I only need the one last partition for my swap but I can't create it.  Can anyone help me?

---

### Post by tonyr on 2006-07-08
Does it show you what partitions are already there?  You might be able
to go back or start over and try manual partitioning to get that
information.

---

### Post by djw on 2006-07-08
Well I had 58 gigs of unpartitioned space on my hd which I'm planning to put Ubuntu on.  I have 2 other partitions I use for windows.  Then I need 1 partition for ubuntu and 1 partition for use between windows and Ubuntu.  So I have 4 primary partitions right there but I can't make my swap space.  Do I really need the swap space?

---

### Post by tonyr on 2006-07-08
Yes, you should have a swap partition.  Your original idea about
an extended partition was correct, but you can't do it from the
install process.  Restart the liveCD (at this point nothing has been
done to the disk), and use the Gnome Partition Editor
(**System->Administration->Gnome Partition Editor**) to create
the **Extended** partition and the **Logical** partitions inside
it for your other needs (including swap).

---

### Post by djw on 2006-07-08
I just quit the install and the option to create a extended partition is still greyed out and I can't select it.  Can I have more then one extended partition because I already have one.

---

### Post by tonyr on 2006-07-08
I don't know about multiple **Extended** partitions, but you shouldn't
need more than one.  Are there any **Logical** partitions already defined 
inside the **Extended** partition?

---

### Post by djw on 2006-07-08
yes and it is where xp boots off of, and is almost full at 24 gigs used out of 30.  

EDIT: I think I have it now, I resized tmy extended partition by a gig to put add my swap so now I have everything.  The problem was I think you can only have one extended partition.

---

### Post by cotcot on 2006-07-08
You have maximum 4 "primary partitions". If you want to use more than that you need "logical partitions". "swap" en "root" can be "logical partitions"; "boot" cannot.
If you want logical partions you need to create an "extended" partition in place of one of the 4 primary partitions.

So practically you can use under linux "fdisk" to create an "extended partition" for instance hda4. Then you can make with fdisk as well "logical partitions". These will be numbered starting from 5 (hda5, ...). You can use these /root, /swap or /home. So the extended partition hda4 is subdivided in logical partitions hda5, hda6, ... . Here is more information : [http://www.linuxhq.com/guides/SAG/x885.html]("http://www.linuxhq.com/guides/SAG/x885.html")

---

