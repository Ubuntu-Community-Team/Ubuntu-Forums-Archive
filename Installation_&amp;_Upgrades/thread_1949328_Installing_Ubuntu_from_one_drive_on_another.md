---
title: "Installing Ubuntu from one drive on another"
date: 2012-03-30
forum: Installation &amp; Upgrades
---

### Post by yngens on 2012-03-30
Dear All,

I am trying to re-configure a server located in a remote datacenter for the first time in my life. No much experience, but quite comfortable at running copy-paste commands via SSH. I would appreciate very much if someone could help me with the following scenario. Should also say my appreciation will be expressed in PayPal bounty of $30 to anyone who will guide me through the right steps.

Task:

My server has 3 hard drives (two x 2 TB + one x 1 TB). I would like to use two 2 TB drives to setup Ubuntu 10.04 (LTE) on software RAID1 and use 1 TB disk just as an additional drive, probably for backups. And I know that Ubuntu server edition offers RAID1 option during setup process, so I believe I could easily setup by myself if not the following peculiarity.

The problem:

The server does not have an optical drive, so I can't ask my datacenter to go to my server and reboot it with setup disk. But I have a SSH access to 1 TB drive, which is mounted and installed with Ubuntu 10.04. 

Now I wonder is it all possible to have a setup image somewhere on 1 TB drive, reboot from it and install Ubuntu 10.04 server with RAID1 on two 2 TB disks? If it is possible, how do I do it?

---

### Post by oldfred on 2012-03-30
First option is can you boot from a USB? Most installs now use USB as an alternative to CDs. There are also network installs but I do not know about them.

I have used hard drives & flash drives to boot ISO directly with grub2.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

But some have posted that the loop mount ISO boot with grub2 does not work for server install. I found these two threads and using both & links above was able to install 12.04 beta from an iso file in my sdb4 partition to a new partition sdc17. If on same drive, I think it would have to be a different partition and maybe not another logical so extended is not mounted. 

[http://demtrex.wordpress.com/2011/04/04/work-around-the-cd-rom-detection-issue-when-installing-ubuntu-server/](http://demtrex.wordpress.com/2011/04/04/work-around-the-cd-rom-detection-issue-when-installing-ubuntu-server/)
[http://askubuntu.com/questions/56174/install-ubuntu-10-10-server-from-usb-with-grub4dos](http://askubuntu.com/questions/56174/install-ubuntu-10-10-server-from-usb-with-grub4dos)

When I had some typos in my grub2 boot stanza, I did get hard lockups or kernel panic and had to use power button to reset. This worked for 12.04, but am not sure about your 10.04. With 12.04 I never got a manual choice on mounting cdrom, but then using the second link of loop mounting it to /cdrom worked.

I first copied my desktop boot stanza (which already worked) but paths were totally wrong and until totally corrected I had severe lockups.

```
menuentry "Uubuntu 12.04 Precise ISO 64bit beta2" {

    set isofile="/iso/ubuntu-12.04-beta2-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Uubuntu 12.04 Precise ISO 64bit beta2 server" {

    set isofile="/iso/ubuntu-12.04-beta2-server-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
#    linux    /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet --
    linux (loop)/install/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt
    initrd (loop)/install/initrd.gz
}
 


```I boot sdb and my ISOs are in sdb4 in a /iso folder, drive is gpt, so I have to insmod that also. It seems once the ISO boots it then wants to find the cd for more data. But since grub used hd0,4, after booting it cannot find the iso file which now is in sdb4 and in /iso folder. 

I think these were the commands I used. As usual my notes are not quite complete.

ALT-f2

mkdir /mnt/tmp
mount -t ext4 /dev/sdb4 /mnt/tmp
mount -o loop -t iso9660 /mnt/tmp/iso/ubuntu-12.04-beta2-server-amd64.iso /cdrom
ALT-f1
I had to do a lot of ls to make sure I typed versions correctly.
Then install proceeded and I was able to boot. But I never saw a choice on where to install grub2's boot loader, it just went into sda. And I am not sure my /home is correct. I may have missed a step or something else may not have worked. First text install for ages. :)

Update:
It had notfully worked. The entire configure step was missed and configure would not work but by skipping configure,  it installed grub and booted.
Tried again. Found from mount the cd was now /target/media/cdrom at at the configure stage. After trying to remount and not working cd to /target/media/cdrom and install then continued. But then grub did not install. Not just to MBR but no grub files nor grub configuration and links used to boot in / were broken, kernel looked ok. But probably would have to chroot into it to repair. Not sure if again going back to find if it moved cdrom again might work.

May be better to look at net type install, but I know nothing about it.

---

### Post by yngens on 2012-04-10
Oldfred, just noticed someone commented on my request. Thanks for the detailed response, however not receiving any prompt response back when I created this request, I had just paid to my data-center for them to install my OS.

---

