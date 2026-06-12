---
title: "Grub Problems"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by gabetz08 on 2011-05-27
So here is the deal. Today I decided to dual boot 7 and ubuntu. Got it installed all fine and dandy, when i restarted so i could start the customizations to make it my own i got the following error. 
"ERROR: no such partition
grub rescue>"
Now i have been doing research and trying to fix the dam thing for 6 hours now and i am all out of ideas. I even tried fixing the windows MBR by putting the windows cd in and going startup repair, no luck. I have read that it has to do with my motherboard not search through my whole hard drive for the config files, and a bios upgrade might help. My computer is an hp and the bios upgrade i download is a exe file. i am unsure how to upgrade from linux. I have also read that i need to create a boot partition. according to gparted i already have a 100 mb partion at the begingin of my disk, can i just use that? Now i have no clue what to do next. I have also tried reinstalling ubuntu hoping that would fix it but same issue occurred. Now i am asking the forums since i am at the point that i want to throw my computer into the ocean. I am not completly new to linux but i am no where near an expert. So please give me some ideas, and if you have any guides that i can follow step by step that would be awesome. Thanks

---

### Post by tommcd on 2011-05-27
In order to find out what is going on, try downloading and running the bootinfo script and post the results here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
You can run the bootinfo script and post the results from the Ubuntu live CD.

---

### Post by shahverdy on 2011-05-27
well, 
first you must find out that you still have ubuntu partitions or not, if not then you must reinstall it again :D
but if you have them, you must reinstall your grub, to do so :

boot from a live cd, from places menu go to your hard drive ubuntu  partition (to mount it), then open terminal and run this :

sudo grub-install --root-directory=/media/your-linux-partition /dev/sda


Notice that /dev/sda is your master hard disk, and /media/your-linux-partition is the folder that your ubuntu partition is mounted to.

---

### Post by gabetz08 on 2011-05-27
tommcd
here are the results you asked for. it says that grub 2 is looking for the core.img of sector 1. is this my issue?

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   153,602,047   153,395,200   7 NTFS / exFAT / HPFS
/dev/sda3         153,602,048   460,802,047   307,200,000   7 NTFS / exFAT / HPFS
/dev/sda4         460,804,094   513,814,527    53,010,434   5 Extended
/dev/sda5         511,862,784   513,814,527     1,951,744  82 Linux swap / Solaris
/dev/sda6    *    460,804,096   511,862,783    51,058,688  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8054 MB, 8054636032 bytes
255 heads, 63 sectors/track, 979 cylinders, total 15731711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,730,687    15,728,640   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D4B0FE24B0FE0CAC                       ntfs       System Reserved
/dev/sda2        8A4829244829110D                       ntfs       
/dev/sda3        0CE04C68E04C5A5A                       ntfs       Storage
/dev/sda5        76ae7770-a7d0-4cff-ac0b-5133ab777ddb   swap       
/dev/sda6        d45ad05c-c877-4308-99e6-56169e35515c   ext4       
/dev/sdb1        CAC1-3167                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

shahverdy
the good news is that my ubuntu install is still in place. the bad news is that i have tried reinstalling grub before and it was no help once so ever. just gave me the same response i had before.

---

### Post by gabetz08 on 2011-05-27
i remember that when i tried to install grub i got an unusual response so i did it again and this is what i got
"/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track."
now i googled flexnet and it seems that it has something to do with adobe which i have installed on my windows partition. i found this [http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254) 
which could fix my problem but that is a little beyond my linux knowledge. anybody have any suggestions?

---

### Post by gabetz08 on 2011-05-27
i gave the flexnet error fix a try and i still get the same error when i boot.

---

### Post by oldfred on 2011-05-27
Flexnet should not be a problem. Grub2 created a work around for flexnet software that does not follow standards. As the area after the MBR is supposed to be for boot code, not DRM. Unless you do not want Adobe do not erase the Flexnet sector.

Did you post the full results.txt? It is missing a lot of info that would normally be posted. Even if it cannot open a partition due to read errors it posts that as an error, but you do not have anything.

You also have two boot flags which is not allowed. With Windows you can only have one boot flag on a primary partition. Use gparted from liveCD and click on sda6 and right click manage flags and remove boot flag. Grub does not use boot flag.

---

### Post by gabetz08 on 2011-05-27
The results that i printed are all i get. i am currently running off a live cd, not sure if that matters for the output. I got ride of the second boot flag and still had the same result

---

### Post by oldfred on 2011-05-27
If that is all you have, then you have just installed grub2 and not installed anything??

If you look in sda6, do you see all the normal Linux folders or just a /boot/grub?

---

### Post by gabetz08 on 2011-05-27
i see all of the normal linux folders

---

### Post by oldfred on 2011-05-27
I might try rerunning boot script and see if it gives more info.

You can try manually booting.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by tommcd on 2011-05-28
gabetz08,
Try reinstalling grub2 to the MBR of /dev/sda according to this tutorial: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
The first method listed there should work fine. Then reboot and see if you can boot into Ubuntu.

As Oldfred has pointed out, your output from the bootinfo script is missing a lot of stuff.

---

### Post by shahverdy on 2011-05-28
I , myself, to fix mbr problems, use tools in a bootable CD named HirenCD. There are a lot of useful tools in it, may be those can help you. Here, I recomend reinstall standard MBR, using a tool named 'MBR Work'. 
{ I always recomend this CD : D }

