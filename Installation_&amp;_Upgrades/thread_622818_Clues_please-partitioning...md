---
title: "Clues please-partitioning.."
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by dooper on 2007-11-25
Hi all,
i have a newish Toshiba a120 Turion x2 lappy which has windows vista prem on it. I would like to dual boot and mainly use ubunto 7.10.  I am not fully skilled in the art of partitioning and formatting HDs.

I ran the live CD and got to the point where the partitioner runs.

i am then presented with the choice of 

prepare disk space-guided use entire disk space 120Gb ATA etc

OR Manual.

Now then,im guessing that i need to use MANUAL as i need to retain my working vista install.

So i select MANUAL.It then rescans and produces this.

device

/dev/sda      file sys    mount                  size                     used

/dev/sda1    ntfs      /media/sda1           1572                 524
/dev/sda2     ntfs     /media/sda2           60016               27700
/dev/sda3     ntfs    /media/sda3            58443               3200

now then,i suspect that sda1 is the hidden toshiba  re-instate your laptop to original as new software state although i also have a supplied backup DVD from Tosh.

sda2 must be my existing vista install

sda3 must be where i want to put my ubuntu install.

I am awary of proceeding past this point !

any clues please??

jo

---

### Post by Pumalite on 2007-11-25
In Vista, you have to allocate space for Ubuntu first, then install Ubuntu. Otherwise, Vista will not let you run anything in that computer.

---

### Post by dooper on 2007-11-25
OK thanks Pumalite,but what I'm saying is that i want to install it to the partition that is known as hda3 in the original post so i am just wondering how to progress from that particular screen on the install..I'm wary of messing up my vista and being unable to boot anything !

ta

---

### Post by Pumalite on 2007-11-25
The best thing is to go Manual and point to the exact partition you want. There a good scheme is:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home.

---

### Post by dooper on 2007-11-25
Thanks again Pumalite,,
unfortunately my enquiry is rather more basic in that i havent a clue how to proceed and would need a step by step guide !
I'll go and read...

---

### Post by Pumalite on 2007-11-25
It's not that difficult. When you choose Manual, you can choose your partition and start making the partitions I indicated to you inside of that partition you chose in the first place (the space you allocated for Ubuntu)

---

