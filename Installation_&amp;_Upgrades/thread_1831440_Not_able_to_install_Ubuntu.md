---
title: "Not able to install Ubuntu"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by chk1123 on 2011-08-23
Hello! I am new to linux, ubuntu, wubi, this forum etc. I tried to install ubuntu using wubi- i downloaded wubi, downloaded the  ubuntu iso(correct one), put wubi and iso in same folder, and clicked on  it. I selected drive f: to install ubuntu, and set up user name,  password etc, then clicked install. It installed correctly, and then  asked whether to reboot now or later. i choose to reboot. when  appropriate screen came up, i choose ubuntu. then it started installing,  but as soon as it finished verifying installation files, an error came  up-
 "No root file system is defined.Please correct this from the partitioning menu" and then asked to choose it during file  partioning. 
I could not understand it, i clicked ok several times but same error  message popped up. What to do?Please help. 
My system specs- Hardware- Acer aspire 6930, 2 Ghz core 2 duo processor, 3 Ghz ram, 320 gB hard  disk. my harddisk had been partitioned while installing windows into  four-C:(30 gb), d:(20 gb), e:(230 gb), f:(20 gb) 
software- Windows 7-it is installed on c: and i am trying to install ubuntu on f: which has 19 gb free.Posting boot info script-
```


Boot Info Script 0.60    from 17 May 2011   ============================= Boot Info Summary:  ===============================   => Windows is installed in the MBR of /dev/sda.  sda1:  __________________________________________________________________________       File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   No errors found in the Boot Parameter Block. ============================ Drive/Partition Info:  =============================  Drive: sda  _____________________________________________________________________  Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *          2,048    61,442,047    61,440,000   7 NTFS /  exFAT / HPFS /dev/sda2          61,442,048   102,402,047    40,960,000   7 NTFS /  exFAT / HPFS /dev/sda3         102,402,048   143,362,047    40,960,000   f W95  Extended (LBA) /dev/sda5         102,404,096   143,359,999    40,955,904   7 NTFS /  exFAT / HPFS /dev/sda6         143,362,048   625,139,711   481,777,664   7 NTFS /  exFAT / HPFS  the logical partition /dev/sda6 is not contained in the extended  partition /dev/sda3  "blkid" output:  ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              iso9660     Ubuntu 11.04 i386 /dev/loop1                                              squashfs    /dev/sda1        3ACA7128CA70E215                       ntfs        Windows 7 /dev/sda2        4A2A525C2A5244DB                       ntfs       LINUX /dev/sda5        88907CB6907CAC76                       ntfs       Local  Disk /dev/sda6        725C2E025C2DC229                       ntfs       DATA  ================================ Mount points:  =================================  Device           Mount_Point              Type       Options  /dev/loop0       /cdrom                   iso9660    (ro,noatime) /dev/loop1       /rofs                    squashfs   (ro,noatime) /dev/sda1        /tmp/BootInfo0/sda1      fuseblk     (ro,nosuid,nodev,allow_other,blksize=4096) /dev/sda2        /isodevice               fuseblk     (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)   ========================== sda1/grldr embedded menu:  ===========================  --------------------------------------------------------------------------------  =========  Devices which don't seem to have a corresponding hard drive: =========  sdb   =============================== StdErr Messages:  ===============================  /home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 :  syntax error: operand expected (error token is "/ 2 ) + 16 ") 
```
 I have posted all relevant info.Please help!!

---

### Post by chk1123 on 2011-08-23
> **chk1123 said:**
> Hello! I am new to linux, ubuntu, wubi, this forum etc. I tried to install ubuntu using wubi- i downloaded wubi, downloaded the  ubuntu iso(correct one), put wubi and iso in same folder, and clicked on  it. I selected drive f: to install ubuntu, and set up user name,  password etc, then clicked install. It installed correctly, and then  asked whether to reboot now or later. i choose to reboot. when  appropriate screen came up, i choose ubuntu. then it started installing,  but as soon as it finished verifying installation files, an error came  up-
 "No root file system is defined.Please correct this from the partitioning menu" and then asked to choose it during file  partioning. 
