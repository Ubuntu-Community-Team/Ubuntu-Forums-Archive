---
title: "[SOLVED] partition help"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by luke9511 on 2007-12-09
im trying to install ubuntu on my main hard drive but i need to make the partitions, well i freed up about 60 gigs of space for ubuntu but when i go to install its wanting more space then i can give it and im wondering how exactly do i set it so that it only uses the 60 gigs of space i got for it?

---

### Post by soulmatic09 on 2007-12-09
have you tried reducing the amount of swap space?

---

### Post by luke9511 on 2007-12-10
well with the little slider bar it uses it goes down to a little bit less then 190 gigs

---

### Post by luke9511 on 2007-12-10
so how do i fix this?

---

### Post by forestpixie on 2007-12-10
how are you dealing with the partitioning - you using the livecd?

---

### Post by luke9511 on 2007-12-10
> **forestpixie said:**
> how are you dealing with the partitioning - you using the livecd?yes i am is there another way of doing it?

---

### Post by forestpixie on 2007-12-11
I always use [gparted ]("http://gparted.sourceforge.net/")livecd myself

burn it as an iso - boot with it, make the partition changes you want - format to ext3

once you've got partitions you choose manual at the partition stage of the install and install to the partition you've made

Backup anything you don't want to lose when you're playing with partitions

---

### Post by luke9511 on 2007-12-11
can someone please explain on how to use gparted?

---

### Post by forestpixie on 2007-12-11
download, burn it as an iso, boot with it - if you're new to partitioning I would look at the [documentation]("http://gparted.sourceforge.net/documentation.php") on the site 

make sure you've got backups

---

### Post by Kinslayer|*= on 2007-12-11
Hello just freed up 10 gigz need to know wut type of partitions to put in for ubuntu i will be hopefully gaming on it:popcorn:

---

### Post by luke9511 on 2007-12-11
> **Kinslayer|*= said:**
> Hello just freed up 10 gigz need to know wut type of partitions to put in for ubuntu i will be hopefully gaming on it:popcorn:i will be trying the same so i wish you luck

---

### Post by forestpixie on 2007-12-11
ext3 for file type, if you've only got 10Gb I would just have one partition, when you come to install mount it as /

luke9511 - check the docs out - and if you're unsure I will be watching this thread for a while

---

### Post by luke9511 on 2007-12-11
> **forestpixie said:**
> ext3 for file type, if you've only got 10Gb I would just have one partition, when you come to install mount it as /

luke9511 - check the docs out - and if you're unsure I will be watching this thread for a whilewill; do and thanks alot for all the help

---

### Post by forestpixie on 2007-12-11
not a problem - 5 or 6 months ago I was in the same position - glad to be able to repay others kindnesses :)

---

### Post by luke9511 on 2007-12-11
well i just messed up my windows partition, i meant to delete the 6 or so gig recovery partition for my windows since i didnt need it and it seems i deleted my windows partition in the process, so is there anyway for me to get my files back through linux or are my files gone since theres no partition?

---

### Post by forestpixie on 2007-12-11
oh dear that could well be a bit of a problem - I expect you're feeling a bit :(

I don't know if you'll be able to do anything with that, if gparted has deleted the partition I think that might be that - whatever you do don't do anything else to the drive don't turn it on either - use the livecd and at least you'll be online - assuming that's you're only pc

I'd put another thread on the abs beginners forum - people look there more frequently I've found

I assume that you still have the recovery partition so you can do that if you need to - I hope that you took the hints earlier and made sure you had backups

Good luck

---

### Post by luke9511 on 2007-12-13
i am marking this thread as solved as i managed to recover my windows partition and am able to boot into windows again thanks alot for the help and advice :)

---

### Post by Kinslayer|*= on 2007-12-13
hey i really enjoy this .deb based o\s I'm thinking about more hard drive space i will unallocate it but how do i get it to be used in ubuntu and will it recognize another partition or should i just try to make my other partition bigger

---

