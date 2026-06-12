---
title: "Backing up with Clonezila before and after installing Ubuntu?"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2014-03-29
Hi
 
I have my clean UEFI windows 8.1 install on my HDD now just as i want
it, drivers, Intel rapid Storage and Start Technology and Expresscache
configured for the 24GB SSD, essential programs etc, the install is
25GB on a 50GB sda5.

 
I initially created sda1 30gb to backup to because I thought
Clonezilla would be able to back up a larger partition to a smaller
partition once the space used was less than the size of the backup
partition - this I now understand is only possible if I shrink the
partition but Disk Management will only allow me shrink it to ~35gb
and GParted will not let me shrink it at all.

 
I have used the default Clonezilla settings to backup the windows
partition to 2gb image blocks first on 50GB sda6 next to the sda5
(Windows) and now on sda7 75GB at the end of the drive. Should I
backup again selecting the other three windows 8.1 partitions created
during install, recovery, mbr, etc?

 
Are the default settings enough to complete replicate my install to an
otherwise blank disk?

 
Once backed up, if I delete the sda1-sda6 partitions how do I
completely recover Windows 8.1 (including the other partitions it
creates at install) from my Clonezilla backup to sda1-sda4, and would
doing so affect Windows 8.1 in anyway, considering it was initially
installed on sda5 - should I instead wipe the drive, install windows
8.1 again (where it should be) and then backup?

 
I plan to install Ubuntu, Debian, Kali, and Clonezilla partitions but
I need to just get Windows 8.1 installed where it should be and backed
up first so I never have to do it again. For partition for the future
installs, could /home backups for Ubuntu and Debian fit side by side
on the extra space on the 75GB partition I am backing Windows 8.1 up
to?

 
Thanks

---

### Post by sudodus on 2014-03-30
Hi, I'm using Clonezilla, and can try to help you.

> **dusf said:**
> Hi
 
I have my clean UEFI windows 8.1 install on my HDD now just as i want
it, drivers, Intel rapid Storage and Start Technology and Expresscache
configured for the 24GB SSD, essential programs etc, the install is
25GB on a 50GB sda5.

 
I initially created sda1 30gb to backup to because I thought
Clonezilla would be able to back up a larger partition to a smaller
partition once the space used was less than the size of the backup
partition - this I now understand is only possible if I shrink the
partition but Disk Management will only allow me shrink it to ~35gb
and GParted will not let me shrink it at all.

You are right, clonezilla can clone (or restore from a compressed image) to a drive or partition of the same size or larger.

Gparted cannot shrink a partition that is mounted, and you cannot unmount a partition that is used, for example the root partition of a running linux system. On the other hand, it is *not* a good idea to shrink a file system, so that there is hardly any free space left.

Gparted has problems to manage partitions of Windows, and in particular, you should not try to do anything with the Windows system partition, if the system is hibernated and not shut down completely. (It is difficult to shut down Windows 8 completely.)

"You linux tools to manage linux file systems and Windows tools to manage Windows file systems!"
> 
 
I have used the default Clonezilla settings to backup the windows
partition to 2gb image blocks first on 50GB sda6 next to the sda5
(Windows) and now on sda7 75GB at the end of the drive. Should I
backup again selecting the other three windows 8.1 partitions created
during install, recovery, mbr, etc?

 
Are the default settings enough to complete replicate my install to an
otherwise blank disk?

Do I understand correctly?

You want to create a backup (or image) with Clonezilla, that can be used to make a complete working copy (clone).

The easiest way to do this is to ***make an image of the whole drive*** (not of partitions, the whole drive for example /dev/sda). From this image you can restore or clone the complete system to a drive of the same size or larger.
> 
 
Once backed up, if I delete the sda1-sda6 partitions how do I
completely recover Windows 8.1 (including the other partitions it
creates at install) from my Clonezilla backup to sda1-sda4, and would
doing so affect Windows 8.1 in anyway, considering it was initially
installed on sda5 - should I instead wipe the drive, install windows
8.1 again (where it should be) and then backup?

To give detailed help about the partitions, it is important to 'see' them, so please run the following command and post the output

```
sudo parted -l
```

and please describe again the content of each partition
 > 
