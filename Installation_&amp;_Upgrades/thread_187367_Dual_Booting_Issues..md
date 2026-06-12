---
title: "Dual Booting Issues."
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by ubuntnoob on 2006-06-02
A little bit of an issue with dapper.  
Correct me if I've got this wrong because I'm just piecing together info from reading these forums.

As far as I know for breezy and dapper development installs GRUB was installed on the ext3 ubuntu partition. (and still is with the alternate install cd)

But using the new desktop install (live) cd GRUB is installed on hda1, even if windows is there.

Therefore, if you want to uninstall ubuntu you can no longer just delete the partition and fixmbr then go back to windows.  If I am understanding this right, if you try to repair the mbr this way it won't recognize your windows anymore because the GRUB data is "in the way" now.

Am I totally off here? let me know.  But I clearly remember my very first breezy (and linux) installation froze halfway through and I just rebooted to windows, deleted the partition, reburned the cd and tried again.  This time after the live installer failed I couldn't boot to XP and even fixmbr and fixboot had no effect.

Thoughts???

---

### Post by Tweek84 on 2006-06-02
Both my breezy and dapper installations have always given me the option for where to install the bootloader, defaulting to hda1's MBR.

Eitherway, if grub is loaded onto hda1 and that is where the windows partition is you should be fine. If you want to uninstall you can still use fixmbr off the windows recovery console. It should re-write the mbr with a windows standard one and allow you to reboot.

---

### Post by Herman on 2006-06-02
Actually, hda1 does not include the hard disk's MBR at all, every install I've ever seen has the first 63 sectors empty, it's not part of any filesystem.

To prove it, when you have a Linux install, try this following code: ```
sudo fdisk -lu
```hda1 does not start untli sector 63. The MBR is in sector no.1, a long way from the beginning of whatever filesystem happens to be on the first partition.

The first partition will have its own boot block where another IPL for another boot loader can be installed if it's another Linux. If it's Windows, I suppose it would be Windows bootloader's IPL.
Not much has changed.

The thing that has upset a few people is that there used to be a choice offered about where you want GRUB's IPL installed. Apparently you need to use the 'alternate' install CD if you still want that to have that choice.

---

### Post by Herman on 2006-06-02
If you want, you can make a backup of your MBR with this command in Ubuntu: ```
sudo dd if=/dev/hda of=/home/ubuntunoob/MBR.image bs=446 count=1
``` You could restore it with:```
sudo dd if=/home/ubuntunoob/MBR.image of=/dev/hda bs=446 count=1
``` 
If you want a backup of the boot block of hda1 (for some reason) you would use:```
sudo dd if=/dev/hda1 of=/home/ubuntunoob/BBL.image bs=512 count=1
```and you could restore it later by reversing the command. (Not that the boot block of hda1 will be distrurbed, mind you.)

If you want to see what your MBR looks like, try this:
```
sudo dd if=/dev/hda count=1|hexdump -C
``` To see your Windows boot block, (presuming Windows is in hda1 partition) try this one:
```
sudo dd if=/dev/hda1 count=1|hexdump -C
``` I don't know if this will do anyone any good as it is except to demonstrate the difference between the MBR and Windows boot block. Shorty I will do a big re-install in my own computer and run a set of Windows XP recovery disks before installing Dapper from scratch a few times. I'll experimaent to see hwo to copy my Windows Boot sector to somewhere with a 'dd' command from a Ubuntu LiveCD, just for fun. Have fun, Regards, Herman :D

---

### Post by Herman on 2006-06-03
Here's how to make a back-up of your original Windows MBR to a USB drive in case it helps anyone:
Back Up Windows MBR with Dapper ubuntu-6.06-desktop-i386.iso CD before installation begins.

1) Plug in USB disk or check to see that it is already plugged in.

2) Boot ubuntu-6.06-desktop-i386.iso

3) Choose Start or Install Ubuntu

4) After boot-up, USB disk icon(s) should appear on the desktop.

5) Open a terminal (Applications, Accessories, Terminal)

6) ```
sudo dd if=/dev/hda of=/home/ubuntu/WINMBR.img bs=446 count=1

``` 7) > 1+0 records in
   1+0 records out
   446 bytes copied,  4.3e-05 seconds, 10.4 MB/s 
8.) Open /home/ubuntu directory, locate file named WINMBR.img

9) Open USB drive (FAT32 partition), drag and drop WINMBR.img there somewhere.

10) Carry on with Ubuntu Install.

I hope that helps some people to install with more confidence. This way it won't matter if you install GRUB to MBR if that's what a few people are concerned about. 

How are you doing with your install now, ubuntnoob?  Anything I can help you with? 
:D Regards, Herman

---

### Post by ubuntnoob on 2006-06-03
Ok,  but why do you suppose that Windows could no longer boot after the failed dapper install attempt?

on boot i got "Error loading operating system"  and even using fixmbr from my XP disk did not fix it.  

Because I used the largest continuous free space option my XP install shouldn't have been touched?

---

### Post by cartur25 on 2006-06-03
I also suffered a failed installation. Now I when I try to boot without the cd I get a:

"Error loading operating system"

Is there a way that I can get windows to load?

Additionally, I have a few files that I want to save on my internal HD - just some pictures - but when I try to access them in linux it says that "I do not have permission to view the contents of the drive"

so...

