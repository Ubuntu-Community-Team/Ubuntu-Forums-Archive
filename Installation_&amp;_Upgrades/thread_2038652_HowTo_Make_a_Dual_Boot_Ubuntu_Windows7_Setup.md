---
title: "HowTo Make a Dual Boot Ubuntu Windows7 Setup"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by pgmer6809 on 2012-08-07
**Windows7 and Ubuntu 12.04 Dual Boot How To.**

 **[FONT=Century Schoolbook L, serif]I Warning!![/FONT]**

 Installing Ubuntu alongside versions of Windows previous to Vista (Win XP etc.) was fairly straightforward. Simply insert the live CD and install; you could let Ubuntu choose how to install or you could shrink and create partitions yourself. You could install GRUB into the MBR and let GRUB manage the boot process on the final system.
 If you adopt the same approach to systems with Windows7 pre-installed you could wind up with a machine that is not bootable at all. I know, I've done it.
 

 Nevertheless if you follow the correct steps it is fairly straightforward to install  Ubuntu alongside a pre-existing Windows7 system.
 
 Why the difference? See here.
 
 [I]More info on how Windows boots, shows Vista but is the same for 7.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)[/I]
 

 The above explains some of the innards of the Vista/Windows7 boot process; but the short answer is that Windows7 checks the MBR for signature bytes when it boots, and it also uses a more complicated menu system – the simple c:\boot.ini  text file has been replaced by the BCD (Boot Configuration Data) 'hive'.  As  a result it is much safer to let Windows7 stay in control of the boot process, and add an Ubuntu entry to its menu.
 To do this you will need the tool EasyBCD which you can download from:
 [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)
 _This is a great little program._ **Do not even attempt to install Ubuntu alongside Windows7 without it.**  
 After you have completed the following, see if you do not think that it is worth it to send them a small donation. The time it will save and the peace of mind that it will give you is well worth a donation of $10.00-$25.00
