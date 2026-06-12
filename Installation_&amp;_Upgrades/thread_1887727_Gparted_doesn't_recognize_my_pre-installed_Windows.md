---
title: "Gparted doesn't recognize my pre-installed Windows7"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Niddhoeggr on 2011-11-27
Hi!
I've already found a couple of threads regarding this problem, however there seems to be no solution :/

I'm trying to create a W7/Ubuntu 11.10 Dual boot. I've installed W7 first and now that I want to create another partition for Ubuntu with Gparted from my Ubuntu USB stick it only shows my whole disk as 160GB of unallocated space.

When I type sudo fdisk -l into the terminal, the partitions are recognized. (see attachment)

I've never really used Ubuntu before, so please help me! :)

edit: The problem was a damaged partition table which can easily be repaired/recreated with a ubuntu live cd and Gparted :)

---

### Post by Paddy Landau on 2011-11-27
Please enter the following command in the terminal (you can copy-and-paste), and post the results here.
```
sudo parted --list
```

---

### Post by Niddhoeggr on 2011-11-27
First of all, thanks for the fast reply!

Unfortunately I can't paste it because Ubuntu doesn't recognize my wireless card (I put a dell wireless card in my NC10 to use it as a hackintosh).

I don't really know what the error means, but it seems related to my dual boot problem, right?

---

### Post by fantab on 2011-11-27
> **Niddhoeggr said:**
> First of all, thanks for the fast reply!

Unfortunately I can't paste it because Ubuntu doesn't recognize my wireless card (I put a dell wireless card in my NC10 to use it as a hackintosh).

I don't really know what the error means, but it seems related to my dual boot problem, right?

Your HDD is using GPT TABLE. I think you will have to Use DOS Partition Table in order to Dual-boot. But before that tell us more about your computer:

Laptop/Desktop- vendor - model?
HDD- Size- vendor model?
Does you computer use PC BIOS or EFI (Extensible Firmware Interface)?

Meanwhile read these, if you haven't already

