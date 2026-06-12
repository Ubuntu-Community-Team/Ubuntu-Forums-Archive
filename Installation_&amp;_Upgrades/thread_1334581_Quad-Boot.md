---
title: "Quad-Boot"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by ShayHP on 2009-11-22
i currently have installed on my desktop computer XP / VISTA / WIN 7
i want to install ubuntu as well.
I'm just afraid about the boot, is there any possibility that installing ubuntu will cause the other OS not to boot?
if so what can be done in that case?

also, what is the try ubuntu option? does it write files to HDD? create partitions? should it work slower than actually installing it?

thanks.:KS

---

### Post by Bunnybugs on 2009-11-22
If you download the ISO-image from the site, and burn it to a disc. You'll find an executable called Wubi.exe (in windows). This installs Ubuntu without partitioning...

It creates a file that Ubuntu sees as Hard Drive!

---

### Post by Bunnybugs on 2009-11-22
> **ShayHP said:**
> i currently have installed on my desktop computer XP / VISTA / WIN 7
i want to install ubuntu as well.
I'm just afraid about the boot, is there any possibility that installing ubuntu will cause the other OS not to boot?
if so what can be done in that case?

also, what is the try ubuntu option? does it write files to HDD? create partitions? should it work slower than actually installing it?

thanks.:KS

Try ubuntu is a live-OS option. it works from the disk, without any changes to your computer...

But, you can't save any files, change directories... You could repartition your PC, but that's not nescecary with the WUBI option, just open the disk in windoze, and run Wubi.exe

---

### Post by audiomick on 2009-11-22
Hallo.
First of all, the "try Ubuntu" option is completely harmless. It  does not write anything anywhere except to RAM. It loads what it needs to run into RAM, and runs from there. This is a good thing to try out, as it should show you if all your hardware will run properly.


As far as booting from all the systems goes, as far as I know, that should not be a problem. The installer should recognise the existing OS installations and include them in Grub2, the boot loader for Ubuntu ) 9.10.

If you try the install and the installer doesn't find the other systems, you can stop anytime up until the last step, which tells you very clearly that it is now going to write to disc, and the process is irreversible.

Apart from that: Trust is good, backups are better...;)

---

### Post by ShayHP on 2009-11-22
ok. thanks for all the help.
just to be clear, the wubi.exe option, it installs just like any other software under windows?
then how do i access ubuntu? from windows? from boot?
and can i also delete it like a regular program without formatting or something?

---

### Post by audiomick on 2009-11-22
As far as I have read, wubi installs an Ubuntu inside windows as if it were a program. It is then accessible only from that windows installation. It can be de-installed like any other program with the windows software management.
I have also read that wubi is intended for trying out Ubuntu, but not neccessarily appropriate for "serious" use.

---

### Post by presence1960 on 2009-11-22
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

Please be aware that wubi is not meant to be used as a permanent installation. It is rather to be used as a test drive to see if you like Ubuntu without partitioning your hard disk. Wubi does have some drawbacks as you will see if you read the links provided.

---

### Post by ShayHP on 2009-11-22
ok, final question,
lets say i partitioned my driver and installed ubuntu on it.
if i want to delete it i will just need to format the partition?
and also i understand it works on its special file system
can i return it to NTFS after deleting?

---

### Post by Bunnybugs on 2009-11-23
> **ShayHP said:**
> ok. thanks for all the help.
just to be clear, the wubi.exe option, it installs just like any other software under windows?
then how do i access ubuntu? from windows? from boot?
and can i also delete it like a regular program without formatting or something?

It's accessed by the boot menu. But, it uses a windows-disk file for a hard drive, not a partition... it doesn't really change your computer, only the boot option 'Ubuntu' is added. If you want to remove Ubuntu, go to the wubi-folder, and press uninstall!

---

### Post by audiomick on 2009-11-23
> **ShayHP said:**
> ok, final question,
lets say i partitioned my driver and installed ubuntu on it.
if i want to delete it i will just need to format the partition?
and also i understand it works on its special file system
can i return it to NTFS after deleting?
Should you chose, after partitioning your drive, and installing Ubuntu ( a "real" install, I mean, not wubi) to remove Ubuntu ( can't imagine why you would want to...;) ) , you can remove it by formatting the partition it is on. You can re-format this partition to NTFS.

You will also have to re-construct the MBR, as far as I know. The linux installation up to version 9.04 installs the boot loader GRUB. 9.10 has changed to GRUB2. This is the thing that lets you choose which OS to boot. As far as I know, when you remove Ubuntu, GRUB goes with it. This is not a problem, as it is no longer necessary when the computer is windows only. To re-construct the MBR, which is what boots windows, there is a windows tool available.

---

### Post by cholericfun on 2009-11-23
two things:

if you properly install Ubuntu on its own partition, it will make a new bootloader, when you wipe ubuntu off that drive then you'll not be able to boot anything until you restored your MBR (Win cd or installing another Linux or other methods... loads of instructions on the web)

another thing:

you need 2 partitions for a proper Linux install, one for the install and one for SWAP, i 'm sure its possible to leave out swap but i'm not sure bout that.
thats a problem because you've got 3 partitions for windows and you can only make 4 primary partitions, you'll need to look at logical partitions here.

before you go about messing around with the HD, i'd take some time and check out the LiveCD (or WUBI) and get a feeling for ubuntu.

---

### Post by Bunnybugs on 2009-11-23
> **cholericfun said:**
> two things:

if you properly install Ubuntu on its own partition, it will make a new bootloader, when you wipe ubuntu off that drive then you'll not be able to boot anything until you restored your MBR (Win cd or installing another Linux or other methods... loads of instructions on the web)

another thing:

you need 2 partitions for a proper Linux install, one for the install and one for SWAP, i 'm sure its possible to leave out swap but i'm not sure bout that.
thats a problem because you've got 3 partitions for windows and you can only make 4 primary partitions, you'll need to look at logical partitions here.

before you go about messing around with the HD, i'd take some time and check out the LiveCD (or WUBI) and get a feeling for ubuntu.

The linux partitioner already auto makes swap memory!

And, if you remove the whole Ubuntu partition, you'll loose GRUB/GRUB2 as well... So don't do that. the prettiest way to install is first linux, then windoze...

Then you'll use the winfoze bootloader;)

---

### Post by ShayHP on 2009-11-23
i see.
well i don't know if i'll remove ubuntu after installing it
but just wanted to know about my other OS boot.

before asking here i installed ubuntu netbook remix on a laptop that had xp, vista and win 7 and they all work in harmony.
that the work computer so i don't mind messing with it,

but i also want to do the same with my desktop computer which is much more important and containt all my data.

so i think i'll give it a try but can you still give me a link to reinstalling the MBR of windows in the easiest way?

---

### Post by presence1960 on 2009-11-23
> **ShayHP said:**
> 

so i think i'll give it a try but can you still give me a link to reinstalling the MBR of windows in the easiest way?

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

if you do not have a Vista installation DVD download a recovery console iso for your version of vista [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it as an image to CD and boot off the CD to access recovery console. Follow instructions from first link.

In the first link you will find instructions for XP & Vista. if you have Windows 7 use instructions for Vista.

---

