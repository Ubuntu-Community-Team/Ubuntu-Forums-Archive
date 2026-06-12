---
title: "Ubutu 12.10 with Win 8 - HDD not selecting"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by matrunner on 2013-01-03
I have windows 8 installed. I have 6 Drive partition out of 320 gb. but when i go into instal screen of ubuntu and choose option someother else i see only full 320GB HDD full partition. It doesnt show six partition. I created 6th Partition of 25GB to Instal Ubuntu.

In Live CD of Ubuntu using USB Pendrive Device

When i Get into Ubuntu Live (I am posting this thru That only) i see all 6 partitions mounted.

then during instal y itshows only full HDD 320 GB as partition to use for instal?

Kindly help to instal Ubuntu and enjoy the best OS as dual boot option

---

### Post by matrunner on 2013-01-03
plz help

if use dvd boot option by burning image ll it solve prob ?

cant burn 12.10 in cd as size 753mb size

---

### Post by darkod on 2013-01-03
If the disk has been used in fakeraid before, it still has meta data present. In this case the installer ignores it and doesn't show the partitions.

If you are NOT running raid, you can try removing any meta data from that disk with:
sudo dmraid -Er /dev/sdX

Make sure to use the correct disk device instead of /dev/sdX like /dev/sda, /dev/sdb, etc. You have to replace the X with the letter of that disk.

If it asks you to remove meta data, this was the problem. Just confirm and the installer should see the disk fine after that.

Note that you will have to do the manual install (Something Else) to install onto already created partition, because you have created it in advance.

---

### Post by matrunner on 2013-01-03
Hey

Tks for immed reply. I am not so sound in ubuntu commands and misc. As per reply i think the prob can be corrected and instal is poss. 

u told clearing metadata and some. will it affect the drives?

have attached a poto taken when used Live CD and used Ubuntu. As u can see there it shows all partions mounted on left hand corner. I prefer Instal in 25gb partition. Rest all partition have files.

[IMG]http://i46.tinypic.com/10o0i9j.jpg[/IMG]

But instal window in centre just see the HDD as 42gb and 270GB two partition alone. It doesnt show all partition. Kindly help to resolve this. How to proceed exactly.

I am completely new to Ubuntu but v much int in using it.

Just help me out how to exactly proceed how to instal. I ll use Boot from USB which i created as specified in ubuntu site for creating USB Boot.

---

### Post by darkod on 2013-01-03
Something is not right. Do not install yet, until you find what it is.

Boot the usb in live mode like you had already, open terminal and post the output of:
```
sudo parted -l (that's a small L)
```

That should show the partitions list. I suspect you had a gpt disk that you converted to msdos using windows, but in this case windows doesn't delete the backup gpt table and that confuses linux partitioning tools. Lets see if this is correct.

---

### Post by matrunner on 2013-01-03
see the screenshot as requested

I am posting this also from live CD only.

If get immed replies i can get more details as u suggest to find out.

kindly help

---

### Post by matrunner on 2013-01-03
plz reply

---

### Post by oldfred on 2013-01-03
MBR has a 4 primary partition limit. If you created more and parted is not showing it, did you create in Windows and did Windows convert to dynamic rather than an extended partition with logical partitions inside the dynamic. Linux does not work with dynamic partitions as those are proprietary to Windows.

If you look at partitions from Windows does it show dymanic not basic?

Post this, you can just copy & paste text. If long include in code tags or highlight & click # in edit panel.

sudo fdisk -lu

---

### Post by matrunner on 2013-01-03
Hi 

yes the partitions are dynamic. Have posted screenshot from windows 8 disk Mgmt for ur ref

Act partition was created inside windows only.

---

### Post by oldfred on 2013-01-04
According to Microsoft it is a one way conversion. The only way to convert back it to back up all your data and reformat to 4 partitions. All the old free versions of third party tools now seem to charge. You might be able to search some of the software download sites for the older free versions. But you have so many partitions, I am not sure how they convert back. All of the links of users who had redo without loss only had 4 partitions or less.

Dynamic partitions will not work with Linux.

       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

### Post by darkod on 2013-01-04
Just to add to what oldfred said, to be more precise. Not only that Dynamic partitions won't work with linux, Dynamic disks won't work.

