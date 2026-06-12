---
title: "UUID and Grub"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by pgmer6809 on 2012-09-05
Q1. In /boot/grub/grub there are many references to a UUID.
Where does grub get this reference? I would like to change the source and then run update-grub.
I prefer not to edit the grub file manually because then when I do run update-grub the UUID will come back.

Q2. There are some obvious drawbacks to using UUID's in grub and fstab, but what are the advantages for a home desktop user?
I can't think of any but there must be some.

pgmer6809

---

### Post by YannBuntu on 2012-09-05
Do you want to remove UUIDs from /boot/grub/grub.cfg ? why ?

AFAIK there are no drawbacks to using UUID wherever.

---

### Post by drmrgd on 2012-09-05
> **YannBuntu said:**
> Do you want to remove UUIDs from /boot/grub/grub.cfg ? why ?

AFAIK there are no drawbacks to using UUID wherever.

Yes, I have to agree with this!  The idea behind UUID is to stabilize the mounting process so that the system will always know where to look for a drive, regardless of any other system changes (changing volume labels and whatnot).  It would be (IMHO) counter productive to circumnavigate this, unless there was an explicit reason to do so.

---

### Post by oldfred on 2012-09-05
Grub & fstab used to use device like /dev/sda5 but then users would add another drive and it became sdb5 or they changed partitions and and it became something else. So UUIDs are more stable.

UUIDs do not normally change, but deleting & recreating a partition creates new UUID or full image copy to another drive may create duplicate UUIDs which can be a problem.

A third choice is label. Most installs & fstab also support the use of labels.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by JKyleOKC on 2012-09-05
> **pgmer6809 said:**
> Q1. In /boot/grub/grub there are many references to a UUID.
Where does grub get this reference?I agree with OldFred and YannBuntu that removing UUIDs would be a step backward, but it's your system. To remove them from the grub.cfg file and the grub menu, go to /etc/default/grub, in super-user mode, and find these lines: ```
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

```Remove the "#" from the second line, save the file, and run update-grub. The UUID references should be replaced by device names.

---

### Post by pgmer6809 on 2012-09-07
> **YannBuntu said:**
> Do you want to remove UUIDs from /boot/grub/grub.cfg ? why ?

AFAIK there are no drawbacks to using UUID wherever.


Yes I want to remove them.
1. The drawback is that if I backup my disk drive, and then it fails and I have to replace it and restore the backup to another drive, the other drive will have a different UUID.
The grub will no longer work. 
I have had this problem before where I wanted to transfer the contents of one drive to another, but doing so broke a bunch of stuff because the UUID's of the drives were not the same.

2. UUID's are very user unfriendly. I know which of  my drives is 'a' and which is 'b'. I know which partition on each I have assigned to what. I have no clue which UUID applies to what and I don't want to have to remember a UUID.

3. I can see NO advantages for a home desktop user to UUID's. Wikipedia mentions that there are advantages in distributed configurations where you do not always know which disk gets discovered first by the hw detecting program but that does not apply in my case.
In any case we used to have that issue with dual ethernet setups where you could never tell which adaptor would be eth0 and which would be eth1, but the Network folks seemed to have solved that without resorting to UUID's.

4. The Wikipedia article mentions that an alternative to UUID's is to use Label=xxxx.
This would be acceptable to me as Labels are both user friendly and under my control, i..e I can assign the same label to the replacement drive. 
UUIDs are NOT under my control, and one of the main reasons I run LINUX is so that I do have control of my machine.

I have absolutely no interest in debating this matter further; UUIDs may be fine for some people; they are not for me, unless there is some advantage I don't know about yet. 

SO back to the original question; What is the best way to get rid of the UUIDs in the /boot/grub/grub file ?
pgmer6809

---

### Post by oldfred on 2012-09-07
Just change fstab to use devices and grub's file as posted above.

---

### Post by Guilden_NL on 2012-09-07
> **oldfred said:**
> Just change fstab to use devices and grub's file as posted above.

:D  Yep....I went to answer and JKyleOKC had already taken care of it.
And, I've held my tongue on the hard left turn into the brick wall regarding not going the UUID route.

---

### Post by pgmer6809 on 2012-09-07
> **JKyleOKC said:**
> I agree with OldFred and YannBuntu that removing UUIDs would be a step backward, but it's your system. To remove them from the grub.cfg file and the grub menu, go to /etc/default/grub, in super-user mode, and find these lines: ```
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

```Remove the "#" from the second line, save the file, and run update-grub. The UUID references should be replaced by device names.


Thank you, that is exactly what I needed to know.
pgmer6809

---

### Post by JKyleOKC on 2012-09-08
You're quite welcome.

You said earlier that you want full control. If that's really true, then you should avoid using the /dev/sdXX notation also! That's not really under your control, since program updates have been known to change the order in which the drives are queried during the boot process. The forums have a number of examples in which a drive's "sdxx" number gets reported differently by different programs.

This is likely to only get worse, as the boot process morphs from the totally sequential SysV tradition into the parallel-process Upstart system. Just having a flash drive plugged in at boot time can potentially change the /dev names that are assigned.

For full control, use the LABEL= option, since you and you alone assign the label and it won't depend on sequence of access or anything else...

EDIT: And if you do switch, be sure to edit fstab also -- and verify that the new one is working properly, via "sudo mount -a" before rebooting. Otherwise you might wind up with a system that would not boot!

---

### Post by YannBuntu on 2012-09-09
For information:
- one can get the UUIDs list via the "sudo blkid" command
- on some computers, sda disk can become sdb, and sdb becomes sda, just after a simple reboot.

---