I plan to install Ubuntu, Debian, Kali, and Clonezilla partitions but
I need to just get Windows 8.1 installed where it should be and backed
up first so I never have to do it again. For partition for the future
installs, could /home backups for Ubuntu and Debian fit side by side
on the extra space on the 75GB partition I am backing Windows 8.1 up
to?

 
Thanks

I suggest that you keep a complete backup image of the whole drive, and to have peace of mind, test that it really works by restoring/cloning it to a 'third drive'.

After that you can do different things with the original drive and if something would be broken, you know that you can restore the original system. Then later, when you have done a considerable amount of work successfully, you can make a 'restore point' by making a new image of the complete drive with Clonezilla. Of course it requires a big external HDD to store several images. So I suggest that you get such a drive if you haven't got one already.

- Backing up to a separate drive is better than to a partition on the same drive.
- Backing up to an external drive is better than to an internal drive.
- Storing a backup in another house is better than storing it in the same house as the computer ...

---

### Post by Mark Phelps on 2014-03-30
> I have my clean UEFI windows 8.1 instal

You would do better using Macrium Reflect to backup/restore MS Windows setups.  Their free version offers all the functions you would need to do this.

---

### Post by Dáire Fagan on 2014-04-02
> **sudodus said:**
> Hi, I'm using Clonezilla, and can try to help you.

Thanks for the reply

> **sudodus said:**
> You are right, clonezilla can clone (or restore  from a compressed image) to a drive or partition of the same size or  larger.

I have read there is some logical reason why it cannot do this, yet, but  it would be really great if it could do this when the destination  backup partition/disk is larger than the *used* space on the partition/disk to be backed up, especially considering the backup was compressed by clonezilla to just 16GB.

> **sudodus said:**
> Gparted cannot shrink a partition that is  mounted, and you cannot unmount a partition that is used, for example  the root partition of a running linux system. On the other hand, it is *not* a good idea to shrink a file system, so that there is hardly any free space left.

Gparted has problems to manage partitions of Windows, and in particular,  you should not try to do anything with the Windows system partition, if  the system is hibernated and not shut down completely. (It is difficult  to shut down Windows 8 completely.)

"You linux tools to manage linux file systems and Windows tools to manage Windows file systems!"

This all makes sense, but I initially tried using Windows Disk Management  to resize the Windows partition but it would only reduce it to around  35GB. I would rather avoid changing the size of the Windows partition at  all if possible, and I think it is.

> **sudodus said:**
> Do I understand correctly?

You want to create a backup (or image) with Clonezilla, that can be used to make a complete working copy (clone).

The easiest way to do this is to ***make an image of the whole drive***  (not of partitions, the whole drive for example /dev/sda). From this  image you can restore or clone the complete system to a drive of the  same size or larger.

To be clear, what I want to do is backup my UEFI Windows 8.1 partition  that I can use to restore it on a disk that will also have several linux  root and home partitions and a media data partition (accessible by all  OS so probably NTFS). I want to be able to restore *just* Windows  8.1, without affecting the other partitons or the partition table and  boot loader etc. For this reason it would seem to me making a complete  image of the drive would not be the way to go because it would also restore  all the Linux partitons (once they are installed).

If I am correct please advise if there are any options in Clonezilla  expert mode for partition to partition backup I need to select, and also  that I only need to backup the Windows partition rather than the  Windows partiton and the 3 other partitions UEFI installs create, boot,  recovery, and something else?

I tried restoring the backup I made to the drive after I formatted it  and installed Windows 8 (without drivers, my software, upgrading to  Windows 8.1 etc) by changing sda2 to sda1 and sda3 to sda3 in the backup  and then trying to let my Windows install media repair it but it did  not work.

I am now on day 2 of a completely fresh install, Windows 8 has been  upgraded to 8.1 and I have run disk cleanup to remove the old Windows 8  install but I still have to install drivers and software etc. When this  is all done I should be able to backup Windows 8.1 in such a way that I  can restore it to the drive as is, and also later even when other OS are  installed? This is why I think I should leave out the other three  Windows partitions that were created during install.

> **sudodus said:**
> To give detailed help about the partitions, it  is important to 'see' them, so please run the following command and post  the output

```
sudo parted -l
```

and please describe again the content of each partition

