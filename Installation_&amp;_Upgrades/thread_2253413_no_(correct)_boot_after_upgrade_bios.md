---
title: "no (correct) boot after upgrade bios"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by bulevardi on 2014-11-19
Hi, I need help dealing with upgrading a CPU, and after BIOS upgrade, pc doesn't boot anymore how it should.


PC is 7 years old now, with the following specs:
Current OS: Linux Ubuntu Studio
Motherboard: MSI Neo P35 F
Old still working CPU: Intel Core 2 duo 2.13 Ghz, E6420 
New CPU I wanted to install: Intel Quad Core Q9650

The PC didn't boot anymore after installing the new CPU, with the old one, it did again. 
I read about upgrading the BIOS, so the new CPU would get recognized.

Yesterdaynight, I flashed the bios. (I put FreeDOS on a USB stick, and the Flash Utilities from the Mobo Manufacturer).
Got this picture after flashing:
[[img]https://farm6.staticflickr.com/5612/15823581711_4aa62ba3ab_o.jpg[/img]](https://flic.kr/p/q7gZyk)[BIOS Flash](https://flic.kr/p/q7gZyk) by [Dirk Desmet](https://www.flickr.com/people/55756714@N04/), on Flickr 

Seems like it worked out great... 

**But **after rebooting, went into BIOS, set Optimized Defaults, then the system rebooted automatically...
And then... the screen stayed black, no beep, no cursor, no keyboard numlock light. Couldn't get into BIOS anymore,... Tried different reboots.

This morning pulled out the CR 2032 battery out of the Mobo for a while. 
At some point, Ubuntu started... could get acces to my hard drive files, ... but when rebooting the pc, the problem continued;  

I now can get into BIOS again, or I get a menu screen titled "GRUB Version 2...." with a possibility to select: 
- Ubuntu (low latency)
- Ubuntu
- Memory test...
- Other Memory test
- ...
Each option I select: the screen just goes black with a flickering cursor.
Can't go further than that.

Anyone an idea what I should do now? Change some settings in BIOS? How to avoid GRUB pops up instead of booting ubuntu right away?
Reïnstall Ubuntu via a Live CD I have? 
When I ever get Ubuntu started again, should I set some settings right somewhere?

Thanks in advance!
bulevardi

---

### Post by bulevardi on 2014-11-19
Maybe I should set SATA mode of bios to AHCI/IDE or switch something?

---

### Post by oldfred on 2014-11-19
You usually want AHCI. And maybe some other settings. Resetting BIOS changes everything back to defaults.
Did you change other settings before.
I had to take photos of my settings as after first BIOS update I lost a lot of settings and had to slowly work thru issues and then remembering it was something I had changed before.

What video card. You may need nomodeset?

---

### Post by bulevardi on 2014-11-20
He mostly won't boot anymore after changing stuff in the BIOS setup, like the boot sequence,...  then I put the battery in/out again to make it work again.

Today I could get further and got Linux started somehow. 
Read about GRUB Customizer, and try to fix it with this program. Didn't work.
 Now pc boots with specific screen with texts like:
 "gave up waiting boot device", "missing modules", "ALERT", "dropping to a shell".
 "BusyBox v1.21.1" and then a commandline kind of program kicks off with <initramfs>.
 
Now I read somewhere I could fix this by "chrooting from a live cd", like this:
 [http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html](http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html)
 
Or here, this "bug" is mentioned too, but not with lots of unclear solutions for it:
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)
 
Don't know yet what I'm going to try first.
 Does not matter for me if I have to reïnstall Ubuntu again and copy my harddrive files back from my backup harddrive.

---

### Post by oldfred on 2014-11-20
What changes did you make with grub customizer? It installs its own scripts to implement some of the functions. 

Post a link to the summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I just built new system, but was going to do it a couple of years ago. My core duo system was from 2006. But it had 4GB of RAM and a decent updates 4 years ago video card. So I added an SSD 64GB and system became so much better that I waited till now to build new system. 
Not sure a new processor in an older system will give you good bang for the buck or good value?

---

### Post by bulevardi on 2014-11-20
I did the boot-repair without any problems.

But the computer still does not boot. I can't even see the first "press dell to enter bios" screen. 
I can only boot after removing/replacing the battery each time, not quite handy.

