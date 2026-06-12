---
title: "How to make larger swap file?"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Matriz on 2005-08-04
Okey so i have noticed that Ubuntu makes only about 128mg(or something like that) swap space and in windows i have about 500> megs of swap and also in SuSe(when i used it) ,so how i can change amount of spaw space? And there is also reason why i need to make it bigger ,bicuss i have "VM_Create on cgame" problem in ET and i have read that making swap make it work..and i thing making bigger swap space than 128megs would correct that...so iam sure someone can help me on this problem...I would be very pleased..and really i love how fast and good Ubuntu is and i dont want to go back to SuSe  :neutral:

---

### Post by scoon on 2005-08-04
Hey there, 

You need to create a partition that is the size of the swap that you want to have.  Then you need to mkswap on the partition and then turn your new swap on with swapon.

regards, 

scoon

---

### Post by heimo on 2005-08-04
[QUOTE=scoon]Hey there, 

You need to create a partition that is the size of the swap that you want to have. Then you need to mkswap on the partition and then turn your new swap on with swapon.

regards, 

scoon[/QUOTE]

But if creating larger swap partition is too complicated, you can use swap file too. (instructions: man mkswap), basicly you create a file using dd command and then initialize it using mkswap. For resizing partitions, use gparted or qtparted. (I've never used swap file in linux, I think swap partition is recommended.)

---

### Post by Matriz on 2005-08-04
Thanks both of you. Really fast action! Okey, i realized that when i installed Ubuntu i di d make only one partition what takes whole drive , so i didnt do any swap partition at all...so thats why Swap was so little...but i installed Ubuntu again and did partitioning right and now i have nice 756mg swap working. \\:D/  and well iam really new to linux(well i used SuSe 9.2-9.3 for about 6months and SuSe have Yast and all so its easy linux,so i dont have experience) at this point. And heimo i noticed that you are from Finland ,ja se on hieno homma ;p -Thanks

---

### Post by Matriz on 2005-08-04
YES! ET works fine and everything else too :) Ah,, iam so happy to get Ubuntu up and running!

---

### Post by heimo on 2005-08-05
[QUOTE=Matriz]YES! ET works fine and everything else too :) Ah,, iam so happy to get Ubuntu up and running![/QUOTE]

:) Great! I've seen several Finns on this forum, and I'm always glad to welcome one more.

BTW, I just had to make a larger swap for my puny mail server (128MB + 384MB swap), which was running out of memory during large batch job (teaching spamassassin bayesian filters from large amount of spam). For a quick solution, I created swapfile, steps were:

 ```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=$((16*65536))
sudo mkswap /swapfile
sudo swapon /swapfile

```

That 16*65536 is just a calculation - how many blocks of 64MB swap do I want? 16 * 64MB = 1024MB = 1GB

---

