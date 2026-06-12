---
title: "Last update -&gt; black screen"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by indifference on 2009-09-16
Hello,

I've updated karmic last night and now I cant boot anymore. All I get is a black screen where nothing works, even the capslock key doesn't work.

I've try to boot in recovery mode but the issue is still present, so I cant do a thing...

My graphics card is an integrated intel 855gm.

Luckly for me, I dual boot with Arch...

Please help!

Thanks,

Pedro Saraiva

---

### Post by Eestlane on 2009-09-16
Try do chroot via Live cd (or Arch) and make an update. Check this forums previous threads and you find all kind of tricks to use.

---

### Post by VMC on 2009-09-16
From Arch...
Here's two scripts I use to chroot:
(replace sda7 with your karmic partition)
```
#!/bin/bash
## /mnt
mount /dev/***[COLOR="Red"]sda7[/COLOR]*** /mnt/
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev/pts /mnt/dev/pts
cp /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt/ /bin/bash
```

Now Inside karmic, I update using this method:
```
sudo aptitude update && sudo aptitude full-upgrade

```
When complete, Ctrl+d to release chroot. Then I run the following script to cleanly unmount everything:
```
#!/bin/bash
## /mnt already exists
umount /mnt/dev/pts
umount /mnt/sys
umount /mnt/proc
umount /mnt/dev
umount /mnt
```

---

### Post by dentaku65 on 2009-09-16
Do you have intel as video card?

---

### Post by bacardiandwatermelon on 2009-09-16
My install is stuffed, i'm just going to wait for alpha 6.

---

### Post by slakkie on 2009-09-16
> **VMC said:**
> From Arch...
Here's two scripts I use to chroot:
(replace sda7 with your karmic partition)
```
#!/bin/bash
## /mnt
mount /dev/***[COLOR="Red"]sda7[/COLOR]*** /mnt/
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev/pts /mnt/dev/pts
cp /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt/ /bin/bash
```

Now Inside karmic, I update using this method:
```
sudo aptitude update && sudo aptitude full-upgrade

```
When complete, Ctrl+d to release chroot. Then I run the following script to cleanly unmount everything:
```
#!/bin/bash
## /mnt already exists
umount /mnt/dev/pts
umount /mnt/sys
umount /mnt/proc
umount /mnt/dev
umount /mnt
```

I use the following for that.

```

#!/bin/bash
mnt=/mnt/karmic-chroot
dev=/dev/sda1
mnt_devices="proc dev dev/pts sys"

start() {
	sudo mkdir "$mnt"
	sudo mount $dev "$mnt"

	for i in $mnt_devices ; do
		sudo mount -o bind /$i "$mnt"/$i
	done

	sudo mv "$mnt"/etc/resolv.conf "$mnt"/etc/resolv.conf.orig
	sudo cp /etc/resolv.conf "$mnt"/etc/resolve.conf
	sudo chroot "$mnt" /bin/bash

}

stop() {
	for i in $mnt_devices; do
		sudo umount "$mnt"/$i
	done
	sudo mv "$mnt"/etc/resolv.conf.orig "$mnt"/etc/resolv.conf
	sudo umount "$mnt"
	sudo rmdir "$mnt"
}

$1

```
```

./script start # Start chroot
./script stop  # Stop the chroot and remove everything

```

---

### Post by ace214 on 2009-09-16
> **dentaku65 said:**
> Do you have intel as video card?

I do, and still am having this problem even after the update that supposedly fixed it for everyone else. Is it an intel issue?

---

### Post by indifference on 2009-09-16
@Eestlane and @VMC

From Arch I chrooted do ubuntu partition. I couldn't access to the net, so I've copyed the file /etc/resolv.conf from Arch.

I've executed a apt-get update && apt-get upgrade.

However the upgrade stoped with errors from some grub stuff.

I rebooted to ubuntu, and it booted with errors into a command prompt.
I've managed to complete the update, but the boot still shows errors and falls to a command line.

@dentaku65

Yes, it's an intel 855gm integrated graphics card.


I think the better solution is to wait for better days :)

Thanks to all,

Pedro Saraiva

---

### Post by Wise Ferret on 2009-09-16
I also have a black screen with radeon x1600 using the open-source radeon driver. I used the useful instructions above to update the system successfully, but it still boots only to a black screen. Woe is me.

