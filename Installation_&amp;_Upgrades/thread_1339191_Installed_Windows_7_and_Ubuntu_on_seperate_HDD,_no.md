---
title: "Installed Windows 7 and Ubuntu on seperate HDD, no grub loader at boot"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by t36 on 2009-11-27
Hi,

I recently got a new PC and I decided to dual boot it. As the PC came with two HDD I decided to install W7 on the first and leave the other one for Ubuntu 9.10
When I installed Ubuntu it only recognized the blank HDD, other than that the install proceeded as normal. But when I reboot I do not see the Grub boot loader.

Can someone help me fix this so that I can have a normal dual boot again.

Thanks in advance,

t36

---

### Post by darkod on 2009-11-27
You didn't specify but I assume it loads win7 directly as if no ubuntu is installed at all. Probably the win7 disk is first in boot order in BIOS. Go into BIOS and change the order of the drives the ubuntu drive to be first. That should sort it out.

---

### Post by t36 on 2009-11-27
Yes, this is indeed what happens. I assume I will have to configure this grub boot loader as well after switching the order of the HDDs?

---

### Post by darkod on 2009-11-27
I've seen cases where you have to, and cases where you don't. Try first, you should have grub menu, with entries for both ubuntu and windows, see if both of them work. If not, we'll deal with it.

---

### Post by Bartender on 2009-11-27
This is odd.  Usually the Ubuntu installer will spot the Windows HDD and install GRUB Stage 1 to the Windows MBR.
Two things have changed recently - Windows 7 and GRUB2 - so a lot of us aren't sure how much of our past experience is reliable any more.

Your new PC should have a "Quick boot" option as it starts up.  You hit a key while BIOS is running, and you get a menu of bootable devices.  It's F12 on my ASUS desktop, but there are at least a few different keys that are used by different manufacturers.

Find your "quick-boot" key and see if Ubuntu will boot up when you ask the PC to boot from the second drive.  If it does, then GRUB installed itself entirely to the second drive.

This is not necessarily a bad thing! :)

---

### Post by phillw on 2009-11-27
Recovering boot loaders for Win and Ubuntu is covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That should get you up and running.

If Grub2 is royally messed up the re-installing it is covered over here -->  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Oh, and for completeness (even though you're not running Wubi) -- that's over here -->  [http://ubuntuforums.org/showthread.php?t=1335464&page=3](http://ubuntuforums.org/showthread.php?t=1335464&page=3)

Regards,

Phill.

---

### Post by t36 on 2009-11-27
Hi,

I switched the HDD boot order of my pc, and now I can boot into Ubuntu :), but I still do not get a dual boot screen.
I assume I now have to follow the tutorial posted by phillw, but I wonder if there is an easier way to do this.
Oh and thanks for the replies guys.

Greetings,

t36

---

### Post by darkod on 2009-11-27
The first thing to try is to open terminal in ubuntu and execute:
sudo update-grub

Reboot and check if it works. If not, the link Phill supplied to reinstall Grub2 will help you.

---

### Post by t36 on 2009-11-27
Thanks, that did the trick.
Switching the boot order and updating grub :)
Happy camper here and amazed by the lightning quick replies!

---

### Post by oldfred on 2009-11-27
This type of problem was rare with old grub but seems pretty common with new grub. I liked darko's recommendation as I like to have the boot loader for an operating system in the MBR of that drive and have different operating systems on different drives if you have more that one drive. That way each drive is bootable if you put it first in BIOS. 

There also is a known bug in grub that causes it to rescan all drives if you boot from one drive but have the ubuntu/grub install on a second drive.

---

### Post by darkod on 2009-11-27
Oldfred, I am actually very confused on this subject. With few people it has worked just changing the order in BIOS and maybe running update-grub if needed. But for others it seems the decision to leave windows MBR on one drive and install grub2 on the other has got them into trouble.
Grub2 uses UUID so the order in BIOS should not matter, but it also still uses the command root(hd0,1) and after you switch drives in BIOS what is hd0 and what is hd1? Do they swap?
I've seen a thread where the OP tried to do the same, leave windows MBR and installed grub2 on the other drive. He then switched the order in BIOS and grub2 was failing to boot both ubuntu and windows. My guess was it was looking at "wrong" hd0 and hd1. With windows drive as first choice of course it was booting windows directly.
According to problems seen here, I am not sure having two bootloaders is helping, especially people new to Ubuntu (I am one of those myself) who do not understand the way grub works and what it actually is. On top of that, people new to Ubuntu are mostly the ones hesitating to rewrite windows MBR. And then it looks like Ubuntu is not working.

