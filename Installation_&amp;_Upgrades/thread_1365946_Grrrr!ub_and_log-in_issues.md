---
title: "Grrrr!ub and log-in issues"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by LasagnaD on 2009-12-27
Hey there!

Been using Karmic for a week, everything went fine even though it couldn't recognize my XP partition for games.

But after a while, a couple things:
One day, fiddling around with the Accessibility Options @ the login menu, the 'login theme'  (in the lack of a more adequate expression) changed, and I couldn't find a way to reverse it. After that, sometimes when I booted, the average 'drum sound' is played like the users and all the stuff are shown, but nothing but the background is displayed, thus forcing a reboot under recovery mode, where this error doesn't happen.
After having had to reboot quite a bunch of times... my Grub2 broke! D:

After seeing SO MANY different guides, some outdated, some unclear, and having struggled for long enough with this, I've decided to ask thee, the community, for a helping hand.

Here, the required info to help me with my issue:

**sudo fdisk -l shows:**
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01230123

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13063   104928516    7  HPFS/NTFS
/dev/sda2           13064       19457    51359805    5  Extended
/dev/sda5           13064       19190    49215096   83  Linux
/dev/sda6           19191       19457     2144646   82  Linux swap / Solaris

**And the boot script Results.txt shows:**
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda5 and 
                       looks at sector 37143935 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01230123

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,857,094   209,857,032   7 HPFS/NTFS
/dev/sda2         209,857,095   312,576,704   102,719,610   5 Extended
/dev/sda5         209,857,158   308,287,349    98,430,192  83 Linux
/dev/sda6         308,287,413   312,576,704     4,289,292  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="12202AC1202AAC23" TYPE="ntfs" 
/dev/sda5: UUID="79411197-538b-44a6-bea1-a48f1bfe4c34" TYPE="ext4" 
/dev/sda6: UUID="08e896ae-ce4d-4871-b611-01f6e3131245" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/12202AC1202AAC23 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Ubuntu" /fastdetect 

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=79411197-538b-44a6-bea1-a48f1bfe4c34 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=08e896ae-ce4d-4871-b611-01f6e3131245 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks a lot!!

:)

---

### Post by drs305 on 2009-12-27
LasagnaD, Welcome to the Ubuntu Forums.

It appears Grub 2 is installed (at least partially) in sda5. The preferred procedure is to install Grub 2 to the device's MBR (sda), so I would recommend reinstalling G2.

The procedure is detailed [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). 

