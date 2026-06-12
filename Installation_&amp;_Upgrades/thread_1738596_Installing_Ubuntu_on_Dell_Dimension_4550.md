---
title: "Installing Ubuntu on Dell Dimension 4550?"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by TheSingingCoyote on 2011-04-25
Hello. I have been trying to install Ubuntu 10.10 on a Dell Dimension 4550. It installed, but when I try to boot it, I have problems. It keeps giving me the error: "error: file not found. grub rescue>"

What do I do?

Thanks!
-Mallory

---

### Post by Sef on 2011-04-25
Instead of installing, go down to check disk for errors. I suspect either the download, burn, or disk is not good.

---

### Post by TheSingingCoyote on 2011-04-25
How do I check the disk for errors?

EDIT: When I click F2 Nothing happens. It ignores that..but I know beforehand the harddrive looked fine...Also the DVD is fine. I already tried installing again. Same problem. 

Any other reasons for this problem?

---

### Post by mörgæs on 2011-04-25
This is an older machine. How much memory does it have?

---

### Post by TheSingingCoyote on 2011-04-25
It should have enough memory. I believe the harddrive is 250 gig...but can't remember for sure...

---

### Post by TheSingingCoyote on 2011-04-25
I hate to double-post, but as a side note, I tried the terminal on the Live DVD boot, and now it is saying:

> grub-probe: error cannot find a device for /boot (is /dev mounted?).

---

### Post by coffeecat on 2011-04-25
> **mörgæs said:**
> This is an older machine. How much memory does it have?

> **TheSingingCoyote said:**
> It should have enough memory. 

mörgæs asked you an important question. How much RAM does the machine have?

---

### Post by TheSingingCoyote on 2011-04-25
> **coffeecat said:**
> mörgæs asked you an important question. How much RAM does the machine have?

Right, I am not avoiding the question, I am just a novice and have no idea...How do I check?

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> Right, I am not avoiding the question, I am just a novice and have no idea...How do I check?

Go into the BIOS - that will tell you. I can't remember the key you press for the BIOS on a Dell, but I believe that when you first switch on you get a screen which says something like, "press *<something*> for setup". "Something" will be del or F2 or F10, or - um - something. :wink: Don't change anything; just read what it tells you about RAM.

I googled your Dell model and all I could determine was that it would have a minimum of 128MB and a maximum of 1GB. Being a Dell, it could be anything between those figures depending on the specification of the original order. The question is important because insufficient RAM is one of the commonest problems for what you describe. If you have 512MB or more, that should be fine. The live CD needs more RAM than a permanent installation, but if you have 256MB, say, it's possible that the installer  appeared to have struggled through but created a corrupted system.

---

### Post by TheSingingCoyote on 2011-04-25
I tried to look, but I can't find it. I pressed F2, and nothing happened. I tried F10, and it still took me to the error screen. I have no idea still...


EDIT: It has 512 MB...So I guess that's not the problem...

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> I tried to look, but I can't find it. I pressed F2, and nothing happened. I tried F10, and it still took me to the error screen. I have no idea still...

Googling took me to this:

