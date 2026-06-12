---
title: "Howto add GRUB to Windows 7 boot menu"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by wombathuffer on 2009-11-30
** Dual boot bcdedit (Windows 7 bootloader) into GRUB**

So - it happened that I decided to run windows 7 on the first two partitions of my disk and Ubuntu 9.10 on the rest.

After a neat and tidy windows install with everything working, I installed the Karmic Koala with everything working.. Booting back into Windows to install some software from my DVD-Drive, and *poof*, it disappeared - gone and no sign of it in the device manager.

I spend a week or so, trying to collect drivers to my TSSTCorp CD/DVD-drive on my Zepto 66W25WD with an Intel ICH8M chipset, and installing the Windows 7 beta again and rebooting into Ubuntu to compare the driver data..

Then I reinstalled windows 7 and ran all them windows updates, and the DVD-drive was still present there.. 
YAY its working! Lets get cracking and reinstall grub!
...or not - when grub was reinstalled, my CD-drive disappeared again.

** CONCLUSION:** (tadaaa!!!)
The Famous GRUB-bootloader is making my CD/DVD-drive invisible.
There got to be some settings in Windows 7s own boot manager, which implies to the ATAPI-controller.

okay - it seemed that I was stuck..
Got Ubuntu installed and I cant use grub... Great! Lets bring a windows DVD and a Ubuntu-CD around with my laptop, in case I want to install something from a DVD on windows... NOT!

I read a sh'tload of post concerning a regedit, removing keys for  upper- lower filters in a regedit class, in windows, but as Murpheys law dictates, I didn't have the upper- lower filter keys to delete.

**SOLUTION:**
I wanted to keep my Windoze 7 MBR, and boot into grub.
So when I got my windows 7 mbr without any ubuntu-options, I booted the Ubuntu CD and as I still got a working menu.lst (or grub.cfg in my case) in /boot/grub of my Ubuntu-partition, I did:

```
 sudo -i
```(stay in root and [COLOR=Red]recheck your future commands for typos before you hit enter![/COLOR])

```
 mkdir /media/tmp
```(make a folder called /media/tmp)

```
 mount /dev/sda5 /media/tmp
```(mount my Ubuntu /root partition into /media/tmp)

```
 grub-install --root-directory=/media/tmp /dev/sda
```(install grub with /media/tmp as root / on the MBR of /dev/sda)

And then I rebooted...
And there was much rejoice as grub was working again. YAY!

Then I booted my Ubuntu on my hdd, and found my two windows 7-drives (first one is the boot-partition second is the system-partition):

```
 ls -al /media/some-disk-id
```and
```
ls -al /media/System Reserved
```(I mounted my Windows system-drive into /media/win7 which I will refer to, further on..)

(if the /media-folders for windows, are not there, find out where they are, with

```
 sudo fdisk -l
```and mount them with 

```
 sudo mount /dev/sdaX /media/folder-of-own-choise
```.)


Then I dumped the grub-mbr into a bin file with the following command:

```
 sudo dd if=/dev/sda of=/media/win7/ubuntu.bin bs=448 count=1
```(dd the mbr from /dev/sda into the file /media/win7/ubuntu.bin and only the first 448 bytes of the MBR.

Why 448? MBR consists of 512 bytes, 448 bytes for the bootstrap and 64 bytes for the partition table, and as we only need the bootstrap we set bs=448)

I wasn't sure where windows is gonna look for the bin-file so I copied it to the win 7 boot-partition aswel:

```
 cp -rf /media/win7/ubuntu.bin /media/System Reserved
```With this bin file written, I rebooted and entered windows 7 in the grub menu (with my CD-drive not working, remember?)

Then I read up on the bcdedit-tool for customising the windows bootloader and did the following in a cmd run as an administrator:


```
 bcdedit /enum
```(Shows the OS the windows bootloader can see at the moment.)

```
 bcdedit /create /d "GRUB" /Application BOOTSECTOR
```(Create a new entry in the Windows boot menu, and call it Grub and look in the bootsector for further instructions.)

In return I got some kind of diskID, in my case: {f16e7bd4-dd5b-11de-80c1-e83d58bc56bc}

