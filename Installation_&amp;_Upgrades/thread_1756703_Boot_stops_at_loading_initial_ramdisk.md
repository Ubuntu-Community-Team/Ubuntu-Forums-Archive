---
title: "Boot stops at loading initial ramdisk"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Luc484 on 2011-05-12
Hi! I recently upgraded to Ubuntu 11.04. Unfortunately I still can't boot the new kernel 2.6.38, I'm still using the old 2.6.35.

The new version stops after writing:

Loading initial ramdisk...

and the screen is completely screwed up. I tried to look in /var/log/messages but the log is not created, it is not there.

Anything I can do to investigate further?
Thanks!

---

### Post by drs305 on 2011-05-12
Does it freeze at the initramfs screen? If so:

You could run the boot info script. It's possible that a path problem with Grub2 is causing the problem. To be honest though, the chances are much greater that it is a problem with the initrd image or kernel. 

If you want to run the boot info script, the link for the download is in my signature line (BIS). We would want to see the contents of RESULTS.txt

Another thing you could try would be to boot the Natty LiveCD and chroot into your Ubuntu partition and reinstall the kernel or update the initrd.img

If Natty was working correctly on the LiveCD (i.e. no hardware issues), experience says that it is often faster to reinstall the OS than troubleshoot the problem. But that's up to you of course.

If it continues, after initramfs, you could try adding "nomodeset" to the end of the linux line in the grub menu. Press 'e' to edit the menuentry, then add **nomodeset** to the end of the 'linux' line and CTRL-x to boot. Add your video driver if it works.

---

### Post by Luc484 on 2011-05-12
Thanks for your help!

I run the script, and this is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   316,418,047   313,344,000   7 HPFS/NTFS
/dev/sda3         316,418,048   523,449,297   207,031,250   7 HPFS/NTFS
/dev/sda4         523,450,366   625,141,759   101,691,394   5 Extended
/dev/sda5         523,450,368   531,261,439     7,811,072  82 Linux swap / Solaris
/dev/sda6         531,263,488   625,141,759    93,878,272  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EC0244B802448A12                       ntfs       WinRE                         
/dev/sda2        BE2C46CD2C46807F                       ntfs       Vista                         
/dev/sda3        58fe66bf-1ca6-4536-9782-6cb6515bed0d   ext4       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e1ff528f-ec89-479d-9a4a-6e9d5458d36b   swap                                     
/dev/sda6        4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root BE2C46CD2C46807F
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4635bd6c-8c24-4f5f-b2f6-02c1bd5d5ec8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1ff528f-ec89-479d-9a4a-6e9d5458d36b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 294.2GB: boot/grub/core.img
 278.6GB: boot/grub/grub.cfg
 304.7GB: boot/initrd.img-2.6.35-28-generic
 308.0GB: boot/initrd.img-2.6.38-8-generic
 315.5GB: boot/initrd.img-2.6.38-8-generic-pae
 294.3GB: boot/vmlinuz-2.6.35-28-generic
 307.6GB: boot/vmlinuz-2.6.38-8-generic
 276.7GB: boot/vmlinuz-2.6.38-8-generic-pae
 308.0GB: initrd.img
 307.6GB: vmlinuz
```

Is using a CD the same as using a USB? I created a USB pendrive with Ubuntu 11.04, but unfortunately I get absolutely nothing on the screen. I succeeded booting 10.10 with the same USB pendrive and system.

As for the reinstalling the system I don't know. This is the system I work with. It would take much time to reconfigure it correctly. Moreover it would be really interesting to fix it to learn something useful.

Thanks for your assistance!

---

### Post by drs305 on 2011-05-12
I don't see any problems with your files. You could try booting from the grub prompt (press 'c' at the Grub menu). I don't think this is the issue but if you get an error message it might reveal something. In the example, I didn't use the PAE kernel - I'm assuming -pae is the default so I thought we'd try the other one.

You should be able to use TAB completion to help write out the kernel and initrd filenames:
```

