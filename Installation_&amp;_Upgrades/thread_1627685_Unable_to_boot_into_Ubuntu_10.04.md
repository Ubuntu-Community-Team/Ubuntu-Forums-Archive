---
title: "Unable to boot into Ubuntu 10.04"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by Destructo47 on 2010-11-21
I have tried so many things to get Ubuntu to start up it's not even funny.  First off, I somehow managed to install two (2) video card drivers.  One is fglrx (which may or may not be the ati catalyst driver) and an open-source edgers driver.  After I rebooted from the fglrx install, my box would boot normally, but "No Signal" shows up when the purple splash screen should.  I have it set to auto-login, but I never hear the login sound (drums, etc) from my speakers.  The first thing I did was go into recovery mode and typed the following: ```
sudo apt-get purge fglrx
``` It removed fglrx without any problems.  I booted from the live cd (which is 9.10) and edited xorg.conf to the settings from a previous video card (nVidia mx2 200/400).  Then I put that video card in and switched from the onboard to the one I had just put in.  Upon boot, I found that the purple splash screen just hangs (all 5 dots are red) and sits there.  Seeing that it wouldn't boot, I turned it off via the power button.  I went back onto the live cd and tried to remove the splash image via ```
sudo nano /boot/grub/grub.conf
``` I removed "quiet" when it appeared before "splash" (about 3 or 4 times).  Now on boot, it shows a bunch of code THEN goes to the purple screen, where it hangs for at least five (5) minutes.  I have yet to see it boot completely.  I have tried refreshing the swap partition using instructions from here:
[http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/](http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/)

At the moment, I have been waiting for a good ten minutes and nothing has changed on the splash screen.  Just to make things clear, fail-safe graphics mode does nothing to help the situation.

This started as another problem I had with a video card.  You can see it here:
[http://art.ubuntuforums.org/showthread.php?p=10121017](http://art.ubuntuforums.org/showthread.php?p=10121017)

Please, someone help!  I'm about to explode with all of this confusion! ](*,)](*,)](*,)](*,)
God help me, I don't want to reinstall everything! [-o<

UPDATE:  Even after 40 minutes, the screen is the same.  At this point, I think it's safe to say it won't start up, period.

---

### Post by oldfred on 2010-11-21
You have more like 30 odd video drivers installed by default.

Count of video drivers
dpkg -l|grep xserver-xorg-video|wc -l
List of drivers
dpkg -l|grep xserver-xorg-video


I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. Use shift from BIOS if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0


After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by Destructo47 on 2010-11-23
Danke sehr, thank you.  I will take a shot at it tomorrow if I'm not totally eaten by homework.

---

### Post by Destructo47 on 2010-11-26
Had to add the "nomodeset" option, since it wasn't available.  Other than, that, it's working right now in a low-res environment.  I'm going to return the Ati card (no drivers from VisionTek) and get an nVidia card.  If the problem shows up again, I'll say something here.

---

### Post by oldfred on 2010-11-26
You will not get drivers from a vendor. I do not know ATI but I thought you could install the Radeon driver and that would work. Do not know if there are different versions?

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by Destructo47 on 2010-12-13
The ATI driver makes it act about as well as my 64 MB card.  Their are multiple vendors of the HD 3650, such as Sapphire, Visiontek, and ATI itself.  On that first link, I do not see the model of video card in question, and I am unable to test it at the moment (reasons stated below).  Also, I wanted it to have full capabilities, but that seems to be a long ways off for Ubuntu.

Well, after I switched back to the old MX 420, I found that I can not get acceleration from the driver.  X doesn't even seem to want to use the proprietary driver I downloaded via System > Hardware Drivers.  I tried running 'nvidia-xorg' (as suggested by nvidia xserver), but I could not find a way to restart X.  Ctrl+Alt+backspace does not work, and I can't get into console mode (keep in mind that I'm running in low-graphics mode).

I tried to reboot into recovery mode and reconfigure the xorg.conf file a few times, all ending with no success.  However, looking at the xserver error log, I noticed that the driver I had installed from nvidia was 96.39.17 and the kernel module's was 96.39.18 (not sure about the middle digits.  Obviously, that meant something but I had no way of changing it.  After six (6) or so tries, I went into recovery mode but this time, instead of letters and numbers and whatnot, everything is represented by a bunch of multicolored bars.  I can't tell what anything is, other than by the length of characters or their position in the menu.

I tried fixing broken packages, and it went through fine.  Since I couldn't tell what the last few lines were saying, I did a hard reboot.  Next, in the recovery menu again, I tried going into low graphics mode.  A few lines of the colored bars showed up, then disappeared, and nothing else happened.  I did a hard shut down, and then switched to try to get my old hard drive to boot instead of the new one: nothing.

To make matters worse, the live cd will not boot either.  I'm really lost at this point.  I plan on getting a new motherboard, processor, and graphics card once I get the money.  For now, though, I need to access all of my documents on the other hard drive (the 320 GB WD), because I have a ginourmous project due tomorrow and everything I've done is on there.  A swift response will be much appreciated.

Also, as a side note, somewhere during this process my computer decided to erase the HPLIP settings for our HP Photosmart All-in-one printer, and I will have to reinstall the configuration files for that as well.  Not sure if this is related to the above problems.

---

### Post by oldfred on 2010-12-14
What do  you want to boot. Solving the video  issue sounds like it will not be quick. 

I do not know why CD will not boot, that is totally controlled by BIOS which what ever is installed on a hard drive does not change. Without liveCD is is difficult to repair any system. Can you boot USB flash drives. Then you can install the liveCD or repair CD to flash.

Do you have windows and want to boot it. If you have a windows repair CD for the version of windows you can reinstall the windows boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From a Ubuntu liveCD you can reinstall a window like boot loader - lilo. Lilo uses the boot flag (active partition in windows) to know which partition to boot which is all the windows boot loader does.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by oldfred on 2010-12-14
fanlynne - see post #2 Often just adding nomodeset in the grub kernel line on the grub menu with e (for edit) in place of quiet splash or one of the other parameters if that does not work.

---

### Post by Destructo47 on 2010-12-14
No, my setup is just a single Ubuntu install with a swap partition on the end of the partition table.  For some reason, the BIOS will not let me change the boot sequence -- the only options I can choose from are the WD disk or a floppy drive (which isn't actually in the computer so I don't know why it shows up).  I cannot set the cd/dvd drive or the 40 GB Seagate drive to boot up (the 40 GB has old install of Ubuntu on it).  One thing I forgot to mention is that the Seagate drive is on a uATA controller ribbon with the cd/dvd drive, while the WD drive is on my secondary SATA port (SATA1).

I'm thinking that it's one of three problems:

1. The hard drives may be having problems, such as read/write errors,

2. the motherboard is failing (that could explain the loss of BIOS options), or

3. I did something really stupid and totally trashed my whole system without knowing it.

I will try booting via USB.  I don't know what I'll do if it works or not.

Would it help if I told what hardware I'm using? I got this for free from some doctors who had upgraded their system (the video card, cd/dvd drive, and the WD hard drive were all mine originally).  I looked on the 40 GB disk case and it says "This drive is manufactured by Seagate for OEM distribution."  I don't know why that would be the problem, since it's on the same setup that I installed it on.

Here is my system info. and approximate ages:

Ubuntu 10.04 Lucid Lynx
Kernel version: 2.6.32-25-generic
Intel Pentium 4 HT 2.4 GHz (Age unknown)
Mobo: Intel D865GLC/D865PE50 (Age unknown) (Has onboard vga graphics)
(Click [here]("http://www.intel.com/support/motherboards/desktop/d865glc/sb/CS-027147.htm") for tech manual & keep in mind there's only 3 PCI slots)
BIOS Version: 010.085.000.001.000000
1.5 GB DIMM RAM (Age & speeds unknown)
Seagate Barracuda 40 Gbytes Model # ST340014A (Disk usage analyzer puts this at about 4.9 years running time but still healthy)
Western Digital 320G/7200 SATA II HDWD-S320JS (a couple days worth of use)
380w RaidMax power supply (4 standard, 1 SATA) set to 115v
Lite-On CD/DVD R+RW (not sure how long this has been used either)
nVidia Geforce4 MX 420 64MB memory (not sure about age or memory speeds, etc)
Linksys WMP54G wireless card (about 3/4 year of use & does not work on live cd)

---

### Post by oldfred on 2010-12-14
Your manual does not mention USB boot and your system is pretty old. 

It also mentions not to put a hard drive on the same channel as the CD/DVD device.

i am surprised a motherboard this old has SATA ports.

---

### Post by Destructo47 on 2010-12-15
Well, like I said, I got it for free.  The sata ports are only at sata I speed.  I would think that setting the jumpers correctly on the ATA hard drive (non-ata compatible slave) would allow for a hd and cd/dvd drive on the same channel with an UltraATA cable.

So, are you saying I should upgrade?  I would agree with you, it's just that money is an issue when it comes to upgrading a computer.

Anyways, even if I do put them on separate channels, I'm not sure if that will allow a boot off of the live cd.  I will see if that fixes it.  Hoping for the best.

---

### Post by Destructo47 on 2010-12-22
Putting the cd drive & hdd on separate channels and they booted fine.  It still won't boot off of the live cd for some reason.

Right now I'm booting off of the old hdd and all of the displays are perfect.  I managed to change the used xorg.conf file to the one used waaaaay back in April.  All I have to do is copy that file in place of the xorg.conf file on the new drive and everything should go well, unless there is a driver issue.  I am still unable to get into console mode for some reason.

I would also like to mention that my uncle was kind enough to give me a new-er motherboard (or at least it performs better) with two (2) video cards.  The mobo is an Abit IS7, and the 2 cards are a Geforce FX5200 256 MB and a Radeon 9250 256 MB.  They are both AGP cards.  It currently has a P4 in it, which I think is one of the few processors that can use that socket.  If I run into any more problems with this I'll be sure to say something.

---

### Post by oldfred on 2010-12-22
You always need a working CD or USB (or even floppy to boot USB with plop), so you have a way to repair system.

Often a download may not be correct. You can check md5sum to see if download is ok.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You also need to burn at lowest speed CD will allow. For whatever reason that works better.

---

### Post by Destructo47 on 2010-12-22
No, the CD isn't the problem.  I've booted from it multiple times.  In fact, I'm using a live cd session on my laptop to type this.  When I burned it, I made sure to have it set at lowest speed.  That gives the burner more time to think about what it's doing.  I think it's something screwed up in the BIOS or something else on the motherboard has gone haywire.  Also, I do not believe that the current motherboard will allow me to boot from USB.

The manual for the new(er) motherboard does not mention anything about booting from USB, either.  I do not have a floppy drive available, and I don't have a floppy disc available (unless you count the 5 1/2 inch under my desk :p).  Like I said, it's not the CD but something else on the system.  It's not the drive either, because I can hear it reading the CD on boot, it just won't boot it.

Also, how do I uninhibit a drive on the Daemon?  I'm trying to mount the 320 GB disc but Disk Utility and terminal tell me that either "the mounting point does not exist" or "the daemon is inhibited".  I need to be able to copy the xorg.conf over to replace the xorg.conf on the other drive.  GParted says the drive is mounted, but I cannot access it and it won't let me unmount it.  Disk utility detects it, but I can't mount it because "the daemon is inhibited".

---

### Post by oldfred on 2010-12-22
Sometimes it is shown twice on the left panel. Once with the little triangle & bar on the right and once without. I like to label partitions so I know which is which. You can add labels with Disk Utility in System, Administration.

---

### Post by Destructo47 on 2010-12-23
I assure you that it only shows up once.  I tried to unmount /dev/sdb2 in GParted, but it always comes up with this message:

[SIZE=4]Could Not Unmount /dev/sdb2
[/SIZE]
[SIZE=2]The partition could not be unmounted from the following mounting points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.[/SIZE]


However is no icon on the desktop or in computer:/// or in /media that allows me to access the drive.  I cannot unmount /dev/sdb1 (which also contains sdb5) because it is not mounted, /dev/sb2 cannot be unmounted because there is a conflict with the mounting points for the partitions.

Here is the full error from Disk Utility when I try to mount /dev/sdb2:

[SIZE=4]Error mounting volume[/SIZE]

[SIZE=2]An error occured while performing an operation on "317 GB Filesystem" (Partition 2 of ATA WDC WD3200AVVS-73L2B0): The daemon is being inhibited.

\/ Details
Daemon is inhibited[/SIZE]

Also, two more problems.  The computer boots as if I'm holding down the Shift key when the BIOS logo shows up.  I get a list of boot options like the generic kernel, and recovery mode, but then I also get the same options again but "on /dev/sb1" or "on /dev/sb2" is at the end.  I'm not sure how good of a picture that paints so I'll try'n get a picture with my camera as soon as we get some AA's in this house.  The other thing isn't really a problem, but when the purple screen should show up, I get the "No Signal" display on my screen for a second or two, then after about 10-15 seconds the desktop shows up.

---

### Post by oldfred on 2010-12-23
Just so we can see how your system is organized. This gives extra info to solve boot issues but documents the system and shows all the partitions:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Destructo47 on 2010-12-24
sdc is just a usb flash drive I have plugged in
Just before I did this I specified the mount points for the 2 hard drives in fstab, so that's what UBUN2 and OLD are

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,862,899    74,862,837  83 Linux
/dev/sda2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sda5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         618,631,020   625,137,344     6,506,325   5 Extended
/dev/sdb5         618,631,083   625,137,344     6,506,262  82 Linux swap / Solaris
/dev/sdb2    *             63   618,631,019   618,630,957  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     2,015,231     2,015,200   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e502147f-3f9b-403c-959e-d3eb0f644df3   ext4       OLD                           
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3bd22569-843a-4887-978c-66f8a3da9116   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        e502147f-3f9b-403c-959e-d3eb0f644df3   ext4                                     
/dev/sdb5        9ee9a59f-835b-4c48-932b-f39214e0362a   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        922B-2057                              vfat       NICK'S PD                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/NICK'S PD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=nick)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3bd22569-843a-4887-978c-66f8a3da9116 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb    /media/26C89F1AC89EE779    auto    rw,user,noauto,exec,utf8    0    0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
  18.5GB: boot/initrd.img-2.6.31-22-generic
   8.6GB: boot/initrd.img-2.6.32-24-generic
  25.8GB: boot/initrd.img-2.6.32-25-generic
   1.6GB: boot/vmlinuz-2.6.31-22-generic
  12.2GB: boot/vmlinuz-2.6.32-24-generic
  27.6GB: boot/vmlinuz-2.6.32-25-generic
  25.8GB: initrd.img
   8.6GB: initrd.img.old
  27.6GB: vmlinuz
  12.2GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(/dev/sdb,2)'
search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
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
insmod ext2
set root='(/dev/sdb,2)'
search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.31-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, with Linux 2.6.31-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e502147f-3f9b-403c-959e-d3eb0f644df3
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3bd22569-843a-4887-978c-66f8a3da9116 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb    /media/UBUN2    auto    rw,user,noauto,exec,utf8    0    0
/dev/sda    /media/OLD    auto    rw,user,noauto,exec,utf8    0    0

=================== sdb2: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
  19.4GB: boot/grub/grub.cfg
  18.5GB: boot/initrd.img-2.6.31-22-generic
   8.6GB: boot/initrd.img-2.6.32-24-generic
  19.2GB: boot/initrd.img-2.6.32-25-generic
   1.6GB: boot/vmlinuz-2.6.31-22-generic
  12.2GB: boot/vmlinuz-2.6.32-24-generic
  27.6GB: boot/vmlinuz-2.6.32-25-generic
  19.2GB: initrd.img
   8.6GB: initrd.img.old
  27.6GB: vmlinuz
  12.2GB: vmlinuz.old
```

