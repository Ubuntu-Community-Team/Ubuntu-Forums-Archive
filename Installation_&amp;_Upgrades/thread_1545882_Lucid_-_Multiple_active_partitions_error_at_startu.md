---
title: "Lucid - Multiple active partitions error at startup"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2010-08-04
Hi folks,

I created a customized Lucid image and installed on my computer which has 1 hard drive (/dev/sda)
When I booted up .. it gave me an error indicating "**Multiple active partitions**" ... and did not boot up ...

I used my live CD and run as live session to check on the hard drive,  When I issued the command
***fdisk -l ***on an terminal , the out put indicated that only /dev/sda1 is bootable, and other /dev/sda* were
not bootable ... 

I am not sure why I got the **"Multiple active partitions"** message at boot up time ... Any suggestion where to look at ?

Thanks

Dang

---

### Post by Rubi1200 on 2010-08-04
Hi,
could you please boot the computer with the LiveCD and then click on the link at the bottom of my post.
 
Follow the instructions there and post the results back here.

---

### Post by uonedang on 2010-08-05
Thanks for the response ...

I will try  and post the result ... 

Thanks

Dang

> **Rubi1200 said:**
> Hi,
could you please boot the computer with the LiveCD and then click on the link at the bottom of my post.
 
Follow the instructions there and post the results back here.

---

### Post by uonedang on 2010-08-05
I have found the problem ...
I repeated the sfdisk command manually  which already ran when 
creating partition (option bootable check box default to be cheched).
 
Thanks
 
Dang

---

