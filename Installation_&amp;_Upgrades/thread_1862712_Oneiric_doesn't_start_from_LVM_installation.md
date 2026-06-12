---
title: "Oneiric doesn't start from LVM installation"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by problemator on 2011-10-17
I installed Oneiric from the desktop-amd64 (usb-live, runs perfectly!) to a brand new puter with an empty 2TB disk partitioned as follows:
sda1 -    100MB bootable primary as /boot
sda2 -    1.99TB extended as one VG, divided into 6 LVs for /, /home, /tmp, /usr, /var, /swap
No RAID, no encryption.

I can mount all volumes in usb-live (at /media/(UUID)/), and both physical and logical views in LVM look fine, but the new system won't start. After selecting any menuitem in Grub it runs a lot of text on the screen (too rapidly to read), and then stops to an error:
ALERT! /dev/mapper/vg1-lv--root does not exist. Dropping to a shell!

I have no idea what could I do in initramfs shell to heal the ill. However, I can access all the installed files from the usb-live (r+w as root), and--as far I can see--the problem lies in the following:

The menuentry in grub.cfg refers (correctly) to 'root=/dev/mapper/vg1-lv--root', but directory /dev/mapper/ is _empty_, except for a 0 bytes file 'control' (which I cannot open even as root user).
(This would affect of course all corresponding links in fstab and mtab, once the process could go further.)
The UUID references are valid.

Q1*** What files/symlinks should be in /dev/mapper/ for a succesful boot to take place with LVM?
Q2*** Is it possible to refer to the LVs in an other way, eg. with their UUIDs, and bypass the /dev/mapper/ altogether? (As Grub does--twice.)

Q3*** At what stage does LVM actually enter the game, 'insmod lvm' looks rather meager to my eyes? And where does/should it hide? I can't find but lvm.mod in /boot. I found some LVM related stuff and (empty) directories in other locations but they seem rather insignificant, and they are in wrong LVs to help booting anyway. (In usb-live all LVM stuff seems to be outside /boot, so I can't get any hints from there.)