set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod (hd0,6)/boot/grub/linux.mod # May report already loaded
linux (hd0,6)/boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 ro nomodeset
initrd (hd0,6)/boot/initrd.img-2.6.38-8-generic
boot
```

You said you tried a pendrive. The black screen - was it completely blank or was there a blinking cursor in the top left part of the screen? If there was, it's probably a video driver issue. Using 'nomodeset' as above should allow you to boot, after which you would need to install your video card's driver.

---

### Post by Luc484 on 2011-05-12
Booted correctly now! I'm logged in the system with the new kernel! :-)
Maybe a mistake with the grub configuration?

Anyway, when I logged in a message stated that my hardware couldn't support Unity. I read about this message somewhere. My system can support Unity, it was running just fine before. So maybe there's still something wrong... maybe with the kernel?

I currently have some other issues with the new 11.04, I suppose with the ATI drivers. Maybe something related to this again?

Thanks again for your help!

---

### Post by drs305 on 2011-05-12
> **Luc484 said:**
> I currently have some other issues with the new 11.04, I suppose with the ATI drivers. Maybe something related to this again?


The message was probably generated because you used the 'nomodeset' option (if you did), which disables a lot of drivers. Some are needed by Unity.

If you haven't already, try to install the ATI drivers. 

The way you booted from the grub prompt is non-persistent so you need to make the changes permanent. First, run the following two commands to help ensure things are as they should be:
```
sudo grub-install /dev/sda  # Do not include the partition number
sudo update-grub

