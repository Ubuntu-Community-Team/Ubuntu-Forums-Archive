---
title: "Installing 10.10 via Wubi crashes on &quot;recalculating splines&quot;"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by TomSerato on 2011-02-15
Let me preface this by saying that i am entirely new to Linux...

I have tried 2 fresh installs of Ubuntu 10.10 from Wubi. After the initial Windows install I reboot, select Ubuntu, get the countdown (at which point I have to hit ESC for options or it will just hang), then select the 'ACPI Workrounds' option. I get to the purple splash screen with preview slide show and Ubuntu begins finalizing the install. The progress bar goes all he way to the end, reading "recalculating splines", but then my system reboots. 

When I chose Ubuntu again I have the standard option and the 'safe mode' option. Neither get me back to the purple splash screen, but instead just hang. Safe mode will begin to load, then hang on [   1.771083] ata: SATA link up 1.5 Gbps...

I have tried to edit the Grub for both of these options. Per some other posted suggestion I tried adding (variously) 'nomodeset', 'noapic', 'nolapic' and have deleted 'quiet splash' [I don't recall every combination of commands I tried, so if there is a specific set please let me know]. No matter what I try here, as soon as I hit CTRL-X, it goes to a screen stating: "Booting command list". It just hangs on this screen and I can not type anything in. I am forced to pull the power cord to reboot. 

I am running an older laptop: Toshiba Satellite A135; Intel Celleron Processor and 2 gigs of RAM, Windows Vista Home Basic pre-installed

Any help would be appreciated.

PS: The only errors I could find in a Google search having to do with "splines" was in relation to Ooo.

---

### Post by TomSerato on 2011-02-15
[SIZE=2]Let me add an important point that I should have added originally. I can actually run Ubuntu 10.10 from a live CD. 

My system has a 32-bit version of Windows Vista installed, so I downloaded the 32-bit version of the 10.10 ISO and placed it in the same folder as Wubi.exe. I then burnt the .iso image to a CD. When I launch from CD I have to hit F6 and choose the 'NOMODESET' and the [/SIZE][SIZE=2][SIZE=2]'Noapic' and 'Nolapic' options. The CD will successfully boot and things run fine (except for my printer being recognized but not printing anything--separate issue I'm sure).[/SIZE]

Questions: 1) Even though I put the 32-bit iso in the same folder as Wubi.exe, might Wubi still be installing a 64-bit version? 
And might the above issues be caused by my system not being able to handle a 64-bit OS?

2) If so, is there a 32-bit version of Wubi?

3) I need to keep my Windows install for the time being. Would anyone expect the Wubi install issues to persist if I attempted to install from the Live CD using the "[/SIZE]Install Ubuntu alongside another operating system" [SIZE=2]option?[/SIZE]

[SIZE=2]4) Will installing from the Live CD introduce new problems because of the  "NOMODESET' and the [/SIZE][SIZE=2][SIZE=2]'Noapic' and 'Nolapic' options?[/SIZE][/SIZE]
[SIZE=2]And are these options a workaround to an issue with a permanent fix once Ubuntu is properly installed?[/SIZE]
[SIZE=2]
Thanks again.

[/SIZE]

---

