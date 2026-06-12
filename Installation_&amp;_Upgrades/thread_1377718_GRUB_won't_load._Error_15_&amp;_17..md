---
title: "GRUB won't load. Error 15 &amp; 17."
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by iTheBadGuy on 2010-01-10
So after having performance issues with Karmic in ext4 I decided to install Hardy with ext3. Was blazing fast, epic, I loved it. But I wanted firefox 3.5 & all the other cool stuff Karmic has.. so I decide to install Karmic, but this time with ext3 instead of 4.

First installation: After the installation went fine, no errors while installing or anything. I remove the CD and reboot. "GRUB Loading, please wait.. Error 15" I did my googling, with the live CD to try and figure out a way of fixing this error. No luck. I did find out that the error is caused by the GRUB trying to load form the wrong drive. So I try to boot directly from the Karmic drive, Error 15. Try to boot directly from the Windows drive, Error 17. What the hell?!.

This is the first time this has ever happened to me. First time installing Hardy, everything went great. Installing Jaunty, everything went great. Installing Karmic (for the first time) everything went great. Uninstalled Karmic and installed Hardy, everything went great. Uninstalled Hardy to install Karmic = FAIL!. I did a clean install every single time. The OS is being installed (clean) in the same drive.

A 40GB drive for Windows. A 200GB drive for Ubuntu +/home +swap, and a 120GB(FAT32) for storage.

I installed Karmic 3 times, yes.. 3 times. The last time I installed I removed both the 40GB & the 120GB drives. Leaving only the one I was going to use for Ubuntu, the 200GB drive. After the installation I rebooted and Karmic loaded without problems. I'm in Karmic right now and it isn't all sluggish like it was with ext4, guess my old drives aren't good with ext4 *sight*.

But I can't use my Windows drive. When trying to boot directly from it, it gives me "GRUB Error 17" - I have to disconnect the Ubuntu drive to boot into Windows. Quick question: What the **** is going on?!

Someone help, please.. I'm tired of this ****.. and if I have to install Karmic one more time, I won't. I'll just give up and disconnect my Ubuntu drive, put it away and let it accumulate dust somewhere, seriously.. Someone help me correct this without having to install the OS again.

P.S The GRUB error is while the GRUB is loading. It doesn't give me the option to select a OS.

---

### Post by ratcheer on 2010-01-10
I got an error 15 when I first installed and configured grub2. At least in my case, it was because I neglected to select the boot drive during configuration, even though the installation instructions specifically said to make sure to do it. The problem was, it looked like the correct drive was pre-selected, so I just "OK'ed" right past it. You must manually select it for it to take effect. I hope this helps.

Tim

---

### Post by iTheBadGuy on 2010-01-10
So you're saying I need to select a "/boot" when manually installing Karmic?. This is what I've always done:

Partitions created:
- /.
- /home.
- Swap.

I also need to create a /boot?. Never had to do this in my past installation.. and while installing it didn't tell me to select a /boot.

Ok, so if this will fix the problem, how would I go about doing this?.

Create a new partition from the 200GB drive which Ubuntu is installed in and mount it as /boot?. Because I need to mount the OS in " / ", right?.

Do I have to configure anything in my BiOS? like boot priority?. At the moment, Karmic's drive (200GB) is set as first drive boot. Should I change it?.

---

### Post by kansasnoob on 2010-01-10
It would greatly simplify matters for us if you'd post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kansasnoob on 2010-01-10
> **iTheBadGuy said:**
> So you're saying I need to select a "/boot" when manually installing Karmic?. This is what I've always done:

Partitions created:
- /.
- /home.
- Swap.

I also need to create a /boot?. Never had to do this in my past installation.. and while installing it didn't tell me to select a /boot.

Ok, so if this will fix the problem, how would I go about doing this?.

Create a new partition from the 200GB drive which Ubuntu is installed in and mount it as /boot?. Because I need to mount the OS in " / ", right?.

Do I have to configure anything in my BiOS? like boot priority?. At the moment, Karmic's drive (200GB) is set as first drive boot. Should I change it?.

You very, very seldom need a separate /boot partition. In fact it can create problems!

---

### Post by iTheBadGuy on 2010-01-10
Ok, so after the Update in Update manager, the GRUB loaded, but when selecting the Windows XP it said "Invalid signature, press any key to continue.." I did and it took me back to grub, I selected Karmic and it booted without problems. So I just can't boot into Windows.

[quote="Kansasnoob"]It would greatly simplify matters for us if you'd post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)[/quote]

