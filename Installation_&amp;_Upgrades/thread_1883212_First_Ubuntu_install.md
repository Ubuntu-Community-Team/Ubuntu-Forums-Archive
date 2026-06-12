---
title: "First Ubuntu install"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by Snipeya on 2011-11-18
Noob alert. I'm currently using Windows Vista and I have never used anything other than windows os's. I really want to try Ubuntu but I'm scared of breaking something or not knowing how to use it and not being able to get Windows back. I'm not great with computers but I'll try anything once! Should I download it to disc and buy a cheap computer to try it on or can I run it while still keeping windows. Thanks in advance guys, Danny

---

### Post by darkod on 2011-11-18
The easiest way to simply try it, is downloading the ISO image, burning a cd with it, and then booting the computer with that cd.
There will be a menu asking whether you want to Try Ubuntu or Install. If you select Try it will load a functional ubuntu from the cd. No changes are made to your hard disk.
Ubuntu includes lots of software by default, you will be able to use Firefox, Libre Office, etc from the live mode. Internet should work with almost any wired connections, for wireless it works for some immediately, for others doesn't, depending on your wireless card.

When you are ready to install ask questions first what is the best way to do it, also there are many manuals on the internet if you google around.

---

### Post by codethulhu on 2011-11-18
I would agree with darkod. The best way to learn is to just try it. Ubuntu makes it simple and easy for beginners. It was the first linux distro I tried and I've been using linux ever since.

Let us know how it goes. :)

---

### Post by dolphin194 on 2011-11-18
The Linux world is great. I started with Fedora about 3 years ago, and decided that I didn't like it very much. Then I switched to Ubuntu and literally fell in love with it! Ubuntu is a great distribution, and I hope you will like it. 

Just like the other two said, simply play around with Linux. Try different ones and decide which one you like the most. Even though most people say the Linux is difficult, it really isn't. It's just different from Windows.

---

### Post by Snipeya on 2011-11-19
Wow, downloaded it onto cd and I love it, it looks great, I'm actually using it to write this ;) I think I want to install it and keep windows as I don't think I can use things like i tunes. Does it take up much room as I only have about 6gb on C: but my D: drive has loads of room about 60+gb. Thanks for your help so far :razz:

---

### Post by darkod on 2011-11-19
It can be installed in as little as 4GB but it's better to have 10-15GB.
It doesn't install on ntfs partitions, so you will have to shrink D: to make space.
In Vista you can open Disk Management and shrink D: for 15GB for example. Or 20GB if you don't need that space.
After shrinking reboot vista few times because it might need to run some disk checks. Do not create any partitions in the unallocated space created from windows.

Then boot with the ubuntu cd and select to Install it. It should offer option to install into the unallocated space existing. And that should be it.

---

### Post by Renntag on 2011-11-19
Go for it and never look back. Using a cd or a thumb drive, drop it in and enjoy a live demo. This really is a wonderful creation. Once you run it you have options of what to do. You can even install in windows as if it were another application. Completely benign to your existing system. I just did an install of 11.10 on my wife's laptop "alongside" the existing windows OS with no effect to the system. On boot up she can select what OS to launch. It is seemless. 

I am no pro. This was a simple 'follow the promts' install any low level enthusiast can do. 

During install I was asked to drag a divider that resprented a virtual partition, allowing me to establish what space was to be used for each OS. Another step even asked me to select the windows profile that should be made available in Ubuntu. Again, just a great product. 

Give it a try.

---

### Post by Snipeya on 2011-11-20
Oh dear. I've installed Ubuntu 11.10 but it never asked me how other than at start to install alongside Windows Vista. Now it boots straight to Ubuntu when I start and if I go to boot menu there are 2 options in hard drive but none go to Windows. I created some space by shrinking D: drive by the max 21gb it would allow but the install never asked me if I wanted to save it here. Do I need to remove Ubuntu and start again and if so how would I go about removing it? Yours panicking, Danny

---

### Post by darkod on 2011-11-20
Don't reinstall again, it usually can get you in worse situation.

