---
title: "adding new hard drive and then beta"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by ray field on 2012-03-15
I want to try out the 12.04 beta so I will be getting a new hard drive. been happy with Lucid but if I'm going to have to move everything over eventually I just want to get used to things, eg if I need to switch to LibreOffice I need to see how it's going to work.

1) can I install 12.04 to the new drive from within Lucid once I've partitioned it?

2) can I rely on Grub to add the new installation on the new hard drive? is there anything I should know/anticipate? what will it look like on bootup? right now there are about twenty kernels, plus XP at the bottom of the list.

---

### Post by darkod on 2012-03-15
1. Why install from within Lucid? You do it in the same way as if you don't have ubuntu. Fire up from the cd and take it from there.

2. Yes, you can rely on grub2 from Lucid to add 12.04 to the menu. But if you plan to keep using grub2 from Lucid, you need to tell 12.04 not to install a bootloader when installing. I am not sure if you can do this because in 11.10 they removed the option not to install a bootloader, you had to select a location to install it. In case it's the same in 12.04 but you do want to keep grub2 from Lucid running the show, you can use the manual install method and tell the bootloader to install on the same 12.04 disk. Keep booting from the Lucid disk and problem solved.
If you use one of the auto methods when installing 12.04 I am not sure where the bootloader will go, whether to sda or sdb.
Depending how you do things, you might need to run update-grub in Lucid so that 12.04 shows up.

If you use grub2 from 12.04 you will notice that the list of all kernels doesn't show up any more. There is only one entry Previous Versions combining all older kernels under it. So the menu looks a bit tidier. In any case, you can remove your old kernels in Lucid and that list will shrink too.

---

### Post by miegiel on 2012-03-15
> **ray field said:**
> 2) can I rely on Grub to add the new installation on the new hard drive? is there anything I should know/anticipate? what will it look like on bootup? right now there are about [COLOR="Red"]twenty kernels[/COLOR], plus XP at the bottom of the list.

lol Sorry, don't be offended but you made me laugh :D

Assuming you don't use all those kernels go to */boot/* and remove the old kernels you don't want/use/need (you'll need root privileges to remove them). I only keep the current and previous kernel.

Regarding GRUB: if there are OSes or kernels on your machine but not in the grub menu, or there are old OSes or kernels in the menu that you have removed, run
```
sudo update-grub
```
and GRUB wil look for new stuff to add and old stuf to remove from the boot menu.

---

### Post by ray field on 2012-03-15
very helpful, Darkod. I really don't much care for installations, they always take longer than I want and something always seems to happen -- I figured if I could install from withing a booted Lucid I could 1) remove the possibility of overwriting 10.04, and 2) continue to use the machine to work on. since I want to see how well all the applications I use on Lucid work on Precise.

I'm indifferent as to which grub I use, though generally speaking I like to assume latest is greatest. I am a little bit worried about sda v. sdb -- are internal drives still master/slave, or will the BIOS allow me to select which drive is recognized first?

no offense taken, Miegiel! I just don't like to futz with anything that MIGHT break.

since I'm asking -- did I see somewhere that 64-bit is the default or something? since I prefer to stay from the bleeding edge, plus I rely on funky things like dosemu which can be touchy, I think I'd rather stay 32-bit -- is that what I'll get with this here ubuntu-12.04-beta1-desktop-i386.iso I downloaded?

---

### Post by miegiel on 2012-03-15
> **ray field said:**
> since I'm asking -- did I see somewhere that 64-bit is the default or something? since I prefer to stay from the bleeding edge, plus I rely on funky things like dosemu which can be touchy, I think I'd rather stay 32-bit -- is that what I'll get with this here ubuntu-12.04-beta1-desktop-i386.iso I downloaded?

Yes, i386 is the 32bit version.

---

### Post by darkod on 2012-03-15
SATA disks have no master/slave settings like IDE although in BIOS you might see the sata ports "grouped" as SATA0 Master, SATA0 Slave, etc.

Usually sda and sdb would be allocated according to discovery on boot, and in general it should be in the order of the sata ports from lowest to highest. But regardless of that, once you have them connected, the reference doesn't change unless you change the ports where the disks are plugged in.

So, for example, you receive the new disk, connect it, boot your Lucid and run fdisk -l. If it shows Lucid as sda and the new disk as sdb, that's what you have got. And it will be easy to tell the disks apart even if they are same size because one is empty. :)

---

### Post by ray field on 2012-03-17
as long as I'm going to play with this beta on a new drive, here's what I'm thinking I would do:

1) copy the /home partition from my Lucid install to the new one

