---
title: "Gparted &quot;greys out&quot; the resize/move option"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2007-11-15
I have allocated way too little space to my Gutsy partition on a dual boot installation and somehow left a lot of unallocated space.

I fired up Gparted to resize the partitions but now find that the menu options are all greyed out eg. NEW DELETE RESIZE/MOVE COPY PASTE UNDO APPLY (except when I select the unallocated bit. That gives me the NEW option only)

The Gutsy partition is adjacent to the unallocated sector so I assumed that I could just expand it into the unallocated sector. But - no menu options are available!

What am I doing wrong?

Thanks

---

### Post by Sef on 2007-11-15
What are your file system of your partitions?  (e.g. ex3, reisferfs, etc.)

---

### Post by tact on 2007-11-15
you cannot edit partitions that you are booted from... or those that are mounted - either way options will be greyed out.  Are you booting from a liveCD and using gparted from the cd?

---

### Post by Buster95 on 2007-11-17
> **Sef said:**
> What are your file system of your partitions?  (e.g. ex3, reisferfs, etc.)
Thanks for the response. I have a multi boot arrangement with XP and two linux distros. All are in separate partitions. The linux partitions are Ext3.
Cheers

---

### Post by Buster95 on 2007-11-17
> **tact said:**
> you cannot edit partitions that you are booted from... or those that are mounted - either way options will be greyed out.  Are you booting from a liveCD and using gparted from the cd?

Thanks,
I know that I can't edit my working partition, but I don't seem to be able to access any partition. I'm uncertain about what you mean by "those that are mounted".

I re-booted into XP and used Partition Magic. It was able to manipulate the two NTFS partitions I have. Of course, in good MS fashion, it refused to have anything to do with the Linux partitions.

I had hoped that with either program, I could have enlarged an Ext3 partition by cribbing a bit (or inded all) of the unallocated space.

Cheers

---

### Post by zveroboy on 2007-11-17
Boot from live cd.  Unmount all the partitions on the hard drive in question.  Turnoff swap ```
#swapoff -a
```  Fire up gparted and you should be good to go.  

A few (ok more than few) words of caution:
In my case, after gparted finished moving/resizing all the partition it core dumped on me.  So, I am not sure if some of the problems that I've encountered afterwards were due to core dump.  Anyhow, after gparted was done UUID of the swap partition was changed.  I also moved/resized / (root) and /home partitions, but there UUIDs luckily didn't change.  So, look at your /etc/fstab file to see if instead of devices such as /dev/sda3 you have UUID=blablbal  .  If you have UUIDs and somehow they got changed after gparted was done, you may not be able to boot.  There are two ways to solve this problem.  1.  changed all the UUID=blbablalb entries to actual device entries.  However, I've read that this is not desirable - don't know why.  I have it like that on my desktop pc and don't really see any problems, but then again, what do I know -  I am new to Linux.  2. This option will only be useful only if you can boot your system back up ok, and just the swap partition isn't working (which what happened to me).  In that case, first, turn swap on  on your swap partition (e.g. ```
#sudo mkswap /dev/sda3
#sudo swapon -v /dev/sda3
``` )
where sda3 is your swap partition.  Note (-v is for verbose) 

after running mkswap you should see the new UUID of the partition.  Make a note of it, or better yet copy and paste it in the fstab fiile in place of the old UUID for this partition.

I hope this helps.  Let me know if you have any questions.

Oh, and one more thing: this may be an understatement, but please, back up everything you deem important before you resize/move partitions.

Laters.:guitar:

---

### Post by Buster95 on 2007-11-21
Thanks,
I'll think about plucking up the courage to try that.

If I understand you correctly, don't install GParted from the Synaptic Package Manager and don't launch it from the Systems Administration icon. Instead, I should go back to the partition editor on the live disk.

What then, is the point of installing Gparted if it doesn't  have the capability of performing any useful function? What benefit can it offer?

Cheers

---

### Post by zveroboy on 2007-11-21
Buster95, you are right you don't have to install GParted, but rather use it from the liveCD.  And, I understand your frastrationwith GParted, especially if you have used windows based partitioning tools such as Partition Magic.  The difference between GParted and Partition Magic, for example, (and as far as I understand) is that GParted tries to modify partitions right then and there on a live system, while PM records your commands then restarts (probably from some temp partition) and performs actions in Dos or Dos-like environment, then reboots back to Windows.  In effect GParted wants the user to boot from a different source (like liveCD for example), or attach the hard drive to another working system via USB/Firewire etc.  Otherwise, the use of GParted would be to partition/re-partition hard drives whose partions can be unmounted on a live system.  Obviously, it is impossible to unmount any partition that is currently part of a live system.  So, if add another hard drive to your system you may happily use GParted to partition it.  

Hope, this helps. :)

---

