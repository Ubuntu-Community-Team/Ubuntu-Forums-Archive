---
title: "Installation/Recovery"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by nonameface on 2008-04-05
Hello all,


I have recently installed Ubuntu onto my Dell laptop after losing all faith in Microsoft's ability to move operating systems forward; Vista has simply moved back to pre Windows 95.  I am finding Ubuntus stability and features to be fantastic, however, I have had some difficulties....

1. When I installed Ubuntu I made a back up of all of my pictures onto DVD, unfortunately there must have been a write error on the DVD and so the pictures are not on it.  

Because of this, I am looking for some way to be able to find all bmp's/jpeg's which were formatted on the old Vista partition so that I can recover them.  I am trying to use different software packages through synaptic and terminal but I don't have the knowledge and understanding to best use these.  Any help here would be greatly received.

2.  I believe I have installed Ubuntu twice as on start up it requests me to select the appropriate Ubuntu OS.  How do I remove one or both installations?

3.  Is there a way of removing the log in phase when booting the system, i.e don't need to enter user and password?


I am new to this operating system and have no experience of Linux based systems but do feel comfortable with computers/programs.  If you need me to give you more information so that you can help me I will try my best.

Thanks

---

### Post by dstew on 2008-04-05
> 1. When I installed Ubuntu I made a back up of all of my pictures onto DVD, unfortunately there must have been a write error on the DVD and so the pictures are not on it.Did you make this backup before you installed Ubuntu, that is, using Windows? After you made the backup, were you able to see the files in Windows? Did you check? When you installed Ubuntu, did you delete your Windows partition?> 2. I believe I have installed Ubuntu twice as on start up it requests me to select the appropriate Ubuntu OS. How do I remove one or both installations?Do you really have two separate installations? That is, are there partitions for two systems on your hard drive? Or, are the menu items for an old kernel, and a newer one, on the same system? Sometimes, when you update, you get a new kernel. That generates a new grub menu item. If you look closely, you will see that they are not identical.> 3. Is there a way of removing the log in phase when booting the system, i.e don't need to enter user and password?In System --> Administration --> Login Window, click the Security tab, and enable Automatic Login

---

### Post by zvacet on 2008-04-05
> I believe I have installed Ubuntu twice as on start up it requests me to select the appropriate Ubuntu OS.

Does second Ubuntu line end with (recovery mode)? If it is don´t remove it.

---

### Post by nonameface on 2008-04-05
Hi guys - thanks for the responses.

1.  I did indeed make the back up before using Ubuntu, i.e it was burnt in windows using nero.    I have looked at the amount of data burnt onto the back of the disc and it doesn't look like it would hold all the photos I had hoped I had put on.  But I am sure I saw them in windows on the disc before.

2.  I am pretty sure that I have two partions with two different OSs!  God knows how I did it but  I did.

3.  Thanks.


No it doesn't show that its used for recovery....

---

### Post by dstew on 2008-04-05
> 1. I did indeed make the back up before using Ubuntu, i.e it was burnt in windows using nero. I have looked at the amount of data burnt onto the back of the disc and it doesn't look like it would hold all the photos I had hoped I had put on. But I am sure I saw them in windows on the disc before.It might be easiest to put the DVD into a Windows computers and try to save the files on another type of media, like a USB stick or CD.> I am looking for some way to be able to find all bmp's/jpeg's which were formatted on the old Vista partition so that I can recover themIs the Vista partition still intact, or did you delete it?> 2. I am pretty sure that I have two partions with two different OSs! God knows how I did it but I did.You can delete one of the two Ubuntu root partitions (and swap if you duplicated that also). You can use the Gnome Partition Editor (System --> Administration) to do that. The partitions you delete have to be unmounted. After you delete the partitions, run```
sudo update-grub
```and your menu items should be deleted.

---

### Post by nonameface on 2008-04-05
Have tried to find the photos on the cd on a windows machine but cannot see them.  I assume that they are most probably lost as the hard discs are used in a different format with linux as apposed to vista right?

 I didn't partition vista off so I assume that that has completely gone.

I have gone on to Gnome Partition editor but cannot unmount the two separate parts of my harddrive.  I have added a screen shot of how it looks.

---

### Post by dstew on 2008-04-05
> I have added a screen shot of how it looksI don't see the screen shot.

---

### Post by nonameface on 2008-04-05
:( Oops

---

### Post by zvacet on 2008-04-05
In short,you deleted your windows partition and now it is unallocated space and you have large Ubuntu partition.My advice will be that you partition like this

1. root =10GB                                             mountpoint /
2.swap =1GB
3.home= rest of free space                       mountpoint /home

To make this you need to download [Gparted live Cd](http://gparted.sourceforge.net/) burn it and boot with it.Shrink Ubuntu partition and create new one on free space.Add unallocated space to newly created partition.Make separate home following [this.](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by nonameface on 2008-04-05
Okay, I can do those changes.  What will they do?

Will I be able to find the photos on the hard drive using some kind of tool?  Or should I give up hope on trying to get these back off the hard drive?

---

### Post by dstew on 2008-04-05
Since you have not overwritten your Windows partition, but only deleted it, it is possible that a partition recovery program can help. [Here is an article]("http://www.linux.com/articles/56588") that mentions two Linux programs, TestDisk and PhotoRec. You can install TestDisk using the Synaptic package manager. It seems that PhotoRec might be included with TestDisk in the Synaptic package. Make sure you enable the Universe repository (Settings tab in Synaptic). Good luck.

---

