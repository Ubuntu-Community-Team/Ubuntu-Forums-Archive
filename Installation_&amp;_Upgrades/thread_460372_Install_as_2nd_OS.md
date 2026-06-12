---
title: "Install as 2nd OS"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by penguin_ninja on 2007-05-31
Hi, 

I just receive Ubuntu in the mail today and i want to install it as a second operating system and not lose windows or any data. How do i go about doing this?

Thank You.

---

### Post by LoganHarbour on 2007-05-31
Read this, it should help.

[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)

---

### Post by penguin_ninja on 2007-05-31
Ok well i went to the site and got all the way to manually edit partition table....and then i was lost. help still needed.

thank you

---

### Post by reckless2k2 on 2007-05-31
Please tell me you defragged! 

If you got as far as now having an open space on the drive, just have ubuntu install on the "free" partition in the walk thru. I think the wording is largest free space. You don't want it it take over the whole partition. But after resizing you should have a free space now. Ubuntu largest free space option will auto create the swap and root directory. i think the fiesty version creates a home partition too.

---

### Post by penguin_ninja on 2007-05-31
Ok so once i defrag then i dont have to manually edit anything just let it do its thing and i should still have windows as a OS...

---

### Post by merlinus on 2007-05-31
Make sure you tell the partitioner to use free space, and not the entire disk!!!

-merlin

---

### Post by penguin_ninja on 2007-05-31
when i get to the prepare disk space step of installation all it says is Guided - Use Entire Disk under that is my hard drive then another option is Manual...

---

### Post by merlinus on 2007-05-31
Do not use Guided - use entire disk, or you will lose windows.

Is there not a Guided - use free space option?

If not, you will have to use some sort of manual partitioning.

-merlin

---

### Post by reckless2k2 on 2007-06-01
Ok....steps....again.....

step 1 - defrag windows partition

step 2 - SHRINK windows partition

step 3 - insert install disk and then select use largest FREE space to install. 


****if you are not getting the largest free space option, then you did not shrink your windows partition suing the program in the guide mentioned in previous post.******

---

