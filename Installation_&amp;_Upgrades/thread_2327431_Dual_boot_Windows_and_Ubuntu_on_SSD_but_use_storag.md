---
title: "Dual boot Windows and Ubuntu on SSD but use storage HDD separately?"
date: 2016-06-10
forum: Installation &amp; Upgrades
---

### Post by cblnchat on 2016-06-10
Hey there,

I haven't used Linux as a main OS for a few years now and I'd like to get back to it.
I'm tinkering with my Chromebook trying to get linux on it, but that's more of a side project.

My current main setup is I have Windows on an SSD and I use a hard drive for storage and such. 

My question is, can I dual boot Windows and Ubuntu on the SSD but use the same HDD for storage without formatting it? 

I've never had a two drive setup like this before so I'm not sure how to go about it.

Thanks!

---

### Post by oldfred on 2016-06-10
Sure, there are a couple of ways.
You can have /home on HDD or keep /home on SSD inside / (root) and mount data partition(s) with your data.

Some just put /home on HDD with system on SSD. But the user settings are on HDD, but they really are mostly small files. 
The /home is easier to set up as you can do that during install and ownership & permissions are automatically set.

Bit more advanced as you cannot normally do it during install is the separate /mnt/data partition. That partition can be NTFS or Linux. I has both a /mnt/data as ext4 and a /mnt/shared as NTFS back when I still had XP. I then moved Firefox & Thunderbird profiles into my NTFS shared data so all installs had same Firefox and could read new e-mails immediately without having to reboot. 

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Is system UEFI or BIOS? You just want to be sure to install in same boot mode as Windows.
Use Windows tools to shrink the NTFS partition and reboot immediately so it can run chkdsk and update itself to its new size.
Do not shrink Windows too much, it really likes 30% free. At 10% free it will be extremely slow and it may take forever to do a defrag.

Do use Something Else to install whether UEFI or BIOS. If UEFI more info in link in my signature below.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by cblnchat on 2016-06-10
> **oldfred said:**
> Sure, there are a couple of ways.

Is system UEFI or BIOS? You just want to be sure to install in same boot mode as Windows.
Use Windows tools to shrink the NTFS partition and reboot immediately so it can run chkdsk and update itself to its new size.
Do not shrink Windows too much, it really likes 30% free. At 10% free it will be extremely slow and it may take forever to do a defrag.


I'm sure it's a UEFI cause it's a Win 10 PC.

So I would be shrinking the NTFS partition of the SSD?

Would the shared data on the storage HDD just cooperate?

I guess after a few years of not using Ubuntu I'm more rusty than I thought. 
This seems quite over my head.

I'll do some more reading of the posts you linked to make sure I understand what is going on.

---

### Post by yancek on 2016-06-11
If you have windows on the SSD already, use the Disk Management tool in windows to shrink the partition to make unallocated space for your Ubuntu.
Make sure you boot and install Ubuntu UEFI if your windows is UEFI.
Your data partitions on the hard drive need to be FAT32 or ntfs formatted since windows is incapable of reading a Linux filesystem much less writing to it.

---

### Post by ubfan1 on 2016-06-11
And your storage hdd should have "basic" partitions, not "dynamic" since Ubuntu can't read those (they are a type of logical volume I guess).

---

### Post by cblnchat on 2016-06-11
> **ubfan1 said:**
> And your storage hdd should have "basic" partitions, not "dynamic" since Ubuntu can't read those (they are a type of logical volume I guess).

So just to be clear, I don't want to mess something up. 

I have to resize the SSD partition for Ubuntu, I can do this. I also have to resize the partition for my storage HDD to a filesystem that Ubuntu can read?

I'm a bit confused about the steps I take during the actual installation to make sure that the OS stays on the SSD and put everything else on the HDD.

I feel real dumb, but it's just been so long since I've worked with Ubuntu

---

### Post by oldfred on 2016-06-11
I normally partition in advance and then use Something Else. Otherwise any autoinstall may randomly install somewhere that you do not want.
I experimented once. I had 4 drives with some unallocated space on most of them, and the autoinstall, just found the largest unallocated space and split it between / & swap.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

