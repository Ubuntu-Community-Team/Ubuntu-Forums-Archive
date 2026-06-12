---
title: "USB-Install on Mac"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by ScherzkeCks on 2011-04-21
Hello all,

I am trying to install Ubuntu with a USB-Stick on my Mac. I know it is discouraged but I am a little out of options here without a working CD-Drive and my University requiring me to have Linux.

I also know that there have been many threads and I searched for them as you will see in the course of this thread. Also I want to apologize in advance if my language seems sometimes weird and not understandable I am not a native english speaker.

So here it comes chronological what I did so far because I think that is best for you to know what I already did so you can hopefully help me.

First things first I downloaded the current stable release of the alternate cd (as well as the normal cd when it comes to that, tried both with same results.)

Then I followed the instructions on the download side to make a Mac-USB stick. 
To make it short, that stick did never show up anywhere not with the Bootmenu from Mac nor with rEFIt.

So I searched some more and found this [Thread ]("http://ubuntuforums.org/showpost.php?p=7926629&postcount=7") in this Forum. That sounded promising so I downloaded those files and did what it said. 
I put the iso in the root of the stick and everything from that download also (unwrapped of course so I had an efi foldoer and subfolders)

It worked so far that now my Mac acknowledged the stick as bootable, loaded grub but it always exited with "You need to load the kernel first".

Next thing I tried was to open the image efi.img in /boot/grub/ on the liux.disc and copy that content (folders efi/boot/bootx64.efi) on the root of my stick. Now i only gut grub running but couldn't get it to load a config-file. The most probable cause for that is my stupidity but I am willing to learn ;) )

Oh well I thought why not try something on you own, so i did. I created my own image that combined everything from that download with the linux-disc files. dd'd that onto my stick and run that. You guess right, nothing really happened. 

Then i changed the grub.cfg from that download, actually I simply replaced it with the one in the boot/grub/ folder normally found on the install-disc.
Now things get interesting, it does start loading the kernel but exits pretty soon with a kernel-panic:

> No filesystem could mount root, tried: ext3, ext2, ext4, fuseblk
Kernel panic - not syncing: VFS : Unable to mount root fs on unknown-block(1,0)

I did some research on that and found out that there are basically two theories as to why this happens, one is the support of filesystem on the hard-drive, but as far as I understand (I might be wrong here) that is normally the case when upgrading the kernel.

The other theory is, that it has something to do with initrd.

And this is where I stand now, because some possible solutions I could try demand a running linux:
compile grub2 efi myself
compile the kernel myself

and changing something with initrd is a problem for me so far because I don't really understand what it is really doing, I know it is used to create a temporary filesystem for the install but I don't know what I could change there to make it work.

Oh, I also want to note I tried fakebios in the grub.cfg with no effect.
Also I want to point out that I tried both the alternate and normal install-disc.

I hope this gives you enough information to help me get this very interesting operatingsystem to work on my little machine.

Greetings

Stefan

PS.: here is my grub.cfg:
```

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Install in expert mode" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu.seed priority=low --
	initrd	/install/initrd.gz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
	initrd	/install/initrd.gz
}
menuentry "Rescue a broken system" {
	set gfxpayload=keep
	linux	/install/vmlinuz  rescue/enable=true --
	initrd	/install/initrd.gz
}

```


PPS.: I also already copied the whole boot directory from the root of the usbstick to the efi/boot just keeping the bootx64.efi from the download mentioned above

If you have any questions just ask :)

---

