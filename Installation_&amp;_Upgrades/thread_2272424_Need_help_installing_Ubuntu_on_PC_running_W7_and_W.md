---
title: "Need help installing Ubuntu on PC running W7 and W8.1."
date: 2015-04-06
forum: Installation &amp; Upgrades
---

### Post by tim105 on 2015-04-06
***(You, from the future, read post [http://ubuntuforums.org/showthread.php?t=2272424&p=13259939#post13259939](http://ubuntuforums.org/showthread.php?t=2272424&p=13259939#post13259939) for solution)***

I am trying to install Ubuntu 14.04 on a laptop already running Windows 7 and Windows 8.1.

Below is a screenshot of the current Disk Management window:

[ATTACH=CONFIG]261125[/ATTACH]

As you can see, I have an unallocated space of ~50GB, which is where I want Ubuntu to be installed.

I have gone through the pre-installation process and when I get to the screen to select which installation type I want, I select *install alongside them* and get the following message:

[ATTACH=CONFIG]261126[/ATTACH]

I had watched a few tutorials on installing Ubuntu and was under the impression that Ubuntu would automatically detect the unallocated space and install itself there, however, that doesnt seem to be the case and I'm confused.  I don't want to accidentally wipe out all the data I have on both hard drives.

1st Hard drive = W7
2nd Hard drive = w8

I need ubuntu on 2nd hard drive.


Thanks! ;)

---

### Post by oldfred on 2015-04-06
With multiple drives much better and safer to use Something Else.
Also Windows only boots from one drive set in BIOS, and then one partition with boot flag. All other installs move boot files into that partition. So your Windows 8 boot files are probably in the Windows 7 partition and BCD just has two Windows entries.

If you can boot from sdb, then you want to use Something Else as that is the only option that also includes the option to specify where to install grub2 boot loader. It defaults to sda, which usually has the Windows boot in the MBR and you want to keep that in the MBR. 
But after you install grub2's boot loader to the MBR of sdb, you want to change BIOS to boot from the drive that is sdb.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
      
 And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

Still with any major system change you need to have good backups which you should have anyway. Hard drives fail, users make mistakes and 'stuff' happens. If you have backups & current version repair disks for every system you have installed then it is not a major issue. 

You have BIOS installs which means drives are MBR(msdos) not gpt, but links in link in my signature in newer UEFI installs for backups and partitioning info may be useful, but all the UEFI info does not apply.

---

### Post by tim105 on 2015-04-06
Hi!

I appreciate your assistance.  It's been so long since I last installed Ubuntu, I previously had it installed as a second OS *dual boot*. I remember the installation process was much easier, perhaps age is catching up lol.

Anyway, here are a few screenshots of the current window I have on the installation page.   I will appreciate it if you could point me to the right direction *Your previous answer was very helpful, btw.*

Selected something else - part 1:

[ATTACH=CONFIG]261141[/ATTACH]

Part 2:

[ATTACH=CONFIG]261140[/ATTACH]

Highlighted Free Space *this is the space I want to use for Ubuntu*:

[ATTACH=CONFIG]261139[/ATTACH]

The next screenshot shows the window I get if I click on the *+* sign on the left side:

[ATTACH=CONFIG]261138[/ATTACH]

If I'm on the right path, what should the next step be?   

Bootfile is on C drive *W7*
Windows 8 is on D drive *2nd physical drive*

Thanks

---

### Post by oldfred on 2015-04-06
Combo box at bottom shows sda, you want to change to sdb. 
Usually we add another partition for swap. If you have 4GB of RAM or more you may not use swap much if at all. Only if hibernating would you need swap equal to RAM in GiB not GB. But Ubuntu boots fast enough and hibernation hardly saves anything. Best to have a little swap like 2GB, just in case.
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

You already have several other NTFS partitions, so you do not need a NTFS data partition. I do prefer to have smaller system partitions like 25GB for Ubuntu and 40 or 50GB for Windows and then have all data in shared NTFS data partitions. Then all systems can use same data more easily.

---

### Post by yancek on 2015-04-06
In the last image you posted, you can use either primary or logical for partition type.  Might as well use primary.  You need something in the mount point box.  Click the down arrow to the right of the text box and you should see the forward slash ( / ), symbol for the root partition.  I would shrink the total size at the top by about 4GB and use that free space for a swap partition although you may not need it.

---

### Post by tim105 on 2015-04-06
HI!

I can't thank you enough for your assistance.  Upon doing some more research, I found out that my HP laptop's BIOS WILL NOT allow me to specify which Hard Drive I wish to boot from (Can only select Harddrive, USB, DVD).  So, what I'm saying is that I wont be able to boot from sdb if I do decide to install the bootloader there.

Now, I do have a much clearer picture on what I need to do to get Ubuntu installed, however, I do have one question:

Would I be able to run ubuntu along with my other two OS's IF I install Ubuntu's bootloader in the default sda while installing Ubuntu  on sdb?  

Thanks

---

### Post by oldfred on 2015-04-06
Usually under hard drive entry would be multiple hard drives if they have boot loaders.
But some older BIOS, did not allow booting from a second drive. But just about any newer BIOS that can boot a USB drive can boot from any drive. My older system actually booted USB flash drives as another hard drive. It took me a while to realize all the USB boot entries would not boot my flash drive. Then one day with it plugged in I looked under hard drive entries and there was flash drive.

You should be able to boot any install anywhere. But a few systems do not load second drive as bootable. You may just need grub in MBR of sda, or a /boot on sda to make it work. A few have loaded grub to a flash drive to boot Ubuntu also. Boot loader can be on any drive that is bootable by BIOS. UEFI a lot different.

---

### Post by tim105 on 2015-04-07
Yes, some pcs do allow you to select the hard drive, sadly, mine does not.

anyway,  is it safe for me to go ahead and install the boot loader in the default location (sda) even if Ubuntu will be installed in a different location?   I already created both partitions (ext 4 and swap) I'm ready to click the "install now" button lol.

thanks again

---

### Post by tim105 on 2015-04-07
I was able to install Ubuntu successfully :)

