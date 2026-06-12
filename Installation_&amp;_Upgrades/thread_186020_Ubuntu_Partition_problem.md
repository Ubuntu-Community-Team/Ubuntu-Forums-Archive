---
title: "Ubuntu Partition problem"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by zXen on 2006-06-01
Hi,

I tried installing the new Ubuntu today and got to the part where you manually set up the partitions. I used the 10gb unallocated space to create a new primary ext3 linux partition and 512mb from that unallocated space I used to make another partition for the swap.
 Then I went to the next screen and it asked me to choose the root partition and the swap partition. Though, there were only three partitions listed, the main 9.5GB partition i made and the other two was my main Windows partition and my other hard drive.
 I tried creating the swap partition as a ext3 and a "Linux-Swap" partition, but no  avail...
 Just wondering why my 512mb partition i made to be a swap partition is not appearing on this section, though the other partition I made is?

---

### Post by Zdravko on 2006-06-01
I had the same problem. I just quit the installation wizard. Then I started it again. This time I repartitioned the harddisk. On the next step there were several listboxes. At first glance it seems very complicated and confisung. Don't worry - just select the module from the left - e.g. 'swap'. Then click on the right listbox - you got a list of options. Choose one of these. Note that you can see its size now. Select 'Format'. This worked for me!

---

### Post by zXen on 2006-06-01
What i was saying though is the swap partition I make everytime doesnt appear on list on the next page following the main partition page. There is just three rows, the first is my other hard drive, the second row is my existing Windows partition and the third is primary 9.5gb partition i just made. Though, there is no sign of the 512mb partition I made...

---

### Post by nrwilk on 2006-06-02
I have the exact same problem, and I've seen at least one other thread with people who've had this problem.

---

