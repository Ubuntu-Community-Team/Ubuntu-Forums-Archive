---
title: "Dualboot problem. Need help."
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Swedish Berserk on 2010-12-05
Hello Ubuntu veterans! I have a major problem and i really need your help. I have tried everything and googled for hours..... 

I want to dualboot my HP laptop with Windows 7 and Ubuntu. The problem is that the harddrive had 4 primary partitions. So i had to delete the Recovery and HP TOOLS partions. I did that after creating my system recovry CDS. 

But now i have a new problem. The "install alongside another operating system" option showed up. And i was really happy for about 1 minute until i discovered that it said Windows Vista loader! 

So now i have this:
sda 640GB harddrive
sda1 Windows 7 loader
sda2 Windows Vista loader

And when im trying to install a dualboot the Windows 7 loader dosent show up! It wants to install Vista loader but i dont have that operating system. I have read that 7 and Vista sometimes gets mixed up in GRUB can this be the case here? Is it safe for me to install Vista loader with Ubuntu 10.10?

I really really need your help i have a massive headache and im absolutly tired. 

Please help me i want Ubuntu on my laptop! 

And sorry for my english im from Sweden.

---

### Post by Quackers on 2010-12-05
It is possible that in deleting the recovery partition you deleted the first 2 Windows boot files. Are you in Windows 7 now?

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> It is possible that in deleting the recovery partition you deleted the first 2 Windows boot files. Are you in Windows 7 now?

Thank god for your fast reply Quackers! Your my hero! :p Yes im in Windows 7 now works like a charm. 

I havent messed with the Windows partitions. I have only deleted the HP partitions. Recovery D: and HP TOOLS E:. 

But how can i fix the dualboot installation? Or should i install Windows Vista loader with Ubuntu 10.10? What do you think mate? 

I did a dualboot quite recently on my Desktop everything worked fine no problems. I bet this is because im running a OEM machine..... 

If you have any ideas please help me im totally lost in this one..... :(

---

### Post by Quackers on 2010-12-05
Go to Start > Control Panel and then select Backup and Restore. On the left of the screen you will see "create system recovery disc" click on that, put a blank cd in the drive and make it :-) It's worth its weight in gold.

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> Go to Start > Control Panel and then select Backup and Restore. On the left of the screen you will see "create system recovery disc" click on that, put a blank cd in the drive and make it :-) It's worth its weight in gold.

I have already burned the HP system recovery discs! I just want to have Ubuntu now on my sytem. :sad:

What do you think is wrong with my system?

---

### Post by Quackers on 2010-12-05
The recovery discs won't repair your MBR and boot files. The repair cd will. You may even need to use it later.

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> The recovery discs won't repair your MBR and boot files. The repair cd will. You may even need to use it later.

Oh okay. My Windows is in swedish do you mean the first alternative to the left?

---

### Post by Quackers on 2010-12-05
I mean the one that translates as "create system recovery disc"  :-)
In Backup and Restore centre

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> I mean the one that translates as "create system recovery disc"  :-)
In Backup and Restore centre

Haha im so tired in my head. Im so sorry. :p

---

### Post by Quackers on 2010-12-05
That's ok :-) If you make the disc then try to reboot and see whether Windows boots ok you can have a sleep. There are many who can give the advice I can.

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> That's ok :-) If you make the disc then try to reboot and see whether Windows boots ok you can have a sleep. There are many who can give the advice I can.

I now that Windows is ok. The thing im trying to understand is why Ubuntu shows my Windows 7 as a Windows Vista loader in the dualboot installation.

---

### Post by Quackers on 2010-12-05
Have you rebooted since you deleted the partitions?
Sometimes Linux mis-labels Vista and Win 7 partitions.

Edit do you mean the grub menu?

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> Have you rebooted since you deleted the partitions?
Sometimes Linux mis-labels Vista and Win 7 partitions.

Edit do you mean the grub menu?

Im setting up some pictures. And in the bootloader box i have three options:

sda 640GB HDD
sda1 Windows 7 loader
sda2 Windows Vista loader

And if you look at the top bar
sda1 contains 208mb 
sda2 contains 640GB

I think that the Windows 7 loader is sda1. And sda2 is where all the goodies are. But why in the world does Ubuntu want sda2 to be the bootloader for Windows Vista??? 

Please help! :(

](*,)

---

### Post by Quackers on 2010-12-05
sda1 includes the first 2 Windows boot files. sda2 is your main Windows partition. This is how oem Windows 7 installation often are. I suspect that sda2 is named Vista by mistake because there is only the winload.exe boot file in it (none of the first 2 boot files) and that is how Ubuntu recognises that file.
I hope your second screenshot is out of date! I presume so.
If you are installing Ubuntu 10.04 you will be ok. If you are installing Ubuntu 10.10 you should select the "specify manual partitions" option as it would be safer. Some people have unexpectedly over-written partitions with the 10.10 installer by selecting "install alongside".

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> sda1 includes the first 2 Windows boot files. sda2 is your main Windows partition. This is how oem Windows 7 installation often are. I suspect that sda2 is named Vista by mistake because there is only the winload.exe boot file in it (none of the first 2 boot files) and that is how Ubuntu recognises that file.
I hope your second screenshot is out of date! I presume so.
If you are installing Ubuntu 10.04 you will be ok. If you are installing Ubuntu 10.10 you should select the "specify manual partitions" option as it would be safer. Some people have unexpectedly over-written partitions with the 10.10 installer by selecting "install alongside".

