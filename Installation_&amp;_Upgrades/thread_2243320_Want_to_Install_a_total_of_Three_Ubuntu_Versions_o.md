---
title: "Want to Install a total of Three Ubuntu Versions on Laptop"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by webusr1 on 2014-09-07
All,
I currently have Windows 7, and Lubuntu 14.04 installed on my Dell Vostro 13 laptop (Celeron, 4GB RAM. 250GB Hard Drive). A few years I had to resort to Xubuntu 13.10 because Ubuntu 12.04 (with Unity) was extremely slow on this hardware. Today, I would like to install Xubuntu 14.04 and KUbuntu 14.04 so I can test the performace of all three buntu flavors on this laptop.

Can someone provide me some guidance on how to get Xubuntu and Kubuntu added to this laptop with existing config of Lubuntu and Win7? I'm wondering how grub2 will react... Let me clarify: I want Grub2 to give me the option to Boot: Lubuntu, Xubuntu, Kubuntu, and Win7. I'm not how that woud appear on the Grub menu because at this time Grub denotes Ubuntu, Advanced Options, Mem Test, and Windoze 7. I'm not sure how to differentiate between the L-X-Kubuntus on Grub.

Thanks!

---

### Post by kansasnoob on 2014-09-08
While booted into Lubuntu please provide some info regarding the current partitioning and disc usage:

```
sudo parted -l
```

```
df -H
```

A screenshot of Gparted would also be helpful.

---

### Post by webusr1 on 2014-09-08
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        57G  3.4G   50G   7% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           397M  1.2M  396M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M   20K  100M   1% /run/user

parted output:
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  105GB  105GB   primary   ntfs            boot
 2      105GB   250GB  145GB   extended                  lba
 5      105GB   186GB  81.0GB  logical   ext3
 7      186GB   247GB  61.3GB  logical   ext4
 6      247GB   250GB  2657MB  logical   linux-swap(v1)

Fdisk output:
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000cb8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   205117919   102558928+   7  HPFS/NTFS/exFAT
/dev/sda2       205117981   488396799   141639409+   f  W95 Ext'd (LBA)
/dev/sda5       205117983   363400366    79141192   83  Linux
/dev/sda6       483207168   488396799     2594816   82  Linux swap / Solaris
/dev/sda7       363401216   483203071    59900928   83  Linux

---

### Post by Dennis N on 2014-09-08
This is easy to do with an bios based (not UEFI mode) system. I think all the installs of Ubuntu flavors and versions would get named Ubuntu in the Grub menu, but that can be fixed by changing the "Grub Distributor" Line in /etc/default/grub to the name you want: Lubuntu or Lubuntu 14.04 for example. This is the line that by default says (on my computer):

```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```

You can modify the part between the single quotes (leave the quotes), then sudo update-grub.

There are several posts on these forums giving this information, which I how I learned of it - I never needed to do it myself as I use a custom menu, which is the other way to deal with this problem.

---

### Post by kansasnoob on 2014-09-08
What is the 81GB ext3 partition (/dev/sda5)? I assume data??? It doesn't really matter much but I'm just curious.

Anyway, I can see from that your existing *ubuntu is on /dev/sda7 which is 57GB and only 3.4GB is used so you have plenty of room.

I multi-boot a lot, more than any sane person would, because I perform iso/upgrade testing and my test box doesn't have enough RAM to handle it in a VM anymore:

[ATTACH=CONFIG]256251[/ATTACH]

That's a lot more partitions than you want or need but you can see that I have a lot of available partitions for installing and testing various flavors/distros. Before I go any further though let me just say that any partitioning or installation procedure presents some risk to existing data so always have a backup of anything and everything important - the data you lose is always the data you don't have backed up!

Just to provide an example I created a mock-up using an 80GB physical drive. Since it's a much smaller drive the mocked up Win and Data? partitions are much smaller than what you'd see in Gparted but the device designations are the same as you showed other than the drive being recognized as /dev/sdb instead of /dev/sda:

[ATTACH=CONFIG]256252[/ATTACH]

