---
title: "How to repair Ubuntu on Dual Boot netbook?"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by ondoin on 2012-03-17
I have a netbook with Windows XP and Ubuntu installed (same drive).
A week ago, I tried to update Ubuntu.
But when the screen saver was activated, the netbook freezed.
I tried everything to shut it down but nothing worked.
Finally I removed the battery. This worked.

Now when I try to boot Ubuntu, it will stop and crash.
The only way I found is to type startx (I think).

Then I tried to update Ubuntu again, but now it says that the upgrade file is corrupted.

Is there any way to repair it?
Can it be done with the Ubuntu CD, Boot Repair or System Rescue CD?

I can connect an external DVD.

---

### Post by sudodus on 2012-03-17
> **ondoin said:**
> I have a netbook with Windows XP and Ubuntu installed (same drive).
A week ago, I tried to update Ubuntu.
But when the screen saver was activated, the netbook freezed.
I tried everything to shut it down but nothing worked.
Finally I removed the battery. This worked.

Now when I try to boot Ubuntu, it will stop and crash.
The only way I found is to type startx (I think).

Then I tried to update Ubuntu again, but now it says that the upgrade file is corrupted.

Is there any way to repair it?
Can it be done with the Ubuntu CD, Boot Repair or System Rescue CD?

I can connect an external DVD.

Before doing anything else, it's a good idea to ***backup*** at least your private files and ***check your file system*** (the system partition / ) with e2fsck. Check what partition it is running the command ```
df
``` You must boot from another drive (I suggest a live session from your Ubuntu install drive. Do not mount any partition on your internal drive! And then run
```
sudo e2fsck -f /dev/sdxy
```
where x is a for the first drive, and y is 1 for the first partition /dev/sda1 and for example /dev/sdb5 for the fifth partition on the second drive.

Next step might be to use one of the repair CDs.

---

### Post by ondoin on 2012-03-17
I don't have any private files.

How to use the Live OR Repair CD?
I'm not very good with console commands.

---

### Post by sudodus on 2012-03-18
> **ondoin said:**
> I don't have any private files.

How to use the Live OR Repair CD?
I'm not very good with console commands.
I suggest that you try at least a little before resorting to re-installing.

If you installed Ubuntu from a desktop iso file via CD or USB, you can boot a live session from that CD or USB drive and 'test' the system instead of installing. In this live system, you can check for the file system and try to repair it.

You start a terminal window with the three keys ***ctrl + alt + t*** at pressed at the same time. Then you type your commands and start running them with the ***Enter*** key.

So, from your live system, please copy and paste the output of the following command to a reply window (in this thread)
```
sudo fdisk -lu
```
and you can try repairing the internal drive according to my previous post
```
sudo e2fsck -f /dev/sdxy
```
Read about the details again, or discuss it here after posting the output of the previous command!

Good luck :-)

---

