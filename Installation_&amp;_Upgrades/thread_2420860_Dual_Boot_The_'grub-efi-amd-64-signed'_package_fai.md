---
title: "Dual Boot: The 'grub-efi-amd-64-signed' package failed to install into /target/"
date: 2019-06-12
forum: Installation &amp; Upgrades
---

### Post by dethrone on 2019-06-12
Hello!

Over the last week, I've struggled tremendously trying to dual boot my Asus VivioX541 with Windows 10 and Ubuntu 16.04.
I'm booting in UEFI mode, and I have three partitions ready for Ubuntu: ext4, swp and efi. When it tries to install 'grub2' package, I get the following error:
```
The 'grub-efi-amd-64-signed' package failed to install into /target/
```

I've literally tried *every* solution I could find on the internet with no success. I've attached a condensed version of the /var/log/syslog ([ATTACH]283419[/ATTACH]) just in case (I filtered out most of the ubuntu-kernel stuff leaving just the part where it tries to install grub...); in particular, it contains the error line in question:
```
Jun 12 04:10:05 ubuntu grub-installer: info: Calling 'apt-install grub-efi-amd64-signed' failed 
```

Potato quality of my partitions... I'm using sda7 for ext4, sda6 for swap, and sda5 for efi.
 [ATTACH=CONFIG]283417[/ATTACH][ATTACH=CONFIG]283418[/ATTACH]

Thanks so much!

---

### Post by yancek on 2019-06-12
The standard method for installing Ubuntu on a system with an EFI  install of windows is to install Grub files into a folder created by the  Ubuntu installer on the already existing EFI partition.  Your EFI  partition (sda4) already has the windows boot files.  You also have two other EFI partitions (sda5 and sda8) which are not necessary and should not be there.  You can mount each partition and check to see if Ubuntu EFI files are installed on any.  They should be on sda4 and the other two EFI partitions should not exist.

---

### Post by dethrone on 2019-06-12
Hi Yancek,

Thanks for the reply. I can try later completely deleting the other two EFI partitions. But I have already tried de-selecting all the other EFI partitions during the installation process by "Do not use this partition" and only using sda4 which did not help.

---

### Post by oldfred on 2019-06-12
Ubuntu installer only finds one ESP - efi system partition, and it uses default, not sure how it selects. I have found a work around for installs to second or external drives.

       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) 
    
Otherwise if dual booting you generally want to have just one ESP per drive. Most systems will not work if more than one ESP seen.

You probably have to totally reinstall grub, so GUID that your UEFI uses to find ESP is correct partition. And ESP needs to have both Windows /EFI/Microsoft & /EFI/ubuntu folders.

If still issues, but autofix is not always correct, sometimes you need to use advanced mode to make full set of fixes.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dethrone on 2019-06-15
Thank you everyone for your answers; however, I am still seeing this error.

I reformatted my entire hard-drive and repeated the entire process. This is what my partitions look like:
[ATTACH=CONFIG]283434[/ATTACH]

A few notes:

1. I always have to add 'pci=nomsi' to my grub boot option in order for the partitions on my disk to be seen (e.g otherwise, when I press "Something else" for the installation no partitions appear). 
2. Looks like my EFI partition is formatted 'vfat' instead of 'fat32'; is that an issue?
3. I only have one EFI partition now, and I have verified it contains both EFI/microsoft and EFI/ubuntu.

What is the next thing I should try?

4. Oldfred, you mention a workaround in your answer:

    1  mount
    2  sudo umount /target/boot/efi
    3  sudo mount /dev/sdc1 /target/boot/efi
    4  mount

But when I use my USB installation media, I have no access to the ubuntu terminal to enter these. So where do I enter these? 

5. "You probably have to totally reinstall grub". How do I do this without access to ubuntu terminal?

---

### Post by dethrone on 2019-06-15
An update:

I chose the option "Try Ubuntu..." with pci=nomsi and ran "ubiquity -b" in the terminal. 
Here's my setup:

[ATTACH=CONFIG]283438[/ATTACH]

246 GB ext4 mounted on /
16 GB swap 
104 MB EFI