That means that even if you delete the 25GB partition you prepared, you will not be able to install ubuntu in its place until you convert the disk to Basic. And I think it will need to have 3 partitions maximum to convert it to Basic, so you will have to delete some of them.
If you don't specifically need so many partitions, don't split it too much. It might sound like a good idea now, but later you can find yourself with free space on one partition when the other partitions are full and you will need to do repartitioning. It all depends how will you use the disk.

On top of everything said so far, I can see that you created 25GB ntfs partition to use with ubuntu. Don't do that. Linux doesn't install on ntfs. It works on its own filesystem. Just leave the 25GB (or as much as you want) as unallocated, unpartitioned space not belonging to any partition, and the ubuntu installer will use it.

---

### Post by matrunner on 2013-01-04
Tks for both of for replying.

Here is the history. This lap had no partition. I made partition thru easeus only. 

Issue ow is i dont get the option to convert the disk to basic from dynamic. I cudnt register in easeus forum to seek help in it.

as u can see in the screenshot now i have attached the HDD itself is shown as dynamic by easeus. 

As per tutorial given by easeus for changing dynamic to basic like right click to get option or DISK menu is not appearing.

@ darkod

i kept it as unallocated space only but then too ubuntu instal didnt detect. So till then i converted back to NTFS to use till i find solution to instal. I cant allocate more than 25gb for ubuntu instal. Now again deleted the partition to keep it as unallocated but linux dont detect it so does windows too


I dont know wat dead end i am struck at. kindly help to resolve this irritating issue..

---

### Post by darkod on 2013-01-04
I haven't used the program to convert to Basic because I never had Dynamic disk.

But you still have 5 partitions and msdos table on the disk. This might be the reason it is not offering the convert option.

msdos disks are limited to 4 primary partitions maximum, or 3 primary + 1 extended. I guess during the conversion process the program is converting all partitions in primary, and it can't do that with 5 of them existing.

Moce your data on some external disk temporarily, and delete 2 more partitions. Your choice which you delete. Leave only 3 partitions on the disk, not 4 or 5.

I say 3 because then when installing ubuntu it will create the extended partition which is allowed. If you already have 4 primary, ubuntu will not be able to install even if there is unallocated space because it can't ceate 5th partition.

My choice would be to delete the partitions from the end, so that all unallocated space is joint together as single large unallocated space. After you install ubuntu on 25GB (use the manual install option to control the partition size), you can create one or more logical ntfs partitions that both ubuntu and windows will be able to use.

If don't know how to use the manual partitioner, no worry, we will think something else. Consult us before trying to install.

The main taks now is to convert the disk to Basic. Leave only 3 partitions on it, and try again with EaseUS.

---

### Post by matrunner on 2013-01-06
hi

i deleted two partition but i dont get option to convert to basic yet.

i have unallocated space of 160gb.

i deleted files and partitions just to use ubuntu.

i cant find a solution now how to instal by converting to basic.

[IMG]http://i48.tinypic.com/xrkpj.jpg[/IMG]

---

### Post by darkod on 2013-01-06
You will have to ask for help in their forum. I have no idea how the software works, just that people have used it to convert to Basic disk. I don't even know where the option should be. In the Advanced menu?

Also, I don't know if it matters that two of your partitions are very very full. They have less than 1GB free. Windows is sometimes problematic with little free space but this usually refers to the system partition, not to data partitions. But since you are trying conversion, who knows if that can affect it. This is just a speculation on my part...

---

### Post by matrunner on 2013-01-06
they dont give support for free versions.

also some prob in forum tat registration gives sql error. tried in al browsers.

which partition need to be basic. this s/w doesnt allow converting unpartition space to basic right? no s/w can do.

if at all have to instal i want to allocate only 25gb for ubuntu. i have to leave rest with windows. my work make me depend on windows.

---

### Post by darkod on 2013-01-06
The space/partitions are not converted in the real meaning of it, the disk type is converted. It's the disk that is either Basic or Dynamic, not the partitions. That's why you can't have one partition basic and another dynamic. They are all basic or all dynamic, depending on the disk.

You can see how it says on the left, Disk 1, Dynamic MBR.

As I said, I haven't worked with the software and I really don't know how it works or why it doesn't offer you the option right now. I am very careful not to convert a disk to dynamic because I know how much hassle it is to get rid of it later. That is MS sh*t.

---

