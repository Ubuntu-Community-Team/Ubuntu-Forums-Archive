---
title: "Better Dual booting windows and ubuntu?"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by yilin on 2008-11-07
I found an instruction for dual booting windows and debian here:
[http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm)

I tried and it worked very well.
The nice part is that if debian installation has problems, it will not affect windows and vice versa.

I cannot figure out how to make windows/ubuntu dual booting the same way. seems ubuntu will write to mbr anyway. So far, this bothers me to use ubuntu on my laptop.

---

### Post by caljohnsmith on 2008-11-07
That tutorial you linked to gives instructions for using "bootpart" to install the Grub boot sector into the Windows boot loader, but it also gives instructions for using Grub in the MBR. So which method are you referring to? If you mean the bootpart method, you can still do that with Ubuntu. Personally, I prefer to use Grub4DOS rather than the Windows boot loader and bootpart, because you can configure Grub4DOS for only one boot screen on start up that displays all your OS/kernel choices, whereas using bootpart with the Windows boot loader means you have to go through two screens to reach your Ubuntu boot menu. If you don't mind that, then by all means you can use bootpart with Ubuntu.

If you decide to use bootpart with Ubuntu, when you install Ubuntu, just click the "advanced" button at the end of the installation setup, and then specify the Ubuntu partition /dev/sdaX to install Grub to (for example /dev/sda5), rather than (hd0) or /dev/sda which would be the MBR. Then you can run bootpart to copy the Grub boot sector and use it with the Windows boot loader. That's the general idea, but if you would like more specifics, let me know.

---

### Post by cariboo on 2008-11-07
Using the default bootloader works for most people without problems, it is when you try to work around the defaults that things go wrong. In your case does it really make any difference which bootloader is in the mbr? both windows bootloader and grub are pretty simple to restore if there are any problems.

Jim

---

### Post by yilin on 2008-11-08
> **caljohnsmith said:**
> you can still do that with Ubuntu. Personally, I prefer to use Grub4DOS rather than the Windows boot loader and bootpart, because you can configure Grub4DOS for only one boot screen on start up that displays all your OS/kernel choices, whereas using bootpart with the Windows boot loader means you have to go through two screens to reach your Ubuntu boot menu. If you don't mind that, then by all means you can use bootpart with Ubuntu.

Thanks a lot caljohnsmith for your reply.

I'm trying to avoid change MBR. I tried suse years ago, when use ghost to backup the win&susu, it turns out that Lilo cannot boot correctly on the retrieved system. Even I deleted the linux partitions, the system still cannot boot to windows.

I hope ntldr+bootpart can help with my system backup goal.

If I find a system backup util that can do win and linux at the same time (without data backup, which i want to do deparately), I'll not care much about the way of dual booting.

Anyway, I tried from my guess as what you suggested (maybe sth wrong):

I have the following partitions (get into windows, use partition magic)

0: NTFS (win2k)  primary   // Win OS and easily infected things
1: ext3 (/boot)  primary   // Linux boot partition
2: extended      primary   // Wrap of many logical partitions
_      NTFS (FStore)        // Shared file store for both systems
_      NTFS (Workspace)     // Windows userhome, software, data
_      ext3 (/)             // Linux root
_      ext3 (/home)         // Linux user data + things to keep
_      swap
3: unused space             //For windows system backup util

During the ubuntu installing, I noticed my /boot partition marked as sda3 (don't understand why 3), so I choosed sda3 in the advanced option. Everything looks ok and the system installation is over.
When reboot, it directly goes to windows as expected. I did

C:\bootpart>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 44ad79dd
 0 : C:* type=7  (HPFS/NTFS), size= 8195008 KB, Lba Pos=63
 1 : C:  type=f  (Win95 XInt 13 extended), size= 65174729 KB, Lba Pos=16662302
 2 : C:  type=7   (HPFS/NTFS), size= 22354888 KB, Lba Pos=16662303
 3 : C:  type=5   (Extended), size= 10206000 KB, Lba Pos=61372080
 4 : C:  type=7    (HPFS/NTFS), size= 10205968 KB, Lba Pos=61372143
 5 : C:  type=5    (Extended), size= 12753720 KB, Lba Pos=81784080
 6 : C:  type=83     (Linux native), size= 12753688 KB, Lba Pos=81784143
 7 : C:  type=5     (Extended), size= 18007920 KB, Lba Pos=107291520
 8 : C:  type=83      (Linux native), size= 18007888 KB, Lba Pos=107291583
 9 : C:  type=5      (Extended), size= 1852200 KB, Lba Pos=143307360
10 : C:  type=82       (Linux swap), size= 1852168 KB, Lba Pos=143307423
11 : C:  type=83  (Linux native), size= 136080 KB, Lba Pos=16390080

It looks like my sda3 becomes 11 (very confusing!). And I did
c:\bootpart>bootpart 11 ubuntu.bin Ubuntu
.......
C:\bootpart\ubuntu.bin written
C:\BOOT.INI updated

Then I reboot: cannot boot to ubuntu (file not found)

One thing can be wrong is that my /boot partition is not set to active. After I tried boot to other partition with all falures,
I think that I have only one posibility. I'll try to make /boot active then

---

### Post by caljohnsmith on 2008-11-08
I understand that you may be hesitant to change the MBR, but if you have a Windows Install CD, or if you download the [Super Grub Disk]("http://www.supergrubdisk.org"), then restoring your Windows MBR at any point is a snap. I agree with Jim (cariboo907) that it would be much simpler if you just let Grub install to the MBR, and if you want your Windows MBR back at some point for some reason, just whip out your Super Grub Disk and Voila, in just a few minutes you have your Windows MBR back. I really don't think it is worth the effort to use bootpart, because at least in my opinion, Grub4DOS is a much more robust solution that will accomplish the same thing.

Thousands of Ubuntu users in these forums use the standard dual boot setup where Grub is in the MBR, and it's not a problem. Also, I would not recommend changing the boot flag from the Windows partition to the Ubuntu /boot partition, because then the Windows MBR will just try to boot the /boot partition; that won't work unless you have Grub installed to the boot sector of the /boot partition. That is one way though that you could keep your Windows MBR and boot Grub; install Grub to the boot sector of the /boot partition and then set the /boot partition's boot flag, while disabling the boot flag on the Windows partition. I can help you do that if you want, but it makes more sense I think to just install Grub to the MBR. It's up to you. :)

