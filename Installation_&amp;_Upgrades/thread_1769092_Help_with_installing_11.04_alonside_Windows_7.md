---
title: "Help with installing 11.04 alonside Windows 7"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by rich52x on 2011-05-27
Hey guys, just got a new laptop with Windows 7 Home Premium 64bit pre-installed, and when I boot into my 11.04 CD, there is no simple option to install alongside windows 7. Only the options to erase the entire disk (wiping windows) or manually specifying partitions.
I'd like to keep my windows install as I use it for gaming, but I don't want to mess around with partitions while I don't know what I'm doing. According to the 'Allocate disk space' part of the installation, all 4 primary partitions are being used, a main one for the Windows 7 install, one entitled HP tools, and another two I forget the names of. I have looked up that I may need to turn a primary partition into an extended one, which I have no idea how to do. So, any help guys?
P.S. I'd rather not install via Wubi because I'd appreciate the hibernate and suspend functions that apparently don't work fully inside wubi.

thanks in advance
rich

---

### Post by Quackers on 2011-05-27
If 4 primary partitions are already in use you will need to delete one before another operating system can be installed.
Others in your position have deleted the HP TOOLS partition then shrunk their C: drive in Windows Disk Management window (after defragmenting the C: drive).
Once that's done the "install alongside" option will be available in the Ubuntu installer.

---

### Post by rich52x on 2011-05-27
Is there anything of importance in the HP TOOLS partition? Or is it safe to get rid of?

---

### Post by rich52x on 2011-05-27
in GParted, the 4 primary partitions are there and then a 5th partition named 'unallocated' with size '1 MiB'.
So could i keep my hp tools partition, shrink the size of my 450GB C:/ partition and install ubuntu on the new unallocated space? (ideally around 50GB)

---

### Post by Hedgehog1 on 2011-05-27
The 'unallocated' space is not a partition.

You are only allowed 4 primary partitions, and HP is using them all to reduce the cost of sending OS disks.

I generally suggest making a set of recovery DVDs from Windows, and then deleting the 'HP_RECOVERY' partition instead.

I have a guide with pictures I can post if you want to see it.

***The Hedge***

:KS

---

### Post by rich52x on 2011-05-27
heres what my partitions look like (see pic)

And if you could post aforementioned guide I'd be forever grateful :D
rich

---

### Post by dadaj on 2011-05-27
rich52x, you may refer to following link. 
 
[http://ubuntuforums.org/showpost.php?p=10755147&postcount=24](http://ubuntuforums.org/showpost.php?p=10755147&postcount=24)

Or. 

[http://jeffond756.xanga.com/746995183/dual-boot-windows-7-and-ubuntu/](http://jeffond756.xanga.com/746995183/dual-boot-windows-7-and-ubuntu/)

---

### Post by sweBers on 2011-05-27
They're right about the 4 partition limit.  [This link]("http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360") from HP's support forum says how you might be able to delete both the recovery and tools partitions.  That will give you enough for a root partition and either swap space or a separate home partition.

---

### Post by rich52x on 2011-05-27
> **sweBers said:**
> They're right about the 4 partition limit.  [This link]("http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360") from HP's support forum says how you might be able to delete both the recovery and tools partitions.  That will give you enough for a root partition and either swap space or a separate home partition.


Would you recommend a separate home partition or swap space?

---

### Post by Hedgehog1 on 2011-05-27
The limit if four PRIMARY partitions, not 4 partitions.

These instruction show you how to create and extended partition, into which you can create many more 'logical' partitions.

So your total partition count can exceed 4.

[SIZE="3"]When all four primary partitions are taken (the HP install)[/SIZE]

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-05-27
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]

[SIZE="4"][COLOR="DarkOrange"]
Once your partitions are laid out, you will start the install and eventually get to the **Disk Space Allocation** screen.  

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.[/COLOR][/SIZE]

[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-27
You can create 3 logical partitions instead of 2:

1) ext4 '/'
2) Linux swap
3) ext4 '/home'

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]

You just need to make room for them.

***The Hedge***

:KS

[IMG]http://img694.imageshack.us/img694/2095/bartsimpsonchalkboard.png[/IMG]

---

### Post by rich52x on 2011-05-27
You know where you say to delete sda3, the HP_RESTORE partition, could I not keep that partition and delete the HP_TOOLS partition instead? 
Also, thankyou very much for the guide, probably the most detailed one I've ever been presented with :')

---

### Post by Hedgehog1 on 2011-05-27
You can certainly delete the HP_TOOLS partiton instead.  Your extended partition will be /dev/sda4 instead of /dev/sda3 - and beyond that there is no real difference.

Whichever you prefer is fine!


***The Hedge***

:KS

---

### Post by rich52x on 2011-05-28
So my HP_TOOLS partition is only 100MB, if i delete that, could i somehow take some space from my 450GB Windows partition (/dev/sda2) for the 3 logical partitons?

---

### Post by rich52x on 2011-05-29
?

---

### Post by Quackers on 2011-05-29
Yes, you can shrink the C: drive using the Windows Disk Management screen. It is strongly advised that you defragment the C: drive first, twice is better.
Then you can create the extended partition within that new unallocated space.

---

### Post by Markmental on 2011-05-29
> **rich52x said:**
> Is there anything of importance in the HP TOOLS partition? Or is it safe to get rid of?
Hp tools may be for system recovery I recommend you install 10.04 LTS, it is more stable and will be supported longer. Plus It has an option for dual booting right off the bat on install.

---

### Post by rich52x on 2011-05-29
Alright, defragging the C: drive now

thanks

---

### Post by Quackers on 2011-05-29
No problem. Have fun :-)

---

### Post by rich52x on 2011-05-29
> **Markmental said:**
> Hp tools may be for system recovery I recommend you install 10.04 LTS, it is more stable and will be supported longer. Plus It has an option for dual booting right off the bat on install.
There's another partition actually named RECOVERY (D:)
So I'll be keeping that and getting rid of the HP TOOLS partition I think. Still gonna have a quick read up on it though, so thanks

Also, I've just defragged the C: drive twice, pretty quickly tbf

---

### Post by rich52x on 2011-05-29
Also, if hp tools were to be a relatively useful/important partition, could i not back up its contents somehow and then somehow reinstate it as a logical partiton in the same way as Hedgehog1 described to make partitions for the ubuntu install

I ask this because I can view the contents of HP TOOLS from the Ubuntu live cd.

Its contents include a folder named Hewlett-Packard, containing the folders; BIOS, BIOSUpdate and SystemDiags.
There is also a folder within the partition named $RECYCLE.BIN, and a file named HP.WSD.dat

---

### Post by rich52x on 2011-05-31
thanks for all the help guys, but i decided to take the easy/lazy route

i did a wubi install :P

---

### Post by rich52x on 2011-06-05
Update:

I was dissatisfied with wubi, it had some major slowdowns that drove me back to windows, even after uninstalling and wubi'ing 10.10
i followed the steps from hedge's guide
and by jove i have a nice fresh 11.04 install

i am forever indebted m'duck
thanks a lot :D

---

### Post by Quackers on 2011-06-05
Glad to hear that. Well persevered! :-)

---

### Post by rich52x on 2011-06-05
thanks :D

the feeling of accomplishment in me is running high

---

### Post by Quackers on 2011-06-05
That's what it's all about :-)

---

### Post by rich52x on 2011-06-05
thread OFFICIALLY solved!! :D

---

