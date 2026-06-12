---
title: "Cannot Install: Free space marked as &quot;Unusable&quot;"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by Harry084 on 2011-05-22
Hi, I'm pretty new to Ubuntu, and am hoping for a relatively easy to follow response. Anyway, I'm trying to dual boot my HP laptop which comes with Windows 7 already installed. I got as far as allocating drive space in the ubuntu installation process. Once i dropped the size of my windows partition by 45 gigs, the space i'd created is listed as unusable. At the top it is color coded white for free space, however in the list of drives it is listed as "unusable" and when I try to install it says that it won't work. I've heard that there can only be so many primary partitions on an HDD and that HP has already claimed all of them with the factory install. If anyone can make a suggestion that would be great. When I click on the Unusable space i cant change it or anything, the only option is to "revert" which doesn't seem to do anything. I really really want to dual boot, so if anyone could help that would be amazing. Sorry to ask what I'm sure is such a basic question. Thanks in advance!

---

### Post by Hedgehog1 on 2011-05-22
Greetings!

Yes indeed, we are only allow 4 primary partitions on a drive that windows can understand.

Also, HP (and other manufacturers) are shipping system with all four primary partitions already taken.

Normally I suggest you make a 2 full sets of system restore DVDs and and Windows Rescue CD, store these somewhere safe, and then recycle the 'HP_RESTORE' partition as your extended partition for Ubuntu.

It means turning this:

[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]

Into this:

[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG] 

I can give you a more detailed post if you would like.

***The Hedge***


:KS

---

### Post by Harry084 on 2011-05-24
First of all, thanks so much for replying so quickly, that seriously just made my day. Anyway if you would be able to post a more detailed guide that would be great. I made a set of recovery cds, although it says I can only make 1 set. Now i just need to work out how to delete the recovery partition. Also, i noticed in your picture that there is an extended partition. How do those work, and what are the sub-divisions? I see one is swap space, and the other is EXT4, is that where Ubuntu is installed?

---

### Post by Hedgehog1 on 2011-05-25
Here is the guide - use this as a 'jumping off' point:


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

### Post by Hedgehog1 on 2011-05-25
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

### Post by Harry084 on 2011-05-27
Thanks so much. How much space would you recommend for an Ubuntu partition? Also, if i want to add more space from my main ntfs partition should i shrink it in windows or using something like Gparted?

---

### Post by Hedgehog1 on 2011-05-28
Whenever possible, use Windows tools to change Windows partitions, and Linux tools to change Linux partitions.

If you are forced to shrink a Windows partition using gparted, please defrag that partition 3 times from Windows first.

As to size, 20 gigs is enough to play and do useful things.

One of two things will happen - you will love Ubuntu and will Shrink Windows and grow Ubuntu partitions; or you will find Ubuntu doesn't fit your needs right now and uninstall it.

***The Hedge***

:KS

---

### Post by srs5694 on 2011-05-28
> **Hedgehog1 said:**
> Whenever possible, use Windows tools to change Windows partitions, and Linux tools to change Linux partitions.

I'm not sure I agree with that. The standard Windows partitioning tools, at least in the last version or two of Windows, have the infuriating tendency to turn normal partitions into Windows Logical Disk Manager (LDM) volumes, aka "dynamic disks." This seems to happen automatically and with little or no warning when you exceed four partitions. There are quite a few threads on this forum from users who've been bitten by this "feature." The trouble is that Linux can't manipulate LDM volumes, and it's difficult (maybe impossible; I've not looked into it in detail) to install Linux in an LDM. Thus, if you experience such a conversion, you've got to reverse it, which can be difficult.

Thus, my own recommendation is to use the Windows tools *only* to shrink a Windows boot partition, if that's necessary, but for no other purpose. Most importantly, *never* create a new partition with the tool -- even an NTFS partition! If you misread the partition table or if there's some oddity about the disk (a partition that the utility doesn't show you, for instance, although I don't recall hearing of such a thing), you could end up converting to LDM, which will then be a hassle to fix.

---

### Post by Hedgehog1 on 2011-05-28
> **srs5694 said:**
> I'm not sure I agree with that. The standard Windows partitioning tools, at least in the last version or two of Windows, have the infuriating tendency to turn normal partitions into Windows Logical Disk Manager (LDM) volumes, aka "dynamic disks." This seems to happen automatically and with little or no warning when you exceed four partitions. ...

Excellent point **srs5694**!  The new (and unadvertised) change in behavior in Windows Disk Manager does indeed cause issues if you try to exceed 4 partitions.

Has it been your observation that it is also turning normal partitions into LDM volumes when Windows Disk Manager is used for shrinking/expanding NTFS partitions that already exists?

***The Hedge***

:KS

---

### Post by srs5694 on 2011-05-28
> **Hedgehog1 said:**
> Has it been your observation that it is also turning normal partitions into LDM volumes when Windows Disk Manager is used for shrinking/expanding NTFS partitions that already exists?

I have yet to study the issue myself on my own systems, so my impressions are based on problem reports I've seen on the Internet (mostly here, in fact). Based on that, exceeding the 4-partition limit is definitely an issue, but I can't recall any reports that say other actions have *definitely* caused problems. Some reports have been vague or incomplete, though, and may have been caused by other actions.

---

### Post by Harry084 on 2011-05-30
Does it matter if i delete the recovery partition using Gparted, or is the windows utility better? One of my friends tried to shrink a windows partition in ubuntu, and every time he tried to boot into windows 7 some sort of disk check utility ran. Is this something that will likely happen?

---

### Post by Harry084 on 2011-05-30
also, is it possible once i install ubuntu in the extended partition to shrink my windows partition and add it to my ubuntu install? if so does it require me to completely reinstall ubuntu?

---

### Post by Expert Novice on 2012-01-08
Hey, what a great guide. I ve been struggling with similar touble installing 11.10 and this really helped. Thanks for taking the time to post such a clear set of instructions. There were some differences in that I didn't have the GParted option on my CD but I seem to have figured things out.

I now have working 11.10/Win7 dual boot install. The only strange thing now is I don't see Windows 7 as an option for which O/S to boot to. I see a purple Ubuntu screen with various start up options. There are two entries for Windows Recovery and if I select one of those it starts the full version of Windiws 7 and all seems well.

---

