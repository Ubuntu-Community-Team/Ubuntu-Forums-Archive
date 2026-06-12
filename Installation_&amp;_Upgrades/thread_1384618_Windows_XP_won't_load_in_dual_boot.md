---
title: "Windows XP won't load in dual boot"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Fuzztop on 2010-01-18
I am a novice, so please help.

I managed somehow to successfully install a dual boot with Ubuntu 9.02 and Windows XP. Ubuntu was on a PATA drive and the WinXP was on a SATA drive. The SATA drive was configured to boot first. As I was having problems with Ubuntu I booted into WinXP, re-formatted the PATA drive, then restarted the computer and installed Ubuntu 9.10. It all went well.

I rebooted the machine and the following message was on the screen:

GRUB Loading stage1.5

GRUB Loading, please wait....

Error 17

I rebooted, changed the boot order so that the PATA disk (Ubuntu) started first, then the SATA(WinXP).  Ubuntu loaded up the dual boot screen.  I chose WINXP, but I was greeted with a black screen.

I rebooted again and chose to load Ubuntu, which it did without a hitch.

Can anyone tell me what I should do to restore my access to WinXP?  Or should I start again? If so, how?

Thank you

---

### Post by audiomick on 2010-01-18
Hi.
I seriously doubt that I will be able to get you through that, but as a first step, you could organize some more info for those that could.
Go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and work through it, and post the RESULTS.TXT file back here.

---

### Post by Fuzztop on 2010-01-18
Thank you.

Here is the Results.txt (For your information, sda is the disk holding Ubuntu. sdd1 holds the WinXP OS)

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf22af22a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,468,944   153,468,882  83 Linux
/dev/sda2         153,468,945   160,071,659     6,602,715   5 Extended
/dev/sda5         153,469,008   160,071,659     6,602,652  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ca88ec0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   398,283,479   398,283,417   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04a73ad0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   398,283,479   398,283,417   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05090508

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sdd2         163,846,935   488,392,064   324,545,130   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="63a8d765-b517-4b3a-92d8-d47ebc585235" TYPE="ext4" 
/dev/sda5: UUID="f749c85b-8104-49b0-babd-d4d073c0b3be" TYPE="swap" 
/dev/sdb1: UUID="46787D47787D3731" LABEL="Back Up" TYPE="ntfs" 
/dev/sdc1: UUID="90CCE266CCE245D6" LABEL="MY DOCUMENTS" TYPE="ntfs" 
/dev/sdd1: UUID="04043D75043D6B36" TYPE="ntfs" 
/dev/sdd2: UUID="5030B9F930B9E65E" LABEL="PHOTOS" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 63a8d765-b517-4b3a-92d8-d47ebc585235
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 63a8d765-b517-4b3a-92d8-d47ebc585235
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=63a8d765-b517-4b3a-92d8-d47ebc585235 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 63a8d765-b517-4b3a-92d8-d47ebc585235
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=63a8d765-b517-4b3a-92d8-d47ebc585235 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 63a8d765-b517-4b3a-92d8-d47ebc585235
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=63a8d765-b517-4b3a-92d8-d47ebc585235 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 63a8d765-b517-4b3a-92d8-d47ebc585235
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=63a8d765-b517-4b3a-92d8-d47ebc585235 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sdd1)" {
    insmod ntfs
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 04043d75043d6b36
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=63a8d765-b517-4b3a-92d8-d47ebc585235 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f749c85b-8104-49b0-babd-d4d073c0b3be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sdd1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  d0 3a a7 04 00 00 00 01  |.........:......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 99 52 bd 17 00 00  |......?....R....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh

---

### Post by phillw on 2010-01-18
Hi, get your system so it can boot the ubuntu system, with the XP drive connected.

The problem is.... there isn't a Ubuntu 9.02...

So, I don't know which grub you are running.