The link:
[http://paste.ubuntu.com/9131927/](http://paste.ubuntu.com/9131927/)

He mentions on the end aswel: "De opstartbestanden van [Het nu gebruikte besturingssysteem - Ubuntu 14.04.1 LTS] liggen ver verwijderd van het begin van de schijf. Mogelijk kan de BIOS ze niet vinden. U kunt het opnieuw proberen nadat u een /boot-partitie heeft aangemaakt (EXT4, >200MB, begin van de schijf). Dit kan uitgevoerd worden via hulpmiddelen zoals gParted. Selecteer daarna deze partitie via de optie [Aparte /boot-partitie:]  van [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)" 
[B]Translated as: the startupfiles for the OS are too far away from the beginning of the hard drive. Perhaps the bios cannot find them. You can try after a /boot-partition like with Gparted,...
[/B]

---

### Post by oldfred on 2014-11-20
Generally with newer systems, the far from start of drive does not apply. It is for old BIOS and perhaps some USB hard drives. If you have IDE on, not AHCI you may be emulating that old mode?
The solution is either a /boot or have a smaller / (root) of 25GB fully inside the first 100GB of drive and use rest of drive as /home or data partition(s).

You only have one install, so grub menu will not normally show. And you have nVidia which in most cases needs you to add nomodeset at grub menu or install nVidia proprietary driver.

If you hold shift key from BIOS, do you get grub menu? If so add nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bulevardi on 2014-11-20
Hmm, no couldn't get into grub via the shift key.

Was able to start up again after removing battery., changed the nomodeset via the terminal using these steps:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) Changed the grub configuration file and updated in terminal.
[B]Rebooted, nothing happenend.
[/B]
Sometimes after reboot: screen:
"ALERT  /dev/disk/by-uuid/.... does not exist"
with Initramfs stuff again.

Sometimes after reboot: screen:
"CMOS Settings Wrong, no data set"

Sometimes after reboot: screen:
 "No bootable device insert boot disc and press any key" error, for the rest of the time... 

Or sometimes just a black screen that does nothing at all.

Well... these are the most common boot screens I receive before it blocks :D Rocka rolla !

---

### Post by oldfred on 2014-11-20
Did you change BIOS to AHCI?

Someone also posted this a long time ago, do not know if you have that setting or not:
 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"

      
 Also check that drive is hd0 and grub in same drive.
