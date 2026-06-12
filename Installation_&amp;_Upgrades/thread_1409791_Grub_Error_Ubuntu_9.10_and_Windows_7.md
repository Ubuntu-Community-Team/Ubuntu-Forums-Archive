---
title: "Grub Error Ubuntu 9.10 and Windows 7"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Mrepenning on 2010-02-18
First off let me say I'm a noob like I just downloaded ubuntu for the first time and have never done anything like this noob.

I ran the liveCD and thought this is pretty cool so I installed on my HP with windows7 and the first time when I was running the partitioner it froze up. I manually shut down and restarted everything went well the second time.

I got everything installed and restarted my system. upon boot-up I ran into:
GRUB loading
error: no such disk
grub rescue>

I have looked on here for some suggestions but I am kinda dumb and I don't think I am doing something right. Help any one?

Thanks, Mike

---

### Post by Mrepenning on 2010-02-18
I rebooted and ran the ls command prompt and found an hd 0 0,4 0,3 0,2 and 0,1. I was reading the help wiki and it said that it normally installed to (hd0,5) there is no grub for that partition, could this be the issue?

If so how do I fix it?
Mike

---

### Post by Mrepenning on 2010-02-18
I also can't get windows to load. Sorry about so many posts I am just posting info as I find it so as to avoid unneeded questions

Mike

---

### Post by popradcan on 2010-02-18
Hi Mike!
This is actually no help which I can offer, but I have gotten a similar problem.

I installed Ubuntu 9.10 on a 5 years old IBM Notebook. First I had booted the notebook with the LiveCD. Everything was pretty fine. So I decided to delete my Windows XP completely and to install Ubuntu as the only OS.

After completing the installation I had to rebood and have a similar GRUB error.

"Grub error: no such device (...)"

I have gotten no inkling how to fix it.

Is there some helping hand out there in cyberspace?

Drew

---

### Post by Mrepenning on 2010-02-18
I have downloaded the boot_info_script but do not know how to open it! any help please I am starting to stress. 
mike

---

### Post by meierfra. on 2010-02-18
Mrepenning:

Instructions for the boot info script:  	
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Could you also type "ls" at the "grub rescue>" prompt and post the output

---

### Post by meierfra. on 2010-02-18
popradcan:  Could you start your own thread? It is nearly impossible to try to solve to problems in one thread.  Follow the instruction for the boot info script (see the link in the previous post) and post the RESULTS.txt in your new thread.
Could you also type "ls" at the "grub rescue>" prompt and post the output in your new thread
Thanks.

---

### Post by Mrepenning on 2010-02-18
I typed in ls and got back
(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)

I only have the option to save, I dont even have the option to tell it where.

I click on it and it asks me to choose a program to open it with.

Mike

---

### Post by meierfra. on 2010-02-18
> I typed in ls and got back
(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) 

Oops.  That request was supposed to be in my second post for popradcan. 

(You already had posted that)

---

### Post by meierfra. on 2010-02-18
> I only have the option to save, I dont even have the option to tell it where.
Where is the script: Is it on the desktop? Or in the Downloads folder?
You need to run the script in a terminal. To open a terminal go to "Applications->Accessories->Terminal.

If the script is in the download folder type

```
sudo bash ~/Downloads/boot_info_script*.sh 
```

If its on the Desktop

```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by Mrepenning on 2010-02-18
I tried getting into the bios to try and get windows to load. no dice just the same grub error

---

### Post by Mrepenning on 2010-02-18
Like I said I am dumb I ran the boot-info-script but now I cant get the results it tells me permision denied

---

### Post by meierfra. on 2010-02-18
> cant get the results it tells me permision denied

That's weird. It should just open if you double click "RESULTS.txt" Did you had any error messages while running the script?  You mighty try again. If still does not open, try

```
gksudo gedit ~/Downloads/RESULTS.txt