```
 bcdedit /set {f16e7bd4-dd5b-11de-80c1-e83d58bc56bc} device boot
```(Tells the bootloader to look for the bootstrap-information for grub on the Boot-partition.)

```
 bcdedit /set {f16e7bd4-dd5b-11de-80c1-e83d58bc56bc} PATH \ubuntu.bin
```(continue to tell the bootloader that the bootstrap info is in \ubuntu.bin)

```
 bcdedit /displayorder {f16e7bd4-dd5b-11de-80c1-e83d58bc56bc} /addlast
```(Showing GRUB as the last choice in the windows boot menu)

[COLOR=Red] OPTIONAL:[/COLOR]
```
 bcdedit /timeout 10
```(as I really dont have the patience to wait 30 sec when booting)


Then I rebooted to test the menu, and it smoothly went to the grub menu, and when choosing Windows 7 in the grub menu, it went straight into the Windows-menu, where I could choose between windows 7 and GRUB.

I tested a few times that I both could boot Ubuntu and Windows, and when I was sure it worked as intended, I  rebooted the Windows DVD, and installed the windows MBR from the command prompt on the Windows DVD, (when booting from it, entering "Repair" on the Windows 7 DVD) by doing:

```
 BootRec.exe /fixmbr
```and rebooted...

Now I got the windows 7 bootmanager first with a working visible DVD-drive in windows 7 and a second option, redirecting me to the grub boot menu with Ubuntu 9.10.


If anyone is interested I have posted the output of bcdedit /enum from windows:

```
 Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  da-DK
inherit                 {globalsettings}
default                 {current}
resumeobject            {f16e7bd5-dd5b-11de-80c1-e83d58bc56bc}
displayorder            {current}
                        {f16e7bd4-dd5b-11de-80c1-e83d58bc56bc}
toolsdisplayorder       {memdiag}
timeout                 5

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  da-DK
inherit                 {bootloadersettings}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {f16e7bd5-dd5b-11de-80c1-e83d58bc56bc}
nx                      OptIn
detecthal               Yes

Real-mode Boot Sector
---------------------
identifier              {f16e7bd4-dd5b-11de-80c1-e83d58bc56bc}
device                  boot
path                    \ubuntu.bin
description             GRUB

```and the menu.lst (mine is grub.cfg):

