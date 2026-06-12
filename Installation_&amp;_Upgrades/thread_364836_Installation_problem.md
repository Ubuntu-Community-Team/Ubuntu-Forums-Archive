---
title: "Installation problem"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Willie G on 2007-02-18
I am having trouble installing Ubuntu on my laptop.
I have one 25 gb partition for windows, one 6 gb
recovery partition and a new 24 gb. partition I made 
after shrinking my original primary partition.

I hope that I don't have to set up any more partitions
because I cannot shrink my newly created partition to
create any more unallocated space and I don't want to
cut up my Windows partition any more.

I'm trying to use the manual setup option in step 5.  I 
get three menus on the left that I can choose /, home, 
boot, user etc.,  and three menus on the right that I set
to the new partition I created.  No matter how I set the 
menu on the left, I get a message "A partition is assigned
to more than one mount point   no root file system".

Can anyone tell me how to proceed or point me to a
good walkthrough on this?

Thanks

---

### Post by Kateikyoushi on 2007-02-18
You need at least two partitions a / and a swap.
Can find an installation guide here. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Willie G on 2007-02-18
> **Kateikyoushi said:**
> You need at least two partitions a / and a swap.
Can find an installation guide here. [LINK]("http://www.psychocats.net/ubuntu/installing")

I saw that link, and in the example "prepare disk space" there are three choices
resize ide1 master, erase the entire disk or manually edit the partition table,
but when I installed I got only two choices, to erase the entire disk or manually
edit.  I did not receive the choice to resize the IDE1 master.
Also, in the link [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) I noticed that the
partitions there had file systems "extended, ext3".  When I create any partitions
in Windows disk manager, I can only choose the file systems ntfs or fat32.

edit:

I now have four free partitions, one 20gb, one 700 mb and two 300 mb
but again I can only format them to ntfs or fat32, not the extended or ext3
file systems shown in the installation guide.

---

### Post by Kateikyoushi on 2007-02-18
You do not need so many partitions, you can freely delete them from the windows disk manager because it can not make ext3 partitions.
The ubuntu installer can create the partitions for you. I would recommend one 1GB swap partition and leave the rest for /.

---

### Post by Willie G on 2007-02-18
I finally did the install, now when I start up, there's no grub menu.
It just boots straight into Ubuntu without giving me any choices.
I've got a long night ahead of me.

edit
I can get the grub menu by hitting esc during bootup,
but I don't see Windows Vista in the boot up menu.
I suspect that this is a Windows problem and not a 
Linux problem.

---

### Post by Kateikyoushi on 2007-02-18
Grub should have detected your windows install and add it automatically but it can be added now as well.

Read this howto. [LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_add_Windows_entry_into_GRUB_menu")

---

### Post by Willie G on 2007-02-19
> **Kateikyoushi said:**
> Grub should have detected your windows install and add it automatically but it can be added now as well.

Read this howto. [LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_add_Windows_entry_into_GRUB_menu")



I have it working now  Thanks very much for your help.

---

