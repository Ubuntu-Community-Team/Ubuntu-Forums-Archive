---
title: "removing one of three linux distros without screwing up other OS's"
date: 2019-05-06
forum: Installation &amp; Upgrades
---

### Post by svoomaz on 2019-05-06
I currently have 2 separate computers each running 3 different distro's each + windows 8.
This was simply done to try out many variants.
I'm done kicking the tires and want to reduce both systems to 2 distro's + windows 8.

I've found tons of articles/help if I wanted to get rid of the dual boot - but I don't want to eliminate dual boot.
I want to eliminate (1) distro on each computer and give that space to the other OS's without hosing the currently installed distro's + windows. 
So far I've found nothing helpful on what I'm trying to do.

1st a little more info. I set up common documents & media partitions on a 2nd drive in ntfs so I can share with all OS's. All fstab edits are done works great. I also set up 3 separate linux home partitions no problems there. The goal was to keep the SSD's with just the OS's (and boot/esp).

I learned the hard way that simply deleting one partition with 1 distro hosed everything else as the uuid's changed, (I'm still recovering from that debacle).
**My current plan is to delete files from the distro's I don't want to keep & resize the partitions leaving a token 10-20MB (or less) and reallocating the space to the other OS's partitions.**
The reason I don't want to reinstall the last 2 distro's standing the time spent getting them just like I want. I don't think it matters, but the 2 distro's I'm keeping are Xubuntu for me and Mint for other remote family members. 

So, that's my plan. Let me know if it's the right way to go? Does it look like it will work without having to reinstall any OS's?
Please let me know what you really experienced guy's think.

Thank,Scott

