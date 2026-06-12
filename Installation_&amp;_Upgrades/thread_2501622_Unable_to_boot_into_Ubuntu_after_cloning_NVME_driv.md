---
title: "Unable to boot into Ubuntu after cloning NVME drive with Macrium Reflect"
date: 2024-10-15
forum: Installation &amp; Upgrades
---

### Post by vw16v on 2024-10-15
Hello, I did a quick search and I believe [this is]("https://ubuntuforums.org/showthread.php?t=1688634") the same or similar issue that I'm having after cloning my NVME 512 GB drive to a new 1 TB NVME.

 I used Macrium Reflect to clone it and it seemed to work fine. I included  a screen shot of my Disk Manager. The 161 GB partition is where my  Ubuntu 24.04 resides. I cloned the NVME within Windows 11. I assumed  that it would work based on some quick searches for Macrium Reflect dual  boot. The Macrium Reflect software also saw this partition and cloned  it. However, after I installed the replacement NVME it booted right to  Windows. I confirmed that the BIOS boot order showed Ubuntu as the first  OS. So, I used my USB thumb drive to boot to boot-repair tool. I ran  the boot repair and it said it repaired the Dual boot but also came up  with this message below.
[URL="https://imgur.com/w5LdMKY"]https://imgur.com/w5LdMKY

