---
title: "Grub cannot boot partition"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Icarium on 2008-07-10
I recently installed Ubuntu (recently being about an hour ago) on one of my three drives. The first one is split in two, one running NTFS with a corrupt version of Windows XP, and the other one FAT 32 and basically serving as my Program Files folder (these are C: and F:). The second drive (E:) also runs NTFS and contains files I cannot lose. However, I was able to mount this using a live CD, and confirmed that they are still there. The third drive (D:) was where I installed Ubuntu, and where I had my backup in case I lost access to C: or E:.

Rebooting the computer after the installation, I get the following message:
Grub loading, please wait
Error 17

I have done my homework this time, and after some time searching, I found a possible solution, some Super Grub Disk. I downloaded it and tried to run either of the three choices of Ubuntu it displayed - to no avail. Same Error 17. Running Windows, I got to the acer recovery, where it offered to reset the drive to factory condition. If it hadn't been for the fact that I fear for my backup, I'd try that. But until that's secured, I would rather not format any drives (bar D:, the third of the lot)

There is also the problem that where the live CD would recognize the 4 partitions as they were in Windows, it now only finds E:. Since it seems that it wiped D:, and thus my backup, I need to get back into the old C: to retrieve my Thunderbird profiles once again.

Could anybody lend a helping hand in either or both of these matters? All help would be greatly appreciated.

---

### Post by Pumalite on 2008-07-10
Boot your Live CD and post:
sudo fdisk -lu
This is good reading:
[http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard](http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard)
You might have a mix of SATA and IDE

---

### Post by franklinjohn1985 on 2008-07-10
hi folks im also have this kind of problem.
have Ubuntu 7.10 live cd and upgrade to 8.04 through web.
i had reinstalled my windows. while restarting my system i cant log onto linux. Grub is loaded and show options, while choosing the linux menu it shows Error 17 message........
pls solve my problem:?:.
thanks in advance:

---

### Post by Pumalite on 2008-07-10
Read post # 2

---

### Post by Icarium on 2008-07-10
Here is the fdisk -lu

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde3a5702

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   612992204   306496071   83  Linux
/dev/sda2       612992205   625137344     6072570    5  Extended
/dev/sda5       612992268   625137344     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e3ecb49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   625137344   312560640    f  W95 Ext'd (LBA)
/dev/sdb5           16128   625137344   312560608+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e3ecb45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   612992204   306496071   83  Linux
/dev/sdc2       612992205   625137344     6072570    5  Extended
/dev/sdc5       612992268   625137344     6072538+  82  Linux swap / Solaris

But I doubt that the problem is due to different harddrives - they should all be identical.

---

### Post by Pumalite on 2008-07-10
Let's see:
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
Post:
cat /media/sda1/boot/grub/menu.lst

---

### Post by Icarium on 2008-07-10
> ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount -t ext3 dev/sda1 /media/sda1
mount: special device dev/sda1 does not exist
ubuntu@ubuntu:~$ cat /media/sda1/boot/grub/menu.lst
cat: /media/sda1/boot/grub/menu.lst: No such file or directory


Did I mistype anything, or is something else causing it?

---

### Post by Pumalite on 2008-07-10
sudo mount -t ext3 /dev/sda1 /media/sda1

---

### Post by Icarium on 2008-07-10
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Pumalite on 2008-07-10
Post a screenshot of Partition Editor.

---

### Post by Icarium on 2008-07-10
Is there any way to show all drives at once in it? Took individual screenshots for the time being, tho

---

### Post by matthewbpt on 2008-07-10
wait so which partition is ubuntu installed on, sda2 or sdc2?
I had this problem before when i first installed ubuntu, same error 17 and everything, i had to edit the grub menu because it was specifying the wrong disks, it said ubuntu was installed on hd0 instead of where it was really installed on, hd1. My vista partition was on hd0. when you're in grub, press 'e' over ubuntu and change the location to another, try different ones, hd1 hd2 or hd3 etc until one of them boots into ubuntu. this only changes it temporarily so once you boot in you have to edit th grub menu to whatever one worked and also set the other ones to their actual values, this will change it permenantly. it sounds more complicated than it actually is its actually quite easy, but i dont have my ubuntu box with me now for reference to give you more details since im at work.