---

### Post by freackout on 2009-09-16
> **indifference said:**
> Hello,

I've updated karmic last night and now I cant boot anymore. All I get is a black screen where nothing works, even the capslock key doesn't work.

I've try to boot in recovery mode but the issue is still present, so I cant do a thing...

My graphics card is an integrated intel 855gm.

Luckly for me, I dual boot with Arch...

Please help!

Thanks,

Pedro Saraiva

pmagic is live cd and you can mount all drives and change or save settings easily.

---

### Post by VMC on 2009-09-16
> **freackout said:**
> pmagic is live cd and you can mount all drives and change or save settings easily.

pmagic is a great tool. I have it attached to grub2 as a loop-back iso. I use gparted, FSArchiver, partclone, Clonzilla. And there all on pmagic!

---

### Post by handaxe on 2009-09-16
> **indifference said:**
> 
@dentaku65

Yes, it's an intel 855gm integrated graphics card.


I think the better solution is to wait for better days :)

Intel i915 driver users (such as for the 855gm chipset) might try putting ```
nomodeset
``` into the grub boot command (via the "e" function within grub).  There may be a KMS issue compounding recovery difficulties.

HA

---

### Post by Wise Ferret on 2009-09-16
The suggested nomodeset grub option did not do anything for me (radeon x1600 on 32 bit laptop), but I removed the vga=791 option so I could see the messages "behind" the black screen. This is what I got:

```
* Setting sensor limits [OK]
* Pulseaudio configured for per-user sessions
saned disables; edit /etc/default/saned
* enabling additional executable binary formats binfmt-support [OK]
FATAL: Module ppp_generic not found.
The SpeedTouch firmware did not load
* checking battery state...
/dev/sda
setting Advanced Power MAnagement level to 0xfe (254)
APM_leve   = 254
[OK]
[... irrelevant timidity loading messages]

Ubuntu karmic (development branch) ubuntu tty1

ubuntu login: _
```

I could login but not start x using startx (threw me back to tty). I have absolutely no idea what to make of it, unfortunately. Any ideas?

---

### Post by alphacrucis2 on 2009-09-16
> **Wise Ferret said:**
> I turned the modeset off as suggested (radeon on 32 bit laptop) and also removed the vga=791 option, so I could see the messages "behind" the black screen:

```
* Setting sensor limits [OK]
* Pulseaudio configured for per-user sessions
saned disables; edit /etc/default/saned
* enabling additional executable binary formats binfmt-support [OK]
FATAL: Module ppp_generic not found.
The SpeedTouch firmware did not load
* checking battery state...
/dev/sda
setting Advanced Power MAnagement level to 0xfe (254)
APM_leve   = 254
[OK]
[... irrelevant timidity loading messages]

Ubuntu karmic (development branch) ubuntu tty1

ubuntu login: _
```

I could login but not start x using startx (threw me back to tty). I have absolutely no idea what to make of it, unfortunately. Any ideas?

I am getting that too. From the cli I can bring the network up via dhclient eth0. At least then I can talk to the Ubu servers and hopefully get the fix :lolflag:

Edit. Some more info. When I do a startx I can see that it gets as far as starting to display the gnome panel but then it just terminates back to the cli. Only update that has come through since the breakage is to network-manager and related so I may have to wait until tomorrow.

---

### Post by Tux Aubrey on 2009-09-16
I've had the borked update issue on Xubuntu since yesterday - ending up at a tty with no network available.  Fortunately I was able to rollback to the previous install (in VBox).  

After four failed attempts to update, I did a 
```
sudo apt-get dist-upgrade
``` 
straight after updating/upgrading (ie. without a reboot).  That fixed just about everything (although gdm is now completely featureless except for the ability to log in  - no restart or session selection boxes)

---

### Post by Wise Ferret on 2009-09-16
> **alphacrucis2 said:**
> I am getting that too. From the cli I can bring the network up via dhclient eth0. At least then I can talk to the Ubu servers and hopefully get the fix :lolflag:

Can you tell us when it is fixed for you? I'm on wireless and cannot connect easily without gui, and using the chroot trick via livecd takes ages...

---

### Post by qwerty800 on 2009-09-16
I get this too, but I have a Nvidia Graphic card...