[/URL][https://imgur.com/C5a2e8q](https://imgur.com/C5a2e8q)
Screen shot of Macrium Reflect showing all partitions including the 161 GB partition where Ubuntu is installed.
[https://imgur.com/qk550gV](https://imgur.com/qk550gV)
Screenshot of disk manager after clone was completed. Looks identical to Original NVME.
[https://imgur.com/U4bdI4N](https://imgur.com/U4bdI4N)

[IMG]https://imgur.com/w5LdMKY[/IMG]
Based on my search results I believe I should attempt to boot off a Ubuntu Live CD and do what is mentioned in the linked post above?
Either do this:
1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,4)", 
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

Or boot off Live CD and restore GRUB via.

sudo grub-install /dev/sda

Thanks for any ideas!

---

### Post by tea for one on 2024-10-15
I wouldn't follow your link from 2011, which refers to an old legacy installation.
You have Windows in UEFI mode and hopefully Ubuntu is also.

Can you boot into Windows10/11?
If so, can you boot into a “Try Ubuntu” live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

---

### Post by oldfred on 2024-10-15
Do you have unique UUIDs & GUIDs. You cannot boot true clone with both drives connected as duplicates not allowed.
Also since to larger drive, often issue where backup gpt partition table is in middle of drive, You can use gdisk to move to end of drive.

lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> I wouldn't follow your link from 2011, which refers to an old legacy installation.
You have Windows in UEFI mode and hopefully Ubuntu is also.

Can you boot into Windows10/11?
If so, can you boot into a “Try Ubuntu” live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

Hi, thanks for your response. Yes, I can boot to Windows 11 fine. That's all I could boot to using the cloned NVME. Even when I manually select Ubuntu using F12 it boots right to Windows. I noticed that was an old thread after I posted this. I'm definitely using UEFI/GPT so that post probably does not apply as you mentioned. 

Just to confirm, I'll need to run Try Ubuntu from a USB thumb Drive correct? The boot repair utility was run off a Linux PEN drive that has multiple Distros on the thumb drive. The boot-repair utility I ran said it saved the results to /var/log/boot-repair/DATE/Boot-info_Date
However, I wasn't sure how I could access this since I can't boot to Ubuntu? I should have emailed that output when I had the Clone installed but I wasn't connected to my network at the time. I probably could have saved it to a text file on my USB drive as well. 

I'm tempted to create a Live Ubuntu USB and then trying to install GRUB that way. I'm still researching this but I want to make sure it will still boot Windows. I just want to be careful since my Original NVME drive is still working correctly and allows me to dual boot. Thanks for any additional ideas! I'm also tempted to try to clone the drive again using Clonezilla since it runs from a USB thumb drive and would clone the NVME when not in Windows.

---

### Post by tea for one on 2024-10-15
> **vw16v said:**
> Yes, I can boot to Windows 11 fine
That's good news
> **vw16v said:**
> Just to confirm, I'll need to run Try Ubuntu from a USB thumb Drive correct? The boot repair utility was run off a Linux PEN drive that has multiple Distros on the thumb drive. The boot-repair utility I ran said it saved the results to /var/log/boot-repair/DATE/Boot-info_Date
That destination /var/log/boot-repair/DATE/Boot-info_Date is the live session not your non-booting installed Ubuntu OS
> **vw16v said:**
> Thanks for any additional ideas! I'm also tempted to try to clone the drive again using Clonezilla since it runs from a USB thumb drive and would clone the NVME when not in Windows.
I wouldn't use Clonezilla to clone Windows because you can already boot there successfully.

Here's a procedure I use to clone Ubuntu
You will need your source disk and target disk attached
Boot into a "Try Ubuntu" live session
Open Gparted
Right click your source Ubuntu partition
Copy to your target Ubuntu partition

Then double check that your ESP contains the Ubuntu folder (the Microsoft folder must be there because you can boot Windows 11)

Happiness will follow......;)

---

### Post by ubfan1 on 2024-10-15
Probably the ...EFI/ubuntu/grub.cfg stub and the maintained /boot/grub/grub.cfg files have the old UUIDs, and the cloaned filesystems got new ones.  Start with getting the UUIDs of all partitions by running sudo blkid in a terminal (take a pic for reference?).  Identify your Ubuntu root's UUID, and confirm that the EFI/ubuntu/grub.cfg files uses that UUID and has the right partition number in the hints (hd?,gpt?).  Edit if necessary to update to the new disk's root UUID. Then check the new /etc/fstab for using the new UUIDs everywhere (root and /boot/efi mount).  Then check the /boot/grub/grub.cfg UUIDs and fix (either just the first boot and rerun update-grub after a successful boot to fix everything, or a blanket edit). That should be a solution to a non-booting disk.  Macrium Reflect is pretty smart about cloaning, allowing resizing in the process, so I'd expect it would not duplicate UUIDs, but the actual files with the old UUIDs will not be changed.

---

### Post by vw16v on 2024-10-15
Thanks for the info @[**[COLOR=#000000]tea for one[/COLOR]**]("https://ubuntuforums.org/member.php?u=585392") and @oldfred. Just to confirm, I removed my original NVME and put in the cloned one in my laptop before trying to dual boot. I can only boot to Windows. I might look into what [**[COLOR=#000000]tea for one[/COLOR]**]("https://ubuntuforums.org/member.php?u=585392") just mentioned mentioned but it's  not exactly clear. I'm assuming I should boot off the Ubuntu Live USB and run gparted and then copy my 162GB partition from Disk0 to Disk1 overwriting the current 162GB on Disk1? 
[https://imgur.com/U4bdI4N](https://imgur.com/U4bdI4N)

I will also look into how to obtain the UUID of my current NVME while I have my original NVME drive installed that allows me to boot to Ubuntu. It should be in /etc/fstab or just running blkid as mentioned. I'm just not sure how I can obtain the UUID of the replacement clone? I'm guessing I can obtain that by re-installing the Cloned NVME and then booting off my Linux Pen drive that has the boot-repair utility installed. Or possibly just booting off a Ubuntu Live CD and trying to obtain the UUID of the cloned NVME that way? Sorry for my confusion but I'm a little rusty. Thanks again for these ideas but it's still not clear to me. I just need to reboot to the Ubuntu I currently have working/installed on my original drive.

---

### Post by vw16v on 2024-10-15
I just booted to my Ubuntu distro on my Original NVME drive.


I'm slightly confused why I have so many "nvme" entries in /dev  ? It looks to be separate partitions where Windows, Linux , etc reside.

I have the following nvme in /dev:
brw-rw----   1 root   disk      259,     0 Oct 15 07:34 nvme0n1
brw-rw----   1 root   disk      259,     1 Oct 15 07:34 nvme0n1p1
brw-rw----   1 root   disk      259,     2 Oct 15 07:34 nvme0n1p2
brw-rw----   1 root   disk      259,     3 Oct 15 07:34 nvme0n1p3
brw-rw----   1 root   disk      259,     4 Oct 15 07:34 nvme0n1p4
brw-rw----   1 root   disk      259,     5 Oct 15 07:34 nvme0n1p5


```
lsblk -d /dev/nvme0*
lsblk: /dev/nvme0: not a block device
NAME      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
nvme0n1   259:0    0 476.9G  0 disk 
nvme0n1p1 259:1    0   260M  0 part /boot/efi
nvme0n1p2 259:2    0    16M  0 part 
nvme0n1p3 259:3    0   314G  0 part 
nvme0n1p4 259:4    0 161.7G  0 part /var/snap/firefox/common/host-hunspell
                                    /
nvme0n1p5 259:5    0  1000M  0 part
``` 


```
sudo fdisk -l 
Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: SAMSUNG MZVLB512HBJQ-000L2              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5DCC9C27-D1C2-4A0A-832F-79FB9021C8F4

```

Based on fdisk -l output below it appears my UUID is 5DCC9C27-D1C2-4A0A-832F-79FB9021C8F4 for /dev/nvme0n1

```
sudo fdisk -l 
Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  659081215 658513920   314G Microsoft basic data
/dev/nvme0n1p4 659081216  998166527 339085312 161.7G Linux filesystem
/dev/nvme0n1p5 998166528 1000214527   2048000  1000M Windows recovery environmen
```


For example,
```
sudo blkid /dev/nvme0n1
/dev/nvme0n1: PTUUID="5dcc9c27-d1c2-4a0a-832f-79fb9021c8f4" PTTYPE="gpt"
```


```
sudo blkid /dev/nvme0n1p1
/dev/nvme0n1p1: LABEL_FATBOOT="SYSTEM_DRV" LABEL="SYSTEM_DRV" UUID="D0E8-205E" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="4c29f2dc-736f-4b76-a238-b3224e258df2"
```

And here's my /etc/fstab output
```
cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=f3409908-cd51-4af4-9735-c5373816ba49 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=D0E8-205E  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw
```

Thanks for any additional input!

---

### Post by tea for one on 2024-10-15
> **vw16v said:**
> I might look into what [**[COLOR=#000000]tea for one[/COLOR]**]("https://ubuntuforums.org/member.php?u=585392") just mentioned mentioned but it's  not exactly clear. I'm assuming I should boot off the Ubuntu Live USB and run gparted and then copy my 162GB partition from Disk0 to Disk1 overwriting the current 162GB on Disk1? 
Yes, that's it. (Disk 0 = Source and Disk 1 = Target)
Gparted will take care of the UUIDs, you do not have to look for them.
Just make sure that your ESP contains the original Ubuntu folder ( I would doubt that Macrium Reflect has damaged/changed it)
You must not reboot with both nvme disks attached because "UUID Clash"

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> Yes, that's it. (Disk 0 = Source and Disk 1 = Target)
Gparted will take care of the UUIDs, you do not have to look for them.
Just make sure that your ESP contains the original Ubuntu folder ( I would doubt that Macrium Reflect has damaged/changed it)
You must not reboot with both nvme disks attached because "UUID Clash"

Ok, so boot off any distro that has gparted installed with my original/dual boot working NVME installed and my Cloned NVME hooked up via my USB-C NVME enclosure and then copy the Linux 162GB on the installed NVME over to the clone NVME on hooked up via USB-C enclosure. Is that correct?
Thanks again!

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> Yes, that's it. (Disk 0 = Source and Disk 1 = Target)
Gparted will take care of the UUIDs, you do not have to look for them.
Just make sure that your ESP contains the original Ubuntu folder ( I would doubt that Macrium Reflect has damaged/changed it)
You must not reboot with both nvme disks attached because "UUID Clash"

Hi tea for one, I just booted into a Linux Mint distro and ran gparted. Here's what I show for the installed/original /dev/nvme0n1 on the 162GB partition.
[https://imgur.com/2VFEc3R](https://imgur.com/2VFEc3R) 

If I right click on choose copy on nvme0n1p4 and then select the drop down and choose my target/cloned NVME I get this option.
[https://imgur.com/MtMzKuX](https://imgur.com/MtMzKuX)

However, I can't delete the current /dev/sd4 that has Linux installed on the Target NVME/Clone drive. I can only resize or move it when right clicking.
Should I paste the source NVME partition directly to the target/Clone NVME? I'm not sure what to do. Thanks again for any help. I'll be sure to give you beans if possible?

---

### Post by tea for one on 2024-10-15
Almost there.
You don't paste nvme0n1p4 into unallocated space.
You paste into sda4 (no need to delete anything, it will replace sda4)

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> Almost there.
You don't paste nvme0n1p4 into unallocated space.
You paste into sda4 (no need to delete anything, it will replace sda4)

:-?, hmm, ok. The only problem is when I copy nvme0n1p4 I can't paste it into /dev/sda4 Target/Clone NVME without selecting the unallocated space. If I right click on nvme0n1p4 and choose copy and then select /dev/sda4 target it does not allow me to paste (It's greyed out). The only way I can appear to paste it is by selecting the unallocated space. Thanks for sticking with me on this. :P

EDIT: I just noticed if I unmount /dev/sd4 I can then paste the nvme0n1p4 to my cloned/NVME. Should I proceed?
[https://imgur.com/gaeIMah](https://imgur.com/gaeIMah)

---

### Post by tea for one on 2024-10-15
The source and target partitions must be unmounted.
In your live session, open a terminal and enter
```
sudo umount -a
```
Edit: I saw your edit after I posted this reply - Please proceed

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> The source and target partitions must be unmounted.
In your live session, open a terminal and enter
```
sudo umount -a
```

Hmm, per my previous screenshot it looks like I could of pasted the source nvme0n1p4 to my target /dev/sda4 where Linux resides without issues.

If I run the command you mentioned I get this.

```
mint@mint:~$ sudo umount -a
umount: /run/user/999: target is busy.
umount: /tmp: target is busy.
umount: /sys/fs/cgroup: target is busy.
umount: /: target is busy.
umount: /cdrom: target is busy.
umount: /run: target is busy.
umount: /dev: target is busy.

```

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> The source and target partitions must be unmounted.
In your live session, open a terminal and enter
```
sudo umount -a
```
Edit: I saw your edit after I posted this reply - Please proceed

Ah, ok. I just noticed your edit. I went ahead and pasted it per your suggestion. I now have the nvme0n1p4  pasted/overwritten to the /dev/sda4.
Do you think If I shut down and then install my Cloned NVME I will be good with GRUB/Dual boot? :-s

---

### Post by tea for one on 2024-10-15
Did you double check that the Ubuntu boot folder is present in your cloned ESP?

---

### Post by vw16v on 2024-10-15
> **tea for one said:**
> Did you double check that the Ubuntu boot folder is present in your cloned ESP?

Yeah, it shows /dev/sda1 in gparted as EFI System Partition with flags boot,esp.
That's the same thing it shows for my original NVME on /dev/nvme0n1 
So, I should be good hopefully?

---

### Post by vw16v on 2024-10-15
Hi tea for one, I installed my NVME Cloned drive after following your suggestions. Unfortunately it's still booting directly to windows. I went ahead and booted off the boot-repair again via USB. Should I attach it to the thread you posted previously or email that you posted on the previous page?

Here's the boot-repair suggestions PRIOR to running the recommended repair.

[https://paste.ubuntu.com/p/3xp5qdNjzs/](https://paste.ubuntu.com/p/3xp5qdNjzs/)

I went ahead and ran the suggested boot repair again. It says it reinstalled GRUB and a few other things. I'm going to see if the 2nd time was a charm? Thanks again for the help.

---

### Post by vw16v on 2024-10-15
FYI, I went ahead and booted to the boot-repair USB drive again and gathered the blkid output as recommended. This is with my cloned/NVME drive installed and my original NVME drive disconnected. Thanks for any other ideas. This is the first time that boot-repair has not worked for me.

```
int@mint:~$ blkid
/dev/nvme0n1p5: BLOCK_SIZE="512" UUID="169818ED9818CCDD" TYPE="ntfs" PARTUUID="64a798c3-252c-49e6-ba79-95e5f4c6a5b1"
/dev/nvme0n1p3: LABEL="Windows-SSD" BLOCK_SIZE="512" UUID="48A2E88AA2E87E36" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e8a7d0b2-0a73-4046-82ca-9d815da05e95"
/dev/nvme0n1p1: LABEL_FATBOOT="SYSTEM_DRV" LABEL="SYSTEM_DRV" UUID="D0E8-205E" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="303a4c17-90b2-4258-a536-590849804b1d"
/dev/nvme0n1p4: UUID="f3409908-cd51-4af4-9735-c5373816ba49" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="99af6c75-dddd-4346-9578-f3df55fe8ebd"
/dev/loop0: TYPE="squashfs"
/dev/dm-0: BLOCK_SIZE="2048" UUID="2023-12-23-05-05-55-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="14eb2669" PTTYPE="dos"
/dev/sda1: LABEL="YUMI" UUID="4E21-0000" BLOCK_SIZE="512" TYPE="exfat" PTTYPE="dos" PARTUUID="ed8fda96-01"

```

Appreciate any other ideas!

---

### Post by vw16v on 2024-10-15
Also, here's a boot summary in case that helps. I'm petty sure it's the same as my other pastebin.

Thanks again.

[https://paste.ubuntu.com/p/dvvzMwDZ9S/](https://paste.ubuntu.com/p/dvvzMwDZ9S/)

---

### Post by oldfred on 2024-10-15
I would still check UUIDs & GUIDs.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint  ,uuid,partuuid
And then UEFI uses partUUID to find ESP to boot from.
sudo efibootmgr -v  #note that older versions needed -v, but now newer versions seems to give too much detail.
And the grub.cfg in ESP has to have uuid of / to find full grub. cfg in your install.
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg
Above works from install only if ESP mounted with defaults, your fstab shows the more secure mount with 0077. So may need to manually mount the ESP in live installer to see files in ESP.

Actually bit easier with Boot-Repair's report as it combines all the necessary info in one report.[/COLOR]

[/FONT]

---

### Post by tea for one on 2024-10-16
Somehow, you seem to have different UUIDs for Windows and Ubuntu

Line 106 - Boot0000* Windows Boot Manager	HD(1,GPT,[COLOR="#0000FF"]303a4c17-90b2-4258-a536-590849804b1d[/COLOR],0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Line 107 - Boot0001* Ubuntu	HD(1,GPT,[COLOR="#FF0000"]4c29f2dc-736f-4b76-a238-b3224e258df2[/COLOR],0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)

Windows boots OK because the UUID is present
Line 206 - &#9500;&#9472;nvme0n1p1 vfat     D0E8-205E                            [COLOR="#0000FF"]303a4c17-90b2-4258-a536-590849804b1d [/COLOR]

Here's an example of a successful dual boot with one ESP and the pertinent UUIDS for Windows and Ubuntu are identical
```
Boot0000* ubuntu	HD(1,GPT,ad1d7958-ab8d-427f-83e0-374660231ec7,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager	HD(1,GPT,ad1d7958-ab8d-427f-83e0-374660231ec7,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
```

What were the boot UUIDs in your original disk?

---

### Post by oldfred on 2024-10-16
You can use efibootmgr to create a correct boot entry, it should overwrite the old one,but check that you do not have two ubuntu entries.
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1
See also
man efibootmgr
Check entries:
sudo efibootmgr -v  # older versions needed -v to see partUUID, but newer version now outputs lots of other data, no -v then works a bit better.

---

### Post by vw16v on 2024-10-16
Thanks a lot for this info oldfred and tea for one!

@oldfred, I'm going to try to determine how I can obtain the partUUID by booting off a live installer and then attempt to mount my Ubuntu if I can figure that out. If I'm able to do that I will provide the output of /boot/efi/EFI/ubuntu/grub.cfg

@tea for one. That's odd that I have two different UUID's for Windows & Ubuntu. I'm not sure how that happened? It might of been when I upgraded from 22.04 to 24.04 recently? 

But my /etc/fstab shows the following info per that pastebin

# / was on /dev/nvme0n1p5 during installation
UUID=f3409908-cd51-4af4-9735-c5373816ba49 /               ext4    errors=remount-ro 0       1 

Per pastebin results this is now an NTFS Windows recovery partition:
nvme0n1p5 998166528 1000214527   2048000  1000M Windows recovery environment

I just downloaded EsayUEFI and this is what it shows. 
Description:Ubuntu
GPT partition GUID:{4C29F2DC-736F-4B76-A238-B3224E258DF2}
Partition number:1
Partition starting sector:2048
Partition ending sector:534527
File path:\EFI\ubuntu\shimx64.efi

Description:Windows Boot Manager
GPT partition GUID:{303A4C17-90B2-4258-A536-590849804B1D}
Partition number:1
Partition starting sector:2048
Partition ending sector:534527
File path:\EFI\Microsoft\Boot\bootmgfw.efi

Basically the same thing as pastebin. It has an option within this software to "Rebuild EFI System Partition"
I think I might give that a try. If it borks it I should just be able to install my original NVME drive back in.

---

### Post by vw16v on 2024-10-16
Hi guys, unfortunately to "Rebuild EFI System Partition" with EsayUEFI did not help. I even tried running boot-repair USB again but same issue. 
Just to confirm, my entries for UUIDs should be Identical for both Ubuntu and Windows correct? I'm hoping I can figure out how to  locate my \EFI\ubuntu\shimx64.efi file from a live boot CD. I might just have to use this drive in an external enclosure instead since I'm in over my head. Thanks

---

### Post by vw16v on 2024-10-16
i guys/oldfred. I booted off my Mint live USB and then I mounted nvme0n1p1 that gparted shows for my EFI system boot partition.

Here's what it shows for the grub.cfg
mint@mint:/mnt/EFI/ubuntu$ cat grub.cfg
search.fs_uuid **f3409908-cd51-4af4-9735-c5373816ba49** root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

Per my pastebin this entry exist on nvme0n1 under "p4" partition 4
&#9500;&#9472;nvme0n1p4 ext4     **f3409908-cd51-4af4-9735-c5373816ba49** 99af6c75-dddd-4346-9578-f3df55fe8ebd

Do you guys think if I change this value to either 4c29f2dc-736f-4b76-a238-b3224e258df2 or 303a4c17-90b2-4258-a536-590849804b1d that it will help load Grub and show both OS's on boot up? 

EDIT: I also connected my original working Dual Boot NVME drive and it shows the same entry>

mint@mint:/mnt/EFI/ubuntu$ cat grub.cfg
search.fs_uuid **f3409908-cd51-4af4-9735-c5373816ba49** root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg



Thanks again for all your help. I can't figure out how to add beans for you guys. Any ideas?

---

### Post by oldfred on 2024-10-16
Your f34... is your UUID for / per Boot-Repair.
Do not mix up UUID and partUUID which is really the GUID that is unique to each gpt partition.

Did you do the efibootmgr entry in post #24. That will put a new Ubuntu entry with correct partUUID.

---

### Post by vw16v on 2024-10-16
> **oldfred said:**
> Your f34... is your UUID for / per Boot-Repair.
Do not mix up UUID and partUUID which is really the GUID that is unique to each gpt partition.

Did you do the efibootmgr entry in post #24. That will put a new Ubuntu entry with correct partUUID.

):P oldfred, I didn't do this command yet because it was not clear to me.
[COLOR=#000000]sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

[/COLOR]If I run this from a Live USB will it add an entry into correct spot? I'm assuming it will since you specified /dev/nvme0n1
Do I need to mount this drive from a live USB first? I currently have my Original NVME drive back in my laptop so I can dual boot. I left all the screws out so I can easily swap back to the clone. I was under the impression if I run this command from a live Mint USB it would add it to the wrong area? Much appreciated!

---

### Post by oldfred on 2024-10-16
That efibootmgr entry creates a new UEFI entry to find shim in the ESP partition specified by -d & -p parameters. If you do not have correct drive installed it will use the incorrect drive.
Since you have correct boot files & folder in ESP a new UEFI entry should work.

Otherwise you can use Boot-Repair to do a total grub reinstall from its advanced mode. You choose drive (which has an ESP) and an install. Grub then uses a similar ( or same?) command to add UEFI entry & adds the /Ubuntu folder with UEFI boot & grub's files that are in ESP. Rest of grub is in your install.

---

### Post by vw16v on 2024-10-16
Great! Thanks for this info oldfred! I'm going to work on this some more tomorrow. I'd really like to get this working instead of having to use my original 512 GB drive and the 1 TB Samsung EVO in an external enclosure.

---

### Post by tea for one on 2024-10-17
If you are feeling adventurous, you could try this:-
Insert your [COLOR="#0000FF"]cloned[/COLOR] disk into the PC
Boot into a "Try Ubuntu" live session
Open a terminal
```
efibootmgr
```
Delete all entries 
Or just delete the Ubuntu entry
```
sudo efibootmgr -b 000X -B (X = Boot Number)
sudo efibootmgr -b 0001 -B # example
```
If you have deleted all entries, you should see a message "No BootOrder is set; firmware will attempt recovery"
When you reboot, the UEFI firmware will re-populate efibootmgr
Hopefully, it may allow Ubuntu to boot?

Edit: You may also have to organise the OS priority in your PC boot menu
I reckon Windows will be in pole position

---

### Post by vw16v on 2024-10-17
Hi oldfred and tea for one. I just tried what oldfred suggested from my Mint Live USB. When I ran the command this is what came back.

```
root@mint:/home/mint# efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1
efibootmgr: ** Warning ** : Boot0001 has same label Ubuntu
BootCurrent: 0019
Timeout: 0 seconds
BootOrder: 0002,0001,0000,0019,0015,0014,0016,0017,0018,001A
Boot0000* Windows Boot Manager
Boot0001* Ubuntu
Boot0010  Setup
Boot0011  Boot Menu
Boot0012  Diagnostic Splash
Boot0013  UEFI Diagnostics
Boot0014* USB CD:
Boot0015* USB FDD:
Boot0016* NVMe: Samsung SSD 990 EVO 1TB                
Boot0017* ATA HDD:
Boot0018* ATA HDD1:
Boot0019* USB HDD: Generic USB Device
Boot001A* PCI LAN:
Boot0002* Ubuntu

```

I'm assuming I wont get the GRUB menu based on this output. I'll give it a shot a see what happens. If not I might try what tea for one suggest. I'll report back shortly. Thanks

---

### Post by vw16v on 2024-10-17
Hi guys! I'm happy to report that after running the command oldfred suggested I now have GRUB!! I have two Ubuntu entries but that's not a big deal. One of them says Ubuntu 24.04 and then the top one that oldfred had me create is Ubuntu. I can't thank both of you enough! This was challenging but with your support I should be up and running now on my 1 TB NMVE! I just need to confirm I can still boot to Winblows and then hopefully re-enable bitlocker. It's guys like you that make the Ubuntu OS and community and awesome place!
:guitar:

---

### Post by vw16v on 2024-10-17
Hey guys, one other quick question. Do you think it's safe to delete one of these Ubuntu GRUB entries using the free trail I have EasyUEFI? If so, do you know which one it would be off hand?

Description:Ubuntu
GPT partition GUID:{303A4C17-90B2-4258-A536-590849804B1D}
Partition number:1
Partition starting sector:2048
Partition ending sector:534527
File path:\EFI\ubuntu\shimx64.efi

Description:Ubuntu
GPT partition GUID:{4C29F2DC-736F-4B76-A238-B3224E258DF2}
Partition number:1
Partition starting sector:2048
Partition ending sector:534527
File path:\EFI\ubuntu\shimx64.efi

I'm in Windows now and performing some test but everything seems good as of right now! :D

---

### Post by tea for one on 2024-10-17
> **vw16v said:**
> Hey guys, one other quick question. Do you think it's safe to delete one of these Ubuntu GRUB entries using the free trail I have EasyUEFI? If so, do you know which one it would be off hand?
The incorrect one is 4C29F2DC-736F-4B76-A238-B3224E258DF2
If you refer back to post 23, you will see that it is the non-booting Ubuntu entry

Admirable perseverance on your part, it's nice to read about a successful outcome.

---

### Post by vw16v on 2024-10-17
> **tea for one said:**
> The incorrect one is 4C29F2DC-736F-4B76-A238-B3224E258DF2
If you refer back to post 23, you will see that it is the non-booting Ubuntu entry

Admirable perseverance on your part, it's nice to read about a successful outcome.

Thanks again tea for one! I'll probably remove that one after some more testing. What's surprising is this drive benchmarks much faster! My laptop is supposed to be limited to PCIe Gen 3 but somehow I'm getting PCIe Gen 4 speeds! I wasn't expecting that bonus. It's quite a bit faster than the stock drive. Thanks for sticking with me on this one guys. I seriously appreciate it and happiness did follow! \\:D/

---

