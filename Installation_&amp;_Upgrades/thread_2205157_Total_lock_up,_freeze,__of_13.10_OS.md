---
title: "Total lock up, freeze,  of 13.10 OS"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by philromford-q on 2014-02-12
I only installed 13.10 a few days ago and was helped to overcome the booting up problem. However, now that it is working I find that the OS will freeze in two stages: first; all running applications halt but the mouse will still move the cursor, without any resulting action. Second; the cursor freezes, now the system is totally locked and can only be sorted with a hard reset.

This has happened three times so far; once when saving files in Rawtherpee, twice when using Firefox and entering ebay items. I will keep on with it to see if there is any kind of pattern to this. In the meantime, could there be a hardware problem that is causing this. When I was previously running Ubuntu 10.xx on the same machine, it never failed, however, the one hardware change since then has been to replace the video card. I had Windows trouble caused by the old video card, but never any Windows trouble with the new card - this may of course, be irrelevant to Ubuntu.

Can anyone advise please.

Thanks

---

### Post by sudodus on 2014-02-12
Please specify your computer and operating system, it makes it easier to give relevant advice,

Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Did you replace Ubuntu 10.xx with a fresh install of 13.10. Which flavour (standard Ubuntu, Lubuntu, Xubuntu or Kubuntu)?

Finally, please post the output of the following commands

```
sudo parted -l
```

and

```
df
```

---

### Post by philromford-q on 2014-02-13
I will send all the details tomorrow once I've identified the exact video card etc. In the meantime I have installed Ubuntu 12.04 LTS since this is known to be stable. The 13.10 version I installed is plain Ubuntu and was a fresh install on a hard disk that has not been used for Linux before.

Thank you.

---

### Post by sudodus on 2014-02-13
On the other hand, if Ubuntu 12.04 LTS is working well, there is no reason to install something else

- unless you like to tamper with bleeding edge software - and in that case I suggest that you keep 12.04 LTS as your production system and install Trusty Tahr (to become 14.04 LTS in April) in another partition or in a virtual machine.

---

### Post by philromford-q on 2014-02-13
Yes, I installed 12.04 after reading about 13.10 instability on another thread. It may now be academic regarding my problem with 13.10, however, it would still be of interest to know whether it is my machine causing it to crash.

Since 12.04 is working - so far, so good - I suppose I may as well uninstall 13.10. How do I do that please?

My PC:-

Home build PC comprising:
ASUS A8V-E motherboard
Hard disk 1 - 320GB Windows XP and Ubuntu 12.04
Hard 2 - 80GB NTFS partition and Ubuntu 13.10
CPU: AMD Athlon 64 3200+
RAM: 2.6GB
Video: Gainward NVIDIA Geforce 210
WiFi: on board chip. The motherboard has a VIA chipset. I am not using the WiFi facility.

13.10  was an install on a disk that had not been used for Linux previously.  Likewise disk 1 had not been used for Linux. In short, not replacing an  old installation.

The terminal outputs are:-
  	 	 	 	   [FONT=Loma]phil@phil-desktop:~$ sudo parted -l [/FONT] 
 [FONT=Loma][sudo] password for phil: [/FONT] 
 [FONT=Loma]Model: ATA WDC WD800BB-00FR (scsi) [/FONT] 
 [FONT=Loma]Disk /dev/sda: 80.0GB [/FONT] 
 [FONT=Loma]Sector size (logical/physical): 512B/512B [/FONT] 
 [FONT=Loma]Partition Table: msdos [/FONT] 
 

 [FONT=Loma]Number  Start   End     Size    Type      File system     Flags [/FONT] 
  [FONT=Loma]1      32.3kB  59.0GB  59.0GB  primary   ntfs            boot [/FONT] 
  [FONT=Loma]2      59.0GB  80.0GB  21.0GB  extended [/FONT] 
  [FONT=Loma]5      59.0GB  77.3GB  18.3GB  logical   ext4 [/FONT] 
  [FONT=Loma]6      77.3GB  80.0GB  2681MB  logical   linux-swap(v1) [/FONT] 
 

 

 [FONT=Loma]Model: ATA ST3320310CS (scsi) [/FONT] 
 [FONT=Loma]Disk /dev/sdb: 320GB [/FONT] 
 [FONT=Loma]Sector size (logical/physical): 512B/512B [/FONT] 
 [FONT=Loma]Partition Table: msdos [/FONT] 
 

 [FONT=Loma]Number  Start   End    Size    Type      File system     Flags [/FONT] 
  [FONT=Loma]1      32.3kB  219GB  219GB   primary   ntfs            boot [/FONT] 
  [FONT=Loma]2      219GB   320GB  101GB   extended [/FONT] 
  [FONT=Loma]5      219GB   317GB  98.1GB  logical   ext4 [/FONT] 
  [FONT=Loma]6      317GB   320GB  2681MB  logical   linux-swap(v1) [/FONT] 
 

 

 

 [FONT=Loma]phil@phil-desktop:~$ df [/FONT] 
 [FONT=Loma]Filesystem     1K-blocks     Used Available Use% Mounted on [/FONT] 
 [FONT=Loma]/dev/sdb5       94149508  4454792  84889136   5% / [/FONT] 
 [FONT=Loma]udev             1272592        4   1272588   1% /dev [/FONT] 
 [FONT=Loma]tmpfs             512868      972    511896   1% /run [/FONT] 
 [FONT=Loma]none                5120        0      5120   0% /run/lock [/FONT] 
 [FONT=Loma]none             1282160      148   1282012   1% /run/shm [/FONT] 
 [FONT=Loma]/dev/sdb1      214167402 45460880 168706523  22% /media/WINXP [/FONT] 
  
