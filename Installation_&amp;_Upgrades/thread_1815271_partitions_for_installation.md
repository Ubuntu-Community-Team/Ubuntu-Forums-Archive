---
title: "partitions for installation"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by eslam elbyaly on 2011-07-31
hi all , 
it is the first time i install linux 
i have windows xp with and my hard has 2 partitions (c,d) , and i am trying 
to install linux , but i do not know about partitions it needs , 

can i make a new partition (e) for linux , and install it on it , or i need more than 
one partition or what ?
guide me please 
thanks in advance

---

### Post by Hakunka-Matata on 2011-07-31
Welcome to the Forums,

Here's a link to the official Ubuntu installation guide.  [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Good luck,

---

### Post by eslam elbyaly on 2011-07-31
thanks matata 
, but i did not found what i am searching for their , i just found what i already know 
i have usb flash memory 4gb
and windows xp 
and i will back up my usb before doing anything 

and so on 
but i do not know how many partitions i have to create for linux(ubuntu) ? to not to affect the primary partitions i have (c,d) 

if u can answer just this question , please ?

---

### Post by garvinrick4 on 2011-07-31
First of all defrag Windows a couple of times just for the hell of it. Some do some don't.
You need to resize your windows partition with OS C: drive, leave the D drive alone it is recovery type partition for windows. Resize and leave how ever much you want for 2 partitions
1 for Ubuntus file system now called / and one for a /swap partition 2 times the size of your RAM. After you reduce size of C drive make the new partition a Extended partition and then
inside that Extended partition make the 2 logical partitions for / and /swap (swap has to do with using drive for extra Ram) Extended partition is just a house for logical partitions which
Linux can survive in without using up the 4 primary partitions your basic drive can handle.
Windows OS is primary, Windows recovery is Primary and Extended is Primary so only using
3 of the 4 allowed, can have oodles of logical partitions inside and Extended partition.
## Or you can use side by side in Ubuntu installer on install cd you make and it will do the
partitions for you.
# If not make your own partitions and use "something else" at install I believe to install and put your ext4 format
and / as mount point and put grub in sda not sda5 or sda1 but SDA after install reboot and
open terminal and "sudo update-grub" without quotes and will put windows in grub (boot loader) as a menuentry and in config file.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
[p22]("http://members.iinet.net.au/%7Eherman546/p22.html") This is a bit about using gparted to make partitions;

---

### Post by eslam elbyaly on 2011-07-31
does not ubuntu asks me if i wanna create new partitions to install it on it during installation steps ?

does not it asks for the two partitions , and can create it within installation steps ?

please , if u can guide me with just a simple answer ? do not post a link please , it is the first time i use ubuntu or linux . 

regards

---

### Post by Hakunka-Matata on 2011-07-31
We do not have enough information about your system yet.
You can try it, experiment, using Ubuntu without installing it, you know that, correct?
Have you already downloaded Ubuntu . iso installation file and burned it to CD or USB yet?

---

### Post by eslam elbyaly on 2011-07-31
the situation is 
i have windows xp service pack 2 , a hard disk with two partitions (c,d) 
and i have a very important data on these partitions , and i do not wanna lose it , so i have to create new partitions (i think it is 2 partitions) to install ubuntu on it , but the proplem is i do not know how to create new partitions or resize a partition ,
that's why i asked if ubuntu does like windows does ( ask you where to install ubuntu , and asks you to create partitions autumatically ? does it do so ?
 
, and i download ubuntu iso on usb flash memory 4gb (burned it) and did the whole thing 

thanks

---

### Post by Hakunka-Matata on 2011-07-31
> **eslam elbyaly said:**
> the situation is 
i have windows xp service pack 2 , a hard disk with two partitions (c,d) 
[COLOR=Red]and i have a very important data on these partitions , and i do not wanna lose it[/COLOR] , so i have to create new partitions (i think it is 2 partitions) to install ubuntu on it , but the proplem is i do not know how to create new partitions or resize a partition ,
that's why i asked if ubuntu does like windows does ( ask you where to install ubuntu , and asks you to create partitions autumatically ? does it do so ?
 
, and i download ubuntu iso on usb flash memory 4gb (burned it) and did the whole thing 

thanks

If you haven't backed up your "Very Important Data" yet, that is the first thing you should do.  It is always possible for something to go wrong while changing any partitioning on a hard disk, power outage, hit wrong key, many things can go wrong.
Until you are satisfied that you have backed up your important data, I won't suggest doing any partition changes on your hard drive.

---

### Post by eslam elbyaly on 2011-07-31
i can not back up my important data because it is (almost 40gb) , and i do not have another hard disk 

what should i do ?

---

### Post by Hakunka-Matata on 2011-07-31
> **eslam elbyaly said:**
> i can not back up my important data because it is (almost 40gb) , and i do not have another hard disk 

what should i do ?


I would NOT install Ubuntu or change any partitions in that case.

---

