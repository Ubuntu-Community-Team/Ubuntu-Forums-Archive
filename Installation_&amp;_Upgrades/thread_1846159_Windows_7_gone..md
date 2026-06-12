---
title: "Windows 7 gone."
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by mistermister on 2011-09-18
I installed Ubuntu from a pendrive, I had only one HDD but with two partitions, I choose "install alongside windows 7" but now I see 900+ gb free and it boots directly into Ubuntu. I have never used Ubuntu before but two of my hdds crashed in July due to power problems and this is basically where I have everything. I have some irreplaceable stuff on this hdd and if it is the case that everything is gone... I really don't know what to do. 

I'm freaking out now because basically 3 month of project, all my backup and personal memories of my fathers last days is on there...

My knowledge of Ubuntu is zero. I installed it using a pendrive and I was recommended Ubuntu to try to run my crashed hdds. The Windows 7 I got frmo my previous job and I have no access to it. I've no cd reader, had this computer for 3 years and never needed one, so i cant burn anything. I just have my usb drive.

Please tell me it's not all gone. I'm not a kid but I'm just very shaken up right now so my thought process is kind of hindered. I also see no hdd, just "my home folder".

EDIT: I have now read a bit about it and apparently there IS a chance to get it back so my hope all rely on it, I read it's called test disk and someone suggested to use the LIVE CD/Pendrive instead of the hdd so not to damage things. Will I be able to use Windows 7 and the programs files if I recover?  Can someone help me out, I'll be forever in your debt and this thing comes 2 days after a 6 years relationship break up, being hospitalized for 2 months and someone close passing away less then half a year ago. I'm just drowning right now and I'm really sorry for all the personal information and freaking out but I can't help it. I have experience with computers but I have never used anything else but Windows.

I'm on my pendrive now and I'll listen to any advice you give me, I have no other harddrive at the moment but if I need to buy one to transfer things to - I'll do it. Oh and please feel free to move it if I put it in the wrong section.

---

### Post by Old_Grey_Wolf on 2011-09-18
First we need to determine if your Windows 7 partition is still there before using recovery tools. If you are in Ubuntu open a terminal and type the following command and post the output back here.
```
sudo fdisk -l
```

It will be helpful if you tell use what version and release of Ubuntu you are using. Such as, Ubuntu, Kubuntu, 10.04, 10.10, 11.04.

Edit: Try to be calm and patient. We live in different time zones so this may take a while and involve several people trying to help.

---

### Post by mistermister on 2011-09-18
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e56df85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT

Disk /dev/sdb: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00200020

Disk /dev/sdb doesn't contain a valid partition table


