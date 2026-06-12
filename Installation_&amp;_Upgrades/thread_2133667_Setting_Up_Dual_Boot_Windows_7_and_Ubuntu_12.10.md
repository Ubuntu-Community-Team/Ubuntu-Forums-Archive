---
title: "Setting Up Dual Boot Windows 7 and Ubuntu 12.10"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by dylan1020 on 2013-04-08
Hello all, I have decided to Dual Boot Ubuntu 12.10 and Windows 7 on my main laptop. I have used Ubuntu before on my secondary machine but I did a clean install. I have already shrunk my Windows Partition down. I have about 300 GB for free space left for the remaining partitions. I just need help making the partitions in gparted. I need one for the Ubuntu installation, I have read that I need a swap partition (need help with that), and a partition for shared files between the two OS's. I have read multiple guides but they are outdated and I would rather have the most up to date information. If you could point me to a guide that's up to date, thank you. If you just tell me here, thanks twice as much lol. 
Thanks in advance

---

### Post by dylan1020 on 2013-04-08
update, I have found a nice guide [http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/)
The only problem is that it does not tell me how to do the shared files thing in both OS's. If anybody could clear that up it would be greatly appreciated.

---

### Post by Bucky Ball on 2013-04-08
Create an NTFS partition for shared files. You may already have one you can use. Ubuntu can see, read and write to NTFS partitions no problems (including the one where Win is installed) but Windows has no idea about Linux EXT* partitions. Hope that helps.

PS: You don't need to set up the partitions for Ubuntu in Gparted prior to installing Ubuntu. That can all be done when you get to the partitioning sections of the install. Choose something else. Mount points like /, /home and /swap are selectable there as defaults, but you can call mount points whatever you like also. A standard plan might be something like:

/ = where the OS goes, 20Gb is plenty (I never use more than 15Gb but have a separate /home);
/home = large as you like, your data like Documents, Videos, Music, etc.;
/swap = 2Gb fine unless you hibernate a lot; then as large as the amount of RAM you have is advised.

Good luck with it.

---

### Post by dylan1020 on 2013-04-08
> **Bucky Ball said:**
> Create an NTFS partition for shared files. You may already have one you can use. Ubuntu can see, read and write to NTFS partitions no problems (including the one where Win is installed) but Windows has no idea about Linux EXT* partitions. Hope that helps.

PS: You don't need to set up the partitions for Ubuntu in Gparted prior to installing Ubuntu. That can all be done when you get to the partitioning sections of the install. Choose something else. Mount points like /, /home and /swap are selectable there as defaults, but you can call mount points whatever you like also. A standard plan might be something like:

/ = where the OS goes, 20Gb is plenty (I never use more than 15Gb but have a separate /home);
/home = large as you like, your data like Documents, Videos, Music, etc.;
/swap = 2Gb fine unless you hibernate a lot; then as large as the amount of RAM you have is advised.

Good luck with it.
Thank you very much, and I knew that I could use Gparted within the live CD session. Would I be able to link to "My Music" and things like that in Ubuntu for the existing Windows Installation? There's really no point in making an extra partition for it if that's the case...

---

### Post by Bucky Ball on 2013-04-08
> **dylan1020 said:**
> Thank you very much, and I knew that I could use Gparted within the live CD session.

It is also what is used when you get to the partitioning section of the install.

> **dylan1020 said:**
>  Would I be able to link to "My Music" and things like that in Ubuntu for the existing Windows Installation?

Yes. You can have them mount like any other partition (they may be discovered and mounted 'automagically' without you having to manually do anything after install and on first boot).

