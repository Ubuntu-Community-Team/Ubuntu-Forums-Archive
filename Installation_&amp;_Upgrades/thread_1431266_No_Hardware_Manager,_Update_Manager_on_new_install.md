---
title: "No Hardware Manager, Update Manager on new install"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-03-16
After a fresh install of Ubuntu 9.10-64bit I don't have Hardware Manager, Update Manager or Software Resources just to name a few.

I tried **sudo apt-get update** & **sudo apt-get upgrade** & everything is up to date.

What else can be done?

---

### Post by spyrule on 2010-03-16
Do you mean they're not listed under System->Administration->...

If that's the case, try right clicking on the menu in the panel and go to edit menus.

Navigate to Administration and make sure the check boxes are ticked next to what you want...


If they're not listed at all, try right clicking on the panel, go to Add to Panel, choose Custom Application Launcher, and when that pops up you can add the name and comment of whatever you want, then put '/usr/bin/update-manager', (without the quotes) into the command box... Click OK and try clicking on the new panel icon to see if it launches... If none of this works, just let us know :)

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Do you mean they're not listed under System->Administration->...

If that's the case, try right clicking on the menu in the panel and go to edit menus.

Navigate to Administration and make sure the check boxes are ticked next to what you want...


If they're not listed at all, try right clicking on the panel, go to Add to Panel, choose Custom Application Launcher, and when that pops up you can add the name and comment of whatever you want, then put '/usr/bin/update-manager', (without the quotes) into the command box... Click OK and try clicking on the new panel icon to see if it launches... If none of this works, just let us know :)

Thanks,
They are listed under System/Administration/ but do not respond when trying to open.

---

### Post by spyrule on 2010-03-16
If you push Alt+F2 on your keyboard, you'll get the run application window. Type 'update-manager' (without quotes) in and click run to see if that makes the update manager pop up.

Let me know.

---

### Post by GARoss on 2010-03-16
*System* + rt mouse offers *Edit Menus* but it does not respond.

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> If you push Alt+F2 on your keyboard, you'll get the run application window. Type 'update-manager' (without quotes) in and click run to see if that makes the update manager pop up.

Let me know.

No response. Update manager doesn't open.

---

### Post by spyrule on 2010-03-16
Hmmm... If you open a file browser (click on Places in the menu bar and then click on Computer), navigate to File System->usr->share->applications you should be able to see the Update Manager listed in there... Try double clicking it.

If it's not there, can you open Synaptic Package Manager from your panel->System->Administration->Synaptic... Or is that not there either?

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Hmmm... If you open a file browser (click on Places in the menu bar and then click on Computer), navigate to File System->usr->share->applications you should be able to see the Update Manager listed in there... Try double clicking it.

If it's not there, can you open Synaptic Package Manager from your panel->System->Administration->Synaptic... Or is that not there either?

It's there in the Applications folder, but will not respond to double-click to open. Same with (in Applications folder) Ubuntu Software Center, Software Sources, Hardware Drivers - maybe more. These are listed  under System/Administration, too, with same results.
I can open Synaptic Package Manager but it does act weird. For example, Search doesn't work.

---

### Post by spyrule on 2010-03-16
Are there a bunch of padlock emblems attached to the icons?  Just want to make sure your disk isn't mounted as read-only...

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Are there a bunch of padlock emblems attached to the icons?  Just want to make sure your disk isn't mounted as read-only...

Yes, I see one on Hardware Drivers. *Properties* says this is owned by ROOT. In fact, Update Manager, Ubuntu Software Center, Software Sources all are owned by ROOT under permissions.

---

### Post by spyrule on 2010-03-16
Being owned by root should be fine... But in the permissions dialog does it say that 'Group' and 'Others' can 'Access Files'? And is there a tick mark next to 'Execute'?

---

### Post by oldos2er on 2010-03-16
Can you run **update-manager** in a terminal and post the output here?

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Being owned by root should be fine... But in the permissions dialog does it say that 'Group' and 'Others' can 'Access Files'? And is there a tick mark next to 'Execute'?
Sorry, I didn't notice a new 2nd page. 
Everything is marked root & grayed out - nothing is selectable. No tick mark by Execute.

---

### Post by GARoss on 2010-03-16
> **oldos2er said:**
> Can you run **update-manager** in a terminal and post the output here?

george@george-desktop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
george@george-desktop:~$ ^C
george@george-desktop:~$

---

