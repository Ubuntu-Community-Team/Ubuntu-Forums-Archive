---
title: "Grub doesn't work"
date: 2018-01-10
forum: MINT
---

### Post by sheine on 2018-01-10
I bought a refurbished Dell Ubuntu computer, Dell Latitude E5510. As I have done with previous Windows computers I partitioned it in order to have several versions of linux. I then installed my favorite, Mint, on a partition and attempted to start it. Grub instead of giving me the usual choice went to the grub rescue terminal, which I didn't know existed. I then hoped that by erasing all the partition and reinstalling Ubuntu on the whole disk, I would have a workable computer. I still got the grub rescue terminal. 

Searching the Internet, I found a number of sites with instructions on how to make the computer usable. They all ended at the same place, so here is a simple one. Install the live Ubuntu and go to the terminal.  Here is what I then did:
sudo apt-get install grub-efi (This command was accepted.)
sudo mount /dev/sda1  mnt. (This command was accepted.)
sudo grub-install --root-directory=/mnt/dev/sda
Installing for i386-pc platform
grub-install :error : install device is not specified

My other attempts were more complicated versions of this and ended with the same last line.

How do I get my computer to install something that I can use?

---

### Post by oldfred on 2018-01-10
Moved to MINT sub-forum.

Is that Dell UEFI or BIOS?
And did you install in UEFI or BIOS?
If is drive gpt partitioned or MBR partitioned?

You have to be consistent. Always UEFI with gpt.
If possibility of Windows in BIOS boot  mode, you must use MBR.
But Ubuntu can also boot in BIOS mode from gpt partitioned drives.
IF drive is gpt.
If UEFI, you must have the ESP, FAT32 with boot flag and if BIOS you must have bios_grub partition, 1 or 2MB unformatted with bios_grub flag.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by sheine on 2018-01-10
I partitioned with current version of Gparted.

I found this on the Internet:
"What OS? How was it installed in UEFI or Legacy?

"This system is the earliest systems with a UEFI BIOS and so may be booting to UEFI instead of legacy etc. 

How would I find out for myself?"


Since it is a Ubuntu computer there should be no Windows elements.

---

### Post by yancek on 2018-01-10
Boot the Mint installation media and go online to the first link posted above by oldfred and download the boot repair software.  When running it, make sure you select the option to Create BootInfo Summary and post a link to the output here.  Do not try to make any repairs before doing this.  Someone should then be able to advise you.

---

