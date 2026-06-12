---
title: "Cylinder 1024 issue"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by mganesh30 on 2011-05-17
I had installed Ubuntu 10.x on a 120 GB HDD long ago and encountered a problem wherein after few days of use, the system failed to boot saying GRUB Error and that Bootloader could not read beyond 1024 cylinders.
 
Has this problem been resolved in Ubuntu 11.04? I now have a 500 GB HDD and will be instaling Ubuntu as a standalone.
 
Thanks.

---

### Post by Rubi1200 on 2011-05-17
Hi,
if I understand your post correctly, the problem is not with Ubuntu or GRUB but with the inability of BIOS to read beyond the first 137GB of the disk. You can also check whether BIOS is recognizing the disk in the first place before trying to install.

If this is the case, and GRUB files are installed beyond this point you may find yourself in this position again.

Here are some possible workarounds:

1. check if BIOS sees the whole drive and enable the large disk option if it is present

2. upgrade your BIOS

3. create a separate /boot partition at the beginning of the disk and install the GRUB files there

4. install normally, then shrink the Ubuntu partition to make sure GRUB is within the 137 limit. This is not really a waste since you could then use the extra space for e.g. a shared data partition

I hope this helps answer your question. Feel free to ask for more information if anything is unclear.

EDIT: if I have misunderstood the problem and this is not what you mean, please post links to the relevant bug reports and threads concerning this so we can investigate further.

---

### Post by mganesh30 on 2011-05-19
How can I check if my BIOS is reading my disk?

---

### Post by Rubi1200 on 2011-05-19
Depending on the make and model of your computer, you can get into BIOS by pressing one of these keys after you see the POST screen (the one which tells you the name of the manufacturer); F2, F12, Esc, Del, or something similar. You may need to check the documentation to find out.

Once you enter BIOS there are a number of menus. Look through and see if there is anything related to reading the disk or enabling a large disk option.

Let me know what you find.

---

### Post by mganesh30 on 2011-05-19
Checked my BIOS and following is displayed regarding my HDD:-

Capacity: 500 GB
Cylinder: 65535
Head: 16

---

### Post by srs5694 on 2011-05-19
In my experience, BIOS size limits (they *all* have them, even brand-new BIOSes; they're just big enough on modern BIOSes that they aren't yet an issue) are never clearly specified in the BIOS itself. Note that correctly identifying a disk as being larger than the (unspecified) limit is no guarantee that the BIOS can actually read the whole disk. You might be able to do a Web search for the information, using your BIOS make and version number, or your motherboard make and model number. It's conceivable your motherboard manufacturer has some information buried on a Web site somewhere; but they usually lose interest in updating their Web sites by the time the relevant limits become important. There might also be a utility out there somewhere that will identify the limit, but if so, I don't know what it is.

In sum, if you've got any doubts whatsoever, it's probably best to just assume that your BIOS has a size limit on the disks it can read. It's really not hard to set it up correctly -- just create a small (~200 MiB) /boot partition at the very start of the disk, below any limit. (For the record, the common limits have been 504 MiB, ~8 GiB, and ~128 GiB, IIRC. Only the last of those is likely to be present in any computer sold in the last 5-10 years.)

---

### Post by mganesh30 on 2011-05-19
But why is this an issue only with Ubuntu & not with Fedora? Is it that GRUB2 is only used by Ubuntu?

---

### Post by oldfred on 2011-05-20
You are showing 16 heads. Most drives are set for LBA and use the defaults of 255 heads, 63 sectors/track. Flash drives or others may not use the standards but rotating drives should.

So what settings do you have in your BIOS? You may have Large, Auto or manual which is CHS or cylinders, heads, sectors.  CHS which really has not been used for 15 years when drives got over 8GB. LBA replaced CHS.

---

### Post by srs5694 on 2011-05-20
> **mganesh30 said:**
> But why is this an issue only with Ubuntu & not with Fedora? Is it that GRUB2 is only used by Ubuntu?

You didn't mention this distinction before, so I know nothing about what symptoms you encountered with Fedora vs. Ubuntu. Going out on a limb, I'd speculate that if you ran into problems with Ubuntu but not with Fedora it was simply a question of where their partitions were located -- Fedora's were under the BIOS limit and Ubuntu's were over it. Alternatively, if you did serial installations to the same partitions, Ubuntu may have placed its kernel and/or initial RAM disk files (the files that the boot loader loads) over the limit and Fedora put them over the limit on a partition that straddled the boundary.

Fedora still uses GRUB Legacy, whereas Ubuntu has used GRUB 2 since (IIRC) version 9.04 or 9.10. Both use the BIOS, and suffer from the same BIOS limits.

---

### Post by mganesh30 on 2011-05-20
Thanks srs5694 for you reply. Let me explain. When I first decided to switch to Linux from Windows, I installed Ubuntu 9.04 alongside Windows (dual boot). Ubuntu worked well for a week and then I got this GRUB Error saying cannot read beyond 1024 cylinders. I could not even boot into Windows after this and also my HDD was not getting recognized by CMOS. I then got a new HDD and installed Ubuntu as a standalone. Again Ubuntu worked well for a week and then the same problem. I couldn't even reinstall Ubuntu as my HDD was not being recognised by CMOS. In both these cases manual partitioning was done and if I remember correctly, the Root partition was at the beginning of the HDD.

**MY QUESTION IS: IF IT WAS A PROBLEM OF READING BEYOND 1024 CYLINDERS, WBY DIDN'T THE ERROR CROP THE VERY FIRST TIME, WHY AFTER A WEEK? ALSO WHY WAS MY HDD NOT GETTING RECOGNIZED BY CMOS AFTER THIS ERROR?**

When I installed Fedora with default partitioning, no such problem.