### Post by bcbc on 2011-02-15
Try this link  [http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

It shows that the "Acpi workarounds" for wubi are: acpi=off noapic nolapic

So you would boot, select Ubuntu, hit 'e' on the first option, then change "quiet splash" to "nomodeset acpi=off noapic nolapic"

Then when you have booted either install the drivers you need, or make the boot options permanent through post 1 in that thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (ignore that it says "(Not for Wubi)" - it works the same after the initial install)

---

### Post by TomSerato on 2011-02-15
Thanks [bcbc]("http://ubuntuforums.org/member.php?u=946783")! I will try that when I get back to the laptop this evening.

Also, regarding the printer, Brother only offers a 64-bit version for Debian/Ubuntu. Will this work with the 32-bit version of 10.10?

The official Ubuntu documentation makes this somewhat ambiguous statement regarding 32-bit vs. 64-bit drivers: "Other platforms (like Windows) which also come in 32 and 64-bit flavours are experiencing significantly more problems especially due to a lack of 64-bit device drivers as incompatible user application. As Ubuntu is entirely open source, this is not the case as all hardware supported by Ubuntu works equally well in 32-bit and 64-bit environments. The same applies to open source user applications as well."

For what it's worth Ubuntu and OO Writer both recognize the printer as the default printer, and will send jobs to the queue, but nothing happens on the printer side.

---

### Post by bcbc on 2011-02-15
> **TomSerato said:**
> Thanks [bcbc]("http://ubuntuforums.org/member.php?u=946783")! I will try that when I get back to the laptop this evening.

Also, regarding the printer, Brother only offers a 64-bit version for Debian/Ubuntu. Will this work with the 32-bit version of 10.10?

The official Ubuntu documentation makes this somewhat ambiguous statement regarding 32-bit vs. 64-bit drivers: "Other platforms (like Windows) which also come in 32 and 64-bit flavours are experiencing significantly more problems especially due to a lack of 64-bit device drivers as incompatible user application. As Ubuntu is entirely open source, this is not the case as all hardware supported by Ubuntu works equally well in 32-bit and 64-bit environments. The same applies to open source user applications as well."

For what it's worth Ubuntu and OO Writer both recognize the printer as the default printer, and will send jobs to the queue, but nothing happens on the printer side.
I'm not big on printer setup under Ubuntu - I just know some printers aren't well supported. But you can't run 64-bit programs on 32-bit so you'll have to find a 32-bit version of the driver.

---

### Post by TomSerato on 2011-02-19
I am able to get in with the Wubi install by replacing 'quiet splash' with the following options: 'nomodeset acpi=off noapic nolapic'. I can also boot with acpi=ht instead of acpi=off, but the system will often freeze at random. 

I then enter gksudo gedit /etc/default/gruband edit the grub file, save, and use the 
sudo update-grub [FONT=monospace]command to make the changes permanent(?).

However, when I restart, my system reverts back to the same issue. I have to remake the changes in the Wubi boot grub menu. Once logged in, I check the grub file again from the command line and the previous changes are there.

I have to conclude, then, that the Wubi grub file I'm changing at bootup is **different** from the Ubuntu grub file I'm changing, once logged in, through the command line. If this is the case, can I edit the Wubi grub file directly? Is it located somewhere in Windows?  

[/FONT]

---

### Post by bcbc on 2011-02-19
what's the output of:
```
cat /etc/default/grub
cat /boot/grub/grub.cfg
```

---

### Post by TomSerato on 2011-02-19
tom@ubuntu:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset acpi=off noapic nolapic"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
tom@ubuntu:~$ ^C
tom@ubuntu:~$ ^C
tom@ubuntu:~$ 

_____________________________________________________________________


tom@ubuntu:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d8c8fef9c8fed52a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   nomodeset acpi=off noapic nolapic
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d8c8fef9c8fed52a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d8c8fef9c8fed52a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   nomodeset acpi=off noapic nolapic
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d8c8fef9c8fed52a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d8c8fef9c8fed52a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
tom@ubuntu:~$

---

### Post by bcbc on 2011-02-19
That looks good. Which makes it puzzling that you wouldn't see that at bootup. I can't think of a good reason but why don't you post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results - maybe something will show up.

Also, if you can just boot it up again, hit 'e' on the first grub menu entry and write down what you see - that might provide some clues.

---

### Post by TomSerato on 2011-02-19
Well, this is interesting. I just rebooted again for the heck of it and a second set of Ubuntu boot options appeared. I now have regular and recovery modes for the .22 and .25 kernels (I think those numbers represent kernel versions?). I selected  the .25 regular Ubuntu option and... it worked.

The last time I started the computer was after the battery had died. I believe I made those final changes prior to this, but perhaps not. Maybe the way the computer shut down had something to do with it, thogh I don't know why that would be be. 

PS: Is there a laptop battery status indicator for Ubuntu?

---

### Post by bcbc on 2011-02-20
The problem is you're booting with acpi off - so running on battery is not a good idea.

I think you need to check if there is a BIOS update available for your computer, so that you don't need to supply those boot overrides in the first place.

---

### Post by TomSerato on 2011-02-25
I did update to the latest BIOS before installing. I'll experiment some more with the apci=ht option some more. Thanks.

---