### Post by sheine on 2018-01-10
[http://paste.ubuntu.com/26362503/](http://paste.ubuntu.com/26362503/)

---

### Post by oldfred on 2018-01-10
Install looks pretty normal.But you only have one ext4 partition, so only one install.
You have BIOS with MBR partitions.

But I do not think you can update an Ubuntu install using MINT, repositories will not be totally the same.
Best to always use same version live installer to run repairs.

---

### Post by sheine on 2018-01-10
What should I do now, wait for more instructions  or use boot-repair?

---

### Post by sheine on 2018-01-11
I ran boot-repair and my computer is now working. If I now install Mint and again lose access, can I get grub to work again by running boot-repair again?

---

### Post by yancek on 2018-01-11
As pointed out by oldfred above, you have a BIOS/MBR system so you need to avoid anything UEFI related and if you want to install another Linux system, you will need unallocated space on which to do it and make sure you do not install the bootloader for the second system to the MBR and continue to use the Mint bootloader,.  Generally, you would be able to do this with a Linux install by selecting the partition when you see an option for 'Device for bootloader installation.

---

### Post by sheine on 2018-01-11
It seems that everything becomes more difficult. I installed Mint and grub still worked taking me to Ubuntu. I then ran update-grub, restarted the computer and selected Mint from grub. But, when I attempted to start Mint, I got this:
error: invalid extent
error: You need to load the kernel first.

I looked at grub.cfg in Ubuntu and it has the correct entry for Mint.

---

### Post by oldfred on 2018-01-11
Post link to new summary report from Boot-Repair.

---

### Post by sheine on 2018-01-11
[http://paste.ubuntu.com/26368286/](http://paste.ubuntu.com/26368286/)

---

### Post by oldfred on 2018-01-12
Is drive set for AHCI?

I do not really see anything wrong.

Did you verify your download of Mint was valid.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sheine on 2018-01-12
The drive is set for AHCI.

---

### Post by oldfred on 2018-01-12
If Ubuntu works and Mint does not, then I would suspect something wrong with your copy of Mint.
Try redownloading it, check its md5sum or use zsync to download to existing ISO which will automatically verify it is correct.

Zsync is in Ubuntu repository:
> zsync is a file transfer program to download files from
remote web servers. If a previous version of a file is available
locally, zsync will only download changed parts and hereby
minimise the download volume.

example of commands, but do not know Mint local mirror for you, or name of Mint ISO.
I have all my ISO in an ISO folder in /home
cd ISO
zsync [http://cdimage.ubuntu.com/daily-live/current/bionic-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/bionic-desktop-amd64.iso.zsync)
zsync [http://mirrors.gigenet.com/ubuntu/16.04/ubuntu-16.04-desktop-amd64.iso.zsync](http://mirrors.gigenet.com/ubuntu/16.04/ubuntu-16.04-desktop-amd64.iso.zsync)

---

### Post by sheine on 2018-01-12
I downloaded a new copy of Mint with md5sum, installed it as before and ended up with the same two errors when I tried to load Mint from grub.

---

### Post by oldfred on 2018-01-12
I thought newer systems with AHCI did not have this issue.

[https://ubuntuforums.org/showthread.php?t=2239624](https://ubuntuforums.org/showthread.php?t=2239624)

You may need to add a /boot or make both installs have / (root) partition in first 100GB of drive.
I typically install in 25GB / (root) partitions, and then have a large ext4 shared data partition mounted at /mnt/data.
And issue depends on where on drive grub & kernels are installed, which normally is random. So system may work until you get an updated kernel and its further into partition.

---

### Post by sheine on 2018-01-12
I tried something that failed but may give you a clue. On my other computer of the same year as the Dell, I successfully installed Mint a while back. I now downloaded the same version of Mint, Petra, and installed it. In this case, grub gave me a different error message: Kernel panic-not syncing: Unable to mount root fs on unknown block.

---

### Post by oldfred on 2018-01-12
It seems like the same kind of issue. 
Are you installing in one very large / (root) partition.
You want a smaller / partition of 25GB for every install and keep that inside the first 100GB of drive. Then rest of drive can be separate /home partition(s) or large data partition.

---

### Post by sheine on 2018-01-13
The Ubuntu boot that I am using is grub 2.02. Can I get into any trouble by reinstalling Mint and using its boot loader rather than the Ubuntu loader on sda1?

---

### Post by oldfred on 2018-01-14
Do not know Mint and what versions it uses.
But  over the years I have used one grub from the current LTS to boot both older & newer Ubuntu versions. 
So I would think it would work. 
Many users re-install, but do not update MBR. The old version in MBR is looking for old install. So make sure to fully install grub.

---

### Post by sheine on 2018-01-14
At least, I did no harm. After the installation, I got the grub terminal. Then I did Boot-Repair. Restarted the computer and could load Ubuntu but not Mint. Code 26386694. I may need to learn to live with just Ubuntu, it is O.K. but not what I want. I do not know how to do this "Many users re-install, but do not update MBR. The old version in MBR is looking for old install. So make sure to fully install grub."

---

### Post by oldfred on 2018-01-14
Normal install should fully update to that installs grub. 
Often if user has more than one install or more than one drive, or elects during install not it install grub to MBR, that is when issues develop.

Best to ask on Mint forum, if issues are unique to Mint.

---

### Post by sheine on 2018-01-14
I did a standard install of Mint which chose the place for grub. I assume that since I can still boot Ubuntu and the Mint grub was installed, Ubuntu  was installed from this grub, otherwise the old grub from Ubuntu is still in control and where can it be. Where is MBR and how do I access it?

---

### Post by oldfred on 2018-01-14
You do not directly access MBR.
When you install a BIOS based system, you tell it which MBR (never a partition) to install the boot loader part of grub.
It defaults to sda which is normally the drive the BIOS defaults to to start the boot process.

With different Linux installs, you can tell which is in MBR as that will then be first in boot menu.
Other installs will be at bottom of grub's boot menu.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by sheine on 2018-01-14
I told Mint to install grub in sda. The first listed OS on starting is Ubuntu. From what you wrote, this means that Mint never installed its version of grub. How can I change this?

---

### Post by oldfred on 2018-01-14
I posted the links, but if Mint did not install its copy of grub, then Mint did not correctly install. 
One of last steps in install process is install of grub. 
Did you see any error messages during install?

Links posted about are reinstalling grub if install is otherwise correct. 
But with Boot-Repair you have to use advanced mode, otherwise it just seems to find first install it sees and offers to reinstall that grub.

---

### Post by sheine on 2018-01-14
I used advanced mode in Boot-Repair and installed the Mint grub with the warning that it might be too far out. It was. I am now back with only Ubuntu working, which is not too bad. I need to learn how to install an OS with its home folder on another partition.

---

### Post by sheine on 2018-01-15
Thanks to oldfred I now have a dual booting computer. I repartitioned with small primary partitions and the home folder in the extended partition. Everything went smoothly and both Mint and Ubuntu are booting.

---

### Post by sheine on 2018-01-15
Solved.

---