if you manage to boot into your ubuntu by temporarily changing the boot location show us the contents of the grub boot list

edit: i re-read your post, it seems that you have quite a few partitions, and that ubuntu is right at the end in sdc, grub uses a different way to name the partitions, hdX, the number after hd (ie X) indicates the partition number and it starts from 0 (so the first partition is hd0) , so your ubuntu is installed in something like hd4 or something

---

### Post by Icarium on 2008-07-10
Thanks, matthew, that did the trick. However, I'm stuck as to how I change it in the permanent Grub menu. I think I know how to pull it up through one of the commands given earlier, but as said, I'm stumped as to editing it.

---

### Post by matthewbpt on 2008-07-10
type this in the terminal:

sudo gedit /boot/grub/menu.lst

then after editing it i think you have to type in the terminal:

sudo update grub

I suggest you search on google a bit about editing the grub list before doing this as i cant be sure im exactly right about the steps

I just realized i made a big mistake in my post its not hdX, its (hdx,y) i believe where x is the drive its on, and y is the partition on that drive. so for example the first partition on the second drive would be (hd1,0)

---

### Post by Icarium on 2008-07-10
I edited and clicked save. Tried the update command, but it returned with a message that it didn't recognize the command "update". I figured it was fine, and rebooted... Still Error 17. However, at least now it recognizes that Ubuntu is on hd1 rather than hd2, so it did save without updating. The rest might be caused by the defective WinXP, so I'll go use recovery now. I'll post what happens thereafter tomorrow

Edit:
Nevermind that. I tried to run recovery, but it just told me it couldn't find the drive. Which means I'm left with only 1 operable drive out of 3...

---

### Post by forger on 2008-07-10
It's
> sudo update-grub

If it doesn't do the trick, clear the grub and re-create it:
> sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub

---

### Post by matthewbpt on 2008-07-10
I hope you arent reinstalling your xp as this will delete your grub entirely...

---

### Post by Icarium on 2008-07-10
> **matthewbpt said:**
> I hope you arent reinstalling your xp...

That would be the plan as soon as possible, as I'd like to get back access to all of my hard drives. However, since the recovery isn't running, that's not an option as of yet... Is there any way to prevent Grub from disappearing if/when I reinstall XP?

Edit:
I tried the update as forger put it, and I got an effect this time, as the terminal began running text. However, still get Error 17 upon normal boot.

---

### Post by forger on 2008-07-10
"17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."


I found some possible solutions:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
[http://ubuntuforums.org/showthread.php?t=442945#9](http://ubuntuforums.org/showthread.php?t=442945#9)
[http://forums.gentoo.org/viewtopic-p-750101.html?sid=08708d3b05da9a12673f9742fab0a111#750101](http://forums.gentoo.org/viewtopic-p-750101.html?sid=08708d3b05da9a12673f9742fab0a111#750101)

---

### Post by Icarium on 2008-07-11
I tried the first and last of them so far, and here's what I got:

The last gave me an error message in terminal, saying there was no setup line (I couldn't find it either) reboot gave Error 17.

I tried to find the drives in my BIOS, but all I could find was the boot order. Changed this around to have hd1 boot first (Linux) which caused this error during boot:

BOOT FROM DISK FAILED, INSERT SYSTEM DISK AND PRESS ENTER

Also, I have another problem. While tinkering to fix hd0, where the faulty Windows is (was), I managed to wipe the whole thing in GParted. Thus, I now technically only have one OS.

Is there a way to partition without removing everything on the drive? During installation of Ubuntu, I couldn't get the partitioning right the way it wanted it, so I just set it to do the partitioning itself, which resulted in Ubuntu hogging an entire 320GB drive to install itself on 5-6BG of it... Can I filter out that part without having to reinstall the entire OS?

Edit: For the record, inserting a system disk (Ubuntu Live) when the PC asks for it has absolutely no effect

---

