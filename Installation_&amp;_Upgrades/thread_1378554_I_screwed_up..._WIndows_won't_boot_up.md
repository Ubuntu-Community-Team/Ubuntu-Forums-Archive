---
title: "I screwed up... WIndows won't boot up"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by rubsnick on 2010-01-11
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

I followed that guide but it still installed GRUB and now whenever I chose the Windows 7 Loader it won't load.... I can load ubuntu just fine but I can't load windows 7.... could someone please help me?

---

### Post by wilee-nilee on 2010-01-11
Which distro of Ubuntu do you have installed?

I am not familiar with EasyBCD so you might explain why you chose this method of grub install in and what partition.

---

### Post by darkod on 2010-01-11
This is exactly why I get annoyed by people here recommending EasyBCD. And when things don't work out again we need to solve it and ubuntu gets blamed usually. :(

So, are you using 9.10 and you have grub2 installed on the MBR? Because you said you can boot ubuntu fine.
And was windows booting before installing EasyBCD?

---

### Post by rubsnick on 2010-01-11
I haven't gotten to that step. I have not booted into windows since I installed Linux. I'm using Ubuntu 9.10 and this is my first linux experience.... anyways I tried playing around and when I click on windows 7 in the grub menu it just says really quickly starting grub. So it's looping.. I have to somehow repair my windows instalation but my Instalattion disc won't allow me to do this (says it's incompatible or something) I'm at my wits end, i've been dealing with this effing PC since 10:30 AM. (Had problem with windows 7 also but it's was moslty user error) but here... I dunno. I'm thinking of uninstalling grub.... or find a way to repair grub or something.

Upddate: Did a system Repair.... that didn't help it at all... still those the same thing.

---

### Post by rubsnick on 2010-01-11
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


Will this help any? I have practically no understanding of what this says....

---

### Post by rubsnick on 2010-01-11
I just did a boot info summary... maybe this can help?


============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda1 and 
                       looks at sector 709499189 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x117437ef

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   586,521,301   586,314,454   7 HPFS/NTFS
/dev/sda3         586,533,150 2,930,272,064 2,343,738,915   5 Extended
/dev/sda5         586,533,213   977,153,624   390,620,412  83 Linux
/dev/sda6         977,153,688 2,930,272,064 1,953,118,377   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="1E885A3A885A111F" LABEL="System Reserved" TYPE="ntfs" 
sda2: UUID="5C7A64737A644BB8" TYPE="ntfs" 
sda5: UUID="4b8539f7-8723-4045-8a7e-6021eb0eaf86" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/rubsnick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rubsnick)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=rubsnick)


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
search --no-floppy --fs-uuid --set 4b8539f7-8723-4045-8a7e-6021eb0eaf86
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 4b8539f7-8723-4045-8a7e-6021eb0eaf86
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4b8539f7-8723-4045-8a7e-6021eb0eaf86 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 4b8539f7-8723-4045-8a7e-6021eb0eaf86
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4b8539f7-8723-4045-8a7e-6021eb0eaf86 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1e885a3a885a111f
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
UUID=4b8539f7-8723-4045-8a7e-6021eb0eaf86 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 300.3GB: boot/grub/core.img
 300.3GB: boot/grub/grub.cfg
 300.3GB: boot/initrd.img-2.6.31-14-generic
 300.3GB: boot/vmlinuz-2.6.31-14-generic
 300.3GB: initrd.img
 300.3GB: vmlinuz

---

### Post by darkod on 2010-01-11
OK, calm down. Don't try everything at once.

If you are trying to use fdisk, the correct format is:
sudo fdisk -l

Boot into ubuntu, download the script in my signature, move it on desktop for example, and run it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with the details about your boot. Copy the content of the file here.

---

### Post by rubsnick on 2010-01-11
> **darkod said:**
> OK, calm down. Don't try everything at once.

If you are trying to use fdisk, the correct format is:
sudo fdisk -l

Boot into ubuntu, download the script in my signature, move it on desktop for example, and run it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with the details about your boot. Copy the content of the file here.

Yeah that's what I did.... I just posted what seemed relevant is all....

---

### Post by darkod on 2010-01-11
Yes, you are in a loop. You have windows bootloader in the MBR of your hdd and then grub2 in the win7 boot partition. It shouldn't be there.
Repair the win7 boot process following instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your win7 dvd doesn't allow you to use the Repair This Computer option, then download win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

After you have confirmed that win7 boot process is repaired and working fine, reinstall grub2 on the MBR by booting with the ubuntu cd, Try Ubuntu option, and in terminal executing:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd and all should be fine.

---

### Post by rubsnick on 2010-01-11
> **darkod said:**
> Yes, you are in a loop. You have windows bootloader in the MBR of your hdd and then grub2 in the win7 boot partition. It shouldn't be there.
Repair the win7 boot process following instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your win7 dvd doesn't allow you to use the Repair This Computer option, then download win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

After you have confirmed that win7 boot process is repaired and working fine, reinstall grub2 on the MBR by booting with the ubuntu cd, Try Ubuntu option, and in terminal executing:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd and all should be fine.

