---
title: "Loading  Ubuntu  sharing disc with  Windows 7 - no option showing"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by frank4360 on 2011-03-24
I have just got a new Compaq/HP netbook with Windows 7, and I have downloaded Ubuntu 10.10 (using my main Ubuntu system) and put it on a USB stick to load it "alongside" Windows.

At install phase on the new machine there is no option shown to add Ubuntu alongside Windows; only two options are shown, to erase the disk entirely and load Ubuntu, or the advanced option to select the disk partitioning manually.

I don't want to do either of these!

What happened to the third option, share the disk between operating systems?

I have used Linux for years, and don't want Windows, but it is safer to be able to boot up Windows for some things (testing ADSL line for Orange France, for instance).

---

### Post by Quackers on 2011-03-24
Have you any unallocated space for Ubuntu to install into? It won't install to a NTFS partition.
Important!!!
How many primary partitions are in use already? 4 is the maximum.

---

### Post by oldfred on 2011-03-24
kansasnoob points out the bug or poor explanation they have on the install screen. Do not use either buttons. It is really best to us manual install and manually create your partitions as then you have total control over sizes and formats.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by frank4360 on 2011-03-24
Thanks to Quackers and oldfred - I will look at your suggestions/remarks.

At present my ADSL connection is running slower than dial-up (a regular problem with Orange here in the wilds of France). As a result it will probably be next week before I can even read the posts you refer to!

---

### Post by frank4360 on 2011-03-26
OK - I have looked at the replies and their references.

There are now specific problems with the HP Compaq netbook on which I want to install Ubuntu alongside Windows 7.

There are already 4 primary partitions on the hard disk - the maximum allowed. I can only create an extended partition by first removing one of the 4. The best candidate for removal seems to be the "HP TOOLS" fat32 partition.

Does anyone know if this will cause a problem with Windows booting?

I will ask the same question in a Win7 forum.

---

### Post by Quackers on 2011-03-26
Others before you have removed that partition without problems. It seems to be used for diagnosing problems. I believe all the programs in that partition can be downloaded from HP, if needed, but they probably won't be.

---

### Post by coffeecat on 2011-03-26
I've never used an HP, but from one thread I was involved in, the HP four primary partitions went something like:

#1 - Windows 7 boot partition - ~ 200MB
#2 - Windows 7 C: partition - huge
#3 - Recovery Partition - ~ 14GB
#4 - HP_TOOLS partition - ~100MB

Which means that if you delete the hp_tools partition, you'll have to shrink the C: partition to make space for an extended partition for logical partitions for Ubuntu. Which means abandoning the 100MB released by the hp_tools partition or moving the recovery partition up (which is not a good idea anyway).

Use the Disk Management utility in Windows 7 to shrink your Windows C: partition. If you use Gparted in the Ubuntu live CD, you risk making Windows unbootable. That's probably easily repaired with a W7 repair disc but best avoided. So, if you haven't done so yet, make a Windows 7 repair disc from within Windows. :)

---

### Post by Hedgehog1 on 2011-03-26
Another option is to burn two sets of the Windows Recovery DVDs (whose data is in the 3rd partition) and then delete the third partition and make it your Ubuntu Extended partition.


When all four primary partitions are taken (the HP install)

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
[SIZE="4"][COLOR="DarkOrange"]Create you sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-03-26
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
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

### Post by frank4360 on 2011-03-26
OK - mostly now done, but with some problems.

First of all, thanks to all the replies - in fact, since I lost my Broadband connection for most of the day, I had not seen them before I managed to load Ubuntu.

I deleted the HP_TOOLS partition (after reading up on it in several forums), and used most of the free space as the 4th primary partition to load Ubuntu.

I was warned in the load process that I hadn't allocated a swp area, so I resized the partition to leave some swap space. As the swap area does not count as a primary partition I did not have to go to Extended partitions.


The load of Ubuntu to the newly created partiton worked well, with only a slight hanging problem when it refused to allow me to specify a French keyboard - it insisted on treating it as Finnish, presumably because of finger trouble, but I had to abort the install and restart.


After installing and checking the Ubuntu and Windows 7 - both looked fine, there have now appeared a few problems.

1. The Windows partitions appear in the Ubuntu File Manager, and I don't see how to stop anyone from fooling around with them. As normally the system will be used for Ubuntu I would like to ensure that the Windows partitions cannot be reformatted - one option in File Manager!

2. The WiFi connection worked perfectly while trying out, and then installing Ubuntu - but as soon as the system was installed it refused to even see the Wireless network! This is still available in Windows. I have edited the Wireless connections in NetworkManager, but nothing works. The settings are exactly the same as for my main Ubuntu system (on which I am writing this post).

3. After several boots of Ubuntu and Windows, to check the installation and remove unnecessary software like Evolution, the startup screen for Ubuntu shows only the BAckground picture! No Application, System, etc - absolutely nothing but the picture! (which is not the default but one of the other supplied themes).

As a result I can now do nothing at all in Ubuntu! - not the desired result of the installation!


Any ideas appreciated.

---

### Post by Hedgehog1 on 2011-03-26
> I was warned in the load process that I hadn't allocated a swp area, so I resized the partition to leave some swap space. As the swap area does not count as a primary partition I did not have to go to Extended partitions.