**The Fu**
Text from df -Th & lsblk
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     798M  1.8M  796M   1% /run
/dev/sdc7      ext4       51G   17G   32G  35% /
tmpfs          tmpfs     3.9G   55M  3.9G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop1     squashfs  4.2M  4.2M     0 100% /snap/gnome-calculator/406
/dev/loop2     squashfs  203M  203M     0 100% /snap/vlc/768
/dev/loop3     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/77
/dev/loop4     squashfs   91M   91M     0 100% /snap/mkvtoolnix-jz/31
/dev/loop5     squashfs  175M  175M     0 100% /snap/inkscape/4693
/dev/loop7     squashfs   15M   15M     0 100% /snap/gnome-characters/206
/dev/loop6     squashfs   80M   80M     0 100% /snap/matroska-tools/19
/dev/loop8     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/70
/dev/loop11    squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/61
/dev/loop10    squashfs   51M   51M     0 100% /snap/p7zip-desktop/163
/dev/loop12    squashfs   15M   15M     0 100% /snap/gnome-characters/254
/dev/loop9     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/78
/dev/loop13    squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/82
/dev/loop14    squashfs  175M  175M     0 100% /snap/inkscape/4690
/dev/loop17    squashfs  144M  144M     0 100% /snap/gnome-3-28-1804/23
/dev/loop15    squashfs  196M  196M     0 100% /snap/vlc/555
/dev/loop19    squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop21    squashfs  154M  154M     0 100% /snap/chromium/691
/dev/loop22    squashfs  139M  139M     0 100% /snap/thunderbird/29
/dev/loop20    squashfs   90M   90M     0 100% /snap/core/6818
/dev/loop25    squashfs   90M   90M     0 100% /snap/core/6673
/dev/loop24    squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop26    squashfs  152M  152M     0 100% /snap/gnome-3-28-1804/36
/dev/loop30    squashfs  172M  172M     0 100% /snap/inkscape/4435
/dev/loop29    squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop27    squashfs   36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop28    squashfs  155M  155M     0 100% /snap/chromium/698
/dev/loop31    squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/57
/dev/loop33    squashfs  203M  203M     0 100% /snap/vlc/770
/dev/loop34    squashfs   54M   54M     0 100% /snap/core18/941
/dev/loop36    squashfs  4.2M  4.2M     0 100% /snap/gnome-calculator/352
/dev/loop35    squashfs   35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop37    squashfs   92M   92M     0 100% /snap/core/6531
/dev/loop38    squashfs   54M   54M     0 100% /snap/core18/782
/dev/loop39    squashfs   91M   91M     0 100% /snap/mkvtoolnix-jz/30
/dev/loop40    squashfs   54M   54M     0 100% /snap/core18/731
/dev/sda2      fuseblk    72G   29G   43G  40% /media/scott/HP_Docs
/dev/sda5      fuseblk   625G  573G   52G  92% /media/scott/HP_Media
/dev/sdb8      ext4       49G   11G   36G  24% /home
tmpfs          tmpfs     798M   24K  798M   1% /run/user/1000
/dev/loop41    squashfs   15M   15M     0 100% /snap/gnome-characters/258
/dev/loop42    squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/81
/dev/loop43    squashfs  152M  152M     0 100% /snap/gnome-3-28-1804/40
/dev/loop44    squashfs   91M   91M     0 100% /snap/mkvtoolnix-jz/58
/dev/loop45    squashfs  155M  155M     0 100% /snap/chromium/705
scott@xxxxxx:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0     7:0    0 140.7M  1 loop /snap/gnome-3-26-1604/74
loop1     7:1    0     4M  1 loop /snap/gnome-calculator/406
loop2     7:2    0 202.6M  1 loop /snap/vlc/768
loop3     7:3    0   3.7M  1 loop /snap/gnome-system-monitor/77
loop4     7:4    0  90.3M  1 loop /snap/mkvtoolnix-jz/31
loop5     7:5    0 174.3M  1 loop /snap/inkscape/4693
loop6     7:6    0  79.6M  1 loop /snap/matroska-tools/19
loop7     7:7    0  14.8M  1 loop /snap/gnome-characters/206
loop8     7:8    0   3.7M  1 loop /snap/gnome-system-monitor/70
loop9     7:9    0 140.7M  1 loop /snap/gnome-3-26-1604/78
loop10    7:10   0  50.7M  1 loop /snap/p7zip-desktop/163
loop11    7:11   0  1008K  1 loop /snap/gnome-logs/61
loop12    7:12   0  14.8M  1 loop /snap/gnome-characters/254
loop13    7:13   0 140.7M  1 loop /snap/gnome-3-26-1604/82
loop14    7:14   0 174.3M  1 loop /snap/inkscape/4690
loop15    7:15   0 195.2M  1 loop /snap/vlc/555
loop17    7:17   0 143.5M  1 loop /snap/gnome-3-28-1804/23
loop19    7:19   0  34.6M  1 loop /snap/gtk-common-themes/818
loop20    7:20   0  89.4M  1 loop /snap/core/6818
loop21    7:21   0 153.8M  1 loop /snap/chromium/691
loop22    7:22   0 138.3M  1 loop /snap/thunderbird/29
loop24    7:24   0   2.3M  1 loop /snap/gnome-calculator/260
loop25    7:25   0  89.3M  1 loop /snap/core/6673
loop26    7:26   0   151M  1 loop /snap/gnome-3-28-1804/36
loop27    7:27   0  35.3M  1 loop /snap/gtk-common-themes/1198
loop28    7:28   0 154.6M  1 loop /snap/chromium/698
loop29    7:29   0  14.5M  1 loop /snap/gnome-logs/45
loop30    7:30   0 171.8M  1 loop /snap/inkscape/4435
loop31    7:31   0  1008K  1 loop /snap/gnome-logs/57
loop33    7:33   0 202.3M  1 loop /snap/vlc/770
loop34    7:34   0  53.7M  1 loop /snap/core18/941
loop35    7:35   0  34.8M  1 loop /snap/gtk-common-themes/1122
loop36    7:36   0     4M  1 loop /snap/gnome-calculator/352
loop37    7:37   0  91.1M  1 loop /snap/core/6531
loop38    7:38   0  53.7M  1 loop /snap/core18/782
loop39    7:39   0  90.3M  1 loop /snap/mkvtoolnix-jz/30
loop40    7:40   0  53.7M  1 loop /snap/core18/731
loop41    7:41   0  14.8M  1 loop /snap/gnome-characters/258
loop42    7:42   0   3.7M  1 loop /snap/gnome-system-monitor/81
loop43    7:43   0   151M  1 loop /snap/gnome-3-28-1804/40
loop44    7:44   0  90.3M  1 loop /snap/mkvtoolnix-jz/58
loop45    7:45   0 154.6M  1 loop /snap/chromium/705
sda       8:0    0 698.7G  0 disk 
&#9500;&#9472;sda1    8:1    0     1K  0 part 
&#9500;&#9472;sda2    8:2    0  71.2G  0 part /media/scott/HP_Docs
&#9492;&#9472;sda5    8:5    0 624.2G  0 part /media/scott/HP_Media
sdb       8:16   0 465.8G  0 disk 
&#9500;&#9472;sdb1    8:17   0   350M  0 part 
&#9500;&#9472;sdb2    8:18   0    20G  0 part 
&#9500;&#9472;sdb3    8:19   0  16.2G  0 part 
&#9500;&#9472;sdb4    8:20   0     1K  0 part 
&#9500;&#9472;sdb5    8:21   0    60G  0 part 
&#9500;&#9472;sdb6    8:22   0    60G  0 part 
&#9500;&#9472;sdb7    8:23   0    50G  0 part 
&#9500;&#9472;sdb8    8:24   0    50G  0 part /home
&#9500;&#9472;sdb9    8:25   0    50G  0 part 
&#9500;&#9472;sdb10   8:26   0    50G  0 part 
&#9492;&#9472;sdb11   8:27   0 109.2G  0 part 
sdc       8:32   0 465.8G  0 disk 
&#9500;&#9472;sdc1    8:33   0   157G  0 part 
&#9500;&#9472;sdc2    8:34   0    32G  0 part [SWAP]
&#9500;&#9472;sdc3    8:35   0     1K  0 part 
&#9500;&#9472;sdc5    8:37   0     1G  0 part 
&#9500;&#9472;sdc6    8:38   0    56G  0 part 
&#9500;&#9472;sdc7    8:39   0    52G  0 part /
&#9500;&#9472;sdc8    8:40   0    49G  0 part 
&#9492;&#9472;sdc9    8:41   0 118.7G  0 part 
sdd       8:48   1   968M  0 disk 
sr0      11:0    1  1024M  0 rom  