Here it is (pretty long tho) :```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=3bb54496-df99-4bf8-bef9-d6102b326cc6)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bf0e40f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000067d2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,344,579   156,344,517  83 Linux
/dev/sdc2         156,344,580   390,716,864   234,372,285   5 Extended
/dev/sdc5         156,344,643   373,141,754   216,797,112  83 Linux
/dev/sdc6         373,141,818   390,716,864    17,575,047  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="BRO0KLYNZ" UUID="FF5B-2A4F" TYPE="vfat" 
sdb1: UUID="A2CC3423CC33F061" LABEL="Windows" TYPE="ntfs" 
sdc1: UUID="43a78f62-da7a-4182-a47e-ef6ab975e50f" TYPE="ext3" 
sdc5: UUID="36b93fd2-3c1b-4655-a9fa-355f9e213ebf" TYPE="ext3" 
sdc6: UUID="88e91315-c113-4ce6-89a5-40cd2becb37f" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
/dev/sdc5 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bro0klynz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bro0klynz)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdc1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdc1 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single 
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
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=43a78f62-da7a-4182-a47e-ef6ab975e50f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=36b93fd2-3c1b-4655-a9fa-355f9e213ebf /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=88e91315-c113-4ce6-89a5-40cd2becb37f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by kansasnoob on 2010-01-10
OK, I'm unsure here. That is I'd really like a second opinion. Grub2 is very new to all of us so we're all learning :)

One thing I'm sure won't hurt anything and might just help is simply running the command:

```
sudo update-grub
```

Be sure to wait until it says "done".

Then compare something, in the /boot/grub/grub.cfg you just posted the Windows entry looks like this:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

I'd just like to see if "update-grub" changes that at all. You can look at that file by running:

```
cat /boot/grub/grub.cfg
```

Then scroll down to the appropriate section and post the results here. I'm not going to get into detail about what I think I see, just suffice it to say I'd like to see if it changes.

Another observation. Windows is on sdb1 but sdb still has a legacy grub mbr:

>  => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

So I'm surprised you can boot Windows even with the Ubuntu drive removed.

---

### Post by iTheBadGuy on 2010-01-10
[quote="Kansasnoob"]So I'm surprised you can boot Windows even with the Ubuntu drive removed.[/quote]
To tell you the truth, I just thought I could if I removed the drive, I didn't really try it.

After ```
sudo update-grub
```
This is what it did, I thought you might want to see it because it doesn't look to me like it did any updating..```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Windows XP Media Center Edition on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
```
But I check what you asked for after, this is what it looks like now```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```
Don't think it changed..

So I'm guessing the problem is that it's a different Grub in the windows partition than in the Karmic partition?. This was caused by installing Hardy, uninstalling and installing Karmic?. So what's the fix? if any.. god will I lose the stuff in the Windows drive?..dammit..

---

### Post by phillw on 2010-01-10
Hi,

firstly, your win stuff should still be safe and sound - it's just the boot loader that seems to have gotten confused (and me !!)

Do a nice clean re-install of Grub2 --> [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

That way, it should go and find all your valid operating systems for you.

Regards,

Phill.

---

### Post by oldfred on 2010-01-10
You should not have to lose anything. Drive order in BIOS is important as the drive that is first is the drive that is used for booting. You can only boot now from sdc as it has the correct MBR with grub2 to boot from sdc1.

I would make the windows drive first in BIOS and run the windows repairs to reinstall into the MBR and make sure it boots ok. Then make sdc the first drive and the windows drive the second.
To reinstall XP:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I would check device.map in /boot/grub to see that all drives are listed. Generally it is the order plugged into the ports and does not change with boot order.

rerun the update-grub as we need it to see that windows is the second drive not the first: Where it says hd0 it needs to say hd1 to match the sdb1. If update-grub does not work copy the entry into 40_custom and  correct it:

gksudo gedit /etc/grub.d/40_custom

menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    drivemap -s (hd[COLOR=Red]0[/COLOR]) ${root}
    chainloader +1
}

---

### Post by kansasnoob on 2010-01-10
Well actually that is helpful. What I am going to suggest may work or may not work. It won't actually damage anything. The worst that could happen is you'd have to boot an Ubuntu Live CD to restore the grub2 bootloader.

**First of all this only applies if you are for sure able to boot into Ubuntu with the Windows drive plugged in. You are sure of that, correct?**

If so run the following commands (we're going to give the Windows drive a Windows mbr and see if grub2 will like it better that way):

```
sudo apt-get install lilo
```

You'll see something about creating lilo config files, don't worry about that, just hit enter. We're only using it as a "tool", and then we'll remove it.

```
sudo lilo -M /dev/sdb mbr
```

```
sudo apt-get remove lilo
```

We're removing it so it doesn't mess with the grub2 configuration later on.

Now try to update the grub2 configuration again:

```
sudo update-grub
```

Again be sure to wait for it to say "done". I'll need to see that output and also any changes to that Windows entry in the grub.cfg file.

We may need to do something different with the data drives mbr also, but lets see how this goes.

---

### Post by iTheBadGuy on 2010-01-10
> **oldfred said:**
> 

I would make the windows drive first in BIOS and run the windows repairs to reinstall into the MBR and make sure it boots ok. Then make sdc the first drive and the windows drive the second.
To reinstall XP:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Thanks, I did this and restored the XP bootloader. Windows XP now boots.

[quote="Oldfred"]I would check device.map in /boot/grub to see that all drives are listed. Generally it is the order plugged into the ports and does not change with boot order.[/quote]
All that is in there is:```
(hd0)    /dev/sda
```Just that...

[quote="Oldfred"]rerun the update-grub as we need it to see that windows is the second drive not the first[/quote]
This came back:```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Windows XP Media Center Edition on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
```[quote="Oldfred"]Where it says hd0 it needs to say hd1 to match the sdb1. If update-grub does not work copy the entry into 40_custom and  correct it:

gksudo gedit /etc/grub.d/40_custom

menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    drivemap -s (hd[COLOR=Red]0[/COLOR]) ${root}
    chainloader +1
}[/quote]
Ok, I added it and saved it. But I'm guessing something is wrong because in the device.map there was only one line (one drive?) ```
(hd0)    /dev/sda
```. I'll reboot and see if it loads Windows from the GRUB.

EDIT:
When trying to boot from GRUB to the Windows XP it says [quote="GRUB"]Error: Invalid Signature. Hit any key to continue...[/quote]
I'm guessing I have to add the drives to the device.map? I'm not sure how I would do that though..

P.S I can boot into Ubuntu without problems in the GRUB of course, at least now I can boot into Windows, but I have to set it as the first boot drive, or go into the "boot menu" and select the Windows drive.

---

### Post by iTheBadGuy on 2010-01-10
> **kansasnoob said:**
> Well actually that is helpful. What I am going to suggest may work or may not work. It won't actually damage anything. The worst that could happen is you'd have to boot an Ubuntu Live CD to restore the grub2 bootloader.

**First of all this only applies if you are for sure able to boot into Ubuntu with the Windows drive plugged in. You are sure of that, correct?**

If so run the following commands (we're going to give the Windows drive a Windows mbr and see if grub2 will like it better that way):

```
sudo apt-get install lilo
```You'll see something about creating lilo config files, don't worry about that, just hit enter. We're only using it as a "tool", and then we'll remove it.

```
sudo lilo -M /dev/sdb mbr
``````
sudo apt-get remove lilo
```We're removing it so it doesn't mess with the grub2 configuration later on.

Now try to update the grub2 configuration again:

```
sudo update-grub
```Again be sure to wait for it to say "done". I'll need to see that output and also any changes to that Windows entry in the grub.cfg file.

We may need to do something different with the data drives mbr also, but lets see how this goes.
Tried this, didn't work. update-grub came back like it always does =/
[quote="phillw"]Hi,

firstly, your win stuff should still be safe and sound - it's just the boot loader that seems to have gotten confused (and me !!)

Do a nice clean re-install of Grub2 --> [https://help.ubuntu.com/community/Gr...ing%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

That way, it should go and find all your valid operating systems for you.

Regards,

Phill.[/quote]
I'll try this now.

---

### Post by iTheBadGuy on 2010-01-10
Reinstalling GRUB = fail. I failed at reinstalling it, I don't know why.. but I'm getting a pretty good picture of why though.

My 120GB HDD is the one set as "Master" the other 2 drives (200GB & 40GB) are set as "Slaves" Ubuntu is installed in the 200GB, while Windows is installed in the 40GB. Why use the 200GB for Ubuntu and not the 120GB, leaving more space for storage in the 200GB you might ask?. Because last time I installed Ubuntu Karmic Koala, it told me this HDD had "Many bad sectors (sign of old age) replace asap!" So now I formatted that drive to FAT32 and I'm using it for storage for both Windows and Ubuntu.

This is what I'll do:

- First, I'll backup all my data from the 120GB drive (only about 20GB used in there) to the 40GB drive that Windows is in. 

- Then I'll format the 120GB & 200GB, installing Ubuntu in the "Master" drive which is the 120GB. 

- After the installation is complete I'll pass the 20GB of data from the 40GB Windows drive, to the then 200GB FAT32 drive.

And what about the "Many bad sectors"? I'll tell Ubuntu to STFU and not warn me about this drive again, it has been working fine with Jaunty, Hardy & Windows before, why start acting up now?!.

Problem solved?. This will be my last attempt..

P.S Windows has it's original Bootloader, so installing Ubuntu in the "Master drive" should make GRUB find the Windows installation and add it to the grub2 easily, right?.

Pray for me guys.. [-o<

---

### Post by iTheBadGuy on 2010-01-10
Success! Grub2 is now working flawlessly!. Thanks for all the help guys, even though in the end I had to reinstall ubuntu to get it to work, I still learned a lot from your posts. Thanks again.

---