2) use dpkg --get-selections > filename to get the full list of packages I want to reinstall on Precise

3) this one could be really chancey: copy /etc/apt/sources.list from the Lucid side and replace "lucid" with "precise" for all

what are the odds of this resulting in a working system? I guess in a way what I'd be doing is an upgrade-drill to my existing LTS release. comments? am I nuts?

---

### Post by oldfred on 2012-03-17
You need to plan ahead on partitions for new drive. Copying /home is fine. New install will update many settings.

I use dpkg to export list of packages and reimport into new install. But now so much has changed that old list installs a lot of software not required anymore. You can manually edit list to remove OpenOffice, old kernels and others. I found I was still installing python2.5. :( 
With 12.04 I will try to run a compare of the default install to my exported list and houseclean down to a reasonable list of only the old apps I really want.

Why copy sources list? You could add if you have one or two you have added to you old system but I would not attempt to copy the entire thing and edit. Any edit error in sources list causes big issues, so whatever you do backup its original first.

Some guides on installing to second drive. Difference in versions are minor as I used the same procedure for every version.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by ray field on 2012-03-18
> **oldfred said:**
> You need to plan ahead on partitions for new drive. Copying /home is fine. New install will update many settings.

I use dpkg to export list of packages and reimport into new install. But now so much has changed that old list installs a lot of software not required anymore. You can manually edit list to remove OpenOffice, old kernels and others. I found I was still installing python2.5. :( 
With 12.04 I will try to run a compare of the default install to my exported list and houseclean down to a reasonable list of only the old apps I really want.

point well taken. in fact the base installation derives from several versions ago -- Jaunty, maybe even Intrepid as well. which might explain the occasional lag I get, or issues I get that probably relate to bodged multimedia libraries. and the last few times I've run Remastersys -dist to back up the system, the filesize has gotten too big. so, much as I would prefer to just copy everything & switch over -- there are dozens of little things I use every day -- it makes more sense to start anew and install as I need. 

last night I put in the new HD and installed the Precise beta, and so far so good, though I haven't done much more than set grub to sdb, reboot to see it worked, and then changed the default Nautilus view to List. 

one thing that concerns me about Unity is I use a ton of applications and I've always liked the Applications menu, especially for things whose names I can't remember.

anyway now I'm back in Lucid, and  

1) using mc, I copied nearly everything from this /home to the Precise /home. although I specified not to overwrite any existing directories, I went back and copied over .thunderbird and .mozilla and will do a few other things. will be very interested to see what happens when I reboot.

2) also copied the Precise /Documents/OpenOffice to /Documents/LibreOffice, since I gather I can't use OO and LO at the same time, I am hoping various templates and macros will work.

3) copied the Lucid fstab entries that refer to two external hard drives and the Lucid /usr/local/data partition to the Precise fstab (after making a copy of the original Precise fstab)

since I use SSH for a few things, including syncing with my netbook and maintaining a Drupal site, I just copied the contents of the Lucid /etc/ssh into the Precise /etc/ssh. fingers are crossed.

---

### Post by oldfred on 2012-03-18
I started with new installs with 9.10 after upgrading every 6 months in place from 6.06. Upgrades always seemed to have some issue so they were not the end all best way.

But I found with clean installs I was doing the same thing over & over. I configured my Laptop to be similar to my Desktop and was doing it all twice. So then I decided to try to do as much as I could from command line, listed history & copied commands into a bash file. After some edits I had a personalized install routine.

I installed fall-back and find it close enough to the old style gnome2. I also so not remember names, believe if using keyboard I should do everything there, or if using mouse should be able to only use mouse. I do not like having to type in a file name to launch a program when using mouse. 

