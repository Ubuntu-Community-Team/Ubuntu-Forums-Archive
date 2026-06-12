---
title: "Need help from someone that understands PARTITIONS."
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by jthompson99 on 2011-01-22
Ok, so I have a laptop that has a 320GB HDD that is is equally divided into the C: and D:

Well, I installed Ubuntu and loved it, but I am selling the computer so I want to put it back to the way it was. So I restored the windows installation to the factory default and I removed GRUB so that it boots directly into Vista.

Now, I noticed that the C: drive is like 140GB and the D: is like 72GB.

So I put the Ubuntu install CD back in so I could use the gparted but I didn't exactly know what I was looking at. So I took a screenshot of the current partition situation.

[IMG]http://c.imagehost.org/0636/partitions.jpg[/IMG]

I need some advice on what to delete and/or resize in order to get this back to the way it was.

Thanks.

---

### Post by PRC09 on 2011-01-22
If you are going to re-size your partitions in Vista use the tools in windows itself.If not Vista will not boot and you will have to repair again.
Start > control panel > System and Maintenance > Admin Tools > Computer Management > Disk Management......

---

### Post by jthompson99 on 2011-01-22
> **PRC09 said:**
> If you are going to re-size your partitions in Vista use the tools in windows itself.If not Vista will not boot and you will have to repair again.
Start > control panel > System and Maintenance > Admin Tools > Computer Management > Disk Management......


Oh ok, thanks, I didn't know you could do it like that.

Any ideas which of these i can remove?

Anyone know what "extended" or "ext4" means?

---

### Post by Quackers on 2011-01-22
Normally that advice is good, however Windows won't see your Linux partitions.
Boot from an Ubuntu live cd/usb (or whatever medium you used to install Ubuntu) and select "try ubuntu" and when the desktop loads go to System > Admin > gparted.
When the screen finishes loading right-click on the swap partition (/dev/sda6) and select "swapoff". Then right-click it again and select "delete" to delete the partition.
Next right-click on the ext4 partition (/dev/sda5) and if shown click on "unmount". If not shown as an option choose "delete" to delete the partition.
In the toolbar above click on the green arrow to apply the changes.
When that's run, right-click on the extended partition (/dev/sda4) and select "delete", then click on the green arrow to apply the change.

An extended partition is a partition which contains logical partitions (sda5 and sda6, in your case)
Ext4 is a file system type for Linux systems.

Please note that the above instructions will remove all traces of your Linux file system (except the grub bootloader, which it appears you've already replaced with the Windows bootloader). Any data in it will be lost! 
As it seems that is your wish you'll be ok then :-)

---

### Post by PRC09 on 2011-01-22
Sorry I just had a Vista machine beside me and remembered how I screwed things up with partitioning before.Ext4 is the Ubuntu native file system and swap is with Ubuntu as well.As to deleteing and resizing I am not sure so hang in there,I am sure someone will advise......

---

### Post by jthompson99 on 2011-01-22
> **Quackers said:**
> Normally that advice is good, however Windows won't see your Linux partitions.
Boot from an Ubuntu live cd/usb (or whatever medium you used to install Ubuntu) and select "try ubuntu" and when the desktop loads go to System > Admin > gparted.
When the screen finishes loading right-click on the swap partition (/dev/sda6) and select "swapoff". Then right-click it again and select "delete" to delete the partition.
Next right-click on the ext4 partition (/dev/sda5) and if shown click on "unmount". If not shown as an option choose "delete" to delete the partition.
In the toolbar above click on the green arrow to apply the changes.
When that's run, right-click on the extended partition (/dev/sda4) and select "delete", then click on the green arrow to apply the change.

An extended partition is a partition which contains logical partitions (sda5 and sda6, in your case)
Ext4 is a file system type for Linux systems.

Please note that the above instructions will remove all traces of your Linux file system (except the grub bootloader, which it appears you've already replaced with the Windows bootloader). Any data in it will be lost! 
As it seems that is your wish you'll be ok then :-)

Nice detailed advice. Thanks man, I will try this out.

---

### Post by garvinrick4 on 2011-01-22
#I do not know which ones you want to delete, you can delete the ones you want in
a Ubuntu install Cd using Try Ubuntu (called live cd) in that program gparted and then resize the sda2 which is the Windows install.
#What is in the data partition there is 3 gig being used?
#You cannot work on any partition that is mounted see the keys next to the partition that
means they are locked or cannot work on them because mounted. Use live CD.
#ext4 is the format for linux like NTFS is for Windows.
#extended partition is a house for logical partitions which linux likes to reside in.
#Do not need sda4, sda5,sda6 
#Again what is sda3 ?

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Quackers on 2011-01-22
No problem :-)
Just a couple of things.
In addition to the above info, if you want to increase the size of your Windows partition(s) to use up the full disc space, DON'T use gparted to do it. Use the disk management screen in Windows to do that.
One other thing. You said in your original post that you had returned the system to its original state (presumably by using the recovery partition, or a set of recovery dvd's). Normally this process will tend to use the whole hard drive space to do this. Thereby over-writing the Linux partitions. This hasn't happened here. Are you sure the pc is back to original condition?

---

### Post by jthompson99 on 2011-01-22
Ok, so I went in and delete the partitions like you said using Ubuntu and then I went into Vista and used Computer Management and increased the 70GB partition to 140GB partition.

Thanks again for the help.

---

### Post by Quackers on 2011-01-22
Nice one :-)

---

### Post by srs5694 on 2011-01-22
Since you intend to sell the computer, I must strongly suggest that you take a completely different approach:


[list=1]
[*]Boot using an Ubuntu CD into live CD mode or using some other Linux emergency disc.
[*]Open a Terminal window.
[*]Type "sudo dd if=/dev/zero of=/dev/sda". This command will take quite a while to finish (several hours). Its intent is to completely erase all the data on the hard disk.
[*]Reboot into your Windows recovery disc and re-install Windows using the default settings.
[/list]


The problem you've got now is that even if you delete your Ubuntu installation and move/resize your Windows partitions, traces of your old data will remain on the hard disk. I'm afraid that Quackers' assurance that your data "will be lost" isn't quite accurate; although the data will be inaccessible to the usual tools, deleting partitions just deletes the indexes to files, not the files' contents. The files, even though no longer indexed via a filesystem, remain recoverable using tools like [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) so your buyer could go snooping through your old files if s/he is so inclined. Although I expect that most buyers wouldn't try this, I also expect that some small percentage of them do, either out of curiosity or for more nefarious purposes. If the buyer is able to recover a credit card number or some other sensitive data, the consequences to you could be pretty bad. (It once took me *months* to get bogus charges removed from a credit card!) Thus, you really should be zeroing out the hard disk prior to selling it to prevent this from happening.

---

