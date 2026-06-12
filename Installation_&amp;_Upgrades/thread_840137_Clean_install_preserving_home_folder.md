---
title: "Clean install preserving /home folder?"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by blazini on 2008-06-25
When I first installed Ubuntu Feisty I obviously didn't realize I should have seperated the /home partition. I'm running Gutsy with a few issues and the update manager won't update to Hardy because of some sort of problem. Even if I got that fixed I really wouldn't trust the update considering the things I had to work out on the Gutsy upgrade, I'd rather do a clean install.

The problem is that the Gutsy install is on a 500gb hdd and it's almost full of data, only 6.6gb are free. Obviously I can't create a partition and move /home to it. I'm thinking maybe I can create a partition with the 6.6gb I have free and do a clean install of Hardy on that, then just wipe out everything on the 493.4gb partition except the /home folder (or any others I may want to keep, suggestions?) 

I don't see why it wouldn't work. It seems like such a simple idea, but I've read other posts with the same issue and this was never advised as an option. I can probably free up maybe another 10gb, if for any reason Hardy should have a bigger partition. Any suggestions?

---

### Post by Kobalt on 2008-06-25
If you don't have big programs to install in Ubuntu, then 6,6Gb can be just fine for a whole Ubuntu system. You can leave your data on a separate partition, and create a custom mount point in your system to have a convenient access to it... I see no problems in what you are trying to do.

---

### Post by meindian523 on 2008-06-25
You can back up your /home to an external storage and then just install over Gutsy.

---

### Post by blazini on 2008-06-25
> **meindian523 said:**
> You can back up your /home to an external storage and then just install over Gutsy.

Not an option, as I said in my post.

---

### Post by Partyboi2 on 2008-06-25
If you were to reinstall my understanding is that you will loose what ever is on that partition. Because your /home folder is currently on the same partition that you need to reinstall to, you would loose your /home folder + contents, unless it is moved to its own partition (which you mentioned you are unable to do).
What size is your /home folder?

---

### Post by meindian523 on 2008-06-26
Why can't you install over Gutsy using a Live CD?That's what's called a clean install,in case you are thinking that upgrading to Hardy through Update Manager is what is called a clean install.It's NOT!

---

### Post by blazini on 2008-06-26
> **Partyboi2 said:**
> If you were to reinstall my understanding is that you will loose what ever is on that partition. Because your /home folder is currently on the same partition that you need to reinstall to, you would loose your /home folder + contents, unless it is moved to its own partition (which you mentioned you are unable to do).
What size is your /home folder?Right, I don't have the space to create a new partition then move /home to the new partition. What I wanted to do was shrink the partition that  has the current install, and create a new smaller partition in the unallocated space to install hardy. 

I actually did it already, seemed to work alright. I just have to edit grub to make the new partition bootable.

---