So you could right-click on your Lubuntu partition, select resize, and shrink it by moving the right end to the left (it's much, much slower to move the left end to the right):

[ATTACH=CONFIG]256253[/ATTACH]

Then you can right-click the newly created free space, select New and create a new partition half the size of the new free space:

[ATTACH=CONFIG]256254[/ATTACH]

Then finally right-click the left-over free space, select New one more time and create another new partition. Then after clicking on Apply you'll have two new partitions (/dev/sda8 and /dev/sda9):

[ATTACH=CONFIG]256255[/ATTACH]

This, of course, must all be done using a live DVD or USB, and you must right-click swap and choose swap-off before editing any partitions within the extended partition. Your existing SWAP will be used automatically by each of the newly installed distros unless told not to.

Then during installation you just have to use the Something else option and choose which partition to use as / (aka: root) as I described here:

[http://ubuntuforums.org/showthread.php?t=2242245&page=6&p=13116544#post13116544](http://ubuntuforums.org/showthread.php?t=2242245&page=6&p=13116544#post13116544)

You may also wish to decide which of your installations you want to have control of grub. Like in my case I always let my Trusty on /dev/sda1 control grub. So if I were to install a new *ubuntu on /dev/sda14 instead of letting the installer install it's grub to the mbr of /dev/sda I'd change that to it's own root partition - in that case /dev/sda14. Clear as mud? Then when I reboot after the installation I boot Trusty on /dev/sda1 and just run "sudo update-grub" and it finds the newly installed OS.

If you ever wish to change which OS is in control of grub it's better to use "sudo dpkg-reconfigure grub-pc" than just using "grub-install" because when updates trigger an automatic "update-grub" the system relies on info created by dpkg. Confused yet?

It's true that the grub boot menu lists all the *ubuntu flavors as Ubuntu but it also displays the device designations so you'll know if you're selecting the installation on /dev/sda8 or /dev/sda9, etc.

This is sort of a lot to soak in so if you need some clarification about anything be sure to ask first before jumping in head first.

---

### Post by webusr1 on 2014-09-08
kansasnoob,
This is exactly what I'm looking for and  I follow the instructions for allocating space with  gparted (it's clear and straight forward. I'm good with install "SomethinElse").  I just noticed that Windoze is eating up 105GB (primary ntfs) and I'd like to take some of that storage back... Can I take about 30GB from windoze primary ntfs to use for another ubuntu version? I don't want to hose up windoze.

I need to think about grub a little since I will be getting kernel updates and I don't want to hose up the other distros after an update.

Thanks!

---

### Post by oldfred on 2014-09-08
Windows likes lots of extra room, 30% to run well and at 10% free gets real slow. So do not shrink the NTFS partition too much.

There are several ways as usual to multi-boot. I do prefer booting the partition which works with Debian based systems as they put links to most current kernel into the / partition. If you boot link you always boot the most current version. Otherwise you have to update version and grub menu, then reboot into the one install that grub in MBR and update grub menu in it to see new kernel in other install.

       I first saw this from Ranch hand who at time was testing installs and did not want to always be updating grub.
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
       sudo update-grub
    ```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

```

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by kansasnoob on 2014-09-09
> **webusr1 said:**
> kansasnoob,
This is exactly what I'm looking for and  I follow the instructions for allocating space with  gparted (it's clear and straight forward. I'm good with install "SomethinElse").  I just noticed that Windoze is eating up 105GB (primary ntfs) and I'd like to take some of that storage back... Can I take about 30GB from windoze primary ntfs to use for another ubuntu version? I don't want to hose up windoze.

I need to think about grub a little since I will be getting kernel updates and I don't want to hose up the other distros after an update.

Thanks!

***oldfred*** makes a good point;

> Windows likes lots of extra room, 30% to run well and at 10% free gets real slow. So do not shrink the NTFS partition too much.

I'd add that Windows should be resized using only it's own partitioning tool:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

It's also generally wise to defrag Windows before resizing.

Regarding grub, back when I was using Precise as my production OS and it was in charge of booting I did have to fiddle around and perform some minor customizations to keep the boot menu fairly clean. But with Trusty in charge things just look good enough for me with no customization. I'll grab a pic of my boot menu so you can see.

---

### Post by kansasnoob on 2014-09-09
OK, about that boot menu - I have Trusty on my /dev/sda1 in charge of booting (it's my production OS) so when I run update-grub I get:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda10
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda11
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda12
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda13
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda2
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda3
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda6
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda7
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda8
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda9
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sdc1
done
```

Here's two pics of what the boot menu actually looks like:

[ATTACH=CONFIG]256281[/ATTACH]

[ATTACH=CONFIG]256282[/ATTACH]

I hadn't booted into Utopic on /dev/sda9 for a few days so I booted it and checked for updates in Synaptic and there was a kernel update available:

[ATTACH=CONFIG]256283[/ATTACH]

So it was a good time to make sure I knew what I was talking about. I applied all of the updates and then rebooted just selecting /dev/sda9 again from the boot menu. No surprise to me that it still booted the older kernel so I rebooted again and this time booted into Trusty on /dev/sda1, ran update-grub, and then the next time I booted Utopic on /dev/sda9 it booted to the new kernel as expected. To me it's no big deal to have to run update-grub in the controlling OS and I prefer tweaking configuration files as little and as seldom as possible ;)

Taking things a step further you probably noticed in my Gparted screenshot that I give each OS a label that makes sense to me, so if I want to access the files on one of those lateral installs they appear as labeled in Places (in fact even those labels I created in the mock-up partitions show):

[ATTACH=CONFIG]256284[/ATTACH]

It all seems simple to me :biggrin:

---

### Post by kansasnoob on 2014-09-09
I did think to add one more thing. Not sure if you have what I assume is a data partition added to fstab or some such thing, and it's doubtful that particular partition would ever be effected because it's the first logical partition - the first will always remain /dev/sdX5 (where X is the drive designation, in your case a).

But you've probably noticed that fstab (and Linux in general) uses UUID's for partition ID instead of just device designations. There is a good reason for that. Let's say you decide at some point to delete /dev/sdb7 in the example I provided earlier. Then what is shown there as /dev/sdb8 becomes /dev/sdb7, and /dev/sdb9 becomes /dev/sdb8. Is that confusing?

Here it is before deleting sdb7:

[ATTACH=CONFIG]256291[/ATTACH]

Here it is after deleting sdb7:

[ATTACH=CONFIG]256292[/ATTACH]

Just something you should know going forward.

---

### Post by webusr1 on 2014-09-09
Guys, Thanks so much for the quick replies and all the detail (It's great!). UUID's, no problem (I got it!). I don't mind running terminal commands (that's the beauty of the Unix/Linux systems) at all to keep Grub in check or if any maintenance needs to be done. 

I'm going to try and install Xubuntu tonight, and will post my results if it gets done. Wish me luck!!!

---

### Post by ajgreeny on 2014-09-09
Regarding Denis N's comment at post #4 I think you have to change the single quotation marks, or backticks, whatever they are, for double quotation marks, ie ```
"whatever you want in grub list"
```to get it to show.

---

### Post by webusr1 on 2014-09-14
All,
I've been stalled due to hardware problems on Dell Vostro V13. I will not use the Vostro V13 due problems with keyboard (fixed now), battery, and WiFi. Instead, I've changed my requirements to utilizing a Dell Latitude E6430.  AND, here's how it went so far...

I ran into some Grub features, so I plan to re-format and re-partition hard drive. Here's what happened and the synopis of the initial system configuration.

- Initial config consist of: Ubuntu 12.04 on a 500GB only one OS. Then:
- Resized 500GB hard drive and added two addition partitions.
- Installed Ubuntu Gnome 3 (LTS)/sda3, and KUbuntu (14.04LTS)/sad4, with existing Ubuntu 12.04 (Unity)/sda1 and sda2.

SEE FDISK -l OUTPUT
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00027ebf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   616376319   308187136   83  Linux
/dev/sda2       960090110   976771071     8340481    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3       616376320   786171241    84897461   83  Linux
/dev/sda4       786171904   960088063    86958080   83  Linux
/dev/sda5       960090112   976771071     8340480   82  Linux swap / Solaris

Partition table entries are not in disk order

----------------------------------------------------------------------------------------
Here's my Grub story of woes:
- Installed KUbuntu grub to sda (same as Ubuntu 12.04)
- Installed Gnome3 Ubuntu grub to sda3 with chainloader.

I wanted to see the difference between chainloading and sharing the same sda. Well, when I ran update-grub it added many entries to the Grub menu. In fact it added all three OS and the chainloader (Gnome3 OS). Grub also duplicated the Gnome3 twice. I'm able to pick out the correct OS's but it is extremly messy.

So, here's where I need some advice on the re-install....

I think that if chainload I won't have to re-run update-grub after kenel updates. Is that correct? That was my goal (to avoid re-running update-grub after kernel updates), but it left a messy GRUB menu at boot up.  

Have any of you guys configured Grub with Linux chainloading successfully (not windows as I know the chainloader is commonaly used with windows)? What I mean by sucessfully - Grub Menu results in only two OS option...


ALSO, I like to SAY that I am very impressed with Gnome 3 and it is currently out performing Unity on 12.04. I'm not sure if this is a 12.04 unity VS 14.04 Gnome 3 scenario. However, I am really liking Gnome 3. And, so CHOICE is another beauty of Linux!

Regards!

---

### Post by oldfred on 2014-09-14
I last used chainloading with grub legacy. 
Grub2 does not fit into a partition boot sector (PBR) and converts to blocklists. Since that is hard coded addresses a major update to grub or even a fsck may move a file and address is wrong and you have to reinstall grub to PBR.

I find booting partition to be a better solution as I posted in #7.

---

### Post by Dennis N on 2014-09-14
I suggest a custom menu to solve the messy Grub menu and avoid the need to update anything manually.    

In my opinion, the easiest guide for a custom menu is here:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

It basically constructs the custom entries by copy and paste from your grub.cfg which anyone can do. You get the current correct syntax this way. Following the last part of that guide gets you to maintainance free. It's the same method that Fred mentions using the symlinks.

Another suggestion would be to use a GPT partiton table with your bios system instead of MS-DOS. Its more robust.

---