```

Hopefully that will be all that is required. Remember that you booted the non-pae kernel, but the pae kernel may be the default Grub entry and it may be that kernel specifically that gave you the problem.

If it fails to boot the next time, reboot via the grub prompt as before (if you installed the video driver you can omit 'nomodeset'). You will probably have to purge and reinstall grub. It's pretty simple from the command line of a running (non-LiveCD) system. Let us know if that becomes necessary.

Once you are satisfied with the boot issue please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post. There is no rush to do so; you can change the status back if necessary.

---

### Post by Luc484 on 2011-05-12
I went through all your indications but the problem remains.
I reinstalled the drivers following [this]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch"). Then I gave the two commands you reported. Boot failed.
So I tried to purge grub and reinstall it. Boot failed again.

I've never been able to run Ubuntu 11.04 from the USB pendrive as well, but now I am. It is sufficient to set the nomodeset and the system boots up just fine.

Maybe I should set this nomodeset in my grub configuration? But I wouldn't be able to start Unity...

Thanks for your help!

---

### Post by Luc484 on 2011-05-13
I can confirm that the problem goes away when I set the nomodeset option. If I boot either the USB pendrive with Ubuntu 11.04 or my system without nomodeset I have nothing on the screen. If I set it, then the system is ok.
Any idea why and how I can fix this problem?
Thanks!

EDIT: By using the new information I noticed this problem seems quite frequent and the solution is simply to add that parameter to the grub configuration. Unfortunately it seems I have to give up Unity...

---

### Post by drs305 on 2011-05-13
> **Luc484 said:**
> I can confirm that the problem goes away when I set the nomodeset option. If I boot either the USB pendrive with Ubuntu 11.04 or my system without nomodeset I have nothing on the screen. If I set it, then the system is ok.
Any idea why and how I can fix this problem?
Thanks!

EDIT: By using the new information I noticed this problem seems quite frequent and the solution is simply to add that parameter to the grub configuration. Unfortunately it seems I have to give up Unity...

Did you try to add the video card driver for your system via 'Additional Drivers'? It is a pretty simple method if it detects your video card and can find a suitable driver. You can start the 'Additional Drivers' applet by clicking the 'home' button (the Ubuntu symbol at the top left of the panel) and typing 'Driver'. It should display the 'Additional Drivers' icon.

---

### Post by Luc484 on 2011-05-13
Do you mean the proprietary ATI drivers? Those were working with 10.10 but now the installation fails. Anyway I switched back to the opensource drivers even with 10.10 because I noticed better performance.

Is it mandatory to use the proprietary drivers to use Unity?

---

### Post by drs305 on 2011-05-13
> **Luc484 said:**
> Do you mean the proprietary ATI drivers? Those were working with 10.10 but now the installation fails. Anyway I switched back to the opensource drivers even with 10.10 because I noticed better performance.

Is it mandatory to use the proprietary drivers to use Unity?

I'm not familiar with the ATI drivers but I know that many users with the Nvidia cards install the appropriate proprietary driver and then can remove the 'nomodeset' option.

---

### Post by Luc484 on 2011-05-14
The last time I tried I had many troubles with 11.04. Before I try again, do you know why it is necessary to remove nomodeset to get Unity? Or, do you know why proprietary drivers are needed to get Unity?

If I boot with kernel 2.6.35 I can use Unity without any problems, without the nomodeset parameter and without proprietary drivers. So I'm not understanding the situation. Do you have any idea?

Thanks again for your help!

---

### Post by drs305 on 2011-05-14
> **Luc484 said:**
> The last time I tried I had many troubles with 11.04. Before I try again, do you know why it is necessary to remove nomodeset to get Unity? Or, do you know why proprietary drivers are needed to get Unity?

No I don't. And I am not sure they are required, especially if you didn't need them previously. I think since you can now boot, even though you don't get the desired result, the best course would be to open a new thread.

Many users won't start reading threads with many replies, and since your issue is now more video and Unity related a new thread with a more appropriate title might draw better responses than those I can provide.

---

### Post by Luc484 on 2011-05-14
I understand. You are right. Marking this as solved.

---

### Post by Neill_R on 2011-12-02
This is to affirm that my PC developed a similar fault today. Ubuntu 2.6.38-13 will not boot a prior release 2.6.38.12 is still there and will let me boot up. The PC does have an Nvidia VGA graphics card but no additional drivers are installed on this older working version. 

My question is that since I have it working on a previous kernel How can i remove the new kernel and go back to this working system. Where is the best guide to show me how to do that please? I have a RESULTS.txt file if you need to see it.

I was in the middle and nearly at what i hoped was the end of configuring this PC to my requirements, so I am loathed reinstall the OS just to get rid of this troublesome kernel (38-13)

---

### Post by drs305 on 2011-12-02
> **Neill_R said:**
> My question is that since I have it working on a previous kernel How can i remove the new kernel and go back to this working system. Where is the best guide to show me how to do that please? I have a RESULTS.txt file if you need to see it.


If you want to remove the kernel, boot the working kernel, then install ubuntu-tweak. It's a great app that can do a variety of tasks. You can visit a thread about how to remove older kernels and install ubuntu-tweak:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by Neill_R on 2011-12-02
I have a similar problem but I can  boot into the previous kernel Can I simply using, synaptic manager, remove the current 'latest" kernel? What other thing might i have to consider? Will it do as I hope and reverse the uodate or is that way too much to hope for? Sorry failed to see your reply

I followed your threads advise [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462). However Ubuntu-tweak did not give me the option to remove 2.6.36-13 when i was using 2.6.38-12. However I removed them via synaptic Package Manager from System--->Administration Menu. 

I remove 

linux-headers-2.6.38-13
linux-headers-2.6.38-13-generic
linux-image-2.6.38-13

and ran 

sudo update-grub

to repair the grub menu

Thank you very much for helping me on this occasion. 

P.S. I am wondering if I should have "removed completely" as if and when I update again update manger does not download the file again. However if the version has moved on to say 14 this is not a problem as i would get new files anyhow.

---

### Post by drs305 on 2011-12-02
> **Neill_R said:**
> 
P.S. I am wondering if I should have "removed completely" as if and when I update again update manger does not download the file again. However if the version has moved on to say 14 this is not a problem as i would get new files anyhow.

I didn't include instructions how to 'lock' the current kernel as I hoped you wouldn't need to do it. Hopefully if a new kernel is downloaded, even if it's the one you previously had issues with, it will work.

If you get a 'nag' asking you to install the problem kernel you can lock the current kernel via Synaptic. Select the current good kernel in Synaptic (linux-image-<version>) then Package > Lock Version. 

See Posts 2 & 4 of the following thread for a bit more detail:
[http://ubuntuforums.org/showthread.php?t=1887588]("http://ubuntuforums.org/showthread.php?t=1887588")

---

### Post by kristjan109 on 2012-04-30
> **drs305 said:**
> The message was probably generated because you used the 'nomodeset' option (if you did), which disables a lot of drivers. Some are needed by Unity.
 
If you haven't already, try to install the ATI drivers. 
 
The way you booted from the grub prompt is non-persistent so you need to make the changes permanent. First, run the following two commands to help ensure things are as they should be:
```
sudo grub-install /dev/sda  # Do not include the partition number
sudo update-grub

```
 
Hopefully that will be all that is required. Remember that you booted the non-pae kernel, but the pae kernel may be the default Grub entry and it may be that kernel specifically that gave you the problem.
 
If it fails to boot the next time, reboot via the grub prompt as before (if you installed the video driver you can omit 'nomodeset'). You will probably have to purge and reinstall grub. It's pretty simple from the command line of a running (non-LiveCD) system. Let us know if that becomes necessary.
 
Once you are satisfied with the boot issue please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post. There is no rush to do so; you can change the status back if necessary.
 
I am having a similar boot issue with Ubuntu 11.10. It started after a recent upgrade via the Update Manager. If I boot in recovery mode, it stops after typing "Loading Initial RamDisk" then stops. In normal mode, it fails with the purple screen of death (PSOD). If I go back a couple of versions in the grub menu, I can get a boot but the video driver is not supported in that release.
 
I have attached the Boot Info summary file below. Does anyone see anything wrong with my BootInfo which would cause Grub to hang? Any suggestions? My Ubuntu is toast at the moment. :( 
 
Thanks for the great posts and suggestions!

---