```
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
search --no-floppy --fs-uuid --set 5520d8ae-dc51-4339-9e46-2afbe5bd06ab
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
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
    search --no-floppy --fs-uuid --set 5520d8ae-dc51-4339-9e46-2afbe5bd06ab
    linux    /boot/vmlinuz-2.6.31-14-generic pci=noacpi root=UUID=5520d8ae-dc51-4339-9e46-2afbe5bd06ab ro  splash vga=799  quiet splash acpi=off
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5520d8ae-dc51-4339-9e46-2afbe5bd06ab
    linux    /boot/vmlinuz-2.6.31-14-generic pci=noacpi root=UUID=5520d8ae-dc51-4339-9e46-2afbe5bd06ab ro single  splash vga=799 acpi=off
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
    search --no-floppy --fs-uuid --set 16BA2FD4BA2FAEE5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by Mark Phelps on 2009-12-01
Hey ... this is a really AMAZING piece of work!  I'm impressed, really!

But ... I'm curious as to why you went through all this work instead of simply installing EasyBCD (from NeoSmart Technologies) and using it to add Ubuntu to the bootloader menu.

The new beta versions of EacyBCD claim to be able to work with GRUB2.

Not a criticism of what you did -- just interested in knowing if you tried the EacyBCD approach and discovered that it didn't work.

---

### Post by wombathuffer on 2009-12-01
I did that for several reasons really..

First of all, Im a bigger fan of using configurable solutions instead of '3rd party' software to handle it.. And until now I didnt find any solutions to my problem on the internet where EasyBCD had solved the problem. (Nor did I find any other noble users of grub whose CD-drives had disappeared, so I felt kind of alone with this problem.. :))

Secondly I would avoid my CD/DVD-drive to disappear again cause of another bootloaders than Windoze own BCDedit. (Does EasyBCD edit the existing MBR and bootmenu in windows, or is it installing a completely new one?)

Thirdly (is that a word?) - I do some times fancy inventing the bowl again... :P
 Well - I could try and install EazyBCD but I dont really feel like messing my MBR up again on purpose.. :P

---

### Post by ubestos on 2009-12-01
hello wombathuffer,

thank you for this how-to!!! Such a short and genius way to make the Win7 boot-loader loading GRUB. I was trying and looking for weeks to handle it, since I installed Win7, but no luck.

I am really want to know what is the reason that makes the way used in Vista become useless hier by Win7. Shortly the steps I used in Vista:

1. I backedup the loaderconfiguration:
```
bcdedit /export "E:\bcdbackup\BcdBackup"
```
2 then the well known way...
```
bcdedit /create {ntldr} /d "Ubuntu"
```
3.
```
bcdedit /set {ntldr} device partition=C:
```
4.
```
bcdedit /set {ntldr} path \custom\ubuntu.bin
```
5.
```
bcdedit /displayorder {current} {ntldr}
```
to remove the grub entry:
```
bcdedit /delete {ntldr} -f
```


Anyhow, your way worked very fine and I could boot into my ubuntu-9.10, I have to say it one more time! Thank you for sharing this!!! 

*low bow*

best greets from Berlin

PS: If we meet some day, I buy you a beer in return :)

---

### Post by wombathuffer on 2009-12-01
The bootloader-program it self is more or less the same in windows 7 as in vista.
The reason why your commands wont work in Windows 7 is because the native bootloader resides in a non-mounted partition on 100mb as default (way too much for a bootloader btw), which you have to assign a drive letter in Diskmanagement in Administration, first.

In vista you will find a bootmgr-file in c:\ (like xp's got ntldr), in Windows 7 the bootmgr file is in the root of the hidden boot partition. :)

---

### Post by ubestos on 2009-12-01
Ok, now I understood it :) thanks again

---

### Post by mogensen89 on 2009-12-27
Hey there...

I have got the Zepto 6625 WD too. I have installed the win 7, and I too discovered that the computer wouldn't find the dvd-drive - Any chance you could guide me to finding it 

ps. I know this is a ubuntu forum and my post does not concern ubunto whatsoever - but you seemed to know stuff :)


Hope you can help me - 

Thanks in advance m8
n' happy holidays :)

---

### Post by wombathuffer on 2009-12-27
> I have got the Zepto 6625 WD too. I have installed the win 7, and I too discovered that the computer wouldn't find the dvd-drive - Any chance you could guide me to finding it

Slightly off topic as you noticed yourself, but the 'default' solution to the missing CD/DVD-drive is as quoted here from

[http://en.kioskea.net/forum/affich-32903-i-cannot-viw-my-cd-rom-dvd-drive](http://en.kioskea.net/forum/affich-32903-i-cannot-viw-my-cd-rom-dvd-drive)

> go to start --> control panel --> system --> device manager --> under dvd/cd drives open + and look for yellow caution triangle icon  --> right click and delete  --> close window.
go to start  --> run --> type in "regedit" click ok  --> go to HKEY_LOCAL_MACHINE  --> open + on SYSTEM open + on CURRENTCONTROLSET open + on CONTROL open + on CLASS open + LOOK 4 {4D36E965-E325-11CE-BFC1-08002BE,etc.} and click on it  --> to screen on right look for "lower filters" and select it  --> right click and delete. Do the same for "Upper filters"  --> close window and restart computer.

---

### Post by mogensen89 on 2009-12-28
Yeah - I have read that a couple of places' too.
The thing is though, that I my regeditor doesn't show such filters.

Further it seems like the regeditor has got a line called "properties" in which I'm not allowed to enter. So I don't know what to do.

---

### Post by wombathuffer on 2009-12-28
To the first - are you sure Windows own bootmanager is the first when you bootup the drive?

Are you sure your drive works in other operating systems? (Not the "it worked in XP 2 days ago before I formated" - its not good enough - test it several times booting the ubuntu Cd or something.)

To the second, try doing it as administrator - you should be able to enter any properties then.

---

