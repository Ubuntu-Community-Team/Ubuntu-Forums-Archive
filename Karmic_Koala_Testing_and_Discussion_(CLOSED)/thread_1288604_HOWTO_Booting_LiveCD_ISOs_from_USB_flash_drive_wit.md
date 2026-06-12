---
title: "HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JustRon on 2009-10-11
[CENTER][SIZE=4]**HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2**[/SIZE]
[/CENTER]
 
[B][SIZE=3]Updates
[/SIZE][/B]2009-10-27 08:50 UTC:
Fixed Ubuntu menu entries

2009-10-26 00:15 UTC:
Because the Lua scripting support was dropped from Grub2 after an update I've split the tutorial in two parts. One shows the old way of auto detecting live systems with the help of Lua and the other new way is to manually edit the grub.cfg.

2009-10-22 21:10 UTC:
bootiso.lua: Added support for Tinycore LiveCDs

2009-10-21 18:40 UTC:
bootiso.lua: Slax LiveCDs are now supported and general code cleanup

**[SIZE=3]Introduction[/SIZE]**
In this tutorial you will prepare a USB flash drive to make it bootable. After you booted it it shows you a menu where you can choose which live system you want to boot.

So you might be interested in this tutorial if:
 
[LIST]
[*]You want to have multiple live systems on one USB flash drive
[*]In the future you want to create a new bootable live system just by copying the ISO file onto the drive and edit the grub.cfg
[*]You don't want to or can't use Distro specific LiveUSB creator tools
[*]You prefer a cleaner solution than the most LiveUSB creator tools which create several folders and files at the device root
[*]You  are feeling bored and want to see cool features of Grub2
[/LIST]
If you have a Grub2 version with Lua support you even don't need to manually edit the grub.cfg when you add new or remove live systems.

[SIZE=3]**System Requirements**[/SIZE]

[LIST]
[*]One USB flash drive
[*]A running Ubuntu 9.10 (Karmic Koala), either installed or from a Live System
[/LIST]

[SIZE=3]**Installation**[/SIZE]
**Warning:** If you have important data on your USB flash drive you might want to backup them, although no step of the tutorial should delete files.

**Please note:** This tutorial will use placeholders like “/dev/sdx” for the device name and “/media/USBFolderName” for the mounted directory name which must be replaced with the proper names of your plugged in USB flash drive. If you don't know them you can look under the File System tab from the System Monitor or execute the “mount” command in a terminal.

The first step is to install Grub2 on the USB flash drive. Be careful that you don't put a number behind the device name because we want to install Grub2 into the MBR of the device and not into a partition. Replace the placeholders and execute the following command in a terminal.

```
sudo grub-install --root-directory=/media/USBFolderName /dev/sdx
```After that you should see a new folder “boot” on your USB flash drive which contains another folder named “grub”. In the "boot" folder you create a new folder “isos”. In this folder you can put supported LiveCD ISOs to boot from.

The next part "Configuration" depends on your Grub2 version and if it does or doesn't support Lua scripting. Please go directly to the right part and ignore the other. The Ubuntu Grub2 versions will most likely have no Lua support but if you manually compile Grub2 with the Grub-extras you have. To check this you can look in the "boot/grub" folder if the "lua.mod" file exist or boot Grub, press "c" and check if the "parser.lua" command exist.

[B][SIZE=3]Configuration (no Lua support)
[/SIZE][/B]Create a "grub.cfg" file in the "boot/grub" folder of your USB drive and add the matching menu entries. Perhaps you must also modify the path to your ISO file.

grml:
```
menuentry "grml" {
    set isofile="/boot/isos/grml.iso"

    loopback loop $isofile 
    linux (loop)/boot/grml/linux26 findiso=$isofile apm=power-off quiet boot=live nomce
    initrd (loop)/boot/grml/initrd.gz
}
```Parted Magic:
```
menuentry "Parted Magic" {
    set isofile="/boot/isos/pmagic.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}
```Slax:
```
menuentry "Slax" {
    set isofile="/boot/isos/slax.iso"

    loopback loop $isofile 
    linux (loop)/boot/vmlinuz from=$isofile ramdisk_size=6666 root=/dev/ram0 rw
    initrd (loop)/boot/initrd.gz
}
```Tinycore:
```
menuentry "Tinycore" {
    set isofile="/boot/isos/tinycore.iso"

    loopback loop $isofile 
    linux (loop)/boot/bzImage
    initrd (loop)/boot/tinycore.gz
}
```Ubuntu (since 9.10 Karmic Koala):
 ```
menuentry "Ubuntu" {
    set isofile="/boot/isos/ubuntu.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
```Ubuntu (before 9.10 Karmic Koala):
 ```
menuentry "Ubuntu" {
    set isofile="/boot/isos/ubuntu.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}
```**[SIZE=3]Configuration (with Lua support)[/SIZE]**
Create the following three files in the "boot/grub" folder of your USB drive.

