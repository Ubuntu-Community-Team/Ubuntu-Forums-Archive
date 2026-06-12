---
title: "Fix Windows MBR without Removing Grub"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by missChex on 2009-11-22
I have a Vista/Ubuntu dual boot on my laptop. The first time I installed Ubuntu, I couldn't boot into Vista. I fixed that by using the Vista Recovery disk to repair the MBR. When I rebooted, grub disappeared. My friend fixed it and all was well.
Five days later, I'm using Ubuntu and I was prompted to update some parts of it by the Update Manager. When I rebooted, grub wouldn't let me boot into Vista. So here's my question: Is there a way to fix the Windows MBR in the Ubuntu terminal without removing Grub?

Thanks in advance.

---

### Post by darkod on 2009-11-22
No, you can't. You can have either windows bootloader on the MBR (which can't boot any linux, not by default) or grub.
I think you should try to troubleshoot why grub can't boot your vista because when you did the updates I guess grub was updated too and it seems the same problem as the first time came back.
Does it give you any specific error message? Is vista installed on the first partition of the HDD?
And which version of Ubuntu do you have, because 9.10 comes with grub2 and earlier versions with grub1.

---

### Post by missChex on 2009-11-22
> **darkod said:**
> No, you can't. You can have either windows bootloader on the MBR (which can't boot any linux, not by default) or grub.
I think you should try to troubleshoot why grub can't boot your vista because when you did the updates I guess grub was updated too and it seems the same problem as the first time came back.
Does it give you any specific error message? Is vista installed on the first partition of the HDD?
And which version of Ubuntu do you have, because 9.10 comes with grub2 and earlier versions with grub1.

Hi. Grub was indeed updated, so the same problem came back.
There wasn't any specific error message, just that when I choose vista, it reboots and I'm get back to grub. Vista is installed in the first partition of the hdd. I have Ubuntu 9.10.

---

### Post by darkod on 2009-11-22
Open terminal in ubuntu and execute:
sudo fdisk -l (small L)

Copy the results here, it will show you all partitions.
Then also execute:
sudo update-grub

It will write few lines, see if it finds Vista on /dev/sda1 or something similar.

---

### Post by missChex on 2009-11-22
Hi! There are the partitions:

> 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24837113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21765   174821344    7  HPFS/NTFS
/dev/sda2           23040       24321    10296320    7  HPFS/NTFS
/dev/sda3           21766       23039    10233405    5  Extended
/dev/sda5           21766       22979     9751423+  83  Linux
/dev/sda6           22980       23039      481918+  82  Linux swap / Solaris


and grub finds vista on /dev/sda1 as seen below:
> 
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2


---

### Post by darkod on 2009-11-22
I was assuming this. You have a recovery/utility partition and that is confusing grub.
You can see yourself there are two Vistas found, on /dev/sda1 which is your vista and on /dev/sda2 which is probably recovery partition.
In addition to that, /dev/sda2 is actually at the back of the drive, look at the start/end numbers, starting at 23040 after Linux ends at 23039.

This is beginning to be common problem with todays computers being shipped with recovery partition instead of windows OS dvd. To some people it has helped deleting the recovery partition BUT if you do not have vista OS dvd that will leave you without a way to reinstall vista.
So you have to decide yourself whether deleting the recovery partition is something you would do.
Plus, take into account the fact that once you start dual booting with ubuntu, that recovery partition is almost useless. Those partition recreate the computer as it was from the factory/dealers, which means it will delete your ubuntu partitions whenever to choose recovery. It would also delete any partitions you have created for windows, to store data separately on them.
It doesn't help in restoring vista, it just restores your computer to how you bought it, destroying the programs you put on it and data.
I would try to find vista dvd which will allow you sometimes just to install or repair vista without destroying everything else. I even heard that if you ask the shop where you bought the computer they usually have to provide the vista dvd because you have paid for a licensed OS and the restore partition is destroying everything on the computer when used.
Think about all of this. With the current situation I am not sure it can work, I've seen it before and even after days of trying, nothing helped.

---

### Post by missChex on 2009-11-22
Ok. I will think about it. Will update you on what happens next.

---

### Post by coffeecat on 2009-11-22
**missChex**, when grub was updated it would have produced two entries in the grub menu, both with the same title, something like, "Vista Bootloader". They look the same but one points to sda1 and one to sda2. Did you try both?

---

