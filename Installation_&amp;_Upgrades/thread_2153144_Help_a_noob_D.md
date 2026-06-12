---
title: "Help a noob :D"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by RobyRc on 2013-06-10
Hi!
My computer: 
AMD Athlon x3 445 3.1gHz
AMD HD5670 512MB GDDR5
4GB RAM
HDD 500GB
I know,linux isn't windows. I KNOW IT.
So,i have some questions.
How can i make 2 partitions? 1 for windows,1 for linux? (i will use ubuntu all the time,windows only for games..)
Ubuntu 13.04 will work ok on my pc?:guitar:

---

### Post by Bucky Ball on 2013-06-10
Welcome to the forums. Just a heads up: You will greatly increase your chances of getting assistance if you use descriptive thread titles. This one says nothing about your issue. You can change it within the first 30 minutes of posting the thread. If you can't change it, let me know what you'd like it changed to and I'll change it. 

Secondly, to the issue. Is the disk free space now? Either way, if it only contains NTFS and FAT partitions, you can repartition when in the Win installer. Boot from the Win disk. You will get to a section of the install which asks you to choose where to install. You can create and size a partition for Win then and make it small as you can, say 40-50Gb depending on which version of Win you are using (check system requirements at MS site perhaps) and how much Win data you intend to keep on that partition. 

One thing to remember; if you intend sharing data between the two installs you are going to need an NTFS partition somewhere (/share for instance) as Win will not read and write to the EXT* file format which is used by Ubuntu.

Anyway, there's TONS of info on the interwebs about this; you might like to start here:

[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

Once Win is installed, boot from the Ubuntu LiveCD and install Ubuntu. When you get to the partitioning section you have options. You can either let Ubuntu install itself next to Win or you can choose 'Something Else' and set up the partitions yourself. My preference as you can choose sizes, etc.

---

### Post by fantab on 2013-06-10
Since you will be using Windows only for games, my suggestion would be to consider the following scheme of partitioning:

/dev/sda1 (your first partition) 100GB Windows (Win7 Ultimate take about less than 30GB for System files, about 70GB of space for your Games should be enough).
/dev/sda2 20-30GB Ubuntu / (for your main Ubuntu System files)
/dev/sda3 2-4GB SWAP
/dev/sda4 All the remaining GB /home (This is where all your Data, like Documents, Music etc, will be stored)

Partitioning is very personal thing. So consider your needs and plan ahead.

---