I redirected the output of sudo parted -l to a file and moved it around  but I was never able to access it off the USB key to copy and paste here  - so please see the attached picture. The first three small partitions  are the ones Windows creates during UEFI Windows 8.1 install, MBR,  recovery, and something else essential. The fourth partition is the  actual Windows install partition. The fifth small partition is new to  me, but since I just upgraded from Windows 8 to 8.1, and my 100GB  Windows partition is that much smaller it must have to do with the  upgrade and I hope once all updates are install Windows will merge this  into the main partition.
 
[IMG]http://i.imgur.com/9mZ9mGA.jpg?1[/IMG]

> **sudodus said:**
> I suggest that you keep a complete backup image  of the whole drive, and to have peace of mind, test that it really works  by restoring/cloning it to a 'third drive'. 

I have  ordered a 128GB USB flash drive to store backups on but it will take  awhile to reach me and if I can avoid buying another 500GB USB drive to  backup what Clonezilla will output to 16GB I would like to.

> **sudodus said:**
> After that you can do different things with the  original drive and if something would be broken, you know that you can  restore the original system. Then later, when you have done a  considerable amount of work successfully, you can make a 'restore point'  by making a new image of the complete drive with Clonezilla. Of course  it requires a big external HDD to store several images. So I suggest  that you get such a drive if you haven't got one already.

- Backing up to a separate drive is better than to a partition on the same drive.
- Backing up to an external drive is better than to an internal drive.
- Storing a backup in another house is better than storing it in the same house as the computer ...

I  appreciate the value of all of that, but for now I just want to get  Windows 8.1 backed up to something restorable so I can finally get  around to working with Ubuntu on my laptop.

> **Mark Phelps said:**
> You would do better using Macrium Reflect to backup/restore MS Windows setups.  Their free version offers all the functions you would need to do this.

Thanks, but I believe it can be done using Clonezilla and I would like to stick with that if possible.

---

### Post by sudodus on 2014-04-02
> **dusf said:**
> Thanks for the reply



I have read there is some logical reason why it cannot do this, yet, but  it would be really great if it could do this when the destination  backup partition/disk is larger than the *used* space on the partition/disk to be backed up, especially considering the backup was compressed by clonezilla to just 16GB.

You can use other kinds of backup: tar, fsarchiver, rsync, but then the backup will not be an exact clone of the original system. Windows 8 and UEFI makes things complicated, and there is a considerable risk that it is not enough to backup the Windows partition. You need the head of the drive and the EFI partition too, and you get all those things if you make a compressed image of the complete disk with Clonezilla.
> 

This all makes sense, but I initially tried using Windows Disk Management  to resize the Windows partition but it would only reduce it to around  35GB. I would rather avoid changing the size of the Windows partition at  all if possible, and I think it is.



To be clear, what I want to do is backup my UEFI Windows 8.1 partition  that I can use to restore it on a disk that will also have several linux  root and home partitions and a media data partition (accessible by all  OS so probably NTFS). I want to be able to restore *just* Windows  8.1, without affecting the other partitons or the partition table and  boot loader etc. For this reason it would seem to me making a complete  image of the drive would not be the way to go because it would also restore  all the Linux partitons (once they are installed).

If I am correct please advise if there are any options in Clonezilla  expert mode for partition to partition backup I need to select, and also  that I only need to backup the Windows partition rather than the  Windows partiton and the 3 other partitions UEFI installs create, boot,  recovery, and something else?

It is possible even in beginner mode to backup 'only' a partition or some partitions. But there is a higher risk that you will fail to make a working drive from such a backup compared to an image of the whole drive.
> 
I tried restoring the backup I made to the drive after I formatted it  and installed Windows 8 (without drivers, my software, upgrading to  Windows 8.1 etc) by changing sda2 to sda1 and sda3 to sda3 in the backup  and then trying to let my Windows install media repair it but it did  not work.

I am now on day 2 of a completely fresh install, Windows 8 has been  upgraded to 8.1 and I have run disk cleanup to remove the old Windows 8  install but I still have to install drivers and software etc. When this  is all done I should be able to backup Windows 8.1 in such a way that I  can restore it to the drive as is, and also later even when other OS are  installed? This is why I think I should leave out the other three  Windows partitions that were created during install.

You can try, but you are making things more complicated than necessary.
> 