I have read reviews about Ubuntu 11.04 and also created a Live CD and tried it out. I am very keen to install it but reluctant to do so fearing that the above problem might surface again.

---

### Post by oldfred on 2011-05-20
Have you checked BIOS settings? Do you have LBA set or is it something else.

We have seen systems with 1 & 2TB drives where the user installs one large partition and part of the system files are at the end of the drive. In your case it may have installed inside the 1024 limit but then updates put new files beyond the boot limit.  In most of these cases the BIOS was not set correctly. Some we do not know as they just reinstalled to small partitions at the beginning of the drive.

---

### Post by Rubi1200 on 2011-05-21
Not sure how much it will help, but please post the results of the boot info script. At the very least it will tell us where GRUB is storing its files on the drive.

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mganesh30 on 2011-05-21
Dear oldfred,

Checked my BIOS Under Drive Configuration, Access Mode is set to Auto. The other option is Large.

---

### Post by mganesh30 on 2011-05-21
Dear rubi,

Here are the results:-

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97 is installed in the MBR of /dev/sda and looks at sector 
    32636 on boot drive #1 for the stage2 file.  A stage2 file is at this 
    location on /dev/sda.  Stage2 looks on partition #1 for /grub/grub.conf..

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sda2           1,026,048   976,773,119   975,747,072  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        b3fcd4eb-bf10-4b81-aaaa-8083b9f22beb   ext4       
/dev/sda2        9wKbjC-yArH-x7qO-ZygO-LfAI-tK8T-D3pexg LVM2_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_kripaganesh-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.13-91.fc14.i686)
    root (hd0,0)
    kernel /vmlinuz-2.6.35.13-91.fc14.i686 ro root=/dev/mapper/vg_kripaganesh-lv_root rd_LVM_LV=vg_kripaganesh/lv_root rd_LVM_LV=vg_kripaganesh/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.13-91.fc14.i686.img
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,0)
    kernel /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/vg_kripaganesh-lv_root rd_LVM_LV=vg_kripaganesh/lv_root rd_LVM_LV=vg_kripaganesh/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.010163307 = 0.010912768    grub/grub.conf                                 2
   0.010163307 = 0.010912768    grub/menu.lst                                  2
   0.015676498 = 0.016832512    grub/stage2                                    1
   0.049777031 = 0.053447680    initramfs-2.6.35.13-91.fc14.i686.img           2
   0.040020943 = 0.042972160    initramfs-2.6.35.6-45.fc14.i686.img            2
   0.021834373 = 0.023444480    initrd-plymouth.img                            1
   0.028110504 = 0.030183424    vmlinuz-2.6.35.13-91.fc14.i686                 1
   0.013884544 = 0.014908416    vmlinuz-2.6.35.6-45.fc14.i686                  1

---

### Post by oldfred on 2011-05-21
I copied these comments from others with similar issues. BIOS do not seem to always use same terms or users did not.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick.

---

### Post by srs5694 on 2011-05-21
> **mganesh30 said:**
> Thanks srs5694 for you reply. Let me explain. When I first decided to switch to Linux from Windows, I installed Ubuntu 9.04 alongside Windows (dual boot). Ubuntu worked well for a week and then I got this GRUB Error saying cannot read beyond 1024 cylinders. I could not even boot into Windows after this and also my HDD was not getting recognized by CMOS. I then got a new HDD and installed Ubuntu as a standalone. Again Ubuntu worked well for a week and then the same problem. I couldn't even reinstall Ubuntu as my HDD was not being recognised by CMOS. In both these cases manual partitioning was done and if I remember correctly, the Root partition was at the beginning of the HDD.

**MY QUESTION IS: IF IT WAS A PROBLEM OF READING BEYOND 1024 CYLINDERS, WBY DIDN'T THE ERROR CROP THE VERY FIRST TIME, WHY AFTER A WEEK? ALSO WHY WAS MY HDD NOT GETTING RECOGNIZED BY CMOS AFTER THIS ERROR?**

Three possibilities occur to me, but I can't be positive of what's going on without actually seeing the computer, reproducing the problem, and performing a variety of diagnostics on it when the problem occurs:


[list]
[*]**Defective hardware** -- The hardware itself could be defective and producing problems that might manifest with misleading symptoms or error messages. This could be a flaky disk controller chip, a bad hard disk, or perhaps something else. It's conceivable that something like a bad power supply is damaging disks, causing them to break after a couple of weeks.
[*]**Changing BIOS settings** -- As others have suggested, a change to the BIOS settings could be causing the disk to be detected or accessed differently. These settings might be changing randomly because of a failing battery or a worn trace on the motherboard, which could make at least some instances of this cause a variant of the previous one. OTOH, you might be changing BIOS settings intentionally or unintentionally in some other way.
[*]**Kernel upgrades** -- If you use a default partitioning system, Ubuntu will create one big partition for most purposes. If that partition happens to span whatever boundary exists in the BIOS, then any given file could reside below or above that boundary (or even span the boundary itself). If the system installation happened to put the kernel and initial RAM disk below the boundary, then it would boot fine. If you then upgrade the kernel (either specifically or as part of a general system update), though, the new kernel might not fall below the BIOS boundary. At that point, the system will no longer boot, at least not if you select the new kernel (which will be the default in the boot loader). This explanation would not, however, explain why you can no longer see the disk in the CMOS setup utility.
[/list]


I can't really diagnose it more precisely than this remotely. If I had the computer in my possession, I could perform a number of tests (deliberately creating /boot partitions late on the disk; fiddling with BIOS settings; swapping hardware with other computers; using a plug-in hard disk controller; etc.), but if the computer was more than 3 or 4 years old, it might not be worth the effort. In such a case, I'd probably replace the computer or perhaps just do a motherboard swap.

---

