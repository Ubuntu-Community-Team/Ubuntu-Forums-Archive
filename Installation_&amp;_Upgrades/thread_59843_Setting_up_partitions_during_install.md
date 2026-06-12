---
title: "Setting up partitions during install"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by sx460 on 2005-08-25
Is there a way to configure/create/setup partitions while installing Ubuntu/Kubuntu or is it just 100% automated? I a 200GB drive and would like to to the following (or something similar):

40GB /home (documents, pictures, ...)
40GB /backup (applications, downloads, ...)
80GB /MP3s
38GB /
2GB SWAP

Does this setup make sense to you guys? Any suggestions? Also, how can I do this while setting up/installing Ubuntu/Kubuntu?

---

### Post by humanity_to_others on 2005-08-25
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)

---

### Post by Buffalo Soldier on 2005-08-25
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by sx460 on 2005-08-25
Thanks for the links guys! In the following link it says "Make your way to the partitioner": [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning). Sort of vague, I don't have my computer in front of me now (or the install CD), will the path to the partitioner be pretty obvious? Thanks!

---

### Post by John.Michael.Kane on 2005-08-25
I have a 40GB what would be the best way to set it up.. Ubuntu will be the only os used.. no windows or m$ based os'es

---

### Post by Lambert on 2005-08-25
[QUOTE=sx460]Thanks for the links guys! In the following link it says "Make your way to the partitioner": [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning). Sort of vague, I don't have my computer in front of me now (or the install CD), will the path to the partitioner be pretty obvious? Thanks![/QUOTE]

After it mounts your drive and reads the files it comes to a page with three options I believe. The bottom option being manually edit partions or something similar.

---

### Post by Lambert on 2005-08-25
[QUOTE=SD-Plissken]I have a 40GB what would be the best way to set it up.. Ubuntu will be the only os used.. no windows or m$ based os'es[/QUOTE]

When i was asking this same question months back I was given advice to partion 7GB of the drive to / 
double my ram to a swap partion 
and the rest to /home

---

### Post by John.Michael.Kane on 2005-08-25
7gig=swapfile
and the rest of the drive is for home .. theres no other options i did not think i would have to allocate that much space for home

---

### Post by Lambert on 2005-08-25
[QUOTE=SD-Plissken]7gig=swapfile
and the rest of the drive is for home .. theres no other options i did not think i would have to allocate that much space for home[/QUOTE]

7 gig to  root represented by / not to the swap file. I have 256mb of ram and a 750mb swap partition. The more ram you have you can actually lower your swap file file size.

You don't have to allocate the rest to /home. I have some space set aside to back up some files and a partition to play with other distros. What ever size you think is needed to store files for users. There are other options but these basic three / ; swap ; /home is all that's really needed.

---

### Post by John.Michael.Kane on 2005-08-25
i have 512mb ram so i could have 128mb swap file

---

### Post by yesplease on 2005-08-26
@sdplisken

Most people suggest to use two times the RAM you have for swapspace.
However, this is a rule of thumb and depends on the kind of work you do. 

Moreover, there is a maximum to this "rule', I have read often that if you have one GB of RAM most users wont need any swap space at all.

All processes use memory, when most of your RAM memory is in use swapspace on the harddisk is used. When you do not have enough swapspace you may encounter problems. Even when most of these problems may be temporary, they will be confusing and erratic. This will cost you a lot of time becauase you and the helpfull people here wont consider a lack of swapspace as the source.

Even though I ended here with a prediction, please keep in mind that I am new to Ubuntu and welcome any corrections on this post.

---

