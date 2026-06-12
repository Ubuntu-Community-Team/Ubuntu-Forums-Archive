---
title: "Question regarding upgrading and partitions"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by xeroguitar on 2008-07-28
Ok, I am new to Ubuntu and Linux in general so I don't know a whole lot yet about it but I am learning.

So to start off I downloaded 8.04 and couldn't install it because I have an older machine. So I installed 6.06 and I now upgraded to 7.04 but I screwed up the partitions so now I have 3 partitions. One is my Windows partition, the other two are 6.06 and 7.04 so it didn't upgrade it just did a clean install on another partition. It split my 6.06 partition in two.

My question is, Is there any way I can delete 6.06 and stretch the partition 7.04 is installed on to make it one partition again? Or do I have to re install everything?

---

### Post by zvacet on 2008-07-28
Can you give more informations about your comp?Maybe you can try [Xubuntu alternate CD.]("http://www.xubuntu.org/get")

---

### Post by snowpine on 2008-07-28
> **xeroguitar said:**
> Ok, I am new to Ubuntu and Linux in general so I don't know a whole lot yet about it but I am learning.

So to start off I downloaded 8.04 and couldn't install it because I have an older machine. So I installed 6.06 and I now upgraded to 7.04 but I screwed up the partitions so now I have 3 partitions. One is my Windows partition, the other two are 6.06 and 7.04 so it didn't upgrade it just did a clean install on another partition. It split my 6.06 partition in two.

My question is, Is there any way I can delete 6.06 and stretch the partition 7.04 is installed on to make it one partition again? Or do I have to re install everything?

To answer your question, you can use a Live CD with a partition editor (I would recommend Gparted since your system presumably can't run the Ubuntu Live CD) to delete the unwanted partition and resize the one you want to keep. It should be easy, but of course, back up anything important first!

However, why don't you post more about your system specs & installation problems, maybe we help you choose a more recent "distro" that will work for you. But if you are happy with 7.04, that is all that matters. :)

---

### Post by snowpine on 2008-07-28
I did just think of one complication, however. Deleting one of the partitions may mess up your Grub. Here is more info on Grub: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by xeroguitar on 2008-07-29
yeah, sorry, i meant to include the system specs... but well... i didn't :guitar:

anywho, its an older HP with a 1200mhz intel celeron, 192mb ram(sdram), a 40gig hd, it does have a dvd rom i installed....

ultimately id like to build a whole new computer but im poor right now and this computer was 20 bucks at a yard sale so i cant really complain too much :)

i thought about upgrading from 7.04 while i was at it but im not sure my computer can handle it... i have an ubuntu 8.04 install cd and a fedora 8 install dvd... think it will handle either of those?

---

