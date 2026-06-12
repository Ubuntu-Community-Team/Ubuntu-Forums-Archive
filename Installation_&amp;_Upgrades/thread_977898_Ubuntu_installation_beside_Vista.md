---
title: "Ubuntu installation beside Vista"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by leopavel on 2008-11-10
Hello guys,

Recently, I got interested to install Ubuntu beside my Vista Home Premium OS. I downloaded the 8.10, burn the iso in a cd. It shows some demo version, complete installation to the HD and so on. So I just installed completely by doing the HD partition following the instruction in order to keep both vista and ubuntu. Now After installation it tells me to take out the cd from the drive to reboot to Ubuntu. Alas !while rebooting it doesn't show any OS named UBUNTU, only vista! I booted to Vista to check the partition which doesn't show the space which I dedicated for Ubuntu. It means partition has been done but why there is no option to boot to Ubuntu? Can you guys help me? As I cannot see the Ubuntu space from the Vista, am I going to loose that space forever?

I tried to install Ubuntu again, but while partition things shows up, it doesn't show the earlier space I dedicated for Ubuntu, instead it tries to acquire space from the vista partition!!

Please help.

Thanks

Leo

---

### Post by Pumalite on 2008-11-10
Boot your Ubuntu Live CD; get to the Desktop. Go to Applications>Accessories>Terminal and type:
sudo fdisk -lu ('Enter')
Copy and paste the output here.

---

### Post by leopavel on 2008-11-10
Hi,

As you say,

This is the output:-

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_rooHere
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -press the backpress the backuyo as lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05eff46b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   235625354   117812646    7  HPFS/NTFS
/dev/sda2       298840064   312578047     6868992    7  HPFS/NTFS
/dev/sda3       235625355   298825064    31599855    5  Extended
/dev/sda5       235625418   296142209    30258396   83  Linux
/dev/sda6       296142273   298825064     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05eff46b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   235625354   117812646    7  HPFS/NTFS
/dev/sda2       298840064   312578047     6868992    7  HPFS/NTFS
/dev/sda3       235625355   298825064    31599855    5  Extended
/dev/sda5       235625418   296142209    30258396   83  Linux
/dev/sda6       296142273   298825064     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 


Also interesting, I can see from the file browser that 31 GB Media drive which was the partition I dedicated for Ubuntu.

Thanks and please advice the next step

Leopavel

---

### Post by Pumalite on 2008-11-10
Do this in the Terminal:
sudo mkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
cat /media/sda5/boot/grub/menu.lst
Copy and paste the output here.

---

### Post by leopavel on 2008-11-10
Hello,

I tried from the terminal, says no file exist. I guess I was in wrong directory. To better understand please look at the screen shots, where the folder structures are there. I have one File System drive, Local Disk (I guess C: NTFS drive), HP_RECOVERY (my NTFS d: drive) and the last 31.0 GB Media drive. 

Thanks

Leo

---

### Post by Pumalite on 2008-11-10
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Pumalite on 2008-11-10
Or do this:
sudo grub
find /boot/grub/stage1
And let me know

---

### Post by caljohnsmith on 2008-11-10
Leo, from that screen shot you posted, it appears your Ubuntu partition does not have Grub (Ubuntu's boot loader) installed. Probably your best bet is to reinstall Ubuntu, use the "manual" partitioning option, select your sda5 partition and give it a mount point of "/", and then set your sda6 swap partition to have a mount point of swap. Then do not change the Grub settings in the "advanced" button at the end of the installation, and Grub should be installed correctly. How about trying that and letting us know how it goes. :)

---

### Post by leopavel on 2008-11-10
Hi,

The second line command outputs this:

      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 

I guess, grub is corrupted. Do you think I have to reinstall Ubuntu?
In that case, how can I install in the existing 31 GB partition?

thanks

---

### Post by leopavel on 2008-11-11
Hello Guys,

As Caljohnsmith says, I did the same and now my Ubuntu boot came back. I can now see my fresh desktop. I must thank to Pumalite and Caljohnsmith.

Thanks for your time and help.

Leo

---

