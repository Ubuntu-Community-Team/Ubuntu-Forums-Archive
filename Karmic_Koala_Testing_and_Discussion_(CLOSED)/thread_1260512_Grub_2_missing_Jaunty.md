---
title: "Grub 2 missing Jaunty"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-09-07
Just updated, and a new grub2 was loaded, and now I no longer have an option for my Jaunty install. When I run sudo update-grub the 9.04 install is listed as found, yet it does not appear on the grub list at startup. The same is also happening for myh install of Moblin2. Anyone else getting the same probs.

---

### Post by patasenko on 2009-09-07
Try searching the forums,
but you could always use comamnd "sudo update-grub2"

---

### Post by celticbhoy on 2009-09-07
I can fix the missing entries using the backup .cfg file I keep, I was wondering if anyone else was having the same problem.

---

### Post by autocrosser on 2009-09-07
Grub2 did the same to me--only install it brought forward was my main testing install--nothing that os-prober had was listed. I did a manual edit & was thinking about a bug report. Have you submitted one yet?

---

### Post by VMC on 2009-09-07
> **celticbhoy said:**
> Just updated, and a new grub2 was loaded, and now I no longer have an option for my Jaunty install. When I run sudo update-grub the 9.04 install is listed as found, yet it does not appear on the grub list at startup. The same is also happening for myh install of Moblin2. Anyone else getting the same probs.

Where are you looking. Grub2 output file is "/boot/grub/grub.cfg" now.

---

### Post by autocrosser on 2009-09-07
If you looked at his second post he knows that......There is a problem with the Grub2 update from today & bringing forward other installs on the system in question--this is only happening with multi-boot systems. Looks like os-prober is having a problem.

I'm posting a bug report against os-prober--will post report# as soon as I do it.

EDIT: looks like a revisit of one of my old bugs---  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500)

---

### Post by cornflake000 on 2009-09-07
I found that after the last grub2 update the jaunty boot line had improper syntax for the UUID.  Where is says --fs_UUID is should actually be --fs-UUID.  Just edit that line to replace the underscore to a dash.

Until it's fixed, that's the way I am getting to my jaunty install.

---

### Post by bennachie on 2009-09-08
Yes, I'm having exactly the same problem, with the added annoyance that Grub2 now doesn't deal correctly with my Windows partition either (it sort of worked with Windows in the previous Alpha). Look forward to hearing the outcomes of the bug report. This kind of thing would be a deal-breaker for most real-world users, so you'd hope it would get pretty high priority.

---

### Post by autocrosser on 2009-09-08
If you were to add to the report things "might" happen a bit faster.....

---

### Post by dino99 on 2009-09-08
solution given on bug report 426061:

in /usr/bin/linux-boot-prober, at the beginning, change :

newns  

        to    


       newns "$@"

then save & close that file & run : sudo grub-mkconfig

that work fine for me.

---

### Post by autocrosser on 2009-09-08
Works a treat!!!  Thanks mate!!!

---

### Post by dino99 on 2009-09-08
there is still something wrong:

since my previous post, a reboot later, the grub2 menu still miss the jaunty entries ( 32 & 64)

Editing the grub,cfg, i don't have any os-prober lines !!! Seem that my grub-mkconfig have not been saved.

So, run again:
sudo os-prober : it don't find the missing distro !!!
sudo update-grub2 : nothing added
sudo grub-mkconfig : everything seem good

run again: sudo update-grub2 & reboot

I'm glad: the grub menu is complete now & it boot fine.

So, it's a workaround but it still need fix

now i'm going to post comments on 426016 bug

---

### Post by philinux on 2009-09-08
I've just updated and the grub update removed startupmanager. Apart from that it seems ok here. Jaunty getting picked up fine.

However. Jaunty is on sda1 and I'm chainloading to karmic on sdb1. Grub2 is installed to the sdb1 root partition not the mbr.

```
### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 40558149-061d-43bc-9068-9c34dbdfa6c7
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro splash vga=792 quiet 
	initrd /boot/initrd.img-2.6.28-14-generic
```

---

### Post by dino99 on 2009-09-08
my config:

karmic 32 on sdc5 with last grub2 1.97b2
jaunty 32 on sdc1 with grub2 1.96
jaunty 64 on sda1 with grub2 1.96

---

### Post by philinux on 2009-09-08
Hi Dino,

My grub legacy is installed on the first HD mbr.

Where is your mbr version of grub then?

---

### Post by dino99 on 2009-09-08
> **philinux said:**
> Hi Dino,