I could not understand it, i clicked ok several times but same error  message popped up. What to do?Please help. 
My system specs- Hardware- Acer aspire 6930, 2 Ghz core 2 duo processor, 3 Ghz ram, 320 gB hard  disk. my harddisk had been partitioned while installing windows into  four-C:(30 gb), d:(20 gb), e:(230 gb), f:(20 gb) 
software- Windows 7-it is installed on c: and i am trying to install ubuntu on f: which has 19 gb free.Posting boot info script-
```


Boot Info Script 0.60    from 17 May 2011   ============================= Boot Info Summary:  ===============================   => Windows is installed in the MBR of /dev/sda.  sda1:  __________________________________________________________________________       File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   No errors found in the Boot Parameter Block. ============================ Drive/Partition Info:  =============================  Drive: sda  _____________________________________________________________________  Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *          2,048    61,442,047    61,440,000   7 NTFS /  exFAT / HPFS /dev/sda2          61,442,048   102,402,047    40,960,000   7 NTFS /  exFAT / HPFS /dev/sda3         102,402,048   143,362,047    40,960,000   f W95  Extended (LBA) /dev/sda5         102,404,096   143,359,999    40,955,904   7 NTFS /  exFAT / HPFS /dev/sda6         143,362,048   625,139,711   481,777,664   7 NTFS /  exFAT / HPFS  the logical partition /dev/sda6 is not contained in the extended  partition /dev/sda3  "blkid" output:  ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              iso9660     Ubuntu 11.04 i386 /dev/loop1                                              squashfs    /dev/sda1        3ACA7128CA70E215                       ntfs        Windows 7 /dev/sda2        4A2A525C2A5244DB                       ntfs       LINUX /dev/sda5        88907CB6907CAC76                       ntfs       Local  Disk /dev/sda6        725C2E025C2DC229                       ntfs       DATA  ================================ Mount points:  =================================  Device           Mount_Point              Type       Options  /dev/loop0       /cdrom                   iso9660    (ro,noatime) /dev/loop1       /rofs                    squashfs   (ro,noatime) /dev/sda1        /tmp/BootInfo0/sda1      fuseblk     (ro,nosuid,nodev,allow_other,blksize=4096) /dev/sda2        /isodevice               fuseblk     (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)   ========================== sda1/grldr embedded menu:  ===========================  --------------------------------------------------------------------------------  =========  Devices which don't seem to have a corresponding hard drive: =========  sdb   =============================== StdErr Messages:  ===============================  /home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 :  syntax error: operand expected (error token is "/ 2 ) + 16 ") 
``` I have posted all relevant info.Please help!!
I am new to this forum, so please bear with my mistakes!

---

### Post by oldfred on 2011-08-23
The advantage of wubi is that you do not have to create partitions and then can easily uninstall like a program in windows. It runs totally inside the windows NTFS partition and boots with the windows boot loader. It is intended for a Windows user to become familiar with Ubuntu as a longer test than a liveCD, but is not intended for long term use.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

But you have create sda5 & sda6. If you want you can convert to Linux type formats (it will erase all data if you have data in them) and do a full install to separate partitions. Then you do not have to rely on windows and the NTFS partition. Possibly better for a new user is just to delete sda5 & sda6 and let the Ubuntu installer on a CD or liveUSB do the auto install. I prefer manual installs, but you have to specify format (ext4) and / (root) and a smaller partition for swap (2GB typically).

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Most important is to have good backups before any major system changes installs or upgrades.

---

### Post by bcbc on 2011-08-23
The problem is this:
> the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3


