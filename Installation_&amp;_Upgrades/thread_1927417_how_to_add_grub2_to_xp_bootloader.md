---
title: "how to add grub2 to xp bootloader"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by mandud on 2012-02-18
i've search how to aadd grub2 to xp bootloader, but i only found for old grub, when i try
```
sudo dd if/dev/sda7 of=/media/windows/ubuntu.bin bs=512 count=1
```and put 
```
c:\ubuntu.bin="ubuntu 11.10"
```it appear in xp bootloader but when i choose ubuntu it restart by itself
how to fix it?

---

### Post by stn21 on 2012-02-18
Try the other way around and add XP to the grub-bootmenu. If you installed xp first and then ubuntu your grub-bootmenu should already be ok. You may have to activate the partition that contains ubuntu.

---

### Post by mandud on 2012-02-18
thanks for reply,yeah i see grub-bootmenu,the problem is i have 3 XP OS
when my pc start it show grub-bootmenu and it show ubuntu menu and menu for xp bootloader (in this bootloader i have put 4 os)
1.xp 1
2.xp 2
3.xp 3
4.ubuntu

all xp can be boot normally except the ubuntu

---

### Post by stn21 on 2012-02-18
> **mandud said:**
> ...it appear in xp bootloader but when i choose ubuntu it restart by itself

Is this the first time you try ubuntu? Maybe your ubuntu does not work because of some hardware-issue, wrong graphics-driver maybe. Happens often :neutral:. Finding the reason for that can be really frustrating. So if you are new to ubuntu try another ...buntu instead, like lubuntu or xubuntu or linux mint. They are much less fragile than ubuntu with its very error-prone unity-desktop and easier to get running.

-

> **mandud said:**
> ... when my pc start it show grub-bootmenu and it  show ubuntu menu and menu for xp bootloader (in this bootloader i have  put 4 os)

As for the bootmenu: What I meant was, do NOT use the xp bootloader to start ubuntu. Do NOT put C:\ubuntu.bin in your C:\boot.ini. Only use grub to start ubuntu and all your XPs. Keep it simple.

Grub can also start each of your three xp-installations. Again no need for the XP-bootloader. After installing ubuntu you should automatically find each of your xp's in the grub-menu. This is the same for ubuntu, lubuntu, xubuntu, linux mint.

---

### Post by mandud on 2012-02-18
> **stn21 said:**
> Is this the first time you try ubuntu? Maybe your ubuntu does not work because of some hardware-issue, wrong graphics-driver maybe. Happens often :neutral:. Finding the reason for that can be really frustrating. So if you are new to ubuntu try another ...buntu instead, like lubuntu or xubuntu or linux mint. They are much less fragile than ubuntu with its very error-prone unity-desktop and easier to get running.

-



As for the bootmenu: What I meant was, do NOT use the xp bootloader to start ubuntu. Do NOT put C:\ubuntu.bin in your C:\boot.ini. Only use grub to start ubuntu and all your XPs. Keep it simple.

Grub can also start each of your three xp-installations. Again no need for the XP-bootloader. After installing ubuntu you should automatically find each of your xp's in the grub-menu. This is the same for ubuntu, lubuntu, xubuntu, linux mint.

no,many times i've installed ubuntu,but not with 3 xp, only xp and ubuntu
if i enter using grub menu it can boot normally but if i using xp bootloader its restart directly

how to add all xp into grub menu?

---

### Post by ottosykora on 2012-02-18
> **mandud said:**
> i've search how to aadd grub2 to xp bootloader, but i only found for old grub, when i try
```
sudo dd if/dev/sda7 of=/media/windows/ubuntu.bin bs=512 count=1
```
and put 
```
c:\ubuntu.bin="ubuntu 11.10"
```

it appear in xp bootloader but when i choose ubuntu it restart by itself
how to fix it?

you probably did all right, but this needsthe grub2 to be installed in the pbr. 
OK, with default install of ubuntu, this is possible and will install grub2 into the pbr if set correctly during install. 
But:
it is not recomended to install grub2 into pbr, apparently because of the large size of some files and it can break easy in this position. And I can tell you it does break , not too often, but often enough of upgrades etc.