So your very first step is to download EasyBCD and install it (under Windows).  Once you have done that carry on with the following.
 

 See this image:
 [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)
 

 [COLOR=#dc2300]***Notice: The following discussion assumes Windows7 preinstalled on a system with the traditional BIOS (not UEFI) and disks that use the DOS partition table (not GPT). Most of this may very well work on these soon to be standard configurations but I have not tested it.***[/COLOR]
 

 **II Backup**

 Because there are extra steps involved, and more chances of mistakes,  it is certainly  prudent to create backups of as many of the key components of your current system as you can.
 
[LIST]
[*]_First_ make yourself a set of Windows7 Recover DVD's.     It may take 4-5 DVD's for this set.
[*]_Second_ make a system repair disk. (One CD should be     enough, but you can use a DVD also).
[/LIST]
 Go into[COLOR=SeaGreen] Control Panel => System => backup Restore => Create System repair Disk  [/COLOR]
 and follow the prompts.
 This step also backs up your BCD, a key component of Windows7.  
 
 At this point you should insert a USB stick into your computer. You are going to want to backup your hard disk MBR to a different media – floppy or USB. Here we will assume USB. We can also use the USB stick to save other small files.
 
 Since the BCD is a key player in the Windows7 boot process, it is also instructive to compare what you have in the BCD hive before you start with what you end up with after you are finished. To do that you need to run the bcdEdit program, from the Windows command prompt.
 
 Click [COLOR=SeaGreen]START => ALL PROGRAMS=> Accessories[/COLOR]. _Right click on the “Command” menu item_.  and choose '_Run as Administrato_r”. 
  Once you have the 'dos prompt' open, type  
 
```
cd \C:
  bcdedit -v >bcd-orig.lst
 exit

``` This will give you a human readable file of the BCD entries you currently have.   
 You may as well  use Windows Explorer to copy that file(C:\bcd-orig.lst) to the USB stick.
 On most computers sold with Windows7 installed there are already 2 or 3 partitions on the hard drive. There is the 'System Info', the 'Windows Recovery' and of course the Windows7 C: drive which occupies a partition of its own. The existing BCD will reflect that.  
 
[LIST]
[*]_Third_ make yourself a 'System Restore Point'. This is     an easy way to undo certain kinds of changes to your windows system.
[/LIST]
 [COLOR=SeaGreen]START => Control Panel => All Items => System =>System Protection  [/COLOR]
  If you cant find it by clicking through menus open Control Panel, and type Restore in the search bar.
 
[LIST]
[*]_Fourth_ you want to backup your MBR (Master Boot  Record).
[/LIST]
 There are Windows utilities available for download  that will do this, (e.g. FIXMBR) but I just use the Linux **dd** command. We will need to boot from the Ubuntu LiveCD. To do that we need to ensure that the CD/DVD device boots before the hard drive. You can set this in the BIOS. Usually you must press a key such as DEL or F8 within 30 seconds of powering on the computer and before Windows starts. Then you will have to change the boot order so that the DVD drive comes before the hard drive. This is not hard to do and quite safe, but varies by machine. The explanations on how to do this are not part of this write up.
 After setting the priority of the DVD drive to come before the hard disk, insert your Ubuntu LiveCD and reboot into Ubuntu. [COLOR=#ff3333]**DONT DO THE INSTALL YET!!**[/COLOR]**.**
 Insert your USB stick into a USB slot. You now want to find out what is its device name.
 Open a terminal window and type at the command prompt:
 ```
cat /proc/partitions
```. You will see something like this:  
 

> major minor  #blocks  name     8        0  245117376     sda  
    8        1   49151071     sda1  
   11        0    1048575     sr0  
    8       16    7831552     sdg
    _8       17    7830428     sdg1 _
You should be able to tell fairly easily which is the USB stick. It will almost certainly have a device name higher than /dev/sda. On my system it is /dev/sdg, with the first and only partition being named /dev/sdg1.   In your terminal window type:


```
mkdir /tmp/usb
 mount -t vfat /dev/sdg1 /tmp/usb

``` To check that you have the correct USB stick etc you can do ```
ls /tmp/usb
```> and you should see the files you had put there under Windows show up. (bcd-orig.lst etc)
 Now comes a tricky part. If you don't do this right you could hose your hard drive.  
 [COLOR=#dc2300]_**TYPE THE FOLLOWING VERY VERY CAREFULLY!!  DO NOT HIT ENTER AFTER YOU TYPE. **_[/COLOR] 
 ```
dd if=/dev/sda ibs=512 count=1 of=/tmp/usb/Win7_MBR.bak obs=512
``` ReRead it carefully.  
 
[LIST]
[*]Are you sure  that the letters     before the /dev/sda say EYE-EFF (if=)?
[*]Are you sure that the letters     after OH-EFF (of=) say /tmp/usb/Win7_MBR.bak ?
[*]Did you remember to put the     <bold>**count=1**</bold>     parameter in?
[/LIST]
 OK. Now ReRead it a third time. Does it still look right?
 NOW you can hit ENTER This will copy the first 512 bytes of your primary hard drive to a file on your USB stick. The file is a binary one. If you must you can re-create the original MBR by booting a Rescue CD (Ubuntu Live CD or something else) and rewriting that .bak file to the hard drive.  
 Now we go back to windows. Shutdown Ubuntu, remove the DVD from the drive and reboot.
 
 **III Preparing Disk Space.**

 If Windows7 is pre installed on your system it has probably used the whole disk. As stated earlier there are probably  three partitions already configured. Two of them you do not want to touch. The third one you want to shrink in size to make room for the Ubuntu system you want to install.  
 Previously it was safe to do this using Linux tools, but with Windows7 it is safer to do as much partition management as possible under Windows7 itself. This is because Windows7 keeps track of the state of the disk drive more closely than XP did.
 On my system with a 1000GB (1,000,000MB) drive, I had a 14,000MB 'Recovery' partition, a 100MB system (bootable) partition, and a 985,000MB Windows7 partition (the _C:\_ drive) of which about 90,000MB were used.  
 I decided to shrink the C: drive to 180,000MB (180GB) and make a second windows partition of around 400,000MB(400GB), leaving approximately 405,000MB(405GB) for Ubuntu.
 Creating a 4th partition on my disk, using Windows accomplished two things:
 a)  I wanted a disk partition that was visible to both Windows7 and Ubuntu, but I did not want Ubuntu to be writing to the C: drive, just to be on the safe side.
 b) Since this was the fourth partition and the disk had space left over, Windows was smart enough to first create a logical partition, and put this fourth partition inside the logical partition. The free space left inside the logical partition can be safely used by Ubuntu without danger of clobbering any key pieces of disk data that Windows7 wants to see.
 So [COLOR=SeaGreen]START=>CONTROL PANEL => System and Security => Administrative Tools:[/COLOR] _Create and format Hard Disk Partitions. _ 
  Once you have the disk management open you will see something like what you see in Gparted, or Partition Magic, or the usual Ubuntu install. (Picture would go here if they would let me.)
  Click on the _C:\_ partition, then right click, and choose 'Shrink Volume'. Choose a size. Since my Windows7 system was already using 90GB, I decided to make the new C: drive twice that at 180GB.
  For the new size enter [COLOR=#ff3333]**180000 **[/COLOR](or whatever you choose). _Note that the sizes are given in MB_. If you enter 180 (thinking in terms of GB) instead[COLOR=Magenta] you could damage your system by trying to fit a 90,000 MB Windows7 system, into 180MB.  [/COLOR]
 Once that step completes you should see a bunch of free space at the end of the disk.  Select it and choose to create a new partition. Give it a type of NTFS and a drive letter (J: on my system).  Provided you leave around 20,000MB (20GB) to install Ubuntu in, you can make it any size you want. I chose to make it about half the size of the total free space. (400,000MB). Windows7 will automatically handle the creation of a logical partition to hold the new one for you if necessary.
 When that completes we have finished with Windows for the time being. Now it is time to install Ubuntu.

 **IV Ubuntu Install  **

 Shut down your computer, insert the Ubuntu LiveCD into the DVD drive and reboot.  
 Click on the 'Install' icon on the desktop.
 You will be asked for your language, choose one and click Continue.  
 You will be presented with a screen telling you of space requirements, and giving you the chance to install 3rd party software (I do) and whether to install updates at the same time (I don't).  Make your choices and click Continue.
 You will then be asked what kind of install you want,  
_**click on the button [COLOR=Red]Something Else[/COLOR]**_.   Then Continue. 
Next you will see a screen showing the disk partition layout at the top, and just below that an entry giving you the choice of where to install the Boot Loader.
 The first thing to do is to select the empty space on the disk drive in the top half of the screen.
 Now Create a new partition.  
 If you are experienced you can create separate / and /home and /boot partitions,  but this discussion keeps it simple by having all of Ubuntu on one partition. Make it an ext4 partition. Make the size such that you leave about 3,000MB(3GB) to 6,000MB(6GB) for the swap partition which you will create next. Tick the format box. Also choose  a mount point of / (slash). On my system I had about 405,0005MB of free space left, so I made an ext4 partition of 400,000MB(400GB) and a swap partition of 5,000MB(5GB). Finally click on the last bit of remaining free space and create a swap partition. The size will default to whatever is left. There may be a delay while the partitions are being formatted.

 *Aside: Guidelines say that swap should be about 2X your memory size, but frankly I have never seen my other Linux systems use even a little bit of swap. So long as you have free RAM available Linux is pretty smart about using RAM instead of swap. But I think you need swap for hibernate to work, so I always give it some.*

 Notice that in all of the above I have given the size in MB, rather than in GB. Again you don't want to enter 400 in a size box thinking you are creating a 400GB partition only to find that the size you specified was in MB.  
 Once the root (“/”) and swap partitions are created there is one more very important step.
 Make certain that you go to the _“Device for Boot Loader Installation”_ portion of the screen and choose the new root (“/”) ext4  partition you have just created. Note that this partition will have a name that ends in a number such as /dev/sda6.  
 [COLOR=#dc2300]**[COLOR=#000000]<Bold>[COLOR=Red]THIS IS VERY VERY IMPORTANT.[/COLOR] [/COLOR]**[COLOR=#000000]**</Bold>**[/COLOR][/COLOR]
 **[COLOR=Magenta]If you do not do this, then the install process will overwrite your MBR on the disk and you probably will not be able to boot Windows7 until you fix it.[/COLOR]**
 Double check this then click Install Now.  
 Follow the prompts about username, password, computer name etc..
 When the install process has finished, you need to reboot your machine. Remove the Ubuntu Live DVD from the drive and reboot. You will boot back into Windows7 from the hard drive. You cant boot Ubuntu yet. You still have to tell the Windows7 BootManager that there is a new OS on the hard drive.  
 Shut Down Ubuntu, remove the DVD from the drive, and reboot your computer. It should reboot into Windows7 normally. If it does this proves that you have not seriously damaged the MBR with your Ubuntu install.  

**V Creating Dual Boot Using EasyBCD.**

 Once you have rebooted into Windows7. Did you already install EasyBCD? If not go do it now. If it is installed, Go to  
 [COLOR=SeaGreen]START=> All Programs=>NeoSmart Technologies =>EasyBCD[/COLOR]
  Before you add a new entry you can have EasyBCD backup your current setup to a file on a USB or on the hard drive itself. Once you have done that,
 _Choose Edit Boot Menu_
  Now Choose _Add NewEntry_ Then _select the Linux/BSD tab._
 In the Linux tab choose Grub2 as the Type, and give it a name such as Ubuntu-12.04. This is what you will see when your computer powers on and gives you a choice of which item to boot.
 Once you click Perform Action you will have a dual boot computer!

 Use EasyBCD to create a backup of the new BCD settings, giving the backup a different name from the first one you did of course.
 Exit EasyBCD.

 Lets take a look at what the BCD hive contains after the EasyBCD mods. Start the command prompt in Administrator mode the same way you did earlier.
 Then type:
 ```
cd \C:
  bcdedit -v >bcd-postUbuntu.lst
 exit

``` This will create a file you can review later to see what changes were made.
 Shut Down Windows with the Restart Option.  
 When your computer restarts you should see a couple of options at the boot menu. The original Windows7 of course, perhaps a recovery option, and a new entry that says “Ubuntu-12.04”.
 Test these out by choosing each one in turn. (use the Up/Down arrows. The mouse is not usually functional at this point.)
 Congratulations you have succeeded!!

  **VI Post Installation Activities.**

 There is one very important thing you must do now before you forget. You have prevented GRUB from installing itself in the MBR during the install process, now you must make sure that it does not install itself in the MBR during some automatic upgrade or security patch. Grub consists of two parts: a very small (<512 bytes) part called the IPL that installs in the MBR or the PBR, and a larger part the BootManager part. EasyBCD installs its own version of  the BootManager part of Grub, and the small IPL part you don't want to be patching anyway, so there is no reason to have Ubuntu automatically update the Grub application.
Boot into ubuntu and start the Synaptics package manager, from one of the Ubuntu menus. If you do not know which use[COLOR=SeaGreen] Accessories=>Application Finder[/COLOR] to find it.
 Enter your password when prompted.
 Select “All” in the sections portion of the Synaptics window. Type GRUB in the search bar.
 You should see a bunch of lines all of which refer to GRUB, many with green boxes on the left. These indicate the packages that were installed on your system. Select each one in turn, Click “Package” on the menu bar, then choose 'Lock Version' from the drop down menu. The green box will now contain a lock, and the background for the package will turn a shade of red.

  When you have done that to all the Grub packages your system install is now complete.  
 Now think back to how easy it was to add an Ubuntu entry to the Windows7 boot menu. 4 clicks and you were done. If you had to do that with the bcdEdit program alone it would have taken you several days maybe even a week to read up on such items as GUID's, you would have had search to find how to install a non Microsoft OS (all the help assumes you are installing a second MS OS), you would have had to type carefully with no typos several lines of text to create one entry. Now isn't the ability to do it in 4 clicks worth a donation to NeoSmart? Go do it right now.  
 [http://neosmart.net/donations.php](http://neosmart.net/donations.php)
 Open your PayPal and send them something.
 

 Lets compare the two BCD configurations.
 Here is the Original Windows7 BCD
> [FONT=Courier New, monospace]Windows Boot Manager [/FONT] 
 [FONT=Courier New, monospace]-------------------- [/FONT] 
 [FONT=Courier New, monospace]identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795} [/FONT] 
 [FONT=Courier New, monospace]device                  partition=\Device\HarddiskVolume2 [/FONT] 
 [FONT=Courier New, monospace]description             Windows Boot Manager [/FONT] 
 [FONT=Courier New, monospace]locale                  en-US [/FONT] 
 [FONT=Courier New, monospace]inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e} [/FONT] 
 [FONT=Courier New, monospace]default                 {8675c3f4-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]resumeobject            {8675c3f3-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]displayorder            {8675c3f4-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d} [/FONT] 
 [FONT=Courier New, monospace]timeout                 30 [/FONT] 
 

 [FONT=Courier New, monospace]Windows Boot Loader [/FONT] 
 [FONT=Courier New, monospace]------------------- [/FONT] 
 [FONT=Courier New, monospace]identifier              {8675c3f4-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]device                  partition=C: [/FONT] 
 [FONT=Courier New, monospace]path                    \Windows\system32\winload.exe [/FONT] 
 [FONT=Courier New, monospace]description             Windows 7 [/FONT] 
 [FONT=Courier New, monospace]locale                  en-US [/FONT] 
 [FONT=Courier New, monospace]inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7} [/FONT] 
 [FONT=Courier New, monospace]recoverysequence        {8675c3f5-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]recoveryenabled         Yes [/FONT] 
 [FONT=Courier New, monospace]osdevice                partition=C: [/FONT] 
 [FONT=Courier New, monospace]systemroot              \Windows [/FONT] 
 [FONT=Courier New, monospace]resumeobject            {8675c3f3-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]nx                      OptIn[/FONT]
 [FONT=Courier New, monospace]And here is what it looks like after the Ubuntu Installation[/FONT]
 

> [FONT=Courier New, monospace]Windows Boot Manager [/FONT] 
 [FONT=Courier New, monospace]-------------------- [/FONT] 
 [FONT=Courier New, monospace]identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795} [/FONT] 
 [FONT=Courier New, monospace]device                  partition=\Device\HarddiskVolume2 [/FONT] 
 [FONT=Courier New, monospace]description             Windows Boot Manager [/FONT] 
 [FONT=Courier New, monospace]locale                  en-US [/FONT] 
 [FONT=Courier New, monospace]inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e} [/FONT] 
 [FONT=Courier New, monospace]default                 {8675c3f4-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]resumeobject            {8675c3f3-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]displayorder            {8675c3f4-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
                         [FONT=Courier New, monospace]{8675c3f7-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d} [/FONT] 
 [FONT=Courier New, monospace]timeout                 30 [/FONT] 
 

 [FONT=Courier New, monospace]Windows Boot Loader [/FONT] 
 [FONT=Courier New, monospace]------------------- [/FONT] 
 [FONT=Courier New, monospace]identifier              {8675c3f4-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]device                  partition=C: [/FONT] 
 [FONT=Courier New, monospace]path                    \Windows\system32\winload.exe [/FONT] 
 [FONT=Courier New, monospace]description             Windows 7 [/FONT] 
 [FONT=Courier New, monospace]locale                  en-US [/FONT] 
 [FONT=Courier New, monospace]inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7} [/FONT] 
 [FONT=Courier New, monospace]recoverysequence        {8675c3f5-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]recoveryenabled         Yes [/FONT] 
 [FONT=Courier New, monospace]osdevice                partition=C: [/FONT] 
 [FONT=Courier New, monospace]systemroot              \Windows [/FONT] 
 [FONT=Courier New, monospace]resumeobject            {8675c3f3-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]nx                      OptIn [/FONT] 
 

 [FONT=Courier New, monospace]Real-mode Boot Sector [/FONT] 
 [FONT=Courier New, monospace]--------------------- [/FONT] 
 [FONT=Courier New, monospace]identifier              {8675c3f7-d2bf-11e1-a7d5-fcfa9cce6506} [/FONT] 
 [FONT=Courier New, monospace]device                  partition=C: [/FONT] 
 **[COLOR=Red][FONT=Courier New, monospace]path                    \NST\AutoNeoGrub0.mbr [/FONT] [/COLOR]**
 [FONT=Courier New, monospace]description             Ubuntu-12.04[/FONT]
