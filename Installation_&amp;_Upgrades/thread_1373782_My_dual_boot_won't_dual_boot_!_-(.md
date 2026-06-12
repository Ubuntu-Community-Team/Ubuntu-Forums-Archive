---
title: "My dual boot won't dual boot ! :-("
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by gsmith45 on 2010-01-06
Hi
Am having a strange problem installing a dual boot XP and Ubuntu 9.10 system.  I've set up one dual boot system previously with no real problem, but have had issues this time around.

I'm using a fairly old AMD Athlon 1100 system which seems to meet all the specs.  I have re-installed XP which now occupies about 10GB of a 27GB partition.  I have installed 9.10 into an 11GB partition at the end of the disk.  (Total disk size is 40GB).

Windows was working just fine before the 9.1 installation.  9.1 seemed to install and upgrade itself perfectly.  My problem came when trying to access Windows again via the start-up menu (I think it's called the GRUB menu?).  The first time I tried to access Windows, I got a blank screen, and then with subsequent attempts I got the screen asking whether I wanted to boot Windows in safe mode or normal mode.  Even booting in safe mode, I could see that Windows was loading a list of drivers etc, but then hung again.

Eventually, after searching this forum, I restored the MBR for Windows, using the XP Recovery Console and commands fixmbr and fixboot.  Windows was fine again, however there was no start-up menu to select Ubuntu.  Sort of back where I started <sigh>

I have now re-loaded Ubuntu all over again, let it upgrade etc, but am now having the same problem that I can't get into Windows.  I can however still mount the windows partition and search the files there.

So it seems I have both Windows and Ubuntu on the pc, but I can't really choose between them, without having to re-load or re-configure.

Any thoughts anyone?  At the moment, I have Ubuntu running, so I'd prefer to start from here rather than fixing the MBR for Windows and then having to reload Ubuntu again.

Thx

Gra

---

### Post by darkod on 2010-01-06
First of all, after restoring windows bootloader on the MBR you do not have to reinstall whole ubuntu from start. You can reinstall only grub2 (the bootloader) on the MBR, same as with windows bootloader.
From what you described, there seems to be no reason for what is happening.
You can do this: download the script in my signature. Move it on desktop for example and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Copy the content of the file here and wrap it in CODE tags (with the text selected hit the # button in the toolbar above) for easier reading. That will show detailed info about your boot process.

---

### Post by gsmith45 on 2010-01-06
Darko  - thx for the response.  Here is the RESULTS file below.  I hope it means something to you!

Gra

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeecdeecd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    55,022,624    55,022,562   c W95 FAT32 (LBA)
/dev/sda2          55,022,625    78,156,224    23,133,600   5 Extended
/dev/sda5          55,022,688    77,079,869    22,057,182  83 Linux
/dev/sda6          77,079,933    78,156,224     1,076,292  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="446F-07D9" TYPE="vfat" 
sda5: UUID="7784a4cb-bb79-4397-bdcc-30cdf2ce5625" TYPE="ext4" 
sda6: UUID="df9fd54c-61fb-49ba-bbb6-f1e2b5558035" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/graeme/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=graeme)


================================ sda1/boot.ini: ================================

 
[boot loader] 
timeout = 5 
default = multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS = "Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

================================ sda1/BOOT.INI: ================================

 
[boot loader] 
timeout = 5 
default = multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS = "Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 7784a4cb-bb79-4397-bdcc-30cdf2ce5625
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7784a4cb-bb79-4397-bdcc-30cdf2ce5625
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7784a4cb-bb79-4397-bdcc-30cdf2ce5625 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7784a4cb-bb79-4397-bdcc-30cdf2ce5625
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7784a4cb-bb79-4397-bdcc-30cdf2ce5625 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7784a4cb-bb79-4397-bdcc-30cdf2ce5625
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7784a4cb-bb79-4397-bdcc-30cdf2ce5625 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7784a4cb-bb79-4397-bdcc-30cdf2ce5625
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7784a4cb-bb79-4397-bdcc-30cdf2ce5625 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 446f-07d9
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7784a4cb-bb79-4397-bdcc-30cdf2ce5625 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=df9fd54c-61fb-49ba-bbb6-f1e2b5558035 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  28.1GB: boot/grub/core.img
  28.1GB: boot/grub/grub.cfg
  28.1GB: boot/initrd.img-2.6.31-14-generic
  28.1GB: boot/initrd.img-2.6.31-16-generic
  28.1GB: boot/vmlinuz-2.6.31-14-generic
  28.1GB: boot/vmlinuz-2.6.31-16-generic
  28.1GB: initrd.img
  28.1GB: initrd.img.old
  28.1GB: vmlinuz
  28.1GB: vmlinuz.old
```

---

### Post by darkod on 2010-01-06
It looks all right except for one thing. See at the top of the results, the boot files for windows on sda1 are doubled. All three files appear twice. I wonder if that is confusing XP to boot.
You can try temporarily to move one copy of the files from ubuntu. Do NOT delete them, just boot ubuntu, open /dev/sda1 partition and move BOOT.INI, NTLDR and NTDETECT.COM (the names in capital letters) to your ubuntu home folder for example.
If it doesn't work, you can put them back on /dev/sda1.
See if that will help to boot XP.

---

### Post by gsmith45 on 2010-01-06
Darko
Thx for the advice.  Can you tell me how to open the /dev/sda1 partition from within Ubuntu please, so that I can copy the files.  Sorry - I'm sure that this is a dumb question, but I'm new at this!

Gra

---

### Post by arty203 on 2010-01-06
I also have a boot problem. I upgraded from XP to Windows 7 (I need this for legacy business) and decided to install Ubuntu permanently rather than using from CD. During an Ubuntu session I was prompted to upgrade, which I did, but when I boot up now, there seems to be 2 versions of Ubuntu which I can choose from the boot up menu, plus the usual mem test, safe mode etc, plus the option to boot Windows 7.
 
Firstly, is there in fact more than one Ubuntu image (and therefore precious disk space taken up) and if so what action should I take.
 
If there is only one Ubuntu and one Windows 7 image, how do I edit (and where is the file) to change the boot order and the various boot selections?
 
Regards, Roy:confused:

---

### Post by gsmith45 on 2010-01-06
Roy
Your problem is very different to mine, so I'd appreciate if you could post a separate thread - which should also attract someone with expertise in that area.  In short though, based on my limited experience, what you are seeing seems typical of an upgrade and to be expected and doesn't mean you have two images.  If you want to edit the GRUB menu, you should search the forums, but make sure if you have 9.10 that you get the correspondingly right directions.  I have searched the same issue myself in the past with success, so I know it's easy to find.
G

---

### Post by darkod on 2010-01-06
> **gsmith45 said:**
> Darko
Thx for the advice.  Can you tell me how to open the /dev/sda1 partition from within Ubuntu please, so that I can copy the files.  Sorry - I'm sure that this is a dumb question, but I'm new at this!

Gra

When in ubuntu, click on Places and you should see there something like 30GB filesystem. The size should match your C: drive size. Click on it, it might ask you for your ubuntu password again, and it will mount it. It should show icon on desktop after mounting it. Then you can look inside and move the files. If you need to put them back later, do the same procedure.

---

### Post by gsmith45 on 2010-01-06
Darko
No luck.  I opened the root directory of my Windows drive as your direction.  There was only one version of each of the three files (although the filenames were all lower case).  I tried moving them anyway to the desktop, just in case there were some other files elsewhere, however when I tried to boot into Windows, I just got error messages (for example that NTLDR was missing etc.)

Any other ideas about why I can't boot into Windows, or how to work around it?

Gra

---

### Post by darkod on 2010-01-06
You mentioned that safe mode was starting. The second copies of the files might be related to that. Unfortunately I don't know about the boot process in that detail.
Put the files back. The error for NTLDR missing should go away (it was normal to get the error with the files removed).
Try booting XP and even if it starts safe mode try to see if it will boot fine into it. I'm suspecting all it needs is to boot safe mode successfully once, and then it should be able to boot the normal mode also.

PS. There is always the option to restore XP boot files again, and then restore grub2 on the MBR after that. But you said you don't want to do that right now, so it can be like last option if all else fails.

---

### Post by gsmith45 on 2010-01-06
Darko
Just tried the safe mode boot, but it's still hanging.  The screen is full of lines that start with:

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS\System32\Drivers\Mup.sys

(The Mup.sys driver is the last one before it freezes, but I noticed yesterday that the next step after this is that it should just boot into safe mode, so it may not be the cause of anything).  

I've tried safe mode a few times now, without success.

What should we do next?!

Gra

---

### Post by gsmith45 on 2010-01-08
Hi
I tried a few more things without success.  So now I have fixed the Windows boot record and the system boots directly into Windows.

I know that Linux is still installed on my machine, but because I don't see the GRUB2 menu anymore (the start-up menu) I can't access it!  

How can I start Ubuntu now, without having to re-install it every time?

Gra

---

### Post by darkod on 2010-01-08
According to the results file you posted earlier, you need to reinstall grub2 on the MBR like this:
Boot with ubuntu 9.10 cd, Try Ubuntu option. Open terminal and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub2 on the MBR of your hdd.

---

### Post by kansasnoob on 2010-01-08
Since grub2 keeps failing on you would you be willing to try reverting to legacy grub?

We could do it thru a mount & chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I'd be glad to type you some custom commands for your specific installation if you'd like.

I would however like to see the output from terminal (using the Live CD) of:

```
sudo fdisk -l
```

BTW that's a lower case L.

I just want to be sure Ubuntu is still on sda5.

---

### Post by ar87 on 2010-01-08
I had somewhat the exact same problem with vista and ubuntu 9.10 dual boot. Vista boot sometimes would work but most of the time I could see the green bar loading and then grub menu would reappear again. After trying couple of things I reverted back to grub legacy and the problem disappeared.  I am now using grub legacy. 
I am a linux and grub newbie but I think this might be a bug in grub2.

---

### Post by kansasnoob on 2010-01-08
> **ar87 said:**
> I had somewhat the exact same problem with vista and ubuntu 9.10 dual boot. Vista boot sometimes would work but most of the time I could see the green bar loading and then grub menu would reappear again. After trying couple of things I reverted back to grub legacy and the problem disappeared.  I am now using grub legacy. 
I am a linux and grub newbie but I think this might be a bug in grub2.

I don't know exactly what the deal is. I've found that some Toshiba laptops refuse to boot with grub2, no idea why and since I don't own one it's not possible for me to file a bug report.

I've also found that some multi-drive systems don't like grub2, but other times it's great. I'm actually growing quite fond of grub2 but after a certain amount of effort people just want to be able to boot.

---

### Post by gsmith45 on 2010-01-09
Guys
thx for the moral support.  Here's where I am:

1) I checked where the Ubuntu partition was, per the instruction from Kansasnoob and got this back:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeecdeecd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3425    27511281    c  W95 FAT32 (LBA)
/dev/sda2            3426        4865    11566800    5  Extended
/dev/sda5            3426        4798    11028591   83  Linux
/dev/sda6            4799        4865      538146   82  Linux swap / Solaris

2.  I tried what Darko suggested.  Starting from my system booting happily only into Windows, I ran the LiveCD, opened a terminal and typed:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

I got this back from terminal:

Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda

3.  Then I rebooted.  The "good" news was that the start-up menu re-appeared with all the Linux, memtest and Windows Options.  The "bad" news was that although I can get into Ubuntu again, I still can't get into Windows.  I tried re-booting again, selected "safe mode" for Windows, but the system is still hung.

So <sigh>, I am back where I started.  Both systems on the PC, but unable to dual-boot. 

I saw a suggestion from Kansasnoob to move to legacy GRUB.  I'm passed the point now where this is a pleasurable learning exercise, and would just like this to work.  I don't have the experience to know whether legacy GRUB will let me dual boot, given the issues I've mentioned.  If you think it will, I'll be happy to try it!

Recommendations please!!!

Gra

---

### Post by gsmith45 on 2010-01-09
Slight update: On re-booting for the 3rd or 4th time (in attempt to get Windows to re-start), the pc immediately went to a command prompt that said "grub rescue>"

I couldn't figure out what to do with it, so I loaded Windows Recovery and ran fixmbr and then fixboot.   I am now back at step 1, where the pc boots directly into Windows!

Well, at least it's not raining today!

Any help appreciated.

G

---

### Post by kansasnoob on 2010-01-09
I just saw this, give me a while, maybe an hour or so, and I'll type up some specific instructions, OK?

There comes a point when a person just wants to be able to boot -PERIOD.

---

### Post by kansasnoob on 2010-01-09
First of all it's much easier for both of us if you can work while actually booted into Ubuntu so when you're ready please repeat the steps in post #17 that got you booting Ubuntu:

[http://ubuntuforums.org/showpost.php?p=8635950&postcount=17](http://ubuntuforums.org/showpost.php?p=8635950&postcount=17)

Now rather than go into a super long explanation of what we're doing, if you wonder, just for general information look here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I will include the steps here to edit the legacy grub menu.lst to add Windows, and we're going to use Startup Manager to simplify things for both of us:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

Since I don't know if you were using Startup Manager with grub2 we want to purge its configuration files so:

```
sudo apt-get --purge remove startupmanager
```

If it says "not installed so not removed" that's OK, we just wanted to be sure no old configuration files messed with us later on.

**Now, I've recently encountered some problems with software sources (especially with the Australian server) so lets do some package list verification.** Go to Synaptic Package Manager and click on Reload. When it's done click on Search and type **grub**, make sure that the packages grub, grub-pc, and grub-common are all available there.

If they're not we need to straighten out the software sources. Since we're in Synaptic I'd begin by just clicking on Settings > Repositories and change to the Main Server. Also be certain that all four of the Ubuntu repos are checked, but that the CD-ROM box is NOT checked.

Then click on reload again, and Search, type **grub** and check again to see that grub, grub-pc, and grub-common are all three there! **If not DO NOT proceed**, I'll need to see the output of:

```
cat /etc/apt/sources.list
```

If all three packages appear to be available we should be able to get down to it. **Please copy-n-paste all commands**, as I said I'm going to seriously limit the verbosity here:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub-pc grub-common
```

You will have to say Yes, you do want to remove all!

```
sudo apt-get install grub
```

```
sudo update-grub
```

You must say Yes (y) to a menu.lst!

```
sudo grub-install /dev/sda
```

Now we need a grub shell:

```
sudo grub
```

```
root (hd0,4)
```

```
setup (hd0)
```

You should see this:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Without the three yes and two succeeded responses something is wrong and you'll likely be unable to boot! If all looked right just run:

```
quit
```

```
sudo apt-get install startupmanager
```

And now we'll backup & edit the menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

```
sudo gedit /boot/grub/menu.lst
```

At the very bottom of the list you should see:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

Just below that we'll add Windows, when done the bottom of the list (including that previous line) should look like this:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added for a non-linux OS on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Be sure to Save, then File > Quit.

Note: I used Code tags only to keep it in the proper format, just copy-n-paste!

You can double check it with "cat /boot/grub/menu.lst" after saving.

Almost done, now we'll go to System > Administration > Startup Manager:

[http://www.psychocats.net/ubuntu/images/sum09.png](http://www.psychocats.net/ubuntu/images/sum09.png)

Make sure that the Show Bootloader Menu box is checked, and also set the timeout to the appropriate time in seconds, I suggest at least 10 seconds. You can also click on the Advanced tab and set the "number of kernels to display" (I recommend 2 so you always have one old kernel to boot if an update goes haywire), and you can uncheck the Memtest option (how often do you use that), I do not recommend removing the Recovery options.

If all went well that should be it. Always feel frre to PM me, just keep it brief and point me back to this thread or a new one if appropriate.

Sorry it took so long to get this done.

---

### Post by meierfra. on 2010-01-09
> See at the top of the results, the boot files for windows on sda1 are doubled. All three files appear twice. 

Actually, there is only one set of boot files, but due to a  bug in the boot info script, they are displayed twice. I fixed that bug today.

---

### Post by darkod on 2010-01-09
> **meierfra. said:**
> Actually, there is only one set of boot files, but due to a  bug in the boot info script, they are displayed twice. I fixed that bug today.

Thanks. Cheers. :)

---

### Post by kansasnoob on 2010-01-09
> **meierfra. said:**
> Actually, there is only one set of boot files, but due to a  bug in the boot info script, they are displayed twice. I fixed that bug today.

Awesome! If you're reading do you have any idea why grub2 doesn't play well with some systems?

I can find no real rhyme or reason to it. Most commonly Toshiba laptops and multi-disk arrangements, but not all Toshiba's or multi-disk arrangements.

I'm actually growing quite fond of grub2 but it's frustrating when it just doesn't work right.

---

### Post by meierfra. on 2010-01-09
> If you're reading do you have any idea why grub2 doesn't play well with some systems?

I think strange cases like this one are due to a miscommunication between Grub 2 and the Bios. (in other words, I have no clue what is going on)

To boot Windows with Grub2, Grub2 just calls the boot sector of the Windows partition, and from there on Windows takes over. 

After the "Fix MBR", the MBR just calls the boot sector of the Windows partition, and from there on Windows takes over. 

Since Windows starts booting, Grub2 clearly has been able to contact the boot sector, so I don't see any reason why "FixMBR" should allow Windows to boot.  

There have been similar cases with Legacy Grub, but only very few.  So your suggestion to switch to Legacy Grub is the right call. If that does not work, one has to run "FixMBR" again and add Ubuntu to the Windows Boot Loader.

> multi-disk arrangements,
I don't want to distract from the case at hand, so I'll respond via PM.

---

### Post by gsmith45 on 2010-01-10
Kansasnoob
First, let me say a huge thank you for the time and effort that you put into the posting earlier that talked me through how to move to legacy GRUB.  I really appreciate that you've taken time out of your day to help me (and probably many others).

Results:  I followed your instructions to the letter and it worked first time!  I can now boot into either Linux or Windows!  Fantastic.   I will try re-booting several times today, just to double check.  I cut and pasted the terminal log, so let me know if you want me to post a copy.

Couple of questions:
1)  If I receive an auto-update via UpdateManager, is there a danger of the system reverting itself to GRUB2?  If so, how can I stop it?
2)  I'd like the default boot to be into Windows, while my kids get used to Ubuntu.  Can I edit this easily, per the many postings on this subject?

