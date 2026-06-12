---
title: "Ubuntu Installation on Fake Raid-Help"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by rajeshs4454 on 2011-05-18
-       When i tried Ubuntu 11.01 Live DVD it was not detecting my Raid 0  Drive [500GB]                                              detecting only my Back up hard disk [Sata ]

-        I cant find Raid driver from GIgabyte Website 

-        So , is there any way to config my Raid 0  on Ubuntu  11.04    or latest ? 

--**Config**
> AMD Phenom II X6 1055T ,Benq G2220HD 22 ,GIGABYTE GA-880GM-UD2H ,COOLER  MASTER Elite 310 ,CORSAIR 2GB 240-Pin DDR3 X3 , FSP Saga II 500 W HD  5750  ,Raid 0 [250G+500G=500G Raid 0]    , HD 2 Sata 500GB  [Backup H.D]
--After searching i did find many users have problem with fake Raid 

**Current OS**
> ATM i am using Win 7 64 bit on partition 1   , I want to install Ubuntu 64 bit on my Raid 0  Drive partition 2 
[note *i CANT install ubuntu on my backup h.d *]
> I cant Buy Raid Card just for Linux

-SO please advice me how to make Ubuntu Installer or wubi installer detect my Raid 0   array so i  can install 

**WUBI**
-When using wubi  after reboot i am getting error unable to detect  image

[IMG]http://img843.imageshack.us/img843/5129/ubuntuwubi.jpg[/IMG]
[IMG]http://img829.imageshack.us/img829/3373/wubidrive.jpg[/IMG]

---

### Post by rajeshs4454 on 2011-05-19
so no reply means there is no way in ubuntu to install on my Fake Raid 0  Array Partition 2 ?

---

### Post by Quackers on 2011-05-20
Boot to the live cd/usb desktop (try ubuntu) then install the kpartx package with synaptic package manager.
Open gparted and it should now show your raid array as dev/mapper/xxxxxxxxxxxx or whatever. 
In gparted create and format your new partitions for Ubuntu including swap space (not exceeding the maximum of 4 primary partitions on an MBR partitioned disc).
Start the installer from the desktop icon.
At the partitioning screen choose "something else".
Choose the partition(s) you just created and give them appropriate mount points ( / for root and /home for home etc) BUT DO NOT check the box to format them again or the installation will likely fail!
At the bottom of that screen change the "location for bootloader installation" from the default /dev/sda to your raid array, /dev/mapper/xxxxxxx, whatever.
Install should now proceed - hopefully :-)

---

### Post by rajeshs4454 on 2011-05-20
> **Quackers said:**
> Boot to the live cd/usb desktop (try ubuntu) then install the kpartx package with synaptic package manager.
Open gparted and it should now show your raid array as dev/mapper/xxxxxxxxxxxx or whatever. 
In gparted create and format your new partitions for Ubuntu including swap space (not exceeding the maximum of 4 primary partitions on an MBR partitioned disc).
Start the installer from the desktop icon.
At the partitioning screen choose "something else".
Choose the partition(s) you just created and give them appropriate mount points ( / for root and /home for home etc) BUT DO NOT check the box to format them again or the installation will likely fail!
At the bottom of that screen change the "location for bootloader installation" from the default /dev/sda to your raid array, /dev/mapper/xxxxxxx, whatever.
Install should now proceed - hopefully :-)

i booted  Ubuntu 11.04   Live CD >installed Kpartx

opened Gparted

