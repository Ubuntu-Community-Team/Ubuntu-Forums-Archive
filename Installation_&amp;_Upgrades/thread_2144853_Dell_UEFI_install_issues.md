---
title: "Dell UEFI install issues"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by divine shine on 2013-05-06
Hey, I'm having almost the same problem. I am able to boot into GRUB2 with my SecureBoot Disabled, but the screen blanks out after I choose any option in the GRUB2 bootloader. Nothing happens after that; the indicator on my pendrive also becomes steady. I tried leaving the system as is for as long as 7hrs (when I went off to sleep :D :P), but nothing happened. It was the same blank screen. :/ :( I want to install Ubuntu 13.04 Raring Ringtail alongside my pre-installed OEM Windows 8 in (U)EFI mode. I think Boot-Repair is supposed to fix problems after the install of the OS. Can it fix such errors as blank screens when booting from a LiveUSB?

Originally part of this thread. Just for reference, that thread was UEFI but Asus.
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)

---

### Post by oldfred on 2013-05-06
@devine shrine
See post #4, Boot-Repair is primarily to fix boot issues. But video issue is actually after you have booted with grub.
Often nomodeset is the fix, but sometimes other kernel boot parameters.

---

### Post by divine shine on 2013-05-07
> **oldfred said:**
> 
But video issue is actually after you have booted with grub.
Often nomodeset is the fix, but sometimes other kernel boot parameters.

