---
title: "[SOLVED] Vista/Ubuntu Dual-Boot Partitions"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by alright on 2008-07-06
Hi,I'm new to Ubuntu.  I've installed it on an old laptop and fooled around with it a bit just to get a feel for it, and have just recently purchased a new laptop with Vista that I'd like to dual-boot.  

I have found the many tutorials on setting up the Vista/Ubuntu dual-boot as well as the partition guide on psychocats.net.  I know there are probably a million posts about this, but I couldn't find any that answered my question completely so figured I'd ask here.  I'm sorry if this is asked all the time.

I have a 160GB HDD with Vista currently installed.  There is a backup partition, but I plan on removing that, since it's empty anyways.  I wanted to have a partition that the Vista and Ubuntu share as large portion of the open space.  I figured breaking it up such as:

1: Vista [25GB, NTFS]
2: Shared Data [100, FAT32]
3: Ubuntu Home [10GB, Ext3]
4: Ubuntu Root [20GB, Ext3]
5: Swap [3GB]

So, Vista and Ubuntu share partition 2.  Partition 3 is where all of Ubuntu's settings are saved.  Partition 4 is where Ubuntu is installed.  And Partition 5, the swap should be the amount of memory?

From what I've gathered, I can shrink the Vista partition.  Then the through the Ubuntu setup, Partition 3,4,5 should be created in an extended Partition.

My questions are:

Do I create the FAT32 partition in Vista or in the Ubuntu setup?

and 

Do these amounts seem fairly reasonable?  I plan on installing a few programs on Vista, so I'm hoping that would be leave some room to play with?

Thanks so much in advance.

---

### Post by Pumalite on 2008-07-06
Allocate space with the Vista partitioner first. Then create an extended partition.You can do it with Partition Editor. Within that put the rest. /swap=RAM in laptops; otherwise 1 GB is enough.

---

### Post by AnonCat on 2008-07-06
The steps on the following website worked perfectly for me:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Be sure to pay special attention to how to setup Grub in the tutorial or it won't work.

---

