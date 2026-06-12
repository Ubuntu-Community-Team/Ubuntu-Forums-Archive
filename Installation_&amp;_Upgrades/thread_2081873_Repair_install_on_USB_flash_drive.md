---
title: "Repair install on USB flash drive"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by AFMARS on 2012-11-07
HELP,  I am a casual user of Ubuntu  12.04 LTS on a 32GB stick on a Vista Machine.  I like ubuntu  for browsing as it is faster,  When I installed,it set up 5GB or so and I have run out of user room and tried to expand using G Parted. Of course it will not boot  just errors and sits and blinks cursor.  

I have a bootable copy of boot repair on  a separate stick.  My question is how to set  boot repair so  it targets the ubuntu  usb stick and not Vista on the hard drive??

I am lost past the GUI  so keep it simple please.

JIM

---

### Post by oldfred on 2012-11-07
Welcome to the forums.

Moved to your own thread.

When you run boot repair it should find all your installs, Vista & Ubuntu. Check off that your Ubuntu is a removable drive. Be sure it is plugged in when you run report.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

I label my flash drives and they get mounted as the label. You can add labels with gparted, disk utility or command line. Default labels may include spaces which then require quotes around label to use it.

---

### Post by AFMARS on 2012-11-08
Fred , I have not punched the auto repair button yet so do not know what happens when I do.  Does it take off  or give me some options like selecting the drive OR do I need to select the drive  under the advanced options screens??

I am confused by linux terms   like   tty vs com port in windows.    I know you all think it is easy but  but what is needed is a  linux to windows terms dictionary  which as far as I know does not exist.  

I do not want the headache of trying to get Vista  debugged.  It is all the trouble I want when it is running right.  So I am a little chicken .   

Thanks for your patience .   

JIM

---

### Post by oldfred on 2012-11-08
You really do not need to know tty or com ports to use Ubuntu. 
tty is  Teletype (TM) which only old timers would even know what it is. And com is com port and was extremely difficult to configure in DOS or even Windows to get a printer to work.

Do not run the actual repairs yet from Boot-Repair, but run the BootInfo report and post the link it gives you to that report so we can review the details of your configuration. then we can better suggest what to do.

---

### Post by AFMARS on 2012-11-17
Fred 


[http://paste2.org/p/2491516](http://paste2.org/p/2491516)

My reading tells me  I have made the program an orphan and the boot sector is ok.  Is that more or less correct?   Any  wisdom?    

Fred you have hit the needle on the head .  Old timer   , my primary interest in linux was to run radio programs  FLDigi etc .  Radio is my love.  I was first introduced to computers in  1966 on the Univac 418 and 1004.  (Google.) 

Lots of tape mounts and un-mounts. Changes were done with large plug boards, one person to plug, one to check.   Plug data was on 128 column sprocket feed paper often times3-4 inches thick.   Was not a lot of fun.  

Vic20 was my first owned computer, again to run radio teletype software.  I also learned I did not want to write code.   

A buddy George , (passed away)  worked for Oracle in Orlando.;  He got me to get a knoxpix  CD.    He said it was easy, and I guess it was if you are a UNIX engineer.   I have remained a casual user .

Well am I going to be able to fix or am I starting over.  ??

JIM:guitar:

---

### Post by oldfred on 2012-11-18
If sdc was your Linux install, it is now showing as FAT16. I see no Linux partitions.

Did you just have the installer version that boots to install or use as liveCD? That would normally be in a FAT32 partition, not FAT16.

What would you like to do now, you have lots of choices as it looks like you are starting over.

If you had some data on the Flash drive it might be recoverable with testdisk, photorec or other tools that just scan a drive for anything that looks like a file. Testdisk may find old partition structure and recover drive. Photorec does not recover full file names, just extensions and takes a while, but with only 32GB to search maybe not too long.

With a 32GB flash drive you can install a full version. You also have only used about a third of your hard drive with Windows in sda2. You could shrink Windows (Use Windows partition tools)  and install Ubuntu on the hard drive in the unallocated space (auto install) and dual boot. 

Let us know what you want to do and we can advise. 

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by AFMARS on 2012-11-19
[SIZE=4]Thanks Fred for your help.   I will reformat the 32GB stick and start over.  I would like to have a 25GB section for adding programs and files on the stick.  That is how I got in t[SIZE=4]rou[SIZE=4]ble with [SIZE=4]Gpart[SIZE=4].[/SIZE][/SIZE][/SIZE][/SIZE]

Can I do that when loading using Unetbootin windows  in the block that is for "[SIZE=4]preserving[/SIZE] files  [SIZE=4]across[/SIZE] reboots"? Will it take  25 [SIZE=4]MB??[/SIZE][/SIZE]

[SIZE=4]JIM[/SIZE]

---

### Post by oldfred on 2012-11-19
With 32GB I would just do a full install.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

You can add partitions with persistence, but I have never done it. I have a full install in 8GB and use another 8GB for data in my 16GB flash drive.

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

   With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

       Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

    But an install to a flash drive is just like any install to a second drive, with a few settings like a SSD to reduce writes and improve speed.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
    
Some suggest the lighter weight version as it may load faster. Once loader if you have a fair amount of RAM system still can be decent.

       HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

       With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

---

