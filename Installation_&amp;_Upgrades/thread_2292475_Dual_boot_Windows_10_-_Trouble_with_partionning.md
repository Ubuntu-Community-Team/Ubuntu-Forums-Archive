---
title: "Dual boot Windows 10 - Trouble with partionning"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by Milleuros on 2015-08-28
[SIZE=1]*Look, another guy having trouble with Ubuntu installation*[/SIZE]

Hello, 

I am new to these forums and Ubuntu generally, so please forgive my mistakes.


I have bought many years ago a laptop (Sony Vaio) with Windows 7. Recently I installed Windows 10, making a clean install with Windows utilities. So I guess, wiping out the hard drive. I now want to make a dual boot with Ubuntu 14.

Following tutorials, I have backed up Win10 (and all my files) and am now installing Ubuntu from a DVD. I reached the point where we resize partitions. I indeed selected the main partition and took around 80Go out of it, which should be enough. However, the free space is now marked as unusable.

Lurking around, it seems that there is a maximum of 4 partitions on most prebuild computers, so I cannot create a 5th one. Thus, I have to delete one.

My question is : how do I know which one is safe to delete ?

Here is the output of **fdisk** command :

[IMG]http://i.imgur.com/ratzBCo.png[/IMG]

And here is the main screen of the **GParted** utility

[IMG]http://i.imgur.com/QSZUZcN.png[/IMG]

---

### Post by oldfred on 2015-08-28
Best to only use Windows own tools to shrink the NTFS partition and reboot immediately into Windows as it has to run chkdsk after a resize.
With Windows 8 or later make sure you have fast startup in Windows off.
If you reinstall Windows always backup MBR partition table details before reinstalling. Windows almost always "forgets" to write the Linux logical partition.

Most vendors have a vendor tools partition like HP. That often can still be downloaded, is smaller and easily backed up, so often first choice. Another is the original vendor recovery partition. Once you have make the vendor recovery DVD set or flash drive that partition is not required.

If you have new install & full backups, you may not need either of the vendor tools or vendor recovery partitions.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Milleuros on 2015-08-28
Thank you for the answer.

In the first link you post, a guy post as a first step to delete the partition dedicated to HP tools. I understand that quite easily, but the problem is thatmy partitions lack tags or descriptions, and thus I do not know which one to safely delete.
My intuition would point toward **/dev/sda4 **but since this operation is irreversible I do not want to simply try out of intuition.

---

### Post by oldfred on 2015-08-28
You have two partitions with diag flags. Larger sda1 is probably the vendor recovery and smaller sda4 the vendor tools. 
What brand/model system? Best to check vendor manual or site on your model and see if they have download of tools partition. Or any explanation of what it contains.
And backup partition (s) and then you should be able to delete it. With HP some have restored it as a logical partition and found it still works, not sure about other brands.

---

### Post by Milleuros on 2015-08-28
If I made a clean install of Windows 10, the vendor recovery tools should have been deleted, right ?

The complete model of the computer is : Sony Vaio VPCEB2S1E
I am currently reading through the user manual, although I'm affraid that this information is not available.
Edit : Cannot find anything about what each of these partitions are.

---

### Post by oldfred on 2015-08-28
Installs of a new system do not typically delete anything other than what you are overwriting.
I might just create Sony's recovery set of DVD just in case you ever wanted system back to as purchased. If not then that partition does not matter.
System tools is small so easily backed up. I would think you could restore it as a logical partition but do not know how Sony uses it or what it has.

---

### Post by Milleuros on 2015-08-28
I am not interested in Sony tools nor in recovering the factory settings, so I guess I can just delete it.

---

### Post by Mark Phelps on 2015-08-28
When you install Win10 it alters the partitioning on the drive and, in many cases, creates a 450MB recovery partition -- which contains a compressed rollback image of the previous OS -- and that allows you to use GoBack to restore the previous OS.  It also might be the original Sony recovery partition, not a new partition created by Win10.  Either way, if you remove it, you will not have the means of going back to a prior OS.

Also, if you did not do an in-place upgrade to Win10, but instead, did a clean-install of Win10, unless you purchased an OEM or Retail license from MS, your version of Win10 will never activate and will eventually expire. Unlike with previous OS versions, Win10 will not accept product keys for activation; instead, that is done as part of the in-place Upgrade.

---

### Post by Milleuros on 2015-08-29
I first made a normal upgrade of Windows 10 and then using Win10 own tools I made a reset of the system. This way I avoid the expiration problem you mention. Making a reset also prevents me from ever returning to my old Win7, so no problem in deleting this 450Mb recovery partition ?

(I used the tool mentioned [here](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) under Reset your PC -> Remove Everything, but did not activate the option to clean the disk).

---