1. Is there a way to boot windows after a failed linux installation
2. Is there a way to grant permission to browse a drive and transfer files

Many Thanks
-Caesar

---

### Post by Herman on 2006-06-03
> Ok, but why do you suppose that Windows could no longer boot after the failed dapper install attempt?on boot i got "Error loading operating system" and even using fixmbr from my XP disk did not fix it. Because I used the largest continuous free space option my XP install shouldn't have been touched?It really could be any number of possible problems. To begin solving the problem some information is needed.
Either by running the ubuntu-6.06-desktop-i386.iso as a Live CD, or by using your Ubuntu system if it is bootable, you can find out the information required by opening up a terminal and entering the following command:
```
sudo fdisk -lu
``` (You can just copy and paste it off this web-page into your terminal if you like). The output of that command can tell someone a lot of information about what might be wrong.
Another thing to see would be a copy of the bottom part of your /boot/grub/menu.lst file.
```
sudo gedit /boot/grub/menu.lst
``` It might look something like this [*Click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#os_entries").
If you can copy some of that to a post here in this forum someone might be able to help, but nothing is guaranteed. You might still have to re-install, but someone can try to help. I will if I'm available. At least it would be nide to know what happended.
Regards, Herman

---

### Post by gadgetgirl on 2006-06-03
I had a similar problem with "Error loading operating system." After a lot of frustration and looking, it seems that the bootable flag was turned off on all my partitions. I booted into the live mode of the dvd and used fdisk to toggle the partition's bootable flag on.

My intention was to dual boot xp and ubuntu, using existing partitions (already had xp and breezy working before) on a Thinkpad T43 laptop (I mention the model, because there is another "recovery" partition to deal with on the drive).  I installed Dapper using the text mode install to have it put grub only in the linux partition, but it still borked the MBR grr. After using the xp cd to "fixmbr" the mbr, and using the Dapper live mode's fdisk to toggle the boot flag, everything is working now. It still sucks that the install went so poorly for me though, since Breezy installed so much more easily.

---

### Post by Herman on 2006-06-03
cartur25,
> Is there a way that I can get windows to load?  You should try making yourself  [GAG Boot Manager]("http://gag.sourceforge.net/") floppy disk or CD-ROM. That's the easiest thing to try first, and if that doesn't work then we know something else is probably wrong other than GRUB.
For help fixing grub if that's your only probelm, it's vital to see your sudo fdisk -lu output and bottom of your menu.lst as explained in another post above here. (The last five or more operating system entries). (Please).:D
Here are more detailed instructions for GAG Boot Manager and Ubuntu, *[click here]("http://users.bigpond.net.au/hermanzone/p12.htm").*> Additionally, I have a few files that I want to save on my internal HD - just some pictures - but when I try to access them in linux it says that "I do not have permission to view the contents of the drive"Oh dear, you should have backed up all your files first. You knew I'd say that right? Okay, you should be easily able to open a file called /etc/fstab, and edit some lines in that to give yourself permission to access your Windows files. [*Click here*]("http://users.bigpond.net.au/hermanzone/p10.htm#1p10").if your Windows files are FAT32 filetype. If not, just look in your help menu under 'System', Help, 'System Documentation', and then go; 'Ubuntu Desktop Guide', Configuring your System,'Partitions and Booting'.
There you will find section 4.2.3 'Make Windows automatically available' and there are instructions that apply to NTFS filesystems.
I hope I have been some help to you, aks again if you want more, Ceasar, Regards Herman

---

### Post by Herman on 2006-06-03
gadgetgirl, I'm sorry your install was a hassle, but I'm glad you got it working now. 
> I had a similar problem with "Error loading operating system." After a lot of frustration and looking, it seems that the bootable flag was turned off on all my partitions. I booted into the live mode of the dvd and used fdisk to toggle the partition's bootable flag on. Thanks for sharing how you fixed it, that's very interesting, the bootable flag was never an issue before, I always thought it wasn't important at all. If that fixes that's the important thing. Good work 99!
Did you really mean fdisk? Or do you mean just a partitioner? I didn't know many people still use fdisk these days.> I installed Dapper using the text mode install to have it put grub only in the linux partition, but it still borked the MBR grr. Maybe you just had bad luck, I'm experimenting right now with the new text mode install and I have formatted and re-installed four or five times already just to learn the best ways to use it. It is working okay for me so far. I did notice one thing odd; I always install with the internet plugged in normally, but I got a bad video resolution every time. Last time I tries without the internet plugged in, and got a good resolution. What do those two things have to do with one another?](*,)
By the way, if you really do use fdisk (which is okay if you prefer it) did you know it can make the partitions start and finish on other than the cylinder boundaries, which might not be compatible with GRUB or Ubuntu? That might have been the cause of your MBR trouble, but I can't say for sure. It happened to me once too, that's how I (think I) know.
Anyhow, thanks for sharing! And happy Ubuntuing,  :D Herman

---

### Post by gadgetgirl on 2006-06-05
Yup, I used fdisk. All I know is that my partitions worked great with a Breezy install, and one install of Dapper blew it up with the "no operated system" error. I started investigating with qparted, but there was nothing I could do with that tool to fix the problem. Fdisk seemed to be my only choice. I also confirmed that flipping the bootable flag on and off fixes and breaks the bootability of the machine respectively, and moving that flag to different partitions causes those partitions to boot first.

---

