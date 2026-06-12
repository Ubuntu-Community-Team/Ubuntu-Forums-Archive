---
title: "Using Recovery Partition to recover Windows"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by apche93 on 2008-07-17
Hi,

I accidentally deleted my Vista partition in Gparted!  But i still have my recovery partition.  Is there anyway that i could copy the files of the vista operating system onto a ntfs partition so that i could boot from it?


AFter copying the files i could edit the grub menu to boot from that ntfs partition.


Would this work??

And what files would i need to copy?

Add'l info:

I have a sony vaio VGN-NR110E.  Does anyone know what files i could copy?

When i try to go to Recovery mode, it says that it cant find my C: drive most likely cuz i deleted it.

I have an XP cd.  When i try to go to recovery in the cd, it says that it cant find any hds!

any help would greatly be appreciated!

---

### Post by logos34 on 2008-07-17
You want to try TestDisk -- recover a lost ntfs partition.

sudo apt-get install testdisk

sudo testdisk

Read the documentation:
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)
[http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS](http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS)

If after recovery you still can't access all your files, try PhotoRec (from cgsecurity also)

---

### Post by apche93 on 2008-07-17
hi,

I went to that site and did what it said.

here are my problems:
[LIST]
[*]My Recovery partition doesnt work anymore as it says that it could not be loaded
[*]Therefore, Vista still doesnt seem to work
[*]Below, you can see my biggest problem (Gparted shows that i wiped my hd clean)
[/LIST]

[IMG]http://i260.photobucket.com/albums/ii30/apche93/screenshot1-1.png[/IMG]

Here is are my partitions according to terminal:
```
$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62abe731

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         852     6843658+   7  HPFS/NTFS
/dev/sda2             853        4767    31447237+   7  HPFS/NTFS
/dev/sda3            4768       13382    69199987+   7  HPFS/NTFS
/dev/sda4           13383       14594     9735390    f  W95 Ext'd (LBA)
/dev/sda5           13383       13578     1574338+  82  Linux swap / Solaris
/dev/sda6           13579       14593     8152956   83  Linux

```


Thats basically how it was before i ran Testdisk.  Now, it looks the same but why is Gparted doing that?????


Also, what is wrong with my recovery partition?  Why isnt it booting up?



Plus, my after deleting my Vista partition i created a brand NEW partition out of it!

---

### Post by logos34 on 2008-07-17
There's still something wrong with the partition table.  Gparted won't detect it until you fix it.  Go back and read the guides/step-by-step docs, then run testdisk again.  

> 
 Plus, my after deleting my Vista partition i created a brand NEW partition out of it!

Which one?
> /dev/sda2             853        4767    31447237+   7  HPFS/NTFS
/dev/sda3            4768       13382    69199987+   7  HPFS/NTFS

---

### Post by apche93 on 2008-07-18
i think it is /dev/sda2.

Why? Do you have any suggestions?

----------------------------------------------------------------------------------------------------------------------
My recovery partition still does not work!

I am sure i followed the instructions correctly on that website.  But my partitions arent lost, i have new ones in the place of them.  SO, i dont know how much of a help the testdisk did.

---

### Post by apche93 on 2008-07-18
I have done everything that the website requires.  Everystep has been done!  Gparted still does not work... Is there a way that i can restore my settings to how it was before i installed Testdisk?

Id rather have a working Ubuntu, over than trying to install windows!

---

### Post by logos34 on 2008-07-18
> **apche93 said:**
> My recovery partition still does not work!...But my partitions arent lost, i have new ones in the place of them.  SO, i dont know how much of a help the testdisk did.

What do you mean '"aren't lost'"?  You reformatted (ntfs) over Vista, and there are two partitions there, but Vista with all the files is buried underneath somewhere, and that's what you're trying to retrieve, right?.  It doesn't always find the lost partition on the first try--you have to "dig deeper".  Find the level where the vista C:\, the recovery partition and the others are correctly listed, with no overlapping sectors.  Then set the appropriate label for the partition type (*, P, L).  If green (ok), write changes to disk.  

Gparted is probably going to continue to say 'unallocated' until you fix the partition table.

---

### Post by apche93 on 2008-07-19
ok, after running a deep scan, this is what i get:

The first picture shows that i couldnt recover a particular drive:

[IMG]http://i260.photobucket.com/albums/ii30/apche93/screenshot2.png[/IMG]