---

### Post by oldfred on 2010-12-24
Grub & I are very confused - what am I booting when I want to boot this UUID [COLOR=Red]e502147f-3f9b-403c-959e-d3eb0f644df3 [/COLOR]? I think you have to either change UUIDs or manually change all grub & fstab entries to not use UUIDs.

/dev/sda1        [COLOR=Red]e502147f-3f9b-403c-959e-d3eb0f644df3[/COLOR]   ext4       OLD                           
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3bd22569-843a-4887-978c-66f8a3da9116   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        [COLOR=Red]e502147f-3f9b-403c-959e-d3eb0f644df3 [/COLOR]  ext4           

Look at these command
Sudo blkid
uuidgen
tune2fs /dev/sdaX -U numbergeneratedbyuuidgen

---

### Post by Destructo47 on 2010-12-24
Output of commands:

```
nick@Nicks-room:~$ sudo blkid
[sudo] password for nick: 
/dev/sda1: LABEL="OLD" UUID="e502147f-3f9b-403c-959e-d3eb0f644df3" TYPE="ext4" 
/dev/sda5: UUID="3bd22569-843a-4887-978c-66f8a3da9116" TYPE="swap" 
/dev/sdb2: UUID="e502147f-3f9b-403c-959e-d3eb0f644df3" TYPE="ext4" 
/dev/sdb5: UUID="9ee9a59f-835b-4c48-932b-f39214e0362a" TYPE="swap" 
nick@Nicks-room:~$ uuidgen
fa245422-df2d-4ff7-88fe-bc93b6c09d16
nick@Nicks-room:~$ tune2fs /dev/sda1 -U fa245422-df2d-4ff7-88fe-bc93b6c09d16
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
nick@Nicks-room:~$ tune2fs /dev/sda -U fa245422-df2d-4ff7-88fe-bc93b6c09d16
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sda
Couldn't find valid filesystem superblock.
nick@Nicks-room:~$ tune2fs /dev/sda2 -U fa245422-df2d-4ff7-88fe-bc93b6c09d16
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sda2
Couldn't find valid filesystem superblock.
nick@Nicks-room:~$ tune2fs /dev/sda5 -U fa245422-df2d-4ff7-88fe-bc93b6c09d16
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sda5
Couldn't find valid filesystem superblock.
```I may have changed something to get grub working from some problems I had when migrating to the new HD.

