---
title: "Grub error no such partition"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by johnson094 on 2011-03-10
Hi, 

I am new to Ubuntu, though I have managed to install a fairly stable 10.04 LTS onto my office desktop on a separate HD next to Windows Vista.   I have a Pentium 4 desktop at home using an  ASUS motherboard, 2 Gb ram, 160 Gb HD.  This is a brand new install so I am not worried about loss of data....just loss of time.

I installed Widows XP on my computer and everything was fine.  I then booted from the Ubuntu 10.04 LTS CD and installed this version.  I used the "advanced" manual partition  and assigned half the drive to Windows and half to Ubuntu.   Everything seemed to install ok, but when I did the reboot, I get the error:  "no such partition Grub rescue"  I am unable to access either operating system, but by booting from the Ubuntu 10.04 LTS CD I can see the partitions and both Operating Systems.

I have been reading through the posts for the last couple of days, but each post seems to be unique to an individual problem, so I am hesitant to try them without some input from you guys.  I have tried to look over the Boot Info Script and have run the "blkid" command in an attempt to see if anything glaring shows up, but honestly I don't know what I am looking at.  I tried to use the "shift key" at startup in order to take a look at the grub menu and script, but my computer does not respond to the shift key.  I have completely reinstalled both operating systems with the same results.

In short, I am attaching my Boot Info Script in  hopes that one of you will look it over and give me some input.

Thanks in advance for your assistance  :D

David

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,000,455   163,000,393   7 HPFS/NTFS
/dev/sda2         163,002,366   312,580,095   149,577,730   5 Extended
/dev/sda5         163,002,368   306,395,135   143,392,768  83 Linux
/dev/sda6         306,397,184   312,580,095     6,182,912  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16022208512 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31293376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    31,293,375    31,293,313   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        04D4FD0BD4FCFFAA                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        92087e27-04cf-497e-ba20-ebdecc3119b9   ext4                                     
/dev/sda6        1f0b4dd7-1b78-4313-9c75-a3eb0fac51a9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C2BC8297BC82859F                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 92087e27-04cf-497e-ba20-ebdecc3119b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 92087e27-04cf-497e-ba20-ebdecc3119b9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 92087e27-04cf-497e-ba20-ebdecc3119b9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=92087e27-04cf-497e-ba20-ebdecc3119b9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 92087e27-04cf-497e-ba20-ebdecc3119b9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=92087e27-04cf-497e-ba20-ebdecc3119b9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 92087e27-04cf-497e-ba20-ebdecc3119b9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 92087e27-04cf-497e-ba20-ebdecc3119b9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 04d4fd0bd4fcffaa
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=92087e27-04cf-497e-ba20-ebdecc3119b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1f0b4dd7-1b78-4313-9c75-a3eb0fac51a9 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  94.3GB: boot/grub/core.img
 148.0GB: boot/grub/grub.cfg
 137.5GB: boot/initrd.img-2.6.32-24-generic
  83.7GB: boot/vmlinuz-2.6.32-24-generic
 137.5GB: initrd.img
  83.7GB: vmlinuz


