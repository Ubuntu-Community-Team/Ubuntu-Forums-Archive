---
title: "Installing ubuntu to dual-boot with a windows 7 software raid0"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by Rythh on 2011-02-23
Hey all,

           I've recently upgraded my computer, and bought two 80gb SSD drives, placing them in a software raid0 with windows 7. The other day, I attempted to install ubuntu on one of my older hard drives, using easeus to create a 60 gb partition, and then i manually set up my partitions to include my / and /home and swap on the older hard drive, while putting my boot loader on the drive that ubuntu defaulted to (it was ssa if i recall correctly).  This was, obviously, before I understood that it wouldn't work because of my software raid. What happened for me was that I would always load ubuntu, and not be given the choice for anything else. 

       So having now fixed my mbr and erased my ubuntu install on my old hard drive, I am asking how, if possible, i can set up a dual boot with my windows 7 raid0 and ubuntu 10.10. I used a startup disc for the ubuntu install, I still have my windows 7 disc, and I am looking for any advice I can get on how to get a dual boot working, preferably in a step by step variety if at all possible ^.^   I'm sorry if I gave more information than is needed for my problem, and conversely, if any other information need be provided for a solution please just ask and I will quickly get back to you the answer. 
    
Thank you!

---

### Post by ronparent on 2011-02-23
Win 7 accesses raid thru a software raid assisted by a raid chip set on the MB. Ubuntu uses a software package called dmraid for the same purpose. 10.10 comes with dmraid packaged with it and is usable with a fakeraid disk set to see the raid drives from the live cd. The catch is that unless you are installing to the raid set dmraid is not installed with your 10.10 system and therefore your system will never see the raid partitions.

No problem. Simply boot into ubuntu on the separate non-raid drive and install dmraid - 'sudo apt-get install dmraid'. Then simply run sudo update-grub to find your win7 install and to automatically enter it into the grub.cfg. After that everything should show up in your grub boot menu. Post if you need more help (you didn't say which drive was set as boot in bios). If need be grub reinstall is a simple proceedure and can be done as often as needed until done right.

---

### Post by Rythh on 2011-02-24
Awesome, thank you very much for the answer.  The only question I have remaining is this, when I install ubuntu I use easeus to partition my drive and then manually install the ubuntu partitions as well, how would you recommend I partition my ubuntu? Assuming about 70 gigs set aside on my E drive for ubuntu, where would you put the boot, swap, root, and home partitions and how much set aside for each?

Thank you again :)

Edit: Also to answer your question, my raid drive, or C, is set as my boot in bios.

---

### Post by ronparent on 2011-02-24
70Gb would be plenty. You are able to share data files in windows partition so unless your storage need are extensive you should have no problems. All partitions will function fine within an extended partition so if you are in danger of exceeding a four primary partition limit you can install to a logical partition within an extended. 

You need primarily the / and a swap. A separate /home is optional. Except for special circumstances any other separate partitions are unnecessary and probably inadvisable.

The Ubuntu install on a separate hd from your current ssd raid set will probably install the grub boot loader on that same disk. That being the case you will have to set that disk as boot in bios to access your install. Since Win7 is not accessible on the raid yet it will not appear in the grub boot menu. After installing dmraid you will need to 'sudo update-grub' in a terminal to add your Win7 to the boot menu. Everything should now be set. Post if you have any problems.

---

### Post by Rythh on 2011-02-25
Alas! More problems to fix! ^.^

   When I installed ubuntu I chose my D drive and put every partition on my D drive (as logical partitions) including the boot loader.  When I finished installing and went into my bios to set my D drive as the priority, I came up with an error and it asked for grub rescue.
   After that, I changed it back to my windows raid as the priority.  When I did that ubuntu loaded, with no option for choosing windows.  So I downloaded dmraid as you suggested, and updated it, no windows came up.  I then upgraded dmraid, no windows came up.  It never seemed to recognize my windows loader or the raid (I verified with restarting my  machine), and any time I set the boot priority to the D drive it wouldn't load. 
    Where I'm at now is I repaired my windows boot record (probably wiping out the grub loader, otherwise it's still sitting on the D drive where I couldn't seem to access it).  Any and all suggestions will be, with many thanks, welcomed. :)

---

### Post by ronparent on 2011-02-26
It sounds like your install defaulted to place the boot loader on the raid (which was probably still designated as boot at the time). You have restored the windows boot loader on the raid which give you access to your windows but not the Ubuntu - absolutely no problem with any of this. Things seem to be working as they should.

Now for a bit of background. The purpose of dmraid is to discover your raid drive from the meta data imprinted on each of the component disks (ssd's in your case). The program then sets up the symbolics links used by your system to access the file system on the raid (as identified by the meta data). These symbolic links will appear in your file system in the location **/dev/mapper**. Once these links are written your file system should be ably to access your raid partitions. You should be able to verify that dmraid is function properly by looking at /dev/mapper (**ls /dev/mappe**r).

Once /dev/mapper is populated you should be able to find any systems installed on your raid when either '**sudo grub-install**' or '**sudo update-grub**' is run. At this point since, you don't have the grub boot loader on what you refer to as d:, you have to run grub install to place it there. This reference will tell you all about reinstalling grub: **[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2**

You will probably already noted that the hard drive designations in linux differ from what you are accustomed to. In linux the drives are indicated as sda, sdb, etc. in the order in which they appear to the system. The partitions are further designated as sda1, sda1, etc. for each of the drives. Those will be the notations you will use in designating them for the reinstall.

To finish setting your self up you will follow roughly these steps:

1) Change the boot order in bios to designate the separate hard drive you have installed Ubuntu to as boot.

2) Boot to a live cd. If you want you can use it to look around your system a bit and verify for your self that the /dev/mapper links are in place. Now open a terminal and write '**sudo blkid**'. This will identify all the block device on your system including the location of your windows and of your Ubuntu install. Remember the partition your Ubuntu is installed on. This will give you the designations for the drive and partition you will be reinstalling rub to.

3) You now use the two step method in the reference I gave you to reinstall grub so that it will boot the hard disk your Ubuntu is installed to. First mount the partition of the install as described to **/mnt** in you live cd file system. Then install grub with the grub boot loader to the locations - grub to the temporary **/mnt/** location (note you will have to reference this location exactly as I have written it) and the boot loader to the corresponding drive location (sda, sdb, etc).

4) Boot to the sustem. Verify that dmraid is actually installed. Write '**sudo dmraid -ay**' to a terminal. If it is not installed, install it (**sudo apt-get install dmraid**). If it wasn't installed, you will have to run '**sudo update-grub**' to update your grub boot menu to find windows on your next boot. 

Now everything should be set. Post if you still have problems.:D

---

