---
title: "A GRUB problem - follow up"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by mikeody on 2010-01-12
I posted a thread a short while back and got some good advice. However I am not quite there yet !
I replaced XP with Windows 7 on a second hard drive. Install went well.
GRUB now shows the correct menu and I can now get into Ubuntu as usual [sigh of relief] but when I select the Windows option I get the 'Windows is Starting' message but it never happens.
Presumably I have to repair something in Windows but am unsure how.
I followed some previous advice that used the Windows 7 install disk and tried to repair the boot via a terminal with : "bootrec.exe /fixboot" and "bootrec.exe /fixmbr" but Windows 7 couldnt find the files.
Any further help would be great.
Thanks.

---

### Post by darkod on 2010-01-12
Since win7 was new install there is big chance the boot files were installed correctly. But depending on your setup, because the change from XP to 7 was done after installation of ubuntu and grub2, it might not know the correct information about your 7.
The first thing is to try in terminal:

sudo update-grub

Reboot and see how it goes.

---

### Post by oldfred on 2010-01-12
To see your exact configuration, please run this script, you can run from your working system or a liveCd:

Boot Info Script courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

Just saw darko's post, that often works for grub2, but if not then run script.

---

### Post by mikeody on 2010-01-12
Thaks 'old Fred'.
Results are :

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70527052

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe35fe35

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   300,511,889   300,511,827  83 Linux
/dev/sdb2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sdb5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0C2C5EF22C5ED674" TYPE="ntfs" 
/dev/sdb1: UUID="6c203b65-3340-49a4-a323-cdcc06ad05ae" TYPE="ext4" 
/dev/sdb5: UUID="b6a485c2-3625-412f-a1fd-6401829e0263" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b6a485c2-3625-412f-a1fd-6401829e0263 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by kansasnoob on 2010-01-12
Well I see something interesting:

> => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.

Windows is on sda1 so why is grub2 looking on that drive for /boot/grub?

Well this:

> Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM **/boot/grub/core.img**

I've never seen that before.

Anyway the first thing I'd try is, while booted into your installed Ubuntu:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdb
```

```
sudo update-grub
```

Be sure and wait for it to say done.

Then reboot and see what happens. I kind of have doubts but it may work.

Otherwise we may need to figure out how to remove the **/boot/grub/core.img** from the Windows boot files/directories. I'll have to puzzle on that for a while.

---

### Post by kansasnoob on 2010-01-12
**[COLOR="Red"]Consider this mostly just me thinking out loud here.[/COLOR]** If that doesn't work, and like I said I have serious doubts, you should be OK to just have a look around in the Windows files.

I wish I had a Win 7 to look around in but I don't. In Win XP I find all of the boot files in the folder Windows XP. Just remember you're only looking for **/boot/grub/core.img**.

To be able to have full read & write capabilities in Windows you need to install ntfsprogs in Ubuntu:

```
sudo apt-get install ntfsprogs
```

And, at least in my experience, that will normally let Nautilus mount any and all Windows files/directories.

There is a remote possibility that you may also have to install nautilus-gksu so you can "open as administrator" to be able to trash that file if you find it. If needed:

```
sudo apt-get install nautilus-gksu
```

There's a reason it's not installed by default. That gives you root privileges and you can really hose things if you're not careful!

Anyway just remember you are only looking for **/boot/grub/core.img**. It does not belong there.

---

### Post by mikeody on 2010-01-12
Thanks for all that.

You were right - the first set of code didnt work. All returned 'happy' responses but I am still unable to boot into Windows 7 via GRUB.

I had no problems in finding "boot/grub/core.img". It is sitting in a folder called boot/grub that is alongside a folder called "Boot" - both at root level [C: in Windows7].

The boot/grub/core.img is a small file [26KB] amongst a huge number of other files within boot/grub.

Do you think I should rename the core.img file and see what happens ?

---

### Post by mikeody on 2010-01-12
Have renamed the file and rebooted.
Same result.
I could always wipe the Windows 7 disk and reinstall. Still may need some sorting out but it should give me a valid MBR in Windows 7.
Any thoughts on that ?

---

### Post by mikeody on 2010-01-13
Am continuing to muddle on with this issue - getting closer to a complete reinstall of Windows7.
Am still getting a successfull boot of Karmic, but Windows7 is not booting - just asking if I should 'repair' - which doesnt work !
So has anyone any thoughts on the 'Boot Info Summary' posted earlier ?
If I end up reinstalling windows7 how should I go about that and what can I expect to happen to GRUB etc ? Do I disconnect the disk that contains Karmic during the windows7 re-install or what ? I am desperate to keep  Karmic 'safe'.
Help please.

---

### Post by meierfra. on 2010-01-13
Seems like  a  plain Window 7 Problem.  Your Window 7 CD  might  do better if Win 7  is on the boot drive. So try this:

Install a Windows Typ MBR on your Window 7 drive:

```
sudo apt-get install lilo
```
(ignore the warning you are getting, just press enter)

```
sudo lilo -M /dev/sda mbr
```

Reboot, but set  the  bios to boot from your 40GB  Window 7 drive. 
Your computer should now try to boot into Window 7 but get stuck at  "Windows starting". (If you are able to boot into Window 7, ignore the rest of the instruction and come back here for further advice)

Next boot from your Windows 7 CD (But make sure that your  Windows drive appears before the Ubuntu drive in the Bios boot order.)
Choose "Repair computer". If the CD offers your to fix a problem,  say yes.  Otherwise, instead of going to the command prompt, choose "Start up Repair".  You might have to run Start Up Repair a few times, before it corrects all the problems.

You should also run "chkdsk" from the "Command prompt" on the Win 7 CD:
Type

```
diskpart
list volume