I redirected the output of sudo parted -l to a file and moved it around  but I was never able to access it off the USB key to copy and paste here  - so please see the attached picture. The first three small partitions  are the ones Windows creates during UEFI Windows 8.1 install, MBR,  recovery, and something else essential. The fourth partition is the  actual Windows install partition. The fifth small partition is new to  me, but since I just upgraded from Windows 8 to 8.1, and my 100GB  Windows partition is that much smaller it must have to do with the  upgrade and I hope once all updates are install Windows will merge this  into the main partition.
 
[IMG]http://i.imgur.com/9mZ9mGA.jpg?1[/IMG]

The other partitions are so small, that they contribute very little to the total size of the backup - the compressed image file.
 > 

I have  ordered a 128GB USB flash drive to store backups on but it will take  awhile to reach me and if I can avoid buying another 500GB USB drive to  backup what Clonezilla will output to 16GB I would like to.



I  appreciate the value of all of that, but for now I just want to get  Windows 8.1 backed up to something restorable so I can finally get  around to working with Ubuntu on my laptop.

---

### Post by Dáire Fagan on 2014-04-02
Will making a backup of the whole drive mean if I restore it my Linux partitions are overwritten? Also, I have a 500GB HDD available and I can clear 105GB from it, but can I make this complete backup to the 500GB USB without losing the other data already on it?

---

### Post by sudodus on 2014-04-02
Yes, if you restore from an image of the drive, the target drive will be like the original one. So you need at least two backups.

- Backup the original drive with Windows, so that you don't lose it, if you get problems during the installation of a dual boot system with Ubuntu alongside Windows.

- Backup the new system, the dual boot drive with Ubuntu and Windows. Also here I recommend a full backup, a compressed image of the whole drive.

- A compressed Clonezilla image is a directory with several files, and it does not destroy anything on the drive, where it is written. The only condition is that there must be enough free space to write it. Otherwise it will not be complete (and probably useless).

---

### Post by Dáire Fagan on 2014-04-02
Surely restoring a whole disk backup image of Windows and Ubuntu will restore not just Windows, but also Ubuntu, which I do not want?

I want to be able to just restore Windows and the Windows partitions back to how things were when everything was working with all the OS installed - but I want to leave the OS other than Windows untouched.

---

### Post by sudodus on 2014-04-02
> **dusf said:**
> Surely restoring a whole disk backup image of Windows and Ubuntu will restore not just Windows, but also Ubuntu, which I do not want?

This is correct

---

### Post by sudodus on 2014-04-02
> **dusf said:**
> I want to be able to just restore Windows and the Windows partitions back to how things were when everything was working with all the OS installed - but I want to leave the OS other than Windows untouched.

Yes I see.

Once you have the new system (with Windows and linux) I assume you want that system backed up (with Windows and linux).

When you have such a backup, it is possible the make a copy of that backup and leave out any partitions you don't want to restore and restore from that copy. Then you would restore only the partitions you want, but still have everything there including the bootloader and partition table, EFI partition etc.

---

### Post by Dáire Fagan on 2014-04-02
> **sudodus said:**
> Yes I see.

Once you have the new system (with Windows and linux) I assume you want that system backed up (with Windows and linux).

When you have such a backup, it is possible the make a copy of that backup and leave out any partitions you don't want to restore and restore from that copy. Then you would restore only the partitions you want, but still have everything there including the bootloader and partition table, EFI partition etc.

Okay, that sounds more like what I am talking about, the only problem is that to do this I will need a USB device larger than all the Windows partitions 101GB combined, and then about 20GB for Ubuntu, 20GB for Debian, and 10GB for Kali - this means I need to buy at minimum another 500GB HDD.

Are you sure this cannot be achieved without that expense by using partition to partition backup selecting ALL of the Windows partitions and anything related to the partition table and EFI etc but not selecting the Linux partitions? It would be a lot cheaper for me...

---

### Post by sudodus on 2014-04-03
No I am not sure. This is the way I would do it, but there are so many possibilities with linux, some of which I don't know. Let us hope someone who knows will chip in and explain how do it without buying more hardware.

One way to get such help is to get ***Boot-Repair*** according to this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and (at least in the beginning not do any repair,) only create a ***BootInfo*** summary, and write a post about it in the following Ubuntu Forums thread
[URL="http://ubuntuforums.org/showthread.php?t=1769482"]
[Boot-Repair] Graphical tool to repair the PC boot in one click[/URL]