ALERT! /dev/disk/by_uuid, then missing keyboard driver, chroot install new kernel
[http://ubuntuforums.org/showthread.php?t=2245053](http://ubuntuforums.org/showthread.php?t=2245053)

If you can boot, I would try a full set of updates. If you cannot boot then you have to chroot into system to run the updates.
      
 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

I would also do the full uninstall & reinstall of grub.

 #reinstall kernel:
sudo apt-get update
sudo apt-get upgrade
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
grub-install /dev/sda

   sudo apt-get install linux-image
sudo update-grub

---

### Post by bulevardi on 2014-11-20
> Did you change BIOS to AHCI?

Someone also posted this a long time ago, do not know if you have that setting or not:
 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
No, couldn't see that option anywhere.

Saw an option in the SATA controls to choose from:
- IDE
- disable


At the moment booting live CD, trying to change the grub.cfg file (as I read in some tutorials) so the address UUID="186545....   changes to /dev/sda1
But can't save that file. 

Guess I'm going to sleep for now. It's 1 AM here, and my daughters will wake me in a few hours,... 

Would a full reinstall of ubuntu from the live cd solve it?

---

### Post by oldfred on 2014-11-20
Maybe, but I would then then use 25GB for / (root) and make /home the rest of the drive.

I think the IDE setting may be an issue. Is this an old computer? My system from 2006 had AHCI as an option.
What does other tell you it is?

---

### Post by bulevardi on 2014-11-26
I cannot find AHCI as an option, anywhere in the BIOS menus.

It's this Motherboard:
[http://www.hardwaresecrets.com/article/MSI-P35-Neo-Combo-Motherboard-Review/460](http://www.hardwaresecrets.com/article/MSI-P35-Neo-Combo-Motherboard-Review/460)

It says: "... controlled by a Marvell chip. This chip controls a parallel ATA port, since Intel P35 chip does not support IDE devices"
In my BIOS, (advanced settings), I found "On Chip IDE Controller", I can only choose between IDE and Default.
I read somewhere that I maybe need to change the jumpers of my HDD to correct this or change cables slave/master. But before it worked... so I think they're good?
Otherwise, I should unplug harddrive, ram etc... plug back in and test again? I see no other solutions anymore.
Anyone else had this problem? Can I fix the IDE controller on my Motherboard?

Anyway, yesterday I found out that I maybe had wrong partitions and maybe no good boot mount.
I ran the live CD, started Gparted, formatted everything, and create a new good partition table with the right partitions for root, boot, swap and home.
Reïnstalled Ubuntu Studio. 
Rebooted, and the screen stayed black again.

So I can only restart again when pulling out the battery again.
Or should I try the reset jumpers on my Motherboard (resetting CMOS?).

---

### Post by oldfred on 2014-11-26
If your BIOS lets you set which drive to boot from you must have drive's jumpers set for cable select and must have the 80 conductor cable.

 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by bulevardi on 2014-11-26
Hmm, it's a Seagate 7200.10 320 GB.
With a connection like in this picture:
[IMG]http://galleryplus.ebayimg.com/ws/web/230977447883_1_0_1/1000x1000.jpg[/IMG]


I just unplugged and plugged again. Will soon test! Keep you posted!

---

### Post by bulevardi on 2014-11-26
Rebooted, got into BIOS, changed the boot sequence so hard drive is first. Saved.
Now, rebooted.... and the pc hangs again :(

Seems like he always blocks after changing a simple setting in bios.

---

### Post by oldfred on 2014-11-26
That is a new SATA drive, not an older IDE/PATA drive.

I would also make sure you are not plugged into the Marvel SATA port, you have 5 Intel SATA ports to use.
Does BIOS have separate settings for the Marvel & Intel ports, some systems do have settings that can be different for different groups of ports.

---

### Post by bulevardi on 2014-11-27
Hmm, as you can see in this manual: [http://www.msi.com/support/mb/P35_Neo.html#down-manual](http://www.msi.com/support/mb/P35_Neo.html#down-manual)
There is no AHCI support in this BIOS.

I don't know how the person who built this pc got this drive to work (before it used to be a win xp pc).
I'm hoping for someone to make a bios-mod to install:
[https://www.bios-mods.com/forum/Thread-AHCI-mod-for-MSI-P35-NEO?pid=80085#pid80085](https://www.bios-mods.com/forum/Thread-AHCI-mod-for-MSI-P35-NEO?pid=80085#pid80085)

Here's someone with the same problem:
[http://ubuntuforums.org/showthread.php?t=2229307](http://ubuntuforums.org/showthread.php?t=2229307)
After 5 pages of troubleshooting, still no solution, finally it seemed to be this AHCI setting in his bios. 
So I guess a bios mod is the only solution?

---

### Post by bulevardi on 2014-11-27
Hmm, found a modded bios:
[http://forum-de.msi.com/index.php?page=Thread&postID=771211#post771211](http://forum-de.msi.com/index.php?page=Thread&postID=771211#post771211)

But it's a german forum, hopefully the bios is not in German, but English...

Am I mad enough to try or not?

---

### Post by bulevardi on 2014-11-27
Haven't upgraded yet, with that modded bios.... pc didn't want to boot on USB anymore.
(maybe some occult powers came in between to save me from upgrading to an unreliable bios?)


Anyhow, currently, I made progress, system boots now with a GRUB prompt screen.
I now followed these steps here:
[http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)

And I could finally boot by following all these steps... 
Unfortunatelly, when trying to make these repairs permanently, and rebooted, the system doesn't boot anymore... again :(

---

### Post by oldfred on 2014-11-27
At the very least I would copy the commands that worked into 40_custom. Then you do not have to type each time.
That is a kludge or work around until actual problem is fixed.

       gksudo gedit /etc/grub.d/40_custom
sudo update-grub


 menuentry "Manual boot - sda1" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}


If you also had any insmod commands to add grub modules, include those in above example boot stanza.
That should add the new entry to the bottom of grub menu.

Did you run the full uninstall & reinstall of grub2 as in post #9? 
If you can boot you can run that. But make sure Internet is working as it has to download new grub and once old one is uninstalled, you must download and install new one.

---

### Post by bulevardi on 2014-12-02
> **oldfred said:**
> 
Did you run the full uninstall & reinstall of grub2 as in post #9? 

I updated with all the commands you proposed here:
```
#Then run whatever other commands needed - no sudo needed if chroot  (maybe good to run "df- H" and "cat /etc/issue" to be certain #you  mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

I would also do the full uninstall & reinstall of grub.

 #reinstall kernel:
sudo apt-get update
sudo apt-get upgrade
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
grub-install /dev/sda

   sudo apt-get install linux-image
sudo update-grub
```
But with that last one, to install the linux-image, he showed a list of linux images:
```
Pakket linux-image is een virtueel pakket voorzien door:
  linux-image-3.16.0-25-lowlatency 3.16.0-25.33~14.04.2
  linux-image-3.16.0-25-generic 3.16.0-25.33~14.04.2
  linux-image-3.13.0-40-lowlatency 3.13.0-40.69
  linux-image-3.13.0-40-generic 3.13.0-40.69
  linux-image-3.13.0-39-lowlatency 3.13.0-39.66
  linux-image-3.13.0-39-generic 3.13.0-39.66
  linux-image-3.13.0-37-lowlatency 3.13.0-37.64
  linux-image-3.13.0-37-generic 3.13.0-37.64
  linux-image-3.13.0-36-lowlatency 3.13.0-36.63
  linux-image-3.13.0-36-generic 3.13.0-36.63
  linux-image-3.13.0-35-lowlatency 3.13.0-35.62
  linux-image-3.13.0-35-generic 3.13.0-35.62
  linux-image-3.13.0-34-lowlatency 3.13.0-34.60
  linux-image-3.13.0-34-generic 3.13.0-34.60
  linux-image-3.13.0-33-lowlatency 3.13.0-33.58
  linux-image-3.13.0-33-generic 3.13.0-33.58
  linux-image-3.13.0-32-lowlatency 3.13.0-32.57
  linux-image-3.13.0-32-generic 3.13.0-32.57
  linux-image-3.13.0-30-lowlatency 3.13.0-30.55
  linux-image-3.13.0-30-generic 3.13.0-30.55
  linux-image-3.13.0-29-lowlatency 3.13.0-29.53
  linux-image-3.13.0-29-generic 3.13.0-29.53
  linux-image-3.13.0-27-lowlatency 3.13.0-27.50
  linux-image-3.13.0-27-generic 3.13.0-27.50
  linux-image-3.13.0-24-lowlatency 3.13.0-24.47
  linux-image-3.13.0-24-generic 3.13.0-24.47
U dient er één expliciet te selecteren voor installatie.

E: Pakket 'linux-image' heeft geen kandidaat voor installatie

```
With a warning: "E: package 'linux-image' does not have a candidate for installation.
Should I select one? And how?

Anyway, below a screenshot of my filesystem in the /boot/
There is a new image: initrd.img-3.13.0-40-lowlatency, but this one is still as GZip, should it get unpacked?
And this one: vmlinuz-3.13.0-40-lowlatency has type "unknown", while the previous one, version 3.13.0-32 has type "DOS/Windows-executive file".

[ATTACH=CONFIG]258321[/ATTACH] 

Haven't changed the 40_custom, yet, before I know I'm doing the right thing. 

I'm not sure which partition I should mention as /dev/sda...
I have following partition table:
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298,1G  0 disk 
&#9500;&#9472;sda1   8:1    0     1G  0 part /boot
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0    16G  0 part [SWAP]
&#9500;&#9472;sda6   8:6    0    30G  0 part /
&#9492;&#9472;sda7   8:7    0 251,1G  0 part /home
sr0     11:0    1  1024M  0 rom  

```
As linux is installed on sda6, I suppose I have to mention that as root? 
```

menuentry "Manual boot" {
    set root=(hd0,msdos6)
        linux /boot/vmlinuz-3.13.0-40-lowlatency root=/dev/sda6 ro quiet splash
        initrd /initrd.img-3.13.0-40-lowlatency
}
```

---

### Post by bulevardi on 2014-12-02
When I shut down the computer. And restart... he hangs again just with a black screen.
So each time I want to restart I have to remove battery again. 
I'm wondering if that has anything to do with these procedures above or not. Maybe he's not shutting down as it should.
Don't know anymore what I'm gonna do. :s

---

### Post by oldfred on 2014-12-02
If manually creating a boot stanza with a separate /boot partition you have to use both.
The set root = must be the boot partition or sda1 in your case
On linux line the root= entry must the the system partition where / is or sda6 in your case.

If not shutting down correctly, then grub gets flagged and should show menu on reboot.

---

### Post by bulevardi on 2014-12-05
Must have done something wrong. 
He now boots by showing only 2 possibilities in the grub menu, the linux generic and the one I've manually made.
None of both are booting, system shuts down automatically.


Now followed this tutorials to boot from grub by going into the menu, pressing C:

Following boot commands: 
```
set root=(hd0,6) 
linux (hd0,1)/vmlinuz-3.13.0-40-lowlatency root=/dev/sda6 
initrd (hd0,1)/initrd.img-3.13.0-40-lowlatency 
boot
```

.. but then my screen went flooding messages like:  "pciehp 00000..... card not present in slot // failed to check link  status" all the time. Tried different times. Anyone had this before too?  
Tried setting root=(hd0,1), same problems.
However, the 2nd line, linux... gives errors when trying to look on the /boot folder, and even with previous version:
linux /boot/vmlinuz-3.13.0-40-lowlatency root=/dev/sda6
linux /boot/vmlinuz-3.13.0-32-lowlatency root=/dev/sda6

Aside of that... 
Made a "super grub disk" repair usb stick. This one only shows a 'default' option that doesn't load anything, and a countdowntimer that loops counting from 10-0 and again and again.
My Ubuntu Studio Live CD (that previously worked well) , shows up menu to choose language and menu to boot live, and then loads... and shuts down the system.

---

### Post by oldfred on 2014-12-05
Post link to summary report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you always have separate /boot partition, or are some kernels in /boot in your / (root)?

---

### Post by bulevardi on 2014-12-07
[http://paste.ubuntu.com/9411961/](http://paste.ubuntu.com/9411961/)

Hopefully you have enough with that.

It's the summary report from a few minutes ago, before doing any changes.

---

### Post by oldfred on 2014-12-07
Go ahead and run Boot-Repair, but be sure to tick or make sure it found that you have the separate /boot in sda1 and / (root) in sda6.

Script often shows the kernels and grub?

In your manual boot in 40_custom needs to say hd0,msdos1 as that is where your /boot is per fstab.
 set root=(hd0,msdos6)

Did you put kernels in the /boot partition?

You have a grub installed to the partition boot sector of sda6, that will never be used and generally you do not install grub to a partition.

---

### Post by bulevardi on 2014-12-08
I ran the Boot-Repair
I now have another log: 
[http://paste.ubuntu.com/9423908/](http://paste.ubuntu.com/9423908/)

I deleted the manual menu from 40_custom.

When I restart, he does not boot at all.
Again same poblem: have to remove battery and place it in again, (new battery).
Then after the first screen with the Motherboard logo  'press tab for post, del for bios', I get error : "CMOS Settings wrong, ... no hard disk detected..."
Then I get to choose F1 to enter setup menu, F2 to load default...
F2
I get to see the Grub Menu with all the options.
I select the first one 'Ubuntu Lowlatency' which is installed.
I get an error message 'malformed file.... '  
And then Ubuntu starts normally.

So I can get it started each time, but I have to go through all this fuzz again each time.
Grub seems to be well... But the problems occur even before. I cannot update settings in BIOS, If I save them, he doesn't start, need to reboot, doesn't reboot, have to remove battery again, and lost the updated bios settings.
So perhaps there's something with the BIOS?  
And then we're back to the beginning of this thread.

---

### Post by oldfred on 2014-12-08
I do not know enough about BIOS settings to know what might need changing. It may just be BIOS is not happy with new CPU? 

If you look in log file do you see the malformed file error and does it tell anything more.

 sudo nano /var/log/dmesg

---

### Post by bulevardi on 2014-12-22
Hi ! 

Just wanted to let you know that everything is solved right now. :)

There seemed to be 2 different kind of BIOS chips for the MSI P35 neo motherboard. On the MSI forum, they helped me to find the correct new BIOS to flash.

The new BIOS seems to work great and saves the changes I make. No need to remove battery anymore.

However, it did not find the OS, so there was something wrong with bootloader, or where the boot, root or grub thing was located.
To avoid all the troubleshooting for that again, I downloaded the new verion of the OS (Linux Ubuntu Studio 14.04), and did a brand new install.
Since then the bootloader works again as it should!

Needs to say: many thanks for the great help right here!

---

### Post by oldfred on 2014-12-22
Sometimes a full reinstall is the quickest way to resolve issues.

Glad you got it resolved. :)

---