I have not tried this yet in 12.04 as I keep trying to learn a bit about Unity. But will install it soon in my test version.
Return to Ubuntu Classic Desktop in Ubuntu 11.10
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

---

### Post by ray field on 2012-03-18
> **oldfred said:**
> I started with new installs with 9.10 after upgrading every 6 months in place from 6.06. Upgrades always seemed to have some issue so they were not the end all best way.

But I found with clean installs I was doing the same thing over & over. I configured my Laptop to be similar to my Desktop and was doing it all twice. So then I decided to try to do as much as I could from command line, listed history & copied commands into a bash file. After some edits I had a personalized install routine.

this is very wise & I think is going to be how I do things going forward. by the time Precise goes gold I should be up to speed & will have an install routine ready for the netbook -- which really *needs* something like Unity, since right now too much screen real estate is taken up with menus and launchers.

> **oldfred said:**
> I installed fall-back and find it close enough to the old style gnome2. I also so not remember names, believe if using keyboard I should do everything there, or if using mouse should be able to only use mouse. I do not like having to type in a file name to launch a program when using mouse. 

I have not tried this yet in 12.04 as I keep trying to learn a bit about Unity. But will install it soon in my test version.

I think the key to not hating Unity is waiting till it got out of alpha. certainly if Compiz is as thoroughly integrated as it seems to be from my first impression, it should be fine. in fact it is starting to look to me like a sort of inevitable evolution rather than some crazed notion of Shuttleworth's.

thanks to all for the guidance (handholding).

---

### Post by ray field on 2012-03-24
okay, I've been playing around with Precise and doing a little tweaking. 

however, though Update Manager has installed another kernel

/boot/vmlinuz-3.2.0-20-generic-pae

it doesn't come up on the grub menu on reboot -- only 3.2.0-19 is there (maybe .17 sometimes as well).  I'm pretty sure I set Grub to boot from the first hard disk since it was more important for me to work on the Lucid side. I tried to run update-grub from there, and it seemed to be aware of the kernel on /dev/sdb but didn't seem willing to add 3.2.0-20.

how can I make sure grub updates the grub menu I use all the time, the one on /dev/hda, or am I missing something?  searching I came across this from good old Fred:

> Grub can be nasty on which MBR it installs. It wants to install to sda or the boot drive. They are updating and it seems to change.

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc

however when I tried to run this in a terminal, I got 

```
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed
```

and when I tried to install grub-pc through synaptic, I got

```
The following packages were automatically installed and are no longer required:
  casper kde-l10n-de libdiscover2 kde-l10n-engb squashfs-tools xresprobe
  discover user-setup kde-l10n-zhcn liblzo2-2 discover-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-gfxpayload-lists grub2-common
The following packages will be REMOVED:
  grub remastersys
The following NEW packages will be installed:
  grub-gfxpayload-lists grub-pc grub2-common
```

which seems a little drastic to me, especially since I plan on using remastersys.

---

### Post by jmore9 on 2012-03-24
As far as master / slave on my machine i have to go into the bios and select which sata drive is to be booted from. Otherwise nothing will happen as far that.  It will go back to the pata drive controller and look there.

---

### Post by ray field on 2012-03-25
drive booting is fine, no concern there.

what's baffling me is why my grub menu won't show the latest installed kernel.

here is the result of running update-grub under Precise:

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-20-generic-pae
Found kernel: /boot/vmlinuz-3.2.0-19-generic-pae
Found kernel: /boot/vmlinuz-3.2.0-17-generic-pae
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

here is /boot/grub/menu.lst from the Precise disk

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=45732781-962e-4e76-9cc8-9aabe50be5be

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
# defoptions=quiet splash

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu precise (development branch), kernel 3.2.0-20-generic-pae
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/vmlinuz-3.2.0-20-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro quiet splash 
initrd		/boot/initrd.img-3.2.0-20-generic-pae

title		Ubuntu precise (development branch), kernel 3.2.0-20-generic-pae (recovery mode)
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/vmlinuz-3.2.0-20-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro  single
initrd		/boot/initrd.img-3.2.0-20-generic-pae