### Post by wanderingarticfox on 2009-11-22
I had a similar problem with XP and 9.04 and what I finally found that fixed the issue with GRUB was SGD, Super GRUB Disc. It located and mounted the XP into my GRUB menu. I would give it a try, good luck :)  [http://supergrubdisk.org/](http://supergrubdisk.org/)

---

### Post by lmarmisa on 2009-11-22
You are probably using the grub version (not grub2).

In that case, I  think that the last lines of the **/boot/grub/menu.lst **corresponding to the Vista system have been deleted during the update.

Could you copy the content of this file (last 20 lines is OK) in order to check if these lines have been deleted?

I have a dual boot system with Ubuntu + XP and these are the last line of that file:

```
 
...
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e57ceeca-00ee-4f38-abfd-b6ff2092cd71 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e57ceeca-00ee-4f38-abfd-b6ff2092cd71 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
makeactive
chainloader    +1


```Best regards,

Luis

---

### Post by missChex on 2009-11-22
Hello again everyone. I still cannot boot into Windows.
@coffeecat: Yes, after grub updated, there were two entries for vista. One of them pointing to sda1, the other to sda2. I've been choosing sda1 and I haven't tried the other one yet.
@wanderingarcticfox: I actually came across Super Grub Disk quite a few times. Does it have a GUI? Do I run it from Ubuntu?
@lmarmisa: When I checked /boot/grub/menu.lst, the listing was different from my current grub menu, but the Vista entry was still there. When I checked /boot/grub/grub.cfg (the menu.lst of Grub2), it matched what was on my current Grub menu. So I'm quite certain that when grub updated, it became Grub2. I tried editing the Windows vista entry, but to no avail. 
Also, I think it might help to add: When my friend restored my Grub when I removed it the first time, he edited it using /boot/grub/menu.lst. I wasn't able to follow everything that he did, but I'm assuming he uninstalled Grub2 and replaced it with Grub.

---

### Post by presence1960 on 2009-11-22
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by missChex on 2009-11-23
@presence1960 here are the contents of RESULTS.txt
```

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 350246148 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24837113

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   349,642,750   349,642,688   7 HPFS/NTFS
/dev/sda2         370,122,752   390,715,391    20,592,640   7 HPFS/NTFS
/dev/sda3         349,654,725   370,121,534    20,466,810   5 Extended
/dev/sda5         349,654,788   369,157,634    19,502,847  83 Linux
/dev/sda6         369,157,698   370,121,534       963,837  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="080EA61556937179" TYPE="ntfs" 
/dev/sda2: UUID="A0DC44E7DC44B974" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda5: UUID="f5b04382-a7a2-4ede-9c86-b469572ab081" TYPE="ext4" 
/dev/sda6: UUID="c4f2ace5-ad32-4464-9201-2fdcdf59b5fc" TYPE="swap" 

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
gvfs-fuse-daemon on /home/nikka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nikka)


=========================== sda5/boot/grub/menu.lst: ===========================

default=0
timeout=5
title Ubuntu
   root (hd0,4)
   kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=f5b04382-a7a2-4ede-9c86-b469572ab081 ro quiet splash
   initrd /boot/initrd.img-2.6.31-14-generic
title Windows Vista
   rootnoverify (hd0,0)
   chainloader +1

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
search --no-floppy --fs-uuid --set f5b04382-a7a2-4ede-9c86-b469572ab081
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
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f5b04382-a7a2-4ede-9c86-b469572ab081
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f5b04382-a7a2-4ede-9c86-b469572ab081 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f5b04382-a7a2-4ede-9c86-b469572ab081
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f5b04382-a7a2-4ede-9c86-b469572ab081 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f5b04382-a7a2-4ede-9c86-b469572ab081
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5b04382-a7a2-4ede-9c86-b469572ab081 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f5b04382-a7a2-4ede-9c86-b469572ab081
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5b04382-a7a2-4ede-9c86-b469572ab081 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    set root=(hd0,1)
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set a0dc44e7dc44b974
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
UUID=f5b04382-a7a2-4ede-9c86-b469572ab081 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c4f2ace5-ad32-4464-9201-2fdcdf59b5fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 179.0GB: boot/grub/grub.cfg
 179.0GB: boot/grub/menu.lst
 179.0GB: boot/grub/stage2
 179.0GB: boot/initrd.img-2.6.31-14-generic
 179.0GB: boot/initrd.img-2.6.31-15-generic
 179.0GB: boot/vmlinuz-2.6.31-14-generic
 179.0GB: boot/vmlinuz-2.6.31-15-generic
 179.0GB: initrd.img
 179.0GB: initrd.img.old
 179.0GB: vmlinuz
 179.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by coffeecat on 2009-11-23
From that output, it looks as though you did have legacy grub on, but that now you're back with grub2. Anyway, I've pinpointed what is probably the problem.

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    set root=(hd0,1)
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set a0dc44e7dc44b974
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###The stanza for sda1 is incomplete. Something is wrong with the way update-grub is working. You need the "insmod ntfs" line and a search line as in the stanza for sda2. But you'll need a different UUID.

You shouldn't edit grub.cfg directly. Something is wrong with 30_os-prober (I would guess), so you'll probably need to add a stanza to /etc/grub.d/40_custom for Vista.

Unless someone can come up with a better idea. Here's a link to help with grub2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by coffeecat on 2009-11-23
OK, try this:

```
gksudo gedit /etc/grub.d/40_custom
```Copy and paste the following into 40_custom:

```


menuentry "Windows Vista on /dev/sda1" {
       insmod ntfs
       set root=(hd0,1)
       search --no-floppy --fs-uuid --set 080ea61556937179
       chainloader +1
}
```Save the file and make it executable with:

```
sudo chmod +x /etc/grub.d/40_custom
```Note that I have made the menu entry text slightly different - this is to distinguish it from the 30_os-prober generated entries which we'll leave in for the moment.

Now:

```
sudo update-grub
```Now reboot and see if you can boot into Vista with the new menu entry. If you can, you can remove the redundant non-working Vista entries by making /etc/grub.d/30_os-prober non-executable and re-running update-grub. Post back if you need help with this.

---

### Post by presence1960 on 2009-11-23
> **coffeecat said:**
> From that output, it looks as though you did have legacy grub on, but that now you're back with grub2. Anyway, I've pinpointed what is probably the problem.

The stanza for sda1 is incomplete. Something is wrong with the way update-grub is working. You need the "insmod ntfs" line and a search line as in the stanza for sda2. But you'll need a different UUID.

You shouldn't edit grub.cfg directly. Something is wrong with 30_os-prober (I would guess), so you'll probably need to add a stanza to /etc/grub.d/40_custom for Vista.

Unless someone can come up with a better idea. Here's a link to help with grub2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

+1

I see the same thing, the stanza for Vista (sda1) is incomplete. I had some problems with GRUB2 initially and reinstalled it from Synaptic- the package is grub-pc. Once reinstalled it worked fine.

---

### Post by missChex on 2009-11-23
@coffeecat: how come after I typed in sudo update-grub, I don't see the new entry "Windows Vista on /dev/sda1" added?

---

### Post by drs305 on 2009-11-23
> **missChex said:**
> @coffeecat: how come after I typed in sudo update-grub, I don't see the new entry "Windows Vista on /dev/sda1" added?

If you are referring to seeing it being added from the 40_custom file, it's probably because there is no "echo" command for displaying this while the script is running. It's not a big deal except that you don't get visual confirmation that it has been added.

Since the 40_custom file isn't updated automatically, if you check it once it will also work in the future. You can quickly see what Vista entries have been added to grub.cfg with this command:
```

grep -A5 Vista /boot/grub/grub.cfg

```

Hope coffeecat doesn't mind me barging in here. ;-)

---

### Post by missChex on 2009-11-23
@coffeecat: Just kidding. I saw the entry on the menu when I rebooted. That seemed to do the trick. I was able to boot into Vista finally. The following

```

menuentry "Windows Vista on /dev/sda1" {
       insmod ntfs
       set root=(hd0,1)
       search --no-floppy --fs-uuid --set 080ea61556937179
       chainloader +1
}

```
was already in grub2 /boot/grub/grub.cfg before I edited it to remove "insmod ntfs" and "search...". Even then, Vista would sometimes not load. Does this have an issue with the MBR?

---

### Post by coffeecat on 2009-11-23
> **missChex said:**
> @coffeecat: how come after I typed in sudo update-grub, I don't see the new entry "Windows Vista on /dev/sda1" added?

Good question! :lol: I don't know, but it doesn't seem to matter. I've disabled 30_os-prober by making it non-executable (for different reasons - I wasn't having your problem) and added entries for Vista and another Linux distro to 40_custom. When I run update-grub, all I get is:

```
$ sudo update-grub 
Generating grub.cfg ...
Found Debian background: MistyMorning_1280x1024.png
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
$ 
```... but my custom entries for Vista and the other distro turn up in my grub menu just fine.

But before trying all that I suggested, why not try presence1960's suggestion of reinstalling the grub-pc package?

**Edit:** we seem to have posted simultaneously. :) But..

[quote=missChex]was already in grub2 /boot/grub/grub.cfg before I edited it to remove "insmod ntfs" and "search...". Even then, Vista would sometimes not load. Does this have an issue with the MBR?[/quote]

I don't quite follow that. Do you mean you had edited grub.cfg at some point? That's not a good idea. All menu editing needs to be done with the files in /etc/grub.d. But I don't think there's an issue with the mbr. You've got grub stage1 on the mbr, and it seems to be working fine. If it wasn't, it wouldn't boot anything, rather than booting Ubuntu and not Vista.

---

### Post by missChex on 2009-11-23
Vista seems to be working fine now. I only have to see if it will work everytime. What I did was to first reinstall grub-pc. However, the original boot loader for Vista didn't work, so I added a new one as coffeecat had said. I used that and Vista loads.

---

### Post by darkod on 2009-11-23
After a while, if you are sure the entry you created manually is working fine every time, you could make grub delete the entries it created automatically, they don't work anyway. You can enable them back anytime you want.
To disable the automatic entries (not your manual one), just execute:

```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

That will disable the automatic os prober, and you can enable it anytime you want with the same command just using +x instead of the -x.

---

### Post by missChex on 2009-11-23
Hi again. Thanks for the help everyone. I can now go into Vista again. Only problem is,Windows takes a looong time to shut down that I usually resort to my power button (hold it down a long time) to turn it off. Anyone experienced this?

---

### Post by coffeecat on 2009-11-23
Are you sure it's not trying to install some updates? Although, normally, it would tell you.

Or perhaps it's repairing the filesystem damage caused the last time you forced a shut down. :wink:

I believe Windows does some rearranging of the swap file on shutdown. Maybe it's got in a muddle and needs to be allowed to do this a couple of times before it will be able to shut down quickly. Give it a couple of reboot/shutdown cycles, but let it shutdown by itself. See if that solves it.

---

### Post by lisati on 2009-11-23
> **missChex said:**
> Hi again. Thanks for the help everyone. I can now go into Vista again. Only problem is,Windows takes a looong time to shut down that I usually resort to my power button (hold it down a long time) to turn it off. Anyone experienced this?

I've noticed on my laptop that Vista sometimes seems to take a while to shut down as well, but haven't got round to doing anything about it yet. I was thinking of a fresh install from recovery disks due to a couple of other annoyances and as part of a general cleanup, but since they're relatively minor it will have to wait until I've finished some stuff that I've been working on.

---

### Post by missChex on 2009-11-23
Hi! I did some reboot/shutdown cycles and now, it's shutting down normally. Thanks again for all your help guys!

---

### Post by missChex on 2009-11-24
Hi again. Another question. Why is it that sometimes, after the ubuntu logo shows up, the screen become black. I don't know if the login screen just takes some time to show up, or it just plain froze. I usually end up doing a forced shutdown.

---

### Post by coffeecat on 2009-11-24
I've just timed a boot up on this machine with an AMD X2 4200. That's a fairly modest dual-core processor. This is what I got from pressing the enter key at the grub menu until the login screen appears (very approximate times):

Black screen - 2 seconds
White on black Ubuntu logo - 20 seconds
Black screen - 5 seconds
Dark Brown Ubuntu screen with the little whizzy thing - 5 seconds

Do you get the 'dark Brown Ubuntu screen with the little whizzy thing'? I believe that's the Xsplash. How long does the screen remain black before the login screen appears?

> **missChex said:**
> I don't know if the login screen just takes some time to show up, or it just plain froze. I usually end up doing a forced shutdown.

To see if it's freezing rather than just being slow, you could try this:

At the grub menu, make sure the 9.10 line is highlighted and press 'e' to edit it. This edit will be a one-time ony - it won't be saved. Move the cursor to the line that starts 'linux /boot/vmlinuz...' and remove 'quiet splash' from the end of that line. Now press ctrl-X to boot. You'll get a mass of scrolling text instead of the Ubuntu logo. If the boot process freezes, make a note of the last 5 or so lines and post them.

However, when I tried this, the scrolling text lasted about as long as the Ubuntu logo usually does and was then replaced by a black screen for a few seconds and then the dark brown screen. So, if you are getting a freeze at the black screen phase, what I have just described might not help.

---

### Post by missChex on 2009-11-24
Hi all again. Apparently, if I restart from one OS and load into another, the "another OS" doesn't start up. Weird.

---

