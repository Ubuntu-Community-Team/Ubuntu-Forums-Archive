---
title: "Ubuntu partition failure"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Bartikky on 2007-06-07
Hey, I just started messing around and trying to get to grips with Ubuntu 7.04 through the LiveCD. I am happy with Ubuntu and think it's fantastic, I want to install it but I get this error when it starts resizing the partition, not quite sure how partitions works and are created and I don't want to mess around with it incase I accidently lose all my music and document files. As I was saying, I get an error and the resizing partition doesn't even get off 0%, the error is something like,

An error occured when writing the changes to the storage devices.
The resize operation is aborted.

I **really, really, really** want to be able to dual-boot Ubuntu along with WIndows XP. I know there are other ways to partition my drive but I don't want to do anything stupid since I don't know what I'm doing and don't want to destroy my only drive that I have and can't afford a replacement, I don't want to be left with no where to do my coursework:shock:.

Thanks, Bartikky

---

### Post by merlinus on 2007-06-07
Excellent info here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

-merlin

---

### Post by Bartikky on 2007-06-07
Hi again and thanks for the link merlin, i need a quick question though, what filesystem does ubuntu need, ext3? I'm not sure, I've decided to use GParted to partition my drive for ubuntu

or can any1 else out there help me on this simple question please, thank you

---

### Post by merlinus on 2007-06-07
ext3.  You can download drivers that will let you write both to ext3 and ntfs.

Gparted is a great choice for partitioning.

Ubuntu will need at least two partitions -- / and swap.  The second should be about 1.5 times your RAM.

-merlin

---

### Post by Bartikky on 2007-06-07
i've created a swap partition, i got this error when i selected the new partitioned drive for ubuntu and pressing 'Frorward',

No root filesystem is defined.
Please correct this from the partition menu.

Help please?

---

### Post by floke on 2007-06-07
Easy.
Right click the ext3 partition - to edit it - change the '/media' to '/'. Make sure the format box is checked.
See you on the other side...

---

### Post by Bartikky on 2007-06-07
thanks, i might not comment back today if i am succesful with the installation...

---

### Post by Bartikky on 2007-06-07
another quickfire question plz, if i tick the box tht formats the partitioned drive for ubuntu, it wont format or touch the partition for win xp, right?

---

### Post by floke on 2007-06-07
It will only format the partitions for the boxes you tick.
Now do it. I dare you :D

---

### Post by Bartikky on 2007-06-07
rofl - excuse the text speak...
OK, here I go, see ya 45mins... or tomorrow

---

### Post by floke on 2007-06-07
And so our intrepid explorer stepped out and faced the blue skies of yonder....

<cue tension music>

---

### Post by merlinus on 2007-06-07
> **Steve.K said:**
> And so our intrepid explorer stepped out and faced the blue skies of yonder....


Much better than facing the windows blue screen of death!

-merlin

---

### Post by floke on 2007-06-07
Well just wait till he installs and gets the kernel update...

---

### Post by merlinus on 2007-06-07
He'll definitely be looking at frequent forum flier miles....

:D

-merlin

---

### Post by Bartikky on 2007-06-08
Haha, well I successfully installed Ubuntu 7.04, yay!
I need to get the internet sorted now, thanks merlin and Steve!

I just remembered the time I had my first computer, windows 3.1, about 2 years old it started getting so many blue screens of death haha, anyhoo thanks again you 2.

---

### Post by frodon on 2007-06-11
Thread closed (OP request).

---

