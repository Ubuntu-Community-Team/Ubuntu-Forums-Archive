---
title: "Ubuntu Dual Boot Reinstall"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by EdenC on 2011-03-20
Hi There,

I've had lots of problems with my Ubuntu dual boot [more info here: [http://www.tomshardware.co.uk/forum/237420-38-ubuntu-win7-dual-boot-problem](http://www.tomshardware.co.uk/forum/237420-38-ubuntu-win7-dual-boot-problem)].

So now I just want to reinstall my Linux partition. How can I go about this without removing my Windows parition?

Thanks Alot,
EdenC

---

### Post by Quackers on 2011-03-20
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by EdenC on 2011-03-20
I don't mean to cause offense, but if you read the whole of the thread linked you will have notcied that the Ubuntu Live CD no longer works on my machine, making your suggestion impossible to follow through.

Thanks,
EdenC

---

### Post by tlcstat on 2011-03-20
Greetings,
I don't know what happened to the OP but great script! Thanks!
tlcstat

---

### Post by Quackers on 2011-03-20
Is your bios set to boot from cd first? It really is a must to get the cd booting, as all your available fixes will be done from there.

---

### Post by EdenC on 2011-03-20
Yes, I do know how to get to boot from the CD first as have got Ubuntu Live working fine before.

---

### Post by Quackers on 2011-03-20
I didn't suggest that you don't know how to do it. I asked you if you had set the bios. Many people use the F12 key (or similar) on a per boot basis, then forget to use it next time.
The fact remains that it is paramount for you to get the cd booting again. I suggest you look for methods of doing that first.

---

### Post by EdenC on 2011-03-20
How would I get the Ubuntu Live CD working again then?
The disk boots, goes to the purple screen and then sits with the flashing underscore in the top left hand of the screen.
I doubt this is something to do with not having the proper disk booting setup.

---

### Post by Quackers on 2011-03-20
These are the first symptoms you have mentioned.
Did you use a boot prompt to get it working before? Has the live desktop loaded before? What graphics card are you running? How much ram do you have?

---

### Post by EdenC on 2011-03-20
I simply chose to get Live CD working by changing my CPU options to always boot from the CD first. I have loaded the Live Desktop before (and this is where I made all my paritions). And (as metioned in the post linked in the OP), my system is made up of the following:

> I built my own computer with the following hardware: 

Asus Motherboard -> M4A88TD-M EVO 
Processor -> AMD Phenom II X4 965 3.40 GHz 
OCZ Stealth Stream Power Supply 2 [Power Supply] 
Pioneer DVD-RW DVR-118L ATA [DVD Drive] 
ATI Radeon HD 5600 Series [Graphics Card] 
4GB of RAM 

             								               							               							

---

### Post by Quackers on 2011-03-20
It's curious that you have booted to the live desktop previously, but you can't do that any more.
I can only suggest that you try again, and, when you get to the first purple screen (the one with the little man icon at the bottom) you press any key. Then choose your language and on the next screen press F6 key. Some boot options will appear at the bottom right of the screen. I would suggest first trying the nomodeset option and see if it then boots.

---

### Post by EdenC on 2011-03-20
Ok, this is odd...

I got to the purple screen, pressed any button, then chose my language. To test out whether or not I could run Ubuntu live from there, I chose to run Ubuntu. After some loading, here I am!

If there's any info you want to me get from Ubuntu Live, then please tell me now while I've managed to get it running!

---

### Post by Quackers on 2011-03-20
If you can run the boot script from my first post it will give a clearer idea of what is where.
It may be that grub has not been installed, or installed incorrectly.

---