Thank you.


    
    
    
    <style type="text/css">P { margin-bottom: 0.21cm; }</style>


<p style="margin-bottom: 0cm"><font face="Loma">phil@phil-desktop:~$
sudo parted -l </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">[sudo] password for
phil: </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Model: ATA WDC
WD800BB-00FR (scsi) </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Disk /dev/sda: 80.0GB
</font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Sector size
(logical/physical): 512B/512B </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Partition Table:
msdos </font>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Number  Start   End  
  Size    Type      File system     Flags </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">1      32.3kB 
59.0GB  59.0GB  primary   ntfs            boot </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">2      59.0GB 
80.0GB  21.0GB  extended </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">5      59.0GB 
77.3GB  18.3GB  logical   ext4 </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">6      77.3GB 
80.0GB  2681MB  logical   linux-swap(v1) </font>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Model: ATA
ST3320310CS (scsi) </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Disk /dev/sdb: 320GB </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Sector size
(logical/physical): 512B/512B </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Partition Table:
msdos </font>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Number  Start   End  
 Size    Type      File system     Flags </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">1      32.3kB  219GB
 219GB   primary   ntfs            boot </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">2      219GB   320GB
 101GB   extended </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">5      219GB   317GB
 98.1GB  logical   ext4 </font>
</p>
<p style="margin-bottom: 0cm"> <font face="Loma">6      317GB   320GB
 2681MB  logical   linux-swap(v1) </font>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><br>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">phil@phil-desktop:~$
df </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">Filesystem    
1K-blocks     Used Available Use% Mounted on </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">/dev/sdb5      
94149508  4454792  84889136   5% / </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">udev            
1272592        4   1272588   1% /dev </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">tmpfs            
512868      972    511896   1% /run </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">none               
5120        0      5120   0% /run/lock </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">none            
1282160      148   1282012   1% /run/shm </font>
</p>
<p style="margin-bottom: 0cm"><font face="Loma">/dev/sdb1     
214167402 45460880 168706523  22% /media/WINXP </font>
</p>

<br>Thank you.<br><br>

---

### Post by philromford-q on 2014-02-13
Here we go:-

Home build PC comprising:
ASUS A8V-E motherboard
Hard disk 1 - 320GB Windows XP and Ubuntu 12.04
Hard 2 - 80GB NTFS partition and Ubuntu 13.10
CPU: AMD Athlon 64 3200+
RAM: 2.6GB
Video: Gainward NVIDIA Geforce 210
WiFi: on board chip. The motherboard has a VIA chipset. I am not using the WiFi facility.

13.10  was an install on a disk that had not been used for Linux previously.  Likewise disk 1 had not been used for Linux. In short, not replacing an  old installation.