I am pretty sure that the installer is actually mounting on the right partitions, including EFI. This is what I see *during *the ubiquity installation, after I select "Something else...":

[ATTACH=CONFIG]283439[/ATTACH]
We see /target/boot/efi is mounted on the EFI partition / Windows Boot Partition.
We see /target mounted on the 246 GB partition.

But, I get a new error from this:

[ATTACH=CONFIG]283440[/ATTACH]

---

### Post by oldfred on 2019-06-15
Your Windows 10 does not look like an UEFI install.
Is or was drive MBR? You normally would have ESP as first or second and Windows required a Microsoft reserved before the first NTFS partition with UEFI. With BIOS you normally have a Boot partition and the main or c: drive partition. But boot partition is not required.

I always boot into live mode and open terminal first thing. Then click on the install icon.

---

### Post by dethrone on 2019-06-15
Hi oldfred, thanks for the reply!

My partition is definitely GPT / GUID partition style - I'm assuming that means it was a UEFI install. 
ESP is the second drive on my disk (sda2), but if you think my partition layout looks wrong, perhaps I downloaded the wrong iso.
I can't remember where I downloaded this iso from or which options I chose, but this is what the filesystem looks like:
[ATTACH=CONFIG]283441[/ATTACH]

I think I used Microsoft's MediaCreationTool to create this installer which technically should have support for both UEFI and BIOS. Or would using something like Rufus be better where I can tell it I just want UEFI support? Maybe I should redownload the Windows installer and try everything again?

---

### Post by oldfred on 2019-06-15
If drive is gpt and Windows boots, then it has to be UEFI as Windows only boots in UEFI mode from gpt (and only in BIOS from MBR).
So then you want Ubuntu in UEFI boot mode. And how you boot install media UEFI or BIOS is then how it installs.

You should only have one ESP - efi system partition per drive and now with 18.04 or later so not need a swap partition as it uses a swap file.
       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
            UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
            Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)  
    
Also more info in link in my signature.

---

