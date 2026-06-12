---
title: "Beginner needs help with Boot-Repair failure - pastebin link provided"
date: 2016-03-09
forum: Installation &amp; Upgrades
---

### Post by Bob_Voges on 2016-03-09
[h=2](cross-posted in New to Ubuntu forum)[/h][COLOR=#000000][INDENT]I have very limited experience with linux and no prior experience with ubuntu, or with installing linux.

I installed Ubuntu from a Lili USB stick onto my Windows 7 Professional SP1 laptop (Lenovo Thinkpad W520) as dual-boot. 

I got the Ubuntu boot options screen (at the top it reads "GNU GRUB version 2.02~beta2-22ubuntu1")but it has never successfully booted all the way into Ubuntu - if I chose Ubuntu before running boot-repair (see below), it tried to start Ubuntu but never quite got there. It ended up in text mode flashing the following message on the screen:


"starting version 219 Starting WPA supplicant... [ OK ] Started Light Display Manager. [ OK ] Started WPA supplicant. [ OK ] Started ACPI event daemon. Starting ACPI event daemon..."


The first few times I tried booting into Windows, it failed almost immediately with a classic Windows bluescreen, but by the third or fourth time it got to the windows login screen before bluescreening, and now it boots Windows reliably every time.


I then booted into Ubuntu using the "Try Ubuntu" option on an Ubuntu Live disc, installed boot-repair, ran boot-repair and chose the "recommended repair" option.

The only change is that the Ubuntu boot fails at a different point with different messages.

Still a flashing screen, with a number of messages, each of which includes the following" "fault at 0x002140 [!ENGINE]"

I can provide the full text of the messages if it's helpful.


[FONT=arial]pastebin link is[/FONT]

[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/15323609/](http://paste.ubuntu.com/15323609/)

Thanks in advance for any help you can provide. I will also ask on the new to ubuntu forum, and I have emailed this information to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].[/FONT][/INDENT]
[/COLOR]

---

### Post by grahammechanical on 2016-03-09
It is unrelated to this problem but it is important none-the-less. It seems that you have installed Ubuntu 15.04 which reached end of life 4 February 2016. It will no longer get any security fixes. Now, as to what I see as the problem and it is in the Boot Repair summary.

> Generating grub configuration file ...
cat: write error: **No space left on device**

How can that be? There are three partitions for Linux

sda5 = Ext4 Ubuntu 15.04 + Grub configuration files
sda6 = swap
sda7 = Ext4 no information as to what it is for.

And then there is this

> Windows not detected by os-prober on sda2.
mkdir: cannot create directory &#8216;/mnt/boot-sav/sda5/var/log/boot-sav/log&#8217;: No space left on device
**sda5** is Read-only **or full****[**/QUOTE]

And this
[QUOTE]
Number  Start   End     Size    Type      File system     Flags
1      1049kB  10.4GB  10.4GB  primary   ntfs            boot, diag
2      10.4GB  144GB   134GB   primary   ntfs
3      144GB   160GB   15.8GB  extended
**5**      144GB   149GB   **4304MB**  logical   ext4
6      149GB   149GB   539MB   logical   linux-swap(v1)
**7**      149GB   160GB   **10.9GB**  logical   ext4


Did you intend sda5 to be a boot partition and sda7 (10.9 GB) to be the Ubuntu partition? I think that sda5 is too small for a Ubuntu installation. Something was not done right during installation. Ubuntu should be in sda7. In my opinion.

> =================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          149.1G
sda1  part ntfs       9.7G System
sda2  part ntfs     124.7G Windows
sda3  part              1K
sda5  part ext4         **4G**
sda6  part swap       514M
sda7  part ext4      10.2G

I think that 5 GB is the absolute minimum but I doubt that you will be able to install many (any?) additional applications. If my memory serves me well, the installer usually  says available disk space 6 - 7 GB.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by Bucky Ball on 2016-03-09
> **grahammechanical said:**
> It is unrelated to this problem but it is important none-the-less. It seems that you have installed Ubuntu 15.04 which reached end of life 4 February 2016.

^^^
This.

Best to [start with a supported release]("http://www.ubuntu.com/download/desktop"). 14.04 LTS is supported until 2019, 15.10 until end of May (from memory) this year. LTS releases have five years support, the rest nine months.

See if you get the same issues and report back.

PS: This has nothing to do with Boot Repair by the looks. If you installed and were getting the boot screen to choose and OS, all good to that point. The WPA supplicant error would indicate it is having an issue with internet, wireless perhaps. 

Did you click the 'Install third-party drivers' box during install? Don't do that next time. It can cause issues. Set up any required drivers later (which might not be required!).

---

### Post by kansasnoob on 2016-03-09
I see you installed 15.04 which is already end-of-life:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Looks like the Lenovo Thinkpad W520 has hybrid graphics:

> *******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
Subsystem: Lenovo Device [17aa:21d1]
Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GLM [Quadro 1000M] [10de:0dfa] (rev a1)
Subsystem: Lenovo Device [17aa:21d1]
Kernel driver in use: nouveau
03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)
*******

