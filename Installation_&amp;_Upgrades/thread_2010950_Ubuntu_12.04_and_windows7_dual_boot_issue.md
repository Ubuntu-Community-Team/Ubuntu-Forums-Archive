---
title: "Ubuntu 12.04 and windows7 dual boot issue"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by Dr. div11 on 2012-06-26
hey 
i am trying to dual boot my acer laptop with Ubuntu 12.04 along with windows7 home premium.
i really need to Know the exact partitions for my hard disk(500gb)
 my windows 7 space usage will be a bit more.

please help.

---

### Post by kc1di on 2012-06-26
Here is the dual boot page that you may want to read through it has a lot of good info. 
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
I'm not exactly sure what your asking. 
if you want to know how to partition your drive here's a good example.

Allow 250 gb or more for your windows 7 install
with the other 250 partition it like this

/ (root Partition) 20 gbs
/swap  2 gbs
/home  rest of drive. 

**[COLOR="Red"]NOTE:: BACK UP any important files before partitioning![/COLOR]**

you can do this in Ubuntu installer when it get to the partition stage by clicking on something else.
Good luck

---

### Post by Dr. div11 on 2012-06-26
but i need to know the exact partitioning like how many linux swap partitions.. what divisions in extended 4.

---

### Post by oldfred on 2012-06-26
You only need one swap partition. If you have 3GB or more of RAM and do not hibernate you can make swap 2GB otherwise the size of RAM in GiB or a bit more than GB.

kc1di gave a good suggestion on partitioning, they all can be logical with Ubuntu inside one primary partition.

Most laptops use all four primary partitions. Post this to see current partitions from a terminal from liveCD or USB or post screenshot from gparted from liveCD and use paperclip icon in edit panel above to attach to your message.

```
sudo fdisk -lu
```

---

### Post by Dr. div11 on 2012-06-26
but i need to know the exact partition space. like many many gbs to allot and will be enough for a windows system.. as in a partition table for dual boot windows 7 and ubuntu 12.04. on 500 GB [/B]hard disk.

please help.

---

### Post by sudodus on 2012-06-26
> **oldfred said:**
> You only need one swap partition. If you have 3GB or more of RAM and do not hibernate you can make swap 2GB otherwise the size of RAM in GiB or a bit more than GB.

kc1di gave a good suggestion on partitioning, they all can be logical with Ubuntu inside one primary partition.

Most laptops use all four primary partitions. Post this to see current partitions from a terminal from liveCD or USB or post screenshot from gparted from liveCD and use paperclip icon in edit panel above to attach to your message.

```
sudo fdisk -lu
```

*@ Dr. div11*

If you run the command line suggested by *oldfred* and post the output in a reply, or attach a screenshot from ***gparted*** when the computer is booted from a liveCD, it will be easier to help you. Otherwise we know too little to really help you.

---

### Post by martinr on 2012-06-26
> **kc1di said:**
> 
/ (root Partition) 20 gbs
/swap  2 gbs
/home  rest of drive. 

How about moving the swap partition in front of the root partition. The beginning of a drive is faster and you minimize head movements between swap and the root partition (that contains the binaries). ):P

---

### Post by BHEJU on 2012-06-26
Hi

This is what I did to dual boot, use it as a starting point. You should change this depending on your need.

100 MB windows reserve (automatically created at the time of win install)*
50 GB NTFS Windows install
06 GB SWAP space
15 GB /  EXT 4-- Ubuntu Install
400+ GB (rest of the HD) NTFS partition for shared data between the two os.

* Install win first to make the dual boot set-up easy.



Hope this helps.
Cheers,
Bheju

---