```
to determine the Drive letter of your Window 7 partition. Then

```
exit
chkdsk /f C:
```
(but use the actual drive letter)
If "chkdsk /f C:" found some errors, run it again.

Also create the file bcd.txt, which we might need for further trouble shooting
```
bcdedit /store C:\boot\bcd > C:\bcd.txt
```
(again use the actual drive letter)

Reboot and see whether you can boot into Window 7.

If you are still not able to boot into Window 7, boot into  Ubuntu (set the bios to boot from the Ubuntu drive).

Open  the file bcd.txt via

```

sudo mount /dev/sda1 /mnt
gedit /mnt/bcd.txt
```
and post the content of that file.

---

### Post by mikeody on 2010-01-13
Thanks meierfra for all that - I can report some progress.
I have :
1. Made the LILO changes as recommended
2. Changed boot order to Windows disk
3. Booted and was given option to 'StartUpRepair'
4. StartUpRepair took ages and ended up saying 'couldnt be repaired'
5. I rebooted and Windows7 ran perfectly !
6. Switched boot order back to Ubuntu disk
7. ReBooted - GRUB menu OK and Ubuntu accessed OK
8. When I selected Windows on the GRUB Menu though it hangs on 'Starting Windows'

Havnt gone any further yet.
Any thoughts ?

---

### Post by meierfra. on 2010-01-13
>  I rebooted and Windows7 ran perfectly !
 
When I selected Windows on the GRUB Menu though it hangs on 'Starting Windows'


Well, it seems you are having a grub problem after all. 
Anyway, you are now able to boot into both  OSs by switching  the boot order.  

I don't have much hope that you  will be able to boot Windows 7 from the Grub2 menu. but  let's try.

Boot into Ubuntu, open a terminal and type

```
gksudo gedit /boot/grub/device.map
```
Change the file so that it looks like

(hd[COLOR="Red"]1[/COLOR]) /dev/sda
(hd[COLOR="Red"]0[/COLOR]) /dev/sdb

Save  and close the file. Back in the terminal:


```
gksudo gedit /etc/grub.d/40_custom
```

Add this to the end file

menuentry "Windows7 (no map)" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}

menuentry "Windows 7 (both maps)" {
insmod ntfs
set root=(hd1,1)
drivemap -s (hd0) (hd1)
chainloader +1
}

menuentry "Windows 7 (0 to 1)" {
insmod ntfs
set root=(hd1,1)
drivemap (hd0) (hd1)
chainloader +1
}

menuentry "Windows 7 (1 to 0)" {
insmod ntfs
set root=(hd1,1)
drivemap (hd1) (hd0)
chainloader +1
}

Save and close the file.

Then

```
sudo update-grub2
```

Reboot. You will have five different entries for Windows 7. Try them all.
If one of them works, you just have to remove all the other entries from your grub menu.


If none of them works, boot into Windows 7. Click on Start. Press "Ctrl+Shift+Enter" to open a commmand prompt with administrative rights. 

Type```
bcdedit > C:\bcd.txt
```

and post the content of the file "C:\bcd.txt"

In case you can't get Window 7 to boot from the Grub2 menu, there are still a couple of  other options:  

1) Add Grub 2 to the Windows 7 boot loader.
2) Use Legacy Grub instead of Grub 2.

But we'll worry about that later.

---

### Post by meierfra. on 2010-01-13
PS.  a few more entries which of a theoretical chance to work

menuentry "Windows7 (mbr, no map)" {
set root=(hd1)
chainloader +1
}

menuentry "Windows 7 (mbr,both maps)" {
set root=(hd1)
drivemap -s (hd0) (hd1)
chainloader +1
}

menuentry "Windows 7 (mbr,0 to 1)" {
set root=(hd1)
drivemap (hd0) (hd1)
chainloader +1
}

menuentry "Windows 7 (mbr,1 to 0)" {
set root=(hd1)
drivemap (hd1) (hd0)
chainloader +1
}

---

### Post by oldfred on 2010-01-13
I am pretty sure one or more of meierfra. posts will work. And it depends on the device.map drive order. If your orginal device.map showed both drives and windows is on the second drive this should also work.

Change from this that says the windows is on the first drive
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
    drivemap -s (hd0) ${root}
    chainloader +1
}

to this that makes windows on the second drive:
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd[COLOR=Red]1[/COLOR],1)
    search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
    drivemap -s (hd[COLOR=Red]1[/COLOR]) ${root}
    chainloader +1
}

The drivemap -s command is just a switch or swap to reverse the entry. I have seen both the fixed (hd0) (hd1) entries and order should not matter. It now seems grub always writes the ${root} device to swap with (hd0) which normally does not do anything as root is hd0.

---

### Post by meierfra. on 2010-01-13
> set root=(hd1,1)
search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
drivemap -s (hd1) ${root}
chainloader +1

The correct entry actually should be

```
set root=(hd1,1)
search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
drivemap -s (hd[COLOR="Red"]0)[/COLOR] ${root}
chainloader +1
```

Windows needs to be mapped to (hd0) (since Windows will look for the boot files on (hd0). That entry will be generated by "os.prober" once the device.map is corrected.

But that entry is essentially equivalent to 

```
set root=(hd[COLOR="Red"]0[/COLOR],1)
search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
drivemap -s (hd[COLOR="Red"]0)[/COLOR] ${root}
chainloader +1
```

since the search command will overwrite the preceding "set root=(hd0,1)".
So the OP is already using the correct entry.  

 I believe that there is some kind of miscommunication between Grub2 and the Bios.  I have seen some very rare case with Legacy Grub, where feeding the wrong information to  Grub actually ended up booting Windows. 

So that's what I'm trying to do:  Feed some wrong information to Grub2 in the hope its ends up as the correct information in the Bios.  Doesn't make much sense, but sometimes this actually works.

---

### Post by wkulecz on 2010-01-13
I had Win7 RC1 32-bit and 64-bit installed dual boot.  Then I installed Kubuntu 9.04 and my windows boot broke, although Kubuntu booted fine.  I then reinstalled Win7RC1 and could boot Windows 7 fine again.  Booted the live CD and reinstalled Grub and can now dual boot Kubuntu 9.04 and Win7RC1.  Win7RC1 was a throwaway test system for me but had it been something I needed it would have been a very bad situation indeed!

IMHO changing from Grub to Grub2 when Win7 is just getting common is a very bad idea unless it fixed the issue I had with Grub and Win7RC1.  This thread and other tales of dual boot woe suggest it didn't fix anything and makes repairs more difficult.

--wally.

---

### Post by mikeody on 2010-01-13
Thanks for everything guys.
Am working for the next couple of days so wont be able to follow up on the last two posts.
So far meierfra's first set of options havnt solved things but there are now more to try !
Will post again as soon as I get back to my PC.
Thanks again,
Mike

---

### Post by meierfra. on 2010-01-14
The fact that you were able to boot Win 7 after your fixed the MBR on the Win 7 drive might have led me down the wrong path. In fact, I now believe that the path kansasnoob was leading  you was the correct one:  

> bootmgr /[COLOR="Red"]Boot[/COLOR]/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /[COLOR="Red"]boot[/COLOR]/grub/core.img


You problem  isn't the file "/boot/grub/core.img", but you have a "Boot" and "boot" folder. The "boot" folder must have been created during some attempt to reinstall grub. Linux is case sensitive  and so it it has no problem with "Boot" and "boot". But Window is case insensitive and might get confused.

 I suggest to rename the "boot" folder. Open a terminal in Ubuntu and type

```
sudo mount /dev/sda1 /mnt
sudo mv /mnt/boot /mnt/boot.moved
```

---

### Post by mikeody on 2010-01-15
YES !!!! There were 2 'boot' folders over in Windows 7 - boot and Boot. The rename immediately had an effect on teh GRUB menu as for the first time I started to see 'Windows7 Loader' as opposed to 'NT etc etc'.
Then I ran the Windows7 StartUP Repair utility about 4 times and bingo !
I can now get Karmic AND Windows 7 via the GRUB menu.
Have rebooted and restarted a dozen or so times since and all SEEMS to be OK - but watch this space if it falls over again !
Thanks to meierfra and all the others who have helped out - without you guys I woudld have been in a lunatic asylm by now !! Keep up teh good work.
Thanks again.

---

### Post by meierfra. on 2010-01-16
> I can now get Karmic AND Windows 7 via the GRUB menu.

Great.  You might consider to email a bug report to [email]linux-ntfs-dev@lists.sourceforge.net[/email]. 

The linux-ntfs drivers lets you create directories  whose  name only differ by capitalization.  And that seems to lead to confusions on the Windows side. 
I tried  the same thing on a Fat32 partition. I had a "/Boot" directory  and no "/boot". But "mkdir /boot"  still resulted in  "File exists".   NTFS partitions should behave the same way. 


PS:  Sorry  for taking this case away from kansasnoob.  He'll probably would have solved this two days ago

---

### Post by kansasnoob on 2010-01-16
> **meierfra. said:**
> Great.  You might consider to email a bug report to [email]linux-ntfs-dev@lists.sourceforge.net[/email]. 

The linux-ntfs drivers lets you create directories  whose  name only differ by capitalization.  And that seems to lead to confusions on the Windows side. 
I tried  the same thing on a Fat32 partition. I had a "/Boot" directory  and no "/boot". But "mkdir /boot"  still resulted in  "File exists".   NTFS partitions should behave the same way. 


PS:  Sorry  for taking this case away from kansasnoob.  He'll probably would have solved this two days ago

You did good, I could see something wasn't quite right but I wasn't sure how to approach it anyway.

Then I got bogged down with iso testing, hardware problems, and filing taxes.

You know 100 times more than I ever will about boot problems and how to fix them. I always read your posts when I see them in hopes I can learn something.

I would not have known how to do this:

```
sudo mount /dev/sda1 /mnt
sudo mv /mnt/boot /mnt/boot.moved
```

---

