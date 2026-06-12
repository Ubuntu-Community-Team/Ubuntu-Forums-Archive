---
title: "GParted vs. Partitiion Magic on HP Pavilion"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by smradek on 2007-02-09
Hello.
I would like to install Ubuntu on my laptoop hard disc. Now there are this partitions:  
/dev/sda1 - ntfs - 102.28 GB, 10.42 GB (used), 91.86 (unused)  boot "Windows XP Media center"
not alockated - not alockated - 7.84 MB  -- --
 /dev/sda2 "!" - fat32 - 8.50 GB -- --   "Windows Recovery"
 /dev/sda3  - ntfs - 1GB, 9.78 (978.99 MB) - "QuickPlay"

I would like to reduce Windows size and to have Ubuntu (about 60GB) on recent /dev/sda1.
What do you recommend me. To use Gparted or to use windows Partition Magic  before installation?

I would like be able to boot to both "QuickPlay" and "Windows"  partition after instalation.

Which version: 6.06 or 6.10?
With live CD it works...problems only with partitioning since I don't know how to make recovery for QuickPlay partition. I made it only for Windows.

---

### Post by ola on 2007-02-09
Hi, 

Start off by doing a real backup of everything important!

When I repartitioned the drives (changed a 60gb ntfs partition to 3 partitions) on my computer the last time GParted worked really great. That's unfortunately all advice I can give you.

Good luck!

---

### Post by housam on 2007-02-09
Use Gparted for partitioning. it is perfect with both os. Defrag your windows partition 2-3 times .
You'll have to resize the windows partition to create an unallocated space ( let say 40 Gb). then transfere this unallocated space to a new extended partition. this partition can be divided to three or more logical partitions.
You need one partition for the root ( / ) ext3 format  ( more than 5Gb). a second partition as swap ( 1 Gb ) swap format. a third ext3 format as a /home partition ( the rest of the 40 Gb )
I suggest to install Dapper drake 6.06 live cd as it is more stable and suitable for newbies.

---

### Post by mikewhatever on 2007-02-09
Hi smradek, 
it does not matter how you resize the first partition. You may even want to start with one of the tools and finish with the other. I used GParted, and it took about 10 seconds to complete the resizing job. I should mention that I have an HP Pavilion 5000. You really need to defragment the partition before resizing. I remember even using Diskeeper trail version, since it does a better job. It is also a good idea to run CHKDSK. I was not able to resize before that done. 
> I would like be able to boot to both "QuickPlay" and "Windows" partition after instalation.

Unfortunately, this feature does not work from 'cold start'. Apparently, Quick Play partition is seen, but not recognised by GRUB. I've tried using it from Windows, and it works, but not by itself.

> Which version: 6.06 or 6.10?

As you can see, I have 6.10, and am happy with it. There should not be too much difference.

Having made HP Recovery DVDs, I have not backed up any of the partitions.


Good Luck and Welcome

---

### Post by smradek on 2007-02-09
Thanks.

I know tried using Partition Magic but it fall down after 983 error (too much errors).

Do you think that it is save to use GParted???

---

### Post by housam on 2007-02-09
Yes it is safe.

---

### Post by smradek on 2007-02-09
even if I tried it with live Ubuntu (DVD Kubuntu 6.10 amd64) and it crash down. No error message...?

---

### Post by mikewhatever on 2007-02-09
Remember to run CHKDSK check in Windows first.

---

### Post by smradek on 2007-02-11
> **mikewhatever said:**
> Remember to run CHKDSK check in Windows first.

Thanks it finally worked! And after everything I installed both system on my laptop and everything work!!!

[http://www.ubuntuforums.org/showthread.php?p=2136459#post2136459](http://www.ubuntuforums.org/showthread.php?p=2136459#post2136459)

---

### Post by mikewhatever on 2007-02-11
I am glad you solved it. It seems that not too many people have the CHKDSK/resize issue, but it comes up every now and again.
Since you have a similar setup, I thought I'd give you another advice. You probably have Window recovery partition mounted in /media/sda2, and an icon on the desktop. Since the recovery partition is FAT32, it is both readable and writable from Ubuntu. Obviously, it is not desirable to edit that partition, and the best thing is to permanently unmount it. I've asked how to do it in [this tread]("http://www.ubuntuforums.org/showthread.php?t=337050&highlight=permanently+unmount")
Do not delete any lines from fstab. Scroll to the bottom of the thread and read bodhi.zazen's instruction.

Now is the time to explore it, but do not expect too much.

---

### Post by smradek on 2007-02-12
Thank you very much.

I didn't know what problems could I have with FAT32 Recovery partition, so thank you very much for recomend.
What did you mean by > **mikewhatever said:**
> Now is the time to explore it, but do not expect too much.
Are you talking about system or about Recovery partition?
Did you have also problem with wifi? How could I found it? What manager do you use? And what about 2  the most important  things for (when travel) me:
Could you change your screen brightness by pressing combination of "Fn" and one of function keys?
Did you have the problems with headphones and microphone? - Nothing changes than both are put into the jack....

Thanks

---

### Post by mikewhatever on 2007-02-12
Hi smradek,
By that sentence you quoted, I only meant that, while Ubuntu is a good OS, is is not void of problems. Your latest post indicates you've already encountered some.
I also had wifi problem, and while the sound worked both from speakers and from headphones, I had to take care of the microphone to use skype. The brightness keys (Fn+Little Sun) do work. Is you laptop intel based? Do you know what your wifi and sound cards are?
For example, mine are: Intel wireless 3945 and Intel hda.
Type 'lshw' in the terminal to get all your hardware listed.

---