grub.cfg
```
# Uncomment for a different ISO files search path
#set isofolder="/boot/isos"
#export isofolder

# Uncomment for a different live system language
#set isolangcode="us"
#export isolangcode

source /boot/grub/listisos.lua
```listisos.lua
```
#!lua

isofolder = grub.getenv ("isofolder")
if (isofolder == nil) then
  isofolder = "/boot/isos"
end

function enum_file (name)
  local title = string.match (name, "(.*)%.[iI][sS][oO]")

  if (title) then
    local source = "set isofile=" .. isofolder .. "/" .. name ..
      "\nsource /boot/grub/bootiso.lua"

    grub.add_menu (source, title)
  end
end

grub.enum_file (enum_file, isofolder)
```bootiso.lua
```
#!lua

-- Detects the live system type and boots it
function boot_iso (isofile, langcode)
  -- grml
  if (dir_exist ("(loop)/boot/grml")) then
    boot_linux (
      "(loop)/boot/grml/linux26", 
      "(loop)/boot/grml/initrd.gz",
      "findiso=" .. isofile .. " apm=power-off quiet boot=live nomce"
    )
  -- Parted Magic
  elseif (dir_exist ("(loop)/pmagic")) then
    boot_linux (
      "(loop)/pmagic/bzImage", 
      "(loop)/pmagic/initramfs",
      "iso_filename=" .. isofile .. 
        " edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw" .. 
        " sleep=10 loglevel=0 keymap=" .. langcode
    )
  -- Sidux
  elseif (dir_exist ("(loop)/sidux")) then
    boot_linux (
      find_file ("(loop)/boot", "vmlinuz%-.*%-sidux%-.*"), 
      find_file ("(loop)/boot", "initrd%.img%-.*%-sidux%-.*"),
      "fromiso=" .. isofile .. " boot=fll quiet"
    )
  -- Slax
  elseif (dir_exist ("(loop)/slax")) then
    boot_linux (
      "(loop)/boot/vmlinuz", 
      "(loop)/boot/initrd.gz",
      "from=" .. isofile .. " ramdisk_size=6666 root=/dev/ram0 rw"
    )
  -- Tinycore
  elseif (grub.file_exist ("(loop)/boot/tinycore.gz")) then
    boot_linux (
      "(loop)/boot/bzImage", 
      "(loop)/boot/tinycore.gz"
    )
  -- Ubuntu and Casper based Distros
  elseif (dir_exist ("(loop)/casper")) then
    boot_linux (
      "(loop)/casper/vmlinuz", 
      find_file ("(loop)/casper", "initrd%..z"),
      "boot=casper iso-scan/filename=" .. isofile .. 
        " quiet splash noprompt" .. 
        " keyb=" .. langcode .. 
        " debian-installer/language=" .. langcode .. 
        " console-setup/layoutcode?=" .. langcode .. 
        " --"
    )
  else
    print_error ("Unsupported ISO type")
  end
end

-- Help function to show an error
function print_error (msg)
  print ("Error: " .. msg)
  grub.run ("read")
end

-- Help function to search for a file
function find_file (folder, match)
  local filename

  local function enum_file (name)
    if (filename == nil) then
      filename = string.match (name, match)
    end
  end

  grub.enum_file (enum_file, folder)

  if (filename) then
    return folder .. "/" .. filename
  else
    return nil
  end
end

-- Help function to check if a directory exist
function dir_exist (dir)
  return (grub.run("test -d '" .. dir .. "'") == 0)
end

-- Boots a Linux live system
function boot_linux (linux, initrd, params)
  if (linux and grub.file_exist (linux)) then
    if (initrd and grub.file_exist (initrd)) then
      if (params) then
        grub.run ("linux " .. linux .. " " .. params)
      else
        grub.run ("linux " .. linux)
      end
      grub.run ("initrd " .. initrd)
    else
      print_error ("Booting Linux failed: cannot find initrd file '" .. initrd .. "'")
    end
  else
    print_error ("Booting Linux failed: cannot find linux file '" .. initrd .. "'")
  end
end

-- Mounts the iso file
function mount_iso (isofile)
  local result = false

  if (isofile == nil) then
    print_error ("variable 'isofile' is undefined")
  elseif (not grub.file_exist (isofile)) then
    print_error ("Cannot find isofile '" .. isofile .. "'")
  else
    local err_no, err_msg = grub.run ("loopback loop " .. isofile)
    if (err_no ~= 0) then
      print_error ("Cannot load ISO: " .. err_msg)
    else
      result = true
    end
  end

  return result
end


-- Getting the environment parameters
isofile = grub.getenv ("isofile")
langcode = grub.getenv ("isolangcode")
if (langcode == nil) then
  langcode = "us"
end

-- Mounting and booting the live system
if (mount_iso (isofile)) then
  boot_iso (isofile, langcode)
end
```**[SIZE=3]Supported LiveCDs[/SIZE]**
Sadly it is not possible to boot every LiveCD ISO out there. The most important thing is that the live system is able to boot from an ISO file. These live systems parse a special boot parameter (like fromiso or findiso) to find the ISO file. Furthermore if you are using the Lua variant only registered live systems in the bootiso.lua file can be booted. Currently the following live systems are supported:

[LIST]
[*]grml ([http://grml.org/](http://grml.org/))
[*]Parted Magic ([http://partedmagic.com/](http://partedmagic.com/))
[*]Sidux ([http://sidux.com/](http://sidux.com/))
[*]Slax ([http://www.slax.org/](http://www.slax.org/))
[*]Tinycore ([http://www.tinycorelinux.com/](http://www.tinycorelinux.com/))
[*]Ubuntu ([http://www.ubuntu.com/](http://www.ubuntu.com/))
[/LIST]

**[SIZE=3]Booting[/SIZE]**
Now after you have successfully completed every step and put at least one supported ISO file in the “isos” folder you should be able to boot from the USB flash drive and see a menu with your ISOs.
 
**[SIZE=3]License information[/SIZE]**
This tutorial and its scripts are public domain.


PS: I know that there is a Tutorials & Tips section in this forum but thought it would be better to post it under Karmic Testing until Karmic is final.

---

### Post by rex4u on 2009-10-11
Thanks...
Was looking for something like this.
Btw, is it possible to have Multi-OS DVD like of Windows...

Thanks again...:guitar:

Yes, I am a noob :)

---

### Post by JustRon on 2009-10-12
> **rex4u said:**
> Btw, is it possible to have Multi-OS DVD like of Windows...

I don't know this Windows Multi-OS DVD stuff but if you want to have multiple Linux live system on one bootable DVD then it should be doable. Maybe I could help if you give me more information.

---

### Post by LiquidMeson on 2009-10-12
Nice script! Very easy to setup, and saves a lot of time. Hope more distro's iso's will follow lead.

---

### Post by VMC on 2009-10-12
Maybe some screenshots would help sell this idea. I'm not sure the benefit over just installing an iso into your usb drive and adding a menu entry on your grub.cfg. Like so:
```
menuentry "loop-back-pmagic from USB (findiso = pmagic-4.6.iso)" {
  loopback loop (hd1,1)/pmagic-4.6.iso
  gfxpayload=1024x768
  linux (loop)/pmagic/bzImage findiso=/pmagic-4.6.iso root=/dev/ram0 noeject noprompt sleep=0 load_ramdisk=1 prompt_ramdisk=0 loglevel=0 keymap=us
  initrd (loop)/pmagic/initramfs
}
```

"pmagic-4.6.iso" is sitting on my usb drive.

---

### Post by JustRon on 2009-10-13
> **VMC said:**
> I'm not sure the benefit over just installing an iso into your usb drive and adding a menu entry on your grub.cfg.

The benefit is that you could skip the second step with editing the grub.cfg because the grub.cfg of my howto auto detects every live system ISO in one folder and gives you a grub menu to choose one.

PS: I've edited the introduction part of my first post to make things clearer.

---

### Post by Sarmacid on 2009-10-18
I'm trying this in Ubuntu 9.04 and was getting this error when trying to install grub2
```
grub-probe: error: cannot find a GRUB drive for /dev/sdc1.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

To fix it, I had to add the --recheck and --no-floppy(not completely sure if this one was necessary) flags to the install command like this```
sudo grub-install --recheck --no-floppy --root-directory=/media/USBFolderName /dev/sdx
```
After that it installed with no problems. But after adding your config files I'm getting the error in the attached file, any ideas?

---

### Post by shafin on 2009-10-18
Is there any way to add an windows vista setup DVD to the setup?

---

### Post by JustRon on 2009-10-18
> **Sarmacid said:**
> I'm trying this in Ubuntu 9.04 and was getting this error when trying to install grub2 ...

Are you using the Grub2 version from the jaunty repo? Because that version is too old and has no Lua scripting support.

---

### Post by Dullstar on 2009-10-18
...or you could just use UNetBootin.

---

### Post by psyke83 on 2009-10-18
> **Dullstar said:**
> ...or you could just use UNetBootin.

...or the USB Startup Disk Creator (included by default since Jaunty).

---

### Post by Sarmacid on 2009-10-19
> **JustRon said:**
> Are you using the Grub2 version from the jaunty repo? Because that version is too old and has no Lua scripting support.

Downloaded and compiled grub2 myself, so I'm guessing it's the latest or one of the latest versions.

---

### Post by BwackNinja on 2009-10-19
Pretty nice guide, now I won't have to reformat my flash drive every time I want a different/updated liveCD on there and its quick to switch.

---

### Post by VMC on 2009-10-19
> **Sarmacid said:**
> Downloaded and compiled grub2 myself, so I'm guessing it's the latest or one of the latest versions.

I'm curious why you didn't just use the repo version. Is there a benefit to compiling grub2 yourself. Did you modify the program somehow.

---

### Post by Sarmacid on 2009-10-19
> **VMC said:**
> I'm curious why you didn't just use the repo version. Is there a benefit to compiling grub2 yourself. Did you modify the program somehow.

Didn't modify anything. I didn't download from the repos because the package listed there is marked as a dummy package and compiling it wasn't a big deal, it was pretty easy.

---

### Post by JustRon on 2009-10-19
> **Sarmacid said:**
> Downloaded and compiled grub2 myself, so I'm guessing it's the latest or one of the latest versions.

Could you print the output from the following command:

```
grub-setup -V
```Additionally could you boot the drive, press "c" to get to the Grub command line and check with tab completion if the command "parser.lua" exist?

---

### Post by Sarmacid on 2009-10-19
```
$ grub-setup -V
grub-setup (GRUB) 1.96
```

```
grub> parser.lua
error: unknown command 'parser.lua'
```

When using my own menu entries I can get it to boot from isos, but seeing this now I'm confused. :|

---

### Post by JustRon on 2009-10-19
> **Sarmacid said:**
> ```
$ grub-setup -V
grub-setup (GRUB) 1.96
```

The Grub version 1.96 is too old and doesn't contain the Lua scripting language. This feature was added in version 1.97 (actually it is not yet final). On the official Grub2 wiki is a download link for the 1.97 Beta4 version that should work: [http://grub.enbug.org/](http://grub.enbug.org/)

---

### Post by Sarmacid on 2009-10-19
> **JustRon said:**
> The Grub version 1.96 is too old and doesn't contain the Lua scripting language. This feature was added in version 1.97 (actually it is not yet final). On the official Grub2 wiki is a download link for the 1.97 Beta4 version that should work: [http://grub.enbug.org/](http://grub.enbug.org/)

Thanks for the feedback. I think I'll wait till it goes stable before installing it. In the meantime my old fashioned menu will have to do.

---

### Post by pxwpxw on 2009-10-19
Slax might be worth adding to the list, small (200MB) and useful backup.
[http://www.slax.org/](http://www.slax.org/)
```

	linux (loop)/boot/vmlinuz from=/slax-6.1.2.iso ramdisk_size=6666 root=/dev/ram0 rw changes=slaxper.dat
      	initrd (loop)/boot/initrd.gz

```

---

### Post by JustRon on 2009-10-21
> **pxwpxw said:**
> Slax might be worth adding to the list.

The more the better. I've updated the bootiso.lua script in the first post.

---

### Post by Sarmacid on 2009-10-21
This is my menu.cfg for grub 1.96, feel free to add these to your post, but bear in mind that for Bactrack to work the files must be extracted from the iso and the casper folder must be at the root of the device.

```
menuentry "Linux Mint 7" {
 loopback loop /boot/isos/LinuxMint-7.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/LinuxMint-7.iso --
 initrd (loop)/casper/initrd.gz
}
menuentry "Ubuntu Live 9.04 32bit" {
 loopback loop /boot/isos/ubuntu9.04.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/ubuntu9.04.iso --
 initrd (loop)/casper/initrd.gz
}
menuentry "Tinycore" {
 loopback loop /boot/isos/tinycore_2.4.1.iso
 linux (loop)/boot/bzImage --
 initrd (loop)/boot/tinycore.gz
}
menuentry "BackTrack 4 Pre Release" {
    linux /boot/isos/bt4/boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317 --
    initrd /boot/isos/bt4/boot/initrd.gz
}
menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}
```

---

### Post by VMC on 2009-10-21
> **Sarmacid said:**
> This is my menu.cfg for grub 1.96, feel free to add these to your post, but bear in mind that for Bactrack to work the files must be extracted from the iso and the casper folder must be at the root of the device.What errors messages did you get when you discovered this out? Maybe that's the issue I have with Lubuntu and Gparted.

---

### Post by Sarmacid on 2009-10-22
I was getting the problem shown here [http://ubuntuforums.org/showthread.php?p=8141575#post8141575](http://ubuntuforums.org/showthread.php?p=8141575#post8141575)

But fortunately by some kind of miracle I found the solution after posting.

---

### Post by JustRon on 2009-10-22
I've updated my first post and added Tinycore to the supported live systems. The script also tries now to boot every Casper based live system (like Linux Mint) even if they doesn't support the iso-from parameter and won't boot. Sadly I couldn't boot Linux Mint because it doesn't recognize my USB drive but it may work for someone else. As far as I know BackTrack doesn't support any iso-from parameter and so I won't support it.

> **VMC said:**
> Maybe that's the issue I have with Lubuntu and Gparted.

Correct me if I'm wrong but neither BackTrack, GParted nor Lubuntu supports an iso-from parameter (or similar) and therefore cannot booted directly from an ISO. So it is likely that this is your issue. But this is no bug it is just a missing feature.

You have two possibilities to boot such a live system directly from an ISO. You must either edit the init script in the initrd file to search for an ISO (this [link]("http://gparted-forum.surf4.info/viewtopic.php?pid=21218#p21218") that you have posted in another thread explains how) which is quite laborious, or you must make a feature request and hope it gets implemented in the next version.

---

### Post by desht on 2009-10-23
Just tried this, and it's not working for me :(

I'm using grub 1.97 beta4 as supplied with the Karmic RC, and followed all the instructions.  But when I boot from the USB drive, I'm just presented with the grub-1.97~beta4 banner, and a "sh:grub> " prompt.

There is no "parser.lua" command built into this grub - at least, running "parser.lua" just gives me "error: unknown command `parser.lua'".

Am I missing something basic here?  I thought grub 1.97b4 had lua built in?

Update: also tried it with grub 1.97 beta4 built from source downloaded from grub.enbug.org - same deal, no lua!  What's going on here, is there some special version of grub needed?

---

### Post by noiv on 2009-10-23
I'm wondering if it is possible to make a lua script for OpenSolaris. This is the start entry from the former grub on my machine.
```
title OpenSolaris 2008.11 snv_101b_rc2 X86
findroot (pool_rpool,2,a)
splashimage /boot/solaris.xpm
foreground d25f00
background 115d93
bootfs rpool/ROOT/opensolaris
kernel$ /platform/i86pc/kernel/$ISADIR/unix -B $ZFS-BOOTFS,console=graphics
module$ /platform/i86pc/$ISADIR/boot_archive
```

---

### Post by JustRon on 2009-10-23
> **desht said:**
> Just tried this, and it's not working for me :(

I'm sorry but it looks like Ubuntu and Grub2 has dropped the support for Lua after an update and so my tutorial doesn't work anymore. Thats probably because of [this decision]("http://lists.gnu.org/archive/html/grub-devel/2009-09/msg00424.html") from a Grub2 maintainer. Unfortunately I don't know a easy way to get a Grub version with Lua support.

---

### Post by lprazdnik on 2009-10-25
Hi. I am new to this forum and I tried the steps, however when I plug in the USB flash drive into my netbook, I only get the grub prompt. I created all three files that were required. I also coppied the ubuntu9.1-desktop-i386.iso to the isos folder. Am I doing anything wrong? thanks.

---

### Post by JustRon on 2009-10-25
> **lprazdnik said:**
> Hi. I am new to this forum and I tried the steps, however when I plug in the USB flash drive into my netbook, I only get the grub prompt.

As I've noted one post above yours my tutorial doesn't worked anymore after a Grub update. This is because Lua was dropped from the default Grub2. But I've updated my first post to show how it is still possible except the auto detection of live systems.

> **Sarmacid said:**
> Thanks for the feedback. I think I'll wait till it goes stable before installing it. In the meantime my old fashioned menu will have to do.

After all Grub 1.97 went [final]("http://lists.gnu.org/archive/html/grub-devel/2009-10/msg00373.html").

---

### Post by lprazdnik on 2009-10-25
Ok here's what I did. I recreated the grub.cfg file and pasted the ubuntu configuration. Then I deleted both of the .lua files since I asume they're no longer required. After that I went into the isos directory, and renamed the ubuntu9.1 image to ubuntu.iso. When I booted off the USB flash drive, it gave me a menu. However when I pressed enter, since I only have one usb image, it just said something like, press a key to continue. Then it returned me back to the same menu. Am I missing anything else here? Do you think I need a menu.lst file? The post doesn't mention it though. or maybe I shouldn't rename the ubuntu file. Thanks for all the help!

---

### Post by JustRon on 2009-10-26
> **lprazdnik said:**
> Am I missing anything else here? Do you think I need a menu.lst file? The post doesn't mention it though. or maybe I shouldn't rename the ubuntu file. Thanks for all the help!

As far as I can tell, you have done everything right. A menu.lst file is not needed because Grub2 uses the grub.cfg file instead and the renaming of the ISO file is also not a problem. Does it really prompts you just the "press a key to continue" text or is there also an error text like "error: file not found" or "error: you need to load the kernel first"? You could also test which command fails if you press "c" when you see the Grub menu to go to the command mode and then execute the commands that are inside the menuentry part.

---

### Post by lprazdnik on 2009-10-26
yup sorry you're right. it says command not found (loop)/casper/initrd

---

### Post by JustRon on 2009-10-27
> **lprazdnik said:**
> yup sorry you're right. it says command not found (loop)/casper/initrd

:oops: Whoops! I'm sorry the Ubuntu menu entries were wrong. They must of course look like this:

```
menuentry "Ubuntu" {
    set isofile="/boot/isos/ubuntu.iso"
 
    loopback loop $isofile 
    **linux** (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    **initrd** (loop)/casper/initrd.lz
}
```

---

### Post by lprazdnik on 2009-10-27
It works! Thanks! This is a much better alternative than to make a startup disk for each distro.

---

### Post by lprazdnik on 2009-10-27
Ok I have a bit of a problem. Usually, when I boot off a live cd, I press f5 to get to the accessibility menu, and enable the features. However the usb version doesn't do anything when I press f5. I'm sure I can find a way around it all but does anyone know of agood solution to fixing this? Other than that, the usb boots up fine. Thanks!

---

### Post by Sarmacid on 2009-10-27
> **lprazdnik said:**
> Ok I have a bit of a problem. Usually, when I boot off a live cd, I press f5 to get to the accessibility menu, and enable the features. However the usb version doesn't do anything when I press f5. I'm sure I can find a way around it all but does anyone know of agood solution to fixing this? Other than that, the usb boots up fine. Thanks!

In the menu, go to System -> Preferences -> Assistive technologies

---

### Post by lprazdnik on 2009-10-28
Yeah but it would be helpful if orca would start automatically, since I need speech feedback. I mean usually when ubuntu would load, I would just press alt f2, type orca and press enter. Then I would go through the configuration. The problem is after the configuration I need to log out and back in again. When I do that, since the 9.1 release, orca doesn't speak at all. So that's why I found it helpful to turn it on at the boot prompt. I don't know if this will be resolved after the 9.1 official release.

---