Boot ubuntu and follow the link in my signature to run the boot info script. Post the results here as explained in that link. That will show more details.

---

### Post by Snipeya on 2011-11-20
Ok I've downloaded the boot info script but now I'm lost I don't know how to extract the zip file as I can't find it and I don't know where to send it after I do find it do I just create a little file on the screen?

---

### Post by sanderd17 on 2011-11-20
I hope you use the Unity interface, there are a lot of different interfaces.

You can open the dash (click on the ubuntu icon on the top left) and search "Nautilus". That's the Ubuntu default file manager. Probably another search like "files" will also work.

Now, in Nautilus, go to your Downloads directory. There you should find it. Right click to extract it to your home directory (the directory with your user name).

Now you should be able to follow the other steps.

EDIT:

Oh right, the new Unity interface. There isn't a menu anymore, so you can't open the terminal with Applications -> Accessories -> Terminal. Instead, you can search for terminal, or I believe CTRL+ALT+T still works as hotkey.

---

### Post by darkod on 2011-11-20
The default download location is your Home/Downloads folder. You can always enter your Home with the second icon in the Unity interface on the left side, that has the house icon. That's Home.

Once you find the compressed script in Downloads, just right click on it and select Extract Here...

When it is extracted, and if it is in Downloads, you can execute it with running in terminal:

sudo bash ~/Downloads/boot_info_script*.sh

Type it as it is, linux makes difference between small caps and capitals. You can find terminal by opening the Dashboard (the first icon in Unity or pressing the Super key on the keyboard, with the windows logo) and typing terminal in the search line.

Executing the script will create a results.txt file in the same folder where the script is. Just attach the file here or post the content (copy-paste). If you are pasting the content it's better to include it in code tags, just select the text you want to include and hit the # button in the toolbar above when creating the post.

---

### Post by Snipeya on 2011-11-20
Ok so I've downloaded right clicked and extracted it now I have a file and a zip box, where do I type the sudo bash thing, step by step please I'm absolutely useless!!! lol

---

### Post by darkod on 2011-11-20
It's already answered...

Hit the windows logo key on the keyboard. That open the Dashboard. In the search box type terminal, that will find the program for you and display an icon.
Click it and that opens the Terminal (a command prompt program).
At the command line just type the sudo bash command and hit Enter.
That creates results.txt in the Downloads folder.
Post the content here.

---

### Post by Snipeya on 2011-11-20
Right I think I got you with where to write it so I copy and pasted it in terminal and hit enter. It then says password for me but when I type in my password and hit enter it says no such file or directory

---

### Post by darkod on 2011-11-20
C'mon man, help me out. I'm working blind here...

I am working under the assumption that the script was extracted in the Downloads folder. If it's in different one, the command will need to change, but that's easy to figure out yourself.
Also, I already mentioned earlier that when typing you need to type exactly for linux, it makes difference between Downloads and downloads.
Listen, it's easiest to move it into Home. Just open Home/Downloads and copy the extracted script to your Home folder.
Then in terminal the command would be:

sudo bash ~/boot_info_script*.sh

Make sure you know exactly where it is, also confirm the script name, and adjust the command if needed. The ~ sign means Home, it's the same when typing commands.

---

### Post by sanderd17 on 2011-11-20
> **Snipeya said:**
> Right I think I got you with where to write it so I copy and pasted it in terminal and hit enter. It then says password for me but when I type in my password and hit enter it says no such file or directory

It's clearly the first time you use a terminal.

As said above, you need to do


```
sudo bash /path/to/script/boot_info_script*.sh
```

Where you fill in the path to your script. (btw, ~/ is short for your home directory, so /home/username).  So if it's in your downloads, you do

```
sudo bash ~/Downloads/boot_info_script*.sh
```

If it's in your home directory, you do

```
sudo bash ~/boot_info_script*.sh
```

etc

If you don't give the right path, and the right file name, it will not find the file you ask. So that's the error you get.

---