The only update abiable is about initscripts, and if I install il, it will remove:
```
root@ubuntu:/# sudo apt-get install initscripts
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xorg-docs-core nvidia-settings nvidia-185-libvdpau nvidia-185-kernel-source
  check tix tcl8.4 tk8.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support alsa-base bluez-cups brltty brltty-x11 checkbox checkbox-gtk
  console-setup cups cups-driver-gutenprint cupsys dmsetup foo2zjs foomatic-db
  foomatic-db-engine fuse-utils gdm gdm-guest-session ghostscript-cups
  gnome-mount gvfs-fuse hal hotkey-setup hpijs hplip hplip-cups
  indicator-applet-session indicator-session initramfs-tools kbd
  libcanberra-pulse linux-backports-modules-2.6.31-10-generic linux-generic
  linux-image-2.6.31-10-generic linux-image-2.6.31-5-generic
  linux-image-2.6.31-6-generic linux-image-2.6.31-7-generic
  linux-image-2.6.31-8-generic linux-image-2.6.31-9-generic
  linux-image-generic lvm2 media-player-info ntfs-3g openprinting-ppds
  pcmciautils pm-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 rhythmbox splix ubuntu-desktop udev usplash
  usplash-theme-ubuntu watershed wireless-crda xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following packages will be upgraded:
  initscripts
1 upgraded, 0 newly installed, 102 to remove and 0 not upgraded.
Need to get 72.7kB of archives.
After this operation, 654MB disk space will be freed.
Do you want to continue [Y/n]? 

```
Can anybody tell me what I am supposed to do I I have to kernel to boot on?? :lolflag:

---

### Post by alphacrucis2 on 2009-09-16
> **Wise Ferret said:**
> Can you tell us when it is fixed for you? I'm on wireless and cannot connect easily without gui, and using the chroot trick via livecd takes ages...

Weird! A small network-manager update seems to have sorted out the main problem. I'm back into gnome. Still have the udev symlink error messages on boot up.

---

### Post by Wise Ferret on 2009-09-16
Hooray, the update fixed that!

But the culprit was not Network Manager, but the new kid on the block: mountall.

---

### Post by VMC on 2009-09-16
> **alphacrucis2 said:**
> Weird! A small network-manager update seems to have sorted out the main problem. I'm back into gnome. Still have the udev symlink error messages on boot up.

Go [**here**]("http://ubuntuforums.org/showpost.php?p=7961543&postcount=27") and then to the mentioned LP post12 for why we still have it. It's by design?!?!

---

### Post by compat on 2009-09-17
i have an 'old' acer laptop (dmesg says 1410), with last kernel 2.6.31-10 (updated yesterday) 

i also get blank screen when booting and i have to do a hard reset pressing power button for secs. 
using kernel 2.6.31-9 (regular and recovery) drops to shell but in read-only mode, and i cant mount a thing.

so, appending 'nomodeset' and removing quite and splash to grub kernel line in boot menu using 'e' lets me enter the messed system to my desktop! thnks thnks thnks because i don't have usb boot, or cdrom (broken), so i would have to prepare a pxe net boot again.

now when doing a apt-get dist-upgrade the crazy system wants to immolate itself, asking me to remove 1GB of packages, including critical ones, seems that it wants to remove everything on earth. using aptitude safe-upgrade avoids the apt ultimate harvest.

great move, at least i can join desktop with nomodeset but...

obviously, network manager is kind of broken but it's not critical (for me)

UPDATE: now i see apt-get dist-upgrade problem has been fixed but blank screen persists, it is triggered after a BIOS line warning that says 'please report it to gawds, aborting'. confirmed nomodeset skips blank screen here

---

### Post by clivejo on 2009-09-17
I too had a blank screen on boot, thank to snippets on this thread I was able to get the system to boot again.  I have listed the steps involved for anyone else with same blank screen problem.  

 1) On boot hold down "Shift" key to enter Grub menu. 
 2) Select the default menu item and press "e" to edit entry 
 3) Edit the following line "linux /boot/vmlinuz-2.6.31-10-generic root=UUID=a3324753-ba2f-4e9c-8476-6119c8f1e999 ro vga=792  quiet splash" 
 4) Remove the "vga=", "quiet" and "splash" 
 5) Press "CTRL + x" to boot the edited commands. 
 6) The system should boot in text mode and drop into graphical logon manager.   

