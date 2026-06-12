---
title: "installing dual boot with vista"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by dc_jt on 2007-09-22
Hi

I have tried the following link (also in tutorial section) but cant get it to work:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first#comment-23214](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first#comment-23214)

I have followed what it says regarding shrinking the c drive. I have 500gb drive by the way.

This seems to work and I end up with c drive having 330gb and then 160g "not allocated", which seems right.

However when I go to install Ubuntu, the option "Manual - use the largest continuous free space" doesnt appear.

Instead it just says guided - use entire disk. Then it has two options sda and sdb both saying 250gb each. 

Why arent I geting the option to use the largest continous space??

Someone please help.

Thanks in advance

---

### Post by logos34 on 2007-09-22
Does gparted see the unallocated space?

system>admin>gnome partition manager

---

### Post by dc_jt on 2007-09-22
how do i check this on vista?

---

### Post by Pumalite on 2007-09-22
Get Gpated:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and you'll know.

---

### Post by logos34 on 2007-09-22
> **dc_jt said:**
> how do i check this on vista?

from the ubuntu live cd is what I meant.

---

### Post by dc_jt on 2007-09-22
Firstly, im not sure about hy har ddrive. On my tower it says 2 x 250gb but when I go to my c drive it says 460gb. 

When I go to manage->disk management it says I have got 2 volumes. One isnt named and uses up 5gb (think this is something to do with the system restore being an advent computer) and the other is the c drive which says 323.14gb. Then it says 137.41 gb unallocated so I presume I have done this bit right.

I booted up the linux live cd and when i went to system->admin->gnome partition editor it has two option in the top right. One says /dev/sda (232.58 GiB) and the other says /dev/sdb (232.58 GiB)

When I click on each it says partition - unallocated 
 file system - unallocated
size 232.58 GiB

Does this help?

Thanks

---

### Post by dc_jt on 2007-09-22
Anyone??

Is it because my hard drive is 500gb but its 2 x 250gb? 

I have done the partition etc correct so why wont it recognise that I have?

Pleas help?

---

### Post by dc_jt on 2007-09-22
BY the way when I go to install ubuntu, instead of saying :

"Manual - use the largest continuous free space"

It says:

Guided - use entire disk
 - SCSI1 - (0,0,0) (sda) - 250.1 GB ATA ...(etc)
 - SCSI2 - (0,0,0) (sdb) - 250.1 GB ATA ...(etc)

Manual

HOpe this is enough information to help me?

Thanks

---

### Post by Pumalite on 2007-09-22
Since it seems that logos34 has logged off, I'll try to help
First post specs: make model, memory, graphics, etc.

---

### Post by dc_jt on 2007-09-22
Thanks

This is my computer