Therefore for this one should replace the grub2 with legacy grub.
try here:
[http://ubuntuforums.org/showthread.php?t=1298932&highlight=revert+grub2](http://ubuntuforums.org/showthread.php?t=1298932&highlight=revert+grub2)

then take care that you install the grub to the pbr of the partition in question only. 

Then do the xp bootloader setup and also leave in the grub legacy in the pbr only the kernels in th eown partition and all os of the computer, this will lead to bite the tail situation sometimes.


BTW: not quite sure how you boot the system at first at all?
Do you use grub2 in the mbr or first XP to start and call from the the other XP?
If second is right, then you need the procedure I have given you above. Youu need complete bootmanager inside your partition with ubuntu in that case unfortunately.

---

### Post by ottosykora on 2012-02-18
>What I meant was, do NOT use the xp bootloader to start ubuntu. Do NOT put C:\ubuntu.bin in your C:\boot.ini. Only use grub to start ubuntu and all your XPs. Keep it simple.

Grub can also start each of your three xp-installations. Again no need for the XP-bootloader. After installing ubuntu you should automatically find each of your xp's in the grub-menu. This is the same for ubuntu, lubuntu, xubuntu, linux mint.<

sure right, but!
as you know, grub can not be deinstalled or removed, it resides then in the linux partition which was installed last and this is not what some people want.

Using XP boot loader was done for many years as standard procedure to preserve windows installation and make linux removable without making the system unbootable.

So in fact, using xp boot manger was long time standard for testing a linux installation and then delete it again etc, similar to the usage we have wubi for ubuntu now.

---

### Post by mandud on 2012-02-18
thanks for all your helps..
finally i use grub-customizer to manage the boot
i order xp to the top of grub menu

but i still dont understand how to put 3 xp into grub loader
its only detect first xp

---

### Post by darkod on 2012-02-18
> **mandud said:**
> thanks for all your helps..
finally i use grub-customizer to manage the boot
i order xp to the top of grub menu

but i still dont understand how to put 3 xp into grub loader
its only detect first xp

Detecting only one XP is no fault of grub.

When you install more than one windows OS it is designed to combine the boot files. So, all boot process for as many windows OS you have, is combined into one. Ubuntu detects this one and adds it to the boot menu.

That's why there is always only one entry for windows in the boot menu.

There is a workaround for this, but it needs to be done before installing the XP systems. By moving the boot flag to the target partition BEFORE installing your XPs, you can avoid the boot files being combined. Then ubuntu will detect all three and make three entries in the boot menu.

---

### Post by ottosykora on 2012-02-18
>https://www.wuala.com/ottosykora/SHARED/DAT/?key=nCs62R33czrV<

how are those xp installed? In what kind of partitions?

In fact with windows systems, when more of them are installed, I was using hide-unhide in the grub, as otherwise all gets very messy as windows claims the system path is C: and chnages the drive letters all the time.

So when I boot windows nr2 for example, I have in the grub unhide command for the windows I want see now and hide command for the two others.

How di you install the 2nd and 3rd xp ? Did you hide the partition with the previous install and then did complete install to the next partition?

Or were the xp installed as second to the primary xp in which case they have to bee started from the xp where the bootmanager is configured.


For more complex system  which has w98se, xp, w7, fedora, ubuntu, debian and sometimes one knoppix or similar extra, I have separate dedicated partition for the grub only. Hide-unhide the windows partitions so they dont get confused.
The advantage is, I can delete any os and the rest will work without problem.


ok, darko was faster, and dead right! this is what I have been doing during the install.

---

### Post by stn21 on 2012-02-18
As for adding ubuntu to the xp bootmenu: I agree that adding the first 512 bytes of the linux-partition to boot.ini is correct, just like [mandud]("http://ubuntuforums.org/member.php?u=1555720") did according to the first post. I also agree with [ottosykora]("http://ubuntuforums.org/member.php?u=758846") that grub needs to be installed in the pbr. Otherwise the file with the 512 bytes will not contain any bootloader and will not be suitable for booting linux. 

Hint: try "hexdump -C ubuntu.bin" and see if the string "GRUB" appears somewhere near the end. If you get lots of zeros then ubuntu.bin does not contain a bootloader. That would then explain why it does not boot ubuntu from the XP-bootmenu.

In case grub is already installed in the MBR I would first restore the MBR of windows. This can be done with the recovery-console on the windows-install-cd. After that the system should be in the state it was before installing ubuntu.

Then I would either try to install grub in the partition-bootrecord (live-ubuntu and grub-install) or I would simply reinstall linux.

-

All in all I would have done the whole thing like this:

0) if necessary: remove grub from the MBR by overwriting with the MBR of XP or with install-mbr <Device> under ubuntu-live. After that test by rebooting to see if XP boots like it did before the ubuntu-installation. That way either the ubuntu-partition or the XP-partition can be activated, so that the computer can boot either with grub OR with the XP-bootmanager.