My grub legacy is installed on the first HD mbr.

Where is your mbr version of grub then?

nothing else : 

the jaunty32 is a dist-upgrade of previous release & i always install grub (legacy or now grub2) on the distro partition. 

jaunty64 is an install from scratch, grub1 installed on the same partition, then moved to grub2

karmic32 is a clean install with his grub2 too.

First hdd in bios : sda

You surely know that grub-legacy is totally dropped now & menu.list is no more used ( changes was made end of last week if i remember).

---

### Post by philinux on 2009-09-08
> **dino99 said:**
> nothing else : 

the jaunty32 is a dist-upgrade of previous release & i always install grub (legacy or now grub2) on the distro partition. 

jaunty64 is an install from scratch, grub1 installed on the same partition, then moved to grub2

karmic32 is a clean install with his grub2 too.

You surely know that grub-legacy is totally dropped now & menu.list is no more used ( changes was made end of last week if i remember).

Only using grub-legacy on jaunty.

---

### Post by dino99 on 2009-09-08
hi Phil

jaunty can use grub2 but it still with 1.96 , that makes me afraid because karmic have a newer version now. Grub2 menu is build by karmic and i can update grub from jaunty without trouble at time. For security grub-legacy seem to be a better choice for jaunty as Ubuntu does not upgrade grub2 at the same time on the 2 distro.

---

### Post by DougieFresh4U on 2009-09-08
Well sadly, I got hit with the drama this morning.
Updated my Karmic 64bit on sda8. Rebooted and only Karmic on sda7 and Windows on sda1 were in my grub. Missing Jaunty on sda6 and Karmic sda8
Would some one look at the following and see what the problem is
Thanks
```
dougie@DougiesLeanMachine:~$ sudo os-prober
[sudo] password for dougie: 
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda6:Ubuntu 9.04 (9.04):Ubuntu:linux
/dev/sda8:Ubuntu karmic (development branch) (9.10):Ubuntu1:linux
dougie@DougiesLeanMachine:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-9-generic
Found initrd image: /boot/initrd.img-2.6.31-9-generic
Found linux image: /boot/vmlinuz-2.6.31-8-generic
Found initrd image: /boot/initrd.img-2.6.31-8-generic
Found linux image: /boot/vmlinuz-2.6.31-7-generic
Found initrd image: /boot/initrd.img-2.6.31-7-generic
Found linux image: /boot/vmlinuz-2.6.30-1-generic
Found initrd image: /boot/initrd.img-2.6.30-1-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 9.04 (9.04) on /dev/sda6
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8
done
dougie@DougiesLeanMachine:~$ sudo grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default=0
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
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
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-9-generic
Found initrd image: /boot/initrd.img-2.6.31-9-generic
menuentry "Ubuntu, Linux 2.6.31-9-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-9-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-9-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-9-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.31-9-generic
}
Found linux image: /boot/vmlinuz-2.6.31-8-generic
Found initrd image: /boot/initrd.img-2.6.31-8-generic
menuentry "Ubuntu, Linux 2.6.31-8-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-8-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-8-generic
}
menuentry "Ubuntu, Linux 2.6.31-8-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-8-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.31-8-generic
}
Found linux image: /boot/vmlinuz-2.6.31-7-generic
Found initrd image: /boot/initrd.img-2.6.31-7-generic
menuentry "Ubuntu, Linux 2.6.31-7-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-7-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-7-generic
}
menuentry "Ubuntu, Linux 2.6.31-7-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-7-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.31-7-generic
}
Found linux image: /boot/vmlinuz-2.6.30-1-generic
Found initrd image: /boot/initrd.img-2.6.30-1-generic
menuentry "Ubuntu, Linux 2.6.30-1-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.30-1-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.30-1-generic
}
menuentry "Ubuntu, Linux 2.6.30-1-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.30-1-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.30-1-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Vista (loader) on /dev/sda1
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0882c33a82c32ad0
	chainloader +1
}
Found Ubuntu 9.04 (9.04) on /dev/sda6
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###
done
dougie@DougiesLeanMachine:~$ 


```

---

### Post by dino99 on 2009-09-08
look at post #12



This bug was fixed in the package os-prober - 1.32

