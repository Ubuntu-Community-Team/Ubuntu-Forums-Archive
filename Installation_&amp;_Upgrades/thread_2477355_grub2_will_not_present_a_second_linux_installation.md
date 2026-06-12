---
title: "grub2 will not present a second linux installation"
date: 2022-07-22
forum: Installation &amp; Upgrades
---

### Post by francois.e on 2022-07-22
Grub2 will not present a second linux installation in the grub2 menu entry at bootup. I have installed kubuntu as a first choice and porteus as a second choice. Kubuntu is on /dev/sda1 and porteus on /dev/sda5. Porteus is booting from the iso file.

I have an old laptop a MSI 340, which is 64 bit capable. As it is rather slow compared to new linux boxes I have installed kubuntu which is considered to do well on old machines.

Here are my /etc/default/grub and /etc/grub.d/40_custom files.

grub
```

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DEFAULT=4  #4 pour 40_custom première entrée de custom_40

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX=""

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
GRUB_SAVEDEFAULT=true

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx"
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper
# modes only.  Entries specified as foreground/background.
GRUB_COLOR_NORMAL="light-gray/black"
GRUB_COLOR_HIGHLIGHT="green/black"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
GRUB_BACKGROUND="/usr/share/grub/background.png"
GRUB_THEME="/boot/grub/themes/Manjaro-Default/theme.txt"


# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

```

40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# ajout fl en dessous

# path to the partition holding ISO images (using UUID)
probe -u $root --set=rootuuid
set imgdevpath="/dev/disk/by-uuid/$rootuuid"



menuentry "Porteus50
insmod ext2
set root=(hd1,1)
set isofile="/isos/Porteus-XFCE-v5.0-x86_64.iso"
search --no-floppy --file --set=root $isofile
loopback loop $isofile
linux (loop)/boot/syslinux/vmlinuz from=$isofile changes=/50_porteus login=root extramod=UUID:67ccab9a-9ae9-4021-90b1-ef18d143711a/50_porteus/xfce extramod=UUID:67ccab9a-9ae9-4021-90b1-ef18d143711a/64_V40/porteus/modules
initrd (loop)/boot/syslinux/initrd.xz
}


```

What can I do to get in addition to the grub entry for kubuntu the grub entry for porteus?

Thanks a lot.

---

### Post by tea for one on 2022-07-22
```
menuentry "Porteus50[COLOR="#0000FF"]"{[/COLOR]
insmod ext2
set root=(hd1,1)
set isofile="/isos/Porteus-XFCE-v5.0-x86_64.iso"
search --no-floppy --file --set=root $isofile
loopback loop $isofile
linux (loop)/boot/syslinux/vmlinuz from=$isofile changes=/50_porteus login=root extramod=UUID:67ccab9a-9ae9-4021-90b1-ef18d143711a/50_porteus/xfce extramod=UUID:67ccab9a-9ae9-4021-90b1-ef18d143711a/64_V40/porteus/modules
initrd (loop)/boot/syslinux/initrd.xz
}
```

After Porteus50, quotation marks and open curly bracket missing.
I have added the quotation marks and bracket in blue.

---

### Post by francois.e on 2022-07-23
You were right. But it did not change the grub menu presentation at bootup. Only kubuntu will appear as a choice.

Here is what I have done. I have tested that on a second installation and it works. But it will not work on the MSI computer. 

1) I have changed the 40_custom file for:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# ajout fl en dessous

# path to the partition holding ISO images (using UUID)
probe -u $root --set=rootuuid
set imgdevpath="/dev/disk/by-uuid/$rootuuid"

menuentry "kubuntu" {
 linux /boot/vmlinuz-5.15.0-41-generic root=UUID:67ccab9a-9ae9-4021-90b1-ef18d143711a
 initrd /boot/initrd.img-5.15.0-41-generic
}

2) updating grub

fl@fl-X340-series:~$ sudo update-grub
[sudo] password for fl: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-41-generic
Found initrd image: /boot/initrd.img-5.15.0-41-generic
Found linux image: /boot/vmlinuz-5.13.0-30-generic
Found initrd image: /boot/initrd.img-5.13.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
fl@fl-X340-series:~$ 

rebooted.

There is still only one choice to boot from the grub menu list at bootup.

Propositions still appreciated.

Thanks.

---

### Post by oldfred on 2022-07-24
I never remembered to run sudo update-grub when I added a new or changed ISO.
So I add a configfile into 40_custom which loads a file in my /ISO folder. I then can edit that file without update-grub.

I add this entry once, and use labels to find data partition with /ISO folder.
```
menuentry 'Live ISOs in data drive' {
search --set=root --label data_nvme
configfile /ISO/livecdimage.cfg

} 

```

Then in my ISO folder in my nvme_data partition, I create livecdimage.cfg file.
```

# spacer line
menuentry " " {
set root= 
}

menuentry "Kubuntu 22.04 Jammy amd64" {
    set isofile="/ISO/kubuntu-22.04-desktop-amd64.iso"
    insmod part_gpt
    #rmmod tpm
    search --set=root --label nvme_data
    loopback loop (${root})$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd
}


```

Just tested entry, and it gives me an error on nvme_data not found, but I press enter & it works?
I may just go back to just saying partition like this with no search nor set root command:
loopback loop (hd0,5)$isofile

Labels have always worked without issue for booting other installs once installed. So grub must be able to see labels.

---

