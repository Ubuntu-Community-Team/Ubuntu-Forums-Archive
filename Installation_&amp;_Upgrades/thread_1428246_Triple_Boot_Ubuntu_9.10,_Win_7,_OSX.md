---
title: "Triple Boot: Ubuntu 9.10, Win 7, OSX"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by cfhowlett on 2010-03-12
Greetings All:

3 months ago, I purchased a Dell Inspiron 1545 laptop with dual core 4300 processors and the Intel GMA4500 chipset.  This is the low-end 1545, not the upgrade which was offered later.  I installed Ubuntu under wubi which turned out badly.  The Grub 2.0 upgrade trashed the wubi configuration.  While researching solutions to that problem, I first saw mention of a &#8220;hackintosh&#8221;.  Over the next few weeks, I learned OSX86 options.  I learned of the the SL132boot.iso and I was intrigued enough by OSX reviews to take a trip to my local Apple store.  I purchased the $29 OSX &#8220;upgrade&#8221; DVD on 01/0610.

According to the OSX86 Hardware Compatibility List, my Dell wasn't OSX compatible.  Imagine my shock at seeing the Apple icon appear.  

My laptop came with Windows 7 pre-installed and triple booting was my ultimate goal at the outset of the project.  As of 03/01/10, I have established a stable, minimally hacked  configuration of Windows 7, Ubuntu Studio 9.10 and OSX.

I won't bore you with the details of repeated OS installations only to see /boot failures and scrambled MBR errors.  My sincere thanks to all those who answered my noobish questions and posted solutions online.  There are other ways to pull this off, but this is what worked for me.

I partitioned my HDD before installing any software.  I booted the SL132boot.iso CD, and started OSX.  I ERASED THE ENTIRE DISK with Utilities > Disk Utilities.  Otherwise, the partitioning menu was not offered.  I then created 3 equally sized primary partitions:

Partition 1, formatted as Mac OSX Extended, named Cider, reserved for OSX.
Partition 2, formated as FAT, named Redmond, reserved for Windows.
Partition 3, formatted as FAT, named Tux, reserved for Ubuntu.
Under partition options, I verified that the partition scheme was GUID.

I continued the OSX installation.  I selected Cider as my installation location and customized the installation by selecting only the minimal required system components.  After I got the triple boot established, I came back and installed the remaining components.

After OSX installed, I rebooted with the SL132boot.iso CD and verified that the chameleon menu offered OSX on the HDD.  Then I installed chameleon to the HDD.  I suggest you use the most recent chameleon customization from Deviato because he's done an excellent job of customizing chameleon to Dell 1545 requirements.  I removed the SL132boot.iso CD and rebooted to confirm that chameleon was properly installed and booting OSX.  (I suppose I should mention that everything seemed to work except DVD player, ichat and qe/ci.  Kext's may fix this.)

Next I installed Windows 7.  I booted from the Win 7 DVD and chose &#8220;Custom&#8221; so I could select the install location from my partition list.  I saw that OSX had installed a 200 mb EFI partition.  I selected the Redmond partition, formatted it as NTFS and installed Windows 7.  Upon rebooting, Windows started normally.  The chameleon menu did not appear.

Then I installed Ubuntu.  I booted the Ubuntu Live CD.  I selected &#8220;TRY UBUNTU WITHOUT MAKING ANY CHANGES TO YOUR DISK&#8221;.  After the Live CD demo started, I selected &#8220;Install Ubuntu&#8221;.   This method ensured that Ubuntu would offer me a choice of boot-loader location.  I selected manual partition option and chose the &#8220;Tux&#8221; partition.  I add a 60 gigabyte primary mount &#8220;/&#8221;, a 6 gigabyte /swap and a 100 gigabyte /home. 

I verified the primary ubuntu mount point &#8220;/&#8221; with System > Administration > Disk Utilities.  I selected advanced options and chose the primary ubuntu partition &#8220;/&#8221;, i.e. /dev/sda4 as the boot-loader location.  I then completed the Ubuntu installation.  I rebooted and &#8211; got the Black Screen of Death.  

I inserted the SL132boot.iso CD and rebooted.  The chameleon menu displayed all 3 OS's.  I had previously downloaded the &#8220;gptsync&#8221; package from the ubuntu packages repository and saved it to USB.  I started Ubuntu and installed the gptsync .deb package.  I verified my HDD device address as &#8220;dev/sda&#8221; with System > Administration > Disk Utility.  Then I created a  hybrid gpt/mbr partition table scheme with gptsync.  (If you want details on why this actually worked, I suggest you Google "rEFIt".)

&#8220;sudo gptsync /dev/sda&#8221;
I got a message stating that gptsync would re-write the mbr.

I rebooted the Win 7 DVD  to fix the Windows boot.  I started the command line by starting Windows &#8220;repair&#8221;.  The command line can also be invoked with Shift-Fn-F10.

&#8220;Diskpart.exe&#8221;
&#8220;select disk 0&#8221;, i.e. the HDD.
&#8220;Select partition 3&#8221;, i.e. the &#8220;Redmond&#8221; partition set aside for Windows 7.
&#8220;active&#8221;
&#8220;quit&#8221;

I closed the command line window and continued &#8220;Repair&#8221; the Windows installation.  I rebooted and Windows started normally. 

I rebooted the Win 7 DVD media again to fix the chameleon boot.  I invoked the command line by starting Windows &#8220;Repair&#8221;.  The command line can also be started with Shift-Fn-F10.  

&#8220;Diskpart.exe&#8221;
&#8220;select disk 0&#8221;, i.e. the HDD.
&#8220;select partition 2&#8221;, i.e. the &#8220;Cider&#8221; partition set aside for OSX.
&#8220;active&#8221;
&#8220;quit&#8221;

I removed the Win 7 DVD and rebooted.  The chameleon menu re-appeared and offered Windows 7, Ubuntu and OSX.  I verified that each OS booted normally from chameleon.  Booting Ubuntu started Grub.  Grub also offered all 3 OS's, but Windows and OSX both failed to boot from this menu.  At some point, I'll figure out how to comment out everything except the Linux options on the Grub menu.

END OF REPORT.

---

### Post by Trilby on 2010-03-21
Wow [=D>],

I'd love to do that but it all sounds way out of my league. Considering that Snow Leoprad only costs just over £20, I would  definately do this if I though I could.

(Currently dual booting Win 7 and Ubuntu 9.10)

---

