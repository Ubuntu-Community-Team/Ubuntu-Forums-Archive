---
title: "Dual boot with windows 8.1 not going well"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by geckoboy3 on 2014-04-18
So I successfully downloaded Ubuntu and have the option to boot either it or windows. However, I have yet toget into Ubuntu because for the past 4 hours I have been selecting it. Then, a unbuntu page comes up and it freezes at a part of the installation process. The only way to escape is to turn the pc off. Why is this happening?


thanks in advance

---

### Post by squakie on 2014-04-18
Have you tried the "Try Ubuntu" option from the live media without actually trying to install it yet?  If not, try that and report the result of that try.  Is the Ubuntu page that comes up one with the word Ubuntu across it and little dots below the word?

Can you post what your hardware is - make/model/cpu/memory/video adapter/wireless adapter (if known) - things like that.  If we know the hardware that is having the problem, we might be able to help you.

Don't give up!!  ;)  We've all been there at one point in time.

---

### Post by geckoboy3 on 2014-04-19
The hardware is all new. It run on:
Intel Core i7-4770 3.40 GHz 8MB Intel Smart Cache LGA1150 
FLASHMEDIA: INTERNAL 12in1 Flash Media Reader/Writer MEMORY: 8GB (4GBx2) DDR3/1866MHz Dual Channel Memory (ADATA XPG V)
MOTHERBOARD: * GIGABYTE Z87X-HD3 ATX w/ On/Off Charge 2, Realtek GbLAN, 2 PCIe x16 (1 Gen3, 1 Gen2), 3 PCIe x1, 2 PCI   NVIDIA GeForce GTX 770 2GB GDDR5 16X PCIe 3.0 Video Card (EVGA Superclocked ACX Cooling) 


The pictures demonstrate where I get stuck. The bit after it reaches 0 is where it is perpetually glitched.

---

### Post by geckoboy3 on 2014-04-19
Hello?

---

### Post by QIII on 2014-04-19
Please wait at least 24 hours before bumping your thread.  By doing it so quickly, you have done two things:

1.  Removed yourself from the unanswered posts list before the folks who look for those threads specifically have had time to find it.

2.  Made the impression that you are impatient.

This is a community made up entirely of volunteers who donate their time as they have it to provide support.  People come from all time zones around the world and it is entirely possible that the person with the very best answer for you is sleeping, at work, having dinner with his family, etc, at this very moment.

Please be patient and courteous.

ALSO:

***Threads merged***.  Please do not create multiple threads with the same subject.

---

### Post by squakie on 2014-04-19
Okay, it's a dual-boot Windows 8.1 and Ubuntu.  With Windows 8 it has to be UEFI, so did you read up on everything for Ubuntu and UEFI?  Do you have fast boot disabled in the BIOS?  Do you have secure boot disabled in the BIOS?

I know these are just a couple of the starting points.

It may also be your video needing a driver - I would search this forum with your video card and/or search the net with:

ubuntu 13.xx geforce GTX 770

in the search string

it's possible you might need something like nomodeset in the boot options.

However, I still need to know if you ever booted the install media and selected "Try Ubuntu".  If not, try it and let us know what happens with it.  This may help us know if it's something with the install or just something in general with the way you installed.

Also, oldfred is an expert on the UEFI "stuff", and a recent thread of mine he noted that grub has a hard time booting with secure boot on, so I would be sure that is off in the BIOS.


EDIT!!!!!:  I mis-interpreted what you were saying on the screen shots.  Are you saying the first screen shot is where the installation itself hangs at the "0"?    It's possible it still might be the UEFI things - try turning off fast boot and secure boot in the BIOS and see what happens.  The 3rd screen actually looks like a Windows boot manager, not the grub boot manager from Linux - seeing that after my initial comments is what made me re-read you post and look at the 1st screen.

---

### Post by geckoboy3 on 2014-04-19
[ATTACH=CONFIG]252227[/ATTACH]Thank you for your suggestions. After checking my bios, it looks okay. Do you see any problems?

I will keep trying todo this, but it is incredibly frustrating (if you can imagine).

---

### Post by squakie on 2014-04-19
I didn't see anything there referring to secure boot, unless that's what "Security Option".  If so, I don't know what "System" means in this case.  I would look in the book for your motherboard and see what it says.  Beyond that, it's getting past my comfort zone to suggest more without me doing a lot more research on the net.

