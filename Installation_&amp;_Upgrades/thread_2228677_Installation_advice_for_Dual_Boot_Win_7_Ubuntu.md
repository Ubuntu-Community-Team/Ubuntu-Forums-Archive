---
title: "Installation advice for Dual Boot Win 7/ Ubuntu"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by kim3 on 2014-06-08
I am keen to install the recent new Ubuntu LTS alongside the Windows 7 OS on my 120GB SSD. I attempted the same thing when I put the desktop together last year, but became muddled due to the UEFI settings.

Can someone please run me through the safest, most simple way of achieving my aim?

Should I/ Must I put Ubuntu on the SSD? Or can it be placed on the 1Tb seagate HD?

---

### Post by ronb19495 on 2014-06-08
If you have a 1tb hard drive as well as ssd you can put ubuntu on there is windows 7 installed in uefi mode
first off if you are installing on hd format hard drive to gpt then from gparted on instalation disk partition your hard drive first partition 300 mb boot efi,second partition ext4 /root partition 3rd partition swap then reboot install the 300 mb boot partition has to be formatted fat 32

---

### Post by ronb19495 on 2014-06-08
heres a screenshot of gparted and ubuntu installed on ssd

---

### Post by Easy Limits on 2014-06-08
I would and have put Ubuntu on my SSD and put Win 7 on my spinning drive.  Install Win 7 first then Ubuntu.

---

### Post by kim3 on 2014-06-08
Too late for that, Mr Easy! I already have Win 7 running fine and dandy from the SSD. Since it is slower and I will use it often, I thought best to chuck it on the faster SSD. Unless you folks think it is for the best to wipe the damn thing clean and start all over?

If not...I am keen on having the dual boot option with Ubuntu. If it can be done with Ubuntu on the Seagate then great. 

'[COLOR=#000000]first off if you are installing on hd format hard drive to gpt then from gparted on instalation disk partition your hard drive first partition 300 mb boot efi,second partition ext4 /root partition 3rd partition swap then reboot install the 300 mb boot partition has to be formatted fat 32'

So..

Back-up my files already on the HD. Use gparted to format then re-assign partitions as follows-
1st partition 300MB boot efi
2nd partition ext4 /root 
3rd partition swap

How large should the ext4/ partition be? and the swap?

And what do you mean by 'install the 300mb boot partition has to be formatted fat 32'?

[/COLOR]

---

### Post by oldfred on 2014-06-09
The issue is your Windows 7. The default install with a DVD is BIOS with MBR partitions. You have to copy DVD to flash drive and do a couple of updates to make Windows 7 install in UEFI mode. And how you boot installer for both Ubuntu & Windows is how it installs.

Both Windows & Ubuntu only boot in BIOS mode from MBR(msdos) partitioned drives.
Windows only boots in UEFI mode from gpt partitioned drives.
Ubuntu can boot in either UEFI if efi partition or BIOS if you have a bios_grub partition with gpt partitioning.

So how drives are partitioned and how Windows is installed matters. I suggest gpt for any drive that will be Linux only as then you can have either UEFI or BIOS. But you really should install Ubuntu in the same boot mode as your Windows is or will be. If not in same boot mode you can only boot from UEFI menu (not grub) and may have to turn on or off UEFI or BIOS/CSM in UEFI/BIOS menu. Some auto switch and allow booting from one time boot key.

Slightly more detailed suggestion.
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[URL="http://ubuntuforums.org/showthread.php?t=2021534"]http://ubuntuforums.org/showthread.php?t=2021534

[/URL] GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

[URL="http://ubuntuforums.org/showthread.php?t=2021534"]
[/URL]

---

### Post by kim3 on 2014-06-09
Many thanks for such a detailed explanation, oldfred.

I installed Windows 7 myself from DVD so it is not installed with UEFI. The UEFI menu options appeared when I installed ubuntu onto the SSD AFTER putting windows 7 there when I put the PC together last year. Problems appeared, which were fixed up with a repair option, but still I was heading through a menu at boot which was not our dear friend The Grub.

So I need to format the 1TB seagate, then use gparted to create the partitions. I wish to have a partition for my documents, music, films etc. How much should I have for Ubuntu system files? And with 8gb of ram and i5 processor, do I need a swap, if so, what size?

And how do I ensure that Ubuntu installs in the MBR format as Windows 7 has?

---

