---
title: "Help with installing Ubuntu on a comp without any current OS and cd-drive"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by SodR on 2007-02-27
Hi everybody!

I got a laptop with a empty harddrive (no current OS) and no cd-drive on which I would like to install ubuntu. My question is simple; how?

I can without problem take out the harddrive an put it into my desktop comp (I got an adapter) and format it and transfer files if needed.

Maybe two partitions, one for the unpacked ubuntu iso and one for the installation, and some kind of bootdisk will do?

Please help me!

btw. I have already searched for it and found a few solutions but non of them have worked :( Can someone please write som kind of super-easy step by step instruction?

Thanks in advance!

---

### Post by Zimmer on 2007-02-27
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Any of these fit the bill ?

---

### Post by SodR on 2007-02-28
Thanks for your reply, this ([https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)) seems to match my needs. I have a few questions that I can't figure out:

1. What filesystem should the two partitions have? (I'm planing on skipping the TomsRtBt stage and do that from an other comp using partitionmagic or something similar). 

2. Can I just create two partitions and dump the ubuntu iso on the "dummy" one and then boot with the grub boot disk or do I have to mount the iso or something?

3. Where can I get the Grub bootdisk and create one in windows? (I have only found installation guides for linux so far.)

4. And lastly, at the end of the guide it says: "cloakable - this needs updating for using with 6.06 and later. Method fails with Ubuntu 6.06. (And, for some reason, on 5.10 too. Bad grub options?)". So I'll probably need an old version of ubuntu (like 6.05 if that version exists). Where can I get that?

Thanks in advance for all answers!

---

### Post by Zimmer on 2007-02-28
> **SodR said:**
> Thanks for your reply, this ([https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)) seems to match my needs. I have a few questions that I can't figure out:



4. And lastly, at the end of the guide it says: "cloakable - this needs updating for using with 6.06 and later. Method fails with Ubuntu 6.06. (And, for some reason, on 5.10 too. Bad grub options?)". So I'll probably need an old version of ubuntu (like 6.05 if that version exists). Where can I get that?

Thanks in advance for all answers!
Hmm.. yes, I have revisited that and it does not look hopeful. Looks like the guide was done for Hoary, that's the release before Breezy (5.10) .

Nearest thing I can find for GRUB disks via Windows is at Herman's place 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Trawling around for a better way I found this 
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)
as it was linked from this
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)
and these
[http://blog.bergcube.net/post/2007/01/08/Ubuntu-laptop-struggle](http://blog.bergcube.net/post/2007/01/08/Ubuntu-laptop-struggle)

[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)
none of which come with the words 'Easy for beginners' stamped on them :)


Having read them all I am not sure I am the right person to be guiding you through it, though. 
UbuntuGeek is probably the best bet as he has written his own HOW TO on the subject
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

(ps will your BIOS allow booting from an external CD drive of some description...?)

---

### Post by SodR on 2007-02-28
Your last suggestion ([http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)) seems pretty neat. The only real question I have for that guide is this step:
> 4)Now you need to Install grub onto either a floppy or hard drive and create a similar entry in your menu.lst file How do I obtain that floppy/create one?

Thanks again.

---

### Post by SodR on 2007-03-01
Bump. Someone must know?

---

### Post by Bagboy23 on 2007-03-01
I did this on a windows machine once. I had to take out the Laptop HD, put it in a seperate Desktop, Install DOS and the i386 folder from the XP CD to the laptop HD, run DOS and execute the installation. It worked.

Linux, as much as I tried I just couldn't get enough help on any of the methods.

---

### Post by SodR on 2007-03-01
> **Bagboy23 said:**
> I did this on a windows machine once. I had to take out the Laptop HD, put it in a seperate Desktop, Install DOS and the i386 folder from the XP CD to the laptop HD, run DOS and execute the installation. It worked.

Acctually I did that but after the first step in the windows installtions ("copying files to harddrive") the computer needs to reboot and the setup is supposed to automatically contiunue but on my computer it didn't! The setup won't launch :S

---

### Post by Bagboy23 on 2007-03-01
That's what happend to mine too; a clear format and repeat of the process solved it. Additionally, you're suppose to run a command at the DOS prompt so that the installation doesn't take a whole day like my first one did. I forget the command but a search on Google will bring something up.

---

### Post by SodR on 2007-03-01
> **Bagboy23 said:**
> That's what happend to mine too; a clear format and repeat of the process solved it. Additionally, you're suppose to run a command at the DOS prompt so that the installation doesn't take a whole day like my first one did. I forget the command but a search on Google will bring something up.