Thanks for the help in previous posts.

---

### Post by ohiomoto on 2009-09-17
FWIW...

I just did a UNR dual boot on a Acer Apsire AS1400 with MS Shista on it.  It worked great on the USB but after installing, UNR would hang during boot.  It turned out that the SATA driver in the BIOS was set to AHCI and my UNR install didn't like it.  I switched the  SATA setting in the BOIS to IDE and all was good...until my wife went to use Shista.  It didn't like the IDE setting.  I re-installed Shista with the SATA BIOS set to IDE and all is good.

I hope this helps (someone).

---

### Post by bacardiandwatermelon on 2009-09-19
> **handaxe said:**
> Intel i915 driver users (such as for the 855gm chipset) might try putting ```
nomodeset
``` into the grub boot command (via the "e" function within grub).  There may be a KMS issue compounding recovery difficulties.

HA


yessss!! your a legend.. Curse this i855 chipset.. At least i'm back now woohoo, things were so much easier on my ati box :-)

---

### Post by dxxvi on 2009-09-19
I installed karmic alpha 6 on ThinkPad SL500 (Intel 4500 graphic card). After an upgrade on Sat Sep 19, I got a blank screen. Removing "quite splash" from the boot command didn't help. Haven't tried "nomodeset" yet (thought it was for intel i915 driver users).

Does anybody succeed with this kind of laptop and karmic alpha 6?

Thank you.

---

### Post by bacardiandwatermelon on 2009-09-19
Just as an idea, rather than editing your grub every boot to put in the nomodeset, you could just do what I did and edit..
```
gksudo gedit /etc/grub.d/40_custom
```And put something like this in there.. :-)
```
menuentry "Ubuntu, Linux 2.6.31-10-generic (nomodeset)" {
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1da30df0-9bc3-4089-9919-6ad9c0070599
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=1da30df0-9bc3-4089-9919-6ad9c0070599 ro   quiet splash nomodeset
    initrd    /boot/initrd.img-2.6.31-10-generic
}
```Yours will probably be different from mine though, so copy it from..
```
gksudo gedit /boot/grub/grub.cfg
```And finally you will have to run..
```
sudo update-grub
```Hopefully the fix comes sooner rather than later :-)

---

### Post by lithorus on 2009-09-19
> **bacardiandwatermelon said:**
> Just as an idea, rather than editing your grub every boot to put in the nomodeset, you could just do what I did and edit..
```
gksudo gedit /etc/grub.d/40_custom
```And put something like this in there.. :-)
```
menuentry "Ubuntu, Linux 2.6.31-10-generic (nomodeset)" {
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1da30df0-9bc3-4089-9919-6ad9c0070599
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=1da30df0-9bc3-4089-9919-6ad9c0070599 ro   quiet splash nomodeset
    initrd    /boot/initrd.img-2.6.31-10-generic
}
```Yours will probably be different from mine though, so copy it from..
```
gksudo gedit /boot/grub/grub.cfg
```And finally you will have to run..
```
sudo update-grub
```Hopefully the fix comes sooner rather than later :-)
Even easier. Open /etc/default/grub and edit the GRUB_CMDLINE_LINUX_DEFAULT option.

---

### Post by indifference on 2009-09-20
This weekend I've installed a fresh install of Karmic alpha 6. The issue is still there: a black screen where nothing can be done. Using the nomodeset kernel option falls to a command prompt, and when I do startx it falls back to it with errors.

What kind of information do I need to fill a bug?

Thanks,

Pedro Saraiva

---

### Post by fooman on 2009-09-20
removing vga=, quiet, and splash from grub's boot line worked for me.

it ain't a pretty boot....but it works.  :)

---

### Post by handaxe on 2009-09-20
> **indifference said:**
> This weekend I've installed a fresh install of Karmic alpha 6. The issue is still there: a black screen where nothing can be done. Using the nomodeset kernel option falls to a command prompt, and when I do startx it falls back to it with errors.

What kind of information do I need to fill a bug?

Thanks,

Pedro Saraiva

