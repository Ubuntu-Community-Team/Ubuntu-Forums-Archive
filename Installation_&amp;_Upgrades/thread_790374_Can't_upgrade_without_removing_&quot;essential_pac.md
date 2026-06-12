---
title: "Can't upgrade without removing &quot;essential package&quot;"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by who_cares on 2008-05-11
I would like to upgrade my copy of Ubuntu 7.10 Studio to 8.04, but when I clicked upgrade in the update manager it came back saying there was an error to look in the logs.
I found this in /var/log/dist-upgrade/main.log
> 2008-05-10 16:10:34,427 ERROR Dist-upgrade failed: 'A essential package would have to be removed'

and this was in apt.log:
> Investigating linux-restricted-modules-rt
Package linux-restricted-modules-rt has broken dep on linux-restricted-modules-2.6.24-16-rt
  Considering linux-restricted-modules-2.6.24-16-rt 1 as a solution to linux-restricted-modules-rt 1
  Holding Back linux-restricted-modules-rt rather than change linux-restricted-modules-2.6.24-16-rt
Investigating linux-rt
Package linux-rt has broken dep on linux-restricted-modules-rt
  Considering linux-restricted-modules-rt 1 as a solution to linux-rt 0
  Removing linux-rt rather than change linux-restricted-modules-rt
 Try to Re-Instate linux-restricted-modules-rt
Done
Log time: 2008-05-10 16:10:38.027178
Does anyone know what I need to do to finish upgrading?

---

### Post by bapoumba on 2008-05-11
May be the sources.list was not properly re-written during the dist-upgrade, please post it:
```
cat /etc/apt/sources.list
```
linux-restricted-modules-2.6.24-16-rt is in multiverse.

---

### Post by who_cares on 2008-05-11
Here you go:
> #
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets


---

### Post by bapoumba on 2008-05-12
You still have gutsy only repos in your sources.list. How did you try to go to hardy? From update-manager?
Please post:

```
lsb_release -cd
uname -a
```

One way to go to hardy would be to remove the CD repo (first line), change all the gutsy occurrences to hardy, and then dist-upgrade. Let's see first what version you are actually running, and which kernel you booted to.

---

### Post by who_cares on 2008-05-12
Well I had to reboot it and now the normal boot doesn't work, I can get to recovery mode though.

Here's lsb_release -cd:
> Description: Ubuntu 7.10
Codename: gutsy
and uname -a:
> Linux Cam-Desktop 2.6.22-14-rt #1 SMP PREEMPT RT Tue Feb 12 09:57:10 UTC 2008 i686 GNU/Linux

---

### Post by who_cares on 2008-05-13
Okay, I can boot normally again now for some reason.
I removed the three non-ubuntu package sources from my sources.list since avant is in the ubuntu repo now, but it still doesn't want to upgrade.
I guess I'll try changing gutsy to hardy in sources.list

---

### Post by who_cares on 2008-05-13
Okay, I got it to upgrade to hardy, lsb_release says 8.04 now, but there were a bunch of packages held back, like X, gdm, and firefox. Also none of the windows have close buttons anymore.

---

### Post by Oldsoldier2003 on 2008-05-13
> **who_cares said:**
> Okay, I got it to upgrade to hardy, lsb_release says 8.04 now, but there were a bunch of packages held back, like X, gdm, and firefox. **Also none of the windows have close buttons anymore**.

```
metacity --replace
```

---

### Post by bapoumba on 2008-05-13
> Linux Cam-Desktop 2.6.22-14-rt #1 SMP PREEMPT RT Tue Feb 12 09:57:10 UTC 2008 i686 GNU/Linux 
Two questions here:
- Hardy kernel is 2.6.24-16, you're not running on it. Please post:
```
cat /boot/grub/menu.lst
```
- any reason to run the -rt kernel and not the generic one?

Also make sure ubuntu-dektop is installed. Your desktop problems may be linked to the kernel you are running on or some missing packages (ruuning compiz and desktop effects?)

---

