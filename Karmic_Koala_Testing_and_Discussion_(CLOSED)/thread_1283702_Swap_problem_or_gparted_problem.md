---
title: "Swap problem or gparted problem?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-10-05
I have noticed that (both) my karmic installs seem not to be using the swap partition; System Monitor shows 0 of 1.4GB used; /etc/mtab does not include a line for swap, although it is listed in /etc/fstab. "swapon -s" lists the correct partition, with 0 used, priority -1. After running "sudo swapoff" there is no such output from "swapon -s", but after running "sudo swapon -a" the information appears as before.

In Gparted, the swap partition has a warning triangle next to it, and is not listed as swap but as Unknown; swapoff does not appear in its right-click menu, and its Information contains the warning "Unable to detect file system....".

The system monitor could be accounted for by the fact that I'm just not using enough memory to bring swap into play, but the gparted warnings worry me.

Does anyone have any insight into what is or is not happening?

---

### Post by kansasnoob on 2009-10-05
Hmmmmmmm, mine's the same way now.

I'm guessing it's a bug. I think there were some gparted updates this morning.

---

### Post by VMC on 2009-10-05
What does "free" say about your swap usage.

edit: ok, i see you've already figured out it works, but rather it's a gparted issue. I'll check mine using PartedMagic.

---

### Post by kansasnoob on 2009-10-05
I did some fiddling. I removed Gparted version 0.4.5-2build1, then tried to install Gparted 0.4.3-0 but also had to install libparted version 1.8.0 (both packages from Jaunty package list).

[COLOR="Red"]Note: you can't just downgrade the installed Karmic libparted! Serious breakage would occur![/COLOR]

Anyway after successfully downgrading Gparted it's fine:

[ATTACH]130915[/ATTACH]

So it's a bug in either Gparted 0.4.5-2build1 or libparted 1.8-12.

Now to try and find a bug report or figure out how to file a new one. They're both Gnome packages.

My bet's on libparted after reading the changelog:

> parted (1.8.8.git.2009.06.03-1ubuntu6) karmic; urgency=low

  * baseline-symbols-update.dpatch (update): Add ped_file_system_alias_*
    functions.
  * debian/rules: Bump DEPVER to -1ubuntu5. This just adds interfaces and so
    doesn't require a soname change.

 -- Colin Watson <cjwatson@ubuntu.com>  Mon, 05 Oct 2009 12:14:16 +0100