Ubuntu will not install with partition table errors (it's much more fussy than Windows obviously).

So you need to correct that problem before installing either with wubi or normal. You can refer to this: [http://www.rodsbooks.com/fixparts/index.html](http://www.rodsbooks.com/fixparts/index.html)

But hopefully the author *srs5694* will drop by this thread to confirm usage if you need help.

---

### Post by srs5694 on 2011-08-23
> **bcbc said:**
> Ubuntu will not install with partition table errors (it's much more fussy than Windows obviously).

So you need to correct that problem before installing either with wubi or normal. You can refer to this: [http://www.rodsbooks.com/fixparts/index.html](http://www.rodsbooks.com/fixparts/index.html)

But hopefully the author *srs5694* will drop by this thread to confirm usage if you need help.

I'd say your analysis is correct. I don't recall ever seeing this specific type of error before, so I'm not sure how FixParts will handle it. Ideally, it'll fix it automatically by either resizing the extended partition to cover /dev/sda6 or by converting /dev/sda6 into a primary partition. It's conceivable that it will try to omit one of the partitions, though. If you type "p" in FixParts and see "omitted" under the "status" column for any of the existing partitions, *do not* type "w"; either work out how to get the partition included yourself or post back with details so I can advise you. If FixParts shows all four of your partitions (FixParts ignores the extended partition) as being either primary or logical, though, with /dev/sda1 as primary, it should be safe to type "w" to save your changes.

---

### Post by chk1123 on 2011-08-24
Dear Sirs,
Thank you all very much for replying.I am new and dont understand your instructions.
The links which are given are for using dual boot, but i want to know why Wubi does not work with my system even when i have followed all instructions and how to correctly install Ubuntu using Wubi only.

---

### Post by oldfred on 2011-08-24
I missed the partition table error that bcbc caught. You need to fix that before doing anything else as that often prevents new installs or causes other problems.

Did youi run the fixparts program?

Do you have a repair CD for every system installed? You should have a Ubuntu liveCD of the version installed and a Windows repairCD or USB for your Windows.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by chk1123 on 2011-08-24
I will make the windows recovery CD.
But i dont want to take any risks with windows as my father and brother also work on the same windows,so they will be much inconvenienced if windows is corrupted.
But if i make recovery CD, then i can correct windows if it was damaged during the fixed parts setup??

One more thing,when i select ubuntu in the boot menu,by pressing escape,i can use ubuntu(demo mode).
From this mode,there was an option on the desktop, "install ubuntu 11.04", but when i selected it, it did not display "install alongside windows 7" even though win 7 is installed and working.When i tried the "something else" option,the partitioning menu does not display any partition of my harddisk, so i cant manually install ubuntu on my F drive partition.only option it displays is"create a new partition table"which will erase my win 7 and all my data! i seem to have no options!:(:(
Please help!!

---

### Post by srs5694 on 2011-08-24
chk1123,

The lack of partitions being displayed when you attempt to install Ubuntu is caused by the partition table error that bcbc identified. FixParts *should* fix this, but be careful and be aware of the caveats I laid out in my earlier post (and on the FixParts Web page).

Once the partition table problem is fixed, your WUBI installation *might* begin working, but I can't promise that. I'm not a WUBI expert (that's more bcbc's area of expertise), so I can't really help you much on that score, but damaged partition tables can cause all sorts of other problems, so it's important to fix them before trying to address other symptoms, especially if they might be related to the partition table problem.

---

### Post by chk1123 on 2011-08-24
Sir can you briefly explain how i have to use this fix-parts tool??:confused:

---

### Post by YesWeCan on 2011-08-24
If those methods don't work out and you have backed up vital files, you can manually correct the partition table.

sudo sfdisk -d /dev/sda > temp

The text file temp will look something like this:
```
/dev/sda1 : start=     2048, size= 61440000, Id=7, bootable
/dev/sda2 : start= 61442048, size= 40960000, Id=7
/dev/sda3 : start=102402048, size= [COLOR="Red"]40960000[/COLOR], Id=5
/dev/sda5 : start=102404096, size= 40955904, Id=7
/dev/sda6 : start=143362048, size=481777664, Id=7
```
The number in red is wrong. You can edit temp using gedit and change the number to this
```
/dev/sda1 : start=     2048, size= 61440000, Id=7, bootable
/dev/sda2 : start= 61442048, size= 40960000, Id=7
/dev/sda3 : start=102402048, size=[COLOR="DarkGreen"]522737664[/COLOR], Id=5
/dev/sda5 : start=102404096, size= 40955904, Id=7
/dev/sda6 : start=143362048, size=481777664, Id=7
```
Then copy the corrected temp back to the partition table:
sudo -s
cat temp | sfdisk /dev/sda
exit

---

### Post by srs5694 on 2011-08-24
> **chk1123 said:**
> Sir can you briefly explain how i have to use this fix-parts tool??:confused:

Please read [its Web page.](http://www.rodsbooks.com/fixparts/) If you have specific questions after reading it, then feel free to post back with your questions.

---

### Post by chk1123 on 2011-08-24
Sorry sir!
As i understand it, first i must go to a terminal through applications, and then i must type-th
```
sudo fixparts /dev/sda
```
is that right??then what i have to do?? do i have to type "p" to display my partition table??
or do i have to first type of sda1 ,then give correct response(whatever it is) then sda2, then sda3 and so on..
or do i directly go to sda6 which is causing problem, should i type-
```
sudo fixparts /dev/sda6
```
I have dowloaded the Gptfdisk from the website in the section how to obtain fixparts, but how to use this file that i have downloaded??
I will be greatly indebted to you and to all the members and admins for your help.:KS

---

### Post by rob45 on 2011-08-24
IF you installed using wubi...and you can still get in to windows just go to add/remove and uninstall it.

---

### Post by srs5694 on 2011-08-24
Type:

```

sudo fixparts /dev/sda

```

You should then view your partition table with "p" to verify that it's all correct. If it is (all partitions are present, not is marked as "omitted," no other obvious problems), type "w" to save your changes.

If you got the gptfdisk_{whatever}.deb file from OBS, you should be able to install it by double-clicking it in a file browser window or by typing "sudo dpkg -i gptfdisk_{whatever}.deb" in a shell prompt.

---

### Post by chk1123 on 2011-08-25
Above instruction is not working.It displays-
sudo: fixparts: command not found

---

### Post by srs5694 on 2011-08-25
> **chk1123 said:**
> Above instruction is not working.It displays-
sudo: fixparts: command not found

You've got to install the program first, by double-clicking the fixparts_{something}.deb or gptfdisk_{something}.deb file, depending on what version you downloaded and from where you obtained it. Alternatively, you can run it from a recovery disc, such as [Parted Magic,](http://partedmagic.com) which comes with the software pre-installed.

---

### Post by chk1123 on 2011-08-25
finally able to run fixparts and output is
```

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 625142448 sectors (298.1 GiB)
MBR disk identifier: 0x688683EF
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048     61442047   primary              Y      0x07
   2              61442048    102399999   primary              Y      0x07
   5             102404096    143359999   logical     Y        Y      0x07
   6             143362048    625139711   logical     Y        Y      0x07

MBR command (? for help): 

```
now what to do??

---

### Post by chk1123 on 2011-08-25
Okay!
By rereading page 1 of this thread, i came to know that now i have to type w as all partitions are displayed and sda1 is primary.so i typed w.it asked for my confirmation and i gave it.now i am going to restart my computer to hopefully see that windows is working fine..:P

---

### Post by chk1123 on 2011-08-25
Thank God windows is working fine!!:P
Now i will again try to install ubuntu with wubi, hopefully without any error!1:popcorn:
Thanks to all  for the help provided.I definitely would not have gone this far without your  collective help.):P

---

### Post by srs5694 on 2011-08-25
That partition list looks correct to me, with one potentially important exception: The Boot Info Script output you posted in post #1 to this thread shows /dev/sda2 ending at sector 102,402,047, whereas FixParts is reading /dev/sda2's ending sector as 102,399,999. Have you used any other partitioning tools on the disk between the time you ran the Boot Info Script and running FixParts? If so, it could be that tool changed the partition's end sector. If not, it's a puzzling discrepancy, and I recommend determining the cause before proceeding. To that end, you can use fdisk and sfdisk to obtain partition listings:

```

sudo fdisk -l /dev/sda
sudo sfdisk -d /dev/sda

```

If those match the FixParts output, I'd be inclined to proceed with the FixParts operation by typing "w" at its command prompt. (Be aware that sfdisk reports partition sizes rather than end sectors, though, so you've got to add the start and size values and subtract 1 to make a comparison.) If the fdisk and sfdisk outputs match your earlier Boot Info Script output, though, something else is going on -- perhaps a FixParts bug or some inconsistency in the MBR data. If you post or send me a copy of the MBR, I could do a better diagnosis. The following command will create a text-mode dump that you can post:

```

sudo hexdump -n 512 /dev/sda
```

If hexdump isn't installed on your system, you can install it by typing "sudo apt-get install bsdmainutils".

---

### Post by chk1123 on 2011-08-25
No luck!!
On installing wubi in windows,after it extracts the files and installes them, when time remaining becomes 0 , the a window pops up with the following error message-

```

Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the path specified.

```
there is also a link to a log file, which i opened, but its so vast that i hesitate to put it.

---

### Post by srs5694 on 2011-08-25
Looks like I posted just a little too slowly....

I recommend you run CHKDSK on /dev/sda2 (by whatever its name is under Windows, of course). If FixParts wrote the wrong (smaller) partition size to disk, it's possible that the partition size and filesystem size don't match, which could cause problems if it's not corrected. I don't know offhand how CHKDSK handles such inconsistencies, but with any luck it'll be able to repair them, or at least tell you that you've got a problem. In the latter case, you should be able to repair the problem by using Linux's fdisk to re-create the partition with its correct size.

---

### Post by chk1123 on 2011-08-25
> **srs5694 said:**
> That partition list looks correct to me, with one potentially important exception: The Boot Info Script output you posted in post #1 to this thread shows /dev/sda2 ending at sector 102,402,047, whereas FixParts is reading /dev/sda2's ending sector as 102,399,999. Have you used any other partitioning tools on the disk between the time you ran the Boot Info Script and running FixParts? If so, it could be that tool changed the partition's end sector. If not, it's a puzzling discrepancy, and I recommend determining the cause before proceeding. To that end, you can use fdisk and sfdisk to obtain partition listings:

```

sudo fdisk -l /dev/sda
sudo sfdisk -d /dev/sda

```If those match the FixParts output, I'd be inclined to proceed with the FixParts operation by typing "w" at its command prompt. (Be aware that sfdisk reports partition sizes rather than end sectors, though, so you've got to add the start and size values and subtract 1 to make a comparison.) If the fdisk and sfdisk outputs match your earlier Boot Info Script output, though, something else is going on -- perhaps a FixParts bug or some inconsistency in the MBR data. If you post or send me a copy of the MBR, I could do a better diagnosis. The following command will create a text-mode dump that you can post:

```

sudo hexdump -n 512 /dev/sda
```If hexdump isn't installed on your system, you can install it by typing "sudo apt-get install bsdmainutils".
Sir i do not remember correctly but i think that at time of boot info script i had deleted my f: partition(using windows disk management) in hopes that ubuntu would recognise it as unallocated space and install on it, but when it failed, i created my f: partition back using windows disk management.Perhaps this can explain the discrepancy.
anyway i have already typed w as i stated earlier then successfully booted to windows and tried to install wubi, when the error message comes which i have posted in next(or previous) post, please help with that as well!!

---

### Post by YesWeCan on 2011-08-25
In post #18 Fixparts has chopped off 2048 sectors of the second partition. Is it meant to do that?

---

### Post by bcbc on 2011-08-25
> **chk1123 said:**
> No luck!!
On installing wubi in windows,after it extracts the files and installes them, when time remaining becomes 0 , the a window pops up with the following error message-

```

Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the path specified.

```
there is also a link to a log file, which i opened, but its so vast that i hesitate to put it.
Windows doesn't know the location of the BCD store. If you run bcdedit (hit START, type cmd, don't press enter yet, look above to CMD.EXE, right-click and run as administrator, then type bcdedit and press enter) it should output your current boot setup. However, it seems like it doesn't have the location of the bcd store set so you should get that same error message.

I'm not sure why this happens (I haven't reproduced this on my win7 computers). If you [search the web]("http://www.google.ca/search?sourceid=chrome&ie=UTF-8&q=bcdedit+store+could+not+be+opened#sclient=psy&hl=en&source=hp&q=The+boot+configuration+data+store+could+not+be+opened+path+specified&pbx=1&oq=The+boot+configuration+data+store+could+not+be+opened+path+specified&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=109162l114390l0l114993l18l16l0l0l0l0l373l4075l0.3.10.3l16l0&bav=on.2,or.r_gc.r_pw.&fp=345d71338e2a06e9&biw=1073&bih=637") you'll see that many people have this issue. For some the solution is to unhide the system partition, assign it a drive and set the store location. 

PS the reason I'm giving a link to a google search is that I haven't personally found a link that seems to provide a satisfactory solution - although there are some workarounds (unhiding the boot partition) that seem to be successful. On my computer, it's hidden, yet bcdedit knows where it is. So you shouldn't have to do this.

Hope that helps.

---

### Post by srs5694 on 2011-08-25
> **YesWeCan said:**
> In post #18 Fixparts has chopped off 2048 sectors of the second partition. Is it meant to do that?

Did you read the second page of messages? We may never know precisely what happened, since chk1123 went ahead and wrote the FixParts data to disk, but:

[quote=chk1123]Sir i do not remember correctly but i think that at time of boot info  script i had deleted my f: partition(using windows disk management) in  hopes that ubuntu would recognise it as unallocated space and install on  it, but when it failed, i created my f: partition back using windows  disk management.Perhaps this can explain the discrepancy.[/quote]

If the partition was re-created with a slightly different size than it originally had between the run of the Boot Info Script and of FixParts, that would certainly explain the discrepancy. Running CHKDSK on the disk, as I suggested in post #23, is advisable in case the filesystem and partition definitions don't quite match.

---

### Post by YesWeCan on 2011-08-26
> **chk1123 said:**
> Sir i do not remember correctly but i think that at time of boot info script i had deleted my f: partition(using windows disk management) in hopes that ubuntu would recognise it as unallocated space and install on it, but when it failed, i created my f: partition back using windows disk management.Perhaps this can explain the discrepancy.
anyway i have already typed w as i stated earlier then successfully booted to windows and tried to install wubi, when the error message comes which i have posted in next(or previous) post, please help with that as well!!
So are you saying that your F: partition is sda2 and that *after *you posted the bootinfoscript results in your first post, you deleted F: and then recreated it and then ran Fixparts? Because if you changed F: before you ran bootinfoscript or if F: is not sda then Fixparts did something naughty.

---

### Post by chk1123 on 2011-08-26
Wubi finally ran successfully!!
When i tried to install it later it did not show the error it had displayed the previous 2 times!
So now i am very happy!!:P:P
THNX ONCE AGAIN TO EVERYONE FOR HELP.:guitar:
I'd say you all are a great bunch of people and great programmers as well.It has convinced me to become a part of linux- in a couple of days i will try to actually install ubuntu using the CD on a seperate partition(s).If all goes well i will close this thread in a couple of days (which is possible only due to supreme the effort by you all).
Till then can anyone tell or suggest links on how to change directories in Terminal? I am still struck on my home folder!:)

---

### Post by oldfred on 2011-08-26
cd /Documents

I cheat whenever the path is long and use Nautilus to drill down, control  -L to get path in copyable mode and copy path after the cd command.

New to Ubuntu? Start here...  Also commands
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://help.ubuntu.com/11.04/index.html](https://help.ubuntu.com/11.04/index.html)

---

### Post by chk1123 on 2011-08-27
Thanks for all the help!!:P:P
Ubuntu is up and running fine..

---

