---
title: "Grub Stalls on Boot"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by chriskirk on 2006-06-26
Hello,

I just installed Ubuntu 6.06 on my computer and after the installation is completed and after it restarts (yes I took the CD out) I am stuck on a black screen with the writing:

GRUB Loading stage1.5

And it just stays at that screen forever. Anyone have any idea what could cause/fix this? Any help would really be appreciated!

Thanks!

---

### Post by Craig Caldwell on 2006-06-26
Quote:
Originally Posted by vnbuddy2002
Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

This is the method i used to get grub working again.
make sure that you remount your / , /home , swap partitions.
scroll up to the mount in the partition option and hit enter.
you will then chose / or /home from a list.
after going through your / , /home and swap partitions save your changes by scrolling all the way to the way down to the bottom of the page for the save option. It wasn't obvious to me that there were more options when you scroll down
to the bottom.
After installing grub get into the shell and "reboot"
Do not continue with the install.
If things start happening that you don't want remember to use Ctrl -c to stop.

this is a simple solution that took me many hours of scouring the forums to get and then follow correctly.

good luck.

---