If primarily a Windows user, you can use NTFS as your shared data partition. But you cannot use NTFS for any Linux system partition such as /home.
But I would probably make / (root) a bit larger as default location of where data is saved is the folders in /home.

---

### Post by cblnchat on 2016-06-12
> **oldfred said:**
> I normally partition in advance and then use Something Else. Otherwise any autoinstall may randomly install somewhere that you do not want.
I experimented once. I had 4 drives with some unallocated space on most of them, and the autoinstall, just found the largest unallocated space and split it between / & swap.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

If primarily a Windows user, you can use NTFS as your shared data partition. But you cannot use NTFS for any Linux system partition such as /home.
But I would probably make / (root) a bit larger as default location of where data is saved is the folders in /home.

Thank you for the help. 

I seem to have made a mistake somewhere along the way though. I've managed to boot into Ubuntu, but it boots by default straight into Windows. I'm not sure what I skipped. Or how to fix it.

Also to be clear, because I don't have much space on the SSD, if I install applications and such and download things from browser, do they go straight to the HDD I use for storage?

---

### Post by oldfred on 2016-06-12
Unless you put /home on HDD, Ubuntu will store info in /home.
As mentioned above on splitting /home, I have all normal folders in my data partition and linked back to /home on SSD. Then system looks like normal system, but data is actually saved to HDD.

What brand/model system.
Can you use UEFI one time boot key like f10 or f12 and choose Ubuntu entry?

       May be best to see details, you can add this to live installer:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by cblnchat on 2016-06-12
> **oldfred said:**
> Unless you put /home on HDD, Ubuntu will store info in /home.
As mentioned above on splitting /home, I have all normal folders in my data partition and linked back to /home on SSD. Then system looks like normal system, but data is actually saved to HDD.

What brand/model system.
Can you use UEFI one time boot key like f10 or f12 and choose Ubuntu entry?

       May be best to see details, you can add this to live installer:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I did put /home on HDD, so there's no other steps I have to do to make sure things get stored on the HDD?

I actually completely forgot about linking the folders back to /home on the SSD while I was installing.

I have a Toshiba Satellite C855D, f10 didn't do anything. I'll give f12 a shot.

What I'm doing to get back to Ubuntu is inserting my bootable usb and hitting escape on the prompt when it boots into that and then typing exit into grub and then I'll get an option to choose what drive to boot into and THEN a choice from Windows, ubuntu and Ubuntu. 

It's very odd.

EDIT: f12 got me into it. But not directly. I still had to choose my SSD and then pick from those three choices. I pick the upper case Ubuntu and then a grub menu comes up for a few seconds and goes away and I boot into Ubuntu

---

### Post by oldfred on 2016-06-12
I think Toshiba is now like Sony & HP.
They modify UEFI to use description. And you can only use the correct description to boot. And of course that description is "Windows Boot Manager". If only booting ubuntu we change description. But dual booting also has a fallback or hard drive boot entry: /EFI/Boot/bootx64.efi. That is same path and name used on external drives and installers for both Windows & Ubuntu (but different actual files).
At the end of the Boot-Repair Summary report is another option where you edit Windows BCD. But then you are booting into Windows & then booting Ubuntu.

Boot-Repair now auto copies shim to be /EFI/Boot/bootx64.efi if you use advanced mode and its "Use standard efi files" option.
If you already have an UEFI hard drive boot entry that should then boot grub/shim/ubuntu. If not we can add one.

       Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
            Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

---

### Post by ubfan1 on 2016-06-12
I think the C855 is old enough to avoid those boot loader name problems. But it might be old enough to have a firmware problem, what is the firmware release number?  (6.60 ? I think or later is good)  The two level selection, sdd, then Ubuntu in the subsequent window is normal.  What order does the efibootmgr -v   output show, reorder if shim/grub is not first.

---

### Post by cblnchat on 2016-06-12
> **ubfan1 said:**
> I think the C855 is old enough to avoid those boot loader name problems. But it might be old enough to have a firmware problem, what is the firmware release number?  (6.60 ? I think or later is good)  The two level selection, sdd, then Ubuntu in the subsequent window is normal.  What order does the efibootmgr -v   output show, reorder if shim/grub is not first.

