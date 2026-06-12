---
title: "GRUB Boot Loader Prob"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by amp_182 on 2005-02-02
[FONT=Trebuchet MS]I already have WIN XP loaded on my machine (i know its bad but i have to deal with it), the problem occurred after i loaded UBUNTU onto my machine. I cannot boot into windows now, cannot find it, eventhough i specified when i installed UBUNTU to include windows as boot option. I allocated partitions for LINUX, which would not overwrite the windows ones.
I don't know what to do about this because i need to use both operating systems on my home machine, i am almost crippled without it.
If anyone can help me that would be great, i just don't know how resolve this issue being a LINUX newbie.
P.S. this has happened to one of my friends machine with XP.  :-(   [/FONT]

---

### Post by KiwiNZ on 2005-02-02
Some more details would help.
 What error messages do you get .

---

### Post by Scribe on 2005-02-02
We've had the exact same problem.  There were no error messages.  We also allocated new space for Ubuntu.  This space is active but the space where Windows XP was shows as FREE SPACE.  We don't get the choice of which operating system to boot into.

I wanted to replace Xandros with Ubuntu on my computer too.  I rarely use Windows XP, but I need access to it occasionally.  Now I'm too scared to load Ubuntu in case I loose Windows.

Can someone help fix this problem please?

---

### Post by amp_182 on 2005-02-02
[QUOTE=amp_182][FONT=Trebuchet MS]I already have WIN XP loaded on my machine (i know its bad but i have to deal with it), the problem occurred after i loaded UBUNTU onto my machine. I cannot boot into windows now, cannot find it, eventhough i specified when i installed UBUNTU to include windows as boot option. I allocated partitions for LINUX, which would not overwrite the windows ones.
I don't know what to do about this because i need to use both operating systems on my home machine, i am almost crippled without it.
If anyone can help me that would be great, i just don't know how resolve this issue being a LINUX newbie.
P.S. this has happened to one of my friends machine with XP.  :-(   [/FONT][/QUOTE]

Ok, when trying to load windows, this is what it displays:
  "Booting 'Windows NT/2000/XP'
root (hd0,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

thanks

---

### Post by rudi on 2005-02-02
Just to make sure windows is still there open a ternimal and run the command:
  cfdisk. This will open a partition program. Probably windows is still there if you find a line similar to this:
   ```
hda1  -- boot -- primary -- NTFS (or W95 FAT32 LBA) -- 
``` 
  You could try to mount it to see if the files are still there:
   ```
mkdir /media/windows
 mount /dev/hda1 /media/windows
``` 
  If all went well you could make an entry in your Grub menu to boot Windows:
   ```
sudo pico /boot/grub/menu.lst 
``` 
  Now add the following lines:
   ```
title		Windoze XP
 root		(hd0,0)
 makeactive
 chainloader	+1
``` 
  If you reboot you should have an option called Windoze XP.
  *(chage the root (hd0,0) according your partition lay-out)*

---

### Post by smoeke on 2005-02-02
[QUOTE=amp_182][FONT=Trebuchet MS]I already have WIN XP loaded on my machine (i know its bad but i have to deal with it), the problem occurred after i loaded UBUNTU onto my machine. I cannot boot into windows now, cannot find it, eventhough i specified when i installed UBUNTU to include windows as boot option. I allocated partitions for LINUX, which would not overwrite the windows ones.
I don't know what to do about this because i need to use both operating systems on my home machine, i am almost crippled without it.
If anyone can help me that would be great, i just don't know how resolve this issue being a LINUX newbie.
P.S. this has happened to one of my friends machine with XP.  :-(   [/FONT][/QUOTE]
 Hi, sadly Ubuntu choose to use Grub, which might a cool program, but it messed the second time my windows partition. If you google around you'll find, that you must change the BIOS settings for your harddisk from "Auto" to LBA type (but only if the disk is of LBA type). If you change that it should work. There seems to be some bug in Grub, so that it can't correctly read this settings and therefore isn't able load a windows partition.
There are also reports, that Grub messes a little around with your partition table, so hopefully, that didn't happen in your cases. Lilo is still a better choice in my opinion. Never had problems with it, it never corrupted anything.

---

### Post by amp_182 on 2005-02-02
[FONT=Trebuchet MS]Thanks, that's tremendously helpful, i'll try that out soon. I hope your fix will work. I had an old distribution of red hat on my machine which was corrupted somehow, but it had LILO and there was never any issues with it so i know what you mean.
Thanks for the post. If it has mucked around with other boot settings, you wouldn't know anyway of restoring them?
Anyway i'll try your suggestion.
Thank you,
Andrew MP[/FONT] :-P

---

### Post by iso_bars on 2005-02-02
Hi everyone,

I'm having similar issues... Having just installed ubuntu next to Windows 2000 on my laptop (replacing Mandrake 10) i can no longer boot into windows.  The error is: NTLDR is missing.

Grub displays the correct boot option - Windows XP/2000 - and is configured correctly:
 title                    Windows NT/2000/XP
 root                    (hd0,0)
 savedefault
 makeactive 
 chainloader         +1

And from cfdisk, i know that on hda1, there is a Bootable Primary W95 Fat32 (LBA) partition of size 15734.97MB.  I understand many people suggest changing to LBA type within the bios, but i cannot do this on my laptop.

However, Its not all bad - I can access all my files through mounting the partition on ubuntu and therefore backup to another computer on my network.  I've seen various solutions on google to this problem, but most involve slightly more drastic measures than i am *quite* happy with!  It seems to me that all my files are there, just the MBR has been screwed up.  Curiously, on the windows partition, there *is* a ntldr file!

Any suggestions?  Thanks in advance,
iso_bars

---

### Post by amp_182 on 2005-02-02
[FONT=Trebuchet MS]Curious, to run these commands in the prompt, what directory do i need to be in for the ctdisk command to work. At present i am at my home directory or desktop, please advise me how to do this since i am only really new to this.
I ran the command but gave me an error running it from where i did.
Anyway thanks for your help.
Andrew MP[/FONT] 8-)

---

### Post by rudi on 2005-02-03
[QUOTE=amp_182][font=Trebuchet MS]Curious, to run these commands in the prompt, what directory do i need to be in for the ctdisk command to work. At present i am at my home directory or desktop, please advise me how to do this since i am only really new to this.
 I ran the command but gave me an error running it from where i did.
 Anyway thanks for your help.
 Andrew MP[/font] 8-)[/QUOTE]
 you can use them from any directory just type **cfdisk **(not ctdisk!).

---

### Post by Wim Sturkenboom on 2005-02-03
Run cfdisk as root (or in the root terminal). Else it will possibly give you a FATAL ERROR that the partition begins after the end_of_disk :D

---

### Post by thestarman on 2005-02-03
That's c**f**disk (not *ctdisk*), and apart from what others said, you might need to use the command: "sudo" in front of "cfdisk" since Ubuntu doesn't allow us to be logged in as 'root'.  Other than cfdisk, you could also use the linux command: "**fdisk -l**" (in a console/shell window) which will '**l**ist' all of your partitions; making it easy to *copy and paste* them into here.

If anyone wants to learn more about booting-up PCs in general, the MBR sector or the GRUB or LILO boot sector(s), etc., you may wish to look through my site starting here: [http://thestarman.pcministry.com/asm/mbr/MBR_in_detail.htm](http://thestarman.pcministry.com/asm/mbr/MBR_in_detail.htm) .

Daniel (aka, The Starman).

---

### Post by toujours on 2005-02-03
Ok, I've got the same kind of problem with the same message. 

I had a Win2k partition and reduced it with partition magic, leaving free space.
By the way, my usb mouse didint work either, but that sanother problem...


   Device   Boot      Start         End      Blocks            Id  System
/dev/hda1   *           1          60945     30716248+   7    HPFS/NTFS
/dev/hda2           60946       78818     9007992       83  Linux
/dev/hda3           78819       79656      422352        f     W95 Ext'd (LBA)
/dev/hda5           78819       79656      422320+     82  Linux swap

Sorry about page setting of this - the forum interface ate my extra spaces !


*** Latest news ***

Switched my HDD to LBA (as recommended) in the BIOS and all seems to be well. Now I just got to sort out USB (it's not just the mouse) not working. Thanks for the help !

---

### Post by baylisscg on 2005-02-03
<snip>

[QUOTE=iso_bars]
However, Its not all bad - I can access all my files through mounting the partition on ubuntu and therefore backup to another computer on my network.  I've seen various solutions on google to this problem, but most involve slightly more drastic measures than i am *quite* happy with!  It seems to me that all my files are there, just the MBR has been screwed up.  Curiously, on the windows partition, there *is* a ntldr file!
[/QUOTE]

I'm having the same problem. The good news is that you have it working. Sort of. NTLDR is the windows bootatrap loader. IFAIK GRUB is correctly loading the MBR code on a windows disk but it can't find the next stage. 

Ho Hum.

---

### Post by baylisscg on 2005-02-03
[QUOTE=baylisscg]<snip>



I'm having the same problem. The good news is that you have it working. Sort of. NTLDR is the windows bootatrap loader. IFAIK GRUB is correctly loading the MBR code on a windows disk but it can't find the next stage. 

Ho Hum.[/QUOTE]

Just fixed it. If you look in the GRUB manual [here](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)  [gnu.org] it tells you that Windows is *really* picky about the disk it boots form. You need to use **map** to reassign hd0 to the windows drive. It gives a small example.

---

### Post by Wim Sturkenboom on 2005-02-04
[QUOTE=thestarman]you might need to use the command: "sudo" in front of "cfdisk" since Ubuntu doesn't allow us to be logged in as 'root'.[/QUOTE]My Ubuntu  does allow me 8-) You just have to set the root password and you will have a root account.

---

### Post by Tichondrius on 2005-02-04
[QUOTE=rudi]you can use them from any directory just type **cfdisk **(not ctdisk!).[/QUOTE]
 it's easier and clearer to use fdisk to print out the partition table, for example:

$ fdisk -l /dev/hda

This will clearly show all your partitions and their types by name, like NTFS, FAT32, Linux, etc. So you'll know immediately if the Windows partition is still there (which it probably is). Now if grub can't boot windows because of the LBA bug, you can install lilo which will replace grub, and hopefully be able to boot Windows as well as linux. btw, you should always have a Linux live-cd (like knoppix, or ubuntu live cd) handy in case you can't boot any of your partitions, so you just boot from the live CD, mount the hardisk partitions, and fix the boot loader configuration. The other option is to restore the Windows master boot record, which you can do by booting with the windows install cd, and choosing to fix the MBR. But note that this will not let you boot the other linux partitions. So if you really can't make grub work, your best option for multi-boot is lilo.

---

### Post by thestarman on 2005-02-04
[QUOTE=smoeke]Hi, sadly Ubuntu chose to use Grub, which might [be] a cool program, but it messed [up] the second time my windows partition. If you google around you'll find, that you must change the BIOS settings for your harddisk from "Auto" to LBA type (but only if the disk is of LBA type). If you change that it should work. There seems to be some bug in Grub, so that it can't correctly read these settings and therefore isn't able load a windows partition.
There are also reports, that Grub messes a little around with your partition table, so hopefully, that didn't happen in your cases. Lilo is still a better choice in my opinion. Never had problems with it, it never corrupted anything.[/QUOTE]

Smoeke,

   I think you're mixing up some problems that many different Linux distros are having!  To the best of my knowledge (and I've been using GRUB for a long time as my boot manager), GRUB will *never* change your Partition Table!  A new Linux install, however,  will not only overwrite any boot code you have in the MBR with the GRUB boot code, but will also make changes to the Partition Table reflecting whatever choices you made during the installation...  unfortunately, if you try using "Parted" with the more recent 2.6.x kernel distros to resize any MS partitions, that's what will often mess things up!  Parted likes to use only 16 heads instead of the standard 255 in the CHS parts of the Partition Table(s).  This can easily happen with distros using LiLo just as much as GRUB.  Furthermore, if any of your MS-Windows partitions are resized in a non-standard way (do not both begin and end on a cylinder boundary) then you may never be able to boot them. This was a very big problem back in August 2004, for RedHat Fedora Core 2, SuSE 9.1 (free and pro) and many other new (at that time) 2.6.x kernel distros!  I  strongly advise people use something like Partition Magic for resizing if they have access to it, and try setting up Ubuntu Linux partitions (for the time being) with the Ubuntu Live CD's 'cfdisk' or 'fdisk,' a "Rescue" boot disk (CD or floppy) or other Linux install; possibly the QTparted in the Knoppix 'Live CD'... But don't use Linux's 'parted' to resize MS partitions (even for FAT32 types)!

The Starman.

---

### Post by thestarman on 2005-02-04
[QUOTE=baylisscg]Just fixed it.  If you look in the GRUB manual [here](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)  [gnu.org] it tells you that Windows is *really* picky about the disk it boots form. You need to use **map** to reassign hd0 to the windows drive. It gives a small example.[/QUOTE]

Perhaps with Win 9x/Me that might be true, but I believe that's only if you're trying to use those OSs on a second drive (not the Primary Master).  Here's what I've been using for my own GRUB settings for quite some time now (with Linux, Win 98 and Win2000 partitions):[FONT=Fixedsys]
[B]
title Red Hat Linux 9.0 (Shrike)
    kernel (hd0,2)/vmlinuz-2.4.20-8 ro root=/dev/hda6
    initrd (hd0,2)/initrd-2.4.20-8.img

title Windows 2000 (SP3)
    root (hd0,0)
    chainloader +1
                                                                                
title Win 98SE/DOS 7.1
    root (hd0,1)
    chainloader +1
                                                                                
title Win 2000
    root (hd1,0)
    chainloader +1

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd1,6)
kernel          /vmlinuz-2.6.8.1-3-386 root=/dev/hdb9 ro quiet
initrd          /initrd.img-2.6.8.1-3-386
boot
                                                                                
title           Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root            (hd1,6)
kernel          /vmlinuz-2.6.8.1-3-386 root=/dev/hdb9 ro single
initrd          /initrd.img-2.6.8.1-3-386
boot
                                                                                
title Floppy Boot
    root (fd0)
    chainloader +1
                                                                                
title Memory Test
    kernel (hd0,2)/memtest.bin[/B][/FONT]

These are all working just fine (plus the BOOT.INI menu selections inside my Win2000 partition as well!).  BEFORE installing any new OS, I recommend that everyone find utils to back up their whold 1st track in binary, their existing Linux "menu.lst" or "grub.conf" files and other pertinent sectors and files depending upon your configuration, layout of the drive, etc. etc. and make sure you have access to them afterwards (such as keeping them and a utility to restore them on a boot diskette!).  I've been using the same GRUB code from a SuSE 9 install that isn't even on my drive now!  NOTE: that some of my Win2000 (and even an XP partition I tested recently) installs are/were even on a 2nd HDD (Primary Slave or even Secondary Master).  Again, I think you only need the "map" commands with Win 9x/Win 3.xx/DOS OSs on 2nd, 3rd, etc. drives where they normally would NEVER run from without that extra GRUB code!

The Starman.

---

### Post by baylisscg on 2005-02-04
[QUOTE=thestarman]Again, I think you only need the "map" commands with Win 9x/Win 3.xx/DOS OSs on 2nd, 3rd, etc. drives where they normally would NEVER run from without that extra GRUB code!
[/QUOTE]

    I'm using Windows XP on a SATA drive with Ubuntu on a drive on an ATA channel and it just will not boot without remapping. For the record I use.
```

# on /dev/sda1
title           Windows XP Pro
map             (hd0) (hd2)
map             (hd2) (hd0)
rootnoverify    (hd0,0)
makeactive
chainloader     +1

```

    I'll admit the GRUB docs make it seem that it doesn't apply to NT/2000/XP but I gave it a go and it works. No more using F8 to manually alter the boot drive for me.

---

### Post by amp_182 on 2005-02-04
[QUOTE=smoeke]Hi, sadly Ubuntu choose to use Grub, which might a cool program, but it messed the second time my windows partition. If you google around you'll find, that you must change the BIOS settings for your harddisk from "Auto" to LBA type (but only if the disk is of LBA type). If you change that it should work. There seems to be some bug in Grub, so that it can't correctly read this settings and therefore isn't able load a windows partition.
There are also reports, that Grub messes a little around with your partition table, so hopefully, that didn't happen in your cases. Lilo is still a better choice in my opinion. Never had problems with it, it never corrupted anything.[/QUOTE]
 Hi, smoeke i changed the access type to LBA and its all good, thanks heaps for your help!
Andrew MP

---