### Post by darkod on 2013-01-06
How are you trying to convert it with EaseUS? I found a tutorial that says you have to click where it says Disk 1, Dynamic MBR and then it will show option on the left side, to convert it. Is this how you tried?

Here are few links if it can help. Look at the first link, option TWO is the one about EaseUS.
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

[http://www.tomshardware.co.uk/forum/246487-14-convert-disk-dynamic-basic](http://www.tomshardware.co.uk/forum/246487-14-convert-disk-dynamic-basic)

---

### Post by matrunner on 2013-01-06
i tried al option. nothing works. it doesnt show any option.

there must be something wrong. Even cleared more files. Allowed 1gb space in each drive. It doesnt work either.

there must be some solution to make ubuntu identify the drives as it very easily mounts them if run live cd.

ha ha try ubuntu only in live cd

---

### Post by darkod on 2013-01-06
Did you see my other post too, with the link from the win7 forums which even has the EaseUS screenshots? That doesn't work too?

There were also other suggestions in that link.

---

### Post by matrunner on 2013-01-06
yes i already had that win 7 forum link. partition wizard doesnt support on free version on convertion.

i tried al option right click all such. nothing working.

---

### Post by darkod on 2013-01-07
Then I don't know what to recommend, sorry. We know what the issue is, and it's not related to ubuntu.

Dynamic disk is specific Microsoft format and linux can't work with it. How you convert the disk to Basic is not related to ubuntu at all. In fact, you might get better help on those windows forums because it's related to windows.

In that link from the sevenforums there were other procedures, some of them include losing the data so you need to make a full backup first, others claim not to lose the data so you can try that too if it looks OK to you. In any case, it's a windows thing.

And in the future, be careful when creating partitions in windows. This might have happened if you tried to create a 5th partition on a disk with msdos table. In that case windows cenverts it to dynamic disk. I don't know whether it gives you a warning or it does it without warning you. If you plan to dual boot having dynamic disk is a very bad idea. So, make sure you never try to make a 5th primary partition in windows on msdos disk.

---

### Post by matrunner on 2013-01-07
hey darkod

i am right here. I am good now. yes i got it working. I can now see all partition. I converted all of my dynamic to Basic. I am ready to instal. see the screenshot.

[IMG]http://i50.tinypic.com/2920fq0.jpg[/IMG]


I have kept 25GB for ubuntu Instal.

Now just take me thru process to use this 25GB for installing ubuntu.

how much to allocate to swap and misc so that it works efficently.

My max dependency is on windows as my work demands. My personal full use i ll with ubuntu. Files i ll keep in windows drives so i can use from it also when use windows 8.

---

### Post by darkod on 2013-01-07
Well, since 25GB is not too much, I would say 2GB for swap and the rest for the / partition.

It's also nice to have separate /home partition but with only 25GB available it's not wise to split the space too much. So, just create 2GB swap and the rest for /. Create the partitions as logical (I don't think it will offer you any choice about this, but in case it does select logical).

Set the / filesystem as ext4. Leave the bootloader destination as /dev/sda.

That should be it.

---

### Post by matrunner on 2013-01-08
i installed ubuntu and i am using it now.

issue is i cant boot into windows 8 which was already in my laptop

boot option shows windows and path.

when i select it shows some error. 

Error: Device format xxxxxxxxxxxx (Some digits)

aft few sec it shows press alt+ctrl+del to restart in next screen. but pressing same doesnt restart. i have to forcibly switch off and on.

now i have to boot into win 8.

plz help immed. in urgent need to boot windows 8

---

### Post by darkod on 2013-01-08
Boot ubuntu and install the boot-repair program. Run it and create the bootinfo summary, post the link it gives you. That will show us more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It looks like you have some strange setup with win8, depending how was it installed. Lets see what is where in the bootinfo.

---

### Post by matrunner on 2013-01-08
Created from Boot Repair

[http://paste.ubuntu.com/1509012/](http://paste.ubuntu.com/1509012/)

Is this useful ?

wat should i do now

---

### Post by darkod on 2013-01-08
I see one win8 boot file that i think should not be there. But don't delete it, just move it in case you need to put it back.

From ubuntu, open the file browser Nautilus and open the win8 partition /dev/sda1 (the size is approx 42GB). In there you should see a file called /Windows/Boot/EFI/bootmgfw.efi. Just follow the path. Move that file to your ubuntu home folder for example.

Reboot and try the win8 entry in the grub menu again. See if that helps.

---

### Post by matrunner on 2013-01-08
dont mistake

how to open nautilus ?

---

### Post by darkod on 2013-01-08
Clicking on the home icon in the Unity interface opens Nautilus. On the left under Devices you will have all other partitions listed. Clicking on one will open it.

---

### Post by matrunner on 2013-01-08
[IMG]http://i46.tinypic.com/2cmq1vo.jpg[/IMG]

no it didnt work.

same error

same issue

see screenshot i am attaching

---

### Post by darkod on 2013-01-08
Try running:
sudo update-grub

but I doubt it will work. You still have traces of the Dyanmic disk (partitions) or the conversion wasn't done successfully. That 'ldm' type points to windows Dynamic disks.
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx)

It seems to me the conversion to Basic is not done fully yet.

---

### Post by matrunner on 2013-01-08
it shows same error though it says found windows 8 loader on /dev/sda1.

error shown in picture is again shown

though grub update identifies boot loader in the drive

error: device format "idm/001xxxxxxxxxxxxxxxxx(as shown in pic)volume1 invalid: must be (f|h)with 0<=n < 128

press any key to continue

---

### Post by matrunner on 2013-01-08
any chance ?

else i wud like to delete ubuntu and go back to win 8

need to use win 8 now cant.

plz give a solution

---

### Post by darkod on 2013-01-08
Try this: In the grub menu press 'c' for command prompt. In the prompt execute one by one:
```
insmod part_msdos
insmod ntfs
set root=(hd0,msdos1)
chainloader +1
boot
```

See if that boots win8.

EDIT: It's not easy to give you solution since this is not ubuntu problem. As i mentioned, the hdd seems to still be dynamic or it has traces of the dynamic disk setup. Maybe windows didn't do the conversion correctly. We have seen that when coverting gpt disk into msdos disk in windows, it doesn't delete the backup gpt table, and later linux can see it and get confused. Windows is doing many things in its own way instead of doing them properly.

I can't be sure if it did the conversion to basic disk correctly.

---

### Post by matrunner on 2013-01-08
wow

amazing

yes once i did all it booted into win 8. it was slow to boot asll such but it booted into win 8.

i shutdown restarted and tried to boot windows 8 by selecting option from grub. it throwed the old error again. goshhhhhhh

ur coding/script worked. when do it it boots into win 8. u r awesome. real dark lord of linux.

is there a permanent solution to boot into ubuntu & win 8 through grub itself

---

### Post by darkod on 2013-01-08
In Ubuntu, you can create your own win8 entry that will work. Open the 40_custom file for editing like this:
gksu gedit /etc/grub.d/40_custom

At the end, add the entry like:
```
menuentry Win8 Custom {
insmod part_msdos
insmod ntfs
set root=(hd0,msdos1)
chainloader +1
}
```

Save and close the file. Run:
sudo update-grub

That should add it to the grub menu. The broken entry will also be there. Reboot and see if your new custom entry works.

---

### Post by matrunner on 2013-01-08
when i type gksu gedit..........
it doesnt show any .

still typed menuentry Win8 Custom { in terminal 
menuentry: command not found error shows

how to do the coding u told

---

### Post by darkod on 2013-01-08
Are you doing this in ubuntu or in the grub prompt? You should boot your ubuntu, open the terminal and do it from there. If you type correctly it has to work. Here it is again:
```
gksu gedit /etc/grub.d/40_custom
```

If it still doesn't work, go to the /etc/grub.d folder and check the content with ls (small LS):
```
cd /etc/grub.d
ls
```

See if the file 40_custom exists.

---

### Post by oldfred on 2013-01-08
I had never heard of LDM, but I guess that is what dynamic partitions are. And like RAID and some others it leaves some hidden data on drive. New grub2 2.00 is now LDM aware, where before it ignored the data.

       GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

    
Darko's suggestion of your own boot stanza (without ldm prefix) is one of the alternatives suggested as work arounds in the bug report.

---

### Post by matrunner on 2013-01-08
@ darkod

it worked like charm. u r really great.

no words to express my heartful gratitude.

patience u shown and way u replied time and time again really thx. u r so knowledged. thank u v v much.

anyway ll have few more queries surely and ll post in forums. bear with me.


@ oldfred.

Seriously i dont know wat u replied. anyway i can boot my windows nad ubuntu with ease.

---