#Output above is direct copy - I know there's a ridiculous amount of Loops - but I haven't read anything that says this is bad - if I misunderstood - let me know.
Also, it's the interaction of the boot, root, mbr/esp, etc that isn't clear to me - I think I actually understand partitions/partitioning pretty well.

**Old Fred**, thanks for the response but these are bios installs and Disk-Repair needed EFI

---

### Post by TheFu on 2019-05-06
```
df -Th 
lsblk
```
commands and output please, use code tags like I did.
Next to each LV or partition, say which you want gone.

No images, please.  Never images. Text.

First step is to remove the partitions/LVs that you don't need anymore.  If you don't use LVM, then using gparted.  If you are using LVM, we need to see **pvs**, **vgs**, and **lvs** output too. Please.  With code tags so everything looks the same here as it does in a terminal window - correct columns.

Lastly, whenever people screw around with their partitioning and don't 100% understand what they are doing, it is highly likely they will make a mistake and delete something important.  That means before you do anything, please, please, please, make a backup of everything you don't want to lose that you know can be restored.  

If all these requests seem too hard, you can install **boot-repair** and run the "boot-info" button to provide us with a URL. This will contain everything we need, and more, to help.  If you go this way, just post the URL it generates.

---

### Post by oldfred on 2019-05-06
You need to know which system is default boot. Normally last installed system has its grub in MBR or if UEFI as /EFI/ubuntu/grub.cfg in ESP. 
You can reinstall grub from inside you main working install to MBR if BIOS.

If you want to know all details & document current configuration:
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