Leave the 300Gb as free space so it is clearly visible during the partitioning section of the install. Just avoid doing anything to the NTFS partitions and make sure they are not ticked for formatting (they shouldn't be unless you manually do that anyway).

---

### Post by dylan1020 on 2013-04-08
> **Bucky Ball said:**
> 
Yes. You can have them mount like any other partition (they may be discovered and mounted 'automagically' without you having to manually do anything after install and on first boot).
Ok thank you. Not going to bother making a separate partition for it then. On to installing Ubuntu! I'll probably be back asking how to make the shortcuts to the Windows partition but I like to try to find things out myself. Thank you for everything.

---

### Post by dylan1020 on 2013-04-08
ok I am having a embarassing issue... The Ubuntu Live CD will not boot completely. I select to boot from a cd in the BIOS and it goes through and then I get like a splash screen for Ubuntu and then it goes black and it has a blinking cursor at the top and it hangs there. Any advice?

---

### Post by oldfred on 2013-04-09
Often Video. What video card do you have? I have nVidia and have to add nomodeset on live install boot and first boot after install until I get nVidia driver installed.
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I highly recommend the shared read/write NTFS data partition and set the Windows system partition as read only. Windows can be particular about too much activity from outside Windows. Also the Linux NTFS driver shows all the hidden files & folders that Windows normally hides, so accidents are too easy. Even when I only used Windows I would turn on show all files and accidentally click and drag too quick and move a system folder under another and totally corrupt system.

---

### Post by dylan1020 on 2013-04-09
> **oldfred said:**
> Often Video. What video card do you have? I have nVidia and have to add nomodeset on live install boot and first boot after install until I get nVidia driver installed.
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I highly recommend the shared read/write NTFS data partition and set the Windows system partition as read only. Windows can be particular about too much activity from outside Windows. Also the Linux NTFS driver shows all the hidden files & folders that Windows normally hides, so accidents are too easy. Even when I only used Windows I would turn on show all files and accidentally click and drag too quick and move a system folder under another and totally corrupt system.

I have Intel Integrated Graphics. I tried the nomodeset and I get the same thing. A blank screen with a blinking cursor at the top.

---

### Post by oldfred on 2013-04-09
Intel is just supposed to work. There is only the one open source driver fully supported & regularly updated by Intel.

Some have needed some settings intead of nomodeset:
        Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1

Others have posted to use the monitor settings, but use your monitor size and hz, not the example 1280x1024x60:

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60


 For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by dylan1020 on 2013-04-09
Update, I have made a live USB to see if it was something with the CD. I can get past the "Try Ubuntu without installing screen", and I got further than with the CD but it hangs after the scrolling text on line "[0.1953841] Booting Node 0, Processors #1".
Do I just completely fail at this?

Edit: a few lines up it says "CPUID marked event: 'bus cycles' unavailable". Could this be the problem?

---

### Post by oldfred on 2013-04-09
Is BIOS up to date? And do you have AHCI on in BIOS?

And it may still need other boot parameters.

 [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by dylan1020 on 2013-04-09
I got the live USB to work. I had to do nolapic. I am to the partition step and the free space I have is listed as unusable... Any ideas on how to fix this?

EDIT: i guess you can only have 4 primary partitions... Am I SOL now?

---

### Post by Bucky Ball on 2013-04-09
Correct. Four primaries only. BUT: If you can delete one of the existing four and replace with an extended partition then you can have as many logical drives, effectively partitions, inside the extended as your hardware can handle. You can create the extended partition in the partitioning section of the install also.

Good news you got the USB to work, though. Getting there ...

---

### Post by dylan1020 on 2013-04-09
> **Bucky Ball said:**
> Correct. Four primaries only. BUT: If you can delete one of the existing four and replace with an extended partition then you can have as many logical drives, effectively partitions, inside the extended as your hardware can handle. You can create the extended partition in the partitioning section of the install also.

Good news you got the USB to work, though. Getting there ...

I'm guessing you have no experience with Windows laptops... Apparently HP laptops ship with 4 primary partitions. I'm gonna do some research and see if the HP_Tools partition does anything special. Thank you guys for all your help.

---

### Post by oldfred on 2013-04-09
HP tools is small, easily copied into Windows partition or backed up, and some have said that is also available for download from HP. Some have also created a small logical partition and restore the files and said it still works.

 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

      
 Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Bucky Ball on 2013-04-10
> **dylan1020 said:**
> I'm guessing you have no experience with Windows laptops... 

Plenty. How do you think I got here? ;)

I also owned a HP until it died and am running Win7 on this machine, a Toshiba Satellite. 

With the HP, I used the option to burn backup/restore disks of the system then got rid of a couple of partitions. I could always get the machine back to the factory default if required using the disks I'd burnt.

---

