---
title: "trying to decide where to put ubuntu and windows with 3 drives"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by jedispork on 2010-03-03
I've been trying to decide on a few different configurations and can't seem to make up my mind. My system consists of a 30 gig ssd, and two 1 tb hdd's.  At the moment I have 9 gigs for ubuntu and the rest for windows 7 on the ssd. I followed some guides and was able to minimise a lot of the bloat from windows.  I have 1 hdd as ntfs and the other as ex4. 

I was thinking of letting ubuntu have the entire ssd and putting windows on the ntfs storage drive (green 5400 rpm). I have enough things figured out in ubuntu so that I only need to use a few programs in windows. I'm not a major pc gamer any more since I have a ps3. However I really want starcraft 2 and can't decide if its worth it to keep windows on the ssd for faster loading of whatever game I'm playing at the time. I'm hoping starcraft 2 will be fully functional in wine as this would probably seal the decision for me to move windows off the ssd. 

thanks

---

### Post by leclerc65 on 2010-03-03
I would put Windows on the SSD, with the assumption that you're going to use it less and less, to prolong its life.

---

### Post by darkod on 2010-03-03
> **leclerc65 said:**
> I would put Windows on the SSD, with the assumption that you're going to use it less and less, to prolong its life.

But that would be a complete waste of the SSD then. Using it for OS you will hardly boot.
I think the "life issue" of SSDs is way pumped up. First of all, any new SSD will come with 2yr or 3yr warranty, some even with 5yr. I haven't gone into details what exactly is covered in that warranty, but if it fails in the first 3yr, it seems you get a replacement. So why worry? Just do regular backups.

And if it fails after 3yr, the price is going to come down so much that it won't really matter. You will probably want larger size SSD by then anyway.

---

### Post by jedispork on 2010-03-04
I moved windows over to the storage drive.  I ran into some problems getting grub to work.  I used the disk manager in windows to create a 100 gb partition on my ntfs storage drive for windows.  Then I shut the computer down and disconnected the ssd. Windows installed fine but the "system reserved" partition that usually comes with windows never showed up. I don't think its needed anyway 

So I shut down again reconnect the ssd(sda) and boot with ubuntu 9.10. I opt to let it erase and use the entire ssd. After the install it reboots into windows...ugh.  So then I try the live cd and follow instructions to reinstall grub. Again no grub prompt on boot. I start to realize that grub is being installed on the drive thats not being looked at on boot so then I try to install grub on sdb2 (windows). I screw up the windows boot loader and have to use bootrec to restore. 

I finally discovered that I can change the boot order in the bios so I move the ssd(ubuntu only now) ahead of the windows drive. Now everything works fine.  So my conclusion is that grub was not working because the primary boot drive was windows? I want to make sure I know what I did wrong so I can learn. I also want to say it would be nice if the ubuntu installer was improved to work better with these kind of situations.

thanks!

---

### Post by darkod on 2010-03-04
> **jedispork said:**
> I moved windows over to the storage drive.  I ran into some problems getting grub to work.  I used the disk manager in windows to create a 100 gb partition on my ntfs storage drive for windows.  Then I shut the computer down and disconnected the ssd. Windows installed fine but the "system reserved" partition that usually comes with windows never showed up. I don't think its needed anyway 

So I shut down again reconnect the ssd(sda) and boot with ubuntu 9.10. I opt to let it erase and use the entire ssd. After the install it reboots into windows...ugh.  So then I try the live cd and follow instructions to reinstall grub. Again no grub prompt on boot. I start to realize that grub is being installed on the drive thats not being looked at on boot so then I try to install grub on sdb2 (windows). I screw up the windows boot loader and have to use bootrec to restore. 

I finally discovered that I can change the boot order in the bios so I move the ssd(ubuntu only now) ahead of the windows drive. Now everything works fine.  So my conclusion is that grub was not working because the primary boot drive was windows? I want to make sure I know what I did wrong so I can learn. I also want to say it would be nice if the ubuntu installer was improved to work better with these kind of situations.

thanks!