Maybe a fix would be to set the ubuntu drive as first choice before installing ubuntu so grub2 when it's installed has the hd0 and hd1 correctly. But most people just start installing with windows drive as first choice, and only change in BIOS later. Still haven't figured it out completely but there are too many threads about this.

---

### Post by ALex_cv on 2010-01-14
Hello, I have the same problem. Here is my fdisk -l
```

Disk /dev/sda: 750.2 &#1043;&#1073;, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93cf5dd5

Device   Boot      Start         End      Blocks      ID  System
/dev/sda1   *           1       5875    47190906    7  HPFS/NTFS
/dev/sda2            5876       91201   685381095    5  Extended
/dev/sda5            5876       38511   262148638+   7  HPFS/NTFS
/dev/sda6           38512       91201   423232393+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 &#1043;&#1073;, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038ed8

Device    Boot         Start       End        Blocks  ID   System
/dev/sdb2   *           2       60801   488376000    5  Extended
/dev/sdb5               2       34639   278229703+   7  HPFS/NTFS
/dev/sdb6           34640       57484   183502431    7  HPFS/NTFS
/dev/sdb7   *       57485       60801    26643771   83  Linux


```**/dev/sda1** - Windows 7
**/dev/sdb7** - Ubuntu 9.10 amd64

grub.conf
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
set root=(hd1,7)
search --no-floppy --fs-uuid --set 89b1127e-4ec8-44f8-be9c-6327187560b2
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
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 89b1127e-4ec8-44f8-be9c-6327187560b2
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=89b1127e-4ec8-44f8-be9c-6327187560b2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 89b1127e-4ec8-44f8-be9c-6327187560b2
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=89b1127e-4ec8-44f8-be9c-6327187560b2 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 606e30136e2fe090
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```When I select windows 7 while booting, appers black screen with "GRUB _ " and that's all.
Can anybody help?
p.s. sorry for my english.

---

### Post by Leppie on 2010-01-14
> **darkod said:**
> With few people it has worked just changing the order in BIOS and maybe running update-grub if needed. But for others it seems the decision to leave windows MBR on one drive and install grub2 on the other has got them into trouble.
Grub2 uses UUID so the order in BIOS should not matter, but it also still uses the command root(hd0,1) and after you switch drives in BIOS what is hd0 and what is hd1? Do they swap?
I've seen a thread where the OP tried to do the same, leave windows MBR and installed grub2 on the other drive. He then switched the order in BIOS and grub2 was failing to boot both ubuntu and windows. My guess was it was looking at "wrong" hd0 and hd1. With windows drive as first choice of course it was booting windows directly.
AFAIK one of the major issues with two different drives and leaving the windows mbr on one of them is that windows is a very *egocentric operating system*. this has the implication that the windows bootloader expects the operating system (and therefore the bootloader itself as well) to be on the first disk (hd0). when changing the boot order in bios, the device.map has to be amended accordingly and use the devicemap option in the menu entry. in the end it's not very complicated once you know it.

---

### Post by oldfred on 2010-01-14
I agree with Darko that we seem to be seeing a lot of these issues with multi-drive configurations, especially removable drives.

On my system changing boot order did not change any drive order. The drive order seems to be the position plugged into the sata ports. My ubuntu was on sdc and I have windows on sda, I was booting from sda and it was slow, so I now boot from sdc.  With removable drives it may be a variable. 

ALex_cv it would have been better if you had started a new thread as this one should have been "solved". try switching drives in BIOS as the original poster did. If that does not work post the boot_info script results.txt.

Boot Info Script courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by gamefreak1998 on 2010-01-14
Well I know some PC's that have recovery partitions give issue because the way the BIOS Sets up the factory partitions.  However I don't know much else.

---