### Post by wolfen69 on 2008-07-06
try the [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php") CD for partitioning. do this ahead of time and you should have no problems.

---

### Post by brian_utd7 on 2008-07-06
Hey, just a few thoughts. Having almost the exact same hardware specs that you do, I would bet that you have an HP laptop as I do. One problem that I ran into was not being able to extend the the free space of the backup partition. For some reason I couldn't get any partitioner to work on my hard drive. I first deleted the backup partition that came pre-installed. I tried extending that using the vista partitioner, gparted, and a couple other partitioners i found on the net. None of them worked. So I ended up installing the system files and everything on the 10g backup partition that came with the system, and at boot I mount the second hard drive that came with the laptop and use it to store all of my files. I contacted HP about having to go to all of this trouble, and they told me that I needed to buy a new Vista product key, re-install vista and then install Ubuntu. So about the long story but It was just a few thoughts that might save some time in the future.

---

### Post by Pumalite on 2008-07-06
Or Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by alright on 2008-07-06
> **Pumalite said:**
> Or Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

Okay, so I take it I should setup the partitions before even entering Ubuntu setup?

---

### Post by alright on 2008-07-06
> **AnonCat said:**
> The steps on the following website worked perfectly for me:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Be sure to pay special attention to how to setup Grub in the tutorial or it won't work.

I saw that earlier and had read it.  The only thing I am confused about is, is it entirely necessary to use EasyBCD and follow those additional steps?  If you have Vista installed, and then install Ubuntu, won't GRUB allow you to dual-boot?

---

### Post by Pumalite on 2008-07-06
You have more control that way. Then you install Ubuntu, go Manual and use the already prepared partitions:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Bucky Ball on 2008-07-06
> **alright said:**
> 

1: Vista [25GB, NTFS]
2: Shared Data [100, FAT32]
3: Ubuntu Home [10GB, Ext3]
4: Ubuntu Root [20GB, Ext3]
5: Swap [3GB]



All looking good. I have Vista/Ubuntu living happily together on my HP lappy with 80 Gb drive. You don't mention how much RAM you have; that would determine the size of swap, as mentioned previously, but generally RAM size x2 (opinions differ but this is pretty standard), a bit different for Windows I think (ram x 2.5?)

[QUOTE=]

My questions are:

Do I create the FAT32 partition in Vista or in the Ubuntu setup?

[/QUOTE] 

I would say either/or but all depends on what you've got to start! If you have Windows already installed ... before doing partition shrinkage of any kind, I would advise (in Windows) a defrag of whatever drive you are intending to manipulate. This will speed things up a bit and jam all the data together. I also advise backing up anything you might want to keep.

From Windows you can just leave free space and the Windows partition on the drive. Ubuntu has a manual partitioner option or it can install and deal with the free space on the drive of its own accord, allocating what it needs where. I always go the manual partitioning and it sounds like you would find it reasonably straight forward.

I am presuming you are talking Hardy Herron 8.04, desktop install? (easy peasy) If you are going for an alternate install image, be aware that it is text based and if you are not comfortable with that do a bit of research first. As I say, you shouldn't have too many probs either way by the sounds.

[QUOTE=]

I plan on installing a few programs on Vista, so I'm hoping that would be leave some room to play with?

[/QUOTE] 

If you were starting from scratch ...
Make your windows partition for the OS/programs only (20Gb about right as Vista itself chews up over 7!), leave the rest as free space and use the Ubuntu install cd as you don't require more NTFS partitions.

You will be asked in the grub install section about the existing operating system on your machine, if there is one, and whether you want to include that in your startup choices. Say yes, reboot and you should be up and running.

One small point, and if you have Windows up already an irrelevant one, but make sure you have windows installed on the first partition and Ubuntu on the second. Those more knowledgeable than I know the nuts and bolts of this, but Windows has odd disk ID protocols and loves to be on that first drive (you know like how it names all the drives what it wants to call them and allocates accordingly?). Trust me, it can get messy.

Cheers and good luck (Hardy Heron rocks even hardier than Gutsy!)

---

### Post by alright on 2008-07-06
Thanks a lot guys, definitely have either confirmed what I wanted or helped me decide what to do.  Can't wait to get Hardy up and running.

---

### Post by Bucky Ball on 2008-07-06
> **brian_utd7 said:**
> I would bet that you have an HP laptop as I do. One problem that I ran into was not being able to extend the the free space of the backup partition.

Brian, I'd say back-up everything (if necessary) and wipe the drive completely. Make one partition for windows and just leave the rest free space when installing Windows and do the rest with Ubuntu Hardy desktop install cd. When I got my HP dv6000, the first thing I did was make  Vista install disk then wiped everything. Second thing I did was load XP to find that it worked but recognised nothing, no usb or devices pretty much! No drivers exist are written for XP and this machine being the reason! Third thing I did was stick Vista back on and then Ubuntu.

At this point, probably going to install just Ubuntu before uni goes back as I barely touch Bill's Bloated Beast and I need that space.

Remember, Windows will only see the FAT32 drives, it recognises not (at all) EXT3 so the shared drive mentioned originally is a must if you need to access data from both OSs.

Happy travels ...

---

### Post by Bucky Ball on 2008-07-06
... as for Grub probs, this the bomb if your dual boot is not happening (although with Windows on the first disk and with Hardy, that is highly unlikely);

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Should get you out of any boot nightmare in a flash. You need to have a working machine to make your boot media, simple as that.

Cheers and have fun.

---

### Post by h0bbe on 2008-07-22
What do you guys think about sharing the /home-partition instead of making a separate partition for sharing between win and ubuntu?
Most of the files I save manually in /home is of such type that they could be good to have acces to from windows.

...or is it better, for security reasons, to keep /home only accessible from Ubuntu. If so, what partition sizes do you recommend for Vista, /root and /home. I want as much as possible left for the shared drive.

---