### Post by Snipeya on 2011-11-21
Hi Sanderd17 yes I've never used terminal before and I've done what your telling me, it's actually called itself boot_info_script060 and so I tried typing that as well and it comes up with the same results no matter what I type. I found my hard drive and it looks as though it is in the 21gb that I took from D: drive so would it be ok to format that drive wiping ubuntu off and then will I be able to use windows again??

---

### Post by sanderd17 on 2011-11-22
> **Snipeya said:**
> Hi Sanderd17 yes I've never used terminal before and I've done what your telling me, it's actually called itself boot_info_script060 and so I tried typing that as well and it comes up with the same results no matter what I type. I found my hard drive and it looks as though it is in the 21gb that I took from D: drive so would it be ok to format that drive wiping ubuntu off and then will I be able to use windows again??

It's normal you see some terminal output, you can post that here (between CODE tags, click on the #-icon in edit mode). But the most important part should be the file RESULTS.txt that it created. You should also post it here.

Formatting your hdd (or the ubuntu partition) will leave you with a broken MBR. That's probably just as hard to fix as your problem now, so I won't do that.

---

### Post by Snipeya on 2011-11-22
danny@Danny-Aspire-T180:~$ sudo bash ~/boot_info_script*.sh
[sudo] password for danny: 
bash: /home/danny/boot_info_script*.sh: No such file or directory
danny@Danny-Aspire-T180:~$ 
danny@Danny-Aspire-T180:~$ sudo bash ~/boot_info_script*.sh
bash: /home/danny/boot_info_script*.sh: No such file or directory
danny@Danny-Aspire-T180:~$ 