1) install ubuntu and at the end of the installation put grub in the linux-partition, not the mbr. (Installing in the  mbr is the default, the linux-partition has to be explicitely named).  That way linux does not influence the existing boot-setup, the mbr stays  unchanged and of course the bootrecords in the xp-partition are also  not changed. This pretty much guarantees that ubuntu does not mess up  XP.

2) activate either an xp-partition (then xp boots with its own bootloader) or activate the linux-partition (then grub boots)

3) manually edit grub.cfg. Example from my hdd, there is one working XP with this entry:

```
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
        insmod ntfs
        set root='(hd2,1)'
        search --no-floppy --fs-uuid --set 128FC4C860CA8521
        drivemap -s (hd0) ${root}
        chainloader +1
```If I had 2 more XPs in for example /dev/sdc2 and /dev/sdc3 then I would  copy the menuitem twice and change the first copy like this:

```
menuentry "Microsoft Windows XP Professional (on /dev/sdc2)" {
        insmod ntfs
        set root='(hd2,2)'
        search --no-floppy --fs-uuid --set <UUID of /dev/sdc2>
        drivemap -s (hd0) ${root}
        chainloader +1
```and the second copy accordingly (/dev/sdc3 and (hd2,3))

Then it should be possible to boot each XP from the grub-menu. I have  already done this with XP and Windows 7 and Linux on the same disk. I also believe that this worked for two XPs on the same disk but that  was a while ago so I cannot say for sure.

---

### Post by darkod on 2012-02-18
> Then it should be possible to boot each XP from the grub-menu. I have   already done this with XP and Windows 7 and Linux on the same disk. I  also believe that this worked for two XPs on the same disk but that  was  a while ago so I cannot say for sure.

You did this when the windows boot files are combined and it worked??? I am under the impression that once the boot files are combined, making a manual entry for the windows partitions won't work. Because the boot files are not on the partitions of the second and third install, they are all on the partition of the first install.

To the OP: But if I understood correctly what you wrote later, you have grub2 on the MBR and using it to boot. If you boot ubuntu, it works. If you select XP it shows the windows bootloader with the options for three XP systems. There is a manual entry you made for ubuntu in it that doesn't work, of course.

If this is correct, why would you want a working ubuntu entry in your windows bootloader when you can simply boot ubuntu right away from grub2? It makes no sense at all, if you want to load ubuntu, to select XP in the grub menu (when you have ubuntu next to it), and then select ubuntu in the windows bootloader.

Adding ubuntu to windows bootloader is usually done if the windows bootloader is on the MBR and this is not the case here.

---

### Post by ottosykora on 2012-02-18
I agree with Darko full

I made such complex installs few times and separate booting of windows os can happen only when they were installed *as independent* os, that means each separate and the other windows closed/hidden/inactive , simply non existent during the installation.
(hide them first manually with any partitioning tool, gparted for example)

Then all windows can be booted separately by in fact any boot manager, grub or windows own or commercial, in the last such install I use acronis product and also this needs the windows to be installed as independent otherwise it will call up just the one holding all the booting things. If installed when other windows is active, as next windows, it will use the windows boot manger and then also commercial boot manager can not see the 'other' windows as separate bootable os as what darkod say, the boot files are kind of merged in one of the installs.

So all depends only how the windows was installed in first place. If independent, then also grub can start them all separate.

However stn21 mentions reasonable test for the grub extract file. To just look into the 512bytes makes sense, as if there is no trace of grub in those 512 bytes, then the whole game was for nothing and result will be that the jump will go back to original grub...tail bite...

---

### Post by oldfred on 2012-02-19
I agree with Darko & ottosykora.

While it may be a bit easier if you install the XP's separately to keep boot files in the install partition, it is possible to repair each XP install by moving the boot files to each XP and fixing boot.ini. With XP you can also directly boot it in a logical partition which is not normal with the newer versions of Windows. Review the multibooters site to understand the Windows boot process.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Info on fixing, geting XP to boot.
How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)
Vista Win7 missing boot files meieifra. More info on Herman's post
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by mandud on 2012-02-20
@everyone who reply this thread
thanks for reply, finally i use grub customizer and manage xp and ubuntu in the grub
if i choose to xp, it will enter to xp bootloader (that show 3 xp)
thanks everyone the help

but i've another problem, when i clone the disk 
for windows os its start normally but when i choose ubuntu its doesnt want boot
and enter to busybox? how to fix this?
i read in some articles , i must change the uuid

---

