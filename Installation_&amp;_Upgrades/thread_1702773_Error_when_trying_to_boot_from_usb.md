---
title: "Error when trying to boot from usb"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by DiMoNd on 2011-03-08
Hi!

A year ago did I a fresh install of ubuntu on my 4gig usb stick. I was able to boot with grub and everything was fine.

Today I tried to boot from my usb and I got an error:

```
GRUB loading.
error: reloc offset is out of the segment
grub rescue>
```

I have read some threads but I am not sure on how to fix this problem and I don't want to risk losing all the work I have done until now.

I could use some help!

Thank you in advance!

---

### Post by oldfred on 2011-03-08
Welcome to the forums.

With the USB flash drive plugged in run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by DiMoNd on 2011-03-08
Hi!

Thank you for your quick response!

Here is the results after running the script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc52cf23d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,980,889    20,980,827  27 Hidden HPFS/NTFS
/dev/sda2    *     20,981,760   312,578,047   291,596,288   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00070a44

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,357,769     7,357,707  83 Linux
/dev/sdb2           7,357,770     7,823,654       465,885   5 Extended
/dev/sdb5           7,357,833     7,823,654       465,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D868DD9868DD75AA                       ntfs       PQSERVICE                     
/dev/sda2        C034F2D034F2C904                       ntfs       OS                            
/dev/sdb1        1d4c698a-9c9e-42aa-9e0f-c952a5b8807f   ext4                                     
/dev/sdb5        359aede7-c9c2-4959-a06e-98ec6c37cf05   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

```

---

### Post by oldfred on 2011-03-08
Either from liveCD or another USB flash drive try this. It says it is an ext4 partition.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

An install into a 4GB partition is tight. You can do it but have to regularly houseclean and maybe remove larger apps like Firefox and OpenOffice and use other apps that are not so large.

---

### Post by DiMoNd on 2011-03-09
It seems that after running the commands the usb is not being detected at all.

I think the best is to format it and install ubuntu again, but now I cannot do it. 

I connected with my other pc with windows 7, it was found but when I check with right-click -- properties I get 0bytes free space 0 bytes used.

When I run ubuntu livecd I can see that it is mounted but I cannot open it or format it..

Something we can do so that I can format it? Or is it damaged?

thank you!

---

### Post by oldfred on 2011-03-09
Windows will not see an ext4 formated partition, so I would expect windows to report nothing. 

What does the liveCD show? Can you see it with gparted.

If teh e2fsck commands did not work.

List backup superblocks:
sudo dumpe2fs /dev/sdb1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sdb1
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by DiMoNd on 2011-03-09
No I cannot see it in gparted. Should I try the comannds you wrote above?

---

### Post by oldfred on 2011-03-09
At this point, it will not hurt to run those commands. 

If those do not work then you can try these, but then if that does not work nothing will.
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)

---