title		Ubuntu precise (development branch), kernel 3.2.0-19-generic-pae
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/vmlinuz-3.2.0-19-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro quiet splash 
initrd		/boot/initrd.img-3.2.0-19-generic-pae

title		Ubuntu precise (development branch), kernel 3.2.0-19-generic-pae (recovery mode)
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/vmlinuz-3.2.0-19-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro  single
initrd		/boot/initrd.img-3.2.0-19-generic-pae

title		Ubuntu precise (development branch), kernel 3.2.0-17-generic-pae
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/vmlinuz-3.2.0-17-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro quiet splash 
initrd		/boot/initrd.img-3.2.0-17-generic-pae

title		Ubuntu precise (development branch), kernel 3.2.0-17-generic-pae (recovery mode)
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/vmlinuz-3.2.0-17-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro  single
initrd		/boot/initrd.img-3.2.0-17-generic-pae

title		Chainload into GRUB 2
root		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/grub/core.img

title		Ubuntu precise (development branch), memtest86+
uuid		45732781-962e-4e76-9cc8-9aabe50be5be
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

here is the Lucid /boot.grub/grub.cfg

```
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
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
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.38-13-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.38-13-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.38-13-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-13-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.38-12-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.38-12-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.38-12-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-12-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-40-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-40-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-40-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-40-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-40-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-39-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-39-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-39-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-39-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-39-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-38-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-38-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-38-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-37-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-37-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-37-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-36-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-36-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-36-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-36-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-36-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-35-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-35-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-35-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-35-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-35-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux	/boot/vmlinuz-2.6.32-34-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-34-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	echo	'Loading Linux 2.6.32-34-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-34-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-34-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c9b2fa81-cb35-4f66-92bc-73de7c949bc7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 367C57DA7C579409
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu precise (development branch), kernel 3.2.0-20-generic-pae (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/vmlinuz-3.2.0-20-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro quiet splash
	initrd /boot/initrd.img-3.2.0-20-generic-pae
}
menuentry "Ubuntu precise (development branch), kernel 3.2.0-20-generic-pae (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/vmlinuz-3.2.0-20-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro single
	initrd /boot/initrd.img-3.2.0-20-generic-pae
}
menuentry "Ubuntu precise (development branch), kernel 3.2.0-19-generic-pae (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/vmlinuz-3.2.0-19-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro quiet splash
	initrd /boot/initrd.img-3.2.0-19-generic-pae
}
menuentry "Ubuntu precise (development branch), kernel 3.2.0-19-generic-pae (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/vmlinuz-3.2.0-19-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro single
	initrd /boot/initrd.img-3.2.0-19-generic-pae
}
menuentry "Ubuntu precise (development branch), kernel 3.2.0-17-generic-pae (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/vmlinuz-3.2.0-17-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro quiet splash
	initrd /boot/initrd.img-3.2.0-17-generic-pae
}
menuentry "Ubuntu precise (development branch), kernel 3.2.0-17-generic-pae (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/vmlinuz-3.2.0-17-generic-pae root=UUID=45732781-962e-4e76-9cc8-9aabe50be5be ro single
	initrd /boot/initrd.img-3.2.0-17-generic-pae
}
menuentry "Chainload into GRUB 2 (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/grub/core.img 
}
menuentry "Ubuntu precise (development branch), memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 45732781-962e-4e76-9cc8-9aabe50be5be
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

yet the startup grub menu NEVER shows 3.2.0-20-generic-pae, instead it shows vmlinuz-3.2.0-19-generic-pae as the very first & highlighted selection.

---

### Post by oldfred on 2012-03-25
You are showing both grub legacy & grub2. A sudo update-grub only updates one or the other not both. Best to uninstall both and cleaning install the one you want. I suggest keeping grub2.

You can skip the chroot steps but make sure you have Internet working as you need to redown load the grub2 packages.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ray field on 2012-03-25
that fixed it. thanks, Fred, you are heaven-sent.

---

