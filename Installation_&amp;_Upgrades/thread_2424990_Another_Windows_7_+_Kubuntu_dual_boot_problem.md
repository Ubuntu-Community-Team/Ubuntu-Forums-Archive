---
title: "Another Windows 7 + Kubuntu dual boot problem"
date: 2019-08-19
forum: Installation &amp; Upgrades
---

### Post by anthonyl2019 on 2019-08-19
I'm on my 4th day and 15th attempt at trying to get Kubuntu to play with  my Win 7 install on my single drive HP Lenovo 8440p laptop with a 1Gb  drive.

For about a year I've had this machine running Win7 Pro, its original  OS, with Mint KDE added and had no issues with the install.  As Mint KDE  is coming to end of life and liking the KDE desktop I opted for Kubuntu  18.043 LTS and have faced issue after issue and reading the threads on  here have only served to add to my confusion which has been added to by  my attempt at pre-empting issues at  [https://www.kubuntuforums.net/showthread.php/75791-Before-I-start-From-Mint-to-Kubuntu](https://www.kubuntuforums.net/showthread.php/75791-Before-I-start-From-Mint-to-Kubuntu)  but it makes for boring reading.

My current state is best described by the boot-repair output at [http://paste.ubuntu.com/p/pmMJBcJnZ3/](http://paste.ubuntu.com/p/pmMJBcJnZ3/) and key output is:
```

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  17 Hidden NTFS / HPFS            <===Windows Recovery
/dev/sda2    *     24,578,048   625,139,711   600,561,664   7 NTFS / exFAT / HPFS           <===Windows 7
/dev/sda3         625,139,712   927,893,062   302,753,351  83 Linux                         <===Main Linux partition
/dev/sda4       1,211,078,654 1,953,523,711   742,445,058   5 Extended
/dev/sda5       1,252,040,704 1,953,523,711   701,483,008   7 NTFS / exFAT / HPFS           <===Shared Linux/Windows data
/dev/sda6       1,211,078,656 1,252,040,703    40,962,048  82 Linux swap / Solaris

and

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Basically I cannot get the Grub menu that I used to have with Mint.  
When I lost my Windows I did a Windows boot repair and that came back but the Grub menu has gone missing.  
If I reinstall Mint that'll be fine.  If I add Kubuntu to the Mint (creating sda7 and sda8) that's fine.  

The laptop is a few years old.  The BIOS supports UEFI but Windows boots in MBR mode.  
I've changed the BIOS to disable UEFI but that made no difference.

Kubuntu is asking questions about where the boot is to go, at the last attempt I said /sda3, I previously tried /sda2

All my installs are being done from ISOs burned to DVD.  
What do I need to do to restore the GRUB menu, retain a Windows boot and be able to get into Kubuntu please?  
And perhaps one for thought; why does Mint do it seamlessly and Kubuntu give me so much grief?

---

### Post by yancek on 2019-08-19
Are you able to boot windows?

If you look at the boot repair output at the very top it states the syslinux bootloader is installed in the MBR.  Not sure how that happened, maybe with boot repair but in any case, Grub is the default bootloader for Kubuntu and there is no sign in your boot repair output that Grub is installed.

Is sda3 where you had your Mint install?
Is sda3 where you tried to install Kubuntu?  

> Kubuntu is asking questions about where the boot is to go, at the last attempt I said /sda3, I previously tried /sda2

Are you using the manual/Something Else install method?  If so, you can leave the default for device for bootloader installation which should be /dev/sda.  That would install Grub to the MBR of the drive and put Grub boot files on the Kubuntu partition (sda3??).  Never install Linux boot files to a windows partitiion so sda2 would definitely not be correct.  Installing Grub to sda3 will not give you a bootable machine unless you have another OS with Grub which is not the case here.

Not sure what the problem is with your Linux partition but you might try doing a filesystem check on sda3 with the fsck command.  The link below gives an explanation and examples of using fsck.
[https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

---

### Post by anthonyl2019 on 2019-08-19
> **yancek said:**
> Are you able to boot windows?

Yes - and only to windows.

> If you look at the boot repair output at the very top it states the syslinux bootloader is installed in the MBR.  Not sure how that happened, maybe with boot repair but in any case, Grub is the default bootloader for Kubuntu and there is no sign in your boot repair output that Grub is installed.

Is sda3 where you had your Mint install?
Is sda3 where you tried to install Kubuntu?  


Yes, sda3 is where had the working Mint and where Kubuntu should now be.

Although I've tried to read up on it I'm not clear on where the bootloader should go and how or why it got into the MBR.  I don't know where things went with the Mint install which was working nor how they got there as the Mint install seems a lot more straightforward.


> Are you using the manual/Something Else install method?  If so, you can leave the default for device for bootloader installation which should be /dev/sda.  That would install Grub to the MBR of the drive and put Grub boot files on the Kubuntu partition (sda3??).  Never install Linux boot files to a windows partitiion so sda2 would definitely not be correct.  Installing Grub to sda3 will not give you a bootable machine unless you have another OS with Grub which is not the case here.


I've been using Manual, selecting SDA3 and reformatting it so that it is empty.  I'm assuming that If I say you "whole of disk" it will wipe everything?  Or will it only use free space?

> Not sure what the problem is with your Linux partition but you might try doing a filesystem check on sda3 with the fsck command.  The link below gives an explanation and examples of using fsck.
[https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

I currently can't get into Linux to even attempt this.  The computer boots straight into Windows.

---

### Post by SeijiSensei on 2019-08-19
I'd hive off a 512 MB chunk of that enormous 40 GB devoted to swap and create a separate /boot partition where grub can do its thing.  I've done this with all dual-boot systems and not had a problem.  Nowadays I use Windows so rarely that I generally just run it as a VirtualBox VM, but I have one dual-boot Windows 7/Kubuntu 19.04 machine with a separate /boot that works fine.

Once things are back up and running, I suggest running the "top" command at some point.  I bet you'll see most of the 40GB of swap space is not being used.

---

### Post by anthonyl2019 on 2019-08-19
Can I check that if I create another partition, which will have to be an extended partition, that it can be used as a boot partition?

The swap partition was automatically allocated when I first installed Mint.  

At some stage in the manual process I recall a question along the lines of "Mount point" for the Linux (sda3) and I have no idea what the response should have been.  I think I just put in /

---

### Post by SeijiSensei on 2019-08-19
Yes, sorry.  /boot has to be a primary partition on MBR drives. And, yes, the correct mount point for the Linux installation is /.  You most certainly do not want to install Linux to /dev/sda2; that would destroy your Windows installation.  Nor do you want the whole-disk option; that would blow everything away.

I'd give this a try.  Install Kubuntu to the swap partition and leave /dev/sda3 alone for the moment.  A complete Kubuntu installation fits in less than 10 GB.  When asked where to put the boot loader specify /dev/sda.  If you end up needing swap, you can use a [swap file]("https://ubuntuforums.org/showthread.php?t=2424008&p=13876856&viewfull=1#post13876856") rather than a dedicated partition.  Usually swap is, at most, twice the size of installed memory.  On this machine less than a gigabyte of swap is currently in use.

---

### Post by oldfred on 2019-08-20
BIOS based systems boot from MBR. And each drive only has one MBR, so if one drive, you must have grub in MBR of that drive.

So even installing Kubuntu to sda3, you have to install grub boot loader to sda which will  install it to the MBR of sda, not to any partitions like sda3.

Grub only boots working Windows, so make sure you keep Windows fast start up or always on hibernation off. Windows may turn it back on with updates & then you may need Windows repair disk to temporarily install Windows boot loader to directly boot it and turn fast start up off again. Then use Boot-Repair to restore grub to MBR of sda.

---

### Post by anthonyl2019 on 2019-08-20
I'm getting ready to install Kubuntu now and have done some resizing so I have more flexibility with extended partitions but I note that my Windows partition /sda2 has /boot marked against it.  Is this a problem that will go away when I install Kubuntu and specify /sda for the boot or do I need to do something first?

---

### Post by yancek on 2019-08-20
Windows systems need to have the partition with boot files marked as active/bootable in order to function.  This is not necessary with any Linux so you should not have to do anything else, just make sure you install Grub to /dev/sda which should be the default.

---

### Post by anthonyl2019 on 2019-08-20
Success, untidy but success. Adapting from the suggestions above I
shrank the /sda3 partition, used the free space to create /sda7 (512Mb
but unused) and /sda8 (for the main new install) and ensured /sda as the
boot. 

I'll tidy up the partitions at some future stage and no doubt will have
lots of other questions which I'll post in the appropriate forums.
Thanks for your help. 

I tried to add a picture of the bootsceen but my post got lost/rejected and you'll know what it looks like anyway.

---