### Post by spyrule on 2010-03-16
Sorry for the delay... When booting up your system, you probably have an option in the grub (you may have to hit the ESC button when the grub is loading to be able to get to it) to enter into Recovery Mode.

If you can boot into Recovery Mode, try selecting FSCK and letting the system check for errors.

I had some issues after I installed 9.10 on my computer, and this fixed them. If it doesn't work for you, let me know.

---

### Post by GARoss on 2010-03-16
BTW-
I had a lot of problems booting 9.10. After install it would not boot to the desktop probably because of a clash with nVidia drivers. I could only boot to a terminal like screen. 

From there I did a update - upgrade & downloaded/installed 160mb of data. After reboot I still couldn't boot but in the terminal I installed v173 nVidia driver. Still no boot. 

Then in GRUB I typed "e", scrolled down & booted without splash (I didn't edit any lines). This time it booted, but, no Hardware Drivers, etc. In terminal I tried to install a more updated nVidia driver, v185. It wouldn't completely un-install & install. It went into a lockup. 

Today I managed to fix & install v185. So, lots of issues.

---

### Post by oldos2er on 2010-03-16
According to that output you're missing one of the python dependencies. Try running ```
sudo aptitude update && sudo aptitude install python python-central python-dbus python-vte python-gconf
```

If there are any errors, please post them here.

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Sorry for the delay... When booting up your system, you probably have an option in the grub (you may have to hit the ESC button when the grub is loading to be able to get to it) to enter into Recovery Mode.

If you can boot into Recovery Mode, try selecting FSCK and letting the system check for errors.

I had some issues after I installed 9.10 on my computer, and this fixed them. If it doesn't work for you, let me know.
In Recovery Mode there are 6 options, resume boot, clean, DPKG, GRUB, netroot & root. I selected *DPKG says to try to repair... *
it found 2 items & installed. I restarted but all is the same.

---

### Post by GARoss on 2010-03-16
> **oldos2er said:**
> According to that output you're missing one of the python dependencies. Try running ```
sudo aptitude update && sudo aptitude install python python-central python-dbus python-vte python-gconf
```

If there are any errors, please post them here.

Here's everything, Ann. They're still not working but I'll restart to see if that helps.

[I]george@george-desktop:~$ sudo aptitude update
[sudo] password for george: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done

george@george-desktop:~$ sudo aptitude install python python-central python-dbus python-vte python-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

george@george-desktop:~$[/I]

---

### Post by GARoss on 2010-03-16
Restart did nothing

---

### Post by oldos2er on 2010-03-16
I'm at something of a loss as to why update-manager's not working for you. Can you verify that **python -V** shows "Python 2.6.4"?

---

### Post by spyrule on 2010-03-16
I really think this is more of a permissions issue than a corrupt install of python...

Try booting into recovery mode again, but this time click on 'root', log in, and type 'fsck' (all lowercase with no quotes)... You may have to do 'sudo fsck'... Try that and let me know :)

---

### Post by GARoss on 2010-03-16
> **oldos2er said:**
> I'm at something of a loss as to why update-manager's not working for you. Can you verify that **python -V** shows "Python 2.6.4"?

Here it is;
george@george-desktop:~$ python -V
Python 2.6.4
george@george-desktop:~$

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> I really think this is more of a permissions issue than a corrupt install of python...

Try booting into recovery mode again, but this time click on 'root', log in, and type 'fsck' (all lowercase with no quotes)... You may have to do 'sudo fsck'... Try that and let me know :)

[I]WARNING!!! Running e2fsck on mounted filesystem may cause severe damage.

/dev/sda1: Recovering journal
/dev/sda1: clean, 149207/4579328 files, 1066494/18287986 blocks
root[/I]
That's all. Still nothing responds.:shock:

---

### Post by spyrule on 2010-03-16
Do you have more than yourself and root listed as users?

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Do you have more than yourself and root listed as users?
No.

---

### Post by spyrule on 2010-03-16
This is a really interesting problem... :popcorn:


Can you paste the code that you have for your grub.... If you're using grub v1.97 or below, it should be one of the lines that use use to boot from... e.g. (from /boot/grub/menu.lst):

title        Ubuntu 9.10, kernel 2.6.31-20-generic
kernel        (hd0,1)/boot/vmlinuz-2.6.31-20-generic root=/dev/sda2 ro splash 
initrd        (hd0,1)/boot/initrd.img-2.6.31-20-generic

---

### Post by GARoss on 2010-03-16
I attached *Permissions* of *Hardware Drivers*.
What is jockey-gtk.desktop? I found this in Trash.

---

### Post by spyrule on 2010-03-16
jockey-gtk checks to see if you have new hardware installed when you first boot...

you can see if it's in /etc/xdg/autostart

...But I'm not too sure that would cause any of your problems.

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> This is a really interesting problem... :popcorn:


Can you paste the code that you have for your grub.... If you're using grub v1.97 or below, it should be one of the lines that use use to boot from... e.g. (from /boot/grub/menu.lst):

title        Ubuntu 9.10, kernel 2.6.31-20-generic
kernel        (hd0,1)/boot/vmlinuz-2.6.31-20-generic root=/dev/sda2 ro splash 
initrd        (hd0,1)/boot/initrd.img-2.6.31-20-generic

Here's photos. 1st photo is normal GRUB, 2nd is in "e" mode. Not sure if this is what you want.

---

### Post by GARoss on 2010-03-16
Sorry, I feel like an idiot! I didn't read you post correctly. I'm now in */boot/grub/* but do not see *menu.lst*. There is grub.cfg;
[I]#
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 85458c8e-2679-48e2-abdb-a7b184eb8ea8
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 85458c8e-2679-48e2-abdb-a7b184eb8ea8
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=85458c8e-2679-48e2-abdb-a7b184eb8ea8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 85458c8e-2679-48e2-abdb-a7b184eb8ea8
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=85458c8e-2679-48e2-abdb-a7b184eb8ea8 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 85458c8e-2679-48e2-abdb-a7b184eb8ea8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=85458c8e-2679-48e2-abdb-a7b184eb8ea8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 85458c8e-2679-48e2-abdb-a7b184eb8ea8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=85458c8e-2679-48e2-abdb-a7b184eb8ea8 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 8878ac7578ac63a2
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###[/I]

---

### Post by GARoss on 2010-03-16
It must be a hidden file in /usr/share/doc/memtest86+/examples;

[I]# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8[/I]

---

### Post by spyrule on 2010-03-16
Sorry for the delay... I'm going through all of your posts again, and I've setup a VM to see if I can duplicate your issue. Give me a little time, and I'll see if I can find an answer for you.

Until then, if anybody else has some more ideas, I'd love to hear em'.

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Sorry for the delay... I'm going through all of your posts again, and I've setup a VM to see if I can duplicate your issue. Give me a little time, and I'll see if I can find an answer for you.

Until then, if anybody else has some more ideas, I'd love to hear em'.
VM as in virtual machine like Virtual Box? I don't think so as VB has it's own way of managing hardware & bypasses install issues as I had with nVidia video drivers.

After what seemed to be a normal install Ubuntu would not boot. It went into a terminal-like screen. I read there were kernel issues because of a clash with nVidia drivers. I boot in Recovery Mode, selected DPKG repair & did an update/upgrade. It downloaded & installed 160mb of data. After reboot I still couldn't boot but in the terminal. I installed v173 nVidia driver because that's the best it offered. Still no boot.

Then in GRUB I typed "e", scrolled down & booted without splash (I didn't edit any lines). This time it booted to the desktop but System/Administration/Hardware Drivers, etc. none of that worked. 

So, I opened the terminal I tried to install a more updated nVidia driver, v185. It wouldn't completely un-install & install. It went into a lockup at *Removing all DKMS Modules*.

Today I managed to fix & install v185 here we are. I don't know why today was different than yesterday but it didn't lock-up at *Removing all DKMS Modules*. Still, lots of issues.

I appreciate your advice!

---

### Post by spyrule on 2010-03-16
Okay... Thanks for the summary.

Try going into Synaptic Package Manager, once it loads click Edit in the toolbar, click on 'Fix Broken Packages', then click apply (the green check mark icon in the menu). See if that changes anything.

If it doesn't help, try running:

```
sudo dpkg --configure -a
```

From a command line, and let me know what happens or if you get any errors.

---

### Post by spyrule on 2010-03-16
...With the VM I tried to corrupt python, and then I completely removed it. But I was never able to duplicate any of the issues you are having. I cashed the VM something awful though. :)

---

### Post by GARoss on 2010-03-16
> **spyrule said:**
> Okay... Thanks for the summary.

Try going into Synaptic Package Manager, once it loads click Edit in the toolbar, click on 'Fix Broken Packages', then click apply (the green check mark icon in the menu). See if that changes anything.

If it doesn't help, try running:

```
sudo dpkg --configure -a
```

From a command line, and let me know what happens or if you get any errors.

Nothing happened in Synaptic Package Manager when click on 'Fix Broken Packages'.

george@george-desktop:~$ sudo dpkg --configure -a
[sudo] password for george: 
george@george-desktop:~$ 

No errors, I guess. Nothing else happened.

---

### Post by GARoss on 2010-03-16
spyrule,
Earlier today, after installing v173 nVidia driver (at this point I had been able to boot to desktop) I typed "e" at GRUB, then scrolled down until the cursor was beneath *linux /boot/vmlinuz-2.6.31.20-generic root=UUID=85458c8e-2679-48e2a-\bdb-a7b184eb8ea8 ro  quiet splash* then typed Ctrl-x & it booted to desktop. Could this have altered something?

---

### Post by spyrule on 2010-03-16
Nah... That just boots what the command tells it to. Your grub looks fine... I'm still looking for something that might cause this...

---

### Post by GARoss on 2010-03-16
One other note. 
The install disc was scanned before install & reported that it was okay. All was normal during install. When install got to downloading languages I hit "Skip". 
As of now, I cannot boot with Live CD nor can I re-install Ubuntu with disc - it crashes. 
This is all very weird!

---

### Post by GARoss on 2010-03-16
I said before that some software isn't working. I tried to launch *Rhythmbox* from *Applications/Multimedia/Rhythmbox*. It tried but never opened. Then I loaded a song & tried to play it with *Rhythmbox*. Same thing. Then in the terminal it typed* Rhythmbox*, enter & got;
george@george-desktop:~$ rhythmbox
[I]
** (rhythmbox:3956): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3956): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:3956): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
george@george-desktop:~$ [/I]

In Synaptic Manager I un-installed & reinstalled but fared no better.
Weird!

---

### Post by spyrule on 2010-03-17
So, I can't really find any reason why this is happening to you. I figure that something must not have installed correctly when you were re-installing Ubuntu on your box. You may want to try re-installing python from Synaptic Package Manager (in Synaptic, just search for python, right click on it, choose mark for re-installation)...

But if that doesn't work, you may want to completely re-install the OS. Instead of installing Karmic, however, you may want to try installing Jaunty (9.04) just to see if there are differences. The computer I'm using now didn't like Karmic at all, I ended up starting with Jaunty and then upgraded later, but only after installing all of the xorg-edgers packages, and completely re-configuring xorg.conf.

Try the re-install of python and see if it changes anything, let me know.

---

### Post by GARoss on 2010-03-17
> **spyrule said:**
> So, I can't really find any reason why this is happening to you. I figure that something must not have installed correctly when you were re-installing Ubuntu on your box. You may want to try re-installing python from Synaptic Package Manager (in Synaptic, just search for python, right click on it, choose mark for re-installation)...

But if that doesn't work, you may want to completely re-install the OS. Instead of installing Karmic, however, you may want to try installing Jaunty (9.04) just to see if there are differences. The computer I'm using now didn't like Karmic at all, I ended up starting with Jaunty and then upgraded later, but only after installing all of the xorg-edgers packages, and completely re-configuring xorg.conf.

Try the re-install of python and see if it changes anything, let me know.

I'll try python. 
I have burned a new disc, this time a DVD & I can Live CD boot which I could not do before with the CD install. So, re-install is an option now.
And a question about install. I did load and almost did a re-install but thought I'd wait (I don't like the nVidia issues). I got to the partition section where it requires a mount point. Is "/" correct? "/root" is another option. Just want to make sure. Also, I'd be installing over the current Ubuntu which is ext4. I think that should be re-formatted, too?

---

### Post by GARoss on 2010-03-17
Python did not help.

---

### Post by spyrule on 2010-03-17
I really think, imho, that your best option is to start fresh. If you don't have anything on the drive that you need to save, formatting the disk is the best idea. (This goes without saying, but, reformatting will erase all of the data you have on your disk.)

The mount point is up to you. It just means that the folder hierarchy expands from that point... That is, if you have your mount point set to '/', then your etc folder would be '/etc/'. Conversely, if you set your mount point to '/root', then your etc directory would be '/root/etc'. I use a mount point of '/' for simplicities sake.

Good luck, I hope all goes well!

---

### Post by GARoss on 2010-03-17
This thing is weird beyond words. The DVD install disc is acting like the old CD disc. That is, where it booted into install just fine this morning, it now - like the CD - stalls in a boot mode, then begins to flash before it gets to the 7 install steps.
This is garbage!

---

