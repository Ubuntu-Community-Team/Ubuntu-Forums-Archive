---
title: "novice needs help with installation 11.04"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by mdm27 on 2011-08-15
I desperately need some help installing Ubuntu 11.04. I am using a Samsung N140 netbook and the USB installation process. 

I'm getting stuck at the "allocate drive space screen".

I go through the installation process and all is well. My computer has the necessary 4.4 Gb and its on line and plugged into the mains. 

I need to keep Windows (as some of my work programs will only run through Windows) so I am trying to install it alongside Windows. As such, I select "something else". 

This leads into the allocate drive space screen. I have a bar running across the top of the screen. This is coloured green, then blue, then green again. I'm fairly new to all this, but it seems to me that this represents the existing partitions. 

I am now at a complete loss as to how to proceed. Can someone please help? I would be grateful if any explanations could be explained in idiot language, for (sadly) I am an idiot. 

Many thanks

---

### Post by mdm27 on 2011-08-15
I should add that whenever I click "install now" I get a warning box reading:

"No root file system is defined.

Please correct this from the partitioning menu"


Thanks

---

### Post by Megaptera on 2011-08-15
Hi,
Could you please try to post a screenshot of your current partitions (the green, blue and green again).
This might help others to better guide you.

Also,just in case, have you backed up all your important docs, pics & vids to external media ... 'cos you can't be too careful!

---

### Post by mdm27 on 2011-08-15
sadly, a screen grab is slightly beyond my abilities, however I am able to take a photo on my phone and upload it, which I have done (with some level of embarrassment). 


Thanks for the suggestion.


[ATTACH]200100[/ATTACH]

---

### Post by MarkVS on 2011-08-15
I will try to help as best I can, as I have been in the exact same spot you have, and botched my first installation. You do not seem to be an idiot, so I assume that you mean idiot to Linux. The warning you see is that you haven't told the installer where to put Ubuntu. When you make a partition for it, you must tell it that you want it to be mounted as "/" (root). To make a partition, you must either wipe one of the existing ones or resize one and make a new one. It would be easier to wipe one of them, but make sure you know which one your doing and what is in that partition. And just to be safe, you should also back up all your data on another hard drive.

---

### Post by mdm27 on 2011-08-15
that's really helpful, thank you. 

Are you able to tell me how to do this? My largest partition, the last green one, is free (I have already cleared it and everything is backed up nicely). 

How can I tell Ubuntu that I want to install it there?

Thank you so much for taking the time to reply, I've been pulling my hair out!

Cheers

---

### Post by Quackers on 2011-08-15
You appear to have 4 primary partitions. This is the maximum number of partitions on an mbr partitioned disc. Consequently there is nowhere for Ubuntu to install to at the moment. It will be necessary to delete one of those primary partitions and, if necessary shrink another partition to give the necessary free space for Ubuntu to install into, then create an extended partition. This new extended partition can hold as many LOGICAL partitions as you wish to create.

---

### Post by Megaptera on 2011-08-15
Useful guide with screenshots re partitioning and making 'free space'.
[http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/)
Says W7 but process similar for Vista.

Hope this helps?

---

### Post by mdm27 on 2011-08-15
How can I delete one of the partitions? Do I have to do this through windows? If so, how?


Again, many thanks

---

### Post by Megaptera on 2011-08-15
> **Megaptera said:**
> Useful guide with screenshots re partitioning and making 'free space'.
[http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/)
Says W7 but process similar for Vista.

Hope this helps?

Posted at same time as your question I think? :D

---

### Post by MarkVS on 2011-08-15
Quackers is completely right. You need to change the last partition to a Extended partition. Click on the last one in the list (sda4) and then click delete. Confirm the delete, then add a new partition there. Make this one an Extended partition, not a logical one. Make sure it uses all the space available. After you make that one, make a partition inside this one (yes it can do that). This will have to be a logical partition. Make this however big you want it, but most likely it will take up all the space. You can leave some room to make other partitions, but I would just make one big one. Make this with a file system of "ext4" and make sure that it is mounted at "/". After you select these, it should let you make the partition and let you install.

---

### Post by Quackers on 2011-08-15
Alternatively you could delete the chosen partition from within Windows Disk Management and leave the resulting "unallocated space" untouched.
You can then boot from the Ubuntu live cd/usb and install using the "install alongside" option. This process should automatically create an extended partition which will include logical partitions for both the root file system and a swap space.

---

### Post by mastablasta on 2011-08-15
also deleting the partition also deletes any data you might have on it. recovery of data deleted in such a way is very difficult.

---

### Post by mdm27 on 2011-08-16
I just wanted to pass on my thanks to all those who took the time to reply. Your advice was invaluable. 

I deleted one of my partitions using the Disk Manager in Windows. This created free unallocated space enabling me to complete the installation process. 

Many thanks again!

---

### Post by Quackers on 2011-08-16
Very nice :-)
Please mark the thread as solved using the Thread Tools near the top of the page.
Happy Ubuntuing!

---