Since 15.04 is EOL it would be best to either install 14.04.4 or 15.10 and then try to sort out the graphics issue. Just search "ubuntu Lenovo Thinkpad W520" and a lot of graphics releated topics pop up. But it would be pointless to try and fix 15.04.

In short, it's not a grub problem but rather a graphics driver problem.

---

### Post by kansasnoob on 2016-03-09
> **grahammechanical said:**
> It is unrelated to this problem but it is important none-the-less. It seems that you have installed Ubuntu 15.04 which reached end of life 4 February 2016. It will no longer get any security fixes. Now, as to what I see as the problem and it is in the Boot Repair summary.



How can that be? There are three partitions for Linux

sda5 = Ext4 Ubuntu 15.04 + Grub configuration files
sda6 = swap
sda7 = Ext4 no information as to what it is for.

And then there is this

> Windows not detected by os-prober on sda2.
mkdir: cannot create directory ‘/mnt/boot-sav/sda5/var/log/boot-sav/log’: No space left on device
**sda5** is Read-only **or full****[**/QUOTE]

And this



Did you intend sda5 to be a boot partition and sda7 (10.9 GB) to be the Ubuntu partition? I think that sda5 is too small for a Ubuntu installation. Something was not done right during installation. Ubuntu should be in sda7. In my opinion.



I think that 5 GB is the absolute minimum but I doubt that you will be able to install many (any?) additional applications. If my memory serves me well, the installer usually  says available disk space 6 - 7 GB.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

Partitioning looks OK to me according to fstab:

[QUOTE]=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=0e891470-a319-4704-8bdf-c2e7547dd534 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=cd1d3bd6-9dd5-43d3-b66d-1a41330972eb /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=74b13ea3-00b2-480a-8fce-dd75a1ac3569 none            swap    sw              0       0
--------------------------------------------------------------------------------

---

### Post by Bucky Ball on 2016-03-09
> **kansasnoob said:**
> 
How can that be? There are three partitions for Linux

sda5 = Ext4 Ubuntu 15.04 + Grub configuration files
sda6 = swap
sda7 = Ext4 no information as to what it is for.

And then there is this

Partitioning looks OK to me according to fstab:

Booting up and getting through the grub menu list fine, stalling on WPA supplicant error. Internet issue. Need to fix that and see if it gets all the way. The first choice is to whack in a cable and get the machine online, then boot. The error message generally indicates it is trying to connect with wireless but the drivers are missing so it just locks there.

There does seem to be an issue when Boot Repair tries a repair, but let's see what a fresh supported release looks like.

@Bob_Voges: When/if you try again and you get the same issue, plug in an ethernet cable and we can help you fix wireless drivers on another thread if you need it. If that doesn't work, try boot repair but don't run the recommended repair. Just run the bootinfo script again and post it here prior to doing anything. Recommended repair spews grubs all over and that's not ideal. ;)

---

