---
title: "Best way to upgrade?"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by chamber on 2010-06-21
I recently moved /home onto a seperate partition and was wondering what the best way to go about upgrading would be?

This system was previously dual booting Vista and 9.04 however in a fit of frustration at Vista I wiped it's partition and used it as a storage space for my media files.

I now have;

[B]Dell utility partition (~3GB)
Storage (210GB)
Unallocated (will eventually be installing windows 7 in at some point)(40GB)
Linux
    /home (~25GB)
    / (20GB)
    /swap (2GB)[/B]

I would like to upgrade as simply and painlessly as possibe, would the best way to do this be by upgrading from within the system or by installing a newer release from the live cd and telling it what partition to use?

---

### Post by wojox on 2010-06-21
Open your terminal and copy and paste this


```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by chamber on 2010-06-21
Thanks, 

Know about that, was just wondering if that way would be the easiest way to keep all my settings etc intact or would it be better to do a fresh install but choose not to format my /home partition?

---

### Post by wojox on 2010-06-21
No it's good to have a separate partition.

---

### Post by chamber on 2010-06-21
Ok,

I do have a seperate /home partition, which I intend to keep.

The question was is it better to use

1. the sudo apt-get upgrade option 

or

2. use the live cd and install, but select not to format the /home partition

Which of these 2 methods is going to be better for not messing up al of my settings.

---

### Post by limestone on 2010-06-21
[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

### Post by wojox on 2010-06-21
> **chamber said:**
> Ok,

I do have a seperate /home partition, which I intend to keep.

The question was is it better to use

1. the sudo apt-get upgrade option 

or

2. use the live cd and install, but select not to format the /home partition

Which of these 2 methods is going to be better for not messing up al of my settings.

it's faster and quicker using the Command line. No don't use the CD.

---

### Post by chamber on 2010-06-21
So your recommendation would be to use the upgrade route then as opposed to the live cd?

The reason I am asking is that the last time that I used the upgrade route it was extremely annoying and took me an age to sort out again, this was however when I did not have a seperate partition for my home folder.

---