Now, this second picture shows all the ones i can recovery.  Do you know which ones i would have to do???

[IMG]http://i260.photobucket.com/albums/ii30/apche93/screenshot3.png[/IMG]


Could you please tell me the ones that seem like my vista files?

This is the copy/paste code for further advice:

```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1   851 254 51   13687305 [Recovery]
D HPFS - NTFS            852   0  1  4297 254 63   55359990
D HPFS - NTFS            852   0  1  4766 254 63   62894475 [Main]
D Linux                 1047   1  1  2066 254 58   16386232
D Linux                 1048   2  1  2068   0 58   16386232
D HPFS - NTFS           2067   0  1  5982 254 63   62910540 [Main]
D Linux Swap            4135   2  1  4297 254 42    2618448
D Linux                 4298   0  1  6121 254 63   29302560
D Linux                 4298   2  1  5269 254 57   15615048
D HPFS - NTFS           4298  15  6 14592 223 31  165386240 [Chinni]
D HPFS - NTFS           4767   0  1 13381 254 63  138399975 [Chinni]
D HPFS - NTFS           5983   0  1 14592 254 63  138319650 [Chinni]
D Linux Swap           13382   1  1 13577 254 42    3148656
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 7007 MB / 6683 MiB
```

---

### Post by logos34 on 2008-07-19
> **apche93 said:**
> ok, after running a deep scan, this is what i get:

The first picture shows that i couldnt recover a particular drive:

That's your root!  Why is it saying that? Before you do anything further try testdisk from the ubuntu live cd:

>system>admin>software sources>enable **universe** repositories

sudo apt-get install testdisk

sudo testdisk

(maximize terminal window first)

If you can't scan down deeper so that root is included in the recoverable partitions, then I guess root sda6 can't be recovered after all.

> Now, this second picture shows all the ones i can recovery.  Do you know which ones i would have to do???

Could you please tell me the ones that seem like my vista files?Well, going by your earlier post:

> **apche93 said:**
> 
Here is are my partitions according to terminal:
```
$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62abe731

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           **1         852**     6843658+   7  HPFS/NTFS
/dev/sda2             **853        4767 **   31447237+   7  HPFS/NTFS
/dev/sda3            **4768       13382**    69199987+   7  HPFS/NTFS
/dev/sda4           13383       14594     9735390    f  W95 Ext'd (LBA)
/dev/sda5           **13383       13578**     1574338+  82  Linux swap / Solaris
/dev/sda6           13579       14593     8152956   83  Linux

```Thats basically how it was **[COLOR=Red]before[/COLOR]** i ran Testdisk.  Now, it looks the same but why is Gparted doing that?????


I'd mark the following partitions:

```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors[B][COLOR=Black]
[/COLOR][/B][COLOR=Black]*[/COLOR]** [COLOR=SeaGreen]HPFS - NTFS              0   1  1   851 254 51   13687305 [Recovery][/COLOR]**
D HPFS - NTFS            852   0  1  4297 254 63   55359990
**[COLOR=Black]P[/COLOR] [COLOR=SeaGreen]HPFS - NTFS            852   0  1  4766 254 63   62894475 [Main][/COLOR]**
D Linux                 1047   1  1  2066 254 58   16386232
D Linux                 1048   2  1  2068   0 58   16386232
D HPFS - NTFS           2067   0  1  5982 254 63   62910540 [Main]
D Linux Swap            4135   2  1  4297 254 42    2618448
D Linux                 4298   0  1  6121 254 63   29302560
D Linux                 4298   2  1  5269 254 57   15615048
D HPFS - NTFS           4298  15  6 14592 223 31  165386240 [Chinni]
**[COLOR=Black]P[/COLOR] [COLOR=SeaGreen]HPFS - NTFS           4767   0  1 13381 254 63  138399975 [Chinni][/COLOR]**
D HPFS - NTFS           5983   0  1 14592 254 63  138319650 [Chinni]
**[COLOR=Black]L[/COLOR] [COLOR=SeaGreen]Linux Swap           13382   1  1 13577 254 42    3148656[/COLOR]**
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 7007 MB / 6683 MiB
```

But then ubuntu will be unbootable!  

Unless to want to just recover vista and then reinstall ubuntu.  If so, then obviuosly back up any personal stuff on sda6 before you write any changes in testdisk.

---

