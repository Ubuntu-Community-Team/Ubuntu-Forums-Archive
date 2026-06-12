---
title: "Making a Partition"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by FreshPrince on 2007-02-07
Hi everyone. New to Ubunte and the ubuntu forums.

Anyways, lets get to buisness. I have, for a long time, wanted to installe linux and try it out. Cuz i am a curious person i like to try out stuff. And this time it was linux i wanted to try.

The only problem is that i have been asking alot of ppl how to make dual boot between vista and linux. Alot of them told me to make a partition with partition magic 8. after doing that, i tried the live cd and was going to install until i saw that ubuntu has its own partitioning program. So i deleted my partition again (the one i made with PM8 ) and went back to live cd and into the step with partitioning.
Now to the problem. I can only choose between deleting my whole drive or making a partition myself. 

The problem is that i dont understand wat ubuntu wants me to do (sumthing about making to partitions, one with swap and the other with minimum 2gb?) is that write?
If so (or if not, dosent matter) i would like to ask how to make those partitions.

I have 66gb harddrive, and from that i have 22gb free. and from those 22gb i was thinking about 15gb to linux.

Thanks for helping (and sry if this is the wrong section)

---

### Post by housam on 2007-02-07
Defrag your windows partition 2-3 times before resizing it.
Using Gparted  resize the partition to what you like ( say 15 Gb) by decreasing its size from the right end of the partition. this will create an unallocated space which can be devided into 2 partitions . one for the root ( / ) ext3 format 14 Gb and the other is swap for the swap partition 1Gb.
Then you can srart the installation after that.

---

### Post by FreshPrince on 2007-02-07
Hmm.....well thanks for telling me how to partition it. But now it wont let me cuz it says i cant make more then 4 partitions.
And i have tre allready, one is my harddrive, second is recovery and the third one is, well i dont know for wat. It ntfs and 1gb (/dev/sda3)

---

### Post by housam on 2007-02-07
OK, make the unallocated space as a new extended partition. and that one can be divided into many logical partitions.

---

### Post by FreshPrince on 2007-02-07
Wohoo...thanks alot.

But now i have one problem remaining, i cant get my network to work.

How can i make it work?

---

### Post by Bartender on 2007-02-07
Did you go into System>Administration>Networking and enable the network card?  Restart the PC with the CAT cable plugged in and see what happens.

---

