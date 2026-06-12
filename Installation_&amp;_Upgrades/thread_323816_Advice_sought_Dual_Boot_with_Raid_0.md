---
title: "Advice sought: Dual Boot with Raid 0"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by Jim Rockford on 2006-12-22
I have 3 SATA hard drives on my PC.  Two of the drives are in Raid-0 configuration, with Windows XP currently installed.  I'd like to put Ubuntu on the 3rd SATA hard drive, and leave the Raid-0 XP drives alone.  In the end I'd have only Ubuntu on the 3rd drive, and only XP on the two drives with Raid-0.

How should I handle the grub installation?  Can I overwrite the MBR and effect the dual boot, or should I put grub elsewhere? 

Thanks,
Jim

---

### Post by ryscar on 2006-12-22
I have the same setup. I put Grub on the third drive and in the BIOS made it the first boot device.  Then I added the following to /boot/grub/menu.list

rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
boot

*edit*
Almost the same setup.  My third disk is not SATA, it's IDE.

Hope that helps!

Ryan

---

### Post by Jim Rockford on 2006-12-22
Thanks Ryan.  That's precisely the concise and lucid sort of answer I was hoping for.  I'll give it a shot.

---

### Post by Jim Rockford on 2006-12-22
> **ryscar said:**
> I have the same setup. I put Grub on the third drive and in the BIOS made it the first boot device.  Then I added the following to /boot/grub/menu.list

rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
boot

*edit*
Almost the same setup.  My third disk is not SATA, it's IDE.

Hope that helps!

Ryan
-----------------------

Okay...I tried your suggestion, and ubuntu booted okay, but when I tried to boot into XP I got the error

'Error 11:  Unrecognized device string'

Am I not specifying the hard drives correctly?  In my BIOS, the two Raid-0 drives are numbered '1' and '2', whereas the other drive is numbered '4' (this is the one linux is on).

Also, I installed grub on the MBR, which I presume was on the Raid-0 disks (not the 3rd disk, where the linux installation is).  Is this a potential problem?  

When I do a 'df' in linux, I only see the file system     /dev/sdc1, which corresponds to the 3rd drive where linux is installed.  It's as if the other 2 drives (with Raid-0) don't exist, so far as linux is concerned.  I'm guessing this is because they're formatted as NTFS, but I thought I'd mention it.

Any help is greatly appreciated.  

Thanks,
Jim

---

### Post by ryscar on 2006-12-23
I was just reinstalling my entire system about an hour ago and was getting the same error with the same setup.  I did not have a space between the two sets of parentheses on the “map” lines.
map (hd0)space(hd1)

About the mbr:  If you installed Ubuntu on the third drive, that should be where it installed grub.  If you want to be sure, just disconnect the drive and it should boot to your Windows installation (if it is set to do so in your BIOS).

As far as being able to see your NTFS stuff, ???.  At this point, that’s over my head.

FYI, I am by no means an expert, just struggled with a similar problem and am glad to help where I can.

Ryan

---

### Post by Jim Rockford on 2006-12-23
Thanks Ryan.  When I get back to work, where I'm installing Ubuntu, I'll try your fix.  I appreciate the help!

Jim

---

### Post by logos34 on 2006-12-23
Linux ext3 can (should) see your NTFS partition, apparently it's just not mountng it automatically. 

Open a terminal and type: 

$ sudo fdisk -l (the letter l, not number 1)

The windows partition should show up ('/dev/sda1' for instance) even if not mounted. The entry with an asterisk '*' in the boot column is where grub is.

Try mounting it:

$ sudo mount /dev/sda1 (or whatever)

If it doesn't show up in fdisk, look to the bottom of your grub config file (/boot/grub/menu.lst) and see if the debian installer left a 'non-linux OS' entry for windows, with a location something like '# on /dev/sd??' (I don't know if this is how linux will see a raid0 volume).  

Try to mount it using that name.