[http://support.dell.com/support/edocs/SYSTEMS/dim4550/syssetup.htm#1097056](http://support.dell.com/support/edocs/SYSTEMS/dim4550/syssetup.htm#1097056)

> [SIZE=2]2. When the DELL logo appears, press <F2> immediately to enter the   system setup program.[/SIZE]You'll find the memory information on the main screen.

---

### Post by TheSingingCoyote on 2011-04-25
I actually just found the memory. It says 512 MB...

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> I actually just found the memory. It says 512 MB...

That's good. 512MB is enough to run Ubuntu so that isn't the problem. Some people may tell you it is insufficient, but I would disagree with them. It's tight but I can run Ubuntu just fine on a 6-year old laptop with only 512MB RAM.

Anyway, to your problem. The next step I would suggest is to run a special diagnostic script to see what might be the problem. I wanted to be sure you had enough RAM before suggesting this.

Boot up the live CD, make sure you can connect to the interent with it, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script, following the instructions there. If you have any problems with those instructions, post back and we can help you. When you post the contents of the RESULTS.txt file please remember to enclose it between [noparse]```
 and 
```[/noparse] tags for legibility. This is very important. You can use the # icon on the message toolbar for this.

---

### Post by TheSingingCoyote on 2011-04-25
I can't access the internet with it right now, since I don't have a wireless card yet, and the cord doesn't work to connect it to the internet. Is there any other way? Otherwise, I will have to wait...

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> I can't access the internet with it right now, since I don't have a wireless card yet, and the cord doesn't work to connect it to the internet. Is there any other way? Otherwise, I will have to wait...

OK. That's often a problem when running a live CD.

Use whatever system you are posting from to download the bootscript file. It's only about 69KB. It doesn't matter if the system is Windows or MacOS or whatever. Copy the bootscript file to a pendrive or USB drive of some sort. Then boot up the live CD, plug in the pendrive and copy the file to the live desktop. You can then run it from the desktop with:

```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by TheSingingCoyote on 2011-04-25
> **coffeecat said:**
> That's good. 512MB is enough to run Ubuntu so that isn't the problem. Some people may tell you it is insufficient, but I would disagree with them. It's tight but I can run Ubuntu just fine on a 6-year old laptop with only 512MB RAM.

Anyway, to your problem. The next step I would suggest is to run a special diagnostic script to see what might be the problem. I wanted to be sure you had enough RAM before suggesting this.

Boot up the live CD, make sure you can connect to the interent with it, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script, following the instructions there. If you have any problems with those instructions, post back and we can help you. When you post the contents of the RESULTS.txt file please remember to enclose it between [noparse]```
 and 
```[/noparse] tags for legibility. This is very important. You can use the # icon on the message toolbar for this.

It gave me a read only document? Is this normal?

---

### Post by TheSingingCoyote on 2011-04-25
It told me to run ```
sudo bash boot_info_script055.sh
```. I typed that in, but it didn't recognize that. 

Then I tried 

```
su -
bash boot_info_script055.sh
```


It did recognize that, but then it prompted me for a password, and I tried typing in my computer's password, but it said the authentication failed...

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> It gave me a read only document? Is this normal?

You mean the boot info script? If that's on a Windows machine, then don't worry about it. It will sort itself out when you transfer it to the Ubuntu live system.

> **TheSingingCoyote said:**
> It told me to run ```
sudo bash boot_info_script055.sh
```. I typed that in, but it didn't recognize that. 

You forgot a bit. If you simply opened a terminal it will be looking in the home folder for the script. If you copied the script to the Desktop, it won't find it. Copy the script to the desktop and run what I posted before:

```
sudo bash ~/Desktop/boot_info_script*.sh 
```Make sure you get "Desktop" right - not "desktop". Linux, unlike Windows, is case sensitive.

> **TheSingingCoyote said:**
>  Then I tried 

```
su -
bash boot_info_script055.sh
```It did recognize that, but then it prompted me for a password, and I tried typing in my computer's password, but it said the authentication failed...

By running 'su -i' you were trying to log in as root and it was prompting you for root's password, which doesn't exist in Ubuntu. Don't try that - it won't work. Go back to the sudo bash command but make sure you type the lot.

One other thing, and apologies for forgetting this. Once you've got the RESULTS.txt file on the live desktop you will need to copy that to a pendrive to transfer it back to Windows. (? - is it Windows you are having to use?) Don't try to open the file in Windows. Windows text editors use a different newline convention to Unix ones and it will garble the formatting of RESULTS.txt. Simply attach the RESULTS.txt file using the "manage attachments" button below the message field or the paperclip icon in the message toolbar. I will then repost it in code tags for you so that others can see it if they wish to help too.

By the way. **Are** you using Windows to post? If you are using MacOS you can open the file in OSX's text editor.

---

### Post by TheSingingCoyote on 2011-04-25
No, I managed to get the internet working on the Live install. It still came up as a text file. So that's not right? Or?

---

### Post by coffeecat on 2011-04-25
boot_info_script055.sh **is** a text file. It is a script which you execute with the sudo bash command. Simply run the sudo bash command. Then you get another text file called RESULTS.txt which is not a script. This is what we need to see.

---

### Post by TheSingingCoyote on 2011-04-25
> **coffeecat said:**
> You forgot a bit. If you simply opened a terminal it will be looking in the home folder for the script. If you copied the script to the Desktop, it won't find it. Copy the script to the desktop and run what I posted before:

```
sudo bash ~/Desktop/boot_info_script*.sh 
```Make sure you get "Desktop" right - not "desktop". Linux, unlike Windows, is case sensitive.


I'm not sure what you mean by this. Did you mean home folder instead of Desktop in the last sentence? If so, how do I do this? Apologies for being so new to all this! I really appreciate your help!

---

### Post by coffeecat on 2011-04-25
The "home" folder is more-or-less the Linux equivalent of "My Documents" in Windows XP.

If you look in the root of the filesystem in a Linux system, you'll see a folder called "home". In that you will find one folder for each account. Say there are two accounts, "fred" and "bill", there will be two folders, fred and bill. These are the home folders for the fred and bill accounts. In each of these will be various folders, Music, Documents, and so on for personal files. There will also be a "Desktop" folder for the desktop - just as in Windows. In fact looking at my Windows 7 filesystem, I see this for the desktop:

C:\Users\myaccountname\Desktop

I think Microsoft has been taking lessons from Linux, because that is almost the same as the path to my desktop in Ubuntu, which is /home/myaccountname/Desktop.

Anyway, when you run the live CD, it creates a temporary user account called "ubuntu" which is the one you use when run the live session. The path to the ubuntu home folder is /home/ubuntu, and the path to ubuntu's Desktop is /home/ubuntu/Desktop. When you open a terminal, you are "in" /home/ubuntu. When you ran:

```
sudo bash boot_info_script055.sh
```... it went, 'uh-oh, can't find that' and errored out on you. You need to tell it that the file is in the Desktop. Either what I posted before:

```
sudo bash ~/Desktop/boot_info_script*.sh
```Note that wildcards are similar to how you use them in the Windows command prompt. Or you could do:

```
cd Desktop
sudo bash boot_info_script*.sh
```"cd" doing exactly what cd does at a DOS prompt.

---

### Post by TheSingingCoyote on 2011-04-25
Here are the results. Warning: LONG!

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   485,326,847   485,324,800  83 Linux
/dev/sda2         485,328,894   488,396,799     3,067,906   5 Extended
/dev/sda5         485,328,896   488,396,799     3,067,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        72e63d08-216b-4c77-9cf2-badb065f0b2b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        aba49f29-98fd-4096-b1ea-c76f2d91d007   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 72e63d08-216b-4c77-9cf2-badb065f0b2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 72e63d08-216b-4c77-9cf2-badb065f0b2b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 72e63d08-216b-4c77-9cf2-badb065f0b2b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=72e63d08-216b-4c77-9cf2-badb065f0b2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 72e63d08-216b-4c77-9cf2-badb065f0b2b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=72e63d08-216b-4c77-9cf2-badb065f0b2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 72e63d08-216b-4c77-9cf2-badb065f0b2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 72e63d08-216b-4c77-9cf2-badb065f0b2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=72e63d08-216b-4c77-9cf2-badb065f0b2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aba49f29-98fd-4096-b1ea-c76f2d91d007 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 214.8GB: boot/grub/core.img
  60.3GB: boot/grub/grub.cfg
 103.3GB: boot/initrd.img-2.6.35-22-generic
    .4GB: boot/vmlinuz-2.6.35-22-generic
 103.3GB: initrd.img
    .4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ce 66 9b 1f d2 8e 3e 03  35 9c 7e ec 1c a0 7b 01  |.f....>.5.~...{.|
00000010  13 0b 24 bb cf 26 fe fa  c3 c2 ca 69 33 88 61 28  |..$..&.....i3.a(|
00000020  d8 07 2c f2 65 f5 58 52  ce 34 8d c6 1a 26 4c 13  |..,.e.XR.4...&L.|
00000030  1c f4 16 31 8a f3 58 27  05 a1 e8 62 da 3f 3b 24  |...1..X'...b.?;$|
00000040  c7 75 64 0c fd 4d e9 91  8d 24 92 41 2b 53 75 17  |.ud..M...$.A+Su.|
00000050  a6 be 8d 74 72 eb 19 c7  09 20 29 98 3b 8d 93 1d  |...tr.... ).;...|
00000060  0f 20 5b a4 7d 60 07 b6  2f 5a ee b4 bb 16 90 90  |. [.}`../Z......|
00000070  34 51 42 40 51 90 be 75  1e 1d 21 be 24 f5 82 24  |4QB@Q..u..!.$..$|
00000080  04 48 52 e1 cc d9 6e c6  85 e6 f1 c4 2f 8c fb 59  |.HR...n...../..Y|
00000090  8f 4d 00 f0 00 23 0e bf  33 96 da 20 1e 31 bd 57  |.M...#..3.. .1.W|
000000a0  e4 de 2f 38 90 75 f7 69  44 14 c6 e9 97 b2 0f c2  |../8.u.iD.......|
000000b0  db 06 19 6d 75 90 c6 7e  2c 39 55 50 a2 92 cb 3c  |...mu..~,9UP...<|
000000c0  41 2d 59 38 f0 a6 0d 64  fe 8f 01 a5 0d e4 de cc  |A-Y8...d........|
000000d0  c2 01 8c 77 d5 de bd f2  12 a2 0d a9 72 0a e8 cd  |...w........r...|
000000e0  48 1e 48 11 eb b2 c8 63  2a 08 6b ba 36 2a 05 08  |H.H....c*.k.6*..|
000000f0  66 96 68 46 84 66 1e 03  ec 5a 08 3f 92 ea 30 1b  |f.hF.f...Z.?..0.|
00000100  1e 59 da 05 39 7e ab 57  29 0f 0d d5 6d 36 4b 26  |.Y..9~.W)...m6K&|
00000110  c2 09 31 f2 87 b9 33 76  b2 04 5b 8f 04 85 59 43  |..1...3v..[...YC|
00000120  17 d4 10 ec 44 bd 16 1d  47 57 14 72 b5 90 48 d7  |....D...GW.r..H.|
00000130  af f0 82 48 9f 68 e5 b4  96 10 b1 c6 2e a2 68 2c  |...H.h........h,|
00000140  51 ed b6 f2 88 39 32 e9  2c b1 c2 41 90 45 bc 5b  |Q....92.,..A.E.[|
00000150  eb 14 93 4a 7c 90 42 34  a6 c8 57 91 78 fd 92 f0  |...J|.B4..W.x...|
00000160  81 82 1f 67 34 65 e6 13  e6 c2 45 e0 db 49 e4 24  |...g4e....E..I.$|
00000170  fb d2 47 8f dd b5 1b 49  75 8a 62 77 8e 0d 36 f0  |..G....Iu.bw..6.|
00000180  82 17 0f 3f 59 98 0e b3  c5 16 fa c8 67 b1 e9 3c  |...?Y.......g..<|
00000190  91 76 2d 0c df 42 a2 17  69 ca 2b 58 09 9f 69 22  |.v-..B..i.+X..i"|
000001a0  0e 0f 48 f3 b3 03 19 05  4f 14 9d 90 99 63 f7 c3  |..H.....O....c..|
000001b0  24 1f c1 a5 2a 1d 3b df  76 2c 88 08 d2 36 00 fe  |$...*.;.v,...6..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 2e 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> Here are the results. Warning: LONG!

Fear not. I have seen **much** longer! :)

What is frustrating is that I can see nothing wrong in your boot script output. Grub is correctly installed to the mbr looking in sda1, which is correct. The menu entries seem OK with the correct UUIDs, and you have the kernel that they are looking for. And the file /etc/fstab looks OK. The only odd thing is the "Unknown BootLoader  on sda2" message which I don't remember having seen before. Since sda2 is your extended partition and has no role in the boot process, I don't think this is relevant.

OK. Let's have a recap. You say that when you try to boot, you get an error which says, "error: file not found. grub rescue>" Is that the exact message? I'm going to ask you to try booting again and note down exactly what the error says and to post it. There may have been something else which may give us a clue.

Also - try starting up the machine (without the live CD) and as soon as the POST screen (the Dell splash) appears, press the shift key and keep it held until a grub menu appears. (It's possible that it won't - the error message you describe may mean that the grub menu won't appear at all. Give it 2 or 3 tries.) The menu, if it appears, should show two entries for "Ubuntu, with Linux 2.6.35-22-generic", the second with "recovery mode". And also two entries for memory test. Highlight the first menu entry and press 'e'. You will then be able to edit the code for that menu entry. Find the line that starts "linux    /boot/vmlinuz-2.6.35-22-generic" and remove the words "quiet splash" from the end of the line. Now press ctrl-X to attempt to boot. A load of text will scroll past rapidly. If it stops take a note of the last couple of lines. Hopefully, there will be an error which may give a clue.

Lastly, I'll pm a couple of people to ask them to take a look in case I've missed something. I think they're off-line at the moment, so it may be some time before one or the other joins in.

---

### Post by TheSingingCoyote on 2011-04-25
The exact error is:

```
GRUB loading.
error: file not found.
grub rescue>
```

I tried holding down the shift key, and nothing happened...


EDIT: I got a BIOS page loaded by holding down shift. 


Says at the bottom (after the basic stuff) :


```
Keyboard failure
error: file not found.
grub rescue>
```

---

### Post by collisionystm on 2011-04-25
> **TheSingingCoyote said:**
> Hello. I have been trying to install Ubuntu 10.10 on a Dell Dimension 4550. It installed, but when I try to boot it, I have problems. It keeps giving me the error: "error: file not found. grub rescue>"

What do I do?

Thanks!
-Mallory



It is either a bad cd burn, bad .iso OR

your cd drive is just dirty lol. 

Get a can of air and clean that thing out!!!!

---

### Post by TheSingingCoyote on 2011-04-25
> **collisionystm said:**
> It is either a bad cd burn, bad .iso OR

your cd drive is just dirty lol. 

Get a can of air and clean that thing out!!!!

No, it isn't. The ISO is fine, the DVD is fine, and the drive is very clean. I tried spraying air into it, and nothing came out.

---

### Post by coffeecat on 2011-04-25
> **TheSingingCoyote said:**
> The exact error is:

```
GRUB loading.
error: file not found.
grub rescue>
```I tried holding down the shift key, and nothing happened...

Yes, that's what I feared. If it's the grub.cfg file it's saying it can't find, then holding the shift key won't reveal the grub menu. 

> **TheSingingCoyote said:**
> EDIT: I got a BIOS page loaded by holding down shift. 


Says at the bottom (after the basic stuff) :


```
Keyboard failure
error: file not found.
grub rescue>
```

Are you sure that was a BIOS page? You accessed the BIOS by pressing F2 before. I don't think the BIOS would tell you anything about grub. The "Keyboard failure" message is intriguing. Do you have another keyboard you can try? Admission: I'm beginning to be out of ideas here.

One other thing you could try, but I have little confidence it will help. Boot up with the live CD and open System > Administration > Gparted. Right-click on the /dev/sda1 partition and choose "check". I think you have to click on the green "apply" icon for this to be actioned. It will carry out a filesystem check.

I'm beginning to wonder if there is a hardware fault somewhere. What were you using the machine for before? How long ago?

---

### Post by collisionystm on 2011-04-25
If you are having a problem with files not being loaded correctly, it is one of those.

Its not rocket science. I suggest you burn another DVD and this time do it at 4x or 2x.

---

### Post by coffeecat on 2011-04-25
> **collisionystm said:**
> If you are having a problem with files not being loaded correctly, it is one of those.

Its not rocket science. I suggest you burn another DVD and this time do it at 4x or 2x.

I don't think the OP is having problems with the live CD but with the permanent hard drive installation that they have already created. Perhaps the OP can confirm this.

---

### Post by mörgæs on 2011-04-25
Have you tried installing using the alternate CD? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Though the regular ISO should work equally well, there are many examples that the alternate does the job best.

---

### Post by confused57 on 2011-04-25
> **mörgæs said:**
> Have you tried installing using the alternate CD? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Though the regular ISO should work equally well, there are many examples that the alternate does the job best.

+1
I had a 4550, which had no problems running Ubuntu.  Try pressing F2 during boot to access bios & check the version of the bios...it could be the bios needs updating in order to access drives larger than 137 GB.

Rather than risk updating the bios, I'd recommend reinstalling with the alternate cd, use manual partitioning, set up approximately a 25GB /(root) partition, approximately 1.5GB swap, & the rest for /home.

Here are some excellent screenshots of the alternate install, thanks to Herman:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

The keyboard failure, as coffeecat mentioned, may indicate a hardware problem; but it might be worth trying with the alternate cd.

---

### Post by coffeecat on 2011-04-25
@TheSingingCoyote, someone has just pm'd me with an excellent suggestion. Your hard drive is 250GB, but some older BIOSs cannot see beyond 137GB. Your main Ubuntu partition, sda1, is 248.5 GB in size. If your grub.cfg is sitting beyond the 137GB point - quite possible with a Linux filesystem - then it's beyond the point it can be read at that stage of the boot process.

Have a look in your BIOS to see if there is any mention of this. If this is the problem, then I believe you would need to re-install, creating a separate boot partition at the beginning of the drive.

**EDIT**: I see confused57 has also mentioned the 137GB limitation. Worth looking into.

---

### Post by Quackers on 2011-04-25
/boot/grub/grub.cfg isn't after the 137GB mark, but /boot/grub/core.img is
```
=================== sda1: Location of files loaded by Grub: ===================


 214.8GB: boot/grub/core.img
  60.3GB: boot/grub/grub.cfg
 103.3GB: boot/initrd.img-2.6.35-22-generic
    .4GB: boot/vmlinuz-2.6.35-22-generic
 103.3GB: initrd.img
    .4GB: vmlinuz
```

---

### Post by TheSingingCoyote on 2011-04-25
Okay, so I am using my "new" computer right now! I found an old 20 gig hard drive (sadly I will have to replace that eventually since it is nearly worthless now), but it *was* a hard drive error. 

It's a little slow, but not too bad. Will have to fix that later.



Thank you everyone for your help! It is much appreciated, especially coffeecat! Thanks for dealing with me! lol

-Mallory

---

### Post by mörgæs on 2011-04-26
Good, please mark the thread 'solved'.

---

