---
title: "Trying to fix my bootdisk on my Ubuntu 22.04 laptop"
date: 2024-07-02
forum: Installation &amp; Upgrades
---

### Post by sitethief on 2024-07-02
This morning I could not get into my Ubuntu when starting my laptop, it complained about a missing boot drive (iirc)
I used a USB drive with Ubuntu live to get access to the system and be able to run Boot Repair

Boot Repair info: [https://pastebin.ubuntu.com/p/Q9jcfxcR9G/](https://pastebin.ubuntu.com/p/Q9jcfxcR9G/)

I was able to mount my LUKS volume by running ```

sudo cryptsetup luksOpen /dev/nvme0n1p3 myvolume


```
which mounted it to ```
/media/mint/41843ba2-{long hash here}
```

I copied out my home folder using rsync to my separate desktop, so that data is back-upped for now. If I can't fix the boot disk I can always install 24.04 and go from there.
But I rather restore my system somehow.

What is my next step to possible restore my system?

---

### Post by sitethief on 2024-07-02
Btw, a while back I switched to Liquorix Kernel (6.8.7-2-liquorix-amd64 I think) to solve some graphics driver issues I had.
No idea if that plays any role here though, had no complains about it so far.

---

### Post by currentshaft on 2024-07-02
> **sitethief said:**
> 

What is my next step to possible restore my system?

Probably posting what the problem actually is. A vague "complaint about a missing boot drive" is a mystery and we're not detectives. How about the actual error message, for a start?

---

### Post by sitethief on 2024-07-02
I managed to get to the `grub-install` step for the empty boot drive and afterwards a successful `update-grub`
even then did not manage to fix it into a bootable installation.
I'm gonna install 24.04

---

### Post by sitethief on 2024-07-02
> **currentshaft said:**
> Probably posting what the problem actually is. A vague "complaint about a missing boot drive" is a mystery and we're not detectives. How about the actual error message, for a start?

All I had was "Default Boot Device Missing or Boot Failed"
Looked exactly like this picture
[https://i.redd.it/by6g23i3n0cc1.jpeg](https://i.redd.it/by6g23i3n0cc1.jpeg)

---

### Post by currentshaft on 2024-07-02
At what boot stage? Do you see the GRUB menu? Can you select a previous kernel version from it?

The boot repair output shows data partitions are intact, so it may be as simple as booting to the last known working configuration.

---

### Post by tea for one on 2024-07-02
Line 131 - nvme0n1p1           ext4        a1d41f74-6d9f-4434-a197-6fe6e4c9266d   52eb99d3-d854-4dae-b852-151a250097a7 Michel VL Backup       EFI System Partition

Your ESP has ext4 filesystem, it should FAT32
Did it somehow change?

You could try to copy the contents, reformat to FAT32 and restore the contents.

---

### Post by sitethief on 2024-07-02
> **currentshaft said:**
> At what boot stage? Do you see the GRUB menu? Can you select a previous kernel version from it?

The boot repair output shows data partitions are intact, so it may be as simple as booting to the last known working configuration.

I have no boot options for the current installation at all, it's not  recognized as a bootable drive at all by the bios, so I can't boot from  it. 
I don't get to the grub menu at all.
What I determined that  somehow during my day yesterday I formatted the wrong partition  containing my boot drive. Instead one of the external drives I was  setting up. And in all the chaos of yesterday I did not notice my boot  drive was basically empty for all intents and purposes
The solution would obviously be to get it to a proper state with grub-install etc.
However that failed to make my system bootable.

So now I'm installing 24.04, or if that is a disappointment back to a new 22.04

---

### Post by sitethief on 2024-07-02
> **tea for one said:**
> Line 131 - nvme0n1p1           ext4        a1d41f74-6d9f-4434-a197-6fe6e4c9266d   52eb99d3-d854-4dae-b852-151a250097a7 Michel VL Backup       EFI System Partition

Your ESP has ext4 filesystem, it should FAT32
Did it somehow change?

You could try to copy the contents, reformat to FAT32 and restore the contents.

Yeah, I determined I accidentally formatted it :( .

---

### Post by tea for one on 2024-07-02
Then, you now realise why your PC doesn't boot.
It would have been helpful if you mentioned this in your original post.

Do you have a backup of your original ESP?

---

### Post by sitethief on 2024-07-02
> **tea for one said:**
> Then, you now realise why your PC doesn't boot.
It would have been helpful if you mentioned this in your original post.

Do you have a backup of your original ESP?


I was not aware that this was what cause the problem when I posted this topic.
I noticed the name of the partition on nvme0n1p1 as one of the names I used for formatting partitions when I started working on restoring a bootable drive.
This was way after I made this post. I first had to backup 700gb of my data from nvme0n1p3 before attempting anything else.
My apologies that this wasn't clear right away.

---

### Post by tea for one on 2024-07-02
OK, I understand.
My observation in post 10 was, in hindsight, a little terse.

How are you planning to proceed now?

---

### Post by sitethief on 2024-07-02
> **tea for one said:**
> OK, I understand.
My observation in post 10 was, in hindsight, a little terse.

How are you planning to proceed now?

Since I managed to backup my data from the LUKS disk by using the Ubuntu live USB the data on the disks was of less importance.
 I successfully installed 24.04 over the old partitions by just removing them all and start over..
I gave it a good try to restore the original OS before that, but since this is my work laptop, getting it up and running again was more important then retaining the original installation.

Thanks for the help though :).

---

### Post by sitethief on 2024-07-02
> **tea for one said:**
> OK, I understand.
My observation in post 10 was, in hindsight, a little terse.


Nah, it's ok, I know how it is dealing with people who (mis)use computers daily and then fail to communicate ;).

---

### Post by tea for one on 2024-07-02
> **sitethief said:**
> Nah, it's ok, I know how it is dealing with people who (mis)use computers daily and then fail to communicate ;).
Cheers, very genial of you.

By the way, as you are using encryption, back up regularly before anything untoward happens.

---