Regarding the command; do you mean enabling smartdrive (type smartdrv two times)? What do you mean by "clear format", just delete the existing paritions in partitionmagic and create a new or do I need to do some low-level formating or what? Please explain how you did it :)

---

### Post by Bagboy23 on 2007-03-01
Honestly I can't remember. I do understand your frustration though as I was desperate to get my laptop running. As for the comman, I did mean smartdrv command.

Ok, this is what I did when it didn't work the first two tries.

1. Check BIOS to make sure nothing is in the way, e.g. not booting to something else.
2. Format once using windows as a secondary drive, it didn't work. So I installed Windows on that drive to test if the drive was ok. Windows installed fine on my laptop HD, so I did a clean format of that drive. 
3. I then copied the i386 folder and installed DOS.
4. Boot into DOS and into the wininit? folder run the executable.

It did it for me.

Hope this helps.

---

### Post by SodR on 2007-03-01
So you only had one partition on your harddrive (in fat32)? SO you basically did no partitioning just a straight format to fat32 and dump the i386 folder on it and then you started the setup?

---

### Post by Bagboy23 on 2007-03-01
That's correct.

---

### Post by Zimmer on 2007-03-01
Sorry for the delay, but with a lot of searching I came up with this which appears to be a disk image of GRUB in .zip file that you can use to create a GRUB boot disk from Windows.

[http://www.osdev.org/osfaq2/index.php/GRUB](http://www.osdev.org/osfaq2/index.php/GRUB)  
gives a reference to a Sourceforge download page.

[https://sourceforge.net/project/showfiles.php?group_id=10181&package_id=43468&release_id=240806](https://sourceforge.net/project/showfiles.php?group_id=10181&package_id=43468&release_id=240806)

---

### Post by SodR on 2007-03-02
Thanks guys! Now I have succesfully created a GRUB floppy disk that boots alright :) I have connected the harddrive on my laptop to my desktop and now I'm about to create two partitions (one 800mb for the ubuntu iso and one for the installation). I just wonder; what kind of file system should the partitions be in? NTFS? Should it be logical or primary? Can I do it with partitionmagic?

Thanks again!

---

### Post by Zimmer on 2007-03-02
> **SodR said:**
> Thanks guys! Now I have succesfully created a GRUB floppy disk that boots alright :) I have connected the harddrive on my laptop to my desktop and now I'm about to create two partitions (one 800mb for the ubuntu iso and one for the installation). I just wonder; what kind of file system should the partitions be in? NTFS? Should it be logical or primary? Can I do it with partitionmagic?

Thanks again!
Erm,, not NTFS... there are a lot of good guides about for partitioning, but you will need
an EXT2 or ext3 or reiserfs partition for a Linux installation. The partition for the iso image I suppose could be anything, but probably best to go with whatever you choose for the Linux install.. ext3 is probably the safest bet. 

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
for a good read to enlightenment

---

### Post by SodR on 2007-03-02
Crap, my harddrive adapter just broke (I connected it wrong). It looks like my only chanse to pull this off now is to to exactly the way the do it in the tutorial. I'm afraid I still havn't figure out how to install TomsRtBt to a floppy. I have downloaded this ([http://www.ibiblio.org/pub/Linux/system/recovery/tomsrtbt-2.0.103.dos.zip](http://www.ibiblio.org/pub/Linux/system/recovery/tomsrtbt-2.0.103.dos.zip)) but I havn't figured out how to install it. This is what the faq says:

> 
5) DOS installation

a) Pkunzip it

b) If you are running Windows-95, do "shutdown and restart in msdos mode".
   You have to be in really-DOS mode.  Not a DOS session under Windows-95.

c) CD to the directory you pkunzipped it into.

d) "install".
   (This boots a GNU/Linux with prompts to make the diskette.)

This is for installing tomsrtbt from a DOS/Windows system.

If you have problems, boot with no config.sys or autoexec.bat.

Note, this creates the *exact same floppy* as the GNU/Linux installer.



I'm guessing that "Pkunzip" means just "unzip". Regarding stage b, do I really need a computer with windows 95? I tried with using cmd and navigating to the directory and typing "install" which is supposed to start loadlin.exe, but it doesn't (the program also complains about that there is no free ram, which is false). Also, there is no files called config.sys or autoexec.bat included in the package...

The guide says that I need the files usb-uhci, usb-storage and usbcore. The links in the guide doesn't work so do you know where I can get these files?

---