### Post by coffeecat on 2008-07-19
**apche93**, I think you're going about this the wrong way. The recovery partition on my Sony Vaio (different model) has compressed files that will restore a system to its factory setting if the C: drive is corrupted. You will lose all your apps and settings, but you will get Windows back. You are in danger of making a bad situation worse by using Linux tools to read and copy stuff that is meant to be used in a completely different way.

Read the manuals that came with your machine to see how to initiate the recovery procedure - it may be different with different models. Also - with my Sony, there was a way of doing a system backup to DVDs when I first started Windows (or as often as I wanted). This is a Sony utility, not a Windows one. Did you do that? And if the worst comes to the worst, you should be able to buy restore discs for your particular model of machine from Sony, but this probably won't be cheap.

---

### Post by lisati on 2008-07-19
On my desktop (by Compaq) the recovery partition for XP shows up on the Grub list of OSes to choose from, & I've found running it from there works more reliably than the original F10 that I would have used had I kept the machine Windows-only.

---

### Post by logos34 on 2008-07-19
> **coffeecat said:**
> **apche93**, I think you're going about this the wrong way. The recovery partition on my Sony Vaio (different model) has compressed files that will restore a system to its factory setting if the C: drive is corrupted. You will lose all your apps and settings, but you will get Windows back. You are in danger of making a bad situation worse by using Linux tools to read and copy stuff that is meant to be used in a completely different way.

He said: 

[quote]  > **apche93 said:**
> When i try to go to Recovery mode, it says that it cant find my C: drive most likely cuz i deleted it.

...

My Recovery partition doesnt work anymore as it says that it could not be loaded.  
Therefore, Vista still doesnt seem to work...

And I believe he has saved files on the vista partition he also wants to recover

---

### Post by apche93 on 2008-07-19
> **logos34 said:**
> 
And I believe he has saved files on the vista partition he also wants to recover

Well, what do you mean by i saved files on the vista partition?


I formatted my vista os partition to /dev/sda2.  Wouldnt this mean that my files on my vista os partition would have been deleted?


But, i did copy all the files in my recovery partition to an external hd.

[QUOTE=coffeecat]**apche93**, I think you're going about this the wrong way. The recovery partition on my Sony Vaio (different model) has compressed files that will restore a system to its factory setting if the C: drive is corrupted. You will lose all your apps and settings, but you will get Windows back. You are in danger of making a bad situation worse by using Linux tools to read and copy stuff that is meant to be used in a completely different way.[/QUOTE]

Yes, trust me.  My first instinct as soon as my vista died was to go into recovery partition.  But i HAD to reformat vista b/c of some error that it was giving (GRUB would not install).  And, when i booted the recovery partition it couldnt find C:.  

Now, it doesnt seem like the recovery partition is even loading!


----------------------------------------------------------------

But logos34, thankyou for all your help, i will try booting from a livecd, and restoring those partitions.  

Hopefully, my next post will be about how i successfully recovered vista!

---

### Post by logos34 on 2008-07-19
> **apche93 said:**
> Well, what do you mean by i saved files on the vista partition?

I formatted my vista os partition to /dev/sda2.  Wouldnt this mean that my files on my vista os partition would have been deleted?