Thats all I get no matter what I type :(

---

### Post by darkod on 2011-11-22
But is it in the Home folder or not?
Try with:
sudo bash ~/Downloads/boot_info_script*.sh

Like we said plenty of times:
1. Locate the extracted script (the .sh file).
2. Copy or move it to Home.
3. Execute it with the command you already tried.

If the script is in different folder you can try all you want, you will always get the same error message.

---

### Post by Snipeya on 2011-11-22
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    14,329,979    14,329,917  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     14,329,980   163,814,804   149,484,825   6 FAT16
/dev/sda3         163,814,805   268,065,468   104,250,664   7 NTFS / exFAT / HPFS
/dev/sda4         268,066,814   312,580,095    44,513,282   5 Extended
/dev/sda5         268,066,816   308,912,127    40,845,312  83 Linux
/dev/sda6         308,914,176   312,580,095     3,665,920  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E6E41B2116D9B5D2                       ntfs       PQSERVICE
/dev/sda2        2ED4F4AED4F47A03                       ntfs       ACER
/dev/sda3        7E784B2D784AE40D                       ntfs       DATA
/dev/sda5        a9d0cd0e-1e08-4a55-8505-28c826b63caf   ext4       
/dev/sda6        b3036e8c-03c2-4f66-96ad-bb7dedfbc68e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 11.10 i386 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root a9d0cd0e-1e08-4a55-8505-28c826b63caf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root a9d0cd0e-1e08-4a55-8505-28c826b63caf
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a9d0cd0e-1e08-4a55-8505-28c826b63caf
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9d0cd0e-1e08-4a55-8505-28c826b63caf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a9d0cd0e-1e08-4a55-8505-28c826b63caf
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9d0cd0e-1e08-4a55-8505-28c826b63caf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a9d0cd0e-1e08-4a55-8505-28c826b63caf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a9d0cd0e-1e08-4a55-8505-28c826b63caf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ED4F4AED4F47A03
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a9d0cd0e-1e08-4a55-8505-28c826b63caf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b3036e8c-03c2-4f66-96ad-bb7dedfbc68e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
00000010  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
00000020  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
00000030  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
00000040  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
00000050  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
00000060  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
00000070  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
00000080  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
00000090  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
000000a0  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
000000b0  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
000000c0  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
000000d0  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
000000e0  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
000000f0  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
00000100  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
00000110  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
00000120  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
00000130  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
00000140  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
00000150  4d 9d 8f 4d 9d 8f 4d 9d  8f 4d 9d 8f 4d 9d 8f 4d  |M..M..M..M..M..M|
00000160  9d 8f 4d 9d 8f 4d 9d 8f  4d 9d 8f 4d 9d 8f 4d 9d  |..M..M..M..M..M.|
00000170  8f 4d 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 9d 8f  |.M..M..M..M..M..|
00000180  4d 9d 8f 4d 9c 8e 4c 9e  90 4e 9d 8f 4d 9a 8c 4a  |M..M..L..N..M..J|
00000190  9d 8f 4d a0 92 50 98 8a  48 8e 80 3e ad 9f 64 00  |..M..P..H..>..d.|
000001a0  a2 94 52 8c 7e 3c ab 9d  5b 9d 8f 4d a1 93 51 99  |..R.~<..[..M..Q.|
000001b0  8b 49 9d 8f 4d 9d 8f 4d  9d 8f 4d 9d 8f 4d 00 fe  |.I..M..M..M..M..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 40 6f 02 00 fe  |...........@o...|
000001d0  ff ff 05 fe ff ff df 46  6f 02 23 f1 37 00 00 00  |.......Fo.#.7...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by Snipeya on 2011-11-22
Now I get you, can you tell me everything step by step I moved the first bit to home but never did the sh file!!! Bare in mind I have no idea what I'm doing !!!

---

### Post by darkod on 2011-11-22
/dev/sda2    *     14,329,980   163,814,804   149,484,825   6 [COLOR=Red]FAT16[/COLOR]

This looks like your problem. Somehow the type of the Vista partition has changed to FAT16. It should probably be NTFS.
Usually if this happens in error, the files are there, just the partition is wrongly marked in the partition table.

But I have no big experience in changing partition types without losing the data so you might wanna wait for second opinion with more instructions.

Let me search for some options.

---

### Post by darkod on 2011-11-22
Sorry, but I have nothing to suggest that will be fairly simple and guarantee your data. Maybe someone else will jump in if they have some advice.

---

### Post by Snipeya on 2011-11-22
Would this help I have no idea ?? [http://www.ntfs.com/bootdisk_partitionrecovery.htm](http://www.ntfs.com/bootdisk_partitionrecovery.htm)

---

### Post by darkod on 2011-11-22
Not sure, it says it's for deleted partitions which your isn't. Plus it's not a free solution, you pay for it.

One free tool, and very popular, is Testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

But it's very powerful and you need to take care with it. That's why I didn't suggest it.

Basically you need to tell it to scan your hdd, and if it discovers the second partition (/dev/sda2) as NTFS tell it to write (save) the changes. And that's it.

But be careful because by selecting wrong options things can go really wrong. And I haven't used it lot, so don't ask me to tell you step by step, too big responsibility. :) Not looking at your computer I can't tell you what to press.

---

### Post by sanderd17 on 2011-11-22
Maybe it's good to ask the advise of Oldfred on this. I'll see if he's willing to answer.

---

### Post by MG&amp;TL on 2011-11-22
@snipeya-I sympathise, but you'll be OK. Done this before and something pulled it through. Nine times out of ten on these forums these cases are solved satisfactorarily.

Just a 'chin-up' post. :)

---

### Post by oldfred on 2011-11-22
I have seen just changing the type with Disk Utility work and I know the sfdisk export & re-import work.

Either way I would back up partition table first.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

I notes are for this with a change to type 83 for a Linux partition. Not sure if it is 07 or blank 7 or just 7.
# to change sda2 to type  7
sudo sfdisk --change-id /dev/sda 2  7


If using Disk Utility it is 0x07 for NTFS.

---

### Post by Snipeya on 2011-11-24
Well I've sorted it. Done a fresh install of windows which left me with about 500 mb left on C:. Removed partition saved all my photos to disk and then deleted everything else of the computer and its like a brand new computer... literally!

---

### Post by MG&amp;TL on 2011-11-24
...pleased you sorted it. What became of ubuntu?

---

### Post by Snipeya on 2011-11-27
Ubuntu is gone for the moment hoping to get a cheap laptop in the future to install it and play around with it ;)

---