Thank you once again for your help! (and to Darko for earlier suggestions)

Gra

---

### Post by kansasnoob on 2010-01-10
> **gsmith45 said:**
> Kansasnoob
First, let me say a huge thank you for the time and effort that you put into the posting earlier that talked me through how to move to legacy GRUB.  I really appreciate that you've taken time out of your day to help me (and probably many others).

Results:  I followed your instructions to the letter and it worked first time!  I can now boot into either Linux or Windows!  Fantastic.   I will try re-booting several times today, just to double check.  I cut and pasted the terminal log, so let me know if you want me to post a copy.

Couple of questions:
1)  If I receive an auto-update via UpdateManager, is there a danger of the system reverting itself to GRUB2?  If so, how can I stop it?
2)  I'd like the default boot to be into Windows, while my kids get used to Ubuntu.  Can I edit this easily, per the many postings on this subject?

Thank you once again for your help! (and to Darko for earlier suggestions)

Gra

> 1)  If I receive an auto-update via UpdateManager, is there a danger of the system reverting itself to GRUB2?  If so, how can I stop it?

Generally no. There is a remote possibility that an update of the package "grub-common" could break things, but it shouldn't.

If you want the package "grub-common" to never update you can go to Synaptic & Search for grub-common, then click on it to highlight it, then go to Package > Lock Version.

> 2)  I'd like the default boot to be into Windows, while my kids get used to Ubuntu.  Can I edit this easily, per the many postings on this subject?

Very easy. If you installed Startup Manager it will allow you to change default boot:

[http://www.psychocats.net/ubuntu/images/sum09.png](http://www.psychocats.net/ubuntu/images/sum09.png)

Just right where it says "Default operating system" click on the toggle thingy to the right and that will display all options, just select the one you want and close Startup Manager. It'll sit there and scroll back and forth while the changes are taking effect. That should be it.

Glad to hear you're booting :)

---