The system reserved is created only when using the win7 installer to create the partition. Because you created the 100GB partition in advance, no system reserved is created, the installer simply uses the existing partition.

What you did "wrong" was that you didn't get informed that you can change boot order in BIOS, and didn't plan from which disk you want to boot and put grub2 on it.

The ubuntu installer is working just fine, it even allows you not to install the bootloader which is much more choice than windows is giving you. It also allows you to select where you want the bootloader installed by clicking on the Advanced button in the last screen of the installer. Again, this is much more choice than windows.

When you have multiple drives you need to check where the bootloader will go, and change that if necessary. But you learned that lesson now. :) You have to tell the computer what to do, don't expect it to do as you wish without you needing to do anything. They're not that advanced yet. :)

---

### Post by jedispork on 2010-03-04
I grabbed all the updates for ubuntu and when prompted for the grub update I click leave local version currently installed. After rebooting windows loader is gone from the menu. I try this from the live cd but still no windows 7 loader.  Windows still loads fine if I select to boot from that drive in the bios. 

```
sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda
```Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c489ea0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      108547   871902208    7  HPFS/NTFS
/dev/sdb2   *      108547      121601   104856576    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x931bbb36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3726    29929063+  83  Linux
/dev/sda2            3727        3892     1333395    5  Extended
/dev/sda5            3727        3892     1333363+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux


thanks!

---

### Post by darkod on 2010-03-04
You might have a mix of grub1 and grub2, although I have no idea how it would get there. If this was a clean install of karmic, it should be grub2 only.
Can you look into the /boot/grub folder whether you have grub.cfg there, and menu.lst which should not be there?

Also, running

sudo grub-install -v

will show you the version. It should be 1.97 (grub2).

---

### Post by jedispork on 2010-03-04
There is no menu.lst . When I installed ubuntu I clicked the option to erase the entire disc and install.

GNU GRUB 1.97~beta4

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
search --no-floppy --fs-uuid --set adfccafa-793c-4044-aa18-e4082fd7e613
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set adfccafa-793c-4044-aa18-e4082fd7e613
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=adfccafa-793c-4044-aa18-e4082fd7e613 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set adfccafa-793c-4044-aa18-e4082fd7e613
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=adfccafa-793c-4044-aa18-e4082fd7e613 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set adfccafa-793c-4044-aa18-e4082fd7e613
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=adfccafa-793c-4044-aa18-e4082fd7e613 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set adfccafa-793c-4044-aa18-e4082fd7e613
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=adfccafa-793c-4044-aa18-e4082fd7e613 ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

I really appreciate the help

---

### Post by darkod on 2010-03-04
How about running:

sudo update-grub

to re-scan for OSs?

---

### Post by jedispork on 2010-03-04
grub-probe: error: cannot find a device for /

---

### Post by darkod on 2010-03-04
> **jedispork said:**
> grub-probe: error: cannot find a device for /

Not from the live desktop, boot the hdd ubuntu. You can, right? You only said win7 loader is gone from boot menu, you didn't mention you can't boot ubuntu too.

---

### Post by jedispork on 2010-03-04
sorry about that. new guy here. yes I can boot to ubuntu

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

---

### Post by darkod on 2010-03-04
Not sure about this error, sorry. I don't know it that good. :(
Hopefully someone else will jump in.

---

### Post by jedispork on 2010-03-04
I found this thread and it looks like it could possibly have something to do with me not having the "system reserved" partition that came with windows.

[http://ubuntuforums.org/showthread.php?t=1374445](http://ubuntuforums.org/showthread.php?t=1374445)

Maybe I will try installing windows to a empty area so it can create this thing and I won't have any more problems.

thank you

---

### Post by oldfred on 2010-03-04
What does your /boot/grub/device.map look like. It should show all three  drives?

---

### Post by jedispork on 2010-03-04
I reinstalled windows (2nd time today). I let it have empty space so it would create the system reserved partition. After that booted back into ubuntu ran 

```
sudo update-grub
```

I have windows back on the grub menu and everything works! 

thanks to everyone for taking the time to help me. Wish I could post a cold beer or soda for you. I will be back if I break anything else.

---

