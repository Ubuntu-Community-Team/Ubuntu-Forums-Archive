---
title: "Trying to install Ubuntu - hit a brick wall."
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by StuMcBill on 2010-12-04
Hi,

I am trying to dual boot Windows 7 and Ubuntu, I have shrunk on of my partitions in Windows and now have an "unallocated" 25Gb partition which I wish to install Ubuntu onto.

I have used unetbootin to put Ubuntu onto a USB stick and can boot it and get to the Install screen no probs!  I am having trouble allocating partitions though.

I am following this guide : [http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)

I get to the point where I need to partition my free space (Page 2 of tutorial), and select "Specify Partitions Manually (Advanced)".

I then go to the next step and I get the "Allocate Drive Space" screen.  I am told that I have "free space - 26844Mb", I have selected this, and pressed the Add button, then go to the next screen, and set up the /boot partition as described in the tutorial.  This works ok.

When I go back to the "Allocate drive space" screen, I am told that the space is now "unusable" and has a size of 26344Mb.

I cannot get any further than this as it will not let me do anything except "revert"?

Does anyone have any pointers or know where I am going wrong?

Thanks

Stewart

---

### Post by Quackers on 2010-12-04
How many partitions are on your system? Including recovery.

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> How many partitions are on your system? Including recovery.

3, I think.  4 if you include the "unallocated" space.

Recovery and 2 NTFS windows partitions.

---

### Post by Habeouscorpus on 2010-12-04
Could you try doing them in a different order? 

Also, what was on this drive space before the installation process?

---

### Post by Quackers on 2010-12-04
If you are now booted in to Windows will you please post a screenshot of your disk management console (Start > right-click Computer > select Manage > select Disk Management)?
If you are booted into the live cd please go to the site below and download the boot script to the DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by matt_symes on 2010-12-04
Hi

Do you just have primary partitions (you can only have a maximum of 4)?  Have you set up logical partitions ?

Kind regards

---

### Post by StuMcBill on 2010-12-04
Please see Disk Management picture below as requested
[IMG]http://i28.photobucket.com/albums/c208/StuMcBill/diskmanagement.jpg[/IMG]

The unallocated space used to be part of the D:\ partition on this screenshot.

Thanks

Stu

---

### Post by matt_symes on 2010-12-04
Hi

Run the bootscript as suggested by quackers. It will give more information about your hard disk setup. Post the results.txt files contents back here between code tags.

Kind regards

---

### Post by Quackers on 2010-12-04
Thanks, that looks ok.
When you get here 
"I then go to the next step and I get the "Allocate Drive Space" screen. I am told that I have "free space - 26844Mb", I have selected this, and pressed the Add button, then go to the next screen, and set up the /boot partition as described in the tutorial."
When the partition manager has scanned your disc and the partitions appear, there should be an entry of "free space" (or unallocated space). Try double clicking on that entry and then set up your swap space by changing the size etc and click ok. Then when the other window returns and it has rescanned your disc the entry for "free space" will be reduced by the amount of swap you have just created. Double click on that entry again and set up your /root partition. But select logical for partition type - not primary.
I can see no reason for not continuing at this stage, unless it just doesn't like you clicking the "add" button again.

---

### Post by StuMcBill on 2010-12-04
OK, done!

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   323,151,871   302,178,304   7 HPFS/NTFS
/dev/sda3         323,151,872   572,710,911   249,559,040   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1027 MB, 1027604480 bytes
65 heads, 32 sectors/track, 964 cylinders, total 2007040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,007,039     2,007,008   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A69CC1EE9CC1B8D7                       ntfs       RECOVERY                      
/dev/sda2        16008CE8008CCFE3                       ntfs                                     
/dev/sda3        5C3698FB3698D6FC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        10EC-509B                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

Hope this helps!

Stu

---

### Post by Quackers on 2010-12-04
Thanks, that looks ok, but I think you've cut some off it :-)
Have a look 2 posts up for an idea.

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> Thanks, that looks ok.
When you get here 
"I then go to the next step and I get the "Allocate Drive Space" screen. I am told that I have "free space - 26844Mb", I have selected this, and pressed the Add button, then go to the next screen, and set up the /boot partition as described in the tutorial."
When the partition manager has scanned your disc and the partitions appear, there should be an entry of "free space" (or unallocated space). Try double clicking on that entry and then set up your swap space by changing the size etc and click ok. Then when the other window returns and it has rescanned your disc the entry for "free space" will be reduced by the amount of swap you have just created. Double click on that entry again and set up your /root partition. But select logical for partition type - not primary.
I can see no reason for not continuing at this stage, unless it just doesn't like you clicking the "add" button again.

Should I set /swap and /root before allocating /boot.  Because once I set /boot, I cannot set any other partitions.  All options except "Revert" are greyed out.

I didn't cut any of the results.txt file off, that was all that was produced?

---

### Post by Quackers on 2010-12-04
I personally don't have a /boot partition. My view is that it just over complicates things. Especially diagnosing booting problems.

Oh ok, a short one then :-) (boot script)

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> I personally don't have a /boot partition. My view is that it just over complicates things. Especially diagnosing booting problems.

Oh ok, a short one then :-) (boot script)

So I can just skip the /boot section, and go straight to /swap and /root?  Set them both as logical?

Thanks again for all the help!

---

### Post by Quackers on 2010-12-04
Yes, that's what I would do.

---

### Post by efflandt on 2010-12-04
> **StuMcBill said:**
> I then go to the next step and I get the "Allocate Drive Space" screen.  I am told that I have "free space - 26844Mb", I have selected this, and pressed the Add button, then go to the next screen, and set up the /boot partition as described in the tutorial.  This works ok.

