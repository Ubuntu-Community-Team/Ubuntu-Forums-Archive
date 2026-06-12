---
title: "Tribooting Ubuntu 10.10 with Windows 7 &amp; XP, I'm almost there..."
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-04-23
I can dual boot no problem once I install either version of Windows before Ubuntu, but installing two versions of Windows first and then Ubuntu didn't work out quite how I had planned.

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2350    18876343+   7  HPFS/NTFS
/dev/sda2            2873       31080   226580760   83  Linux
/dev/sda3           31081       38914    62920749+   5  Extended
/dev/sda4            2351        2872     4192256   82  Linux swap / Solaris
/dev/sda5           31081       35911    38804976    7  HPFS/NTFS
/dev/sda6           35912       36955     8385898+   7  HPFS/NTFS
/dev/sda7           36956       38914    15729664   83  Linux

Partition table entries are not in disk order
```I first installed Windows 7 on an 18gb partition, then Windows XP on an 8gb partition and on rebooting I was slightly dismayed to find it booted right into XP rather than giving me a choice. 

Hoping the installation of Ubuntu 10.10 and Grub would fix this I proceeded to install Ubuntu's / on a 15gb partition and point /home at a prexisting 225gb filesystem.

On restarting Ubuntu did give me a choice, but only between itself and Windows 7. I am able to access the Windows XP 8gb filesystem to confirm it is still there from here in Ubuntu, so can I make Grub give me the option on boot?

---

### Post by oldfred on 2011-04-23
You seem to only have one windows in a primary partition. That will work only as long as you keep the one in the primary partition sda1.

If XP is in the logical it can be made to boot from grub. if it is win7 it will only boot thru the win install in the primary partition. 

To get each MS to have its own boot loader make a second [COLOR=Red]primary [/COLOR]partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Way to boot windows in extended logical partition with lilo's MBR post#5
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)
Create small FAT Primary to boot windows in logical
[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

meierfra. Repair 2 windows installs to get each to be able to have grub entries XP & Win7 or Vista
[http://ubuntuforums.org/showthread.php?t=1362297](http://ubuntuforums.org/showthread.php?t=1362297)
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)
Edit the Vista or Win7 boot loader
Fix the XP bootsector.
Add Vista to "menu.lst"
Move the boot files from XP to Vista

---

### Post by Dáire Fagan on 2011-04-23
Okay, please correct me if I am wrong, but from my understanding I need to create two primary partitions, one for each version of Windows.

I install XP first on partition one, and then after turning off the bootflag on it using Gparted I proceed to install Windows 7 on the second partition. 

Curiously, would it be possible to do this so that the Windows 7 partition is the C:/ and XP D:/ even though XP is being installed first? This is only a preference because when I am forced to use Windows it will mainly be Windows 7 and this makes more sense to me.

I also understand that I can then just install Ubuntu 10.10 a separate logical partition which along with a 4gbps swap is off a single extended.

If all that makes sense great, but there is more to consider.

Please have a look at the attached screenshot below before reading further so you can have an idea of how things will stand when I delete all partitions I am able to, leaving only my current /home filesystem, which contains media and personal documents etc. Please note I am unable to back this up and understand the risks of proceeding without doing so.

I would like to split the drive into 6 partitions, namely: Ubuntu / system 'UBUNTU' (EXT4 15gb), Ubuntu /home 'HOME' (unsure 5/10gb, planning on storing media and even .wine on the partition 'Storage'), swap 4gbs, 'WINDOWS XP' ( MBT E:\ 8gb NTFS), 'WINDOWS 7' (MBT C:\ 18gbs, again storing C:/Program Files, C:/ProgramData, users and possibly page file and temp on the partition 'Storage' using symlinks and registry tweaks), 'Storage'  (MBT D:\ NTFS all media Program Files, ProgramData etc from 'WINDOWS 7' and possible 'WINDOWS XP')  

I would like to gradually shrink my current /home dir right down to make it as I have mentioned above, gradually migrating data over and shrinking 60gbs or so a time.

Considering I cannot yet delete my current /home (although I would like to as I think it may be a primary?), can you tell me if it is possible to partition the disk as I have outlined, and also how to do so, should I start tonight by moving the large home partition in the screenshot to the end of the disk, or maybe the end of the disk leaving some space for my 'Storage' parition which can then start growing... ?

All input appreciated.

---

### Post by oldfred on 2011-04-23
When you install the second windows, you have to have the boot flag on that partition. If you have it formated & flagged, win7 will install to one partition, otherwise it will want two, one 100MB boot/recovery partition. Your windows do seem a little small, but I have not installed windows for ages. Windows NTFS likes lots of free space to work well - 20 to 30% free is best.

If installed separately, both or each will be c: when booted into it and other NTFS partitions it sees will be d:, e: etc. Not sure if there is any other way.

Moving nearly full partitions can be a slow process, you seem to understand there is risk with any partitioning and should have good backups.

When I upgraded to 64bit I had to do a clean install and have been sold on that ever since. But at that time I had a new drive so I had room to play. I created a 100GB partition for /home and moved everything to it. But then I decided I really wanted a /data and moved just data and then /home was only 1GB which is 3/4 .wine with Picasa. For a while I had a 100GB partition with 1GB used, but now that is several / partitions for testing.

I now just leave /home inside my / (root) and mount the data partitions into each new install with a script since I found I was doing the same configuration over & over (partly because I clean install alpha beta, RC (if one) and final). I just saved history and converted it to a bash file. I only copy some settings from /home as I do not customize a lot.

---

### Post by Dáire Fagan on 2011-04-23
> **oldfred said:**
> When you install the second windows, you have to  have the boot flag on that partition. If you have it formated &  flagged, win7 will install to one partition, otherwise it will want two,  one 100MB boot/recovery partition. Your windows do seem a little small,  but I have not installed windows for ages. Windows NTFS likes lots of  free space to work well - 20 to 30% free is best.

> **dusf said:**
> I install XP first on partition one, and then after  turning off the bootflag on it using Gparted I proceed to install  Windows 7 on the second partition. 


Would not that cover making the second install, Windows 7, be the only primary Windows on with the bootflag on? :)

Yes they are small, but if you consider that all media and Program Files etc will be stored on the Storage Partition?

> **oldfred said:**
> If installed separately, both or each will be c: when booted into it and  other NTFS partitions it sees will be d:, e: etc. Not sure if there is  any other way.

I have read Windows 7 will always call its own partition C:\ whenever booted into, even if it's not the first one, but are you certain XP does that?

> **oldfred said:**
> Moving nearly full partitions can be a slow process, you seem to  understand there is risk with any partitioning and should have good  backups.

I know it's risky, but I really don't have the option to back up right now. It's not anything like 25% risky though, right? Probably 1 in 100?

> **oldfred said:**
> When I upgraded to 64bit I had to do a clean install and have been sold  on that ever since.

Yeah, that was the initial reasons I split the drive into a / and /home partition, now I'm trying to do the same with Windows 7 ;)

So saying I accept the risks of moving the mostly full partition, where do I being? Can you tell if it is a primary from the screenshot of fdisk output on my previous post? If so should I move it to the end, or have my new 'Storage' NTFS at the end, and my current /home next to it as to make it easy to increase the former as I migrate data from the latter?

Would the Storage NTFS have to be a primary for any reason, maybe if the current /home was at the end it wouldn't have to be?

What about the other partitions etc?

---

### Post by oldfred on 2011-04-23
Not sure about XP. I just wanted to make it clear that just turning off boot flag is not the same as turning it on. I have seen drives with no boot flags and with multiple boot flags which should not even happen.

Your partition is sda2 and sda1 thru sda4 are the primary partitions, one primary becomes the extended to hold the logicals. Windows reads logical NTFS just fine.

---

### Post by Dáire Fagan on 2011-04-23
> **oldfred said:**
> Not sure about XP. I just wanted to make it clear that just turning off boot flag is not the same as turning it on. I have seen drives with no boot flags and with multiple boot flags which should not even happen.


Thanks. 

I know I said I would install XP first and then 7, but does it matter which goes first once I turn off the boot flag on the first install?

Other than that the plan is to:



[LIST=1]
[*]Reduce SDA2 to 200gb, keep it for now as the /home partition and move it to the end of the drive.
[*]8gb NTFS primary Windows XP partition at the start.
[*]18gb NTFS primary Windows 7 partition next.
[*]74gb extended partition last with =>
[/LIST]

[LIST]
[*]= > 15gb EXT logical Ubuntu system ( / ) partition.
[*]= > 4gb logical SWAP.
[*]= > 55gb NTFS logical Storage partition.
[/LIST]

Over time I plan to move media etc from the 200gb SDA2 to Storage, decreasing SDA2 and increasing Storage in size as I do so that when it is just a small /home partition I will back it up on Storage, delete it, and create a new logical /home partition.

This would leave me a free primary partition for the future, who knows, Mac OS? :)

Does the above sound possible and correct? Does it matter which order the primary partitions are in, and does it help the SWAP will be next to the Ubuntu filesystem?

One more thing, someone just suggested I put /boot on another logical partition:

> 00:05 < lelle> btw i think you should have /boot on seperate partition if you want to reinstall/remove ubuntu partition and not needing to manually edit the 
               grub new config..

This sounds like a good idea, but wouldn't reinstalling, or removing and reinstalling Ubuntu on ( / ) partition just overwrite grub with exactly what was there before?

If you think a separate logical /boot partition is a good idea, how much of the 15gb should I allocate it? 

Sorry, I know I am asking a lot of questions.

---

### Post by oldfred on 2011-04-23
I do not believe in separate /boot. It makes standard desktops more complex. You may only need a /boot if you have an old computer that can only boot from the first 137GB, RAID or LVM and even then not always.

I had a separate /boot for all of 5 minutes (literally) and then converted to a grub only partition back when we booted with grub legacy & I was chainbooting. Like you said if you reinstall Ubuntu,  grub2 gets reinstalled.

---

### Post by Dáire Fagan on 2011-04-24
Thanks for all your help:)

Managed to get it set up like this:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
/dev/sda1               1        1305    10482381    7  HPFS/NTFS
/dev/sda2   *        1306        3263    15727635    7  HPFS/NTFS
/dev/sda3            3264       12805    76646084+   5  Extended
/dev/sda4           12806       38913   209712510   83  Linux
/dev/sda5            3264        3295      257008+  83  Linux
/dev/sda6            3296        3426     1052226   83  Linux
/dev/sda7            3427        3948     4192933+  82  Linux swap / Solaris
/dev/sda8            3949        5906    15727603+  83  Linux
/dev/sda9            5907       12805    55416186    7  HPFS/NTFS

Disk /dev/sdb: 1015 MB, 1015021568 bytes
/dev/sdb1   ?      398636      983425  2283019262   72  Unknown
/dev/sdb2   ?       86419     1078237  3872056480   65  Novell Netware 386
/dev/sdb3   ?      957932     1949749  3872056384   79  Unknown
/dev/sdb4   ?     1478321     1478349      110998    d  Unknown

```

Win XP, Win7, /boot, /opt, SWAP, /, Storage, /Home.

Although, I don't really understand what the Novell Netware and sdb partitions are about, could be my empty 4 in 1 memory card reader.

---

