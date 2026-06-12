---
title: "Multiple O/s and Grub screen"
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by rllarocca on 2016-12-31
Greetings.  I installed Xubuntu side by side with windows vista on one of my pcs.  I do not use Vista at all now and was hoping there was a way to eliminate the windows partition and grub screen without performing a whole new install of Xubuntu.

Thanks

---

### Post by grahammechanical on 2016-12-31
The answer is Yes. There is a risk of loosing data. So, back up any important documents that you do not want to loose. But having said that I have several times resized, moved, deleted and created partitions without breaking existing installations of Ubuntu.

To give specific advice we would need to see a screen shot of your partition layout. We do partitioning from a Xubuntu/Ubuntu live session and we use a utility called gparted. That utility will let us que-up several operations and they will take a long time to complete. I like to do things one operation at a time.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

To put it simply. We use Gparted from the live session to delete the Windows partitions. That will create unallocated space and then we expand the Ubuntu partitions to take up that unallocated space. If the Ubuntu partition is large enough we might just move the Ubuntu partition so that the unallocated space is behind Ubuntu and then use some of the unallocated space to create another partition that we can use as a data partition. Then we can re-install Ubuntu without risking the data in the data partition.

Please keep this in mind. The live session makes use of an existing swap partition and Gparted will not let us work on partitions if they are mounted. So, we have to go into the Gparted menu system to take swap off. 

You may have MBR partitioning. So, you may need a little help understanding Extended & Logical partitions and help to work with them. So, we come back to the usefulness of a screen shot of your partition layout. It does not matter if the screen shot is take from Windows or Xubuntu.

Oh, once we have finished with partitioning and you can load into Xubuntu open a teminal and run

```
sudo update-grub
```

That should re-configure the Grub boot menu and remove those references to Windows.



Regards.

---