```

It says Welcome to Ubuntu 11.04 so I assume it is that.

---

### Post by Mark Phelps on 2011-09-18
> **mistermister said:**
> I have never used Ubuntu before but two of my hdds crashed in July due to power problems and this is basically where I have everything. I have some irreplaceable stuff on this hdd and if it is the case that everything is gone... I really don't know what to do. ... My knowledge of Ubuntu is zero. I installed it using a pendrive and I was recommended Ubuntu to try to run my crashed hdds. 
NO OS is going to work with crashed drives, period.  Unfortunately the person who recomended using Ubuntu with crashed drives did not understand this simple fact ...

> I'm freaking out now because basically 3 month of project, all my backup and personal memories of my fathers last days is on there...
There are ways to recover data from Windows filesystems ... even if the OS on those drives no longer boots.

> The Windows 7 I got frmo my previous job and I have no access to it. I've no cd reader, had this computer for 3 years and never needed one, so i cant burn anything. I just have my usb drive.
That's no problem because you don't want to actually use the OS on those drives if they are damages or have been overwritten.

> Please tell me it's not all gone. 
OK ... "it's not all gone".

My own experience, having gone through similar problems for other folks, is that Windows utilities are BEST at recovering data from Windows filesystem drives; Linux utilities are best at recovering data from Linux filesystem drives.

Unfortunately, the best of the Windows utilities are not free -- but their trial versions ARE.

So, I would strongly recommend the following:
1) Remove the physical drives in question and don't attempt to use them with ANY OS.  Any usage is going to severely worsen your chances of recovering data.
2) Find someone with a working Windows PC.
3) Have that person go to the Runtime Software website, download and install the trial version of GetDataBack for NTFS.
4) Hook up the drive from which you want to recover data to the Windows PC. Run GetDataBack -- but let it run overnight in the deepest discovery mode.
5) Check in the morning to see if it found the files that you want to recover.  IF if did, you will then have to purchase the software to do the actual recovery.  But, you will not have to reinstall it or restart the PC.

Your data -- your money -- your choice.

---

### Post by mistermister on 2011-09-18
Sadly I have only one hdd. I can borrow a laptop but I'll have to buy an extra hdd too it seem to copy things over or install windows 7 on.

I'll wait for more people to post and more advice but for tmrw, it's 10 pm here now, I'll buy a new S-ata hdd and install Windows 7 on. Then you're telling me that I should buy GetDataBack, how much percentage does it usually restore if anyone knows? Is there such a big difference with GetDataBack and Testdisk? I'll spend the money if people think it is worth it. I'm using the LIVE pendrive now but I guess it's indirectly using the hdd too which is plugged in. I'll plug it out and try to find someone with a laptop I can borrow.

(Thanks to both you guys btw. I personally figure there should be more information about it formating the hdd or some kind of red blinking warning )

---

### Post by Old_Grey_Wolf on 2011-09-18
> **mistermister said:**
> ... I personally figure there should be more information about it formating the hdd or some kind of red blinking warning 

Just take this as a learning experience. I'm not being critical of you as this is something we all have to learn, and sometimes the hard way. There is an assumption made by all operating systems developers that you back up important files regularly. You never know when a disk is going to fail, and sometimes bad things happen when you play around with the drive's partitions. Windows 7 has a backup utility for a reason. You are not alone in your situation. That is part of the reason why my signature below read as it does.

I am glad that Mark Phelps stepped in. When I saw the output from the fdisk command, I realized you are using large disk drives **with new partition table formats that I am not familiar with**. I probably wouldn't have been able to help.

---

### Post by mistermister on 2011-09-18
Thanks 

Wont it be linux file system build up since it formated everything and installed over it?

---

### Post by MG&amp;TL on 2011-09-18
Technically, yes, but as I understand it (feel free to correct me everyone) you can format something, but nothing will be irreparably 'gone' until you overwrite it, and with a fresh install and 900+GB, I guess most stuff will still be there.

So I guess the windows filesystem is still there?

IDK much about this, but I've had to recover some CF a couple of times.

---

### Post by YesWeCan on 2011-09-18
Don't give up yet! Your 1TB disk has a new type of partition table on it called GPT which fdisk does not work with. It may be your Windows partitions are still there and accessible.

Please post the output of
```
sudo parted /dev/sda print
```

And we'll see what's there and figure out how to access it.

---

### Post by mistermister on 2011-09-18
Thanks guys, every post even though its just advice or pointing something out does up the spirit a bit. I've calmed down now and I hope I'll manage to recover much of the data.Supposed to have a logo presentation done by Tuesday but I doubt I'll be able to recover that. Might cost me the job but let us hope not.
> **YesWeCan said:**
> Don't give up yet! Your 1TB disk has a new type of partition table on it called GPT which fdisk does not work with. It may be your Windows partitions are still there and accessible.

Please post the output of
```
sudo parted /dev/sda print
```And we'll see what's there and figure out how to access it.
```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sda: 8006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8005MB  8004MB  primary  fat32        boot

ubuntu@ubuntu:~$ 