I would try the nomodeset option for boot as well.  You can add this on the "Try Ubuntu" option on the live media as well.

---

### Post by geckoboy3 on 2014-04-19
> **squakie said:**
> I didn't see anything there referring to secure boot, unless that's what "Security Option".  If so, I don't know what "System" means in this case.  I would look in the book for your motherboard and see what it says.  Beyond that, it's getting past my comfort zone to suggest more without me doing a lot more research on the net.

I would try the nomodeset option for boot as well.  You can add this on the "Try Ubuntu" option on the live media as well.
My secure boot status is "unsupported", so I assume it is off.
 
the advanced options for booting are:
normal mmodes are graphic mode
acpiworkarounds 
verbose mode 
and demo mode
Which of these should I select?

---

### Post by oldfred on 2014-04-19
Every vendor and every model of computer has new UEFI settings. Even with old BIOS it was hard to keep track of what settings work. Often users end up having to experiment and most then do not remember what they changed ot make it work or do not post back what does work.
With my own old BIOS I had to take photos like you have done, to document settins as it reset to defaults on every BIOS update.
Have you updated UEFI/BIOS to latest version?

Some other Gigabyte boards, older ones may not have same issues.
       Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

   Gigabyte's ASPM Motherboard Fix: Use Windows
[http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg)
Gigabyte GA-Z87X-UD3H, Ubuntu 13.10, and Intermittent External USB Drive Failure 
[http://ubuntuforums.org/showthread.php?t=2194155](http://ubuntuforums.org/showthread.php?t=2194155)

Updates to kernel, support software & video drivers have made 14.04 work a lot better with new hardware. 
But with nVidia you will need nomodeset on every boot until installed with nVidia proprietary driver. Also usually best to only install from Ubuntu repository. Only a few very new nVidia cards may need the very latest from a ppa or nVidia directly. And each type of install repository, ppa or nVidia directly may conflict so do not attempt to install from more than one source without through purge of older version.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by squakie on 2014-04-19
Oh man I am SO glad you're here oldfred!!!  I'm just going to be on the sidelines watching and learning now ;)

---

### Post by geckoboy3 on 2014-04-19
I entered the commands. However, it still goes to the screen that says: 
completing the Ubuntu installation.
For more installation boot options, press esc now...
0
then has a _ blinking.


This is the same problem as before; nothing had changed.

what is wrong with ubuntu/my computer?! I'm at the point where I am beyond frustrated, and have spent over 10 hours trying set it up myself, and had someone else helping me for another three and I have gotten no where.

---

### Post by oldfred on 2014-04-19
Are you getting blank screen at end of install? 
Or after rebooting and selecting ubuntu entry in UEFI menu?

Does try Ubuntu work if you add the nomodeset as above?

---

### Post by geckoboy3 on 2014-04-19
This is the page that I am frozen on 
(attached)

---

### Post by oldfred on 2014-04-19
Can you shut down.

With Linux you always want to try this first.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Is system fully installed but not shutting down afterwards correctly?
Can you boot into live mode, try Ubuntu?
Are you choosing to install restricted extras and proprietary drivers?

---

### Post by geckoboy3 on 2014-04-19
1.It is fully installed, but freezes before I can actually use it. 
2. No.
3. Yes and I cannot undo that as I can't actually access the os.

ps it's a desktop not a laptop.

any ideas of what's going on?

i put the cd back in and am currently attempting to boot it without installing. It is a solid black screen right now...

---

### Post by oldfred on 2014-04-19
I just fully installed 14.04 with updates into my SSD which will be my new working install once I get it configured. 
On the progress bar at bottom, does it finish the installing grub, then uninstall some software not needed in your install and then finishing?

This is the last screen I get.
Then I go into BIOS and choose to boot that new install. But my system is BIOS not UEFI so it is a lot different.
I also have to add nomodeset into grub menu item for it to boot. Then install nVidia driver.