Hm why would it be easier with 10.04? Does it recognize it in the right way? So this is a 10.10 bug? I want to do the simple install alongside another operating system option way. 

So this is because its an OEM laptop? My own Desktop with custom components works fine in dualboot with Ubuntu 10.10. 

Im sorry for my bad english hope you understand and thanks for all your help it means alot to me. :p

---

### Post by Quackers on 2010-12-05
Yes, an oem installation of Win 7 is different nowadays.
Yes, the 10.10 installer has bugs logged about its "install alongside" option. People have trashed existing installations with it. It is much safer to select the manual option and make your own swap and root (/) partitions. You just need to take a bit of care. It's quite obvious if you think a bit about it. You just need to remember to use ext4 for the root partition and to select the mount point as " / " and to check the box to format it. You should also select Logical for partition type rather than Primary. Your swap partition is simpler to make.

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> Yes, an oem installation of Win 7 is different nowadays.
Yes, the 10.10 installer has bugs logged about its "install alongside" option. People have trashed existing installations with it. It is much safer to select the manual option and make your own swap and root (/) partitions. You just need to take a bit of care. It's quite obvious if you think a bit about it. You just need to remember to use ext4 for the root partition and to select the mount point as " / " and to check the box to format it. You should also select Logical for partition type rather than Primary. Your swap partition is simpler to make.

Hello again. This is how the 10.04.1 looks like. 

Same problem i think. Anyone have a good guide for manually partitions?

---

### Post by Quackers on 2010-12-05
There is something wrong here. That is similar to the second screenshot you posted before. According to that you have Windows occupying 639GB and no free space for Ubuntu to install to. You should have some unallocated space from the partitions you deleted, but it's not showing.
Also is Ubuntu already installed. It's very unclear to me.

---

### Post by Swedish Berserk on 2010-12-05
> **Quackers said:**
> There is something wrong here. That is similar to the second screenshot you posted before. According to that you have Windows occupying 639GB and no free space for Ubuntu to install to. You should have some unallocated space from the partitions you deleted, but it's not showing.
Also is Ubuntu already installed. It's very unclear to me.

No it is not. And when i deleted the HP partition it merged into the C: drive. I have no idea what is wrong here. I need help im clueless. 

And thanks for helping me Quackers.

EDIT: Maybe i need to shrink the Windows partitions? I just dont understand why it shows Windows Vista loader.....

---

### Post by Quackers on 2010-12-05
I suggest you boot back into Windows and post a screenshot of the Disk Management screen, if you will please.

---

### Post by wilee-nilee on 2010-12-05
Post a screen shot of the gparted partition manger on the live Ubuntu cd, or thumb, which ever your using.

menu-system-admin-gparted

Your going to want to be familiar with gparted at the least it is a important tool.

---

### Post by Swedish Berserk on 2010-12-05
Thanks for all your help today. Quackers thanks for helping me. Here is the screenshot you requested. 

Its getting late here in Sweden and im pooped for today. Hope you can continue helping me tomorrow :p

Note that its in Swedish hope you understand something of it.....

---

### Post by Quackers on 2010-12-05
Thanks.
If you have a 640GB hard drive there are approximately 40GB missing. It may be an idea to run a chkdsk over night.
Also how did you delete the two partitions? 
Tomorrow will do though. 
Go to sleep :-)

---

### Post by Swedish Berserk on 2010-12-06
> **Quackers said:**
> Thanks.
If you have a 640GB hard drive there are approximately 40GB missing. It may be an idea to run a chkdsk over night.
Also how did you delete the two partitions? 
Tomorrow will do though. 
Go to sleep :-)

The first partition the Recovery one ca 16GB was deleted using HP:s own software. It merged the partition with C:. 
The second one i simply deleted with diskmanager. It was only a ca 100MB partition.

---

### Post by Quackers on 2010-12-06
So the 103MB free space at the end of the disc is from the deletion of one partition.
In that case I would suggest shrinking the C: drive.
But first it is highly recommended to defrag the drive at least once. Twice is better!
 Then in the disk management window you should right-click on the C: drive and select "shrink". The resulting window will show the amount of shrinkage which Windows thinks is available. It may be up to half the disk size. Choose how much you want to shrink C: by and click OK.

Then you can boot from the Ubuntu Live cd and install away and manually create your partitions for Ubuntu.

---

### Post by Swedish Berserk on 2010-12-09
> **Quackers said:**
> So the 103MB free space at the end of the disc is from the deletion of one partition.
In that case I would suggest shrinking the C: drive.
But first it is highly recommended to defrag the drive at least once. Twice is better!
 Then in the disk management window you should right-click on the C: drive and select "shrink". The resulting window will show the amount of shrinkage which Windows thinks is available. It may be up to half the disk size. Choose how much you want to shrink C: by and click OK.

Then you can boot from the Ubuntu Live cd and install away and manually create your partitions for Ubuntu.

I forgot about this thread. Im so sorry. I managed to get it to work the only downside is that i have Windows 7 loader on sda1 and Windows Vista loader on dev2 in GRUB. After installation i had no sound but managed to fix it when updating my ALSA driver. Tried installing FGLRX driver but got stripes in the menus..... So im back with the open source driver but the computer runs fine. I can play 1080P with it so im satisfied ( ATI HD4250 ) is the card im using. 

Quackers thanks for all your help! And thanks to all the other people who helped me! :guitar:

Solved! ;)

---