Got to Terminal (Applications --> Accessories --> Terminal)
```
grub-install -v
```It will show > grub-install (GNU GRUB [COLOR=#ff0000]1[/COLOR].xx.......)Or 
It will show > grub-install (GNU GRUB [COLOR=#ff0000]0[/COLOR].xx.......)The important thing being the 1 or 0  - A zero means you are running Grub Legacy, a number one means you are on Grub2 (Confusing, i know.. - But important).

Then head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
to get your XP area back.

/edit you're on Grub2 !!! that thread will get XP back for you !!

Regards,

Phill.

---

### Post by Fuzztop on 2010-01-18
My mistake, Phill,
It was 9.04.

From the instructions you sent and the links, I have Grub 2.

Having read through the instructions on the link, I think this will mean I will be able to boot up WinXp again, but am I right in assuming that the dual boot facility will be lost?

---

### Post by phillw on 2010-01-18
That's odd, as 9.04 comes with Grub Legacy Hmmm.. but you're deffinately on Grub2 !!

Once Ubuntu is booted up you should simply be able to go to terminal and type ```
sudo update-grub
``` And grub will go find XP for you and add it to the list.

Report back how you get on.

Regards,

Phill

---

### Post by audiomick on 2010-01-18
There is a grub legacy in amongst that as well
```
=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #1 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb
=> No known boot loader is installed in the MBR of /dev/sdc
[COLOR="Red"]=> Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]
```

The windows wont boot because the MBR of sdd has the old grub in it, I think, but I am not sure. It is a bit too complicated for me :(

Did Phillw's advice help?

---

### Post by phillw on 2010-01-18
Crikey, how many disks does the OP have ?!!!

May be one for presence, this one. I'm reasonable with Grub2, but haven't got the experience he, drs305, darkod etc. have with it.

I'm pretty sure that Grub2 should be able to find everything ... Not seen a setup like that one, though !!

Phill.

---

### Post by audiomick on 2010-01-18
> **phillw said:**
> Not seen a setup like that one, though !!

yeah, it is good, isn't it.

I've just been looking at his output for about 20 minutes, and as far as I can see, it is all there:confused:

@ Fuzztop, firstly and by the way, if you use the # button in the posting window to put code tags around your output, it puts it in a box with a scroll bar, which keeps the post more compact.

As I said, to me, it looks like avery thing is there. If you are booting to sda it should be finding the Grub 1.97 which has an entry pointing to the windows install on sdd1.

I fear you will have to wait for someone a bit more experienced. Unfortunately, none of the people Phill mentioned seem to be here at the moment.

---

### Post by meierfra. on 2010-01-18
Everything seems to be configured correctly.  Lets see whether Grub can see your Windows partition at boot up. At the grub menu at boot up press "c" to get to the "grub>" prompt

Type 

```

insmod ntfs
ls
```
Does that detect all your partitions?

Also try

```
ls (hd3,1)
ls (hd3,1)/
```

Does the  output match your windows XP  partition?  If not, try "1" and "2" in place of the "3"'s.

What is the output of 

```
search --no-floppy --fs-uuid  04043d75043d6b36
```



Finally, lets  see whether you can boot XP if you install a Windows Style MBR to /dev/sdd:

```
sudo apt-get install lilo
```
(Ignore the message you will get, just press "enter")
```
sudo lilo -M /dev/sdd mbr
```

Then reboot, with the bios set to boot from your  250GB Windows XP drive.


Does that boot you into XP?

---

### Post by Fuzztop on 2010-01-19
Thank you for your suggestions. I am still attempting to follow the "restore the Windows XP Bootloader" instructions that PhilW pointed me to.  I managed to lose my Ubuntu boot up too. I am reinstalling Ubuntu at the moment and will follow your other suggestions when I get there - sometime tomorrow or Thursday, I expect.

---

### Post by Fuzztop on 2010-01-21
Hello Meierfra,

I followed your instructions

Code:
insmod ntfs
ls
Does that detect all your partitions? [COLOR="Red"]Yes[/COLOR]

Also try

Code:
ls (hd3,1)
ls (hd3,1)/
Does the output match your windows XP partition? If not, try "1" and "2" in place of the "3"'s. **[COLOR="red"]Yes[/COLOR]**

What is the output of 

Code:
search --no-floppy --fs-uuid  04043d75043d6b36 [COLOR="red"]**hd3,1**[/COLOR]


Finally, lets see whether you can boot XP if you install a Windows Style MBR to /dev/sdd:

Code:
sudo apt-get install lilo
(Ignore the message you will get, just press "enter")
Code:
sudo lilo -M /dev/sdd mbr
Then reboot, with the bios set to boot from your 250GB Windows XP drive.


Does that boot you into XP? [COLOR="red"]**Yes**[/COLOR]

So thank you. My computer now boots up into Windows XP.  I am greatly relieved as I was expecting I would have to reinstall the WinXP OS, which is a really tedious.

However, I have lost my boot into Ubuntu, unless I go into the BIOS and alter the boot order.  Is there a safe way I can set up a dual booting menu?

---

### Post by oldfred on 2010-01-21
If these are all SATA drives you should be able to control which drive boots with a setting in BIOS. You also should have a one time boot choice just as the BIOS loads to choose a different drive to boot from.

You want to have the MBR of the drive to boot to the operating system on that drive. You will want to have Ubuntu boot set in the BIOS as it will then let you also boot windows. With many drives drive order, device.map and what boot loader is installed where all become important. I regularly run the boot info script on my desktop system just to understand where things are. 

Try setting the drive that is sda to boot and see if it works. Then run 
sudo update-grub 
to see if it adds windows and that boot works.

---

### Post by meierfra. on 2010-01-21
Well, everything seems to be configured correctly, grub at boot up detects the Windows partition and there is no problem with Windows XP.  So I have no clue what could going wrong. 

But lets see whether you can boot XP by chainloading the MBR rather than the boot sector. Open the file /etc/grub.d/40_custom via


```
gksudo gedit /etc/grub.d/40_custom
```

and add this to the end of the file:

title "Windows XP both maps"
drivemap -s (hd0) (hd3)
chainloader (hd3)+1

title "Windows XP no maps"
chainloader (hd3)+1

title "Windows XP 03"
drivemap  (hd0) (hd3)
chainloader (hd3)+1

title "Windows XP 30"
drivemap  (hd3) (hd0)
chainloader (hd3)+1


Save the file. The run

```
sudo update-grub
```

Reboot from the Ubuntu drive. Try  each of the four new entries on menu.lst. If one of them works, just delete the others from 40_custom.  If none of them work, come back here and report any error messages you got.

---

### Post by Fuzztop on 2010-01-23
I edited the 40_custom file as you said, but this has not altered the menu I get when I boot into the Ubuntu drive.  Among the Ubuntu options there remains one for Windows XP on sdd1, which fails to boot into Windows.

---

### Post by kansasnoob on 2010-01-23
> **Fuzztop said:**
> I edited the 40_custom file as you said, but this has not altered the menu I get when I boot into the Ubuntu drive.  Among the Ubuntu options there remains one for Windows XP on sdd1, which fails to boot into Windows.

After editing /etc/grub.d/40_custom in Gedit were you sure to click on Save before closing?

Then did you run:

```
sudo update-grub
```

And wait until it said done?

To see what the /etc/grub.d/40_custom looks like now you can use the "cat" prefix like:

```
cat /etc/grub.d/40_custom
```

Likewise after running "update-grub" you can check the new grub.cfg with:

```
cat /boot/grub/grub.cfg
```

I always check files after editing because I'm old and prone to making silly mistakes :)

---

### Post by Fuzztop on 2010-01-23
[COLOR=DarkRed]I have checked and I did save the work and used update-grub.

The grub.cfg reads as follows:[/COLOR]

paul@study:~$ cat /boot/grub/grub.cfg
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set cf3cc437-9f88-448b-8fe8-25d43445c1ed
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cf3cc437-9f88-448b-8fe8-25d43445c1ed
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=cf3cc437-9f88-448b-8fe8-25d43445c1ed ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cf3cc437-9f88-448b-8fe8-25d43445c1ed
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=cf3cc437-9f88-448b-8fe8-25d43445c1ed ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cf3cc437-9f88-448b-8fe8-25d43445c1ed
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cf3cc437-9f88-448b-8fe8-25d43445c1ed ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cf3cc437-9f88-448b-8fe8-25d43445c1ed
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cf3cc437-9f88-448b-8fe8-25d43445c1ed ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sdd1)" {
    insmod ntfs
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 04043d75043d6b36
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

title "Windows XP both maps"
drivemap -s (hd0) (hd3)
chainloader (hd3)+1

title "Windows XP no maps"
chainloader (hd3)+1

title "Windows XP 03"
drivemap (hd0) (hd3)
chainloader (hd3)+1

title "Windows XP 30"
drivemap (hd3) (hd0)
chainloader (hd3)+1

### END /etc/grub.d/40_custom ###
paul@study:~$

[COLOR=DarkRed]But the list that appears at boot up does not contain the four windows boot loaders that follow the line: ### BEGIN /etc/grub.d/40_custom ###[/COLOR]

---

### Post by kansasnoob on 2010-01-23
Would you please also post the output of:

```
cat /etc/grub.d/40_custom
```

Maybe something is wrong with the exec tail.

---

### Post by darkod on 2010-01-23
Excuse me for jumping in, but in your results in post #3 you have grub2 on /dev/sda and grub1 /dev/sdd.
It's a dumb question but are you sure you are booting the correct grub?

---

### Post by kansasnoob on 2010-01-23
> **darkod said:**
> Excuse me for jumping in, but in your results in post #3 you have grub2 on /dev/sda and grub1 /dev/sdd.
It's a dumb question but are you sure you are booting the correct grub?

I think meierfra took care of that in post #10.

Off topic but have you seen this one:

[http://ubuntuforums.org/showthread.php?t=1388577](http://ubuntuforums.org/showthread.php?t=1388577)

I almost wet myself :P

---

### Post by meierfra. on 2010-01-23
My bad. I must have been asleep when I wrote my last post. It needs to be

[COLOR="Red"]menuentry[/COLOR] "Windows XP both maps" [COLOR="Red"]{[/COLOR]
drivemap -s (hd0) (hd3)
chainloader (hd3)+1
[COLOR="Red"]}[/COLOR]

[COLOR="Red"]menuentry[/COLOR] "Windows XP no maps"[COLOR="Red"] {[/COLOR]
chainloader (hd3)+1
[COLOR="Red"]}[/COLOR]

[COLOR="Red"]menuentry[/COLOR] "Windows XP 03"[COLOR="Red"] {[/COLOR]
drivemap (hd0) (hd3)
chainloader (hd3)+1
[COLOR="Red"]}[/COLOR]

[COLOR="Red"]menuentry[/COLOR] "Windows XP 30"[COLOR="Red"] {[/COLOR]
drivemap (hd3) (hd0)
chainloader (hd3)+1
[COLOR="Red"]}[/COLOR]

(So replace "title" by "menuentry" and place the code in curly braces.)

Sorry,:redface:

---

### Post by Fuzztop on 2010-01-23
I have edited the 40_custom as requested.  The four Windows options appear in the menu when I boot up, but none of them load Windows.

Here is the 40_custom:

#paul@study:~$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows XP both maps" {
drivemap -s (hd0) (hd3)
chainloader (hd3)+1
}

menuentry "Windows XP no maps" {
chainloader (hd3)+1
}

menuentry "Windows XP 03" {
drivemap (hd0) (hd3)
chainloader (hd3)+1
}

menuentry "Windows XP 30" {
drivemap (hd3) (hd0)
chainloader (hd3)+1
}

#

---

### Post by Fuzztop on 2010-01-23
Ignore the # at the beginning and the end of 40_custom.  I was trying to create a scroll box.  I am such a novice.

---

### Post by Fuzztop on 2010-01-23
Because of all the trouble I am having with the dual boot, would it not be easier to start the installation of Ubuntu again? 

If so, making the SATA (sdd) the first boot drive (Windows), how can I make sure that Ubuntu has not left on the drive any files that will be picked up by the new Ubuntu installation?

---

### Post by meierfra. on 2010-01-23
```
but none of them load Windows.
```
Oh well , I didn't have much hope, but  thought it's worth a try.
Just deleted those fours entries from "40_custom"

Did you still get the "black screen" or something else? 


> would it not be easier to start the installation of Ubuntu again? 
You  can give it a try,  But, since Ubuntu is working perfectly, I really don't think it will make any difference. Or are you planning to install Ubuntu to a different drive?

> If so, making the SATA (sdd) the first boot drive (Windows),
You don't have to reinstall Ubuntu for this, just Grub.

So lets see what happens if  you  install Grub to MBR of the Windows drive

```

sudo grub-install  /dev/sdd
```

Then boot from sdd and see what happens.

(If needed you still will be able to get into Ubuntu by booting from the Ubuntu drive, and you  can fix the MBR of sdd again using "sudo lilo -M /dev/sdd mbr"

---

### Post by kansasnoob on 2010-01-23
Consider this just thinking out loud for the moment but when you say:

> Because of all the trouble I am having with the dual boot, would it not be easier to start the installation of Ubuntu again?


I'm sensing that you're getting frustrated and that's certainly understandable. I've been there :)

Now, since we've come this far I'd definitely try what meierfra suggested:

```
sudo grub-install  /dev/sdd
```

And possibly:

```
sudo update-grub
```

One last time, and if that doesn't get it I'm 95% sure that we could get you booting by reverting you to legacy grub. I sometimes think I wait too long before suggesting that, and other times I think I offer that option too soon.

I wrote a HowTo if you're interested:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Since it's something new to you I'd be glad to customize the commands for your machine and write a Windows entry to add to the menu.lst. If you decide to go that way feel free to click on my user name and send me a brief PM pointing me back to this thread.

While I find playing with grub2 intriguing and even fun I know some people just want to be able to boot and get on with things, and I'd much rather help someone revert bootloaders than have them give up on Ubuntu altogether.

---

### Post by meierfra. on 2010-01-23
> sudo update-grub
??? It will generated the exact same menu as before.

---

### Post by kansasnoob on 2010-01-23
> **meierfra. said:**
> ??? It will generated the exact same menu as before.

I've just made that a habit after making any changes. I know it's overkill.

It won't break anything :D

---

### Post by Fuzztop on 2010-01-24
> **meierfra. said:**
> ```
but none of them load Windows.
```
Oh well , I didn't have much hope, but  thought it's worth a try.
Just deleted those fours entries from "40_custom"

Did you still get the "black screen" or something else? 



You  can give it a try,  But, since Ubuntu is working perfectly, I really don't think it will make any difference. Or are you planning to install Ubuntu to a different drive?


You don't have to reinstall Ubuntu for this, just Grub.

So lets see what happens if  you  install Grub to MBR of the Windows drive

```

sudo grub-install  /dev/sdd
```

Then boot from sdd and see what happens.

(If needed you still will be able to get into Ubuntu by booting from the Ubuntu drive, and you  can fix the MBR of sdd again using "sudo lilo -M /dev/sdd mbr"
Thank you for all your help.  I have set the Windows drive as the first drive. I installed GRUB to its MBR and now the menu appears and boots happily into either Ubuntu or Windows, whatever I choose.

Can I check, just to be sure.  The instruction was to install the GRUB on /dev/sdd, even though Windows is on the sdd1 (the first partiion of sdd)?

---

### Post by kansasnoob on 2010-01-24
> The instruction was to install the GRUB on /dev/sdd, even though Windows is on the sdd1 (the first partiion of sdd)?

Yes that was right. Meierfra's amazing at this isn't he?

---

### Post by meierfra. on 2010-01-24
> and boots happily into either Ubuntu or Windows, whatever I choose.
Great.   I didn't had much hope that installing Grub to the MBR of the Windows drive would work, but I didn't want to give up on Grub 2 yet.


> The instruction was to install the GRUB on /dev/sdd, even though Windows is on the sdd1 (the first partiion of sdd)?
Definitely. Installing Grub to /dev/sdd1 overwrites the Windows boot sector and you would not have been able to boot Windows anymore.

But I don't really understand why installing Grub to the  MBR of Windows drive works, but installing Grub to the MBR of Ubuntu drive does not.

I think  that the "drivemap" command in Grub2 is buggy.    That's why I made a fool out of myself and tried  those  four different "drivemap" versions in post 14. I was hoping that two wrongs would make a right. (That actually works sometimes, but only very  rarely)

Installing grub to the MBR of the Windows drive means that Grub2 does not need to map the Windows drive.  So this is some indication that really the "drivemap" command  is  to blame. I'll do some googling to see whether I can find similar cases and might file a bug report (if there isn't one already)

---

### Post by oldfred on 2010-01-24
I would swear that I have seen drivemap work, but sometimes it does not seem to be consistent. 

On my desktop my drives are in order plugged into the SATA ports, but in BIOS I can choose boot order and they can be in any order after the one I want to boot. I am wondering if the drive order seen by grub is not the SATA port order but the BIOS boot order, although only the first drive should matter for boot order?

---

### Post by meierfra. on 2010-01-24
> I am wondering if the drive order seen by grub is not the SATA port order but the BIOS boot order,
Yes, Grub gets  the boot order from the BIOS.  Thats is one of the reason Grub 2 uses "UUID's". With Grub2,  you can change the boot order in the bios, and you still should be able to boot all your OS's (but of  course Grub must be install to the MBR of the boot drive)

The entry

set root=(hd3,1)
search --no-floppy --fs-uuid --set 04043d75043d6b36
drivemap -s (hd0) ${root}
chainloader +1


should really work regardless of the boot order, since the search command will automatically determine the correct root.  (But just to make sure, I had asked the OP for the output of the "search" and the "ls" command. Search returned (hd3,1) and Windows was on (hd3,1).  So Grub was looking at the correct place for Windows.


The "drivemap" command serves a  different purpose.  Windows XP is hard coded to look at the boot drive for its boot files.  So if you boot from the Ubuntu drive, XP will look  on the Ubuntu drive for its boot files, and booting fails.  XP gets the information about the boot drive from the Bios. The "drivemap" command will change  the message XP gets  from the BIOS, so that XP  will think that the XP drive is the boot drive.

The "drivemap" trick usually works just fine, but maybe it failed in in this case.

---

### Post by Fuzztop on 2010-01-24
Thank you to all who have helped me to get my dual boot up and running, with particular thanks to Meierfra.

---