This says your video card should work.
[http://www.phoronix.com/scan.php?page=news_item&px=MTUyMTI](http://www.phoronix.com/scan.php?page=news_item&px=MTUyMTI)
But this says Nouveau driver does not work well and may be part of your issue?
[http://www.phoronix.com/scan.php?page=article&item=nouveau_geforce_700&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_geforce_700&num=1)

---

### Post by geckoboy3 on 2014-04-19
I followed your suggestions and was able to boot from the cd without actually installing. Thank you so much!

now that I'm in, however, when I tried to download it, it says:

installation type 
this computer currently has no detected operating systems. What would you like to do?
erase disk and install Ubuntu 
encrypt the new Ubuntu installation for ssecurity 
use lvm with the new Ubuntu installation
sonething else

what does that mean? I should still have windows 8.1. Could the fact that I also have unbutu downloaded already, but it is faulty, har anythig to do with it? What should I select?

your help is greatly appreciated, as without you I would have never gotten this far.

---

### Post by squakie on 2014-04-19
Glad too see I at least didn't lead you astray!  oldfred is an expert at all of this, and I relied on the various posts he has done on dual booting with win8, uefi, etc., to try on my new laptop.  I was one of the extremely lucky ones - it worked right away!

I'm sure they'll get you going.  Glad you finally booted the live media.

---

### Post by oldfred on 2014-04-19
Before installing.
In Windows use Windows disk tools to shrink Windows NTFS partition and reboot so it can run chkdsk to update itself to its new size. Do not create any partitions in Windows, that may create even bigger issues.
Make sure secure boot is off.
Make sure fast boot is off.
Windows often turns these back on when ever you do Windows maintenance or updates.

Did you boot installer in BIOS or UEFI mode?
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

If it still does not show Windows I would not use any auto install options. And all the LVM options are full drive or erase everything options.
So that leaves something else but it is a bit more complex. I prefer to create partitions in advance with gparted from live Installer, but you can create them as you install
If a new user you only need two / (root) and swap. I show me installing a new / partition in #17 above. I already had the partition so I just clicked change. If you want new partitions in the unallocated space you click +.

---

### Post by geckoboy3 on 2014-04-19
It is booting straight to Ubuntu now... It is going me these options:

try Ubuntu
install unbuntu 
oem install
Check disks for defects


how do I access windows?!

edit: I ejected the disk and am back in windows. I already shrunk windows but downloaded the previous (faulty) Ubuntu in the freed space. How should I go about reinstalling Ubuntu?

---

### Post by oldfred on 2014-04-19
If you have unallocated space, does the installer show Windows?
If not you should only use Something else or manual install.

If a new user you should be fine with / (root) and swap. You could add either a separate /home and/or another NTFS data partition. Generally better not to write into the Windows system partition. But you still have to keep fast boot off or any hibernation in Windows as that also may keep the NTFS data partition mounted. I do not know a way in Windows to unmount a d: drive or you data partition.

I showed a couple screens above, this shows some more.
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

The 14.04 install is essentially the same as shown above, and you should not need Boot-Repair as grub2's os-prober has been fixed.

---

### Post by geckoboy3 on 2014-04-20
Hello, 
i followed the instructions and now have Ubuntu booted and installed.

however, my windows is now gone. It is nowhere to be found. How do I get back to windows? I really need to be able to use both os's and am freaking out because I need to use windows just as much as I need to run Ubuntu.

Update:
I am freaking out right now. I can't find it anywhere... I think I might have downloaded ubuntu in window's place. I know I selected "other options" in Ubuntu (in order to not replace windows) but when I chose the biggest available space, I think it might have been occupied by windows. 

HELP!!!! I need to get windows and Ubuntu.

---

### Post by oldfred on 2014-04-20
Did you make the full backup of Windows?
If you overwrote Windows there will be no way to get it back in working order. If you had some data not backed up it may be possible to recover some of the data, but it is a long process.

Did you also overwrite the recovery partitions?

Post this:

       sudo parted /dev/sda unit s print

If you only shrank Windows a small amount why did you then install to the largest partition?

---

### Post by geckoboy3 on 2014-04-20
I am really stupid and wasnt thinking. I saw the largest amount of unused space there so thought that I should use it.

sudo parted /dev/sad unit s print reveals this:

model; ATA ADATA SP900 (scsi)
Disk /dev/sda: 250069680s 
Secotor size (logical/physical) 512 B/512 B
partician table: gtp

number      Starts.        End.           Size                File   System name flags
1.               2048.      250066944s.  250066944s.   Ext4

(my name)@(my name)-z87x-hd3:~$


also as for the backup I have a disk containing windows and had a app that backuped the first 60% of what I did on windows.

what should I do?

---

### Post by geckoboy3 on 2014-04-20
I have contacted the application that did the 60% backup and see why they will restore tomorrow when they are back online. Do you have any suggestions for what I should do in the meantime?

---

### Post by geckoboy3 on 2014-04-20
Gparted says that I have one partition, /dev/sda1 Which is 119.24 gib
Here is what it says:
Partition. File system Mount point. Size. Used. Unused. Flags
 /dev/sda1. Ext4. /. 119.24 GiB. 5.59 GiB. 113.64 GiB

---

### Post by oldfred on 2014-04-20
It sounds like you did a total erase of drive type install, not a manual choose one partition.
Do you only have one drive? sda? It shows only one partition.

For output from terminal just copy & paste from either your working install or the live installer which ever is working. If output is longer use Go Advanced reply and click on # to add code tags.

Like this:

```
fred@fred-Precise:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```

I do not understand a 60% backup? That would not be the full system that you could restore as that would have to be the entire NTFS partition. 
Do you have recovery set of DVD, or a full Windows install set of DVDs?
If purchased with Windows 8, they do not give you a restore set of DVDs but expect you to make your own as soon as you get system.
If you do not have a full system, you may be able to get a full restore for your system from the vendor for a nominal shipping charge. Some vendors do not offer that. 
One users went to retailer he bought system from and tech person had identical system on floor and made a restore set of DVDs. I thought that was good customer service.

---

### Post by geckoboy3 on 2014-04-20
I am doing something wrong with the coding... I don't know why. I used this same code about ahour ago briefly and it worked...
nico@nico-Z87X-HD3:~$ sudo parted /dev/unit s print
[sudo] password for nico: 
Error: Could not stat device /dev/unit - No such file or directory.       
Retry/Cancel?                                                             



Retry/Cancel? sudu /dev/sdd unit s print                                  
parted: invalid token: sudu
Retry/Cancel?   

Also, I have a disk containing windows 8.1 but need the key (I called microsoft).Even though it is a custom pc, I can easily get it tomorrow. However, before I do anything else, I need to know exactly what I should do to get space for windows on the hard drive without deleting Ubuntu.

As for the 60& backup, I downloaded a application which copied 60% of my data and that is currently online. The company name is MyPC Backup.

---

### Post by oldfred on 2014-04-20
You have to have a drive in the parted statement.
       sudo parted /dev/sda unit s print

If in terminal in your install, not live installer, you can just press up arrow until you get to the command your previously used. It saves 500 or 1000 commands and you can list all with one command - history.

If Windows was pre-installed the serial number is in UEFI.
      
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

You will probably have to delete Ubuntu to reinstall Windows. It requires a variety of partitions and some have to be in a particular order on drive.  And if you only have one partition, you must have converted from UEFI to BIOS, and that would change partitioning from gpt to MBR (msdos). Windows requires gpt partitioning to boot in UEFI mode.

      
 Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

     
     Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by geckoboy3 on 2014-04-21
Thank you so much! 
With your  help, I have been able to access the windows installer. However, I face another problem.

According to Microsoft support, if I create a new partition that is ntfs, I can download the windows. When I try to create a new partition, however, (change /dev/sda1) I get this error from Gparted:
The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually

When I try from the terminal. I get this error:
(name)(name)-Z87X-HD3:~$ umount /dev/sda1
umount: only root can unmount UUID=44399210-a8f8-44a5-898e-b48157825ffc from /

Help would be appreciated, as I am definately a noob when it comes to this stuff.

---

### Post by oldfred on 2014-04-21
You cannot edit mounted partitions.
Or if you see the little key symbol that is mounted. And you cannot unmount your working system.

So you have to use live installer system. And if you have swap it may mount that, but you can unmount it.

---

### Post by oldfred on 2014-04-21
I just am not sure how you recover Windows in this case. I have never heard of a 60% backup.

Best way to backup Windows before an install. And for whatever reason those who do a backup do not have issues, but the one's that skip the full backup invariably are the ones with major issues.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by geckoboy3 on 2014-04-22
I have solve this. Using my hard copy of windows 8.1, I deleted everything (EVERYTHING) and reinstalled windows and then ubuntu following exactly oldfred's suggestions..


thank you so much! You are honestly the most helpful person that I've encountered so far out of all the forums I've visited! Now I can have fun with my new Linux/windows desktop :).


thanks again! I truly appreciate your help.

---

### Post by oldfred on 2014-04-22
Glad you got it working, I was not sure there for a while. :)

---

### Post by squakie on 2014-04-22
> **geckoboy3 said:**
> ....you are honestly the most helpful person that i've encountered so far out of all the forums i've visited!....

a big +1!!

---