---

### Post by oldfred on 2010-12-24
I often forget the sudo when running system  commands. 

try:
sudo tune2fs

---

### Post by Destructo47 on 2010-12-25
```
nick@Nicks-room:~$ sudo tune2fs /dev/sda1 -U 48817df4-de4b-4e44-851b-57f393493295
tune2fs 1.41.11 (14-Mar-2010)
nick@Nicks-room:~$ sudo tune2fs /dev/sda2 -U 48817df4-de4b-4e44-851b-57f393493295
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Couldn't find valid filesystem superblock.
nick@Nicks-room:~$ sudo tune2fs /dev/sda5 -U 48817df4-de4b-4e44-851b-57f393493295
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.

```

Yay it's showing up now!  Thank you!

---

### Post by oldfred on 2010-12-25
Your change to sda1 worked. You cannot change sda2 (and should not use same UUID anyway) as it is the extended partition which is just a container for all the logicals.

Glad it is working. Does everything work ok now? If so change post to solved.

---

### Post by Destructo47 on 2010-12-26
I just needed that to move the old xorg.conf to the new drive from the old drive.  Now my problem is that I still cannot get into console mode on the new drive, and the nvidia kernel driver module is different from the system module.  I'll try and get a copy of the X error log so you can see what I mean.  One driver is 96.xx.18 and the other is 96.xx.17 (not sure about the x's but I know they're all the same).