you can download this CD from here : 
[http://dl.asandownload.com/SoftWare/Utility/Useful_Tool/Hirens_BootCD_v13.2_Keyboard_Patch_www.AsanDownload.com.zip](http://dl.asandownload.com/SoftWare/Utility/Useful_Tool/Hirens_BootCD_v13.2_Keyboard_Patch_www.AsanDownload.com.zip)

and the password is : [www.asandownload.com](www.asandownload.com)


after installing standard mbr try installing grub2 ; )

---

### Post by kansasnoob on 2011-05-28
About the BIS output this has me a bit confused:

> =============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1888: ( / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

I didn't realize until now that the new BIS is a .zip requiring that one open it and then extract "boot_info_script.sh" before running the script. So I wonder if the extraction was unsuccessful :confused:

---

### Post by kansasnoob on 2011-05-28
I think it's referring to the highlighted line in the section of the script shown below:

```
get_embedded_menu () {
  local source=$1 titlename=$2;

  # Check if magic bytes that go before the embedded menu, are present.
  offset_menu=$(dd if="${source}" count=4 bs=128k 2>> ${Trash} | hexdump -v -e '/1 "%02x"' | grep -b -o 'b0021ace000000000000000000000000');

  if [ -n ${offset_menu} ] ; then
     # Magic found.
     titlebar_gen "${titlename}" " embedded menu";
     echo '--------------------------------------------------------------------------------' >> "${Log1}";

     # Calcutate the exact offset to the embedded menu.
     **[COLOR="Red"]offset_menu=$(( ( ${offset_menu%:*} / 2 ) + 16 ));[/COLOR]**
	 dd if="${source}" count=1 skip=1 bs=${offset_menu} 2>> ${Trash} | ${AWK} 'BEGIN { RS="\0" } { if (NR == 1) print $0 }' >> "${Log1}";

     echo '--------------------------------------------------------------------------------' >> "${Log1}";
  fi
}
```

I'm guessing that either the download or extraction of the script was faulty :(

---

### Post by YesWeCan on 2011-05-28
Alternatively,
If the linux /boot files are ok you should be able to boot linux from the grub_rescue prompt:

> set prefix=(hd0,6)/boot/grub
> insmod (hd0,6)/boot/grub/linux.mod
> set root=(hd0,6)
> linux /vmlinuz root=/dev/sda6 ro
> initrd /initrd.img
> boot

If this works you will boot into Ubuntu and then you should resinstall Grub: 'sudo grub-install /dev/sda'. Also do a 'sudo update-grub' to make sure Windows is in the menu.

If this does not work, there is something wrong with your Ubuntu installation. Either re-install Ubuntu from scratch or reinstall Grub using the live CD as already mentioned.

---

### Post by kansasnoob on 2011-05-28
@ gabetz08,

As oldfred said please use gparted to remove the boot flag from sda6, then please read this post:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Please ignore the rest of that thread, I just used that old thread as a placeholder for that post so I didn't have to repost everything each time it's needed ;)

---

### Post by YesWeCan on 2011-05-28
I don't think the boot flags have anything to do with these symptoms since Grub MBR ignores them.

Having two boot flags set would be illegal if a standard MBR was being used. Whether this would cause a problem or not is another matter; the MBR might just boot the first one. I am not sure.

---

### Post by gabetz08 on 2011-05-28
So today i decided that i had nothing to lose so i reinstalled ubuntu for a third time. still have the same issues. I ran the boot info script again and have the same output. not sure what i am missing. I doubt the script was downloaded or extracted wrong since i have done it multiple times with different files downloaded and still get the same output. I removed the boot flag from the ubuntu partition so i know that is not the issue. I am trying the super grub 2 idea next and will let you know how that goes

---

### Post by gabetz08 on 2011-05-28
YesWeCan
 
i just tried your suggestions of booting from rescue and i had some issues. here are my results

> set prefix=(hd0,6)/boot/grub
> insmod (hd0,6)/boot/grub/linux.mod
             error: no such partition
> set root=(hd0,6)
> linux /vmlinuz root=/dev/sda6 ro
             unknown command 'linux'
> initrd /initrd.img
             unknown command 'initrd'
> boot
              unknown command 'boot'
 
ls shows
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

Is this all a bios issue that i need to upgrade?

---

### Post by YesWeCan on 2011-05-29
Curious. How old is your bios?

There is some problem I have heard about with very old systems where the bios' address range is too limited to reach far parts of modern disks. There is a thread about this somewhere (by drs305?) but I can't find it. If this were the issue then the problem is that Grub's early stage uses the bios' disk addressing system to find the Ubuntu partition and fails.

This may or may not be the problem. It is curious that fdisk sees 6 partitions but Grub sees only 3. Perhaps updating your bios will fix this.

BTW if you want to be able to boot Windows again, you can restore the original MBR using a live CD:
[B]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/B]
This will over-write the Grub MBR code.

---

### Post by gabetz08 on 2011-05-29
To everyone who helped and put in their 2 cents Thank you. The problem was my bios not searching my whole hard drive. The solution that i did. Since i was unable to figure out how to install a bios update from ubuntu i took an old flash drive and installed grub on it. From there i added windows to the grub menu. This allowed my to boot my computer to windows where i was able to update the bios. When i rebooted the grub menu  from my mbr showed up and i am now able to boot everything successfully. Thank you again everyone

---