### Post by stn21 on 2012-02-21
> **mandud said:**
> ... how to fix this? i read in some articles , i must change the uuid

That may be the case. If it is you

1) find the UUID of your new root-partition. You can use live-linux for that, with the command "blkid <device>", for example blkid /dev/sda1

2) it also helps to write down the UUID of your old root-partition. Then it is easier to find the places where you have to change it. You can find that the same way, with your old harddisk.

3) change the UUID by editing several textfiles. Those are: /etc/fstab, /etc/blkid.tab, /boot/grub.cfg. I also found it in /etc/default/extlinux and /boot/extlinux/linux.cfg.

---

### Post by stn21 on 2012-02-21
> **darkod said:**
> You did this when the windows boot files are combined and it worked??? I am under the impression that once the boot files are combined, making a manual entry for the windows partitions won't work. Because the boot files are not on the partitions of the second and third install, they are all on the partition of the first install. 

To get a specific XP-partition to boot you need the prerequesites listed below. With these any XP-partition will boot independently of any other XP-partition.

"Combined" bootfiles simply mean that some of the prerequesites are on other partitions. You can always manually add any of them to an existing XP and afterwards it will boot if addressed by the MBR or a chainloader (see below).

In some cases the prerequesites are all OK and XP will still not boot and abort with a stop-error. That usually means that the hardware was changed, for example after plugging the harddisk into another computer. This is a driver-problem and has nothing to do with this thread.


The prerequesites are:

1) a partition-bootrecord. That can be added later with the recovery-console of the XP-install-cd, with the command FIXBOOT <drive-letter>. If you have multiple drives or partitions be careful to check for correct drive-letters first. Adding a PBR never hurts, it can be done even if it is not actually used later on.

2) a correct entry in the file \boot.ini on the partition you want to boot. If necessary this can be manually edited. The important thing is that the numbers for multi(0)disk(0)rdisk(0)partition(1) are correct for your computer. For details google the numerous docs for boot.ini.

3) the partition must be addressed during boot. That means either 
* it is active (and the MBR exists of course)
* or it is addressed by chainloading with grub from another partition or the MBR
* or it is addressed by chainloading with the XP-bootloader, in that case it is also registered in the file \boot.ini in the chainloading XP-partition (not necessarily in the one that is being booted)

4) the MBR must there of course. Either
* the standard-MBR that you can install with ubuntu's "install-mbr"
* or the MBR of XP, which can be installed with "FIXMBR" on the recovery-console of the XP-install-cd
* or grub installed in the MBR. Grub combines the function of the standard MBRs with the additional option of selecting different operating systems.

Personally I prefer a boot-config where all partitions are as independent as possible from each other. Each partition should boot by itself if active. Any bootmenus or chainloaders are nice to have and come afterwards.

That means I use a standard MBR (XP or linux does not matter) and I always install grub in the partition bootrecord of the linux-partition.

That way I even got windows 7 to work on a multiboot XP/W7/linux-system. And windows 7 *really* likes to mess with your boot-config, including other partitions and the MBR.

---

### Post by darkod on 2012-02-21
> "Combined" bootfiles simply mean that some of the prerequesites are on  other partitions. You can always manually add any of them to an existing  XP and afterwards it will boot if addressed by the MBR or a chainloader  (see below).

Why didn't you say so right away. :)

I was talking about default situation, not messing with the boot files after. I know it can work that way, you can even add XP boot files if they are completely deleted and it will work.

The thing is, most people without much experience wouldn't start messing with these things, so I was talking about the default situation. If it combines them on one partition, you can get only one entry detected by os-prober.

Lets not confuse the OP and others looking at this thread any more by continuing this.

---

### Post by mandud on 2012-02-21
@stn21
i've successfull to clone the disk,but the cloned disk (i will call it "a")
i clone to another disk from "a" 
it can show grub menu but when i choose ubuntu its doesnt like "a" disk after clone from the original disk,its only show black monitor, the "a" disk after clone its show busybox and i can see uuid from blkid

how to see uuid ? i just can enter to grub gnu commands

---

### Post by oldfred on 2012-02-21
From an Ubuntu command line:
```

sudo blkid
```

If you only get a grub line, you would then have to boot with a liveCD.

So you have both drive and clone connected? Then you have duplicate UUIDs and that may prevent system from working. Disconnect clone and see if it works. Cloning is not for backup of a drive you want to keep connected.

---

### Post by mandud on 2012-02-22
thanks oldfred,yesterday i didn't brought the dvd external so i can't enter to livecd
but in the morning i've tried using livecd and its work 
thanks

---

