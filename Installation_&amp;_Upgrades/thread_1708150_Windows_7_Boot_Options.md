---
title: "Windows 7 Boot Options"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by jmvizanko on 2011-03-16
I installed Ubuntu 10.10 on my laptop that is a new gateway with Windows 7 on it, as a full dual boot installation. I went with the automatic partition resizing option (I know, I should have done more research and probably figured out what I was doing more with repartitioning).
 
I now get two options for booting Windows 7. One is SDA2, and one is SDA3. Does it matter which one I select? It does boot up in both (hopefully trying that wasn't bad). I'm assuming one is more of a Windows system partition and the other is for all the user's free space? (obviously a huge newb here)
 
And also, can you rearrange the boot up selection list, so that Windows 7 is at the top (so if I don't hit any keys, it default goes into Windows)?
 
Thanks for any help.

---

### Post by zvacet on 2011-03-16
From synaptic install **startup manager** and with it select Windows as first boot option.

---

### Post by ronparent on 2011-03-16
When Win 7 is installed, it creates a small boot partition and a second partition to install to. I don't know why the grub menu shows both. You select the 1st instance to boot to win 7. If selected the second instance will do nothing.

---

### Post by jmvizanko on 2011-03-16
Thank you for the Synaptic suggestion, although I can't try it out at the moment.

As for selecting the second windows partition to boot from, they both successfully start windows 7.  Is there any reason why it would be bad if the wrong one was selected?  I can only imagine no, but I obviously don't understand why.  Thanks again for any help.

---

### Post by jmvizanko on 2011-03-16
Startup Manager was exactly what I needed to know about, so thanks.

Now if I could have a better understanding of what it means to select either of the two windows boots, I would be good to go.

---

### Post by Mark Phelps on 2011-03-17
When PCs come with Win7 preinstalled, they typically have the following partitioning scheme:
1) Boot partition -- contains boot loader directory and files
2) OS partition -- contains OS files

GRUB2 sometimes sees BOTH partitions as containing Win7.

If, by some chance, you happen to have the boot loader files installed in both partitions, then you're basically booting to the same Win7 each time.

Usually, the boot partition is very small (100MB or so), so I would look at the size in Win7 or Ubuntu.  Then, look at the contents of grub.cfg -- to see which entry is pointing to which partition.

Select the entry that is pointing to the larger Win7 OS partition.

---

### Post by jmvizanko on 2011-03-17
Thanks for the help.  This topic could be changed to solved now.

PS: I really have to wonder why I didn't try this OS before.  I'm in love.

---

### Post by wilee-nilee on 2011-03-17
> **jmvizanko said:**
> Thanks for the help.  This topic could be changed to solved now.

PS: I really have to wonder why I didn't try this OS before.  I'm in love.

You have to do the solve look in thread tools when logged in on this thread.

---