### Post by who_cares on 2008-05-13
> **bapoumba said:**
> Two questions here:
- Hardy kernel is 2.6.24-16, you're not running on it. Please post:
```
cat /boot/grub/menu.lst
```
- any reason to run the -rt kernel and not the generic one?
No idea, that was the kernel that it originally installed (I'm using the Ubuntu Studio version)

> Also make sure ubuntu-dektop is installed. Your desktop problems may be linked to the kernel you are running on or some missing packages (ruuning compiz and desktop effects?)
installing ubuntu-desktop leads to this:
> cameron@Cam-Desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for cameron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: ubuntu-sounds but it is not going to be installed
                  Recommends: bug-buddy but it is not going to be installed
E: Broken packages


---

### Post by bapoumba on 2008-05-14
Let's go back to the basics, please post your sources.list again:
```
cat /etc/sources.list
```
The error is typical of missing repositories.

And:
```
cat /boot/grub/menu.lst
```
I've seen some cases where the previous kernel was automatically selected (did you say to keep the menu.lst when upgrading to hardy?).

---

### Post by who_cares on 2008-05-14
Okay, here's sources.list:
> cameron@Cam-Desktop:~$ cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
cameron@Cam-Desktop:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
#deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


and here's menu.lst:
> cameron@Cam-Desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
splashimage=(hd0,2)/boot/grub/splashimages/blu.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9713a9b4-459d-4ad3-a184-af303db57a2f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=775

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=9713a9b4-459d-4ad3-a184-af303db57a2f ro quiet splash vga=775
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=9713a9b4-459d-4ad3-a184-af303db57a2f ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1



---

### Post by bapoumba on 2008-05-14
Your sources.list is fine.

Something I do not understand: hardy kernel is 2.6.24-16, at least for the generic one I am using. I searched around and did not find which one ubuntu-studio is supposed to install (I guess the rt, real time kernel, comes from ubuntu-studio). May be I did not look enough, will try again.

So I'll assume your upgrade to hardy is not complete. Please try:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Sometimes the dist-upgrade has to be run several times in a row (just happened to me this morning, had to run it twice). dist-upgrade performs an upgrade checking for dependencies more carefully.

---

### Post by who_cares on 2008-05-15
Okay, that upgraded most of my packages. I now have the 2.6.24-16-rt kernel, but I can't login either. When it finishes booting it goes to the normal login screen, but when I login it goes to a gray screen with a black x for a mouse and stays there.

---

### Post by bapoumba on 2008-05-15
> **who_cares said:**
> Okay, that upgraded most of my packages. I now have the 2.6.24-16-rt kernel, but I can't login either. When it finishes booting it goes to the normal login screen, but when I login it goes to a gray screen with a black x for a mouse and stays there.

That could be a video driver issue. Do you know which video card you have, and how you got it to run with gutsy?

---

### Post by dstew on 2008-05-15
This problem may be with the inability of the standard Hardy upgrade to come to terms with the Ubuntu studio system. Maybe you have to upgrade to the Hardy Ubuntu Studio system instead. It reminds me of the problems upgrading when using restricted drivers.

---

### Post by bapoumba on 2008-05-15
> **dstew said:**
> This problem may be with the inability of the standard Hardy upgrade to come to terms with the Ubuntu studio system. Maybe you have to upgrade to the Hardy Ubuntu Studio system instead. It reminds me of the problems upgrading when using restricted drivers.

Or the rt kernel, [see here]("http://ubuntuforums.org/showthread.php?t=793480").

Please have a look at this bug: [lpbug]197130[/lpbug]. Do you have an nvidia video card? Please see at the end og the bug, some have made it work.
Could you use the generic kernel?

---

### Post by who_cares on 2008-05-15
> **bapoumba said:**
> Or the rt kernel, [see here]("http://ubuntuforums.org/showthread.php?t=793480").

Please have a look at this bug: [lpbug]197130[/lpbug]. Do you have an nvidia video card? Please see at the end og the bug, some have made it work.
Could you use the generic kernel?
My problem doesn't seem quite the same as those. X loads just fine and I get the normal login screen. It's after I login that it goes gray and leaves me with an x for a mouse. The mouse still works but there's nothing to click. Ctrl+Alt+Backspace restarts X like it should, but it never lets me finish the login.
I'm not really sure if I even need the rt kernel, that's just how it was when I installed it. If I need the generic one then I don't see why I wouldn't be able to use it.
Oh, and I do have an nvidia card.

---

### Post by bapoumba on 2008-05-15
As dstew said, it is somewhere during the upgrade to hardy, or some problem with the video drivers, associated or not to the kernel. I do not know ubuntu studio very well. As their support page states they use the Multimedia Production sub-forum on UF for support, I'll move the post there. Hopefully, someone will be better able to help you :)

---

### Post by appzattak on 2008-05-15
I had the same prob, when looking in at the /var/log/dist-upgrade/main.log I noticed that the package causing the prob was nvidia-glx 

I uninstalled it from the Synaptic Package Manager and then the upgrade went fine. After workds I had to reinstall that and all is good to go now.

---