I am sorry - but this just is not correct.  The swap space needs to be defined as a partition; or you can not use swap (and never use sleep or hibernate).

> 3. After several boots of Ubuntu and Windows, to check the installation and remove unnecessary software like Evolution, the startup screen for Ubuntu shows only the BAckground picture! No Application, System, etc - absolutely nothing but the picture! (which is not the default but one of the other supplied themes).

I don't know if this is a result of deleting too much, or the swap partition confusion (I expect the excessive deleting did it).

How about installing Ubuntu the correct way first (extended partition, ext4 as '/' & swap partition) and see if that goes any better?

***The Hedge***

:KS

---

### Post by oldfred on 2011-03-26
Someone posted before that evolution was tied to the entire desktop. 

So when you uninstalled evolution you uninstalled the desktop. It should have shown in the dependencies what it was uninstalling and it was a long list. I did something similar once and uninstalled the entire desktop. Then I had to chroot and just about reinstall everything from there, but I had a lot of settings & data I wanted back.

Do you have it connected with a Ethernet cable for the install. It needs that to download the additional drivers for wireless in many cases.

---

### Post by coffeecat on 2011-03-26
> **frank4360 said:**
> 
1. The Windows partitions appear in the Ubuntu File Manager, and I don't see how to stop anyone from fooling around with them. As normally the system will be used for Ubuntu I would like to ensure that the Windows partitions cannot be reformatted - one option in File Manager!

:?

If by "File manager" you mean Nautilus, the Ubuntu equivalent of Windows Explorer, no you can't reformat a partition from Nautilus. You can mount it to access it, but you can't format it. You can (re)format a partition in Disk Utility (or in Gparted if you install it) but only with the administrator password.

---

### Post by frank4360 on 2011-03-26
> **oldfred said:**
> Someone posted before that evolution was tied to the entire desktop. 

So when you uninstalled evolution you uninstalled the desktop. It should have shown in the dependencies what it was uninstalling and it was a long list. I did something similar once and uninstalled the entire desktop. Then I had to chroot and just about reinstall everything from there, but I had a lot of settings & data I wanted back.

Looks like that is what has happened.

Is there any way short of re-installing that I can get the Desktop back? Or get to a command line that I can use to re-install Evolution (which I don't actually want, but someone in Canonical has decided I must have!)?

---

### Post by Quackers on 2011-03-26
I did the same thing.
[http://ubuntuforums.org/showthread.php?t=1559996](http://ubuntuforums.org/showthread.php?t=1559996)
I ended up re-installing :-(

You could try pressing ctrl+Alt+F1 and go to a command line then try ```
sudo apt-get install evolution-data-server ubuntu-desktop
```
as those are two of the main packages that others depend on, as I understand it.
Other people here may know a lot more about it than I do though!

---

### Post by coffeecat on 2011-03-26
> **frank4360 said:**
> Is there any way short of re-installing that I can get the Desktop back?

Can't guarantee this but it's worth a try.

Can you connect with an ethernet cable? If so, choose recovery mode from the grub menu, and when you get the second menu, choose "drop to root shell with networking", or words to that effect. 

When you get the # prompt, run:

```
apt-get update
```... to make sure your metadata are up-to-date. You don't need sudo - you have root powers. Now:

```
apt-get install ubuntu-desktop
```The package ubuntu-desktop is a meta-package which has as dependencies everything that goes to make the Ubuntu desktop. So, anything taken out when you uninstalled evolution *should* be restored.

---

### Post by frank4360 on 2011-03-26
> **Quackers said:**
> 
You could try pressing ctrl+Alt+F1 and go to a command line then try ```
sudo apt-get install evolution-data-server ubuntu-desktop
```
as those are two of the main packages that others depend on, as I understand it.

This worked perfectly!! Thanks a million.

I have now recovered the Desktop.

I wonder why Ubuntu is so wedded to Evolution, which may be very good. Personally I prefer Thunderbird, which is available also in Windows.

Thanks again, Quackers

---

### Post by frank4360 on 2011-03-26
Thanks, coffeecat - I tried Quackers solution first and it got me out of my hole!

---

### Post by Quackers on 2011-03-26
Glad to hear that it worked. I wasn't convinced it would :-)
I had the same question. It seems an odd thing to marry so much to.
You're welcome.
Please mark the thread as solved using the Thread Tools near the top of the page.

---

### Post by frank4360 on 2011-03-26
> **Hedgehog1 said:**
> I am sorry - but this just is not correct.  The swap space needs to be defined as a partition; or you can not use swap (and never use sleep or hibernate).


I have checked the Ubuntu "sleep" and "hibernate" offered during the shutdown, and they seem to work.

I need to doublecheck exactly how I set up the partitions to see if I made a mistake in what I posted.

Thanks

---

### Post by frank4360 on 2011-03-27
Thanks to all.

I have now resolved the Netbook Wireless Problem.

Broadcom drivers are proprietary, so not in Ubuntu by default.

However, I noticed there is a tab for Additional Drivers: System>>Administration>>Additional Drivers

And it was as simple as that - the drivers for my Broadcom BCM4313 were offered, and I installed with no problem at all.

So now all seems to be working well -until the next problem!!

---