```

---

### Post by Rubi1200 on 2011-03-10
Is sdb being used for storage, backup?

How is BIOS set to boot; which device priority?

Why do you have this file on sdb?:>    /wubildr

---

### Post by johnson094 on 2011-03-10
Hi Rubi1200,
 
Thanks for your response...believe you have assisted me in the past.
 
First of all, boot order is CD/DVD Rom, then harddrive. That 16 gb drive is a thumb drive that,  after I ran the boot script and sent my post, I realized was still in the USB port. I used it to download the script file onto my office computer and then to place it on the desktop of the home computer which I am trying to get going. The "wubldr" file was still on it at the time.

---

### Post by Rubi1200 on 2011-03-10
I don't see anything in the results that immediately jumps out as being problematic.

That said, I will ask some other forum members to take a look and offer some perspectives on the situation.

---

### Post by johnson094 on 2011-03-10
Okay, sounds great.

---

### Post by drs305 on 2011-03-10
The files look correct so here is my guess...

Since you have XP, this is probably a bit older machine. Everything looks normal but two of your Grub2 files are beyond 137GB. This was a common BIOS maximum disk size in earlier computers. If your BIOS can't see the boot files beyond 137GB, it won't boot.

You can check by entering BIOS as you power up the machine. Check the reported disk size. If it's less than 138GB, you should try to enable any 'large disk' option that might be available, or try to find out if your manufacturer has a BIOS update. These would allow you to retain your current setup without changing anything.

Your Grub configuration file doesn't contain the code to allow it to check for a stuck key (which is what holding SHIFT down activates). You may be able to press the ESC key repeatedly during boot, but since your grub menu is also beyond the 137GB limit that may not do any good either.

If you can't update your BIOS there are other steps you can take, such as shrinking your Ubuntu partition to have it all contained within the first 137GB, or creating a separate /boot partition early in the disk, but let's see if that is the issue first.

---

### Post by johnson094 on 2011-03-10
Drs305
 
You mention that
> two of your Grub2 files are beyond 137GB
 
Is that what you meant?  My hard drive is only 160 GB.
 
You are correct, my motherboard is   Asus #P4B266 Give me a little while to check my bios settings and upgrade if possible.  
 
I'll get back with you soon.
 
Thanks

---

### Post by drs305 on 2011-03-10
> **johnson094 said:**
> Drs305
 
You mention that

 
Is that what you meant?  My hard drive is only 160 GB.
 
You are correct, my motherboard is   Asus #P4B266 Give me a little while to check my bios settings and upgrade if possible.  
 
I'll get back with you soon.
 
Thanks

Yes, your kernel and grub configuration/menu files are outside the limit. Actually so is your shortcut "vmlinuz" but the current menu doesn't point to that.

The BIOS may not be able to see anything beyond 137GB, even though the drive is 160GB.  Sometimes it's only the grub menu file that is outside the limit and you could boot manually; unfortunately your "vmlinuz..." file is also outside the limits so that isn't going to be possible if it's a BIOS limit problem.

---

### Post by johnson094 on 2011-03-10
I opened up BIOS, don't see anything about "disc size".  When I select my hard drive in BIOS, this info comes up:
 
[WDC WD1600AAJB - 00J3A 0 ]
 
Cylinders                 1024
Head                         255
CHS Capacity      8422 MB
Max LBA capacity 8455 MB
 
Is this what you meant?
 
Thanks

---

### Post by johnson094 on 2011-03-10
Just hit me what you were talking about, Drs305...Because I split the harddrive pretty much evenly between the 2 operating systems, I put the Boot files beyond the reach of the BIOS recognition.  I have a link to an upgrade but the latest is 2003.  What if I were to go into GParted and shrink Windows and Ubuntu down a bit and then create another partition at the end of the drive for file storage?  Would that work?
 
 
Thanks

---

### Post by johnson094 on 2011-03-10
Thought I would try the BIOS update before I changed partitions.
Would you mind helping me to try and update my Bios?  Never done this before and the instructions state I must perform everything in dos mode.  This is the site that has instructions for my type of motherboard.  It mentions "floppy drive" (shows how old the computer is) but I'll be working off thumb  drive and running Ubuntu off the CD.  Does it matter whether I upgrade using the Linux uprade or the Windows?  Can't access Windows so I was going to try and do it off the Unbuntu CD.  Would greatly appreciate your help.
 
David

---

### Post by YesWeCan on 2011-03-10
I can't advise on your bios upgrade. Also, you didn't include the link?

I notice you have a Windows installation on your 16GB drive.

If you want to be able to boot the 160GB drive into Windows again, try this from the Ubuntu live CD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then boot off the 160GB drive.

---

### Post by YesWeCan on 2011-03-10
> **drs305 said:**
> The BIOS may not be able to see anything beyond 137GB, even though the drive is 160GB.  Sometimes it's only the grub menu file that is outside the limit and you could boot manually; unfortunately your "vmlinuz..." file is also outside the limits so that isn't going to be possible if it's a BIOS limit problem.
Just out of interest, assuming your hypothesis is right, why is it the case that the Ubuntu installer can use the disk space beyond 137GB but the Grub bootloader cannot?

---

### Post by drs305 on 2011-03-10
I didn't see a link to your BIOS update in your post. It really depends on the BIOS maker. You may have to make a bootable floppy/removable drive to be able to install it. You can make a bootable Windows drive, which is probably what most update instructions are written for. If you can find instructions on how to do it via Linux that would be fine as well. The BIOS doesn't know OS's...

BIOS updates have been made very easy lately, although upgrades really shouldn't be attempted IMO unless necessary (in your case it is). If the site doesn't provide specific instructions on how to upgrade your BIOS, do a search for your specific BIOS and you will find a guide posted somewhere.

---

### Post by johnson094 on 2011-03-10
That link to my BIOS update site is: [http://support.asus.com/technicaldocuments/technicaldocuments.aspx?root=198&SLanguage=en-us](http://support.asus.com/technicaldocuments/technicaldocuments.aspx?root=198&SLanguage=en-us)
As you can see, the upgrade utility built into my BIOS will be looking for A:/ the floppy drive which I have disabled on my computer. I wouldn't know where to begin to find a floppy... any way to get around that by means of a thumb drive or CD?  Based on the instructions found in the above link and in this link ([https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux#BiosDisk](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux#BiosDisk)) could someone explain how to use the mkimage command in order to get around the use of a floppy?
 
As for determining the Bios disc size limit, I tried to reboot and catch the script as the Bios posts but even using the "pause scrn" key, I just can't get it to halt on the line that describes the disc size. I have tried and tried and tried.
 
I have a couple of thoughts. 
 
1) If I am able to get the 2 operating systems both within the 138 GB range, would I still be able to use the remainder for file storage, ie would the BIOS see that?
 
2) Would installing Ubuntu ahead of Windows make a difference?
 
Appreciate all the help thus far, got to turn it loose for awhile, but I'll check back in AM.
 
Thanks guys.

---

### Post by drs305 on 2011-03-10
> **johnson094 said:**
> 
I have a couple of thoughts. 
 
1) If I am able to get the 2 operating systems both within the 138 GB range, would I still be able to use the remainder for file storage, ie would the BIOS see that?
 
2) Would installing Ubuntu ahead of Windows make a difference?
 
Appreciate all the help thus far, got to turn it loose for awhile, but I'll check back in AM.
 
Thanks guys.

I'll take a look at the BIOS update links but to be honest I've updated my own BIOS a few times but am sadly lacking enough experience to advise others.

1) Yes. Once an OS boots, it can see the entire disk. It's only the BIOS that can't see it.

2) If you restrict all your boot files, from whatever OS you are using, to the range seen by BIOS it will work. Generally, *if the BIOS sees 137GB* and all the OS's are within those limits, they should work.

Normally I'd say you could just shrink your Ubuntu a bit using Gparted - it's very easy to do. But I don't know how to analyse what you posted about the cylinders and LBA. I don't know how much of your drive the BIOS is seeing based on what you reported. It could be as little as the first 8GB. There was a time that the BIOS limit was about 8.5GB, and it looks like that is what you posted. But I just don't know. 

I'll look at those links and if I can tell you how to update the flash via USB I'll post back.

---

### Post by drs305 on 2011-03-11
If you still want to try to update the BIOS but haven't found instructions on making a bootable USB drive for DOS, the easiest way would be to do it from Windows. You can most likely restore Windows from the LiveCD with the following commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Just run those 2 commands. Don't worry about the lilo messages.

Once you get Windows back, here is a link to making USB DOS flash drives via a variety of methods:
[http://www.bootdisk.com/pendrive.htm]("http://www.bootdisk.com/pendrive.htm")

---

### Post by YesWeCan on 2011-03-11
Here's an idea.
You could use a live CD and gparted to insert a new partition just in front of the Windows partition. Say 200MB size, ext2 and mounted at /boot. This will cause the Grub files to be accessible within the bios size limit.

You would need to create this partition, then copy all your /boot files from your Ubuntu partititon to it and then add an entry to /etc/fstab to mount it at /boot. Then reinstall grub specifying the new partition as the root directory.

I don't know if this will work but it should allow Grub2 to find all the files it needs to boot Ubuntu and Windows.

---

### Post by johnson094 on 2011-03-12
Sorry Drs305,
 
Been away from the computer for awhile. Got a bad case of bronchitis and have been in bed for two days, feel better today.
 
In the meantime, I looked over that site ref BIOS and USB boot disc. I'm a little afraid to tackle that with my limited knowlede..though on the other hand I don't have much of a motherboard as it is. I just finished formating my drive and reinstalling Windows XP to the point it is stable and all updates and drivers are working. I limited it to 60 GB.
 
I was preparing to reinstall 10.04.1 LTS, when I noticed Yes WE Can' post. That is pretty much one of the options you gave me earlier. If I were to do the manual partition off the CD, and I created a 200 Mb partition in front of Windows as Ext2 and have it mount at /boot, then created the EXT4 partition behind Windows, do you think this would work? Would I still have to do all the copy and paste of the boot files to the partition and then add the entry to /etc/fstab/ (whatever that is....I'll google it and read up on it in a minute) to mount it at /boot? Though I have never done this, it appears easier than the BIOS thing.
 
Thanks for your input Drs305 and thanks for the idea Yes We Can.
 
Hope to hear back.

---

### Post by drs305 on 2011-03-12
Yes, that will work. I wish we had discussed this before you reinstalled Windows. It's not critical, but it may have saved some time. 

From what you posted, I don't know if your current BIOS only sees 8Gb or 137GB. If it's 137, you can just make a /boot partition right after Windows when you install Ubuntu. If you are installing Ubuntu from the CD, just create the /boot partition (1 or 2 GB will will be plenty) and then create and extended partition with two logical partitions (one for / and one for /swap). As it installs, Ubuntu will make the appropriate entries in fstab. You could also make another partition for /home, but I don't want rehash that debate here. There are plenty of threads about the advantages/disadvantages of having a separate /home partition.

The reason for the discussion about how you reinstall Ubuntu is that it's possible your BIOS only sees 8GB, in which case the installation will fail. In this case, you will have to make the /boot partition the first one on your drive. 

The second optoin is to move the entire Windows partition "to the right" to make space for a /boot partition, but it will probably take a couple of hours to run and there is always the slight chance of losing your Windows files.

Hope you get to feeling better soon.  :-)

---

### Post by johnson094 on 2011-03-12
Ok, here goes! Just to know ahead of time, I am opting for Plan A..."the BIOS sees at least 137 Gb." I shrunk the Windows partition down to 50 Gb and that worked out ok. Now before I start, if the install ends with a boot failure will I be able to recover the harddrive in the same condition as it stands right now? If so, if the boot failure does occur, I'll check with you on how to put the boot partition in front of Windows.
 
 
Thanks much

---

### Post by drs305 on 2011-03-12
> **johnson094 said:**
> Ok, here goes! 

Good luck. We are all counting on you.  ;-)

---

### Post by johnson094 on 2011-03-12
Have a quick question .  As I selected manual partition.  I selected "unallocated area" then set up a partition 2 GB in size..this is for boot partition.  In the "type of partition" drop down box, I don't see boot.

---

### Post by drs305 on 2011-03-12
> **johnson094 said:**
> Have a quick question .  As I selected manual partition.  I selected "unallocated area" then set up a partition 2 GB in size..this is for boot partition.  In the "type of partition" drop down box, I don't see boot.

The type would be ext3 or ext4, the mountpoint would be /boot.

---

### Post by YesWeCan on 2011-03-12
I thought only 100MB or 200MB was needed for /boot?
2GB is a little wasteful, or am I missing something?

---

### Post by johnson094 on 2011-03-12
Ok got that, then I highlighted free space and created 2 Gb swap partition (size of RAM) at end of free space . I next highlighted free space, chose Ext 4 partition and set mount as "/". Is this right?
 
I read in one tutorial @ [http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
 
that I should set this partition as Primary, but my install screen doesn't give that option.

---

### Post by drs305 on 2011-03-12
> **YesWeCan said:**
> I thought only 100MB or 200MB was needed for /boot?
2GB is a little wasteful, or am I missing something?

I've dealt with about a dozen posts over the course of helping people where users allowed kernels to build up without deleting them (I think about 15 was the most I've seen). I agree 2GB seems too large for the foreseeable future, and 1GB is probably also overkill.

However, Grub 2 puts things in /boot/grub. I don't know if it was a bug or a glimpse into the future, but for a while in Grub 1.99 if you put an image in /boot/grub it was automatically added as a splash image. I thought it was pretty cool that you could just copy an image file into /boot/grub and it would appear. That 'bug' disappeared fairly quickly and I never established whether it was a mistake or not. 

However, as Grub 2 expands it's capabilities and adds things such as locales into /boot/grub, I'd rather err on the large side when a user isn't pressed for space. 

That being said, my /boot folder is currently only holding 50MB worth of files at the moment, so I think your question is certainly reasonable.

---

### Post by YesWeCan on 2011-03-12
I see where you are coming from. It is a pest when /boot fills up with junk and one has to go and weed it. I would have thought 1GB would keep most people going for quite some time.
It's sort of funny these days with such huge drive capacities; like I have 2TB of space and I still spent more minutes than I should have deliberating about whether my /boot should be 100MB or 200MB! A GB here, a GB there, soon we're talking real storage. :p

---

### Post by kagerato on 2011-03-12
> **YesWeCan said:**
> Just out of interest, assuming your hypothesis is right, why is it the case that the Ubuntu installer can use the disk space beyond 137GB but the Grub bootloader cannot?

Although your question was answered in an indirect manner, I think it warrants a more direct response.

The fundamental reason for this limitation is that an older version of the hard disk ATA interface uses 28 bits to store the sector index. BIOSes, various hardware firmware, and older software all typically assumed that interface and were designed for it.

28 bits gives you 2^28 possible sectors, and each sector is 2^9 or 512 bytes.  The maximum storage addressable with this scheme will thus be (2^28)*(2^9) = (2^37) bytes.  2^37 is roughly 1.37 x 10^11, or ~137 gigabytes.  Using the perhaps more appropriate binary unit gibibyte, it's 128 GiB.

Logical block addressing for hard disks was extended in a later version of ATA (ATA-6), such that the sector index was expanded to 48 bits.  The resulting maximum storage using the same sector size of 512 bytes is 144 petabytes or 128 pebibytes.

Nearly all modern systems have migrated either to a newer ATA standard or to an alternate standard with much higher caps, so the old limits typically only come into play with legacy systems now.

> **YesWeCan said:**
> I thought only 100MB or 200MB was needed for /boot?
2GB is a little wasteful, or am I missing something?

Yes.  Normally you only need about 50 to 75 MiB for a boot partition, although playing it conservative is typically wise.  I've seen and used boot partitions as small as 16 MiB, though this is pushing it.

The storage required depends on how many kernels you intend to install there, whether they're custom slimlined kernels or full-support-everything kernels, and the size of the bootloader and its support files.

I would say it's better to try to keep boot slim, if for no other reason than making it easier to track what is going on with the system and the boot process.  Having a lot of old kernels laying around makes it difficult to remember what features are supported in each, which are used and which are forgotten, and how the grub configuration maps to each one.

[QUOTE=johnson094]Ok got that, then I highlighted free space and created 2 Gb swap  partition (size of RAM) at end of free space . I next highlighted free  space, chose Ext 4 partition and set mount as "/". Is this right?
 
I read in one tutorial @ [http://www.linuxbsdos.com/2010/10/12...tioning-guide/]("http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/")
 
that I should set this partition as Primary, but my install screen doesn't give that option.[/QUOTE]

It sounds roughly correct, depending on exactly what you're trying to do.  The reason why you're not able to set a primary partition is most likely that you're capped.  Only four primary partitions are available, due to the shortsighted limitations of DOS-style partition tables.  That limit is circumvented by creating an extended partiton as one of those primaries, and then creating "logical" partitions inside of that extended partition.

Note that Linux (and most modern OSes) can boot from logical partitions without issue.  Windows XP requires a primary partition, as I recall.  The Windows 7 installer still seems to dislike it if you try to install it in a logical partition especially on drives other than the first one registered, but I believe that problem can be circumvented in various ways.

I would recommend only consuming primary partitions as necessary.  For example, use the first for the boot partition, the second for XP, leave the third empty, and turn the fourth into a extended partition.  Then create all other partitions (swap, Win7, Ubuntu, storage partitions) as logicals in that same extended partition.  It requires some thought to get the sizes correct.

---

### Post by johnson094 on 2011-03-12
I'll have to take your word for that...my lack of expertise preceeds me.  As for the partitions I set up, I notice they are labeled 5,6 & 7.  On this 160 gb hard drive I only had Windows XP in it's own partition at start of drive.  Do multiple attempts at install leave ghost partitions on the hard drive?

---

### Post by drs305 on 2011-03-12
> **johnson094 said:**
> As for the partitions I set up, I notice they are labeled 5,6 & 7.  On this 160 gb hard drive I only had Windows XP in it's own partition at start of drive.  Do multiple attempts at install leave ghost partitions on the hard drive?

No ghosts. They must all be logical partitions. The logical partitions start with 5, regardless of how many primary partitions there are.

---

### Post by johnson094 on 2011-03-12
> Good luck. We are all counting on you. :wink:
 
In review, this is what I did:
 
Windows XP occupies the first 50 Gb of hard drive.
 
#1 I created a 2 Gb partition just behind windows in the unallocated space, Ext 4 partition mount at "/boot"
 
#2 I created a 2 Gb partition at the end of the unallocated space , swap file.
 
#3 The remainder of the unallocated space I designated as EXT 4 and set to mount at "/"
 
The install went well but upon reboot I got the error that prompted this thread. Guess my BIOS is older than I thought. As I see it I have 3 options:
 
#1 Update BIOS...most current update is 2003...may not help. 
#2 Attempt to use install CD to move windows over by 2 Gb and set up boot partition ahead of windows which may cause loss of files and lead to complete reinstall.
#3 Do a complete reinstall of Windows after first using GPartin to set up the partitions as /boot, Windows, Ext 4 and swap. Then install windows into it's designated partition. I have read that Windows should come ahead of Ubuntu.
 
One is last resort because it looks like the most complicated. Think I'll give 2 a go and I can always fall back on option #3. It's only time, and look at all the experience I'm getting.
 
Thanks to all
 
BTW, I'll not get started until tomorrow, so if any of you see any "madness" in this madness, drop me a post. I'll check back before I start.  
 
Also when I format the hard drive doesn,t it get rid of the Primary partitions?  if so where are they?

---

### Post by drs305 on 2011-03-12
> **johnson094 said:**
> One is last resort because it looks like the most complicated. Think I'll give 2 a go and I can always fall back on option #3. It's only time, and look at all the experience I'm getting. 

Two would probably be my choice as well. We are hesitant to recommend moving partitions right since it means every byte in the partition is generally moved, but the move occurs most of the time without any problems. Just be prepared to let the software do its thing - it will take a while so check your power sources and relax...

---

### Post by drs305 on 2011-03-12
> **johnson094 said:**
> One is last resort because it looks like the most complicated. Think I'll give 2 a go and I can always fall back on option #3. It's only time, and look at all the experience I'm getting. 

Two would probably be my choice as well. We are hesitant to recommend moving partitions right since it means every byte in the partition is generally moved, but the move occurs most of the time without any problems. Just be prepared to let the software do its thing - it will take a while so check your power sources and relax... 

And while 1GB would probably be more than I enough if you ever decide to have another OS on the system you could split your primary /boot partition to allow another primary /boot partition for the third OS...  ;-)

---

### Post by kagerato on 2011-03-12
> **johnson094 said:**
> The install went well but upon reboot I got the error that prompted this thread. Guess my BIOS is older than I thought.

It's not impossible, but I would be surprised if a Pentium 4-era machine were still subject to the 8 GB barrier.  (That one is caused by the archaic Cylinder, Head, Track addressing scheme, which mirrors the way very old hard disks addressed the sectors.)

Either way, you can circumvent it by placing your boot partition within the first 8 GB of the drive.

I wouldn't recommend updating the BIOS unless you have some evidence that the problem will actually be addressed.  Some vendors keep detailed, published notes about changes made by their BIOS updates, but others provide almost no information at all.

---

### Post by johnson094 on 2011-03-12
I understand, have a good night or day depending on where you are.  I'm eastcoast US.
 
Thanks again

---

### Post by johnson094 on 2011-03-12
> I would be surprised if a Pentium 4-era machine were still subject to the 8 GB barrier. (That one is caused by the archaic Cylinder, Head, Track addressing scheme, which mirrors the way very old hard disks addressed the sectors.)


 
 
You know, that's what I was thinking, but this computer is a self build that my son was going to toss and I took it to practice on.  He may have put a larger processor on the old motherboard but the hard drive I bought brand new.  Oh well, I have know fears of data loss because its a fresh install and I'm actually enjoying the chase.
 
See ya

---

### Post by YesWeCan on 2011-03-12
> **kagerato said:**
> Although your question was answered in an indirect manner, I think it warrants a more direct response.

The fundamental reason for this limitation is that an older version of the hard disk ATA interface uses 28 bits to store the sector index. BIOSes, various hardware firmware, and older software all typically assumed that interface and were designed for it.

28 bits gives you 2^28 possible sectors, and each sector is 2^9 or 512 bytes.  The maximum storage addressable with this scheme will thus be (2^28)*(2^9) = (2^37) bytes.  2^37 is roughly 1.37 x 10^11, or ~137 gigabytes.  Using the perhaps more appropriate binary unit gibibyte, it's 128 GiB.

Logical block addressing for hard disks was extended in a later version of ATA (ATA-6), such that the sector index was expanded to 48 bits.  The resulting maximum storage using the same sector size of 512 bytes is 144 petabytes or 128 pebibytes.

Nearly all modern systems have migrated either to a newer ATA standard or to an alternate standard with much higher caps, so the old limits typically only come into play with legacy systems now.
Thanks that is useful.
What I still don't understand is why the installer is able to install more than 128GiB on the drive. This would suggest that the installer is using a different sector addressing method to Grub/bios. If so, what is the difference and why doesn't Grub use it?

---

### Post by kagerato on 2011-03-12
> **YesWeCan said:**
> This would suggest that the installer is using a different sector addressing method to Grub/bios. If so, what is the difference and why doesn't Grub use it?

Yes, the operating system kernel (Linux, in our case) does use a different sector addressing scheme.  Typically it uses some modern form of logical block addressing with at least 48 bits for the sector index, and sometimes as many as 64 (or more).

Now, the reason why these old BIOSes don't use a modern method is simple.  They weren't designed to, either because the standard didn't exist at the time or because development time and money was too limited to implement it (and they cynically didn't think anyone would demand it).

As for Grub, it is stuck in the middle.  When Grub starts, the operating system kernel is not yet available.  Indeed, Grub's purpose is to hand-off control to the selected OS.  Therefore, it's not possible for Grub to simply say: hello Linux, replace this broken BIOS logic for me.  If we do that, there's no real reason to even have Grub; we could simply boot directly to a particular Linux system from the BIOS and handle everything else after that.

Essentially, Grub has a chicken-and-egg problem.  Either it can (1) incorporate the same functionality and logic as an OS kernel, which would bloat up its size massively and essentially turn itself into an OS of sorts, or (2) it can rely only on hardware and firmware services like the BIOS, and face all the limitations and other consequences of that.

---

### Post by johnson094 on 2011-03-13
:popcorn:

As usual you guys have come thru again.  When I first set up my partitions I allowed 10 Gb of space out front of windows (after moving windows to the right) for boot files as was suggested and then installed my Ubuntu behind windows.  When all done I rebooted and Ubuntu came up fine.  When I rebooted to go to Windows I got the error "out of disk"...now the bios wasn't seeing the windows boot because 10 Gb out front was beyond the BIOS detection.  

So I went back to the CD and slid all the partitions to the left about 8 Gb and rebooted. Everything boots fine and I got my wireless up and running so I could send you a screen shot 

[IMG]file:///tmp/moz-screenshot.png[/IMG]


Thanks for all your help Drs305!  Thanks for the input from YesWeCan and kageratu I learned some valuable information.  Also, once I picked up on it, I really appreciate the fact that you guys provide valuable links within your signatures.

I'll talk to you again in the future.  

David

---

### Post by drs305 on 2011-03-13
:p :p

Glad you got it working. This has definitely been an interesting issue. Didn't think I'd ever see another 8GB BIOS limit...

Should you decide to install another version of Linux, you can split your /boot partition in two and install another /boot primary partition within the BIOS limits.

If your computer supports it, and you decide to install a new copy of Windows, it should work with your current setup. Even though it will be installed deeper on the disk, I believe the Windows bootloader now piggybacks on any existing Windows boot files so it shouldn't be a problem.

Happy Ubuntu-ing !

---

