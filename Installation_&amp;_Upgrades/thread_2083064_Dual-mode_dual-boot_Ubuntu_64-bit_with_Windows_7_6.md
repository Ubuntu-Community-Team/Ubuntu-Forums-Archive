---
title: "Dual-mode dual-boot Ubuntu 64-bit with Windows 7 64-bit without burning a CD"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by xuancong on 2012-11-11
Dual-booting Ubuntu in Win7 is no longer a big problem for many people. Just a bit of googling will give you dozens of solutions. However, to install a single physical copy of Ubuntu (on the same harddisk of currently running Win7) which can run both under Win7 and standalone (I call it dual-mode) is kind of headache for 64-bit windows because of the new restriction on raw disk access from Vista onwards ([http://support.microsoft.com/kb/942448](http://support.microsoft.com/kb/942448)) as well as Windows 7 64-bit forbid loading unsigned kernel driver signature (this can be solved by enabling testsigning in boot config using bcdedit).

I have cracked my head and eventually managed to install Ubuntu 12.04 64-bit on Windows 7 Ultimate 64-bit using VirtualBox 4.2.4 using a Ubuntu ISO image without burning a physical CD. The copy of Ubuntu is installed using VirtualBox but can run not only inside Windows 7's virtualBox but also on its own (restart computer and boot directly into the same copy of Ubuntu). I think this way of installing is very useful because certain big tasks is better to be run directly in Ubuntu but not in virtualbox's ubuntu. However, I am skeptical about the repeatability of my installation procedures, hope other people can have a try and see whether it works as well.

[COLOR="Red"]Warning: DO NOT try this if you are NOT an expert in OS boot principle and harddisk partition, attempting things without understanding what exactly it does may result total loss of your harddisk data and at the same time rendering your system unbootable. [/COLOR]

Here're the required stuffs you need to prepare:
1. VirtualBox 4.2.4
2. EasyBCD 2.2 (in case needed)
3. EaseUS Partition Master (in case needed)
4. Ubuntu CD (12.04 I used)
5. basic knowledge in Command Prompt and Windows disk management
6. in BIOS, enable Intel virtualization technology, otherwise, 64-bit Ubuntu cannot be run in virtual machine

To get started:
1. Make sure you are in administrator mode with UAC disabled, so each operation has admin privilege;

2. run the following command in command prompt to enable test signing mode so that some kernel drivers can be loaded (I'm not sure if it's neccesary)
Bcdedit.exe -set TESTSIGNING ON

3. in "Windows disk management" (by right-click Computer -> Manage -> Storage -> Disk Management), make sure you have 2 empty partitions prepared for Ubuntu, 1 for system (suggest >=8GB), 1 for swap (total memory size). Your current harddisk type must be a basic (not a 'dynamic disk' or a 'GPT disk').
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227003&stc=1&d=1352639716[/IMG]
For example, in the figure above, Drive X is for Ubuntu OS and Y is for swap area (optional but strongly recommended unless you don't need virtual memory in Ubuntu).
Take note that the Ubuntu OS better to be installed on a primary partition, swap can be either on primary or extended partition.


4. The two Ubuntu partitions must be unformatted by Win7, if formatted, delete and recreate; moreover, you MUST assign letters to the two partitions but don't use it in Win7. In addition, all partitions must have be assigned a letter, including the system reserved partition M in my case.

5. Create the disk image. In command prompt, goto virtual box folder,
C:\Program Files\Oracle\VirtualBox in my case, run this:
VBoxManage internalcommands createrawvmdk -filename C:\rawdisk0.vmdk -rawdisk "\\.\PhysicalDrive0" -partitions 0,1,2,3,4,5,6
The image file 'disk0.vmdk' can be put anywhere you want with folder names not containing space. The actual number of partitions "0,1,2,3,4,5,6" depends on your harddisk. There must be no error running this command, if there's an error, delete the possibly wrongly created disk0.vmdk and disk0-pt.vmdk file and change parameters and retry.

6. Create a new virtual machine in VirtualBox, use this C:\disk0.vmdk as the disk and load Ubuntu ISO image into CD-DVD drive as shown below.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227005&stc=1&d=1352640738[/IMG]
Make sure you select Linux -> Ubuntu (64 bit) when creating the VM and have no other warnings in VirtualBox manager on this VM.

7. Launch the created virtual machine, press F12 to boot into Ubuntu CD, perform normal install, make sure you install into the right partition and set correct swap area. For the boot loader I install into the Ubuntu partition, not MBR.

Here comes tricky! I often encounter the problem when either 1. Ubuntu installer cannot find any partition or 2. cannot write into the partition or 3. cannot write boot-loader. If you encounter so, try removing drive letters, reassigning drive letters (trying using only the 2 partitions instead of putting all 0,1,2,3,4,5,6), deleting VM in virtualBox completely and recreating disk0.vmdk and VM. You may even try running EasyBCD 2.2 or EaseUS Partition Master to make raw disk operations doable. That's the part which I suspect to be non-repeatable.

If the boot-loaders fail to install, you can still force to boot into Ubuntu using EasyBCD by adding a new entry and setting the drive to be the Ubuntu partition as shown below:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227010&stc=1&d=1352643512[/IMG]

8. The installation eventually complete successfully and the resultant copy of Ubuntu 64-bit can be run both inside Win7's virtualBox and upon machine reboot.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227009&stc=1&d=1352643512[/IMG]
Unfortunately, you cannot run the same copy of Win7 both on its own or in Linux's virtualBox because too many hardware changes will require another windows activation.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227008&stc=1&d=1352643512[/IMG]
[COLOR="Red"]Warning: do not rebooting into the same copy of Win7 from Win7's virtualBox although you can do so in the boot option above. Doing so may result in file system corruption or rendering operating system unbootable.[/COLOR]

The good thing is that the Ubuntu in virtualBox is able to access windows partitions in read-only mode or full-access if they are unmounted, to unmount a volume E:, run in command prompt:
mountvol E:\ /D

I hope some people may have a try and figure out a better/clearer way of doing so.:P Be very careful throughout, bear in mind that you may blow out your system and data:popcorn:

---