Q4*** Is it possible LVM is not installed properly for my new system, although it was (quite apparently) present in my usb-live before I started installing to a disk. (The process didn't ask about LVM, but used the existing LVs without any error messages!)
If so, how do I install LVM to the new system, when I can't even launch it?

Yet another possible problem may be in the LV naming. I named the LVs as lv-root, lv-home, etc. but LVM seems to have written them in form vg1-lv--root, vg1-lv--home, etc. (vg1 is the only volume group in use.)
The first reference to LVs in grub.cfg is however '(vg1-lv-usr)' while the "consistent" name should be 'vg1-lv--usr'.
Q5*** Is there some discrepancy that may cause problems?

Here are the essential excerpts:
___________________________________________
grub.cfg:

-----------
insmod lvm
insmod part_msdos
insmod ext2
set root='(vg1-lv-usr)'
search --no-floppy --fs-uuid --set=root 32c92c4a-b900-4c47-a3ae-4b2ead7fd9e1
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 0bcf088d-01d8-4b91-9637-f4dfb5cb440e
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
-----------
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0bcf088d-01d8-4b91-9637-f4dfb5cb440e
    linux    /vmlinuz-3.0.0-12-generic root=/dev/mapper/vg1-lv--root ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic

(+ recovery mode and memtest entries as usual)
------------
________________________________________________
fstab:

--------------
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/vg1-lv--root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0bcf088d-01d8-4b91-9637-f4dfb5cb440e /boot           ext4    defaults        0       2
/dev/mapper/vg1-lv--home /home           ext4    defaults        0       2
/dev/mapper/vg1-lv--tmp /tmp            ext4    defaults        0       2
/dev/mapper/vg1-lv--usr /usr            ext4    defaults        0       2
/dev/mapper/vg1-lv--var /var            ext4    defaults        0       2
/dev/mapper/vg1-lv--swap none            swap    sw              0       0
________________________________________________
mtab:

/dev/mapper/vg1-lv--root / ext4 rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,stripe=1,data=ordered 0 0
/dev/sda1 /boot ext4 rw,relatime,user_xattr,acl,barrier=1,stripe=4,data=ordered 0 0
/dev/mapper/vg1-lv--home /home ext4 rw,relatime,user_xattr,acl,barrier=1,stripe=1,data=ordered 0 0
/dev/mapper/vg1-lv--tmp /tmp ext4 rw,relatime,user_xattr,acl,barrier=1,stripe=1,data=ordered 0 0
/dev/mapper/vg1-lv--usr /usr ext4 rw,relatime,user_xattr,acl,barrier=1,stripe=1,data=ordered 0 0
/dev/mapper/vg1-lv--var /var ext4 rw,relatime,user_xattr,acl,barrier=1,stripe=1,data=ordered 0 0
/dev/sdb1 /cdrom vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1986520k,nr_inodes=496630,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
proc /proc proc rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
________________________________________________

---

### Post by Gideon Eisenstadter on 2011-10-18
problemator,

What does[INDENT][FONT=Courier New]lvs[/FONT]
[/INDENT]indicate about the status of the LVs when your boot sequence hits trouble?

[http://ubuntuforums.org/showthread.php?t=1862185](http://ubuntuforums.org/showthread.php?t=1862185) might be a similar problem.

---

### Post by problemator on 2011-10-19
I checked and rechecked...
I think LVM is not present at boot time, the 11.10 installing process didn't install it at all!. There's nothing referring to LVM in my new /boot partition, nor in any other directories within the LVs.

Simple questions:
1. What directories/files of the LVM must be in /boot so that the boot process can mount the LVs?
2. Where do I find the needed files in a working live system, which seems to have everything necessary?
3. How do I initialize LVM in grub.cfg, in what order, etc?
Please be specific, I'm not a Linux techie, as you can see!
TIA

---

### Post by Gideon Eisenstadter on 2011-10-19
Problemator,

A1: Different things are available at different points in the boot process. (I'll leave the details to an expert.)  You can get a sense of the dependencies -- and also the non-dependencies -- from my set-up:

[LIST=1]
[*]separate [FONT=Arial]/boot[/FONT] partition (my choice)
[*][FONT=Arial]/[/FONT] is on an LV (my choice)
[*]/boot/grub/lvm.mod
[*]LVM utilities under [FONT=Courier New]/sbin/...[/FONT] on root partition
[/LIST]
#2 and #4 show there's enough of LVM in the initrd to mount my root LV, before which you can't get at [FONT=Courier New]/sbin/...[/FONT]

A2:  They're among the "essential system binaries" in [FONT=Courier New]/sbin/...[/FONT]  
'[FONT=Courier New]whereis lvm[/FONT]' would be a quick-check.  Lots of programs named pv*, vg*, lv*, etc.

A3:  Your listing of grub.cfg already has [FONT=Courier New][FONT=Arial]'[/FONT]insmod lvm[/FONT]', which is all you need there.  Mounting of volumes gets done by init (Upstart) scripts.

[[Wikipedia's article on initrd]("http://en.wikipedia.org/wiki/Initrd") lays out the "big picture" that LVM has to fit into at boot time.]

---

### Post by problemator on 2011-10-20
Thanks, Gideon. OK, but not quite...

I copied all lv*, pv* and vg* files that I could find from /sbin, the lvm directory from /etc, and even the man pages from /usr/share... to my new system, but that didn't get me any further. The files in /sbin were mostly links to executables--where are the executables themselves? (Not in /bin!)
There was nothing to add to /boot, and the boot process still doesn't know about my LVs (nor LVM itself). The lvs command is unknown to the shell that I get. In the live system lvs shows all LVs correctly, so at least they are correctly configured (and I can mount them for reading and writing, if it comes to that!).

Something clearly needs to be added to /boot.
The (temporary) UUID addresses in grub.cfg are correct, /boot/grub/lvm.mod is there, what is missing???

I read the wikipedia article, and the linked pages there, but the information was too unspecific to help a bit. I'm a little wiser now, however :)) I've also found other articles about LVM that were quite detailed, but too old (3-6 years) to be of any use in OS installing phase today.

I'm new to this forum. How can I get contact to the guys who wrote the Ubuntu installing software?

---

### Post by Gideon Eisenstadter on 2011-10-20
Re. the links in /sbin:  I never noticed that before; they point to _/sbin_/lvm.  From '[FONT=Courier New]man lvm[/FONT]':[INDENT]*If lvm is invoked with argv[0] set to the name of a specific  LVM  command  (for  example  by using a hard or soft link) it acts as that command.*
[/INDENT]In principle you only need lvm, but in practice the init scripts will expect at least some of the links to it.

Wikipedia's articles might clarify a bit what's happening with /dev and /dev/mapper:  (i) [*Device mapper*]("http://en.wikipedia.org/wiki/Device_mapper"); (ii) [*udev*]("http://en.wikipedia.org/wiki/Udev").  LVM startup depends on both of them.  If LVM comes up right, you'll have "files" under /dev/mapper whose names will be a hyphenation of the VG name and the LV name.  I think the issue for you is not whether there are alternate ways to refer to LVs, but that the device-mapping isn't occurring.

Unfortunately, I'm as new to this forum as you are so I don't know where you might turn for more detailed help.  Perhaps try #ubuntu on IRC (see [https://wiki.ubuntu.com/IRC/ChannelList](https://wiki.ubuntu.com/IRC/ChannelList)) and just ask "Where's the best place to take this problem?".

---

### Post by problemator on 2011-10-20
Yep, it seems that installing LVM manually is an overwhelming task, but fortunately one of your links got me back to the right source I had forgotten. In [www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem) there are instructions for installing LVM to a Ubuntu system from outside. The thread is long and complicates simple things :), so I have to digest it thoroughly first.
I'll report about my (un)success when the time is ripe. Thanks again for your help!

---

### Post by tenflo on 2011-10-22
It seems that I have the same problem. At the reboot after the upgrade from 11.04 to 11.10, I had the message :

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/VolGroup00-ubuntu does not exist. Dropping to a shell!
```I tried with a 120 seconds rootdelay without success.

I tried to install 11.10 on the lvm volume (instead of upgrade) and I have the same message at the boot.

I can access to the volume without problem from a Fedora Core live cd. 

When I do the command lvm on the BusyBox (that appears at the boot):
```
lvm> lvs
LV              VG       Attr      LSize      Origin     Snap%    Move    Log    Copy%    Convert
LogVol00   Volgroup00    -wi---    10.16g
LogVol01   Volgroup00    -wi---    1.94g
LogVol02   Volgroup00    -wi---    109.44g
ubuntu       Volgroup00    -wi---    18.44g
lvm>
```And same thing than *problemator*, in the */dev/mapper*, I have only the file *control*.

---

### Post by carstenschnorr on 2012-01-06
For my problem this showed the solution:
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)
 
the Ubuntu installer didn't install the lvm2 packages. So I had to start from a live-usb, install lvm2 there, than mounted the lvm volumes from the harddisk, "chroot"ed to the mounted harddisk and did apt-get install lvm2 on the harddisk. After that, an appropriate initrd was available and grub started as desired.
 
:)
 
I post this, to accelerate search ;-) maybe someone can add this to the ubuntu faqs as well.

---

### Post by darkod on 2012-01-06
> **carstenschnorr said:**
> For my problem this showed the solution:
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)
 
the Ubuntu installer didn't install the lvm2 packages. So I had to start from a live-usb, install lvm2 there, than mounted the lvm volumes from the harddisk, "chroot"ed to the mounted harddisk and did apt-get install lvm2 on the harddisk. After that, an appropriate initrd was available and grub started as desired.
 
:)
 
I post this, to accelerate search ;-) maybe someone can add this to the ubuntu faqs as well.

That tutorial has an important mistake from the start: you should use the alternate install cd for raid/lvm not the desktop cd. If you also used the desktop cd, that's why lvm2 wasn't installed right away.

If you used the alternate cd and selected to configure LVM during install, it does install the package and you don't need to do anything later.

---