```8GB? I don't think I had a 8gb partition, maybe the "Program" partition.

EDIT: It is 2 am for me and I'll sleep. Tomorrow I'll go off to buy a harddrive but keep the advices coming or ask if you need more info. Oh and I do know about keeping back up. One external crashed but I had backup on my internal hdd. The next week my internal hdd breaks after the power went in the neighborhood, happened a few times and nothing crashed before, so I lost those backups. I managed to copy a few of the most important things from the external, using ubuntu, before it gave up and I had them on my internal. I was waiting for the prices to drop on the computer market, end of the year, before buying a completely new computer alas this happened now and I find myself looking like an idiot.

---

### Post by Old_Grey_Wolf on 2011-09-18
If you are running the OS from the USB stick (sda I guess); then, try these commands to see if it gives you the info for your two HDDs (sdb or sdc).
```
sudo parted /dev/sdb print
``````
sudo parted /dev/sdc print
```

---

### Post by YesWeCan on 2011-09-18
> **Old_Gray_Wolf said:**
> You are running the OS from the USB stick (sda); therefore, try this command to see if it gives you the info for your HDD (sdb).
```
sudo parted /dev/sdb print
```
Yes. Unfortunately the drive letters tend to change when you boot from a different device.

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e56df85

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Blue]/dev/sda1               1      121602   976762583+  ee  GPT[/COLOR]
```
So a GUID partition table (GPT) disk format has 2 partition tables on it, confusingly. It has the new GUID table and it also has an MBR table with a "fake" entry in it. This is called a "protective MBR" and is intended to show old systems that do not know about GPT that the disk has one partition on it of maximum size. The idea is to fool the old system that the drive is full and should not be written to.

fdisk does not know how to read the GPT so instead it just shows the protective MBR table. The single partition is always of type EE and spans from sector 1 to the last sector on the disk or 2^32 sectors, whichever is lower. The MBR table can only specify up to 2^32 sectors which is usually 2TiB.

---

### Post by mistermister on 2011-09-18
```
Number  Start   End     Size    File system     Name                          Flags
 1      17.4kB  134MB   134MB                   Microsoft reserved partition  msftres
 2      134MB   135MB   1000kB                                                bios_grub
 3      135MB   996GB   996GB   ext4
 4      996GB   1000GB  4295MB  linux-swap(v1)

```

I couldn't boot from the usb  for some reason. So I'm on my hdd for a quickie. I don't have two harddrives, just my usb and my internal hdd. I have two external though.

---

### Post by YesWeCan on 2011-09-18
Unfortunately, that shows no Windows OS or data partitions. There are other ways to try to find the data like testdisk but best to leave it until tomorrow now. At least for me.

I'd second Mark Phelps in advising not to use this Ubuntu because the more you use it the more of the Windows remains will get corrupted and the less chance you will have to recover anything. Try only to boot off USB, CD or another Ubuntu installation.

---

### Post by Old_Grey_Wolf on 2011-09-18
> **YesWeCan said:**
> Unfortunately, that shows no Windows OS or data partitions. There are other ways to try to find the data like testdisk but best to leave it until tomorrow now. At least for me.

I agree! I think we all need to get some sleep. I have to go to work tomorrow so it is time to sleep. When we are tired, it is not the best time to troubleshoot these types of problems. 

Good night all.

---

### Post by YesWeCan on 2011-09-20
Here are some instructions for using testdisk: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can install it from the Ubuntu Software Centre.

I have never used it to recover lost partitions so I can't really help any further, sorry. I seem to recall member coffeecat has more knowledge.

---

### Post by Mark Phelps on 2011-09-20
If you install ANYTHING to the drive you're trying to recover, you will pretty much guarantee that you will be able to recover little or nothing of the former files.

My recommendation was to NOT use the drive with any OS, but instead, to use MS Windows, and a Windows-based utility that I have found to work very well in the past.

It won't restore your working Windows OS, but it might do a very good job of finding your former files ...

But NOT if you keep using it.

---

