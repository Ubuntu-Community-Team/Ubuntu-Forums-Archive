---
title: "Adding new HD. &quot;Reinstalling&quot; Boot Info"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by Jodokos on 2007-05-07
Hello!

I have the following problem:

I moved around and changed partitions in feisty.

Before I had it installed with one "big" partition. Ubuntu and its /boot files were on one partition, /dev/sda4, ext3. (still booting from that).

Now I made some space free and copied everything over to /dev/sda8, ext3.

Except I made an extra partition for booting /dev/sda7, ext2. I copied the files from sda4/boot into that directory.

My questions are now: How do I tell my ubuntu installation to boot from /dev/sda7 and use (mount?) the partition /dev/sda8 as "/"?

What commands are needed?

I also moved my swap and ubuntu doesn't use the new swap partition anymore, it "forgets" the "swapon" command everytime.

(I can get the UUIDS of my new partitions, that should be no problem, but now - where/what to change?)


Thanx
Josef

PS: I'm a little familiar with grub and the fstab and searched the forums, but could'nt find a suitable answer.

---

### Post by Jodokos on 2007-05-08
Ok, at least I got a part:

The swap file can be set in fstab: Get the UUID of the new swap-partition and replace the old old with the new one.

In /boot/grub/menu.lst (note: <-the one from sda4) I changed every occurence from my UUID of sd4 and replaced it with the UUID from my sda8.

Then changed 
```
root            (hd0,3)
```

to

```
root            (hd0,7)
```.

Booted from the new partition.
Then I copied the menu.lst from sda4 over to sda8.
Now the system runs from the sda8-partition like intended.

However, one big issue is left:
How do I make it boot from my extra boot-partition? Which settings are important?


Thank you
J.

---

### Post by Jodokos on 2007-05-23
I really ask myself:

Are my posts not ok at some point??

I mean, this is already the 3rd post or so I'm doing on this forum that has been completely ignored!

Is there some advice on how to change my posts so that I can get finally some help from this forum?

Thanks!
J.

---

### Post by LaRoza on 2007-05-23
To answer your question about why no one answered your post, it is not you, it is probably the question. If a lot of people viewed your post and didn't answer, it probably means they do not know. (I don't know myself).

To increase the probability of getting answers, keep the post as short as possible and state the question clearly. It is a good idea to start out with saying what you want to do, then saying what happened.

Also, you seem very good at doing things yourself, such a question is difficult to answer, because the question changed as you went. Try posting the new question separately .

Sorry I couldn't help, but I hope somebody does.

-edit 76 viewed, none answered, they do not know the answer

---

