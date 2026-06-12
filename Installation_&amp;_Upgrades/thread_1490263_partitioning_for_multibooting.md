---
title: "partitioning for multibooting"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by rockette morton on 2010-05-22
hi!

i've been trying to partition my disk for multibooting - two windows xp installations, one ubuntu, and getting grub to handle each separate installation.  i've had some success in doing this, however i decided to make things a little more difficult for myself by installing ubuntu studio as well on a separate partition.

the way i've set it up is as follows: (1) i partitioned my disk, installed xp on the first primary partition.  

(2) moved the boot flag to the second partition and installed the second xp there.  

(3) moved the flag again, now to the third partition.  i converted the third partition into a logical volume in lvm format (using the ubuntu studio 10.04 alternate cd), creating two volumes - one for swap, one for root.  i did not install grub.

(4) this time i did not move the boot flag. converted the fourth partition to lvm, 2 volumes again - one for swap and one for root, this time with the ubuntu 10.04  alternate cd).  installed ubuntu, now installed grub and let it write to the master boot record.

the weird thing is that it boots okay, and does what i intended it to - i.e. boot each installation from grub.  but i get errors, and that bothers me.  first, before i get to grub, i receive the following error: 'error: no such disk'.  second, i get this error after selecting ubuntu 10.04 from the grub menu: 'udevd-work[92]: inotify_add_watch(6, /dev/sda4, 10) failed: No such disk or directory.

i will attach my boot info script results if these are any help.
if anyone could shed any light on this, i would be very grateful.  i'm at the point where i've done a clean installation of everything on this disk, so i'm happy to tinker about as much as i need to.

many thanks!
tim

---

### Post by darkod on 2010-05-22
Hmmm... From my (limited) knowledge of LVM I thought you need separate /boot partition outside the LVM. At least a few guides I read said that. :)

But it seems the boot process if working fine for you without one.

On another note, you didn't need to move the boot flag again before installing the Studio LVM. Only windows depends on the boot flag, not ubuntu. In fact, that makes it possible to dual boot because the boot flag stays on the windows partition.

Do you think that could have made the difference that errors are reported for Studio and not for Ubuntu? You didn't move the boot flag to Ubuntu before installing it. Just guessing here.

The script results definitely doesn't like something about the Studio LVM. It's not reported the same as the Ubuntu LVM.

---

### Post by oldfred on 2010-05-22
I also know nothing about LVM. I thought the advantage was to allow easy resizing of partitions as needs change. But I would use that for data partition(s). 

As Darko says linux does not use the boot flag. Some BIOS do require the boot flag on a primary partition (they assume windows).

I do not know if the messages at the end of the boot info script say there is an issue with your LVM or just that the script cannot fully process it.

Since I bought a new drive about 9 months ago, I reorganized, and moved /home out of root and then moved all data folders into /data. I now find my root is about 6GB with lots of programs, my /home is about 1GB with years of hidden settings accumulating and some misc data that is not yet in the /data partition. With that I do not see root, swap nor home changing much in size and little or no advantage to having them in a LVM. I do have some data in a NTFS shared partition and possibly see where as I have moved away from windows and needing data in NTFS for sharing, to Ubuntu and just having data in /data might be easier with LVM. But I have just resized occasionally.

---

### Post by rockette morton on 2010-05-22
thanks, guys.  i can't help but think that there might have been a much better way of doing this.  i was a little unsure about using lvm, i must admit.  the reason i went down that route was because i was thinking i was not going to be able to partition it any other way - i.e. with more than four primary partitions.  could i have simplified things for myself?  i understand that the two ubuntu installations could have shared a swap partition - is this correct?

my data (and /home directory) will be on a separate hard drive.  i just haven't got that plugged in at the moment while i'm formatting volumes - just for peace of mind!

so . . . do you have any suggestions as to how i might have done this better?  it's all a learning curve for me so i'm quite happy going back and re-jigging things.  any advice is as always much appreciated.