I assume you updated after installing the alpha-6? As I am unsure where the alpha-6 is in the development of the fixes for the problem (and the intel frame-buffer KMS issue remains unresolved AFAIK), try the following as the command prompt:
```
sudo start dbus
sudo start hal
sudo start network manager
sudo start gdm
```If no luck then search the bug reports first as the chance is that your issue is already reported (this is NB). One is now meant to use from the CLI ubuntu-bugs <programme-name> to bug report. Help on bugs available on launchpad and at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs).

HA

---

### Post by dxxvi on 2009-09-21
Just an update for those who wanna try Karmic (iso image on Sep 21) on a ThinkPad SL500 (intel 4500 graphic card):

I installed a new Karmic on this laptop. In the first run after the installation, everything is fine except no boot menu entry for Windows 7 enterprise (the 90-day trial version). No update on any package at all (only deleted some packages like yelp, gnome-games-common, brltty, xsane, evolution, empathy, mono, evince ...). Run sudo update-grub2 to make the Windows 7 appear in the boot menu. Installed the mac4lin icons and gtk theme. Rebooted.

In the second run: black screen. Ctrl + Alt + Backspace then Ctrl + Alt + Del and the machine rebooted.

In the third run: removed "quiet splash" and added "nomodeset", no graphic login at all, and saw a lot of something like errors.

---

### Post by indifference on 2009-09-21
Hello,

No I didn't update after install alpha-6 because I don't have a wired access. I'll try to do that later tonight.

I've tried the commands you gave me, and insted of starting gdm i've done a startx and the desktop almost appeared, it showed the wallpaper and the panels, but it fail to the command line after a while.

XServer stoped and showed an error as "i810 module not found". Seems that my graphics card is not properly managed.

> **handaxe said:**
> I assume you updated after installing the alpha-6? As I am unsure where the alpha-6 is in the development of the fixes for the problem (and the intel frame-buffer KMS issue remains unresolved AFAIK), try the following as the command prompt:
```
sudo start dbus
sudo start hal
sudo start network manager
sudo start gdm
```If no luck then search the bug reports first as the chance is that your issue is already reported (this is NB). One is now meant to use from the CLI ubuntu-bugs <programme-name> to bug report. Help on bugs available on launchpad and at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs).

HA

---

### Post by Matt Behrens on 2009-09-22
I think this is the bug in question

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/431812](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/431812)

I seem particularly unlucky on my Eee 1000HEB; when I get the black screen, my screen is still off after I power off and on again.  But the boot seems to work properly at that point and I can see the screen again by using the hard brightness keys.

---

### Post by fianor on 2009-09-22
I've no idea if this is where I should be posting this, but this thread solved my blank-screen problem with ubuntu 9.04 with the 2.6.31 kernel.
I have an Intel GMA 4500M processor on my acer aspire laptop.

**Problem**: boots, but ends up with blank screen. linux login sounds DO play in the background before and after i type in my login info.

**Solution**: removed quiet and splash from the specified grub boot line as mentioned in previous posts here.

Thanks a lot.

P.S. : apparmor fails to load, i noticed, but apparently that's just because it's not been updated for the new kernel, but that's off topic.

---

### Post by indifference on 2009-09-22
I guessing it's not the same issue I'm getting, because my system completly freezes when the black screens comes in, the caps lock light doesn't work, Alt-SysRq REISUB doesn't work, etc...

Trying to remove the splash and quiet kernel options doesn't help neither.

Booting with the nomodeset option falls to a command prompt, and when I do startx it shows an error "module i810 not found". Doing lsmod I can see that the module i955 (and i810) is loaded..

---

### Post by handaxe on 2009-09-23
> **indifference said:**
> I guessing it's not the same issue I'm getting, because my system completly freezes when the black screens comes in, the caps lock light doesn't work, Alt-SysRq REISUB doesn't work, etc...

Trying to remove the splash and quiet kernel options doesn't help neither.

Booting with the nomodeset option falls to a command prompt, and when I do startx it shows an error "module i810 not found". Doing lsmod I can see that the module i955 (and i810) is loaded..

Hmm, from earlier in the thread ... you have an 855gm, as do I.  You have i955 module loaded, as do I and you have the i810 module loaded as I do NOT.... so,

as the cli and before you do "startx", try ```
sudo rmmod i810
``` and then try startx..  Trying to see if you have a module conflict.

HA

---

