---
title: "Read/write 64-bit chunks"
date: 2021-05-27
forum: Installation &amp; Upgrades
---

### Post by shahgols on 2021-05-27
Hi all, I have googled this but couldn't find an answer.  How do I install Ubuntu so that it reads/writes in 64k chunks?  Is it even possible?  Thanks in advance.

Edit:  sorry for the wrong title, it should be 64K, not 64-bit.

---

### Post by scorp123 on 2021-05-28
"64K chunks" of what exactly??  Disk? RAM? A file? Serial port? Your post is super vague.

---

### Post by grahammechanical on 2021-05-28
I think the issue will come down to Linux having drivers for the hardware you are thinking of. Whatever that is. Ubuntu will make use of the Linux drivers. This may be what you are thinking about. Read down to the section 16 parallel 64KiB random write processes.

[https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/)

> This time, we're creating 16 separate 256MB files (still totaling 4GB,  when all put together) and we're issuing 64KB blocksized random write  operations. We're doing it with sixteen separate processes running in  parallel, and we're queuing up to 16 simultaneous asynchronous ops  before we pause and wait for the OS to start acknowledging their  receipt.

If this guess of mine is inaccurate, then perhaps you could give some more explanation. From your post we do not even know if you are referring to Desktop Ubuntu or Server Ubuntu. Both will be using the same Linux kernel.

Regards

---

### Post by shahgols on 2021-05-28
Thank you very much and sorry for being vague, had a long day....   

I was asking about reading 64k from disk into ram, and writing 64k from ram to disk.

Graham, thank you for sharing the link, I'll take a look.

---

### Post by ActionParsnip on 2021-05-28
Just 64kb of random disk into a random place in RAM? What is the scenario here? What are you try to achieve?

---

### Post by shahgols on 2021-05-28
Hi, I am going to be setting up an Ubuntu Server for a PostgreSQL database application, and the more read/write performance we get, the better.

---

