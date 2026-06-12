---
title: "Need some help setting up 10.04 (Lynx) and GRUB"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Puffie40 on 2010-05-04
Hey everyone.

I just upgraded to Lucid Lynx, and while everything kernel-wise is running fine so far,  I have a problem that is giving me heartburn.

It appears that I have broken my Windows XP boot command, as selecting that boot option will only loop back to the GRUB selection menu.

The Partition is there, and I can access it through ubuntu's file manager, but right now I simply cannot  boot into windows.

Partition information: 540gb set for windows (NTFS), 55 set for unbuntu. 

Menu Configuration:
> ### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44e3b502-02a3-4ccb-b00e-2df2903b1de9
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=44e3b502-02a3-4ccb-b00e-2df2903b1de9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44e3b502-02a3-4ccb-b00e-2df2903b1de9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=44e3b502-02a3-4ccb-b00e-2df2903b1de9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44e3b502-02a3-4ccb-b00e-2df2903b1de9
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=44e3b502-02a3-4ccb-b00e-2df2903b1de9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44e3b502-02a3-4ccb-b00e-2df2903b1de9
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=44e3b502-02a3-4ccb-b00e-2df2903b1de9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44e3b502-02a3-4ccb-b00e-2df2903b1de9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44e3b502-02a3-4ccb-b00e-2df2903b1de9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4048620d48620250
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###During the update, an autoconfig screen came up asking me to select what I wanted to boot from in GRUB.  I selected *what I thought* referred to the harddisk partitions (and not simply selecting all of them.  ](*,))  Is there any way to bring that window back up to change that?

while I am a [SIZE=1]*cough* Windows power user *cough*[/SIZE],  I don't understand ubuntu (or Linux) very well, so please keep that in mind when replying.

Thanks!

Chris

---

### Post by lidsjunky on 2010-05-04
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

check this out, should fix it

---

### Post by FreedomSlave on 2010-05-04
Same problem here! 

During the upgrade to Lucid Lynx I was asked to choose where to install the GRUB, because I didn’t know what to choose I just followed the instructions and marked all of the options.
Right now the windows XP is in the GRUB list of OS’s, but when I’m trying to boot it – nothing happens (black screen).

Please help.

---

### Post by bep7987 on 2010-05-04
I had problems with grub2 and windows too.  The Windows startup repair in Windows 7 didn't work, so I had to use a rescue disc to boot to the prompt and the run bootrec.exe with one of the following switches:

to fix master boot record: bootrec /fixmbr

to fix boot sector: bootrec /fixboot

to rebuild entire bcd: bootrec /rebuildbcd.

I was able to boot into windows but not into ubuntu.

So I followed these excellent instructions to install grub2 from the ubuntu live cd:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")


The more I think about it though I think XP doesn't have the startup repair, but you should be able to run the XP recovery console from disc using these instructions:
[http://support.microsoft.com/kb/307654/#3](http://support.microsoft.com/kb/307654/#3)  (scroll up on that page to view the recovery console installation instructions).

Here's a link to the Recovery Console overview, which includes links to pages instructing how to use the Recovery Console and to a list of the Recovery Console commands:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

I hope this helps.

---

### Post by Puffie40 on 2010-05-04
Following the instructions in lidsjunky's link repaired the windows boot entry (I was able to do it right in Ubuntu's terminal with the instructions in firefox opened, which is a plus)

I'm relieved it was just a simple boot sector problem. it looks like the entry was miswritten / corrupted when ubuntu was updated.

---

### Post by FreedomSlave on 2010-05-04
lidsjunky you are my hero! Worked like a charm! Thanks mate.

---