No, if the restoration is successful, most of your files should be there (although some may not be readable...The procedure isn't perfect).  So cross your fingers.

>  But logos34, thankyou for all your help, i will try booting from a livecd, and restoring those partitions.  

Hopefully, my next post will be about how i successfully recovered vista!
Yep, let's hope.

---

### Post by apche93 on 2008-07-19
Well, i did it and........ it didnt work!


I think this is b/c u told me to recover the exact same ones that ive tried before (without doing the deep search).


Is there any other combination that i could try?

*********

And it said that one of the Linux partitions could not be recovered either in Live Disc.

---

### Post by logos34 on 2008-07-19
> **apche93 said:**
> Well, i did it and........ it didnt work! I think this is b/c u told me to recover the exact same ones that ive tried before (without doing the deep search).


I hope that's not a reproach...I thought that was about as far as you could go (you said you did a "deep scan")...See my posts # 7 and 9.

Comparing fdisk and testdisk output, it is safe to say the recovery and swap partitions are correct.  That leave the root and the vista ntfs partitions.  Now, let me clear something up: these ntfs partitions:

> /dev/sda2             **853        4767**    31447237+   7  HPFS/NTFS
/dev/sda3            **4768       13382**    69199987+   7  HPFS/NTFS

Were they this way originally, with vista on sda2, or was vista on one big partition from 853-13382, at which point you accidentally deleted vista and 'created a brand new partition' out of it?  Because if there was just one partition in that space, try to dig down deeper.  Maybe doing so will find your linux root (in a recoverable state this time), although I'm not terribly optimistic:

>  And it said that one of the Linux partitions could not be recovered either in Live Disc.

I have no idea why there's a problem with sda6.

---

### Post by apche93 on 2008-07-19
First of, Let me apologize for any wrong intention that i may have had.  I am just so frustrated with so many things going wrong!!

But i am thankful that you can help me.

---------------------------------

Now to business-

This is what happened.

When i installed ubuntu for the first time, my huge vista partition (the entire disk [besides recovery partition]) was divided up by the installation partitioner b/c i had no idea it selected a guided disk.

So, then i had:

/dev/sda1       Recovery
/dev/sda2       Vista
/dev/sda3       Swap
/dev/sda4       Extended
/dev/sda5       Chinni (the extra space for common files)
/dev/sda6       Ubuntu
----------------------------------

After getting frustrated with ubuntu, i restored MBR thru CMD in Vista by using some application i found online.

I then deleted Ubuntu and Swap using Disk Management in Windows.

My disk then basically looked like this:

/dev/sda1       Recovery
/dev/sda2       Vista
/dev/sda4       Extended
/dev/sda5       Chinni (the extra space for common files)
-----------------------------------

Then, after getting a virus in Vista (not for the reasons u may be thinking :lolflag: ), i decided that Vista was a complete waste cuz of the numerous antivirus apps that were constantly bloated.

This is when i decided to reinstall the Ubuntu i have today.

I HAD to erase Vista cuz that application i used to restore MBR probably put some sort of block on changing my boot manager.

So, in live cd, i deleted all remaining partitions but Recovery.  Then, out of the new unallocated space, i created what i have today:


/dev/sda1       Recovery
/dev/sda2       Main (No Vista)
/dev/sda3       Chinni (the extra space for common files)
/dev/sda4       Extended
/dev/sda5       Swap
/dev/sda6       Ubuntu

I hope that will help u a little!  Thats the entire history of my computer. Lolz :).

---

### Post by logos34 on 2008-07-19
Ok, that clears things up.  I understand now (I think).

So what you need to do is scan deeper and restore to the last known state with vista:

>  /dev/sda1       Recovery
/dev/sda2       Vista
/dev/sda4       Extended
/dev/sda5       Chinni (the extra space for common files)

Maybe that will finally get the recovery partition and vista working (the vista boot files will be on sda1).  But I think that's about all you can ask for...getting ubuntu root back is out of the question I think because the extended partition boundary was changed.  You made a lot of changes on the rest of the disk, and I don't see how you can recover them.

---

### Post by apche93 on 2008-07-19
> **logos34 said:**
> Ok, that clears things up.  I understand now (I think).

Glad to know my long history made some sense!

> 
Maybe that will finally get the recovery partition and vista working (the vista boot files will be on sda1).  But I think that's about all you can ask for...getting ubuntu root back is out of the question I think because the extended partition boundary was changed.  You made a lot of changes on the rest of the disk, and I don't see how you can recover them.

Its okay, If that fixes vista, im happy, and even if it doesnt im happy too.  I would delete everything but my recovery partition, and keep just linux for now :).

I dont know how much i can do, but ill do as much as i can in testdisk.

Btw, if Gparted still does not work in the end, what do u suggest i do?

---

### Post by logos34 on 2008-07-20
ok, good luck.  

> **apche93 said:**
> Btw, if Gparted still does not work in the end, what do u suggest i do?

I'm not sure...I've experienced the same thing with Gparted I don't how many times, and testDisk has always managed to straighten out my partition table.  Maybe someone else has a suggestion.

Maybe when you reinstall ubuntu it will overwrite the existing table so that gparted can read it

---

### Post by apche93 on 2008-07-20
Is there a way of getting my current themes, customizations, files in ubuntu back in a fresh install?

(Like backup and restore kind of system)

B/c i want to wipe my hd clean, and permanently keep ubuntu!

---

### Post by apche93 on 2008-07-20
Okay everybody,

I just ended up wiping my hd and installing a fresh ubuntu, which basically fixed all my problems (took out Windows).

---

