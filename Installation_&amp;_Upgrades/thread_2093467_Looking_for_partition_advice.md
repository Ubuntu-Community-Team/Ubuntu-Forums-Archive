---
title: "Looking for partition advice"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by singen on 2012-12-10
Hi everyone. I'm planning on migrating over to ubuntu but I have some concerns about how I should go about partitioning. Currently I'm using windows 7 (installed on a 120GB ssd) along with a separate 1TB hdd. Here is how I currently have things set up.

120GB SSD
-120GB Windows partition

1TB HDD
-300GB Applications
-200GB Media (music)
-200GB Work
-300GB General Storage
(I've rounded the numbers for clarity)

I'm going to be doing some python coding and web development and I'd like to install a vm for it. In my situation how would you guys recommend I set up my partitions?

Thanks.

(btw I have 12GB memory)

---

### Post by 1clue on 2012-12-10
If it's going to be a VM, don't change anything.  Find a spot with enough room and good filesystem characteristics and put your VM there.  The VM will be a file or files on the host filesystem.

---

### Post by singen on 2012-12-10
sorry, I should clarify that I'll be using ubuntu as my os (as in I'm replacing windows 7 with ubuntu) and likely another distro for the vm. I'm not sure how much space I need for vm, and that is the reason I mentioned it.

---

### Post by PapaNerd on 2012-12-10
Exclusive of VM, my root partition has about 17G used, so 50G or so would be more than generous for the OS.  Adequate swap space would be 2X the memory you have (or are planning) plus 10%.

---

### Post by singen on 2012-12-10
So then do you think it would be appropriate to set my entire ssd as root and the hdd in its entirety as /home?

---

### Post by sammiev on 2012-12-10
You can always keep your SSD for Win7 as a great backup if thing go wrong. Use the 1TB HDD for testing Linux OS as you can have multiple OS on the same drive. I have 3 Linux OS and one Windows OS all on the same drive.

---

### Post by Pjotr123 on 2012-12-11
No need for a hybrid solution if you configure the SSD right:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Then you can use the platter disk for simple mass storage. :)

---

### Post by cybrsaylr on 2012-12-11
> **Pjotr123 said:**
> No need for a hybrid solution if you configure the SSD right:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Thanks for the link.Lots of good info.
Recently got a SSD and am using it mainly as a boot drive for 12.04, with a 2TB HDD for mass storage. Was wondering what has to be done to keep the SSD from wearing out prematurely.

---