/dev/sda       232.88GB                     [My HD.1  250GB   (1 of the H.D in Raid 0 Array )
/dev/sdb       465.76GB                     [My W.D   500GB  Back Up hard disk ]
/dev/sdc       465.76GB                     [My H.D2  500GB   ( 2nd H.D in Raid 0 Array)
/dev/sdd       7.45GB  


pls advice , even after installation of kpart  Raid array is not showing

[img]http://s4.postimage.org/7mmjrlure/Screenshot.png[/img]

---

### Post by linuxinstalledfromhdd on 2011-05-20
You will have to research this on google for a couple of days while everyone can take a look at your details.

---

### Post by Quackers on 2011-05-20
Hmm, I see you have a 250GB drive and a 500GB drive in raid0. That should give a /dev/mapper raid array of approx 500GB.
What does the Disk Utility show please?

And I am presuming that dmraid is installed?

---

### Post by rajeshs4454 on 2011-05-20
> **Quackers said:**
> Hmm, I see you have a 250GB drive and a 500GB drive in raid0. That should give a /dev/mapper raid array of approx 500GB.
What does the Disk Utility show please?

And I am presuming that dmraid is installed?



Disk  Utlity

[IMG]http://s2.postimage.org/a406cb2uy/diskutlity.png[/IMG]



is it due to lack of driver it showing running in non Raid mode?
DMraid 

Yes installed

[IMG]http://s2.postimage.org/a407zufcq/dmraid.png[/IMG]

extra note :  Mdadm is also installed

---

### Post by Quackers on 2011-05-20
No output for disk utility is shown.
If you look in your raid setup (in bios) is it showing the raid array as "normal"? Not degraded or failed is it?

---

### Post by rajeshs4454 on 2011-05-20
> **Quackers said:**
> No output for disk utility is shown.
If you look in your raid setup (in bios) is it showing the raid array as "normal"? Not degraded or failed is it?


attached pic 


edit

> **Quackers said:**
> No output for disk utility is shown.
If you look in your raid setup (in bios) is it showing the raid array as "normal"? Not degraded or failed is it?


Dont know why it wasnt showing pic , even for me in Windows it wasnt showing image attached with img tag

but on ubuntu it is showing , i will use attach feature





[IMG]http://s3.postimage.org/lpregyog2/Raid_f.jpg[/IMG]

---

### Post by Quackers on 2011-05-20
I don't really understand your setup.
On the one hand it says you are using non-raid-5 and on the other hand it appears to say you have one disc in raid0. Obviously you can't have just one disc in raid0. That would be pointless.
If you press ctrl + F at boot do the raid member discs show up? They do on mine when pressing ctrl + I during boot.

---

### Post by rajeshs4454 on 2011-05-20
> **Quackers said:**
> I don't really understand your setup.
On the one hand it says you are using non-raid-5 and on the other hand it appears to say you have one disc in raid0. Obviously you can't have just one disc in raid0. That would be pointless.
If you press ctrl + F at boot do the raid member discs show up? They do on mine when pressing ctrl + I during boot.


Ctrl I is not working


attached controller config 
View LD Def Menu
View drive assignment menu SS
and Disk manager SS in windows  showing partition and free spaces

Note Ubuntu is saying its in Non Raid 5  But actually i am using Raid 0  , dk why ubuntu is saying so

---

### Post by Quackers on 2011-05-20
I think ctrl + I only works with Intel raid (like mine).
You do have 2 discs in the raid0 array, as you stated.
It is a different setup from mine so am unfamiliar with it.
If you open up a terminal in the live desktop and run ```
ls -l /dev/mapper/
``` is there any output?

---

### Post by Quackers on 2011-05-20
Nice duplicate post.

---

### Post by rajeshs4454 on 2011-05-20
> ubuntu@ubuntu:~$ ls -l /dev/mapper/
total 0
crw------- 1 root root 10, 236 2011-05-20 18:51 control
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

Thank u

---

### Post by Quackers on 2011-05-20
Oh my, that's not what I expected to see :-)
Unfortunately as your setup is so different from my own I'm afraid that I will be of no help to you.
Do not despair! There are several people on here who have much greater "fakeraid" experience than I do :-)  Hang in there!

---

### Post by rajeshs4454 on 2011-05-20
> **Quackers said:**
> Oh my, that's not what I expected to see :-)
Unfortunately as your setup is so different from my own I'm afraid that I will be of no help to you.
Do not despair! There are several people on here who have much greater "fakeraid" experience than I do :-)  Hang in there!


ok , i will wait for others 

 thank you   vm for sparing ur valuable time and  looking into my case deeply 

Thank u

---

### Post by Quackers on 2011-05-20
Not a problem, you're welcome.
Hopefully somebody with more know-how will come along and help you :-)

---

### Post by rajeshs4454 on 2011-05-22
bumb 

~48 hrs+ ~

---

### Post by Pumalite on 2011-05-22
> **rajeshs4454 said:**
> so no reply means there is no way in ubuntu to install on my Fake Raid 0  Array Partition 2 ?


[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by rajeshs4454 on 2011-05-22
> **Pumalite said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
Link 1
```
https://help.ubuntu.com/community/FakeRaidHowto
```This Thread shows how to config Software RAID 

it also says
> 
 That said, linux software raid is more robust and better supported and  thus, recommended over fakeraid if you **do not need to dual boot with  Windows. **[B]  I do need to duel boot 

```
http://ubuntuforums.org/showthread.php?t=630644
```[/B]
after step 2 i getting following error instead of displaying partitions

> 
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdc: pdc, "pdc_cfdcdcdjb", stripe, ok, 486328064 sectors, data@ 0
ubntu@ubuntu:~$ 


it should b showing less than 400GB   cause i alrdy have Win installed on 115 GB Partition so (490GB - 115 GB )


> 

Link 4```
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
```**Not Found**

 The requested URL /wiki/SATA_RAID_Howto was not found on this server.


---