I read about the nomodset option in the kernel setting. But inorder to change the nomodset setting, I need to boot into the kernel atleast. But that doesn't happen with me. I can't view even 1 screen after the GRUB2 bootloader. The screen goes blank after I choose any of the 4 options in the boot menu (i.e., Try Ubuntu without installing, Install Ubuntu, OEM install (for manufacturers), Check disk for errors), all options converge to giving me a blank screen and after a little activity, my USB's LED activity indicator becomes idle, which clearly indicates that the USB isn't working anymore. This screen stays as is for as long as 7hrs (I literally left my system as was for 7hrs when I went off to sleep during the night), but in vain. :(

---

### Post by oldfred on 2013-05-07
With UEFI you also boot with grub and press e on grub menu and scroll down to linux line & replace quiet splash with nomodeset. That is just like first boot after install procedure. If in BIOS mode you should get accessibility screen, press any key and use f6 to add nomodeset. If UEFI you do not want BIOS mode unless that is absolutely the only way you can install which is the case for a few systems. Many need secure boot off, but Ubuntu should boot with secure boot on.

I think the first part shows a BIOS boot screens, but further down shows the grub screens as on first boot after install (or now UEFI boot).
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by divine shine on 2013-05-12
Firstly, I do not use the ASUS K55N. I'm using Dell Inspiron 15z Ultrabook. It has a Intel HD 4000 alongside a NVidia GeForce GT 630M.
The problem is I cannot access the LiveSession from the LiveUSB PenDrive in the (U)EFI mode. That's where I get the blank screen hang.
If I was able to get into the LiveSession, then I'm hoping everything else would go smooth. Then only will the methods you suggested last work.
I tried booting using the Legacy(CSM) mode, the LiveSession booted correctly. But the session wouldn't recognize my gpt partitioned Interal HDD. So I couldn't install it in the Legacy Mode either.
Hope you have understood my problem now and will help me as soon as possible. :(

---

### Post by divine shine on 2013-05-12
Thanks for your help blind3d. But I don't use the above mentioned ASUS K55N laptop. I'm using a Dell Inspiron 15z Ultrabook. I started commenting on this thread only cuz my problem was related to the (U)EFI booting problem. So I don't think any of your steps are going to be of any help for me. But thanks anyways for trying. I really appreciate it. Thanks a lot.

---

### Post by oldfred on 2013-05-12
@ devine shine - Then you should have started your own thread.
I assumed you also had the Asus. There are a bunch of threads with different models of Dell's that all have worked. If anything the Dell systems seem to be the better ones with dual booting.
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by divine shine on 2013-05-13
I'm sorry oldfred, as I stated earlier, I continued with this post because I thought I had a similar problem. I went through all the links that you posted above, but none seem to be my problem. My problem is that I can't log into the LiveSession at all. My boot does not go beyond the GRUB2 Bootloader. All your links stated how to fix boot problems (using boot-repair) AFTER installing Ubuntu, but my progress hasn't got me that far! I'd start with my own thread from now on if you'd suggest. Awaiting your reply soon.

---

### Post by divine shine on 2013-05-13
ok oldfred, I finally managed to get into the Ubuntu Live Session by disabling the Integrated NIC technology from the Advanced System Settings tab. Well, now the problem seem to have changed. Ubuntu doesn't seem to recognize my internal hard-drive. It doesn't show any page (which is actually supposed to be there) saying that there is or there is no operating system. Instead the installer directly shows me the partitioning window but with a blank table, no partitions. What do I do now?

---

### Post by oldfred on 2013-05-13
If it is an UltraBook, you probably have Intel SRT which uses RAID. You have to turn off the Intel SRT, and remove RAID meta-data from drives. 
Some install Ubuntu to SSD, but those are primarily Ubuntu users. The Intel SRT caches Windows and makes it faster, so if primarily a Windows user you will probably want to reenable it after your Ubuntu install.

        HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
      
 Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

           
  
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

    

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by divine shine on 2013-05-13
ok, oldfred, I finally got into the Ubuntu Live Session by disabling the Integrated NIC. But now the problem seem to have changed. Now Ubuntu doesn't seem to recognize my internal harddrive. The installer just skips the page where it is supposed to show the type of install that I might want to perform (like Install Ubuntu alongside Windows, Erase Windows and Install Ubuntu, etc), it doesn't even show whether I have another OS or not. It doesn't even tell me that I do not have another OS. Instead it directly takes me to the partitioning window where there is a table that is blank. There are no partitions to install Ubuntu on. Earlier when I logged into Ubuntu using the Legacy (CSM) mode, the installer atleast did show the partition of my PenDrive that I was using to boot into Ubuntu though it didn't seem to recognize my internal hard-drive. But this is like blank. Totally blank table. What do I do now?

---

### Post by oldfred on 2013-05-13
You now have your own thread.

Posted just before you did above.

---

### Post by divine shine on 2013-05-13
Well, that seem to be my problem exactly. But my doubt is, will the missing RAID meta-data affect the drives' performance in Windows after I re-enable Intel SRT after the Ubuntu installation? Is the change permanent? Or will I be able to restore the RADI meta-data after the Ubuntu installation?

---

### Post by oldfred on 2013-05-13
I have not done it. Several of the threads mention they just turned it back on and it worked.
See the threads I posted above.

---

### Post by divine shine on 2013-05-13
[SIZE=5][U][B]Here's a Step By Step Procedure of Dual-booting Ubuntu with pre-installed OEM Windows on a (U)EFI system with more than one HDDs
[/B][/U][/SIZE]
[SIZE=3][U][I]

Preparation[/I][/U][/SIZE]

1. Download Ubuntu from [here]("http://ubuntu.com/download/") and burn the image file onto a CD or make a bootable LiveUSB Pendrive using [LinuxLive USB Creator]("http://linuxliveusb.com/en/download").

2. Allocate sufficient amount of memory for the Linux partitions,
a. Open the Run dialog by pressing the Window+R key combination.
    b. type 'diskmgmt.msc' and press 'Enter'.
    c. Select your hard drive in which you wish to install Ubuntu and chooose a partition that has sufficient space for the installation.
    d. Now, right click the partition and choose the 'Shrink Volume' option.
    e. Recommended space to be allocated for Ubuntu would be >30GB. Do not format the partition now as Windows formats the partitions in NTFS mode which cannot be read by Linux. Linux partitions are ext4, ext3, ext2, etc. Just leave the newly shrunk space 'Unallocated'.

3. Restart the system several times so that the system can run a Disk Check-up (chdisk) and get accustomed to the new capacity setting change.

4. After this process, Enter the System Setup and disable the Intel's Rapid Start Technology from the Advanced tab in the System Setup menu. Also disable the Integrated NIC option in the Advanced tab to avoid further display hangs.


[U][I][SIZE=3]
Installation[/SIZE][/I][/U]

5. Restart the system and hold the F12 key to get the boot menu. Choose your LiveUSB PenDrive. This takes you to the GRUB2 bootloader.

6. Choose the 'Try Ubuntu without Installing' option. This takes your right to the Ubuntu Live session.

7. Press the Ctrl+Alt+T key combinations to open a Terminal window in Linux and type in the following code:
```
 sudo dmraid -E -r /dev/sda 
``` and press 'Enter'. This code is to remove the RAID meta-data from the hard-drive.
You could either remove the RAID meta-data from both the drives (for this you'd have to change the drive name from sda to sdb for the second drive in the above code) or else leave the second unused drive as is. Just remove the RAID meta-data from the drive that we are going to install Ubuntu on.

8. Now start the installation by clicking on the Install Ubuntu icon on the desktop. This should start the installer and the first few steps are pretty much just read-and-follow steps.

9. The twist happens when the installer asks for the type of install we want to perform. The installer might indicate that the system doesn't have any operating systems that it has detected. Don't worry, that doesn't matter. Just choose the 'Something Else' option and click 'Continue'.

10. This takes you to the partitioning tool that helps you partition the drive and choose where to install your Linux Distro (Ubuntu).

11. The partition table shows all your partitions numbered along with the drive name (e.g., sda1, sda2, etc.)

12. Look for some 'free space' in the partition table. (Hint: the free space won't have a numbered label to it).

13. Double click the free space and then comes a dialog box asking how to use the free space.

14. Recommended installation guidelines are to specify separate partitions for the /, /boot, /home and swap. So divide this free space accordingly.
a. the / (root) partition holds all the system files, 10-15GB must be sufficient enough for that.
     b. the /boot partition is where the bootloader and boot information are stored. 250MB should be enough for the boot partitions.
(U)EFI is a technology that supports multiple bootloaders. So you could exclude the /boot partition and assign the installer to store the bootloader in the EFI partition of the system (described below).
     c. the /home partition is like the 'My Documents' folder in Windows. It stores all your data. The remaining amount of memory capacity can be used to mount the home folder.
PS : It is always best to have a shared NTFS partition to share files and folders between OSes (i.e., Linux and Windows).
     d. PS : the / and /home partitions must be in ext4 format so as to make it recognizable for Linux. The /boot partition is described later.
     e. the swap area is like the page file in Windows. It is like a virtual cache memory that resides in the memory for fast access of data. With modern systems, the use of a swap partition is redundant as RAM themselves come in more than 4GB. Unless you're gonna use the system for heavy video editing and processing or applications that are memory-extensive, the only use of the swap area would be when you 'Suspend' your system. And if you have an 8GB RAM. The use of a swap partition would be simply unnecessary.

15. After the partitions are allocated from the free space, the next step is to specify where the bootloader is to be stored.
As stated earlier, EFI systems are capable of handling multiple bootloaders. It's like MBR that can support multiple bootloaders. So mounting the /boot onto the EFI partition wouldn't harm the Windows Boot Manager. The EFI partition can be identified by the EFI label next to its numbered drive label (usually, sda1 is the EFI partition). I had no problems after I allocated the bootloader to the EFI partition.

16. The remaining steps are simply piece of cake like setting up your time-zone, user, etc that even a 6-year old kid can do.

17. After completing the installation, go ahead and restart your system.

18. Press the F2 key again to enter the System Setup. Navigate to the Boot tab and if you've installed the bootloader into the EFI partition, you'll be able to see the ubuntu bootloader along with the Windows Boot Manager. Make sure that Ubuntu is set to the first priority. Save the changes and exit to restart the system with the applied changes.

19. Check whether you are able to boot in Ubuntu with the changes made. If not, and you have the SecureBoot feature turned ON in the (U)EFI menu in the System Setup menu, you should try with the SecureBoot OFF. That should pretty much fix the boot.

20. When you have to use Windows, you can simply press the F12 key to get into the boot menu to choose the Windows Boot Manager and boot into Windows.

21. Check whether the Windows installation is working properly before settling down with Ubuntu.

[SIZE=3][U][I]

Restoring Intel Rapid Start Technology[/I][/U][/SIZE]

Follow the steps in post #5 in the following thread to restore your Intel RST.
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)


_[SIZE=3]*Disabling nVIDIA discrete graphics to save battery power*[/SIZE]_

If you've got a nVIDIA graphic card, it's most likely that the proprietary driver may cause Ubuntu to crash since nVIDIA and Linux were never at good terms. ;) Also the card remains powered on even if it's not in use eating up a lot of your battery power. You wouldn't require the graphics card since you're not going to play any hard-core games (which you practically can't) on Ubuntu. So, you might want to disable your nVIDIA graphics. Head over to the following link to learn how to disable your graphics card and save a lot of battery power.
[http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work)

Enjoy Ubuntu - Free and Open Source.
Why mess with licenses when you have free software? :D ;) :)