The program that is in red is a 9.2KB program. It  will not fit in anMBR, but it is the one that the Windows7 BootManager runs when you select the Ubuntu 12.04 entry. This program in turn causes the usual Grub menu to be displayed from which you can then boot the version of Ubuntu you want.
 

 I don't really mind two menus; and besides I don't re-boot that often. Usually I just suspend.
 If you don't want to see two menus, you can change the timeout in the Grub control file to Zero. This will mean that the default entry in the control file will boot with no delay and you will not  see the menu. I have not tested this but apparently what you do is:
 

 ```
sudo su
 cd /etc/default
 cp grub grub.bak
 vi grub

``` Now find the line that says:
 GRUB_TIMEOUT=10
 and change it to  
 GRUB_TIMEOUT=0
 Save and close your file.
 Now type: ```
update-grub
``` to generate the new file that grub will use during the boot process (/boot/grub/grub.cfg)
 To verify that your changes have taken place you can type the following (notice “timeout” is in lower case)
 ```
grep timeout /boot/grub/grub.cfg
``` This ends my write up on how to add Ubuntu to a Windows7 system and make it dual boot.
 

 Pgmer6809
 Copyright: Greg Morse August 2012.
 Permission granted to distribute under the GNU PUBLIC LICENSE GPL version 2.

---

### Post by pgmer6809 on 2012-08-15
There is one thing I have since discovered.

Some activities, such as creating a System Restore point, or installing a new driver, might put a file in the middle of the NTFS parition.
Example: Say your main partition is 400GB, say 90GB used,  and you want to give 200GB to your Linux install.
Start                   .......................100GB                      ....................200GB                       ....................300GB                                  ....................................400GB
Windows OS||    free>-------------------------------------------> Sys File|| free----------------->

You would like to shrink the partition down to 200GB. If Windows has installed an um-moveable file at the 300GB mark, Windows will refuse to shrink the partition past the 300GB mark. 
As a result you will only be able to create a 100GB partition, even though you have over 300GB free. 
So far as I know there is no way around this. 
Moral: Shrink your main Windows partition as soon as you have done the backup steps.
Don't install any new software on a Win7 machine until you have shrunk the main partition. 
pgmer6809

---

### Post by hank22077 on 2012-08-15
All I did was shrink the Windows7 partition, and leave it as free, unallocated space.
Then during 12.04 install chose that space under the  **'Something else'** option for my install.
So far, no problems...
Therefore, after reading this; should I be concerned at all?

---