I don't think grub comes first, but I've never needed to run this particular command before so I don't know what exactly I'm looking for.

```

cody@cody-Satellite-C855D:~$ efibootmgr -v output show
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0004,0005,0000,2003,2001,2002
Boot0000* Ubuntu    HD(1,GPT,0000e243-7a80-1f58-895c-d10186c40100,0x800,0x81800)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0001* Windows Boot Manager    HD(1,GPT,3ea4a0d5-6cc2-11e2-b5b0-bdabb930c0c9,0x1000,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-33-D1-CB)     PciRoot(0x0)/Pci(0x4,0x0)/Pci(0x0,0x0)/MAC(008cfa33d1cb,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-33-D1-CB)     PciRoot(0x0)/Pci(0x4,0x0)/Pci(0x0,0x0)/MAC(008cfa33d1cb,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)RC
Boot0004* Windows Boot Manager    HD(1,GPT,0000e243-7a80-1f58-895c-d10186c40100,0x800,0x81800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0005* ubuntu    HD(1,GPT,0000e243-7a80-1f58-895c-d10186c40100,0x800,0x81800)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

I don't know the firmware number also.

---

### Post by oldfred on 2016-06-12
You show 0004 first and one of the ubuntu entries second.
You normally get two ubuntu entries, one is shim and the other grub. Shim is for Secure boot but works with secure boot off.

Did you reinstall Windows as you have a Windows entry 0001 that does not match the others.

You can reset order with efibootmgr, or you should be able to do that inside your UEFI.

       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 5,4

  
You can also delete the obsolete Windows entry, 0001:

 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by cblnchat on 2016-06-15
> **oldfred said:**
> You show 0004 first and one of the ubuntu entries second.
You normally get two ubuntu entries, one is shim and the other grub. Shim is for Secure boot but works with secure boot off.

Did you reinstall Windows as you have a Windows entry 0001 that does not match the others.

You can reset order with efibootmgr, or you should be able to do that inside your UEFI.

       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 5,4

  
You can also delete the obsolete Windows entry, 0001:

 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)


I did reinstall Windows a while back, that's pretty awesome you could tell that. Was it just the fact that there were two there that showed I had reinstalled Windows?

Just out of curiosity, why did that command take all the other numbers out of the boot order?

```

cody@cody-Satellite-C855D:~$ sudo efibootmgr -b 0001 -B
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0004,0005,0000,2003,2001,2002
Boot0000* Ubuntu
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-33-D1-CB) 
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-33-D1-CB) 
Boot0004* Windows Boot Manager
Boot0005* ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
cody@cody-Satellite-C855D:~$ sudo efibootmgr -o 5,4
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0005,0004
Boot0000* Ubuntu
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-33-D1-CB) 
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-33-D1-CB) 
Boot0004* Windows Boot Manager
Boot0005* ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network

```
 
Do the others just not matter?


Also thank you very much for the help. I'm working on getting all my knowledge of Linux back, it left me in only a few short years.

---

### Post by oldfred on 2016-06-15
If you want them in the boot order that is ok, just add as many as you want.

But very few of us would ever use a network boot, and if both Ubuntu & Windows would not boot, you still should be able to use the one time boot key to choose other entries, but USB might be one to add. It just is the only default entries are now in boot order.

The one Windows entry had a different GUID that was inconsistent with both Windows and Ubuntu's UEFI entries. So that looked like an old install. UEFI NVRAM remembers entries, but if you disconnect a drive it forgets all of them.  Some will find them again in the ESP on several reboots, others may need efibootmgr to add specific boot entries.

Always best to have a Windows repair flash drive or installer with repair console and your Ubuntu live installer to use as a repair tool if needed.

---

### Post by cblnchat on 2016-06-16
I usually keep a Ubuntu live installer with me just in case something goes wrong, but I've never heard of a Windows repair flash drive. I should look into that.

Again thank you for the help!

---

