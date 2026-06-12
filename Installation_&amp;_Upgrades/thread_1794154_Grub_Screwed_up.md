---
title: "Grub Screwed up"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by ags131 on 2011-06-30
I installed Fedora on my pc over Ubuntu and now Grub wont go any farther than rescue mode. (Apparently grubs boot folder was on the Ubuntu partition... Now i see why a dedicated boot partition is handy.)

I used VMware to install Fedora as im currently out of CDs. VMware is setup to use the Physical HDD for the primary HDD in the VM. (I made sure VMware disabled access to the windows partitions so the guest couldn't access them.)
Im in Windows 7 at the moment and am avoiding rebooting as that will basically lock me out of the only computer I have access to. I tried running the Ubuntu LiveCD to restore grub but dont know how to mount Fedoras LVM partitions.

What can I do to repair grub or at least install an MBR that is capable of booting windows? I can boot floppies and cds using VMware but am not sure what to use to fix this. 

Fedora LiveCD wont mount any of the partitions to install grub,
Ubuntu LiveCD may work if i can mount the LVM partitions.

---

### Post by YesWeCan on 2011-06-30
To restore your MBR so Windows always boots,

[COLOR="Navy"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR] (assuming sda is the name of your Windows disk)

I don't know much about booting fedora. I think it installs Grub-legacy if you tell it to. It ought to be possible to boot fedora from the grub rescue> prompt, but I don't have a recipe.

---

### Post by oldfred on 2011-06-30
To understand where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
[]("http://grub.enbug.org/LVMandRAID")sudo apt-get install mawk

---

### Post by ags131 on 2011-06-30
sda1 and sda2 are dell's recovery partitions. sda3 is a NTFS Windows partition. Theyre showing as unknown because i told VMware not to allow access to them to keep the guest from screwing with windows. sda6 is supposed to be the LVM group. Its not being detected even with LVM2 installed. (This is all from a liveCd through Mware)

```
               Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and
    looks in partition 5 for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  2d Unknown
/dev/sda2             206,848    30,926,847    30,720,000  2d Unknown
/dev/sda3          30,926,848   384,350,207   353,423,360  2d Unknown
/dev/sda4         384,350,208   488,396,799   104,046,592   5 Extended
/dev/sda5         384,352,256   483,274,751    98,922,496  83 Linux
/dev/sda6         483,276,800   488,396,799     5,120,000  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        5ca59cef-8bb0-4cff-8cd5-eabc26199dc9   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/5ca59cef-8bb0-4cff-8cd5-eabc26199dc9 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda5/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,4)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_fedora00-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd0,4)
    kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_fedora00-lv_root rd_LVM_LV=vg_fedora00/lv_root rd_LVM_LV=vg_fedora/lv_swap rd_LVM_LV=vg_fedora00/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 183.416007996 = 196.941438976  boot/grub/core.img                             1
 183.287049294 = 196.802970624  grub/grub.conf                                 1
 183.287049294 = 196.802970624  grub/menu.lst                                  1
 183.281957626 = 196.797503488  grub/stage2                                    1
 183.304249763 = 196.821439488  initramfs-2.6.38.6-26.rc1.fc15.i686.img        4
 183.292607307 = 196.808938496  vmlinuz-2.6.38.6-26.rc1.fc15.i686              1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  69 74 20 6d 61 69 73 20  72 65 63 65 6e 74 65 00  |it mais recente.|
00000010  6f 20 66 69 63 68 65 69  72 6f 20 60 25 2e 32 35  |o ficheiro `%.25|
00000020  30 73 27 20 6e c3 a3 6f  20 c3 a9 20 75 6d 20 61  |0s' n..o .. um a|
00000030  72 71 75 69 76 6f 20 62  69 6e c3 a1 72 69 6f 20  |rquivo bin..rio |
00000040  64 65 62 69 61 6e 20 28  74 65 6e 74 65 20 64 70  |debian (tente dp|
00000050  6b 67 2d 73 70 6c 69 74  3f 29 00 6f 20 66 69 63  |kg-split?).o fic|
00000060  68 65 69 72 6f 20 60 25  32 35 30 73 27 20 6e c3  |heiro `%250s' n.|
00000070  a3 6f 20 c3 a9 20 75 6d  61 20 70 61 72 74 65 20  |.o .. uma parte |
00000080  64 65 20 61 72 71 75 69  76 6f 00 6f 20 66 69 63  |de arquivo.o fic|
00000090  68 65 69 72 6f 20 60 25  73 27 20 6e c3 a3 6f 20  |heiro `%s' n..o |
000000a0  c3 a9 20 75 6d 61 20 70  61 72 74 65 20 64 65 20  |.. uma parte de |
000000b0  61 72 71 75 69 76 6f 0a  00 63 61 6d 70 6f 20 60  |arquivo..campo `|
000000c0  25 73 27 20 64 65 20 64  65 74 61 6c 68 65 73 20  |%s' de detalhes |
000000d0  64 65 20 66 69 63 68 65  69 72 6f 20 6e c3 a3 6f  |de ficheiro n..o|
000000e0  20 c3 a9 20 70 65 72 6d  69 74 69 64 6f 20 6e 6f  | .. permitido no|
000000f0  20 66 69 63 68 65 69 72  6f 20 73 74 61 74 75 73  | ficheiro status|
00000100  00 6f 20 66 69 63 68 65  69 72 6f 20 6e c3 a3 6f  |.o ficheiro n..o|
00000110  20 70 6f 64 65 20 63 6f  6e 74 65 72 20 71 75 65  | pode conter que|
00000120  62 72 61 73 20 64 65 20  6c 69 6e 68 61 00 6f 20  |bras de linha.o |
00000130  6e 6f 6d 65 20 64 65 20  66 69 63 68 65 69 72 6f  |nome de ficheiro|
00000140  20 27 25 2e 35 30 73 2e  2e 2e 27 20 c3 a9 20 64  | '%.50s...' .. d|
00000150  65 6d 61 73 69 61 64 6f  20 67 72 61 6e 64 65 00  |emasiado grande.|
00000160  72 65 67 69 73 74 6f 20  64 65 20 66 69 63 68 65  |registo de fiche|
00000170  69 72 6f 20 64 65 20 27  74 72 69 67 67 65 72 27  |iro de 'trigger'|
00000180  20 6d 65 6e 63 69 6f 6e  61 20 6f 20 6e 6f 6d 65  | menciona o nome|
00000190  20 64 65 20 70 61 63 6f  74 65 20 69 6c 65 67 61  | de pacote ilega|
000001a0  6c 20 60 25 2e 32 35 30  73 27 20 28 70 61 72 61  |l `%.250s' (para|
000001b0  20 6f 20 69 6e 74 65 72  65 73 73 65 20 6e 00 fe  | o interesse n..|
000001c0  ff ff 83 fe ff ff 00 08  00 00 00 70 e5 05 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 00 78  e5 05 00 28 4e 00 00 00  |.......x...(N...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found

```

---

### Post by YesWeCan on 2011-06-30
In the live CD you'll need to install lvm
sudo apt-get install lvm2

And then you'll need to scan for LVM volumes
sudo vgscan

Then they may show up.

When you installed fedora, what choice did you make about the boot code?

---

### Post by oldfred on 2011-06-30
You have grub2 in the MBR, but do not have a grub.cfg in sda5 for it to load??

In sda5 you do have menu.lst which is from old grub and a grub.conf which is from Fedora??

Did you tell Fedora your Ubuntu was the boot partition so it installed its boot files there, then reinstalled grub2 to the MBR? The grub.conf shows hd0,4 as the boot partition which in grub legacy is sda5.

Because Fedora uses the LVM it creates a separate /boot that is not inside the LVM. But script did not show that partition either.

I think the overlapping Fedora boot & Ubuntu has caused problems with both installs. I think you could repair Ubuntu with a chroot and a grub purge & reinstall. Not sure about Fedora.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by ags131 on 2011-06-30
sda5 is the /boot partition. The menu.lst file is symlinked to grub.conf Fedora repartitioned 

> Did you tell Fedora your Ubuntu was the boot partition so it installed its boot files there, then reinstalled grub2 to the MBR? The grub.conf shows hd0,4 as the boot partition which in grub legacy is sda5.

Yes, it supposedly removed the swap (sda6) and replaced it with LVM

sudo vgscan returns "No volume groups found."

EDIT: Told VMware to use entire harddrive and now Fedora can see the LVM group. Ubuntu LiveCD wont boot with entire harddrive. It crashes the VM when it tries mounting the windows partition.

---

### Post by YesWeCan on 2011-06-30
As oldfred observes, you have got half old and half new Grub.

The thing is, you may not want to mess with your MBR code because it stops Windows booting when grub becomes unavailable. If you have a spare USB stick I'd suggest installing Ubuntu 11.04 to it and make sure it installs its boot code to the stick (the installer tends to default to sda). Then you can use this stick as your boot device and its grub2 to boot everything else.

Grub2 will not auto-detect fedora. I just tried it. But you can manually add the loading instructions to /etc/grub.d/40_custom and run sudo update-grub.

---

### Post by ags131 on 2011-06-30
Windows wouldnt boot at the moment anyway if i actually rebooted and tried. Im running the liveCD ISOs in VMWare with access to the physical HDD. When i try booting grub hrough VMWare (Which worked before i screwed it up) grub would show the menu. Now it goes to rescue mode.

---

### Post by ags131 on 2011-06-30
Solved! I finally got Fedora LiveCD to install grub and it worked this time. Now all i have to do is add the entries for windows.

---

### Post by YesWeCan on 2011-06-30
This has instructions about how to reinstall fedora's grub.
[http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-rescuemode-boot.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-rescuemode-boot.html)

---