When I go back to the "Allocate drive space" screen, I am told that the space is now "unusable" and has a size of 26344Mb.

I see one problem with that.  You need a root (/) partition, and if you assign all of your unallocated space to /boot, you have no place for /, hence, installation would fail.  You don't really need a separate /boot partition (unless you know what you are doing and have a reason for that).  If instead you set that partition sda4 as / (and ignore the warning about not having swap) it should work.

However, if you do not have enough RAM and/or want swap to be able to hibernate (not needed for suspend), you should create an "extended" partition, and then logical partitions within that for /, swap, and any other Linux partitions you want (maybe /home).  It is best not to make too many partitions initially when you have no clue what size they might need to be.

My new PC already had 3 partitions, so I just made 1 primary Linux partition for / and no swap. But I have 8 GB of RAM and do not really need to hibernate (I can suspend), so I do not have swap.

---

### Post by Quackers on 2010-12-04
That's true :-) I read /boot as /root, doh

---

### Post by wannacme16 on 2010-12-04
I have dual booted Windows & Ubuntu before and unless you have a particular need to specify your partitioning scheme you can let Ubuntu install side by side in place of the advanced partitioning scheme. The installer will automatically install Ubuntu onto the unallocated partition without the need for you to use the advanced partitioning feature. Remember the old saying keep it simple stupid.

---

### Post by wilee-nilee on 2010-12-04
m

---

### Post by Quackers on 2010-12-04
A bit on the harsh side wilee-nilee :-)

wannacme16, the newer installer is not quite as friendly.

---

### Post by wilee-nilee on 2010-12-04
n

---

### Post by StuMcBill on 2010-12-04
Well I have got it going.

Created a 4Gb swap, 6Gb \ and the remainder as /home.

So far so good.

I can boot into Ubuntu and Windows 7 from the Ubuntu grub (is this the correct terminology?) loader and all seems well.

Thanks

Stu

Edit:

One thing that does concern me is this (from the tutorial I was using):
> **Note: It has been reported that Windows 7 tends to mess with the  GRUB menu after a Windows update/upgrade. To avoid any issue that might  arise from that, you need to install GRUB to the boot partition of the  Ubuntu installation, then use EasyBCD to edit the Windows boot menu and  add an entry for Ubuntu. This method was used in [how to dual-boot Fedora 14 and Windows 7]("http://www.linuxbsdos.com/2010/11/09/how-to-dual-boot-fedora-14-and-windows-7/").  If you opt for this method, select the boot partition (/dev/sda3 in  this example) from the dropdown menu under Boot loader section.**

Is this something I *should* be concerned about? As I have no /boot partition, I cannot install GRUB to /boot?  Is this correct?

Also, what did you mean earlier about allocating all my space to /boot?  I only allocated 500Mb and the rest showed up as unusable?

Thanks again

Stu

---

### Post by Quackers on 2010-12-04
Excellent news :-)
I think grub menu is the accepted term, but we all know what you mean.
Have fun :-)
It would be good if you will mark the thread as solved using the Thread Tools near the top of the page. Thanks.

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> Excellent news :-)
I think grub menu is the accepted term, but we all know what you mean.
Have fun :-)
It would be good if you will mark the thread as solved using the Thread Tools near the top of the page. Thanks.

OK, will do. 

Do you have any ideas about the quoted text I have posted in my edit above?

Thanks

Stu

---

### Post by Quackers on 2010-12-04
As you have installed without a /boot partition and all installed operating systems boot normally we can assume that you have installed grub to the default place (the mbr of sda). This is fine and there will be no need to trouble EasyBCD :-)

Yes, I appreciate that you only allocated 500MB to /boot and I honestly don't know if that was in any way connected with your problem. It could have been to do with clicking on the add button rather than what we later did. I'm not sure.

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> As you have installed without a /boot partition and all installed operating systems boot normally we can assume that you have installed grub to the default place (the mbr of sda). This is fine and there will be no need to trouble EasyBCD :-)

Yes, I appreciate that you only allocated 500MB to /boot and I honestly don't know if that was in any way connected with your problem. It could have been to do with clicking on the add button rather than what we later did. I'm not sure.

Ok, so any updates I do to Windows should not affect my Ubuntu installation?

I did prefer having the "Windows Boot Manager" appear first, then when I select Ubuntu, then the GRUB menu appears (this was how it was when I had it installed via WUBI).  But never mind.

Could I (potentally) add a boot partition now that I have Ubuntu up and running?

Using System>Administration>Disk Utility?

Thanks

Stu

---

### Post by Quackers on 2010-12-04
It is more straightforward now! Just one menu. You can change the menu so that the default system is Windows if you want to.
You don't need a /boot partition to use EasyBCD. You can use it now if you want to.

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> It is more straightforward now! Just one menu. You can change the menu so that the default system is Windows if you want to.
You don't need a /boot partition to use EasyBCD. You can use it now if you want to.

Ok thanks Quackers.

It is more the "Windows update may corrupt everything and the world will end" scenario I was worried about! ;)

I guess I will wait and see! :D

Thanks again!

---

### Post by Quackers on 2010-12-04
Windows updates won't do anything to Ubuntu or grub. They could mess up Windows though :-)

---

### Post by StuMcBill on 2010-12-04
> **Quackers said:**
> Windows updates won't do anything to Ubuntu or grub. They could mess up Windows though :-)

Ha Ha!

Thanks for all your help!

Stewart

---

### Post by Quackers on 2010-12-04
Not a problem :-)

---