many thanks,
tim

---

### Post by oldfred on 2010-05-22
Only windows and a few other distributions require primary partitions. You can install Ubuntu to logical partitions inside an extended partition which is one of the four primary.

I do not know GPT, but it is used by Apple and some windows servers. It does not work with XP. I believe 7 will read GPT but may not boot from it. With GPT all partitions are primary and it supports drives over the MBR partition limit of 2TB.  

You can share swap unless you want to hibernate. Then swap will get overwritten and hibernate will not work.

---

### Post by darkod on 2010-05-22
If your only worry was the 4 primary partitions limit, yes, there was a much better way.

Although I like LVM too, if nothing else, because of learning the system.

Yes, swap partition would have been shared between two ubuntu (or other linux) installs. You can have only one booted at any time, so it takes the swap.

Also, ubuntu doesn't need primary partition, only windows. Windows doesn't need it also if you can manage to put the boot files on primary partition, but lets not get into that.

So, one example how you could have done this:

/dev/sda1   XP
/dev/sda2   XP
/dev/sda3   extended
/dev/sda5   studio
/dev/sda6   ubuntu
/dev/sda7   swap

If you are using grub2 on the MBR, the above should work fine. If you plan chainloading from EasyBCD and having grub2 on the root partition, I'm not sure you can do that if the root partition is logical.

Also, when installing studio and ubuntu, you need only one grub2 so you can plan which to install first and during the second install select not to install a bootloader by hitting the Advanced button in the last screen of the installer.

And moving the boot flag to make windows put the boot files for each XP on its own partition was a great move. :)

---

### Post by rockette morton on 2010-05-22
many, many thanks.

oldfred - thanks for your insight once again! i'm just confused now about GPT.  am i using GPT?

darkod - many thanks also.  i think i will follow your example pretty much to the t.  if i just blow away my current sda3 and sda4 and start from there - that shouldn't cause any problems (with the other existing xp partitions) - should it?  i will agree, moving the boot flag when installing xp was a great move, and one i give credit entirely to oldfred, from an older post.

---

### Post by darkod on 2010-05-22
> **rockette morton said:**
> many, many thanks.

oldfred - thanks for your insight once again! i'm just confused now about GPT.  am i using GPT?

darkod - many thanks also.  i think i will follow your example pretty much to the t.  if i just blow away my current sda3 and sda4 and start from there - that shouldn't cause any problems (with the other existing xp partitions) - should it?  i will agree, moving the boot flag when installing xp was a great move, and one i give credit entirely to oldfred, from an older post.

Be careful when deleting linux from a computer. If you are using grub2, and you are, it won't be able to boot once the ubuntu partition(s) are deleted.

However, if you do it all in one step, it shouldn't be a problem. Boot into live mode, delete the partitions with Gparted, click the Install icon on the desktop of live mode, and install for example ubuntu desktop. Let it install grub2 to the MBR.

It should work out fine. Boot all three systems to check.

After you're happy, just add studio without installing grub2. Boot ubuntu and do update-grub.

---

### Post by oldfred on 2010-05-22
Sorry did not mean to confuse you with GPT. It was just your comment about wanting primary partitions and that will be the new standard. Except for those that still run XP will still need a MBR partition hard drive. 

They just announced a 3TB drive and part of the concern is that it will have to be GPT and few understand it. So someone will try to install XP and when it does not work blame the new drive.

Partition planning is very important, and each user has different needs. Even over time I have found I want different layouts but usually by then I have a new drive, so it becomes easier to reorganize & houseclean.

---

### Post by rockette morton on 2010-05-22
oldfred - thanks for the info!

darkod - pleased to say i am now up and running, can boot neatly from all partitions from the grub menu, no errors or problems.

thank you both for your help throughout, when many people would have just said, why bother?  hope you both have a pleasant evening!

tim

---

