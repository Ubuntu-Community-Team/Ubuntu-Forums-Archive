---
title: "Problem while installing the ubuntu 10.10 in my Hp laptop"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by chansanle on 2011-05-12
My Hp laptop Pavilion dv6 runs the windows 7 and i want to install ubuntu 10.10 but the following error occurs.

Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe/set
{cb6d002a-efa5-11df-a20c-ff847b0445f8}device partition=G:
>>retval=1
>>stderr=An error has occured setting the element data.
The request is ot supported.

>>stdout=

for more information,please see the log file:
c:\users\chandra\appdata\local\temp\wubi-10.10-rev197.log

---

### Post by bcbc on 2011-05-12
Are you using dynamic drives? These can only be used with Windows.

---

### Post by chansanle on 2011-05-13
Thanks for ur reply bcbc. Sorry that i dono abt the dynamic drives.So can u tell me "how can i find that i am using the dynamic drives in my laptop or not". And will that affect the installation steps of Ubuntu 10.10

---

### Post by Hedgehog1 on 2011-05-13
The best way to get a look at you system and see what your install options are is to do this:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by chansanle on 2011-05-13
thanks for ur help hedge. But my laptop runs on Win7, so how can i run the shell script .sh file.

---

### Post by bcbc on 2011-05-13
> **chansanle said:**
> Thanks for ur reply bcbc. Sorry that i dono abt the dynamic drives.So can u tell me "how can i find that i am using the dynamic drives in my laptop or not". And will that affect the installation steps of Ubuntu 10.10

Right click on Computer, Manage, go to the Disk Manager. It should tell you whether the partitions are dynamic or simple. Or just post a screen shot.

You cannot install Ubuntu on a drive that has dynamic drives without risking your data (since ubuntu will be unaware of the partitions that are not in the partition table).

---

### Post by chansanle on 2011-05-14
Hi bcbc,
            Thanx for ur kind help,u r correct it is dynamic drive only. The Layout is simple, Type is dynamic, File System is NTFS except one drive which is FAT32 for HP_TOOLS then finally status is healthy. i have attached the screen shot also bcbc.

---

### Post by bcbc on 2011-05-14
Yeah HP seems to like shipping computers with 4 primary partitions already used. Windows 7 is okay switching those to dynamic in order to create more, but these don't play well with Ubuntu. Your best bet is installing to an external drive or booting from a USB stick (with persistence)... but I think even mounting and writing to a dynamic drive from Ubuntu could be dangerous (Ubuntu will see C: as a single 575GB partition instead of 3 separate partitions).

The only way around this would be to convert back from Dynamic to normal (which I believe requires an external tool), delete one of the primary partitions and shrink another, then create an extended partition in the space (which can contain many logicals). You'd want to do a full system backup (restore image) before attempting something like this.

---

### Post by chansanle on 2011-05-14
hi bcbc,
           again thanx for ur dedicated work for newbie lik me bcbc. It seems that changing dynamic drive to normal is risky and notworth, so decided to install by usb stick or external drive, but i have to study about how to install ubuntu by usb or hard drive. If i face any issues then i will post here. Then my questions are
1) Is that a nice decision to install ubuntu through USB stick or Hard Drive ?
2)Is there any other unix variant i.e. red hat, fedora, etc... which is easy to install in dynamic drive?
3)Can i know more about u in deep, since i am a fresher in a s/w industry, i consider u as a motivational factor who help all the newbie and doing ur job simultaneously.
4)If possible give ur personal email ID or FB ID where it is possible to contact u wen i have been struck?
5)I am been going to engage in a N/W project within 2 weeks, so can u give me a idea where i can start and to whom i can ask this type of technical questions.
6)Finally where r u working and how r u making urself technically strong ?

Sorry for asking these many number of question, but i am totally excited to meet passionate people like u. I love ur dedicated work bcbc.

---

### Post by bcbc on 2011-05-14
> **chansanle said:**
> hi bcbc,
           again thanx for ur dedicated work for newbie lik me bcbc. It seems that changing dynamic drive to normal is risky and notworth, so decided to install by usb stick or external drive, but i have to study about how to install ubuntu by usb or hard drive. If i face any issues then i will post here. Then my questions are
1) Is that a nice decision to install ubuntu through USB stick or Hard Drive ?
2)Is there any other unix variant i.e. red hat, fedora, etc... which is easy to install in dynamic drive?
3)Can i know more about u in deep, since i am a fresher in a s/w industry, i consider u as a motivational factor who help all the newbie and doing ur job simultaneously.
4)If possible give ur personal email ID or FB ID where it is possible to contact u wen i have been struck?
5)I am been going to engage in a N/W project within 2 weeks, so can u give me a idea where i can start and to whom i can ask this type of technical questions.
6)Finally where r u working and how r u making urself technically strong ?