---------------
os-prober (1.32) unstable; urgency=low

  * Pass arguments properly to newns (thanks, Roger E Critchlow Jr; LP:
    #426061).

 -- Colin Watson <cjwatson@canonical.com> Tue, 08 Sep 2009 12:33:12 +0100

---

### Post by ranch hand on 2009-09-08
> **DougieFresh4U said:**
> Well sadly, I got hit with the drama this morning.
Updated my Karmic 64bit on sda8. Rebooted and only Karmic on sda7 and Windows on sda1 were in my grub. Missing Jaunty on sda6 and Karmic sda8
Would some one look at the following and see what the problem is
Thanks
```
dougie@DougiesLeanMachine:~$ sudo os-prober
[sudo] password for dougie: 
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda6:Ubuntu 9.04 (9.04):Ubuntu:linux
/dev/sda8:Ubuntu karmic (development branch) (9.10):Ubuntu1:linux
dougie@DougiesLeanMachine:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-9-generic
Found initrd image: /boot/initrd.img-2.6.31-9-generic
Found linux image: /boot/vmlinuz-2.6.31-8-generic
Found initrd image: /boot/initrd.img-2.6.31-8-generic
Found linux image: /boot/vmlinuz-2.6.31-7-generic
Found initrd image: /boot/initrd.img-2.6.31-7-generic
Found linux image: /boot/vmlinuz-2.6.30-1-generic
Found initrd image: /boot/initrd.img-2.6.30-1-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 9.04 (9.04) on /dev/sda6
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8
done
dougie@DougiesLeanMachine:~$ sudo grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default=0
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
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
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-9-generic
Found initrd image: /boot/initrd.img-2.6.31-9-generic
menuentry "Ubuntu, Linux 2.6.31-9-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-9-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-9-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-9-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.31-9-generic
}
Found linux image: /boot/vmlinuz-2.6.31-8-generic
Found initrd image: /boot/initrd.img-2.6.31-8-generic
menuentry "Ubuntu, Linux 2.6.31-8-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-8-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-8-generic
}
menuentry "Ubuntu, Linux 2.6.31-8-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-8-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.31-8-generic
}
Found linux image: /boot/vmlinuz-2.6.31-7-generic
Found initrd image: /boot/initrd.img-2.6.31-7-generic
menuentry "Ubuntu, Linux 2.6.31-7-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-7-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-7-generic
}
menuentry "Ubuntu, Linux 2.6.31-7-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.31-7-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.31-7-generic
}
Found linux image: /boot/vmlinuz-2.6.30-1-generic
Found initrd image: /boot/initrd.img-2.6.30-1-generic
menuentry "Ubuntu, Linux 2.6.30-1-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.30-1-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro splash #GRUB_DISABLE_LINUX_UUID=true vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.30-1-generic
}
menuentry "Ubuntu, Linux 2.6.30-1-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 785fc95b-8e13-4e69-b347-5c7e831952b5
	linux	/boot/vmlinuz-2.6.30-1-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=794
	initrd	/boot/initrd.img-2.6.30-1-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Vista (loader) on /dev/sda1
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0882c33a82c32ad0
	chainloader +1
}
Found Ubuntu 9.04 (9.04) on /dev/sda6
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###
done
dougie@DougiesLeanMachine:~$ 


```
I don't see any mention of "30_os-prober on your menu.  While I never had it not mentioned I did have problems like this last night.

That was on my 64bit variations that I update in the evening.  The grub.cfg would look fine until you got to the prober part and it was empty.

Updated the 32bit variations this morning and they did not have this problem.

Booted to my 64bit drive and ran update on one of them and go another os-prober update that cured the problem there too.

I think that a new update of your system will cure the problem.

---

### Post by dino99 on 2009-09-08
upgrade to os-prober 1.32

---

### Post by DougieFresh4U on 2009-09-08
Thanks ranch hand
Some times the easiest solution is so hard.
All is good except my compiz is not working now.
That's for another time to settle

---

### Post by bluebyt on 2009-09-10
I run the following command "sudo os-prober" and "sudo update-grub2".

Now all my os are listed and boot up properly. (Jaunty, Karmic, Windows seven)

But when I boot with Jaunty the usplash doesn't appeared?

---

### Post by celticbhoy on 2009-09-10
I have the Usplash problem with both Jaunty & Karmic since Grub2.

---

### Post by celticbhoy on 2009-09-10
I have had the Usplash problem with Jaunty & Karmic since Grub2

---

### Post by m10 on 2009-09-19
i have that problem too(grub2 doesn't recognize jaunty). all mentioned fixes do not work. more info at [http://ubuntuforums.org/showthread.php?t=1270132](http://ubuntuforums.org/showthread.php?t=1270132).
I discovered this post only after having posted mine,sry.
Any help is much appreciated

---