I had grub installed on the MBR of a windows disk (master) with Ubuntu on a slave drive and had no problems.  As far as not being able to boot windows raid setup, if all else fails you could always boot from your Windows cd in restore mode and restore your windows bootloader, and then reinstall Ubuntu, this time rearranging the boot order in BIOS so that the linux sata drive is first (grub by default installs to the first disk detected), or even unplug the raid drives if you have to. 

You might have to try the Alternate install CD, which gives you options for LVM/RAID, grub, etc.)

---

### Post by ryscar on 2006-12-23
Jim,

Now that I have everything running, here is the Windows portion copied from my menu.list.

```
title           Windows XP
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
makeactive
chainloader     +1
boot
```

Let me know if you still have troubles and I will see what I can do to help.

Ryan

---

### Post by Jim Rockford on 2007-01-09
Hey Ryan (and all others) -- thanks again for the replies.  Sorry for not replying promptly, but the holidays and subsequent installation problems intervened.  It turns out that my configuration is even more problematic than I initially realized.  I'll try to explain as succinctly as possible.

But first....your format for grub worked perfectly, but only after I went through the following:

First, just to inform other readers, I am attempting a dual boot using 3 SATA drives, 2 of which are in a raid-0 configuration for Windoze XP x64, and the third is reserved for my Ubuntu installation.  A problem I was having had to do with an insane feature of the Windoze install (surprise surprise).  I had Ubuntu and grub nicely installed (without a working ethernet connection; more on that later) on the 3rd disk (call it HD3).  I then went through the Windoze installation, and noticed that although I specifically told the installer to install to the raid-0 discs (HD1/2), Windoze warned me that it wanted to install some files on HD3, which was listed first among all the drives it detected.  Apparently, there is some formula for ordering the hard drives in the detection process.  The raid-0 drives, although installed in SATA slots 1 and 2 on my motherboard, took less precedence than my HD3 drive, which I find weird since that drive (HD3 for Ubuntu) was installed in slot 4 on the motherboard (which can accomodate 6 sata drives).  I'd figure that Windoze would list the drives according to the same numerical scheme on the motherboard, but apparently the raid-0 configuration of 2 drives screwed up this ordering.  Windoze was just compelled to write its boot sector on HD3, even though I didn't list this as the drive to which to install!  I hadn't noticed this before in my initial struggles.  Windoze just wanted to blaze ahead and overwrite the grub sector.  Real nice.

To get around this I first wiped out everything and started anew, this time disconnecting the appropriate drives when installing LINUX or Windoze separately.  For the Windoze install I disconnected the drive (HD3) intended for Ubuntu, and vice-versa for the Ubuntu install.  This left GRUB on the linux drive and the Windoze boot loader on the other drive.
After editing 'menu.lst' in /boot/grub in the manner you suggest I was able to get the dual boot to work just fine.  I just had to make sure my BIOS first went to the grub drive for booting.  Note that I did *not* overwrite the Windoze boot loader.

I now have more serious problems.  My motherboard is an ASUS P5N32-E SLI with nVidia 680i chipset.  I absolutely cannot get an ethernet connection in my edgy install, and I've tried the primary fix suggested elsewhere involving a 'forcedeath' option in modprobe.conf.

I'm stuck!  Without an ethernet connection my install is basically useless, since I need to transfer gigabytes of files from other computers.  

Anyone out there with this same chipset who found a fix?

Thanks, 
Jim

---

### Post by HotRod on 2007-01-12
> **ryscar said:**
> I have the same setup. I put Grub on the third drive and in the BIOS made it the first boot device.  Then I added the following to /boot/grub/menu.list

rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
boot

*edit*
Almost the same setup.  My third disk is not SATA, it's IDE.

Hope that helps!

Ryan

How do I add this script to the menu.list???

AMD 165 opty
2 sata III in raid 0  WIndows WP Pro
1 sata I Unbuntu 6.06