---

### Post by Mahogan on 2008-12-07
**_caljohnsmith_**

Can you help me with a very similar problem, just the reverse that you mentioned in this post.  I have a Compaq laptop that I used the old version of Super Grub Disk to use as a boot loader when I power on the computer it gives me a screen to choose Ubuntu from a USB mobile drive.  I am wanting to remove this and go back to the Windows XP boot.  I am a total newbie and don't have a clue.  Just to give you more history, I have been using Ubuntu 7.04 on the mobile drive and tried to upgrade to the newest, but ran into problems downloading the files and kinda messed up my mobile drive when it loads 7.04 it will stall for a long time, then give me an error message. So I decided to download the newest 8.10 and try that, but it did not work either.  So then I saw that I can install 8.10 directly into Windows like a program, so I did this on my laptop drive (not the mobile).  I like this install and am happy with it.  But now, when I start the computer, I still have that original menu mentioned earlier, and when not booting to the mobile drive, and choosing the Windows boot option, it will go to another screen where it gives me the option to boot to Windows or Ubuntu, with the new Virtual 8.10 installation.  So I am fine with the second screen, but would like to remove the first, original boot option screen.  Since I did not install using the Automatic Super Grub Disk, will I need to uninstall this original boot screen manually?  Or will I mess up my computer by attempting to remove this?  It is more of an inconvience than anything, if it is super difficult, I could live with it, but if it is really easy, I wouldn't mind removing that.  I still want to use Ubuntu 8.10 via my Windows install, just not the mobile option.  Thanks ~Mahogan

---

### Post by caljohnsmith on 2008-12-07
> **Mahogan said:**
> **_caljohnsmith_**

Can you help me with a very similar problem, just the reverse that you mentioned in this post.  I have a Compaq laptop that I used the old version of Super Grub Disk to use as a boot loader when I power on the computer it gives me a screen to choose Ubuntu from a USB mobile drive.  I am wanting to remove this and go back to the Windows XP boot.  I am a total newbie and don't have a clue.  Just to give you more history, I have been using Ubuntu 7.04 on the mobile drive and tried to upgrade to the newest, but ran into problems downloading the files and kinda messed up my mobile drive when it loads 7.04 it will stall for a long time, then give me an error message. So I decided to download the newest 8.10 and try that, but it did not work either.  So then I saw that I can install 8.10 directly into Windows like a program, so I did this on my laptop drive (not the mobile).  I like this install and am happy with it.  But now, when I start the computer, I still have that original menu mentioned earlier, and when not booting to the mobile drive, and choosing the Windows boot option, it will go to another screen where it gives me the option to boot to Windows or Ubuntu, with the new Virtual 8.10 installation.  So I am fine with the second screen, but would like to remove the first, original boot option screen.  Since I did not install using the Automatic Super Grub Disk, will I need to uninstall this original boot screen manually?  Or will I mess up my computer by attempting to remove this?  It is more of an inconvience than anything, if it is super difficult, I could live with it, but if it is really easy, I wouldn't mind removing that.  I still want to use Ubuntu 8.10 via my Windows install, just not the mobile option.  Thanks ~Mahogan
OK, if you have a Windows Install CD, if you boot that up and go to the "recovery console", just run:
```
fixmbr
```
And that should restore the Windows MBR so that you will just get the Windows boot menu, i.e. the "second" screen you mentioned. But if you would like me to check your setup first to make sure that will work OK, then go ahead and boot your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
Note that "-l" is a lowercase L, not a one.

---

### Post by Mahogan on 2008-12-07
Thanks for your reply.  Here are the results:

sudo fdisk -lu
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   218495169   108792148+   7  HPFS/NTFS
/dev/sda2       218600425   234447544     8418060    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     1957887      978928    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 64, 32) logical=(941, 18, 32)
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda
eb48
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
01ff
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-07
OK, that definitely makes it clearer; now that I know what your setup is, to save you the hassle of booting a Windows Install CD (which you may or may not have), you can instead install a Windows equivalent MBR from your Live CD by doing: 
```
sudo lilo -M  /dev/sda mbr
```
Reboot, and hopefully you should be all set. Let me know how it goes. :)

---

### Post by Mahogan on 2008-12-07
That worked Great!  You made it so easy!  Thank you so much!

---

### Post by caljohnsmith on 2008-12-08
You're welcome, I'm glad the solution to your problem turned out to be easy. Cheers and have fun with your OSes. :)

---

