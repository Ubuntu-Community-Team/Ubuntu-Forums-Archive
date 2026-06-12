---
title: "[SOLVED] Increasing pagefile size"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by zombrax on 2008-04-21
A newbie question.. how do i increase my pagefile size? As it is, running on 128MB of RAM is soooo slow its not funny. Where can i go to increase the virtual memory so that maybe it might my system not to run too slow?

More RAM is on the way but in the mean time.. ??

thanks in advance :)

---

### Post by Partyboi2 on 2008-04-21
Create a swap file, try [this]("http://www.astahost.com/index.php?showtopic=2815")

---

### Post by zombrax on 2008-04-22
> **Partyboi2 said:**
> Create a swap file, try [this]("http://www.astahost.com/index.php?showtopic=2815")

thanks for this.. however when trying to login as su

i simply cannot understand why it wont take my root password! to test that my password works i tried to go through administrative tasks to open up an administrative process which asks me for the password. when i put in my root pswd, it accepts it without any probs. so why wouldnt it go through the terminal. this is the error msg;

zombrax@ub-lap:~$ su -
Password: 
su: Authentication failure
Sorry.
zombrax@ub-lap:~$ su -

could someone help please? many thanks in advance.

---

### Post by Partyboi2 on 2008-04-22
use sudo instead of su

here is another small how to that might be easier then the one I posted previously.
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by zombrax on 2008-04-22
oops i get this err msg.. do i create that dir manually?

zombrax@ub-lap:~$ sudo dd if=/dev/zero of=/SWAP.img bs=1M count=512
512+0 records in
512+0 records out
536870912 bytes (537 MB) copied, 51.02 seconds, 10.5 MB/s
zombrax@ub-lap:~$ losetup /dev/loop5 /SWAP.img
/SWAP.img: Permission denied
zombrax@ub-lap:~$ sudo losetup /dev/loop5 /SWAP.img
/dev/loop5: No such file or directory
zombrax@ub-lap:~$

---

### Post by Partyboi2 on 2008-04-22
Instead of using loop5 try using loop0
```
sudo losetup /dev/loop0 /SWAP.img
```

---

### Post by zombrax on 2008-04-22
i think i've done it mate... could you pse double check to see that i've done it correctly? BTW, the free -m command lists the results in MB i take it??

zombrax@ub-lap:~$ sudo losetup /dev/loop0 /SWAP.img
zombrax@ub-lap:~$ mkswap /dev/loop0
/dev/loop0: Permission denied
zombrax@ub-lap:~$ sudo mkswap /dev/loop0
Setting up swapspace version 1, size = 536866 kB
no label, UUID=6ec09da6-233c-4e23-ba57-1119792d1f3b
zombrax@ub-lap:~$ sudo swapon /dev/loop0
zombrax@ub-lap:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           107        103          3          0          0         25
-/+ buffers/cache:         77         30
Swap:          825        106        718
zombrax@ub-lap:~$

---

### Post by Partyboi2 on 2008-04-22
Looks ok to me. Using the -m option gives it in mb, you can also use  -k (kilobytes) or -b (bytes) or -g (gigbytes) depending on what takes your fancy.

---

### Post by zombrax on 2008-04-22
um turned the laptop on this morning and did a free -m check; looks like its gone back to the old settings!!

zombrax@ub-lap:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           107        104          2          0          0         33
-/+ buffers/cache:         69         37
Swap:          313         44        269
zombrax@ub-lap:~$ 

how can i get my swap to remain the same??!! thanks once again.

---

### Post by Partyboi2 on 2008-04-22
Did you add it to  /etc/init.d/rc.local like it mentions at the bottom of the page?

---

### Post by zombrax on 2008-04-23
oops just tried to do that after running the whole thing again and get this err msg.. any ideas please?

zombrax@ub-lap:~$ sudo losetup /dev/loop0 /SWAP.img
ioctl: LOOP_SET_FD: Device or resource busy

---

### Post by zombrax on 2008-04-26
any more ideas for this guys? many thanks in advance..

---

### Post by zombrax on 2008-04-30
no further solution to this problem gurus? :)

---

### Post by Partyboi2 on 2008-04-30
did you try the other link I provided for creating swap? It is a slighlty different way of doing it. Here is the link again
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by zombrax on 2008-05-02
many thanks partyboi2 for your dedicated help mate. gonna send you a pm as well. after about a couple of weeks this prob is now solved. thanks to others as well :)

---

