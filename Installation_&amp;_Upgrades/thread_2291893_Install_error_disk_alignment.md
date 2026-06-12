---
title: "Install error: disk alignment"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by Kyrsa on 2015-08-23
[FONT=arial]Hey all, I experiencing an error while trying to install ubuntu on an external hard drive:
[B]The partition /dev/sdc2 assigned to /boot starts at an offset of 3584 bytes from the minimum alignment for this disk, which may lead to very poor performance.
Since you are formatting this partition, you should correct this problem now by realigning the partition, as it will be difficult to change later. To do this, go back to the main partitioning menu, delete the partition, and recreate it in the same position with the same settings. This will cause the partition to start at a point best suited for this disk.[/B]

I have been following this video:
[https://www.youtube.com/watch?v=JKL1tmn-xC0](https://www.youtube.com/watch?v=JKL1tmn-xC0)


I have a unformatted 1TB Seagate Backup Portable Drive and am booting from a seperate usb to install ubuntu.
When I open it in GParted it says the size is 931.51GiB

I have tried searching for how to fix this while partitioning the drive in the install menu and haven't found anything.
Any help is appreciated.



ps: I am brand new to ubuntu so I am sorry if I seem a little slow.
[/FONT]

---

### Post by oldfred on 2015-08-23
Another thread with similar issues on Seagate drive. 
I think Seagates do something unique?
[http://ubuntuforums.org/showthread.php?t=2291488](http://ubuntuforums.org/showthread.php?t=2291488)

Post this on whatever drive Seagate is seen as sdb or whatever.
       sudo parted /dev/sda unit s print

I always partition in advance with gparted and have not had issues, but do not have Seagate external drives. I also only use gpt partitioning to avoid the primary, extended, logical partition issue.

---

### Post by Kyrsa on 2015-08-23
Thank you for the reply oldfred. I saw the thread but i have not found a resolution. 
I think I am just going to return the seagate I purchased. Is there a recommended brand? I know there are mypassport's at bestbuy where I purchased it from, do you know of any issues installing to those?

---

### Post by oldfred on 2015-08-23
I do not have any external drives, so do not know.
I have just used flash drives & internal drives.

Some use Internal drives & USB caddies. But you have to be careful as some caddies only work with USB2 or only support smaller drives 2TiB or smaller.

---

