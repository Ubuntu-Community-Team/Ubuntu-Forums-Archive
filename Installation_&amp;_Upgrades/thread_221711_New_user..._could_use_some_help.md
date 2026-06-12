---
title: "New user... could use some help"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by fwqhgads on 2006-07-23
Hi, I'd like to install Ubuntu 6.06 on my laptop, but I'm kind of stuck here. 

I'm able to boot from the CD just fine, and get the the installer, but I'm not really sure what I want to do.

My laptop's original Windows C drive was screwed over, so I had to re-install. I had to re-install on my second partition however, and am now left with a bad windows partition and a good one. Now, I want to put Ubuntu on the bad partition, but keep my other windows partition. I just want to make sure I don't end up loosing my Windows partition, or possibly brick my laptop (the original C drive is tagged as boot). 

Sorry if this sounds confusing... But please help if you can.

---

### Post by Sef on 2006-07-23
Read this excellent tutorial on [How to Dual Boot.]("http://users.bigpond.net.au/hermanzone/")

It will tell you how to save your windows partition.

---

### Post by fwqhgads on 2006-07-23
Well, it appears that I can't boot my computer anymore...

---

### Post by confused57 on 2006-07-23
I'm pretty sure you won't be able to install Ubuntu on a partition located before the Windows partition on a single hard drive.  I know this doesn't help you, but everything I've read suggests it's difficult to do this.

---

### Post by fwqhgads on 2006-07-23
Well from what I can tell is I've gotten rid of the old partition which is partly what I wanted to do. I don't understand the Ubuntu Installation stuff though.

---

### Post by fwqhgads on 2006-07-24
I'm unsure of when I get to the stage pictured here:

[http://img153.imageshack.us/img153/2556/w2u310xn.png](http://img153.imageshack.us/img153/2556/w2u310xn.png)

Both of the partions are the same size, so I can't tell which is which that way.

That picture was taken from here: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

Please help. :(

---

### Post by Sef on 2006-07-24
You should see if one is /.  / means that is the root partition where the operating system should go.

If there isn't one, then post what they say, so we can help you install it correctly. (Write down and post it here.)

---

### Post by confused57 on 2006-07-24
You could also boot up with the LiveCD, open a terminal:

```
sudo fdisk -l
```
The -l is a small "L".

This will show the partition table of the hard drive.

If there is any way at all possible, it would be best to reinstall Windows to the first partition; then install Ubuntu on the second partition...maybe someone else will have a better solution for you.
Good Luck.

---

### Post by fwqhgads on 2006-07-24
> **Sef said:**
> You should see if one is /.  / means that is the root partition where the operating system should go.

If there isn't one, then post what they say, so we can help you install it correctly. (Write down and post it here.)

When I get to the "Prepare Mount Points" section, the first one says:

/media/hda5...9 Gb...Partition 5 Dic IDE/ATA 1 (Logical [hda5]...No Reformat.

^ Those all being in the series of drop down boxes.

The second one says:

/...9 Gb...Partition 1 Disc IDE/ATA 1 (Primary) [hda1]...Reformat

Would this be correct? Will I be presented with a menue at startup to choose between Ubuntu and Windows? Sorry for being such a n00b here. I'm completely new to this. ](*,)

EDIT: Here's some screenshots.

[[IMG]http://img346.imageshack.us/img346/7395/screenshot1ei5.png[/IMG]](http://imageshack.us)
[[IMG]http://img373.imageshack.us/img373/7995/screenshot2lx9.png[/IMG]](http://imageshack.us)

..From what I can tell, this configuration will put Ubuntu on the Partition that I want to be able to boot Windows from.

---

### Post by fwqhgads on 2006-07-24
Actually, it does appear that it will put ubuntu on the empty partition. What does the /media/hda5 on my windows one mean though?

Also, do I have to do anything more to have it give me a boot menue at startup?

---

### Post by fwqhgads on 2006-07-24
Bump

I reallly need help guys. Please.

---