The short story on how to reinstall Grub 2:
Boot to the LiveCD.
Open a terminal (Applications, Accessories, Terminal)
Run these commands:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```

Reboot and see if it boots to Ubuntu. If it successfully boots, run "sudo update-grub" and it should see your Windows install and put it into the Grub 2 menu.

There is a lot of information contained in the community doc, but the above should restore your Grub bootloader.

---

### Post by LasagnaD on 2009-12-27
drs305, thank you very much for your quick reply.

I had no probs mountin[FONT=monospace]g, but when it came to
[/FONT]sudo grub-install --root-directory=/mnt/ /dev/sda
[FONT=monospace]It replied:[/FONT]
[FONT=monospace]grub-probe: error: Cannot find a GRUB drive for /dev/sda5.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly[/FONT]

[FONT=monospace][/FONT]Any ideas on how to fix this? I don't know how to work this out... :(

Thanks again for both the kind welcome and the help. :)

---

### Post by LasagnaD on 2009-12-27
Searched a bit, managed to make the proper [FONT=monospace]device.map file. :)

But after rebooting, I got a non-graphical kinda command line menu thingy...

GNU GRUB Version 1.97 BETA 4

Then a Sh:grub> command line.


What now? :(

Sorry for the double post! :P
[/FONT]

---

### Post by adam814 on 2009-12-27
I've seen similar issues where only a background has displayed.  For me it doesn't happen often enough for me to track it down (and I have a custom enough setup it doesn't surprise me).  I'm always able to drop to a terminal and restart gdm for a quick fix though.

In any case you can safely shut down from graphical corruption with this key sequence:
While holding down ALT+PrintScreen press R,S,E,I,N,U,B in that order.

This (among other things) flushes filesystem buffers so you can avoid any of the ext4 data corruption bugs related to hard resets.

Are the files grub is looking for there?  In the grub folder do you have a device.map and a core.img that aren't 0 bytes?  If not try reinstalling the grub2 package.

---

### Post by LasagnaD on 2009-12-27
Thanks! :D

Will try that and attempt the solution posted here:
[http://ubuntuforums.org/showpost.php?p=8444565&postcount=10](http://ubuntuforums.org/showpost.php?p=8444565&postcount=10)

BRB!

---

### Post by adam814 on 2009-12-27
Ok, just read last post.  I doubt you'd get that far without a core.img as well so you're probably ok without reinstalling grub2.

If you're getting the grub command prompt I'm guessing it's missing the grub.cfg.  You can enter the boot parameters directly at the command line to boot, then run grub-mkconfig as root to create a grub.cfg for you.

Here's an example:
```
linux (hd0,1)/boot/vmlinuz-2.6.31-16-generic
initrd (hd0,1)/boot/initrd.img-2.6.31-16-generic
boot
```That assumes your ubuntu partition is mapped to (hd0,1) in the device.map you created and you're booting the 2.6.31-16-generic kernel.  Hope this helps.

---

### Post by LasagnaD on 2009-12-28
Thanks for the replies!

Thing is, I dunno what to do next.

I've been running the commands you gave me, but... it says

"error: file not found"

Whenever I want to specify my kernel!

o_O

What can I do now? What command should I run to see the 'filename' so I can input it correctly?

I'm starting to get scared, there is some data in my comp I wouldn't like to lose over this. :(

---

### Post by adam814 on 2009-12-28
You can use ls at the grub prompt "almost" like in a shell.  With no parameters it returns the devices grub can "see."  If you pass a device as a parameter i.e. "ls (hd0,1)" it gives the filesystem type (you want to make sure in your case it's ext4).  Once you find the partition that's formatted ext4 do something like "ls (hd0,1)/boot/" to find your kernel and initrd filenames.

Even if you don't get grub working right away that alone won't lose your data.  If your grub problem is because of filesystem corruption you might be out of luck (or you might be lucky and those files are fine, you never know until you try).  Otherwise you should be able to mount it read-only with a live cd and copy your files you want to save elsewhere.

---

### Post by LasagnaD on 2009-12-28
Thanks, again, but my fears are confirmed. There aren't any kernel files! D:

Having checked the directories boot and boot/grub, I only see files quite akin to the functions I see upon pressing tab.

...

What can I do? Is there any way I can restore any of this stuff?

Right now, all I care about is my home folder, which I foolishly chose to encrypt upon installation *pulls hair* and now can't just upon LiveCDing. :'(

---

### Post by adam814 on 2009-12-28
Hmm...The LiveCD should be able to mount the filesystem even if it is encrypted as long as you remember your passphrase.  All the setups I've seen were encrypted LVM but the boot script info you posted didn't look like it was from a system using LVM.  The cryptsetup package has tools for doing that, specifically "cryptsetup luksOpen" which will prompt you for a passphrase and allow you to mount the volume.

Then you should be able to copy any files left on it to another safe location (maybe an external drive).  After doing that you should be able to copy over the kernel and initrd from the LiveCD to the /boot folder and boot using those filenames at least long enough to sort this out and get a proper kernel back.

I'd recommend doing that after salvaging data because trying to boot will probably cause the drive to get fsck-ed and it might make data recovery harder.

---

### Post by LasagnaD on 2009-12-28
I've read the docs on "cryptsetup luksOpen" and it requires both the device (which I assume is /dev/sda5), but also the name... which I don't know. I've never 'labeled' my partitions. Not to mention encrypting/decrypting them. :P
 
As embarassing as this request sounds, may I get some help on this department as well, considering this info, reposted from last page?
 
[B]sudo fdisk -l shows:
[/B]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01230123

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13063 104928516 7 HPFS/NTFS
/dev/sda2 13064 19457 51359805 5 Extended
/dev/sda5 13064 19190 49215096 83 Linux
/dev/sda6 19191 19457 2144646 82 Linux swap / Solaris

**And the boot script Results.txt shows:**
============================= Boot Info Summary: ==============================

=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
in partition #1 for /boot/grub.
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: Grub 1.97
Boot sector info: Grub 1.97 is installed in the boot sector of sda5 and 
looks at sector 37143935 of the same hard drive for 
core.img, but core.img can not be found at this 
location.
Operating System: Ubuntu 9.10
Boot files/dirs: /etc/fstab

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01230123

Partition Boot Start End Size Id System

/dev/sda1 * 63 209,857,094 209,857,032 7 HPFS/NTFS
/dev/sda2 209,857,095 312,576,704 102,719,610 5 Extended
/dev/sda5 209,857,158 308,287,349 98,430,192 83 Linux
/dev/sda6 308,287,413 312,576,704 4,289,292 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="12202AC1202AAC23" TYPE="ntfs" 
/dev/sda5: UUID="79411197-538b-44a6-bea1-a48f1bfe4c34" TYPE="ext4" 
/dev/sda6: UUID="08e896ae-ce4d-4871-b611-01f6e3131245" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/12202AC1202AAC23 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,b lksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Ubunt u" /fastdetect 

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=79411197-538b-44a6-bea1-a48f1bfe4c34 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=08e896ae-ce4d-4871-b611-01f6e3131245 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

 
It would be really nice if I didn't lose my home folder to this crisis, guys.
 
Thanks again for everything.

---

### Post by adam814 on 2009-12-28
Post the output from this:
```
ls -l /dev/mapper 
```
That should give you the name you need for cryptsetup luksOpen.  It's probably just ubuntu since your root and home aren't separate.

---

### Post by LasagnaD on 2009-12-28
[FONT=monospace]Thanks a lot, again! :)

Sorry for the delay, it was 4 AM and I had to get some sleep. :p

Having run the command you recommended, the name seems to be root.

Running sudo cryptsetup luksOpen /dev/sda5 root, though...

"Command failed: /dev/sda5 is not a LUKS partition"

What the...? How did it...? My home folder is still encrypted!!!

I'm going nuts here. :p
[/FONT]

---

### Post by LasagnaD on 2009-12-28
Sorry for the double post!

Here comes the semi-solution I've implemented:

Following this guide, [http://www.linux-mag.com/id/7568/3/](http://www.linux-mag.com/id/7568/3/) , I've managed to mount the encrypted directory into a terminal. So, my data is still there *phew*...

But now, here comes another embarassing part (I reek of noobness, don't I?); I don't know how to copy the home/sebastian folder (my folder), considering all the stuff mounted/unmounted, and the fact that I have to copy it into a different partition. -_-

Anyone out there care to give me a hand?

After that's copied, I can safely format and reinstall Ubuntu.

Right now, I'm looking at a terminal, from a LiveCD, which displays 'sebastian@ubuntu', after running 'su sebastian' and inputting my passphrase. 

How can I copy the stuff from home/sebastian to the LiveCD 'partition'? Or to a usb disk? Or a DVD...?

EDIT: Well, I managed to copy the main stuff. Both my dissertation and my porn collection are safe!! :D

Thx for all the help and patience!

---

### Post by adam814 on 2009-12-28
Yeah, it looks like it's pure ecryptfs, not LUKS and dm-crypt.

To get your files out mount your ubuntu partition and the drive you want to copy to (can't be the LiveCD, i'd recommend a USB drive).  Then do this:
```
cd <home folder location>
sudo cp -R . /media/<usb drive>
```
replacing <home folder location> and <usb drive> with the proper paths.

---