parted (1.8.8.git.2009.06.03-1ubuntu5) karmic; urgency=low

  * rationalise-linux-swap.dpatch: Backport upstream change to rationalise
    linux-swap fs names, and add a "linux-swap" alias (LP: #399428).

 -- Colin Watson <cjwatson@ubuntu.com>  Mon, 05 Oct 2009 10:55:31 +0100

I suck at filing bug reports so any help would be appreciated!

---

### Post by VMC on 2009-10-05
It's probably just your Ubuntu installed Gparted.

I tried PartedMagic and it works ok, but that is using v0.46

---

### Post by scradock on 2009-10-05
Yes, that looks like it - only parted and libparted1.8-12 were upgraded today. I'll file a bug-report for parted/libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6 as soon as I can....

Thanks for the responses!

Edit - filed - bug #444203. Please confirm and add any useful info.....

---

### Post by kansasnoob on 2009-10-05
I'm posting a screenshot of the problem here just for reference:

[ATTACH]130918[/ATTACH]

Feel free to attach a link to it to any bug report.

---

### Post by ranch hand on 2009-10-05
If you have an "old" LiveCD (Jaunty) I would boot to it and reformat your swap partition.  If you do not have that option, do it with cfdisk through the terminal.

That way you can be sure that it is good and you can ignore the warning.  I don't know how much ram you have but I don't hardly use swap at all with the 3Gb that I have.

---

### Post by kansasnoob on 2009-10-05
> **scradock said:**
> Yes, that looks like it - only parted and libparted1.8-12 were upgraded today. I'll file a bug-report for parted/libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6 as soon as I can....

Thanks for the responses!

Edit - filed - bug #444203. Please confirm and add any useful info.....

Would you put up a link to that bug report please. Is it filed against Ubuntu or Gnome?

When I tried I just got slapped with the "no package gparted in ubuntu" line.

---

### Post by FuturePilot on 2009-10-05
> **kansasnoob said:**
> Would you put up a link to that bug report please. Is it filed against Ubuntu or Gnome?

When I tried I just got slapped with the "no package gparted in ubuntu" line.

Found it [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/444203]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/444203")

---

### Post by kansasnoob on 2009-10-05
Thank you.

---

### Post by scradock on 2009-10-05
> **kansasnoob said:**
> Would you put up a link to that bug report please. Is it filed against Ubuntu or Gnome?

When I tried I just got slapped with the "no package gparted in ubuntu" line.
The bug is filed under parted, not gparted.....

Thanks, FuturePilot...

---

### Post by scradock on 2009-10-06
Well, it's fixed now. It appears that some changes to parted left Gparted unable to figure out what sort of partition it was. Now Gparted has been brought (more) up-to-date it works fine.

Thanks to Colin Watson for the quick fix.

---

### Post by desperado666 on 2009-10-17
Still not working. Tried to create a swap partition with my installed karmic system -> not possible , device or resource busy

than i booted with jaunty - creation of swap partition was possible but still karmic doesnt recognized it.

what do to now ?

---

### Post by ranch hand on 2009-10-17
Is there an entry for the swap in your /etc/fstab?

---

### Post by desperado666 on 2009-10-17
```
# swap was on /dev/sda3 during installation
#UUID=35d5d398-febf-4eac-976b-1fe0709f594e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by kansasnoob on 2009-10-17
Please post the output of the following commands:

```
dpkg -s gparted
```

```
sudo fdisk -l
```

```
sudo blkid -c /dev/null
```

```
cat /etc/fstab
```

```
cat  /etc/initramfs-tools/conf.d/resume
```

---

### Post by desperado666 on 2009-10-18
> dpkg -s gparted
Package: gparted
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 3704
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.4.5-2ubuntu1
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libcairomm-1.0-1 (>= 1.6.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libglibmm-2.4-1c2a (>= 2.21.3), libgtk2.0-0 (>= 2.8.0), libgtkmm-2.4-1c2a (>= 1:2.17.9), libpango1.0-0 (>= 1.14.0), libpangomm-1.4-1 (>= 2.24.0), libparted1.8-12 (>= 1.8.8.git.2009.06.03-1ubuntu5), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.4.0), libuuid1 (>= 2.16-1), hal, gksu
Recommends: yelp, kpartx, dmraid, dmsetup
Suggests: xfsprogs, reiserfsprogs, reiser4progs, jfsutils, ntfsprogs, dosfstools
Description: GNOME partition editor
 GParted uses libparted to detect and manipulate devices and partition
 tables while several (optional) filesystem tools provide support for
 filesystems not included in libparted.
Homepage: [http://gparted.sourceforge.net](http://gparted.sourceforge.net)
Original-Maintainer: Anibal Monsalve Salazar <anibal@debian.org>

> Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1173     9422091   83  Linux
/dev/sda2            1302        3221    15422400   83  Linux
/dev/sda3            1174        1301     1028160   82  Linux Swap / Solaris
/dev/sda4            3222       12145    71682030    5  Erweiterte
/dev/sda5            3222        7045    30716248+   7  HPFS/NTFS
/dev/sda6            7046       12145    40965718+  83  Linux

> /dev/sda1: UUID="1c3b1b38-66c4-4c78-af18-b3a1682d4024" TYPE="ext4" 
/dev/sda2: UUID="49c48f6f-d57c-4f51-86ed-eeeecd829155" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="21883D9F4DA225C4" TYPE="ntfs" 
/dev/sda6: LABEL="virtuelle maschi" UUID="abc34e26-5746-4671-8d33-d7569704e790" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/cryptswap1: UUID="7a27fb92-517e-4cbe-8773-25f92227e199" TYPE="swap" 

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1c3b1b38-66c4-4c78-af18-b3a1682d4024 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=35d5d398-febf-4eac-976b-1fe0709f594e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

> cat /etc/initramfs-tools/conf.d/resume
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory

OK here :)

Edit : Picture added

---

### Post by kansasnoob on 2009-10-18
OK, this is going to take a while:

Gparted version is good, then:

> /dev/sda3 1174 1301 1028160 82 Linux Swap / Solaris

and:

> /dev/mapper/cryptswap1: UUID="7a27fb92-517e-4cbe-8773-25f92227e199" TYPE="swap" 

Tells me swap is on sda3 as does:

> # swap was on /dev/sda3 during installation
#UUID=35d5d398-febf-4eac-976b-1fe0709f594e none swap sw 0 0
/dev/mapper/cryptswap1 none swap sw 0 0 

Of course this tells me swap is not recognized:

> cat /etc/initramfs-tools/conf.d/resume
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory 

The puzzling part for me is:

> /dev/mapper/cryptswap1

and:

> #UUID=35d5d398-febf-4eac-976b-1fe0709f594e none swap sw 0 0
/dev/mapper/cryptswap1 none swap sw 0 0 

Of course there's a language barrier but I'm smart enough to know that your swap appears to be encrypted. Why?

Why would swap be encrypted, or are my language skills messing things up?

Look at my sample output of the same commands:

> lance@lance-desktop:~$ sudo blkid -c /dev/null
[sudo] password for lance: 
/dev/sda1: UUID="5A3CAE183CADEEE7" TYPE="ntfs" 
/dev/sda3: UUID="d3d589c9-29e6-463e-9c99-806ec3646dea" TYPE="ext4" 
/dev/sda5: UUID="6ceb25f1-5904-490b-a7cc-d14b9d63c3b7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="238b5ad8-c8fd-4c65-a190-1828af9fe54a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="51ebb887-909b-43cb-b022-1300ddd78074" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="2c9d2789-e4b6-46c3-b9c8-145951f916cc" SEC_TYPE="ext2" TYPE="ext3" 
**/dev/sda9: UUID="2897adb6-b16f-4ba7-901f-2aec9e1c994d" TYPE="swap" **
/dev/sda10: UUID="d22b2a45-6143-4f7b-b4d4-946355077517" TYPE="ext4" 


> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d3d589c9-29e6-463e-9c99-806ec3646dea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=d22b2a45-6143-4f7b-b4d4-946355077517 /home           ext4    defaults        0       2
[B]# swap was on /dev/sda9 during installation
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d none            swap    sw              0    [/B]   0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exe

> lance@lance-desktop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d

NO encryption! I've never seen that.

I'm thinking that you need to reformat the swap partition but I'm honestly not sure!

I don't understand the encryption and there is a language barrier.

---

### Post by desperado666 on 2009-10-20
I used the option to encrypt my home during installation of ubuntu karmic. I tried to reformat my swap partition with ubuntu jaunty. no problem at all. then booted to karmic and my swap partition could not be detected. 

see picture

---

### Post by kansasnoob on 2009-10-20
**[COLOR="Red"]If you've not yet begun this procedure wait just a bit! I had another thought. If you have begun go ahead and complete all steps as I still believe this is the most sane approach, but I'll put up another post directly! OK, if you've not yet begun skip to post #22 and lets start there, otherwise complete as requested here.[/COLOR]**

OK, some googling tells me that unbekannt = unknown or stranger, so that swap (sda3) is not recognized.

**[COLOR="Red"]Please read all of this before proceeding![/COLOR]**

So, I would spin up a live CD (I think you said you have a Jaunty Live CD), and delete partition sda3. Just leave that area unpartitioned for now!

Then I would click on sda4 which is the extended partition and select Resize/Move, then "grow" the extended partition about 1.25GB to the right. 

This should create an unpartitioned area of slightly more than 1GB within the extended partition, so now right click on that "new" area and select New. You must be certain to format that "new" small area as linux-swap.

There are two reasons for creating the new swap there. #1: swap is not working where it's at, and #2: all hard drives have a four primary partition limit, so this is simply a more sane approach to allow for future use of the unused 50+GB of space.

Anyway that should result in you having three operations to Apply in Gparted:
#1: Delete sda3
#2: Resize sda4 to the right about 1.25GB
#3: Create new swap within the extended partition.

After reviewing those changes click on Apply and wait for the procedure to complete. Then reboot.

Now, you will still not be done, but I'll want to see a new screenshot when that is done and I'll also need the new output of:

```
sudo blkid -c /dev/null
```

```
cat /etc/fstab
```

```
cat /etc/initramfs-tools/conf.d/resume
```

You see anytime you resize, move, or recreate swap you end up in what I like to call UUID hell. It's easy to fix though, we'll just have to change the uuid's in fstab and initramfs-tools/conf.d/resume and update initramfs. Just never change any numbers in blkid!

Once I see the new screenshot and the new output of those three commands I'll show you exactly what to do.

Please also include new output of "sudo fdisk -l" just to be on the safe side.

---

### Post by kansasnoob on 2009-10-20
Post the output of:

```
ls ~ /etc/
```

and:

```
ls ~ /etc/initramfs-tools
```

---

### Post by desperado666 on 2009-10-21
```
sudo blkid -c /dev/null
/dev/sda1: UUID="1c3b1b38-66c4-4c78-af18-b3a1682d4024" TYPE="ext4" 
/dev/sda2: UUID="49c48f6f-d57c-4f51-86ed-eeeecd829155" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="21883D9F4DA225C4" TYPE="ntfs" 
/dev/sda6: LABEL="virtuelle maschi" UUID="abc34e26-5746-4671-8d33-d7569704e790" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="swap" UUID="4e62c256-41d9-4c3c-9321-15fd3cc70f53" TYPE="swap"
```


```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1c3b1b38-66c4-4c78-af18-b3a1682d4024 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=35d5d398-febf-4eac-976b-1fe0709f594e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

**[COLOR="Red"]During boot there is a message containing one or more of the mounts listed in /etc/fstab cannot be mounted :([/COLOR]**

```
cat /etc/initramfs-tools/conf.d/resume
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory
```

```
sudo fdisk -l

Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x2c792c78

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1173     9422091   83  Linux
/dev/sda2            1302        3189    15165360   83  Linux
/dev/sda4            3222       12304    72959197+   5  Erweiterte
/dev/sda5            3222        7045    30716248+   7  HPFS/NTFS
/dev/sda6            7046       12145    40965718+  83  Linux
/dev/sda7           12146       12304     1277136   82  Linux Swap / Solaris
```

```
ls ~ /etc/
/etc/:
00-header               group                   passwd
acpi                    group-                  passwd-
adduser.conf            grub.d                  pcmcia
alternatives            gshadow                 perl
anacrontab              gshadow-                pm
apache2                 gtk-2.0                 pnm2ppa.conf
apm                     hal                     PolicyKit
apparmor                hdparm.conf             polkit-1
apparmor.d              host.conf               popularity-contest.conf
apport                  hostname                power
apt                     hosts                   ppp
at.deny                 hosts.allow             printcap
avahi                   hosts.deny              profile
bash.bashrc             hp                      profile.d
bash_completion         ifplugd                 protocols
bash_completion.d       inetd.conf              pulse
bindresvport.blacklist  init                    purple
blkid.conf              init.d                  python
blkid.tab               initramfs-tools         python2.6
bluetooth               inputrc                 qt3
bogofilter.cf           insserv                 rarfiles.lst
bonobo-activation       insserv.conf            rc0.d
brlapi.key              insserv.conf.d          rc1.d
brltty                  iproute2                rc2.d
brltty.conf             issue                   rc3.d
byobu                   issue.net               rc4.d
ca-certificates         java-6-openjdk          rc5.d
ca-certificates.conf    kbd                     rc6.d
calendar                kernel                  rc.local
chatscripts             kernel-img.conf         rcS.d
checkbox.d              kerneloops.conf         request-key.conf
compizconfig            keys                    resolv.conf
computer-janitor.d      laptop-mode             resolvconf
ConsoleKit              ldap                    rmt
console-setup           ld.so.cache             rpc
console-tools           ld.so.conf              rsyslog.conf
couchdb                 ld.so.conf.d            rsyslog.d
cron.d                  legal                   samba
cron.daily              lftp.conf               sane.d
cron.hourly             libpaper.d              screenrc
cron.monthly            locale.alias            securetty
crontab                 localtime               security
cron.weekly             logcheck                sensors.conf
crypttab                login.defs              services
cups                    logrotate.conf          sgml
cvs-cron.conf           logrotate.d             shadow
cvs-pserver.conf        lsb-base                shadow-
dbus-1                  lsb-base-logging.sh     shells
debconf.conf            lsb-release             skel
debian_version          ltrace.conf             sound
default                 magic                   speech-dispatcher
defoma                  magic.mime              ssh
deluser.conf            mailcap                 ssl
depmod.d                mailcap.order           sudoers
dhcp3                   manpath.config          sysctl.conf
dictionaries-common     mime.types              sysctl.d
doc-base                mke2fs.conf             terminfo
dpkg                    modprobe.d              timezone
emacs                   modules                 timidity
environment             mono                    ts.conf
esound                  motd                    ucf.conf
firefox-3.0             motd.tail               udev
firefox-3.5             mtab                    ufw
fonts                   mtools.conf             updatedb.conf
foomatic                mysql                   update-manager
fstab                   nanorc                  update-motd.d
fuse.conf               netscsid.conf           update-notifier
gai.conf                network                 usplash.conf
gamin                   NetworkManager          vim
gconf                   networks                w3m
gdb                     nsswitch.conf           wgetrc
gdm                     obex-data-server        wildmidi
gimp                    openoffice              wodim.conf
gnome                   operaprefs_default.ini  wpa_supplicant
gnome-app-install       operaprefs_fixed.ini    X11
gnome-system-tools      opt                     xdg
gnome-vfs-2.0           pam.conf                xml
gnome-vfs-mime-magic    pam.d                   xulrunner-1.9.1
gre.d                   pango                   zsh_command_not_found
groff                   papersize

/home/despo:
Bilder     Downloads         Musik       searchedit.conf  Vorlagen
Desktop    Dropbox           Öffentlich  Ubuntu One
Dokumente  examples.desktop  PDF         Videos
```


```
ls ~ /etc/initramfs-tools
/etc/initramfs-tools:
conf.d  hooks  initramfs.conf  modules  scripts  update-initramfs.conf

/home/despo:
Bilder     Downloads         Musik       searchedit.conf  Vorlagen
Desktop    Dropbox           Öffentlich  Ubuntu One
Dokumente  examples.desktop  PDF         Videos
```

OK here it is hope it helps :)

---

### Post by kansasnoob on 2009-10-22
OK, at least I see we got rid of "unbekannt", that rascal.

Just an FYI, from now on when you're posting "outputs" or such use the quote tags instead of the code tags (use the code tags only for commands, please). It makes it easier for blind old farts like me to read :)

**I should say I'm reasonably sure this will work, but I have very limited experience with encrypted partitions!** Of course swap is no longer encrypted!

Anyway we need to fix some UUID's. I may have already mentioned but [COLOR="Red"]DO NOT edit any of the uuid's in blkid[/COLOR], it could at the very least make the system unbootable, and I've actually had to do data recovery and reinstallation after such a mistake!

Here's your blkid -c /dev/null ([COLOR="Red"]Again do not edit anything in this file!)[/COLOR] You can see that I've highlighted the swap uuid in **bold**:

> /dev/sda1: UUID="1c3b1b38-66c4-4c78-af18-b3a1682d4024" TYPE="ext4" 
/dev/sda2: UUID="49c48f6f-d57c-4f51-86ed-eeeecd829155" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="21883D9F4DA225C4" TYPE="ntfs" 
/dev/sda6: LABEL="virtuelle maschi" UUID="abc34e26-5746-4671-8d33-d7569704e790" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="swap" UUID="**4e62c256-41d9-4c3c-9321-15fd3cc70f53**" TYPE="swap"

That uuid number is the number we want to use editing/creating the next two files. Here's your "/etc/fstab":

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1c3b1b38-66c4-4c78-af18-b3a1682d4024 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=35d5d398-febf-4eac-976b-1fe0709f594e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

We want to edit that file so it looks like this (all additions in **[COLOR="Red"]bold red[/COLOR]**):

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1c3b1b38-66c4-4c78-af18-b3a1682d4024 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=35d5d398-febf-4eac-976b-1fe0709f594e none            swap    sw              0       0
**[COLOR="Red"]#[/COLOR]**/dev/mapper/cryptswap1 none swap sw 0 0
[B][COLOR="Red"]# Entry for /dev/sda7 :
UUID=4e62c256-41d9-4c3c-9321-15fd3cc70f53 none swap sw 0 0[/COLOR][/B]


To do that you must open /etc/fstab as root to be edited so run the command:

```
gksudo gedit /etc/fstab
```

You'll then be able to copy-n-paste most of the changes, don't forget to comment out that one line with a **[COLOR="Red"]#[/COLOR]**! And be careful! If you break it, you own it!

After editing be sure you click on the "graphic" Save, then go to File > Quit. If you'd like to check to see if the editing was correct (I always do) just run the command:

```
cat /etc/fstab
```

If anything is wrong open again with gedit and FIX IT before you continue!

Now we have to fix "/etc/initramfs-tools/conf.d", so run the command:

```
gksudo nautilus /etc/initramfs-tools/conf.d
```

Since you have no "resume" file you'll have to create one so go to File > Create Document > Empty File. Name the file **resume**. Just resume. no punctuation or capital letters!

Now, to be certain that's right just click on close and run the command:

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

If that file was created properly you'll see a blank text document and in the upper left hand corner (just below the "new" and "open" icons) you'll see resume.

If so copy-n-paste this into that file:

> **RESUME=UUID=4e62c256-41d9-4c3c-9321-15fd3cc70f53**

Then, again, be sure you click on the graphic "Save" and then File > Quit. And double check by running:

```
cat /etc/initramfs-tools/conf.d/resume

```

At this point if you run the three commands:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
cat /etc/initramfs-tools/conf.d/resume
```

The SWAP uuid should be the same in all three. [COLOR="Red"]Just never change the UUID in blkid![/COLOR]

If that all looks good now we have one last thing to do. Run the command:

```
sudo update-initramfs -u
```

That may take a few minutes to run so DO NOT close the terminal until you see it's done, that is you'll see:

> lance@lance-desktop:~$ sudo update-initramfs -u
[sudo] password for lance: 
update-initramfs: Generating /boot/initrd.img-2.6.28-14-generic
lance@lance-desktop:~$ 


Of course you're not "lance@lance" but you get the drift, eh?

---

### Post by desperado666 on 2009-10-22
thanks for help :) all worked well but i have a question. this is my gnome-system-monitor. why is swap not used at all ?

---

### Post by kansasnoob on 2009-10-22
> **desperado666 said:**
> thanks for help :) all worked well but i have a question. this is my gnome-system-monitor. why is swap not used at all ?

Swap will only be used when absolutely needed. That is, if CPU, Ram and/or graphics RAM, etc are all used up. It's also essential to "waking up" after hibernate or suspend.

Have you checked in Gparted right after restarting to be sure it's now mounting properly?

---

### Post by desperado666 on 2009-10-22
```
swapon -s
Filename				Type		Size	Used	Priority 
```

Its mounted yes. see

---

### Post by kansasnoob on 2009-10-22
Awesome, glad I could help.

Just FYI regarding that "gray" space you have now around sda1 and sda2, I'd just leave it be!

Should you choose not to do that be sure to "grow" the existing partitions to the right. Never to the left!

---

### Post by ranch hand on 2009-10-22
> **desperado666 said:**
> thanks for help :) all worked well but i have a question. this is my gnome-system-monitor. why is swap not used at all ?
Fire up Gimp and open about 6 photos that you have taken.  I think that you will see some swap being used then.

---

### Post by desperado666 on 2009-10-22
> **kansasnoob said:**
> Swap will only be used when absolutely needed. That is, if CPU, Ram and/or graphics RAM, etc are all used up. It's also essential to "waking up" after hibernate or suspend.

Have you checked in Gparted right after restarting to be sure it's now mounting properly?

I remember swap was used in jaunty. I am a bit preplex why starting opera takes so much time when i boot my karmic system.

---