```
or

```
gksudo gedit ~/Desktop/RESULTS.txt
```

---

### Post by Mrepenning on 2010-02-18
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script*.sh
bash: /home/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Downloads/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Downloads
ubuntu@ubuntu:~$ RESULTS.txt/home/ubuntu/Downloads
bash: RESULTS.txt/home/ubuntu/Downloads: No such file or directory
ubuntu@ubuntu:~$ /home/ubuntu/Downloads/RESULTS.txt
bash: /home/ubuntu/Downloads/RESULTS.txt: Permission denied
ubuntu@ubuntu:~$ sudo /home/ubuntu/Downloads/RESULTS.txt
sudo: /home/ubuntu/Downloads/RESULTS.txt: command not found
ubuntu@ubuntu:~$ results.txt
results.txt: command not found
ubuntu@ubuntu:~$ sudo /home/ubuntu/Downloads/RESULTS.txt
sudo: /home/ubuntu/Downloads/RESULTS.txt: command not found
ubuntu@ubuntu:~$ bash/home/ubuntu/Downloads/RESULTS.txt
bash: bash/home/ubuntu/Downloads/RESULTS.txt: No such file or directory
ubuntu@ubuntu:~$ bash /home/ubuntu/Downloads/RESULTS.txt
/home/ubuntu/Downloads/RESULTS.txt: line 1: Boot: command not found
/home/ubuntu/Downloads/RESULTS.txt: line 3: =============================: command not found
/home/ubuntu/Downloads/RESULTS.txt: line 5: =: command not found
/home/ubuntu/Downloads/RESULTS.txt: line 6: syntax error near unexpected token `/boot/grub.'
/home/ubuntu/Downloads/RESULTS.txt: line 6: `    (UUID=8146facb-078e-4a55-a1d8-f6d3ada6735a)/boot/grub.'
ubuntu@ubuntu:~$ 


This is everything I got from the beginning of the terminal.

I am going to run those other prompts and see what I get ill post them on here.

Mike

This is what I got with the first prompt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=8146facb-078e-4a55-a1d8-f6d3ada6735a)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29e95222

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   940,021,759   939,612,160   7 HPFS/NTFS
/dev/sda3         940,021,760   976,560,127    36,538,368   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
255 heads, 63 sectors/track, 966 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b937c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065     8,642,969     8,626,905   b W95 FAT32
/dev/sdb2           8,642,970    15,518,789     6,875,820   5 Extended
/dev/sdb5           8,643,033    15,101,099     6,458,067  83 Linux
/dev/sdb6          15,101,163    15,518,789       417,627  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        981C041B1C03F354                       ntfs       SYSTEM                        
/dev/sda2        96F0BBAFF0BB93C9                       ntfs                                     
/dev/sda3        AA46307E46304CF7                       ntfs       RECOVERY                      
/dev/sda4        D437-1A89                              vfat       HP_TOOLS                      
/dev/sdb1        3239-3865                              vfat       NIKON D60                     
/dev/sdb5        8146facb-078e-4a55-a1d8-f6d3ada6735a   ext4                                     
/dev/sdb6        43fc5ff6-82a3-4404-9a31-e595139ff5bf   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/NIKON D60         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /media/8146facb-078e-4a55-a1d8-f6d3ada6735a ext4       (rw,nosuid,nodev,uhelper=devkit)


=================== sda2: Location of files loaded by Grub: ===================


    HPGB: boot/grub/core.img

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 8146facb-078e-4a55-a1d8-f6d3ada6735a
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
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 8146facb-078e-4a55-a1d8-f6d3ada6735a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8146facb-078e-4a55-a1d8-f6d3ada6735a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 8146facb-078e-4a55-a1d8-f6d3ada6735a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8146facb-078e-4a55-a1d8-f6d3ada6735a ro single 
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
    search --no-floppy --fs-uuid --set 981c041b1c03f354
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 96f0bbaff0bb93c9
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set aa46307e46304cf7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=8146facb-078e-4a55-a1d8-f6d3ada6735a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=43fc5ff6-82a3-4404-9a31-e595139ff5bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


   5.2GB: boot/grub/core.img
   6.9GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.31-14-generic
   6.8GB: boot/vmlinuz-2.6.31-14-generic
   5.2GB: initrd.img
   6.8GB: vmlinuz

---

### Post by Mrepenning on 2010-02-18
The grub is not installed on hd0,5 I think this might be part of the problem.

Thanks for the help, I am no longer in the featal position sucking my thumb ;) but I still need help until I get this thing going, just wanted to show some appreciation

Mike

---

### Post by popradcan on 2010-02-18
> **meierfra. said:**
> popradcan:  Could you start your own thread? It is nearly impossible to try to solve to problems in one thread.  Follow the instruction for the boot info script (see the link in the previous post) and post the RESULTS.txt in your new thread.
Could you also type "ls" at the "grub rescue>" prompt and post the output in your new thread
Thanks.


THANK you so far. I've just come back and still have to try it out. ... O.K. I will start a new thread in case of need. I just thought that I have gotten a similar problem.

---

### Post by meierfra. on 2010-02-18
The "ls" command only shows your 500GB hard drive.  So that means that your 8GB drive is not detected by the bios.  Is the 8GB drive a USB flash drive?    You might have to enable USB support in the Bios.

Did you already try to set the Bios to boot from the 8GB drive?

For some reason Grub is installed  on the MBR of both hard drives.
The following will restore the MBR of the 500GB drive, and you should be able to boot into  Windows 7 again (if you set the Bios to boot from the 500GB drive):

```
sudo apt-get install lilo
```
(ignore the messages you get, just press enter)

```
sudo lilo -M /dev/sda mbr
```

---

### Post by Mrepenning on 2010-02-18
This is what I got with the first prompt:

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main mbr 1.1.10-2
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main lilo 1:22.8-8ubuntu1
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ 


I will run the second and see what I get.

Mike

---

### Post by Mrepenning on 2010-02-18
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
sudo: lilo: command not found
ubuntu@ubuntu:~$ 

Mike

---

### Post by meierfra. on 2010-02-18
Seems "apt-get" was not able to reach the Ubuntu server.   Is the Internet connection working in the Live CD?

Go to "System->Administration->Software Sources" and choose a different server in"Download From". 

Then try the two "lilo" commands again.

---

### Post by Mrepenning on 2010-02-18
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 223 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main mbr 1.1.10-2 [23.0kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main lilo 1:22.8-8ubuntu1 [390kB]            
Fetched 413kB in 15s (26.6kB/s)                                                        
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 120319 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


ubuntu@ubuntu:~$ /sbin/lilo
Fatal: Cannot open: /etc/lilo.conf
ubuntu@ubuntu:~$ /usr/share/doc/lilo/README.Debian
bash: /usr/share/doc/lilo/README.Debian: Permission denied
ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2010-02-18
I think you should still run the second command:

```
sudo lilo -M /dev/sda mbr
```

That will only let you attempt to boot Windows anyway.

And I think this may be a problem:

```
sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /boot/BCD /Windows/System32/winload.exe
**[COLOR="Red"]/boot/grub/core.img[/COLOR]**
```

Just be a little patient. Meierfra is the best you could hope for when it comes to working out boot problems :)

---

### Post by meierfra. on 2010-02-18
> /sbin/lilo

???
The "sudo apt-get install lilo" command was successful.  But afterwards you were supposed to do "sudo lilo -M /dev/sda mbr".

Since you are working on a Live cd, also changes are lost after rebooting. So if you rebooted since your last post you have to install "lilo" again.

Do this:

Go to "System->Administration->Software Sources" and choose a different server in"Download From". 

```
sudo apt-get install lilo
```
(ignore the messages you get, just press enter)

```
sudo lilo -M /dev/sda  mbr
```


> Boot files/dirs: /bootmgr /boot/BCD /Windows/System32/winload.exe
[COLOR="Red"]/boot/grub/core.img[/COLOR]

core.img is only a problem if you have a "/boot" and a "/Boot" folder.  So you don't have to worry about this.

---

### Post by kansasnoob on 2010-02-18
> core.img is only a problem if you have a "/boot" and a "/Boot" folder. So you don't have to worry about this.

Thanks, good to know.

---

### Post by Mrepenning on 2010-02-18
This is what I have done.

```
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
ubuntu@ubuntu:~$ ~/Downloads/boot_info_script*.sh
bash: /home/ubuntu/Downloads/boot_info_script055.sh: Permission denied
ubuntu@ubuntu:~$ 