I need detailed instructions please,  This is my first Ubuntu.

---

### Post by ryscar on 2007-01-14
Jim,
Glad I could help.  Unfortunately, I will not be able to help with your new problems.  Although, I did run into a similar problem with an Ubuntu server I built a while ago.  It did not recognize the on-board network controller.  I just put in a $15 Netgear card that I picked up at Fry's and disabled the other on the BIOS.  I know it defeats the purpose of having one on the mobo but, it works.

HotRod,

It should go something like this:

```
sudo nano /boot/grub/menu.lst
```

after entering your password,  it will open the file in nano (text editor).  Now you can make the changes you need.  I placed the Windows portition at the end of the file.

When you are done making the changes, hit “ctrl o” (this writes the file), then “ctrl x” to exit.

Let me now if it works.

Ryan

---

### Post by pattison on 2007-01-14
BACK UP your important files.
I tried with 5.04 to do this (install, grub on 3rd non-raid drive) and the installer broke my win install when it touched the RAID without my permission. Unrecoverable w/ repair console. Thank goodness for backups.
This is the reason I have not used Ubuntu since then. :neutral: 

I am guessing that this issue has been fixed since then, and I am ready to try feisty when it comes out.

edit:
With the distro I currently use I gave up on grub loading windows, and just use the boot time keystroke (esc) to pick my boot device. (bios feature, depends on your bios)
Also, after re-reading the thread it looks like you are installing both from scratch, so nothing to lose I guess.

---

### Post by Jim Rockford on 2007-01-16
> **HotRod said:**
> How do I add this script to the menu.list???

AMD 165 opty
2 sata III in raid 0  WIndows WP Pro
1 sata I Unbuntu 6.06

I need detailed instructions please,  This is my first Ubuntu.

First go to the directory  /boot/grub   where you'll find the file  'menu.lst'
You can then add these lines with any text editor (you'll have to use sudo because
  you need root permissions).

Write back if you still have questions.

---

### Post by Jim Rockford on 2007-01-18
> **ryscar said:**
> Jim,
Glad I could help.  Unfortunately, I will not be able to help with your new problems.  Although, I did run into a similar problem with an Ubuntu server I built a while ago.  It did not recognize the on-board network controller.  I just put in a $15 Netgear card that I picked up at Fry's and disabled the other on the BIOS.  I know it defeats the purpose of having one on the mobo but, it works.
Ryan

Hey Ryan.  Thanks again for the help.  You Ubuntu forum guys are the greatest.  Unfortunately, I had to go with Fedora 6 (64bit) for now because I was able to surmount the ethernet problem, but not with Ubuntu.  My Ubuntu days will have to wait.

Jim

---

### Post by Mnemonicman on 2007-01-29
I have a similar setup with 2 Sata2 drives in RAID0 for Windows XP64 and one Sata for Ubuntu. Got Ubuntu to boot by editing Grub so the Ubuntu drive is set to sdd instead of the default sda. Now it boots but it doesn't see the raid as one partition. How do you configure Ubuntu to recognize the windows raid as a single drive so files can be accessed? Not to hijack the thread but it would help to know.

---

### Post by danbert on 2007-01-29
That doesn't surprise me that Windows is stupid about drive ordering.  I wasn't paying close enough attention when I install Windows XP on my computer, and the damn thing installed the bootloader on my external USB drive which it saw as primary over my SATA drive.  Stupid MS!

---

### Post by l0c0m0c0 on 2007-05-09
I also have a Raid0 setup with XP on it and it's own mbr untouched still on the raid0 drives.  I then have an IDE drive with ubuntu and grub working on it.  Here is my menu.lst:

title		XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
boot

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ad2b63c7-5d91-4031-b04c-c0fd9348f874 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Ubuntu boots and XP does not.  I can boot XP if I switch the HD boot order in Bios or unplug the power from the Ubuntu drive.  Any help?  Oh and here's this:

j0nnyr0773n@D00Machin3:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4260    34218418+  83  Linux
/dev/sda2            4261        4882     4996215   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

---

### Post by l0c0m0c0 on 2007-05-09
In case anyone is wondering or having the same problem all I did was remove Boot from the last part of the XP part and it works now.  


> title		XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by TGenX on 2007-05-10
I just want to confirm that this does work...

My setup is:
Windows XP Home on a Promise Fasttrack Raid controller in a RAID 0 configuration (two 80gb drives)
Linux is on a normal IDE controller (at first, I had it set up as a slave on my raid controller - this was an error and I just wasn't thinking when I plugged it in)

My trials were as follows:
Attempt 1:
Added a harddrive to be used for Linux as a slave on my fasttrack raid controller (not sure why I did this exactly, but it wasn't intended).  Basically, the Windows XP drive was still set in bios to boot first and my linux drive wasn't an option because it was really only pointing to the Raid controller.  Installed Linux on the slave drive and hosed my Windows MBR.  Grub boot loader would hang shortly after stage 1.5 and nothing would happen.

So, I fired up my Live CD (didn't always work well... see below) and mounted my Linux drive and played around with GRUB -> menu.lst a bit to see if I could get it to boot, but was unsuccessful.  So, I fired up my Windows XP disk to recover the Master Boot Record of my windows drive, but Winblows XP would hang at a blue screen that said "Windows Setup" and wouldn't give me the menu options.  I fixed the MBR by downloading the Western Digital Data Lifeguard Tools, burning a cd and booting to it.  In the WD tools, there was an option to fix the MBR I tried (Not sure what it does, but I restarted and it went right in to Windows XP).  At this point I drew out a "map" of what I wanted to do to get linux to dual boot properly.

Attempt 2:
I had so many errors in attempt #2 that I don't want to go into it... but I found out that my installation disk had errors on it after many hours of screwing around with it...  At any point, when you start a LiveCD once, it doesn't seem like it takes TOOOOOOOOO long, but when you start it about 9 or 10 times in a row trying to figure out why it works sometimes and it doesn't others, you begin to pull your hair out over how long it takes.  Word to the wise, don't be afraid to do the "check cd" option that a lot of the Live CDs offer....   Downloaded a new ISO, burnt it, moved to attempt #3.

Attempt 3:
I realised the error I made in putting my Linux drive on my RAID controller so I moved it from the raid controller to a standard IDE port (not controlled by raid).  In my bios, I set the Linux drive to boot first, followed by the RAID controller.  I booted from the Live CD and installed Linux without any problems (had grub point to hd0).  As part of the installation I rebooted.  When it got to the Grub screen, I hit ESC to take me to the menu to see if Windows was showing.  It wasn't, so I figured I would set it up.

Fixing menu.lst to include Windows XP:
First thing I did was made a backup of the file: 
 - sudo cp /boot/grub/menu.lst /home/tgenx/menu.lst
 - sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
Then I maded the following changes to the menu.lst file:
  Change 1: Changed timeout from 3 to 10
  Change 2: Uncommented out the "color cyan/blue white/blue" line
  Change 3: Commented out "hiddenmenu"
  Change 4: Added the following as the first in the list:
                    title    Microsoft Windows XP Home
                    root   (hd2,0)
                    map   (0X82) (0x80)
                    map   (0x80) (0x82)
                    makeactive
                    chainloader +1

I rebooted to test it out, and both operating systems work.

After googling "grub and raid0" and seeing how many people said it wouldn't work, I was getting a bit discouraged.  I am not sure what clicked for me to try to put the IDE drive first in the bios boot record, but I did a search on it after a few hours and came to this thread which confirmed that the idea might work.  With a bit of trial and error, it payed off.

1:  It does work...
2: Thanks for the post becuase it helped get my brain working on what I needed to do to get the system set up properly.

---

