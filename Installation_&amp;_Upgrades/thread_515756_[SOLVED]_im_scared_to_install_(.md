---
title: "[SOLVED] im scared to install :("
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by Aesir09 on 2007-08-02
last time i used norton partitoner and had to  go through A WHOLE LOT OF ****, to say the least, i understand that within the installer, for 7.04, 

there is a partioner so once i install and when my computer boots up will i be asked if i want to use winblows or ubuntu? im pretty sure but yeah....

---

### Post by Takmadeus on 2007-08-02
Yeah, the install program inside the live cd allows you to do the partitioning, plus it installs grub so you can choose between ubuntu and windows. it is pretty safe and it does not need any other partitioning program

---

### Post by Aesir09 on 2007-08-02
thanks man.

and when the partitoner comes up in the install, with the bar and percentage you are resizing your current HDD and making IT smaller correct?

---

### Post by zuzuzzzip on 2007-08-02
uhm no?

ur creating a partition for ubuntu to install on, because it's another filesystem then windows. make sure you select a swap partition too.
That's all there is to it :)

---

### Post by Warren Watts on 2007-08-02
I would suggest defragmenting your hard drive(s) first, and you may want to back up any important files before you start the install...

I'm not trying to scare you suggesting this; it's just a good idea.   You never know what could happen, and you are better safe than sorry!

In my personal experience, installing Ubuntu went faultlessly.  But I have seen a lot of threads posted here where people experienced problems with grub (the boot loader).

---

### Post by Aesir09 on 2007-08-02
[IMG]http://i71.photobucket.com/albums/i141/Bodomshadow/Screenshot-Install.png[/IMG]

All i want to do is have **20GB for my ubuntu partition....?**

---

### Post by Warren Watts on 2007-08-02
I'm installed Ubuntu on a 10GB partition, and after 10 weeks, I still have 47% of the 10GB still available, so 30GB should be plenty of space.

---

### Post by Aesir09 on 2007-08-02
i put this bar all the way to the left and it reads:**49%(53.7GB)**

i put this bar all the way to the left and it reads **100%109.5GB**

my HDD is like 111GB, and has 50GB or so free.... and i want to use 20GB for the ubuntu partition.... HELP

---

### Post by merlinus on 2007-08-02
Have you tried the Manual option?  It will allow you to specify partition sizes.
-merlin

---

### Post by dabl on 2007-08-02
If you really want to get total control and visibility of the partitions and partitioning process, download and burn a GParted Live CD from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

After you've run defrag and disk cleanup in Windows, boot the GParted CD, arrange your partitions the way you want, and then "apply" and exit.  Then boot your Ubuntu CD and do "guided installation" to set your mount point(s) as you wish.  :)

---

### Post by tadada on 2007-08-02
you could also use the alternate CD it's text based and when you go to install you do get the option of shrinking the existing partition (I'm sure on the live CD you do get the option too but I don't know how to use the Live CD. I skipped and when right to the Alternate). So you shrink the existing the configure a small partition as swap (like 1 gig) and then configure the rest of the space you freed up as the Ubuntu boot partition and mount it to root.

---

### Post by Tadmen on 2007-08-02
How come that when I tried to install it on a windows vista laptop I did not get an option for resizing  a partition?
It only showed me Guided: 120GB SCSI partition and Manual option.

I'm afraid to proceed so as not to wipe out my vista partition

Tad

---

### Post by merlinus on 2007-08-02
If using vista, then use its disk manager to shrink its partition and make space to install ubuntu.  

Beforehand, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back to original size after installing ubuntu), and defrag several times.

-merlin

---

### Post by Aesir09 on 2007-08-02
ok guyz, look at the picture i posted on the first page and the percents and what not and tell me if im resizing my windows partition or if i am creating one!

im almost 90% sure im resizing my winblows partition

---

### Post by Jeremywilms on 2007-08-02
Well I was forced to clean install after ubuntu messed up my computer, I could say I am still going through ****. and "I whent through alot of ****"

---

### Post by zuzuzzzip on 2007-08-03
> **Aesir09 said:**
> ok guyz, look at the picture i posted on the first page and the percents and what not and tell me if im resizing my windows partition or if i am creating one!

im almost 90% sure im resizing my winblows partition

I also think it will use your free space on the disk to create a partition.
I don't like something else resizing my partitions so I chose manual, you get a clear view on what options you have there, you can always hit the back button if you're to confused.

---

### Post by Aesir09 on 2007-08-03
acutally you didnt have to clean install, but good choice anyways,

**POST CLOSED PROBELM SOLVED. ALL IT DOES IS RESIZE YOUR CURRENT PARTITION AND USE THE FREED SPACE, THANK YOU**:lolflag:

---

### Post by apswartz on 2007-08-03
Use the thread tools to mark the thread "Solved"

---