### Post by Bob_Voges on 2016-03-09
OK, thanks for all this help (and fast, too). So my next question is: is it safe to just install 14.04 over the current install? That is, if I have a 14.04 ubuntu live disk, can I just boot from it and choose install ubuntu? I don't have to remove/repair the current installation first.

(Worked in technical jobs at Lotus and IBM for 28 years and managed to avoid learning anything at all about bootloaders. Now I teach programming in high school and my students know more about this stuff than I do.)

---

### Post by oldfred on 2016-03-09
You do not have much if any room.

Windows works best with 30% free space inside the NTFS partition. At 10% free it gets so limited that you may not be able to run defrag as no space to move things around. And it gets real slow due to all the fragments. 
You show sda2 at 92% used.

And best to only use Windows own disk tools to resize it and then immediately reboot as after any resize it needs to run chkdsk to update internal size to new size.
Using installer usually works but some users have had major issues and best just to use Windows tools for Windows and Linux tools for Linux.

I partition 20GB for / (root) and actually have used about 11 to 13GB in main working install. I think new minimum is about 9GB but then you do not have room to add anything.

---

### Post by Bob_Voges on 2016-03-09
[COLOR=#000000]> Did you intend sda5 to be a boot partition and sda7 (10.9 GB) to be the Ubuntu partition? I think that sda5 is too small for a Ubuntu installation. Something was not done right during installation. Ubuntu should be in sda7. In my opinion. 

[/COLOR]I didn't intend anything except to get a working ubuntu on the machine. I believe I just followed the instructions and accepted the defaults in the LiLi usb instructions.

Sounds like I need to start by freeing up space in the NTFS partition by removing stuff I don't need. Then - correct me if I'm wrong, please - it sounds like I need the NTFS partition to have roughly 30-40% free space, plus I need a small boot partition and a large (20gb?) partition for ubuntu? Is it safe to remove the existing partitions, other than the NTFS, the hidden system restore partition, and the 10.4 GB boot partition? 

And I should do all of this partition management with the Windows disk tools, then reboot immediately so that Windows can chkdsk, and then install 14.04.4 as dualboot? 

And what about if I wanted to bail out of dualboot on this machine, and do it from scratch on a different machine? Is there a straightforward, reliable path to get this machine back to straight Windows?

Windows Disk Management tool shows (stuff in square brackets is my attempt to map these to what's listed above from the boot repair summary):
9.67 GB: Healthy (Active, Recovery Partition) 100% free [sda1 - ubuntu says this is the boot partitions]
4.01 GB: Healthy (Primary Partition) 100& free [sda5]
514 MB: Healthy (Primary Partition) 100% free [sda6]
10.36 GB: Healthy (Primary Partition) 100% free [sda7]
124.70 GB: Healthy (Boot, Page File, Crash Dump, Primary Partition) 7% free [sda2]

No sign of anything corresponding to sda3

---

### Post by oldfred on 2016-03-09
Windows does not know about nor show Linux partition. 

Boot flag is used by Windows to know which NTFS partition has more boot files, do not confuse with a /boot partition in Linux.
You need to work from live installer to see partitions in Linux style. It also avoids the issue where Windows confused a D:drive. In Windows that can be a second partition on same drive or another partition on a totally different physical drive.
In Linux sda is first drive and sdb second drive, and partitions are numbers like sda1, sda2, and sdb1 etc.

You can you use your Windows repair disk to restore a Windows MBR with fixMBR command. Then you can directly boot Windows. Boot-Repair can only do minor fixes to Windows but restore a Windows type boot loader is one of them.

Normal Linux desktop does not need nor have a separate /boot partition. Server type installs or full drive encryption installs often have or need a separate /boot partition. 
Default install is / (root) or system partition and swap which is used if you run out of RAM. Often that is all that is needed for a new user for first install, but more advanced is a separate /home and/or /mnt/data partitions for data. If dual booting with Windows often a good idea to have a NTFS data partition for shared data, so not writing into Windows system partition.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Before any install or change to partitions always backup all your data.


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 


 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Bob_Voges on 2016-03-09
OK, thanks, everyone. I'm good to go for now. Will update thread when I have something new to report.

---

