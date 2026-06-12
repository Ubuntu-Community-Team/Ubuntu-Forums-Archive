---
title: "invalid partition table (no os now)"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by eslam elbyaly on 2012-06-10
hi all , i had ubuntu on my pc , and i was trying windows xp beside ubuntu , 
- i had c ,d  partitions (c) for windows copy , (d) for my data and the two partition for ubuntu , one for the system and the other for swap space 

- when i tried to install xp on c partition after formatting it , i got this error (invalid partition table 

i deleted (c) partition , and made it again from the unpartitioned space , and the error still exist ,
- i deleted all partitions (ubuntu partition , swap partition , (c) partition ) , and now i do not have anything on my hard disk except the (d) partition for my data , and the rest of my hd is unpartitioned space , and i can not install xp , which is the osi wanna install 

help quickly , please

---

### Post by dino99 on 2012-06-10
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by eslam elbyaly on 2012-06-10
thanks for your prompt reply , but i am sorry you did not get ,

[SIZE=4]_**i have no operating system now , just my data on d partition **_[/SIZE]

---

### Post by wilee-nilee on 2012-06-10
> **eslam elbyaly said:**
> thanks for your prompt reply , but i am sorry you did not get ,

[SIZE=4]_**i have no operating system now , just my data on d partition **_[/SIZE]

Boot a live ubuntu cd take a screenshot of gparted and post it using the paper clip in the reply panel.

You mention no extended partition and over four partitions.

---

### Post by darkod on 2012-06-10
Boot the ubuntu cd in live mode, open terminal and post the output of:
```
sudo fdisk -l
sudo parted /dev/sda print
```

---

### Post by eslam elbyaly on 2012-06-10
what would these comands do 
sudo fdisk -l sudo parted /dev/sda print
would it enable me to install the xp ?

---

### Post by darkod on 2012-06-10
It would print the partitions on the disk with two different programs (fdisk and parted), so we can have a look at them.

Otherwise, this sounds like general error, not related to ubuntu. If you can copy the data from D: to another external disk, you can start all over.

Which program did you use to initially create your partitions, some tool from ubuntu or...?

---

### Post by eslam elbyaly on 2012-06-10
i have used windows cd to make windows partitions c and d 

and when i installed ubuntu , used ubuntu itself to make its partitions too

---

### Post by eslam elbyaly on 2012-06-10
excuse me please , 
can i just put the ubuntu cd in my drive , then just try it and use the terminal to type these commands (fdisk .......), or do i have to make complete installation ?

---

### Post by darkod on 2012-06-10
> **eslam elbyaly said:**
> excuse me please , 
can i just put the ubuntu cd in my drive , then just try it and use the terminal to type these commands (fdisk .......), or do i have to make complete installation ?

Correct, use Try Ubuntu, when it loads the live desktop open terminal and run them.

---

### Post by eslam elbyaly on 2012-06-10
i got the screen shots , but i do not know where the reply panel is , and i do not know where the paper clip is ?

---

### Post by darkod on 2012-06-10
I don't know about the lba flags shown by parted, but the boot flag should not be on /dev/sda2, only on /dev/sda1.

From live mode (Try Ubuntu), in terminal try this:
```
sudo parted /dev/sda
set 2 boot off
quit
```

Then again check with the same parted print command to see if the boot flag is gone from /dev/sda2.

I think windows made some mess creating the partition table and partitions on the disk. But you can try to install XP again after turning off the boot flag on /dev/sda2 and see if that changes anything.

---

### Post by eslam elbyaly on 2012-06-11
[SIZE=4][B]you are the man , 
thanks a lot ,  i did what you told me , and it worked very well , 

but my data partition d has the shape of ( you know when you try to open  file and you are asked to pick a program to open it with ,

the partition shape is like that icon 

if you know something , tell me please 
and thanks again 
you are the man :popcorn:
[/B][/SIZE]

---

### Post by Hakunka-Matata on 2012-06-17
You input the  "sudo fdisk -l" command incorrectly, typo.

the fdisk command option is a lowercase L, not the number ONE.

The two most common errors made by operators typing commands into the Terminal incorrectly, (with typos), are:
[LIST]
[*]Failing to start the command-line-input with 'sudo'
[*]inserting an invalid option (- or --) as you did, 1 instead of l
[/LIST]
A very good way to learn is first to COPY the command line and paste it into the Terminal program.  Ctrl-C for copy, BUT in Terminal, the paste command by default it CTRL-SHIFT-v.  It can be easily changed to be Ctrl-v, don't recall off hand where to change it.  
Second thing to do, if you're using options, is to do a "man fdisk" for instance, it'll explain the options, use "q" to get out of the man page.

Good Luck,

---