[http://www.pcworld.co.uk/martprd/product/seo/216880](http://www.pcworld.co.uk/martprd/product/seo/216880)

It says 500gb hard drive but on my tower it says 500gb (2 x 250gb, 7200 rpm)


HOpe you can help. THanks a lot

---

### Post by dc_jt on 2007-09-22
BY the way I have updated and now got 4gb of RAM

---

### Post by logos34 on 2007-09-22
What version of vista are you running? (home basic, premium, ultimate?)  If ultimate, it sounds like it's configured for dynamic disks

---

### Post by dc_jt on 2007-09-22
Im running home premium

---

### Post by dc_jt on 2007-09-22
:( Anyone?

---

### Post by Pumalite on 2007-09-22
Make sure you use Vista's partitioner. Then install>Manual: give 10 GB to '/', 500 MB to /swap, the rest to /home.

---

### Post by dc_jt on 2007-09-22
Sorry if i am being thick, where do you mean when you say "use vista partitioner"? Is this a program or do you mean select this at a certain screen or what?

Thanks

---

### Post by Pumalite on 2007-09-22
You Vista has a partitioner. Must be in Administration or something (sorry, not a Vista user). Use it to partition your drive.

---

### Post by logos34 on 2007-09-22
I believe it's Control panel>admin tools>computer management>disk management 

wonder why it's showing C: so big unless it's spanning the two drives

---

### Post by dc_jt on 2007-09-22
SO when you say use vista partitioner do you mean to shrink the volume of c? If so, I have done that already and set c to 400gb and left 60gb unallocated.

NOw should I install ubuntu and go to manual and do what you said? (BUt should i do 60 insteead of 10?)

---

### Post by Pumalite on 2007-09-22
Yes, install Ubuntu in your 60 GB.

---

### Post by dc_jt on 2007-09-22
Thats the problem, I  cant! When im installing ubuntu, the option to "Manual - use the largest continuous free space" is not there, instead it just says 

Guided - use entire disk
- SCSI1 - (0,0,0) (sda) - 250.1 GB ATA ...(etc)
- SCSI2 - (0,0,0) (sdb) - 250.1 GB ATA ...(etc)

Manual

If I go to manual, it then has the two options sda and sdb??

---

### Post by Pumalite on 2007-09-22
Try it.

---

### Post by dc_jt on 2007-09-22
Try what? Please explain? (Sorry)

Go to manual or click on one of the two options?

If I go to manual which option should I click on? And then do what?

I dont want to lost my Vista so want to be sure.

Thanks for you help by the way :)

---

### Post by Pumalite on 2007-09-22
You have to click Manual and then do the partitioning as I told you.

---

### Post by dc_jt on 2007-09-22
OK so I go to manual and I have two options /dev/sda and /dev/sdb

Should I click on 'New partition table'? And if so, what option should i click on first sda or sdb?

Thanks again

---

### Post by Pumalite on 2007-09-22
sdb

---

### Post by dc_jt on 2007-09-22
by the way i clicked on sda just to try and it comes up a sub option saying free space 250059 mb. If i click that *and then go to 'New partition' *then it comes up:

type - primary or logical
new partition size - set to 250059 as default
location - beginning or end
use as - ext3 set as default
mount point - nothing in drop down

If this is correct can you tell me which ones to choose for each?

** if i dont click New partition table and go to next it says 'No root file system'. PLease correct this from the partitioning menu.

Thanks

**edited

---

### Post by krimz on 2007-09-22
Looks to me that your system is running a fakeraid which means you'll need to install dmraid for the live-cd even to be able to see your setup correctly.

btw: If you tell the ubuntu installer to just install on sda, chances are you're going to hose your vista installation...

---

### Post by Pumalite on 2007-09-22
Thats funny because your Vista is in sda. I wouldn't touch it if you want your Vista still alive at the end of the process.

---

### Post by dc_jt on 2007-09-22
THanks krimz, however what is a fakeraid. And what do I need to do? IS it complicated or easily done?

---

### Post by krimz on 2007-09-22
[fakeraid howto]("https://help.ubuntu.com/community/FakeRaidHowto")

read it and weep :)

---

### Post by Pumalite on 2007-09-22
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Pumalite on 2007-09-22
You were right logos; C looked 'too big'

---

### Post by dc_jt on 2007-09-22
I really cant see me being able to follow that how to, is this the only alternative? :(

---

### Post by krimz on 2007-09-22
Here are the [cliff notes]("http://ubuntuforums.org/showthread.php?t=464758") to that fakeraid-howto above. The guy that wrote them seems to not be absolutely sure what he's doing though (parts of step 5 seem redundant to my mind e.g.)

---

### Post by dc_jt on 2007-09-22
I have just followed the very first bit of that how to and now i have got the option to use the largest free space...etc.

However if i click that and go to next, it says no operating system to import from then if i click next enter my username an password etc i get this screen:

 Language: English
 Keyboard layout: United Kingdom
 Name: David
 Login name: david
 Location: Europe/London
 Migration Assistant:



If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 LVM VG isw_bccfbbfccc_RAID_Volume0, LV isw_bccfbbfccc_RAID_Volume0

The following partitions are going to be formatted:
 LVM VG isw_bccfbbfccc_RAID_Volume0, LV isw_bccfbbfccc_RAID_Volume0 as ext3
 LVM VG isw_bccfbbfccc_RAID_Volume0, LV isw_bccfbbfccc_RAID_Volume0 as swap

SHouldnt it say Vista/Longhorn underneath Migration Assistant????

---

### Post by krimz on 2007-09-22
My advice to you is to really sit down and read everything about fakeraid so that you thouroughly understand what you're doing and really plan your installation (number and size of partitions etc..) Don't just jump right into it without fully understanding what you're doing because that will probably cause trouble for you later (Of course, if you don't mind installing Vista from scratch again, then by all means go right ahead - trial and error is a great way of learning new stuff :) )

---

