---
title: "No basic filesystem?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Vinze on 2007-05-01
Hello,

This man I'm helping to install Ubuntu (via email) made partitions for Ubuntu in Windows with the program [PartitionExpert](http://www.acronis.com/homecomputing/products/partitionexpert/index.html).

Now, when he tries to install Ubuntu Feisty, he gets the following screen:

[[img]http://farm1.static.flickr.com/226/480145795_1eaaca4f2c.jpg[/img]](http://www.flickr.com/photos/vincentt/480145795/)

This error says something like "No basic filesystem defined. Please restore this from the partitioning menu."

However, the only option he then has is formatting the whole of hda, while he wants to dual boot with Windows. How can he fix this?

Thanks in advance.

---

### Post by loserboy on 2007-05-01
choose the manual partition option, then if i remember right, you just click on the ntfs partition and choose create new i think

---

### Post by Vinze on 2007-05-01
> **loserboy said:**
> choose the manual partition option

That's what he did, as you can see from the "New partition table" button ;)

---

### Post by mcduck on 2007-05-01
The easiest way would probably be to remove the partition he made with the windows tool, and just leave the disk space as empty unpartitioned space. Then let the Ubuntu installer create the partition.

---

### Post by Vinze on 2007-05-01
> **mcduck said:**
> The easiest way would probably be to remove the partition he made with the windows tool, and just leave the disk space as empty unpartitioned space. Then let the Ubuntu installer create the partition.

Sounds plausible, I'll recommend that and post back the result, thanks!

---

### Post by loserboy on 2007-05-01
> That's what he did, as you can see from the "New partition table" button 

sorry, i'm not used to the feisty installer, I only have one comp with feisty.

looks like vinze has it covered, I had a problem with partition magic once when i trying to make some ext3 parts and ubuntu didnt like it at all.

---

### Post by Apoorv on 2007-05-04
My problem is somewhat similar, that's why I'm hijacking the thread. I booted from the Xubuntu 7.04 live CD, everything was perfect, it even mounted all my partitions and placed shortcuts to them on my desktop.the stupid thing is, the installer and GNOME Partition editor, both do not read my partiton table, and display 74 GB of unallocated space. It's not a defect in the architecture, as it has mounted my NTFS partitions too, and I can read them. I wanted to post a screenshot, just to show how stupid it looks, having shortcuts to partitions on the desktop and a window telling me my hard disk is blank, but the system hangs on taking a screeenshot. Any ideas, as to what the problem could be?

---

### Post by Vinze on 2007-05-04
> **Apoorv said:**
> My problem is somewhat similar, that's why I'm hijacking the thread. I booted from the Xubuntu 7.04 live CD, everything was perfect, it even mounted all my partitions and placed shortcuts to them on my desktop.the stupid thing is, the installer and GNOME Partition editor, both do not read my partiton table, and display 74 GB of unallocated space. It's not a defect in the architecture, as it has mounted my NTFS partitions too, and I can read them. I wanted to post a screenshot, just to show how stupid it looks, having shortcuts to partitions on the desktop and a window telling me my hard disk is blank, but the system hangs on taking a screeenshot. Any ideas, as to what the problem could be?

I can't help you with your problem, but perhaps you can use the Gimp to take a screenshot: File->Acquire->Screenshot.

---

### Post by Apoorv on 2007-05-05
Goddamnit, thread hijackers! BUMP.

---

### Post by Apoorv on 2007-05-06
<bump>

---

### Post by Apoorv on 2007-05-06
[IMG]http://i76.photobucket.com/albums/j26/apoorvkhatreja/stupidity.png[/IMG]


Here's the screenshot, I finally managed to take it.

---