### Post by EdenC on 2011-03-20
[http://i.imgur.com/DXynJ.png](http://i.imgur.com/DXynJ.png)

Above is a link to my partitions from GParted.

---

### Post by EdenC on 2011-03-20
As requested:       
 >   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 1638610944.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             210,944   819,410,943   819,200,000   7 HPFS/NTFS
/dev/sda3         819,410,944 1,638,610,943   819,200,000  83 Linux
/dev/sda4       1,638,610,944 1,953,523,711   314,912,768   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        46E8BADAE8BAC787                       ntfs       System Reserved               
/dev/sda2        B878BC9478BC52BC                       ntfs                                     
/dev/sda3        6a3296a6-2020-41a5-b52a-c721104cf166   ext4                                     
/dev/sda4        AA37-AAD2                              vfat                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###

---

### Post by Quackers on 2011-03-20
I see that Ubuntu is on sda3. That doesn't tell us where grub or its files are though.

---

### Post by EdenC on 2011-03-20
How can I find out where the GRUB files are then?

---

### Post by Quackers on 2011-03-20
We cross posted last time. 
You appear to have chopped the end of the boot script output off. Can you add the rest please?

---

### Post by EdenC on 2011-03-20
Thought we might have done. Sorry for not adding all the info, not used to using Ubuntu yet :p
Here you go:
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 1638610944.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             210,944   819,410,943   819,200,000   7 HPFS/NTFS
/dev/sda3         819,410,944 1,638,610,943   819,200,000  83 Linux
/dev/sda4       1,638,610,944 1,953,523,711   314,912,768   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        46E8BADAE8BAC787                       ntfs       System Reserved               
/dev/sda2        B878BC9478BC52BC                       ntfs                                     
/dev/sda3        6a3296a6-2020-41a5-b52a-c721104cf166   ext4                                     
/dev/sda4        AA37-AAD2                              vfat                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 6a3296a6-2020-41a5-b52a-c721104cf166
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 6a3296a6-2020-41a5-b52a-c721104cf166
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6a3296a6-2020-41a5-b52a-c721104cf166
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=6a3296a6-2020-41a5-b52a-c721104cf166 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6a3296a6-2020-41a5-b52a-c721104cf166
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=6a3296a6-2020-41a5-b52a-c721104cf166 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6a3296a6-2020-41a5-b52a-c721104cf166
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6a3296a6-2020-41a5-b52a-c721104cf166
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 46e8badae8bac787
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=6a3296a6-2020-41a5-b52a-c721104cf166 /               ext4    errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


 797.6GB: boot/grub/core.img
 617.3GB: boot/grub/grub.cfg
 420.3GB: boot/initrd.img-2.6.35-22-generic-pae
 797.6GB: boot/vmlinuz-2.6.35-22-generic-pae
 420.3GB: initrd.img
 797.6GB: vmlinuz

---

### Post by Quackers on 2011-03-20
Ok, thanks for the extra info.
Grub appears to be fine, as do its boot files.
So, to recap then, what exactly happens when you try to boot from the hard drive?
Do you get to a grub menu? If so, what exactly happens when you select Ubuntu?

---

### Post by EdenC on 2011-03-20
Ok, to recap:

I get to the GRUB menu.I then chose Linux. After that all I get is a blinking underscore in the top right hand corner, which stays there forever (well, until I reboot).

[By the way, thanks for all your help so far :KS]

---

### Post by Quackers on 2011-03-20
Your previous problems with the live cd could be clouding the issue. I would suspect that your system should be booting.
If I had known nothing of your previous problems I would suggest using the nomodeset option. It is still worth trying.
At the grub menu, when the Ubuntu option is highlighted, press the "e" key. On the next screen navigate to the end of the boot line which ends with "quiet splash". Using the backspace key remove quiet splash and then type in nomodeset then press ctrl+X to boot. See what happens.

---

### Post by EdenC on 2011-03-20
I did that and got a black screen and a load of text, which I took a picture of and upload here:
[http://i.imgur.com/Qphob.jpg](http://i.imgur.com/Qphob.jpg)

---

### Post by Quackers on 2011-03-20
And did it just stop there? Was there any hard disc activity?

---

### Post by EdenC on 2011-03-20
It just stopped there.
There was more info (in the form of some more black text) before the stuff in the pic, but this flew by so quick that I couldn't read it, meaning the stuff in the pic is all the info I got.

[Note: EDIT: Back Now]

---

### Post by Quackers on 2011-03-20
All that script comes up because the quiet splash was removed. That was supposed to give us a clue as to where the process stopped. Sadly it doesn't help me.
I take it that you removed the cd?
I'll ask another member to take a look, but I'm not sure if he's online at the moment.

---

### Post by EdenC on 2011-03-20
Yeah, the CD was removed.

---

### Post by Quackers on 2011-03-20
Ok, we can speak again later perhaps. I'll see if anyone else can suggest something.

---

### Post by coffeecat on 2011-03-20
> **Quackers said:**
> 
I'll ask another member to take a look, but I'm not sure if he's online at the moment.

Oh, yes I am, but I'm multi-tasking at the moment! :)

@EdenC, do you mind if I recap? I've read both your threads but it's easy to miss something when one comes in after some time. Correct me if I've got anything wrong.

First - you can boot from the live CD now? And you get a perfectly usable graphical live desktop running the CD? You were able to install Ubuntu to the hard drive, but you were never able to get to a GUI when booting from the HD - just a black screen with a blinking cursor. Correct? And you have an ATI radeon HD 5600 graphics card?

I agree with Quackers that it was necessary to try try the 'nomodeset' option in the kernel parameters - this sort of thing is often down to a graphics issue - but unfortunately it doesn't seem to have worked for you. A question: the screenshot you posted in post #23, was that where the scrolling text stopped or was there some more? By getting you to remove the 'quiet splash' options from the grub kernel line Quackers was hoping that you would see an error in the scrolling text. But the important error is usually in the last or last few lines before it stops scrolling. If that was a photo you took before it stopped scrolling, then we need to see the end of the messages.

---

### Post by EdenC on 2011-03-20
Yep, all that recap is correct.

And yes, that is at the end of the scrolling text, not during.

---

### Post by Quackers on 2011-03-20
It may be worth re-installng grub at this time, just for confirmation that it is ok.
From the live cd desktop please go to Applications > Accessories > Terminal and copy/paste these two commands in, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If that reports no errors, please reboot and choose Ubuntu from the grub menu.

---

### Post by EdenC on 2011-03-20
](*,)
Live CD is now not wanting to boot after I choose "Try Ubuntu". Get that same blinking underscore. Bear with me...

EDIT: Checking the disk for defects brings up the same thing. Maybe my computer just hates Linux...

2ND EDIT: Loading now....

---

### Post by EdenC on 2011-03-20
No Errors Reported.

Choosing Linux from GRUB.
Same flashing line appears...

What shall I do now?

---

### Post by Quackers on 2011-03-20
Hmm, does your bios have an option for "large drives"? If so, please select it.

---

### Post by EdenC on 2011-03-20
I went into the BIOS setup and could only have the LBA/Large Mode changed from either Auto (its current state) or Disabled.

However it only tells me that LBA Mode is "supported" and not whether it is on or not.

A description of the auto state follows:

> 
Enables LBA Mode if the device supports it and the device is not already formatted with LBA Mode disabled.


---

### Post by EdenC on 2011-03-20
Holy cow. Ubuntu just loaded!
OMG!
Thanks so much!

---

### Post by Quackers on 2011-03-20
Hmm, very interesting. I wonder if your bios had a 137GB limit. Some older ones do. This means that it won't look further than 137GB into a disc to find boot files. All your boot files are much further into the disc than that. 
It doesn't explain the failures to boot the live cd though. I am wondering if the bios has a problem.

---

### Post by coffeecat on 2011-03-20
> **Quackers said:**
> I am wondering if the bios has a problem.

Agreed. A buggy BIOS is often at the root of difficulties booting Linux but it's odd that the CD sometimes boots and sometimes doesn't.

---

### Post by EdenC on 2011-03-22
OK, it hasn't been fixed. After trying again just now I still get the same flashing underscore!

However, something has changed! Rather than just having (and this is not an accurate quote:
> 
Linux
Linux Recovery
Memteset
Memtest

I now have another set of Linux + Linux Recovery! One has 2.6.35-22-generic pae and the other 2.6.35-28-generic-pae. (If that makes any difference).

Having no knowledge in this kind of stuff, my only thought was that my BIOS Large Drive option was buggy, but if you can once again offer your faboulous help then I would be in debt to you for a very long time!

Thanks,
EdenC

---

### Post by Quackers on 2011-03-22
The extra entries are for a different kernel. You will get 2 more entries to the grub menu every time a new kernel is installed. Have you updated recently?
Regarding the hit and miss bios (if that's what's causing your boot problems) I'm unable to offer any advice, other than to check everything that you can. I know very little about bios problems.

---

### Post by EdenC on 2011-03-22
Yh, I updated as soon as I got into Linux.

I think want I want to do now is to remove Linux and having Windows taking up my whole HDD [getting another computer to run Linux on]. As long as this doesn't deystroy all my Windows stuff that is! If it doesn't would I simply use GParted from the Ubuntu Live CD and have C take up my whole drive?

---

### Post by Quackers on 2011-03-22
No, it won't destroy your Windows stuff, but you'll need to restore the mbr so that Windows can boot. Do you have a Windows repair disc?

---

### Post by EdenC on 2011-03-22
I think I still have my Windows 7 64-bit OEM disk. Would I just need to click "repair" from that menu?

---

### Post by Quackers on 2011-03-22
That may work yes.
If it doesn't, you should choose the command prompt option from the repair console and run ```
bootrec.exe /fixmbr
``` and if it reports no errors, reboot, hopefully to Windows.
This would be done after you have deleted all Linux partitions and swap partition from the Ubuntu live cd desktop. You may need to right-click on the swap partition and select "swapoff" first.
If you're not sure whether the Windows disc you have can run the recovery console you should check now! It is important to know that you can do it.
Alternatively you can boot to Windows and go to Start > Control Panel > Backup & Restore Centre, then in the left pane click on "make Windows recovery cd", pop a blank cd in the drive and click on OK. It only takes a minute.

---

### Post by EdenC on 2011-03-22
OK. I will try making a backup disk in a minute and remove my Linux partition.
What do you mean by "swaping"?
So, before I go through this, do I just do this:

- Go To Ubuntu Live CD
- Open GParted
- Remove Everything Except The C Drive
- Make The C Drive Take Up The Whole Drive
- Once This Is Done, Restart
- If Windows Doesn't Boot At First, Put In The Recovery Disk And Run It

I'm just trying to check through this as much as possible as I'm super worried that I'm going to lose everything [not that I don't trust you :D].

---

### Post by EdenC on 2011-03-22
And Can I Just Burn It On A DVD Rather Than A CD?

---

### Post by Quackers on 2011-03-22
You can use a dvd yes.

NO! don't do what you propose, do this.

From the Ubuntu live desktop open gparted.
Right-click on the swap partition, if you have one, and select "swapoff"
Then delete the swap partition, if you have one.
Delete the Linux partitions only.
Don't forget to apply the changes by clicking on the green arrow in the toolbar.

LEAVE the Windows partition(s) alone - do not extend the Windows partition in gparted!

If you reboot now Windows will not boot. This is because grub is still in the mbr of the hard drive and will look for partitions that are no longer there. Grub will fail to load anything, including Windows!

Boot from the disc that will run the Windows repair console.
Run the automatic startup repair. If it runs ok, reboot and see if Windows boots.

If it doesn't boot from the same cd/dvd and in the recovery console choose the Command Prompt option. 
In the command prompt window type in
```
bootrec.exe /fixmbr
```Note the space between exe and /fixmbr.
If that runs ok, reboot and Windows should boot.

You can then extend the Windows C: partition using Windows Disk Management Console.

---

### Post by EdenC on 2011-03-22
OK thankyou. I shall do this after dinner [when I have more time].

Do I only need to delete the Swap Partitions and the Linux Partition? If so, using my Gparted screenshot from a previous post [linked here [http://i.imgur.com/DXynJ.png](http://i.imgur.com/DXynJ.png)] which dev/sdas do I need to swap and remove?

[Thanks For All Your Help, Again, So Far :KS]

---

### Post by Quackers on 2011-03-22
You have no swap partition it seems. So all you need to delete is /dev/sda3, the ext4 partition.
I do not understand what you mean by "switch".

---

### Post by EdenC on 2011-03-22
I edited to Swap just now [TYPO].

OK, will do all this after dinner / at about 6:30pm.

Thanks Alot!

---

### Post by Quackers on 2011-03-22
Ah, so I see. As you have no swap partition you can ignore those instructions regarding swap :-)

---

### Post by EdenC on 2011-03-22
Thanks, worked like a charm!

Now I just need to find a cheap computer on eBay that can actualy run Linux :P

---

### Post by Quackers on 2011-03-22
Glad to hear it.
Happy hunting :-)

---

