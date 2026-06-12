---
title: "Partition sizes when dual booting"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by peabee on 2006-10-12
Good morning helpful people. 
After some deliberation I have decided to dual boot XP on my laptop (1.6 GHz, 512MB RAM and 34 Gig HDD)
I've split the drive down the middle and installed XP Pro on noe 17Gig partition.
I now have 17Gig (give or take a few MB) to install Ubuntu. 
I am assuming that the only option for partitioning it to select option 3 - manual. 
This is where my lack of knowledge comes into play. 
I have seen various partition size posts and web pages but no definitive solution to my problem. 
How many partitions do I need to install?
What sizes are the best?
I'd like to leave some space for a file repositry (fat32 I presume so both OSs can read it. 
Help would be appreciated as I've been banging away at thie for a week now and work is suffering :)
Thanks
P

---

### Post by Kateikyoushi on 2006-10-12
You could create a 512MB swap and the rest as ext3 for ubuntu,

[Use this driver to read and write your ext3 partition from windows.]("http://www.fs-driver.org/")

[This site]("http://users.bigpond.net.au/hermanzone/") can help you with partitioning.

---

### Post by peabee on 2006-10-12
Thanks for the reply, although the website referes to installing Dapper via text mode. 
Ideally I wanted the sizes so I can get a set of 'rules' for other PCs to go by - this would help my customers and other people dual booting. 
Thanks
P

P.S.  Actually I would like the partitions and relative sizes that Ubuntu would create on a normal single-OS installation....thank you.  I don't have another spare machine to install Ubuntu on!!!

---

### Post by epennings on 2006-10-12
My Ubuntu installation takes up 6GB total, with a lot of extra programs that arent installed by default. 

It might be wise to split your Ubuntu over multiple partitions (this is not required )

Here are some typical sizes for partitions :

/boot : 32MB - Contains files to boot Linux
/usr  : 3GB-5GB - This is where most programs are installed
/home : 2GB-xGB - This is where you put your personal files
/     : 5GB-10GB - This is where all system files are(includes /usr, /boot and/or /home if they are not on a seperate partition!!!)
swap  : 512MB - Linux swap, a bit like Windows Page File

I hope this clarifies it a bit.

---

### Post by peabee on 2006-10-12
Thanks, that helps. 
If possible would you be able to let me know if you let Ubuntu decide the partition sizes, or did them yourself. 
Because I don't want Ubunutu to delete the XP partition I think the only was if to manually do it, but I would like to mimic the default installation as much as possible. 
Thanks again for your patience. 
P

---

### Post by Kateikyoushi on 2006-10-12
Ubuntu by default only makes a / and a swap partition.
You have to partition it for yourself to make several partitions or to keep XP.

I am on a 10GB / partition using edgy eft beta it takes 2.5GB space + a swap.

If you make several partitions you have to calcuate the size of each not to run out of space onany of them.

You are on the safer side with using only 1-2 partitions then you can delete uninstall something if you need more space.

---

### Post by peabee on 2006-10-12
Ahhh, 
Sorry to be an idiot...
if I have a 17Gig partition, can I create a 512MB (same size as RAM) swap partition and a.....er...say.... 12 Gig / partition leaving me with 2GB for 'storage'?
I promise if I get  this OK in my head, I won't pester again :)

---

### Post by Kateikyoushi on 2006-10-12
12GB should be more than enough, but you will realise it by installing removing softwares and using it. To some extent these all depend on what programs you use and install.

512MB swap is good you won't need that much but it is safe to have a bit more.
I would say make a 10GB / partition and make the storage bigger.

---

### Post by peabee on 2006-10-12
Brilliant, 
Thanks for your idiot-proof explanation.  I shall create the two partitions (say 600MB for swap and 10Gig for / and see what Ubuntu does :)
P

---