---

### Post by divine shine on 2013-05-13
Finally, I've got it all right... I've got Ubuntu 13.04 Raring Ringtail up and running smoothly in (U)EFI mode just as I wanted it. Thanks to oldfred who pointed me in the right directions. Thanks a lot oldfred.

The Whole Story... Everything I went through...

Well, in summary, I wanted Ubuntu 13.04 dual-booted with my pre-installed OEM Windows 8 which I didn't wanna let go cuz it was OEM.

I've installed various distros of Linux in the past for my friends and I've tried various distros myself using Virtual Machines. But all that was in the BIOS mode and not (U)EFI. Since (U)EFI is latest technology and comes with advantages, I decided to keep it. I seldom use Windows. Only when I'm in a hurry to perform certain tasks and don't know how to get about them in Linux. I'd rather prefer Windows 7 for such unimportant yet urgent tasks. But I didn't want to let go of my OEM Windows 8. Since I knew how to install Linux in the BIOS mode, I could've installed it in the Legacy (CSM) mode. But it was really painstaking to switch from (U)EFI to Legacy (CSM) everytime I wanted to switch between OSes and it was a waste of time. Initially I tried booting into the Legacy mode, but the installer showed me only the partitions of the PenDrive I was using as LiveUSB to install. This was unacceptable. The installer wasn't recognizing my internal HDD which was a 500GB HDD coupled with a 32GB SSD for fast caching in Windows in which 22GB was used up by the Intel RST for fast caching Windows. (I hadn't known that Linux was incapable of using RAID-enabled drives then).

Then I tried booting the LiveUSB PenDrive in (U)EFI mode in the beginning, but in vain. It simply wouldn't boot into the Ubuntu Live Session.  The screen would go blank after I chose any of the options from the GRUB2 Bootloader. I tested the same LiveUSB on another laptop with an ATI Radeon Graphics card and it worked smoothy even with the SecureBoot option of the (U)EFI technology was turned ON. So after much reading I concluded that it was the conflict of my graphics card (nVIDIA) which was coupled along with integrated Intel HD 4000 Graphics which was causing a conflict of drivers that led to the hang of the screen. I tried using all kinds of commands that tried to disable the graphics drivers such as nomodeset, i915.i915_enable_rc6=1, etc. But none seemed to work.

Actually none of that was the problem at all. The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working. I read somewhere to disable all the Intel's technology from the Advanced tab in the System Settings menu. At first, I disabled everything and checked to see if anything happened and to my surprise, something did happen. Then I tried to locate the exact problem and then found out it was the integrated NIC that was causing the problem. I disabled the NIC alone and went on ahead with my installation.

Here came my next problem. The installer was still not recognizing my internal HDD. Then again, my savior oldfred, pointed me in the direction of RAID and Intel's RS technology. Reading about all that enlightened me about how Linux was exempted from the RAID drivers and Intel's RST and caching mechanisms were hindering Linux from recognizing the partitions on the Hard-drive though it was aware they were there and they were RAID-enabled. The installer could detect RAID-enabled hard-disks but couldn't access them. In the end, after some reading again, I got the following code:  to figure that problem out. This would remove the RAID meta-data from the drive and separate the 2 drives. This ade the Linux installer to recognize the hard-drive and it's partitions. Then it was as simple as child's play with the installation.

In the end, after the installation, when I restarted my system, the Bootmanager booted directly into Windows even though I had installed the Ubuntu BootLoader (GRUB) in the EFI partition system. I checked with the boot order in the EFI menu and it was Ubuntu that was supposed to boot first. But it was always Windows. Then it struck me that in the beginning, I had read that some users would need to turn their SecureBoot (U)EFI feature OFF inorder to correctly boot into Linux. So I decided to test that and bingo, I was booting into Ubuntu. Now, whenever I want to go to Windows, all I need to do is press the F12 key to open the boot menu and choose the Windows Boot Manager option.

Thanks again to oldfred who helped me and directed me in the right directions to achieve this successful installation. Thanks a lot oldfred. :)

---

### Post by oldfred on 2013-05-13
You are welcome. Glad you got it working. :)

And thanks for the updates and install procedures. I will add it to my links of successful installs.

---

### Post by divine shine on 2013-05-13
Thank you oldfred. Appreciate that gesture. Thanks again. :)

---