```

What should I do now. Sorry for not knowing more I feel kinda stupid right now. Thanks for all the help because I would be so lost.

Mike

---

### Post by kansasnoob on 2010-02-18
> **Mrepenning said:**
> This is what I have done.

```
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
ubuntu@ubuntu:~$ ~/Downloads/boot_info_script*.sh
bash: /home/ubuntu/Downloads/boot_info_script055.sh: Permission denied
ubuntu@ubuntu:~$ 

```

What should I do now. Sorry for not knowing more I feel kinda stupid right now. Thanks for all the help because I would be so lost.

Mike

So if you reboot now can you boot into Windows?

---

### Post by meierfra. on 2010-02-18
> ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800


That looks good.  

Reboot and set your bios to boot from  Windows drive. You should boot directly into Windows.

We'll worry about booting into Ubuntu, after you successfully booted into Windows.

(Edit: Seems   kansasnoob already told you the same thing.)

---

### Post by kansasnoob on 2010-02-18
Actually after such a lapse in time did you pay attention to Meierfra's last post?

If you'd exited the live environment then you must run both:

```
sudo apt-get install lilo
```

Ignore any BS, just hit enter, and:

```
sudo lilo -M /dev/sda  mbr
```

Then reboot and see what happens.

---

### Post by Mrepenning on 2010-02-18
Thank you both I am posting from windows7

I really appreciate it. Now to get ubuntu to load.

Mike

---

### Post by meierfra. on 2010-02-18
> Actually after such a lapse in time did you pay attention to Meierfra's last post?

???

lilo ran successfully.  So Mrepenning must have followed my advice.

---

### Post by meierfra. on 2010-02-18
> I am posting from windows7
Great.

> Now to get ubuntu to load.

I had asked you this before, but did not   get an explicit answer.

1) What exactly happens when you boot with your BIOS set to boot from the Ubuntu Drive.

2)  Is your 8GB Ubuntu drive a USB flash drive?

3)  Check your Bios and see whether it has a place to enable USB devices

---

### Post by Mrepenning on 2010-02-18
Can I do what I need to from windows or do I need to run the liveCD?

Mike

---

### Post by kansasnoob on 2010-02-18
First of all let's review what we know. This shows Ubuntu's grub2 was installed to both sda and sdb:

```
=> Grub 2 is installed in the MBR of /dev/sda and looks for
(UUID=8146facb-078e-4a55-a1d8-f6d3ada6735a)/boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #5 for /boot/grub.
```

We also know that sda is an internal 500 GB drive and I'd guess that sdb is an external 8 GB drive. Why didn't you just say that?

Or am I wrong?

If I'm right you need to have your BIOS set to boot CD first, USB second, and then hard drive (basically). Do you understand how to change settings in the BIOS?

Maybe this will be helpful:

[http://www.ehow.com/how_4533733_change-boot-order-bios.html](http://www.ehow.com/how_4533733_change-boot-order-bios.html)

Otherwise I'm too tired to continue tonight.

I really don't see anything wrong with grub2. You're just booting straight to the hard drive without the BIOS looking to USB first.

---

### Post by Mrepenning on 2010-02-18
I think I know what happened! I have my 8gig SD card from my camera in the SD slot! I was wondering why the partition was only 8 instead of 500.

How do I get it to load from my SD first? It is drive G:

This is making much more sense. I was wondering why some one had said usb drive I didn't even realize that it could load to my SD drive.

Mike

---

### Post by meierfra. on 2010-02-18
> How do I get it to load from my SD first? It is drive G:

Well, you  accidentally installed Ubuntu to the SD card.
I hope you didn't loose any pictures/videos.

Do you want to keep Ubuntu on the SD card? 
If you want to keep Ubuntu on the SD card, you will have to figure out how to set your Bios to boot from the SD card. Have a look at the link kansasnoob posted.  But maybe your Bios won't even let you boot from the SD card.

---

### Post by Mrepenning on 2010-02-18
I can't boot from the SD card can I just redo the install but install it directly to my hard drive? Are there any precautions that I should take before installing ubuntu? 

This is what I am thinking remove the SD reboot install ubuntu and everything will be smooth sailing. Do I need to worry about anything not installing right? I guess if it dies screw up I know where to go.

Mike

P.S. no I didn't lose any pictures thanks for asking.

---

### Post by kansasnoob on 2010-02-19
Generally booting from an internal card reader is the same as booting from floppy. So you would have to have the BIOS set to boot floppy first, then CD, then USB, then hard drive (but my BIOS doesn't allow that).

As far as installing on the Win 7 drive this may be helpful:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

I know that's for Vista but after playing with the Win 7 RC I can tell you it's quite similar.

---