### Post by dethrone on 2019-06-15
Hi [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711"), thanks for the help!

I read through all the links, but I'm still getting these errors.
I tried something new from this link: [https://askubuntu.com/questions/1028703/the-grub-efi-amd64-signed-package-failed-to-install-target](https://askubuntu.com/questions/1028703/the-grub-efi-amd64-signed-package-failed-to-install-target)

Basically, I'm running the installer manually:
```

sudo ubiquity -b
sudo mount /dev/sda6 /mnt
sudo mkdir /mnt/boot/efi
sudo mount /dev/sda2 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

sudo modprobe efivars
sudo apt-get install --reinstall grub-efi-amd64-signed
```

One modification - I had to remount /dev/sda6 with "rw" permissions because otherwise it wouldn't let me modify/install anything in /mnt.
**However,** whenever I run either

```
sudo grub-install --no-nvram --root-directory=/mnt
```

or 
```

update-grub

```

I get the error:
```

Generating grub configuration file ...
error: cannot read 'dev/sda': Input/output error.
error: cannot read 'dev/sda': Input/output error.
error: cannot read 'dev/sda': Input/output error.
error: cannot read 'dev/sda': Input/output error.

```

These are the same errors I get when I run installer directly from the USB (I verified this by reading through the /var/log/syslogs, attached earlier).
I don't think there's anything wrong with my hard-drive...
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
                                                                               
      229287 inodes used (1.53%, out of 15024128)
          53 non-contiguous files (0.0%)
         208 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 181766/8
     2313940 blocks used (3.85%, out of 60093696)
           0 bad blocks
           1 large file

      140110 regular files
       24573 directories
          54 character device files
          25 block device files
           0 fifos
           2 links
       64516 symbolic links (47426 fast symbolic links)
           0 sockets
------------
      229280 files
```

And
```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda6
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      229287 inodes used (1.53%, out of 15024128)
          53 non-contiguous files (0.0%)
         208 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 181766/8
     2313940 blocks used (3.85%, out of 60093696)
           0 bad blocks
           1 large file

      140110 regular files
       24573 directories
          54 character device files
          25 block device files
           0 fifos
           2 links
       64516 symbolic links (47426 fast symbolic links)
           0 sockets
------------
      229280 files
```

---

### Post by oldfred on 2019-06-16
I might download a new copy of Ubuntu ISO and install it fresh to a flash drive.

       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)
Create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by dethrone on 2019-06-16
Hi oldfred,

Already tried that many times already. :(
I guess I;ll try install 18.04 instead of 16.04.

---

### Post by oldfred on 2019-06-16
You may also need nomodeset boot parameter until you install the nVidia proprietary driver.
Very newest versions of Ubuntu will install that also when you check to install proprietary drivers during install.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[URL="https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter"]https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter

      [/URL]
 Asus Zenbook UX433FN with nVidia
[https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn](https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn)
Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221)
Asus X541UV [SOLVED] How to partition my ssd in order to install ubuntu 17.10 / 16.04.4
[https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)
Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408) 
    [URL="https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter"]
[/URL]

---

### Post by dethrone on 2019-06-17
Hi oldfred,

I was able to fix the error by turning off fast  start-up and hibernation in Windows 10 which was making the EFI  partition read-only.

However, I am failing at the 'update-grub' stage. For some reason, *before* running grub-install or update-grub, /target/boot/grub is read-writable, but *after*  running, /target/boot/grub is changed to read-only and it complains  that it cannot remove /boot/grub/grub.cfg.new because the partition is  read-only.

Any ideas how to fix this, or what could be causing this? The partitions are all OK (fsck returns no errors), and mount -o remount,rw / doesn't work.

Thanks.

---

### Post by oldfred on 2019-06-17
Back with 14.04 Ubuntu's default parameter for the ESP was defaults. The since changed to 0077 which means it is mounted with no permissions to write. So Boot-Repair automatically changes it and I change mine manually by commenting out original entry with #.
It probably is a good idea to change it back  as preventing writes is a secuity issue and Windows formats like NTFS & FAT32 have only permissions set at mount. 

But you should never have /boot/grub/grub.cfg.new as that is only written when you have a typo somewhere in either the scripts or parameters that grub uses to build grub.cfg.
Check /etc/default/grub     and if you edited any scripts in /etc/grub.d.

```
# /boot/efi was on /dev/sda1 during installation
#UUID=FD76-E33D  /boot/efi       vfat    umask=0077      0       1
UUID=F626-A4D4  /boot/efi       vfat    defaults      0       1


```

---

### Post by dethrone on 2019-06-17
Hi oldfred,

Again, super grateful for the help.
I'm not at home right now so I can't check, but if I am understanding correctly, i just need to comment out the first line (UUID=FD76-E33D) of this file *before* I run the installer? 

```
# /boot/efi was on /dev/sda1 during installation
#UUID=FD76-E33D  /boot/efi       vfat    umask=0077      0       1
UUID=F626-A4D4  /boot/efi       vfat    defaults      0       1
```

Which file is this?

Actually, since the installer mounts the partitions, I would need to edit this file during the installation when the partitions are mounted, but before grub is being installed? Either that or I do it all manually.

---

### Post by oldfred on 2019-06-17
Is error writing into ESP - efi system partition /boot/efi/EFI/ubuntu/grub.cfg or really in /boot/grub/grub.cfg?  The grub.cfg in ESP is just 3 lines to load the full grub.cfg in your install.

I think real issue must be some configuration setting as you should not have /boot/grub/grub.cfg.new, any install should be overwriting /boot/grub/grub.cfg.


If booted it is /etc/fstab, but that is the grub.cfg for UEFI boot and is just a 3 line configfile entry to boot full grub.cfg in your install.

If in live installer you have to mount partition, so depends on mount.

I normally edit it after install, and do not have issues during install, but only when manually changing settings in UEFI. New install always overwrites /EFI/ubuntu but I have a main working install using 18.04LTS and always want that as default. So I typically boot, edit fstab, or booting my 18.04 from new install's grub and edit /boot/efi/EFI/ubuntu/grub.cfg to change to correct install.

---

### Post by dethrone on 2019-06-17
Hi oldfred,

Some updates. Ran the installer manually in live mode so I could debug... when I got to this step:

```
ubuntu@ubuntu:~$ sudo grub-install --no-nvram --root-directory=/target
Installing for x86_64-efi platform.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.

 Installation finished. No error reported.
```

and

```
ubuntu@ubuntu:~$ sudo chroot /target
root@ubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
error: cannot read `/dev/sda': Input/output error.
cat: write error: Read-only file system
cat: write error: Read-only file system
```

In the file /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=7b59cef1-ec97-493a-aac3-6b658543fa3b /               ext4    errors=remount-rw 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=22E9-8C35  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda5 during installation
UUID=c033c24d-7af5-4022-ba79-6bde9b16899c none            swap    sw              0       0
```

I did comment out that line "/boot/efi". But I think that is not the problem? The problem is that /target/boot/grub somehow always gets remounted as "ro". 
Just to be safe, I also changed the first line from "errors=remount-ro" to "errors=remount-rw".

1. There were no "grub.cfg.new" file generated this time. There isn't even a grub.cfg since the grub stuff failed.
2. The main culprit seems to be the line "cannot read `/dev/sda': Input/output error.". 
3. Maybe we can get some insight on this if we can somehow run grub-install or update-grub in *verbose mode*. Is there such a setting?
4. I believe if we can generate a grub.cfg, then the problem is solved. Maybe there is a filesystem on /dev/sda that is somehow not readable?

---

### Post by oldfred on 2019-06-17
Change back to ro as that lets you boot recovery mode and run fsck if needed as partition is not mounted.

It seems strange that it says it cannot read sda, as it should be working with partitions like sda2 for ESP and sda6 for /. 

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dethrone on 2019-06-18
> **oldfred said:**
> 
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thanks, I will try that in a bit.

I read online ([https://ubuntuforums.org/showthread.php?t=2246824](https://ubuntuforums.org/showthread.php?t=2246824)) that it could be due to bad sectors on disk. 
I'm currently running "badblocks" and I'm 10% finished with 751 bad sectors so far...
Would you recommend me try and zero out those sectors? ([https://askubuntu.com/questions/751134/problems-restoring-damaged-sectors-on-hdd](https://askubuntu.com/questions/751134/problems-restoring-damaged-sectors-on-hdd))
I think the hard drive should be fine... startctl status is PASS and I can run windows just fine. But maybe Ubuntu is complaining because it can't read some of the sectors?

EDIT:
Running grub-install in verbose mode, I see a ton of messages being logged as "adding a relocation entry for xxx". So maybe this is a case of too many bad sectors on the disk.

---

### Post by oldfred on 2019-06-18
A few bad sectors can be normal, yours looks like a lot.
I would make sure backups are good and get a new drive.

---

### Post by dethrone on 2019-06-19
Hi Oldfred, thanks very much for the help through this long journey. I was finally able to successfully dual-boot by writing zeros to the bad sectors.

I'm going to put a quick summary here for future readers.

Laptop Model: Asus VivioX541
1. Run installer with grub boot parameter pci=nomsi
2. Make sure to turn off Window's fast start-up and hibernation. Otherwise, during boot-up the dirty bit of the EFI partition gets set and Ubuntu can only mount a read-only filesystem of the EFI partition. Grub cannot install like this.
2. If 'grub-efi-amd-64-signed' package failed to install into /target/ is still seen, try to run the installer manually to see exactly where the issue lies: [https://askubuntu.com/questions/1028...install-target]("https://askubuntu.com/questions/1028703/the-grub-efi-amd64-signed-package-failed-to-install-target")
3. Run the grub-install in verbose mode and check the kernel logs (/var/log/syslog). If it complains that it can't read /dev/sda/, run a bad sector check using "badblocks". Either write zeros to those sectors directly or write zeros to the entire ext4 and EFI partition using "shred" so that the bad sectors get relocated or marked. 
4. Redo the installer. 
5. If this works, but ubuntu boots to a purple or black screen, add "nomodeset" as a temporary workaround.
6. Once booted, upgrade the system to get the latest graphic drivers. At this point, most likely nomodeset is no longer needed (at least for me).
7. Update grub parameters before powering off, and run sudo grub-update.

I'm using the following grub parameters:
pci=nomsi quiet splash i915.modeset=1
GRUB_GFXMODE=1366x768

Hope I didn't leave anything out. :p

---