Sorry for asking these many number of question, but i am totally excited to meet passionate people like u. I love ur dedicated work bcbc.
Thank you for the compliments. There are a lot of knowledgeable people on ubuntuforums.org that I have learned from - and I recommend monitoring the forums in areas that interest you - you will learn very quickly by helping others or trying things out. There are many different subforums where you'll find different subject matter experts e.g. Development and programming. Also you can check out the IRC (see [http://irclogs.ubuntu.com/](http://irclogs.ubuntu.com/) for a list of official ubuntu channels) and askubuntu.com.
If you cannot install on your internal hard drive, I think it's a good idea to install to an external USB drive. You probably won't notice a difference in performance - make sure you put the grub bootloader on the external (or else nothing will boot unless the external is plugged in). Alternatively you can also install wubi to an external. Don't mount your internal drive's partitions though - I think that might be a risk since Ubuntu won't be aware of the dynamic drives. I'm not aware of any other distro that can handle dynamic drives. 

Good luck!

---

### Post by foresthill on 2011-05-14
I believe that Windows 7 can create a new partition from the unused space on the drive, using tools in the Disc Management app. IIRC, that's what I did on my Gateway notebook.

I can't recall the exact details of what I did, but that's the general idea of how I did it.

---

### Post by chansanle on 2011-05-15
thanx for ur help bcbc.
If i am using usb for installing ubuntu, the image and bootloader will be in the usb stick. Where will the User data will be stored in the usb stick or in the internal hard drive.

---

### Post by chansanle on 2011-05-15
thanx for ur replay foresthill, but i heard that ubuntu will not be able to recognize the dynamic drives ?, so how can i proceed with the installation of the ubuntu having dynamic drive in my HP pavilion dv6.

---

### Post by bcbc on 2011-05-15
> **chansanle said:**
> thanx for ur help bcbc.
If i am using usb for installing ubuntu, the image and bootloader will be in the usb stick. Where will the User data will be stored in the usb stick or in the internal hard drive.
You can use create an Ubuntu USB with the universal USB installer - see here for instructions: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (go to step 2, click on USB stick, and Show Me How). If you create a persistence file - recommended - then it will save your settings/data. But it's going to be much slower than a regular install.

You can 'install' Ubuntu to a USB drive or stick - it will be the same as if you installed to your internal drive in terms of speed and experience. Make sure you install the bootloader on the USB drive. Don't mount your windows partitions from Ubuntu.
If you have a USB drive with enough space you could create an ntfs partition on it for sharing data between Windows and Ubuntu.

---

### Post by chansanle on 2011-05-16
> **bcbc said:**
> You can use create an Ubuntu USB with the universal USB installer - see here for instructions: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (go to step 2, click on USB stick, and Show Me How). If you create a persistence file - recommended - then it will save your settings/data. But it's going to be much slower than a regular install.

You can 'install' Ubuntu to a USB drive or stick - it will be the same as if you installed to your internal drive in terms of speed and experience. Make sure you install the bootloader on the USB drive. Don't mount your windows partitions from Ubuntu.
If you have a USB drive with enough space you could create an ntfs partition on it for sharing data between Windows and Ubuntu.

Thanks for your reply bcbc.is it k to use a 4gb USB stick?
wat file format is supported by ubuntu? is it FAT32? then y i should not mount window partition in ubuntu?

---

### Post by bcbc on 2011-05-17
If you're installing to the USB then it will format it ext4, not fat32. If you're just creating a bootable Ubuntu USB then the base format is probably fat32, but once the live desktop is running it has a virtualized file system -  so once Ubuntu (regardless of source medium) is running it does not recognize dynamic drives. In particular it will treat C:, G: and H: as one partition. My advice is to avoid mounting the partitions unless you have found some reliable source stating it is safe.

---

### Post by chansanle on 2011-05-17
hmmm thanks a lot bcbc

---

### Post by bcbc on 2011-05-17
I've been trying to find something definitive on whether ubuntu supports dynamic drives or not. Haven't been able to find it. There is a product Paragon LDM that retails for $30 that supports all versions of dynamic drives under linux.

I'll search on this some more and consider filing a bug so at least we might get a developer opinion on this as I suspect we'll see this more and more with Windows 7 for Wubi users.

---

### Post by chansanle on 2011-05-18
hey bcbc really 1000*thanks for ur dedicated work man. If u were able to find a solution for this dynamic driver under linux then u r the source for ubuntu entering the Win7 OS (i.e. a Gateway). :)

---