---

### Post by Destructo47 on 2010-12-29
Copy of /var/log/Xorg.0.log generated today after booting on the new motherboard.

```
[    30.690] 
X.Org X Server 1.8.2
Release Date: 2010-07-01
[    30.690] X Protocol Version 11, Revision 0
[    30.690] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    30.690] Current Operating System: Linux Nicks-room 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686
[    30.690] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=e502147f-3f9b-403c-959e-d3eb0f644df3 ro splash vga=795 quiet splash
[    30.690] Build Date: 08 July 2010  01:50:14AM
[    30.690] xorg-server 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2~lucid (For technical support please see http://www.ubuntu.com/support) 
[    30.690] Current version of pixman: 0.20.0
[    30.690]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.690] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.690] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 29 09:54:22 2010
[    30.690] (==) Using config file: "/etc/X11/xorg.conf"
[    30.691] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.691] (==) ServerLayout "Layout0"
[    30.691] (**) |-->Screen "Screen0" (0)
[    30.691] (**) |   |-->Monitor "Monitor0"
[    30.691] (**) |   |-->Device "Device0"
[    30.691] (**) |-->Input Device "Keyboard0"
[    30.691] (**) |-->Input Device "Mouse0"
[    30.691] (**) Option "Xinerama" "0"
[    30.691] (==) Automatically adding devices
[    30.696] (==) Automatically enabling devices
[    30.696] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.696]     Entry deleted from font path.
[    30.696] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    30.696] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.696] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    30.696] (WW) Disabling Keyboard0
[    30.696] (WW) Disabling Mouse0
[    30.696] (II) Loader magic: 0x81f4ba0
[    30.696] (II) Module ABI versions:
[    30.696]     X.Org ANSI C Emulation: 0.4
[    30.696]     X.Org Video Driver: 7.0
[    30.696]     X.Org XInput driver : 9.0
[    30.696]     X.Org Server Extension : 3.0
[    30.785] (--) PCI:*(0:1:0:0) 10de:0172:10de:015a nVidia Corporation NV17 [GeForce4 MX 420] rev 163, Mem @ 0xf8000000/16777216, 0xf0000000/67108864, 0xf4000000/524288, BIOS @ 0x????????/131072
[    30.788] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.788] (II) LoadModule: "extmod"
[    30.806] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.806] (II) Module extmod: vendor="X.Org Foundation"
[    30.806]     compiled for 1.8.2, module version = 1.0.0
[    30.806]     Module class: X.Org Server Extension
[    30.806]     ABI class: X.Org Server Extension, version 3.0
[    30.806] (II) Loading extension MIT-SCREEN-SAVER
[    30.806] (II) Loading extension XFree86-VidModeExtension
[    30.806] (II) Loading extension XFree86-DGA
[    30.806] (II) Loading extension DPMS
[    30.806] (II) Loading extension XVideo
[    30.806] (II) Loading extension XVideo-MotionCompensation
[    30.806] (II) Loading extension X-Resource
[    30.807] (II) LoadModule: "dbe"
[    30.807] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.807] (II) Module dbe: vendor="X.Org Foundation"
[    30.807]     compiled for 1.8.2, module version = 1.0.0
[    30.807]     Module class: X.Org Server Extension
[    30.807]     ABI class: X.Org Server Extension, version 3.0
[    30.807] (II) Loading extension DOUBLE-BUFFER
[    30.807] (II) LoadModule: "glx"
[    30.807] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    30.828] (II) Module glx: vendor="NVIDIA Corporation"
[    30.878]     compiled for 4.0.2, module version = 1.0.0
[    30.878]     Module class: X.Org Server Extension
[    30.878] (II) NVIDIA GLX Module  96.43.17  Thu Apr 15 05:52:20 PDT 2010
[    30.878] (II) Loading extension GLX
[    30.878] (II) LoadModule: "record"
[    30.878] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.878] (II) Module record: vendor="X.Org Foundation"
[    30.878]     compiled for 1.8.2, module version = 1.13.0
[    30.878]     Module class: X.Org Server Extension
[    30.878]     ABI class: X.Org Server Extension, version 3.0
[    30.878] (II) Loading extension RECORD
[    30.878] (II) LoadModule: "dri"
[    30.878] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.879] (II) Module dri: vendor="X.Org Foundation"
[    30.879]     compiled for 1.8.2, module version = 1.0.0
[    30.879]     ABI class: X.Org Server Extension, version 3.0
[    30.879] (II) Loading extension XFree86-DRI
[    30.879] (II) LoadModule: "dri2"
[    30.879] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.879] (II) Module dri2: vendor="X.Org Foundation"
[    30.879]     compiled for 1.8.2, module version = 1.2.0
[    30.879]     ABI class: X.Org Server Extension, version 3.0
[    30.879] (II) Loading extension DRI2
[    30.879] (II) LoadModule: "nvidia"
[    30.879] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    30.880] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.880]     compiled for 4.0.2, module version = 1.0.0
[    30.880]     Module class: X.Org Video Driver
[    30.880] (WW) NVIDIA: This server has an unsupported input driver ABI version (have 9.0, need < 8.0).  The driver will continue to load, but may behave strangely.
[    30.880] (II) NVIDIA dlloader X Driver  96.43.17  Thu Apr 15 05:35:23 PDT 2010
[    30.880] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.880] (++) using VT number 7

[    30.882] (II) Primary Device is: PCI 01@00:00:0
[    30.882] (II) Loading sub module "fb"
[    30.882] (II) LoadModule: "fb"
[    30.882] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.883] (II) Module fb: vendor="X.Org Foundation"
[    30.883]     compiled for 1.8.2, module version = 1.0.0
[    30.883]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.883] (II) Loading sub module "ramdac"
[    30.883] (II) LoadModule: "ramdac"
[    30.883] (II) Module "ramdac" already built-in
[    30.883] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    30.883] (==) NVIDIA(0): RGB weight 888
[    30.883] (==) NVIDIA(0): Default visual is TrueColor
[    30.883] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.883] (**) NVIDIA(0): Option "TwinView" "0"
[    30.883] (**) NVIDIA(0): Option "MetaModes" "1440x900_75 +0+0; nvidia-auto-select +0+0"
[    30.883] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    30.883] (**) NVIDIA(0): Enabling RENDER acceleration
[    30.883] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    30.883] (II) NVIDIA(0):     enabled.
[    30.884] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
[    30.884] (EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
[    30.884] (EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
[    30.884] (EE) NVIDIA(0):     Please consult the NVIDIA README for details.
[    30.884] (EE) NVIDIA(0):  *** Aborting ***
[    30.884] (II) UnloadModule: "nvidia"
[    30.884] (II) UnloadModule: "fb"
[    30.884] (EE) Screen(s) found, but none have a usable configuration.
[    30.884] 
Fatal server error:
[    30.884] no screens found
[    30.884] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    30.884] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    30.884] 
```

It doesn't say anything about a version mismatch, but it's not using it.

---

### Post by Destructo47 on 2011-03-27
I hate to revive this thread, but I just wanted to let you know that my problem was ***_not_*** solved, and that I had to erase the entire disk and start over. Because my problem wasn't solved, I will not mark this thread as 'Solved.'

---