I am able to boot all 3 OSs, but I would like to have W8's bootloader as default and then select Ubuntu whenever I want it rather than having Ubuntu's loader as the default.

I dont know if I should start a new thread or continue with this one.

Thanks.

---

### Post by tim105 on 2015-04-07
I would like to thank you guys for pointing me to the right direction.

I was able to install Ubuntu on second hard drive, same hard drive that has W8.

I got rid of the Ubuntu bootloader by fixing/restoring the W8 bootloader *bootrec.exe fixmbr* command in cmd.  Once I booted into w8, I installed easybcd and added Ubuntu.

I am now able to choose which OS I want to use from the W8 bootloader (w8,w7, Ubuntu).  

If this helps anyone in the future, here is what I did:

1. Created space in Windows Disk Management for Ubuntu (I gave it 60GB unallocated space)
2. Downloaded Ubuntu .ISO onto USB drive.
3. Booted PC from USB drive.
4. Selected Try/install Ubuntu
5. Proceeded with the pre-installation screen.
6. Selected *Something else* under Installation Type
7: Highlighted 60GB unallocated space I previously created in Windows Disk Management
8. Clicked the + sign on the lower left hand side.
9. Created ext 4 partition *50 GB* - Logical - set Mount Point as: /
10. Highlighted remaining unallocated/free space Clicked the + sign on the lower left hand side.
11. Created swap partition *10 GB* - logical.  (installed ubuntu bootloader in default location dev/sda)
12. Clicked install now *began installation process*
13.  Confirmed that I wanted to continue (will indicate that two partitions will be formated, same two I created)
14.  Installation took about 4 minutes to complete.
15. Restarted PC and Ubuntu bootloader showed up as it took over Windows' bootloader.
16. Selected w8 from bootloader option.
17. Clicked *Other options* within w8 bootloader: troubleshoot, advanced options, command prompt
18. Ran the following command:  bootrec.exe fixmbr
19. Restarted PC. (W8 bootloader showed up instantly.)
20: Booted w8.
21: Downloaded and installed EasyBCD
22. Added new entry (Linux, grub 2, name: Ubuntu, Linux partition)
23. Restarted PC once more.
24. Done.  

I ended up with 3 options to choose from (w7, w8 and Ubuntu)


Once again, thank you very much for your assistance.   :D :popcorn:

---

