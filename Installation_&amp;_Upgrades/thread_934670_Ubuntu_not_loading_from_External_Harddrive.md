---
title: "Ubuntu not loading from External Harddrive"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by lamagy on 2008-09-30
hi all, im a noob to linux world.

I Installed ubuntu 8.04 on my external usb hd and i have xp on the main hd.

bios has been updated to boot from external hd first but when i restart it goes straight into xp.

i did a sudo grub on stage1 and i get (hd2,5) which is the linux partition on the external drive.

the only thing i can think of is the bootloader upon the installing selection screen i chose /dev/sdc which is the external drive, should i have chosen '/dev/sdc5' ??

is the bootloader the same as grub?
is this whats causing the problem or ubuntu cannot load unless its on the main partition? is this the problem?

pls help, i've been trying for days.

---

### Post by mikewhatever on 2008-09-30
Can you post the outputs of the following:
> sudo fdisk -l
cat /boot/grub/device.map
cat /boot/grub/menu.lst

---

### Post by lamagy on 2008-10-01
here are the fdisk -l details, i couldn't action the cat command, not sure why but nothing would happen

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 17.2 GB, 17245863936 bytes
240 heads, 63 sectors/track, 2227 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x220aa2b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2226    16828528+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa431a431

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13e8ac0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       45553   365904441    7  HPFS/NTFS
/dev/sdc2           45554       60801   122479560    5  Extended
/dev/sdc5   *       52648       60801    65496973+   7  HPFS/NTFS
/dev/sdc6           45554       52471    55568772   83  Linux
/dev/sdc7           52472       52647     1413688+  82  Linux swap / Solaris

Partition table entries are not in disk order

i did a find /boot/grub/device.map & menu.lst and their both show up at (h2,5)

---

### Post by louieb on 2008-10-01
> the only thing i can think of is the bootloader upon the installing selection screen i chose /dev/sdc which is the external drive, should i have chosen '/dev/sdc5' ??

is the bootloader the same as grub?
is this whats causing the problem or ubuntu cannot load unless its on the main partition? is this the problem?
GRUB is the boot loader used by Ubuntu.

/dev/sdc should have worked. But sometimes it fails so here is another way. 

After you get to the GRUB> set up the mbr of the external drive to boot grub.  

from what you described this should work: at the grub> prompt
```
root (hd2,5)
```then
```
setup (hd2)
```that will setup the mbr of your external drive to load GRUB.

---

### Post by lamagy on 2008-10-01
thanks for that, let me understand it abit better, as im new to linux commands.

so at the terminal i type 
sudo grub

[I]then that should make the promt 'grub>' correct?

then:
grub> root (hd2,5) (enter)

then

grub> setup (hd2)(enter)[/I]

is this the idea? pls remember that im using the live cd to run ubuntu and then get to the command screen.

---

### Post by louieb on 2008-10-02
That is correct.  I assumed you were using the live CD when you posted that you found  /boot/grub/menu.lst  on (hd2,5) using the grub> prompt.

You should get a success message after you run the setup command.

Good luck.

---

### Post by lamagy on 2008-10-02
URGENCY...PLLLLLssss

i did the above, when i type in the root command and press enter nothing happens get another grub promt, then i type the setup (hd2) command and i get the message about stage1/stage2 and then success..

then i restarted and got a blank screen with  'GRUB_' at the top.

i dont know what i did after a couple of the mount commands or something like that, to no avail...then i loaded up to xp and the main partition sdc1 on the ext HD is corrupt, well when i try to access it in xp it tells me if i want to format the disk.

pls help how do i restore this??? i got too much data there to lose..

---

### Post by caljohnsmith on 2008-10-02
Some BIOSes are not able to access anything on the HDD past 137 GB, and your Ubuntu partition starts at about 375 GB, or clearly past that point (and your Ubuntu partition has all your Grub files necessary to boot properly). Usually if the 137 GB BIOS limitation is the problem, you'll get a Grub error like error 18, but I've seen the situation where Grub's stage1.5 file is not embedded in the MBR for some USB drives, and then I think you may not get a Grub error and instead get the result you got.

So bottom line is that I would recommend that you move Grub's files closer to the beginning of your HDD and see if that helps. What you can do is reduce the end of your sdc1 Windows partition by just 10-20 MB using gparted, and then create another ~10 MB primary partition with that space and format it to ext3. Then you can move all your Grub files there, reinstall Grub to the MBR so that it points to your new Grub partition, and that may solve your problem. 

To do this, boot your Ubuntu Live CD, open a terminal, and do:
```
gksudo gparted
```
Use that to shrink the end of sdc1 by 10-20 MB and create a new primary partition of about 10 MB with that space, formatted to ext3. Once you get that far, post the output of:
```
sudo fdisk -lu
```
And we can go from there.

---

### Post by louieb on 2008-10-02
> **lamagy said:**
> 
i dont know what i did after a couple of the mount commands or something like that, to no avail...then i loaded up to xp and the main partition sdc1 on the ext HD is corrupt, well when i try to access it in xp it tells me if i want to format the disk...  i got too much data there to lose..

Don't know what happened either. Your data is probably still there. To to recover your data get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  on that CD is program called **testdisk**  run its diagnostics - that alone should get your data back. Another program on that is photorec it has a good reputation for recovering files.

sounds like caljohnsmith is right about that pc having a bios limit of 137GB that would accout for  the " blank screen with  'GRUB_' at the top"

---

### Post by lamagy on 2008-10-06
hi all, i managed to save the data and re-formated the hard drive.

no i installed ubuntu 'again'. and now im getting a grub> promt upon loading.

what can i do now, i already tried find/boot/grub/stage1 then root the partition of stage1 then set up (SDC)

is there a 'run' command which can get ubuntu going???

---

### Post by louieb on 2008-10-07
Curious as to what you did to "get your data back"?

At the grub> do a  
```
find /boot/grub/menu.lst

```what does it return? 
if it found something try loading the menu.lst file
```
configfile (<whatever the find command returned>)/boot/grub/menu.lst
```If you get a menu try the Ubuntu entry. What did it do? 

If it doesn't work 
Since you reformatted the drive and reinstalled. Boot the live CD and   post the output of 
```
sudo fdisk -lu
```And last about the run command. Sorta you can enter the same type of statements that are in the menu.lst file. for example if I wanted to boot my Ubuntu install from the grub prompt I would enter. 
```

root       (hd0,0)
kernel     /vmlinuz  root=/dev/sda1  ro 
initrd     /initrd.img 
boot

```What you enter would not be the same this is just an example.

---

### Post by lamagy on 2008-10-07
Hi, to recover the data back i used a proggie called eusus data recovery or something like that.

takes about half a day to scan your hard drive but well worth it as then all your files will be located and you can move them to a working drive.

as for the grub promt, well i tried find /boot/grub/stage1 and nothing comes up.

can't do an fdisk -l command either, i just gave up.

i've now installed ubuntu again and let it use the whole external hard drive, before i would split partition between ntfs, when i get home i'll check to see if that's the cause, maybe the ntfs primary partition does not hold a bootloader or something i dont know, im about to send linux out the window..

---