Well I already repaired it and windows said it was repaired but it won't boot... I'm pretty sure it's fixed tough. What's MBR? anyways you mean I should boot the CD in live mode? Not install mode? and then I should execute the code? that will pretty much restore my problems? Thanks for the help I hope I haven't been too nooby I usually spend my times hacking PSP's and Wii's so I know how annyoing noobs are I just have no experience with linux. I know my problem was well created by myself... so thanks for the heads up I'll do it now.

UPDATE: Tried what you said... Windows still refused to boot.... *sigh*

---

### Post by darkod on 2010-01-11
> **rubsnick said:**
> Well I already repaired it and windows said it was repaired but it won't boot... I'm pretty sure it's fixed tough. What's MBR? anyways you mean I should boot the CD in live mode? Not install mode? and then I should execute the code? that will pretty much restore my problems? Thanks for the help I hope I haven't been too nooby I usually spend my times hacking PSP's and Wii's so I know how annyoing noobs are I just have no experience with linux. I know my problem was well created by myself... so thanks for the heads up I'll do it now.

Yes, boot with ubuntu cd and select Try Ubuntu option, not Install Ubuntu. That will run it from the cd but you can open terminal and execute commands just like it was running from hdd (it's not exactly the same but lets not get into that right now).
That commands will install grub2 to the MBR (Master Boot Record) of your hdd.

But before that, win7 should be able to boot correctly. If it doesn't, reinstalling grub2 won't help, this is a win7 boot issue. You can see towards the top of the results file that grub 1.97 (that's grub2) is installed in the /dev/sda1 partition and it shouldn't be there. I was hoping the win7 boot repair would get rid of it.
Try again the suggested procedure from that link. It includes commands too, not the automated process. If that doesn't help, I don't know how to remove grub2 from /dev/sda1. :(

---

### Post by rubsnick on 2010-01-11
NVM IT WORKED! AWESOME! THANK YOUR THE LINK! *nods* Thank you... but now how do I boot to Ubuntu?

---

### Post by darkod on 2010-01-11
Since you are asking about ubuntu, I guess what worked is booting into win7.
Now just boot with the ubuntu cd, Try Ubuntu option, open terminal and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should install grub2 on your hdd MBR and grub2 will give you a menu to choose either ubuntu or win7. Reboot without the cd in the drive and see whether it worked.

---

### Post by rubsnick on 2010-01-11
> **darkod said:**
> Since you are asking about ubuntu, I guess what worked is booting into win7.
Now just boot with the ubuntu cd, Try Ubuntu option, open terminal and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should install grub2 on your hdd MBR and grub2 will give you a menu to choose either ubuntu or win7. Reboot without the cd in the drive and see whether it worked.

Is their a way I can do that but with the Windows loader instead?

---

### Post by darkod on 2010-01-11
Yes and no. Now you are starting from the beginning. By default, windows bootloader can't load linux, that's why it's not offering option to boot ubuntu to you. It can't even see it. There are ways to do it, but depending how familiar you are with that, it can easily get messed up.
Remember that following the EasyBCD tutorial got you here?
On the other hand, grub2 can boot both linux and windows, and I see no reason not to use it.
Even if something goes wrong, you just repaired windows bootloader, you saw it's not difficult. You'll just do it again.
My advice is use grub2. If you want to use anything else, your choice. But I don't know much about the other options and I can't help much.

---

### Post by rubsnick on 2010-01-11
> **darkod said:**
> Yes and no. Now you are starting from the beginning. By default, windows bootloader can't load linux, that's why it's not offering option to boot ubuntu to you. It can't even see it. There are ways to do it, but depending how familiar you are with that, it can easily get messed up.
Remember that following the EasyBCD tutorial got you here?
On the other hand, grub2 can boot both linux and windows, and I see no reason not to use it.
Even if something goes wrong, you just repaired windows bootloader, you saw it's not difficult. You'll just do it again.
My advice is use grub2. If you want to use anything else, your choice. But I don't know much about the other options and I can't help much.

Alright I googled a bit and that guide is outdated... @_@ Someone just told me it will work and I took their word for it my fault really. I'm gonna use easyBCD 2.0 and it that doesn't work then I"ll use grub 2. I'm more familiar with the Windows Side of things so I would like to stay in my comfort zone for something like this. Again thank you very much for your help. Sorry I was a bit of a noob.

---

### Post by darkod on 2010-01-11
> **rubsnick said:**
> Alright I googled a bit and that guide is outdated... @_@ Someone just told me it will work and I took their word for it my fault really. I'm gonna use easyBCD 2.0 and it that doesn't work then I"ll use grub 2. I'm more familiar with the Windows Side of things so I would like to stay in my comfort zone for something like this. Again thank you very much for your help. Sorry I was a bit of a noob.

No problem, whatever works for you. Just an advice, being comfortable with windows doesn't automatically make this kind of dual booting necessarily easier. I know you got freaked when I said use grub2 instead of windows bootloader but in fact I'm sure that if you just used the default settings the first time, and let grub2 install itself on the MBR when installing ubuntu instead of following the EasyBCD tutorial, you would already had a working system instead of wasting your time here to repair this.
In some situations, not letting go of windows comfort is getting you into trouble. :)

---

### Post by rubsnick on 2010-01-11
I can't get it to work at all... Grub2 doesn't seem to like windows 7 in my case at least. I think I"ll stick with a virtual machine I"m just going to use ubuntu to mess around and learn more about OS's, I'm studying computer science so yeah I like this stuff.

---