[http://ubuntuforums.org/showthread.php?t=1826661](http://ubuntuforums.org/showthread.php?t=1826661)

[http://ubuntuforums.org/showthread.php?t=1561689](http://ubuntuforums.org/showthread.php?t=1561689)
see oldfred's post.

---

### Post by mastablasta on 2011-11-28
use the Windows 7 disk managemnet to create an empty space on your disk. this will become your ubuntu parittion. mkae sure you defragment the disk first and run checkdisk a couple of times.
 
then during install you may need to manually choose the partition you want to install Ubuntu to (sicne windows7 is recognised as unnocupied space).
 
you could also give parted magic distribution a try (for disk partitioning): [http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)
 
as it uses latest gparted.
 
To me as well ubuntu (gparted) failed to recognise NTFS partition changed over from FAT32. it was unknown file system.

---

### Post by coffeecat on 2011-11-28
> **Niddhoeggr said:**
> I've installed W7 first and now that I want to create another partition for Ubuntu with Gparted from my Ubuntu USB stick it only shows my whole disk as 160GB of unallocated space.

Gparted showing unallocated space in a drive that has usable partitions means that you have a corrupted partition table or a partition table with an illegal entry. And indeed your second screenshot of the parted output shows that parted is having difficulty making sense of the partition table. It would be unwise to attempt to create more partitions until this is fixed. Also - Windows will not boot from a GUID partition table on a BIOS machine, only from one with EFI, hence fantab's question.

Are you able to boot Windows from that drive?

**EDIT**: by the way, please do not post terminal outputs as screenshots. It is impossible for people trying to help to highlight and repost relevant parts, which can be useful. When posting terminal output, highlight the relevant output with the mouse, right-click and "copy" and then paste into your post by pasting it between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the pasted output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by Niddhoeggr on 2011-11-28
> **fantab said:**
> Your HDD is using GPT TABLE. I think you will  have to Use DOS Partition Table in order to Dual-boot. But before that  tell us more about your computer:
 
 Laptop/Desktop- vendor - model?
 HDD- Size- vendor model?
 Does you computer use PC BIOS or EFI (Extensible Firmware Interface)?
 
 Meanwhile read these, if you haven't already
 
 [http://ubuntuforums.org/showthread.php?t=1826661](http://ubuntuforums.org/showthread.php?t=1826661)
 
 [http://ubuntuforums.org/showthread.php?t=1561689](http://ubuntuforums.org/showthread.php?t=1561689)
 see oldfred's post.
 
 Thanks I'll have a look at these threads!
 
 My netbook is a Samsung NC10 (**[FONT=Arial][SIZE=1]NC10-anyNet N270 BBT[/SIZE][/FONT]**) with a 160GB Sata drive and bios.
 
 Could this be a bios related problem? I've downgraded my bios to make snow leopard work, maybe Ubuntu needs a newer bios?


> **coffeecat said:**
> 
Are you able to boot Windows from that drive?

Yep, windows boots fine. 
Before installation I tried to create the partitions with gparted like  in this guide:  [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Windows however wouldn't even install on a drive formatted by gparted  (ntfs). After this I deleted the partitions I created with Gparted and  re-created them with the w7 installation disk. 

 > **coffeecat said:**
> 
**EDIT**: by the way, please do not post terminal outputs as screenshots. 
Sorry, I know its a hassle (for me as well) but I have a custom wireless  card which isn't supported out of the box, so I've got no wifi on my  netbook.

> **mastablasta said:**
> use the Windows 7 disk managemnet to create an empty space on your disk. this will become your ubuntu parittion. mkae sure you defragment the disk first and run checkdisk a couple of times.
That's what I used in my first try with my pre-installed windows7, no luck :/
 
 > **mastablasta said:**
> 
you could also give parted magic distribution a try (for disk partitioning): [http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)
as it uses latest gparted.
 To me as well ubuntu (gparted) failed to recognise NTFS partition changed over from FAT32. it was unknown file system.
I'll give it a try, thanks!

Thanks for all the help, I really appreciate it.. i hope we can get this to work :)

---

### Post by mastablasta on 2011-11-28
> **Niddhoeggr said:**
> That's what I used in my first try with my pre-installed windows7, no luck :/
 
 
use chkdsk command:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
 
and don't forget to defrag first. It should work. and linux should recognise new partition. if not create a FAT32 partition and then select it and install to it manually.

---

### Post by Niddhoeggr on 2011-11-28
> **mastablasta said:**
> use chkdsk command:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
 
and don't forget to defrag first. It should work. and linux should recognise new partition. if not create a FAT32 partition and then select it and install to it manually.

Defraged the disk and run chkdsk 3 times, 2x with /x option 1x with /f but gparted still shows the disk as unallocated space :/

I don't mind starting over and wiping the entire disk, but if I do it with gparted windows can't install and if I do it with Windows gparted doesn't recognize my partitions. :(

If the partition table is broken, how can I fix it?

thanks!

---

### Post by coffeecat on 2011-11-28
> **Niddhoeggr said:**
> 
I don't mind starting over and wiping the entire disk, but if I do it with gparted windows can't install and if I do it with Windows gparted doesn't recognize my partitions. :(

To be honest, starting over is probably best. To repeat - **you have a bad partition table**. I don't understand exactly what is wrong, but with a faulty partition table, all the chkdsk-ing and defragging in the world is not going to fix that.

Also, with an undamaged partition table you can install Windows to a NTFS partition created with Gparted - I've done this successfully with XP, Vista and Windows 7. And a partition created by Windows will be detectable by Gparted. All your problems can probably be explained by an illegality or inconsistency in the partition table. 

But you haven't answered one question: BIOS or EFI? With BIOS, you must have a mbr partition table for Windows, not GUID. Use Gparted to create a new one.

---

### Post by Niddhoeggr on 2011-11-28
> **coffeecat said:**
> To be honest, starting over is probably best. To repeat - **you have a bad partition table**. I don't understand exactly what is wrong, but with a faulty partition table, all the chkdsk-ing and defragging in the world is not going to fix that.

Also, with an undamaged partition table you can install Windows to a NTFS partition created with Gparted - I've done this successfully with XP, Vista and Windows 7. And a partition created by Windows will be detectable by Gparted. All your problems can probably be explained by an illegality or inconsistency in the partition table. 

But you haven't answered one question: BIOS or EFI? With BIOS, you must have a mbr partition table for Windows, not GUID. Use Gparted to create a new one.

Sorry, I don't even know what EFI is. :?
If I press F2 while booting I get into bios (NC10 was originally shipped with windows xp installed). I hope thats what you mean?

So I'll boot Ubuntu from my USB stick, wipe my harddisk with Gparted and create 1 ntfs partition for windows, 1 unformatted partition for ubuntu and 1 ntfs partition for storage, is this about right? I'll search for an option to create a new partition table, though I don't really know how that works. I hope that's about right? :)


Again, thanks for the help, really appreciate it!

---

### Post by fantab on 2011-11-28
> **coffeecat said:**
> To be honest, starting over is probably best. To repeat - **you have a bad partition table**. I don't understand exactly what is wrong, but with a faulty partition table, all the chkdsk-ing and defragging in the world is not going to fix that.

Also, with an undamaged partition table you can install Windows to a NTFS partition created with Gparted - I've done this successfully with XP, Vista and Windows 7. And a partition created by Windows will be detectable by Gparted. All your problems can probably be explained by an illegality or inconsistency in the partition table. 

But you haven't answered one question: BIOS or EFI? With BIOS, you must have a mbr partition table for Windows, not GUID. Use Gparted to create a new one.

+1.



Start over and use [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") to manage your HDD from boot. I personally use DOS Partition Table and it works great with Windows and Linux.

Also NEVER downgrade BIOS versions... you may have hardware errors later. It is ok if you don't update buy don't downgrade. Now coming to this, **how exactly did you downgrade your BIOS?**

---

### Post by darkod on 2011-11-28
Just to say that it looks like this custom BIOS is to blame.
I have a Samsung NC10 and the original bios definitely doesn't have EFI option, and the disk doesn't come with GPT. Why would it for 160GB.

However, I have no idea what the custom BIOS did.

---

### Post by Niddhoeggr on 2011-11-28
I used WinPhlash for downgrading. Without downgrading I couldn't activate AHCI which restricted me from installing Leopard, worked fine in the end though :)

I'm currently installing W7 onto a partition which I created with W7 from unallocated space created by gparted (is this even understandable? :P).
This didn't work before, so I'm pretty happy :) Seems like creating a new Partition table with Gparted was the solution..I'll keep you posted!

Thanks again for all the help, especially coffeecat!
If the installation works out fine, I'll be sure to bug you guys with many other stupid questions ;)

---

### Post by coffeecat on 2011-11-28
If you have a BIOS, then you don't have EFI and if Windows is booting OK then that can't be a GUID partition table whatever parted is telling us.

> **Niddhoeggr said:**
> So I'll boot Ubuntu from my USB stick, wipe my harddisk with Gparted 

You need to be even more radical than that. In Gparted, Device menu -> create partition table. Choose msdos/mbr which is the default. The partition table needs to be completely remade.

**EDIT**: I didn't notice your last post, and it seems as though you already have re-created the partition table. If you still have any problems, post back and we can look at zeroing out the partition table before re-creating it.

---

### Post by Niddhoeggr on 2011-11-28
> **darkod said:**
> Just to say that it looks like this custom BIOS is to blame.
I have a Samsung NC10 and the original bios definitely doesn't have EFI option, and the disk doesn't come with GPT. Why would it for 160GB.

However, I have no idea what the custom BIOS did.

It's not really custom, just an older version (05a) :) I think the GPT partition table was a result of a former Snow Leopard installation I did on the NC10.

Unfortunately I got an "APT Configuration Error" during installation which I'm trying to figure out right now. I'm currently burning the Ubuntu ISO onto a CD instead of a USB stick, I'll report back!

---

### Post by oldfred on 2011-11-28
It looks like you are booting from MBR, but the Windows installer only deletes the primary gpt partition table and does not delete the backup. Some software still sees the backup and gets confused on whether it is gpt or MBR(msdos).

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Niddhoeggr on 2011-11-29
After burning Ubuntu onto a cd the setup worked :) Unfortunately I'm encountering a bug so that I can't shut down.. after clicking shutdown Ubuntu only logs me out.
After some googling it seems that this bug is known but hasn't been fixed, so I guess I'll have to wait :/

Thanks again for all the help! :)

---

