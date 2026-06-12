---
title: "Ubuntu Installation"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by anshul on 2008-11-20
Hi i am new to linux had never used it before always used windows in pc nw i just need a change so i want some help 
my system configuration is 
System Model: D945GCR_
Processor: Intel(R) Pentium(R) D CPU 2.80GHz (2 CPUs)
Memory: 2046MB RAM
Card name: NVIDIA GeForce 8400 GS
Display Memory: 512.0 MB
 so wud plz tel which version of ubuntu shall i download tats suit to my pc
thanks in advance

---

### Post by icanfly0307 on 2008-11-20
There really aren't *versions* of Ubuntu. Just download Ubuntu from [here]("http://mirrors.us.kernel.org/ubuntu-releases/intrepid/ubuntu-8.10-desktop-amd64.iso") (the download will start automatically), burn it to a cd, and install it. Good Luck! :)

---

### Post by anshul on 2008-11-20
> There really aren't versions of Ubuntu. Just download Ubuntu from here (the download will start automatically), burn it to a cd, and install it. Good Luck!
and wat about installing my motherboard drivers i dnt think they for linux also  ??

---

### Post by anshul on 2008-11-20
and ya any1 plz tell me about its partions i need to instal a fresh copy in  my pc

---

### Post by quimico69 on 2008-11-20
Even though your cpu is 64-bit, you might want to consider downloading a 32-bit version if you want to install things like firefox plugins and other software that is not available for 64-bit platforms (ubuntu-8.04.1-desktop-i386.iso or ubuntu-8.10-desktop-i386.iso).

Otherwise, you should get the Ubuntu 8.10 or 8.04 for 64 bit.  Look for the iso ending in *amd64.iso (ubuntu-8.04.1-desktop-amd64.iso or ubuntu-8.10-desktop-amd64.iso)  Do not be misled by the bit "amd".  It works with intel cpus too.

hope this helps

Victor

---

### Post by anshul on 2008-11-20
can any1 tell me about partitions ?

---

### Post by icanfly0307 on 2008-11-20
Hi,
      To answer your first question, the motherboard drivers and everything else: they'll be automatically installed. Don't worry about it. As for the partitions, it would be helpful if you posted your current setup. Do you have Windows already installed? Have you decreased its partition size to make space for Ubuntu?

---

### Post by trendyabinash on 2008-11-20
Hi Anshul.

It is really easy to create a partition for linux
I don't remember exactly all the steps but here is the basics.
if you are running windows and want to keep a dual operating system(very helpful for new users)
then just boot with the ubuntu CD run live as u can see some basic features before installation then click on install follow some easy steps till partition manager is started.

When partiton manager shows up go for manual partition.

Assuming that you have 2 partition let A and B, where A is of 30GB and B is of 20GB and both are having NTFS file system A has windows loaded in it.
When partition manager starts it will show you some details of your partitions, as for new users it is confusing to understand the names of partitions so recognise your partition by looking at there disk space.
Next step is to delete the partition B select it and click on delete partition.
You will able to see free space of 20GB. Click it and create a new partition alloting about 18-19 GB of space to it there in the file system  tab select ext3 journaline file system. if format option is provided then then slect it and at last there will be mount point click it and select "/" also popularly known as ROOT.
then click OK.
You will see that 1Gb or 2GB as you have decided is left. Again click the free space and create a partition but this time in the file system select swap, it doesn't requires any mount points so click Ok after that and click on FORWARD button.
Finish. After that enter some details of your's and YOU are ON.

I tried to explain in the best possible way I can.
you Can ask me if anywhere you want help. I can not explain why it is done but I can tell you how it is done

---

### Post by anshul on 2008-11-21
> Hi,
To answer your first question, the motherboard drivers and everything else: they'll be automatically installed. Don't worry about it. As for the partitions, it would be helpful if you posted your current setup. Do you have Windows already installed? Have you decreased its partition size to make space for Ubuntu?
right now i am windows xp my hard disk is 80gb and it is divided into 4 partitions in C drive(its of 16 gb) windows are installed and another 3 partitons r divided in to equal parts and they in NTFS file system .
i had downloaded ubuntu-8.10-desktop-i386.iso image

---

### Post by anshul on 2008-11-21
no reply yet :O

---

### Post by Arseny92 on 2008-11-21
> i had downloaded ubuntu-8.10-desktop-i386.iso image
burn it to a cd and boot it
you can boot into the livecd environment to try the features, or boot into the installer. Follow the instructions. At the point of partitioning you need to choose where to install ubuntu, resize existing partitions ans so on. The names of the partitions are different, for example: the partition that Windows installed on is called not as C:\ , but (possibly) /dev/sda1 and so on.

---

### Post by theozzlives on 2008-11-22
> **anshul said:**
> Hi i am new to linux had never used it before always used windows in pc nw i just need a change so i want some help 
my system configuration is 
System Model: D945GCR_
Processor: Intel(R) Pentium(R) D CPU 2.80GHz (2 CPUs)
Memory: 2046MB RAM
Card name: NVIDIA GeForce 8400 GS
Display Memory: 512.0 MB
 so wud plz tel which version of ubuntu shall i download tats suit to my pc
thanks in advance

I have a 1.73 GHz core duo and run the 64 bit version

---