The terminal outputs are:-
                        [FONT=Loma]phil@phil-desktop:~$ sudo parted -l [/FONT] 
 [FONT=Loma][sudo] password for phil: [/FONT] 
 [FONT=Loma]Model: ATA WDC WD800BB-00FR (scsi) [/FONT] 
 [FONT=Loma]Disk /dev/sda: 80.0GB [/FONT] 
 [FONT=Loma]Sector size (logical/physical): 512B/512B [/FONT] 
 [FONT=Loma]Partition Table: msdos [/FONT] 
 

 [FONT=Loma]Number  Start   End     Size    Type      File system     Flags [/FONT] 
  [FONT=Loma]1      32.3kB  59.0GB  59.0GB  primary   ntfs            boot [/FONT] 
  [FONT=Loma]2      59.0GB  80.0GB  21.0GB  extended [/FONT] 
  [FONT=Loma]5      59.0GB  77.3GB  18.3GB  logical   ext4 [/FONT] 
  [FONT=Loma]6      77.3GB  80.0GB  2681MB  logical   linux-swap(v1) [/FONT] 
 

 

 [FONT=Loma]Model: ATA ST3320310CS (scsi) [/FONT] 
 [FONT=Loma]Disk /dev/sdb: 320GB [/FONT] 
 [FONT=Loma]Sector size (logical/physical): 512B/512B [/FONT] 
 [FONT=Loma]Partition Table: msdos [/FONT] 
 

 [FONT=Loma]Number  Start   End    Size    Type      File system     Flags [/FONT] 
  [FONT=Loma]1      32.3kB  219GB  219GB   primary   ntfs            boot [/FONT] 
  [FONT=Loma]2      219GB   320GB  101GB   extended [/FONT] 
  [FONT=Loma]5      219GB   317GB  98.1GB  logical   ext4 [/FONT] 
  [FONT=Loma]6      317GB   320GB  2681MB  logical   linux-swap(v1) [/FONT] 
 

 

 

 [FONT=Loma]phil@phil-desktop:~$ df [/FONT] 
 [FONT=Loma]Filesystem     1K-blocks     Used Available Use% Mounted on [/FONT] 
 [FONT=Loma]/dev/sdb5       94149508  4454792  84889136   5% / [/FONT] 
 [FONT=Loma]udev             1272592        4   1272588   1% /dev [/FONT] 
 [FONT=Loma]tmpfs             512868      972    511896   1% /run [/FONT] 
 [FONT=Loma]none                5120        0      5120   0% /run/lock [/FONT] 
 [FONT=Loma]none             1282160      148   1282012   1% /run/shm [/FONT] 
 [FONT=Loma]/dev/sdb1      214167402 45460880 168706523  22% /media/WINXP [/FONT] 
  
Thank you.

---

### Post by frank18 on 2014-02-13
I run 13.10 and don't have no problems on my Lenovo Intel I5,but i only run Ubuntu 13.10 by itself, you should give up Xp win since there is no more support and if you like win get Win7 then use Virtual-box to install Ubuntu 13.10 inside win7, 
i also will be not surprised if the cause of your problems are not caused by winxp!

---

### Post by ubfan1 on 2014-02-13
I started seeing things liike this on a fresh 13.10 install on an older HP with Nvidia Geforce 6150 video.  Sometimes there is a crash, and the dump points to the Nvidia driver, which is 304.88.  I am going to try the 304.108 driver to see if that helps.  Never had any problems of this sort with the 12.04 release.

---

### Post by philromford-q on 2014-02-13
The aim is to dump XP on this machine, since as you say XP is no longer supported. Once I am sure that 12.04 LTS is as stable as it is said to be, I shall then dump XP. This machine doesn't have the horsepower to run Win 7, so that is not an option.

---

### Post by philromford-q on 2014-02-13
Yes it could be the video card, once I know how to get at the logs, I can perhaps find out. Being very new to Ubuntu I have a great deal to learn. In the meantime, I'm running 12.04 LTS which so far is fine. I'll probably stick with this until 13.10 is declared LTS.

I still want to know what causes the crash though!

---

### Post by ubfan1 on 2014-02-13
I did try the 304.108 nvidia driver, same crash, so that was no help.  I can live with the problem though, so guess I'll upgrade to 14.04 when it's out rather than drop back to 12.04.

---

### Post by sudodus on 2014-02-14
> **philromford-q said:**
> Yes it could be the video card, once I know how to get at the logs, I can perhaps find out. Being very new to Ubuntu I have a great deal to learn. In the meantime, I'm running 12.04 LTS which so far is fine. I'll probably stick with this until 13.10 is declared LTS.

I still want to know what causes the crash though!

13.10 will never be declared LTS. Its lifetime is only 9 months. The next version, Trusty Tahr, will be released as 14.04 LTS in April (and will get long time support (which is the meaning of the acronym LTS). But there might be another problem. Support for some hardware is dropped along the road to new versions, that are made to support new hardware. For this reason it is a good idea to run an ageing but well supported LTS release like Ubuntu 12.04.

---