---

### Post by mastablasta on 2014-04-03
> **dusf said:**
> Okay, that sounds more like what I am talking about, the only problem is that to do this I will need a USB device larger than all the Windows partitions 101GB combined, and then about 20GB for Ubuntu, 20GB for Debian, and 10GB for Kali - this means I need to buy at minimum another 500GB HDD.



the device you are backing up to needs to be big enough for the image. but the device where you restore data to need to be of same size or larger.

example -  i had a 500 GB disk, before i did dualboot i backed up the disk. the image took about 40 or 50 GB space and can easilly be added to other data on my 500 GB backup disk. now to restore this 40 GB image i need a 500 GB disk or larger.

so if these sizes are the sizes of images then yes you need bigger drive. if these are the OS sizes then 128GB might be enough. by the way isn't it cheaper to have a 500 GB hdd than 128GB flash drive? :-O

---

### Post by Dáire Fagan on 2014-04-03
> **mastablasta said:**
> the device you are backing up to needs to be big enough for the image. but the device where you restore data to need to be of same size or larger.

example -  i had a 500 GB disk, before i did dualboot i backed up the disk. the image took about 40 or 50 GB space and can easilly be added to other data on my 500 GB backup disk. now to restore this 40 GB image i need a 500 GB disk or larger.

so if these sizes are the sizes of images then yes you need bigger drive. if these are the OS sizes then 128GB might be enough. by the way isn't it cheaper to have a 500 GB hdd than 128GB flash drive? :-O

Hi mastablasta, thanks for the response.

Previously I tried backing up my main windows partition which was 50GB but with only around ~24GB in use to a 30GB partition but Clonezilla gave me the error that there was not enough space - this is despite the fact that when I reinstalled everything again and tried backing up the same to a 50GB partition instead it worked (creating only a 16GB too) - this seems to go against what you are saying?

Maybe when you did it you backed up to a larger disk first and then moved the image - if so you began backing up to an  image of the same size or larger, which Clonezilla seems to require?

Without checking I think a 500GB HDD and 128GB flash drive are probably very close in price ;) The point I should have made is that if I am just creating backups not much larger than 16Gb I would prefer to backup to a 128GB flash drive as I could use that for other purposes that I could not use the physically large HDD for.

Sudodus, if you are still following the thread, I have to read through it again carefully and then try it but this guide seems to suggest what I want to do is possible, without external storage - [URL="http://www.dedoimedo.com/computers/clonezilla.html"]The new and definite CloneZilla tutorial - Dedoimedo
[/URL]

Just to categorically state again I do appreciate the value of non local back up media but for the moment I need to get Windows backed up somewhere so I can start installing Linux :) Also, if I will be working with partitions and the Windows backup is going to be 16GB I have a key I can transfer it to afterwards, the problem is Clonezilla seems to require a backup destination larger or equal to the size of the source. I think it would also be cool to be able to restore Windows just using a backup partition from my laptop in case I am on the road etc without it.

---

### Post by sudodus on 2014-04-04
Clonezilla needs  a destination (target drive) larger or equal to the size of the source

1. for cloning directly to a target drive

2. for expanding an image of the source drive to a target drive

*. but *not* for creating an image (of a drive or of a partition). In this case it is enough to 'house' the size of the compressed image or the files in the source drive plus some rather small administration (boot loader, partition table, file system administration etc).

But there is a catch: Yes, you can create such an image, but you cannot test that it is good without a destination (target drive) larger or equal to the size of the source. So you don't know if your backup is good (can be used to restore your system).

---

### Post by mastablasta on 2014-04-04
i used redobackup last time i imaged the disk. clonezilla is good and has a lot of settings. however, a wrong setting set and it could give you such a "problem". so if you want to still use clonezilla, make sure what you set up is correct. 

i only used clonezilla and i think free disk space was larger than backup parittion. the image was good. thoough eventually i couldn't get computer to boot (for other reasons)

also it's true what sudodus says you can not test it with a smaller disk. so the only option would be is to image it back ot the good system or to same disk size. or to trust it that the image is good.

nice Clonezilla tutorial: [http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

---