### Post by dangerfirebob on 2014-06-09
Hi, I installed Ubuntu Studio on a Lenovo Thinkpad with 4 gb of ram and gave it 2 gb for the swap which is sufficient I believe, (I don't plan to hibernate) after installing Windows 7 I setup my bios to boot from cd and then use my g-parted partition manager live cd  to shrink my Windows partition sufficiently then I made a 100 gb ntfs partition named /D  for comunication between the fresh install of Windows 7 and my desired version of Ubuntu Studio. That is where documents, music and films can go. I installed Ubuntu Studio from a live dvd on a 30gb ext4 partition leaving Windows 7  on its 250gb ntfs partition (sda1) please note I did this by using the option "somthing else" from the Ubuntu installation dialogue NOT "install alongside windows" or "replace everything", In the Ubuntu live cd partition manager the only modification necessary was to mark my ext4 partition as "/" and set the 2gb partition as swap. That worked perfectly... Untill... I am only learning now about efi and uefi and here's what happened:

It all continued to work perfectly for a month, the laptop is not mine and belongs to a busy mother of three who lets her children play with all the games I installed for them, that  = chaos, plus the pc dropped in the past but the only apparent damage was a failing keyboard wich turned out to be a manufacture defect and easily fixed by insulating the cable. Now Windows does NOT load anymore (Blue Screen), warning:  mbr-cylinders-not-equal-bios-cylinders, I updated the bios and managed to get into the recovery mode and then ran out of time and had to give the laptop back to its owners, at least they can still enjoy Ubuntu :) and maybe Windows 7 will return, my question is:

Is it possible that this problem is caused by uefi/efi incompatabilty (I have not had the chance to check that yet) or is it a hardware issue caused by bad sectors on the hard drive? Why did it work perfectly for a month and then stop working? it may have undergone some stress and no defragmentation but the owners have no internet and will have installed nothing new. Would what seemed to be a perfect dual boot setup fail after time due to the uefi and efi. I will have another chance to fix it in a months time and any input ideas about this would be really helpful. I have much older laptops with dual and triple boots with Windows XP that work fine but the uefi/efi issue does not apply to them as they are pre 2010 so please let me know its not really a problem to start over, but this is the second time dual boot setup failed on this Lenovo Thinkpad, the first time  some one else did it giving a 100gb partition to Ubuntu 13.04. shortly after that Windows died irretrievably! Should I start looking for a new replacement hard disc drive for the kids?

---

### Post by oldfred on 2014-06-09
If you install Ubuntu in UEFI mode over a Windows install in BIOS mode, drive gets converted to gpt and Windows will not work. It has to be installed in UEFI mode to work from a gpt drive.

How you boot installer is how it installs for both Windows & Ubuntu. UEFI should have two choices for flash drive. One is clearly UEFI and the other is not usually clear but is not UEFI then. Often just name or label on flash drive shown.

My suggestion on swap is the same as dangerfirebob or about 2GB, just to have a little. Some with 8GB or more of RAM may suggest you do not need swap. Others suggest 8GiB (not GB) so you can hibernate. But system boots so fast there is no need for hibernation anyway.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If system is UEFI capable, and you are booting Windows from a MBR drive, I would still partition all other drives as gpt. Ubuntu can boot in BIOS mode from gpt partitioned drive and if you have the efi partition you can later easily convert or experiment with UEFI. It is difficult to change a drive to gpt and add an efi partition at the beginning of a drive when it has lots of data.

        
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

When dual booting with XP I originally had a shared NTFS data partition. But then as I phased out XP, I started putting new data in a shared (with other Ubuntu installs) Linux formatted partition. I create folders in partition and link folders into /home. 

      
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by dangerfirebob on 2014-06-09
Thank you for the links oldfred, it looks very likely that my friends laptop win7 installation has become unstable due to the UEFI and gpt issue. Now I will have to just wait a month to see for sure, on the bright side that's plenty of time to study the correct setup and get it right next time. Splitting the home directory looks like interesting reading too.

---

### Post by kim3 on 2014-06-10
Which version of ubuntu do I use? The 64 bit version or 32bit?

I checked my bios...if I enter set-up the first menu I reach is titled-
'gigabyte - UEFI Dual Bios'

Does this help decide my next step in terms of installing Ubuntu onto the HD?

---

### Post by oldfred on 2014-06-10
Only the 64bit is UEFI capable. And from your UEFI/BIOS menu you should then see two boot options of flash drive. One should say UEFI or efi and the other perhaps just flash drive name or label. Sometimes not clear.
But how you boot flash drive is how it will install.
And how you install Windows BIOS or UEFI,  is how you should install Ubuntu.

With new hardware there really is no reason for the 32 bit full Ubuntu version. Any system so old to require 32bit version will not run Unity both RAM and video chip/card and needs Lubuntu. 

If installing in UEFI mode:
Be sure to review links in my signature, particularly the first two as they include many screen shots and other info.

---

