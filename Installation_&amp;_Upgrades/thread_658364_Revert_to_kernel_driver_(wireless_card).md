---
title: "Revert to kernel driver (wireless card)?"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by WardLoockx on 2008-01-04
Hello,

I have a intel wireless pro 4965 card and try'd some other drivers. by default the card worked under Gutsy (I think it used the 3945modue of the intel wireless driver). Now I can't find any wlan0 card so is it possible to remove the driver that the card is using (don't now the exact name :() and then use the default kernel driver for my card ?

Greets,
Ward

---

### Post by dannyboy79 on 2008-01-04
what does this command entered into a terminal session return?

lsmod

also please post the output of this command.

lspci

that way I can see what wifi chipset your computer has in it to see what module should be loaded. whatever guide you used to install new modules, you can just first remove that module by entering 

sudo modprobe -r modulename

then if you updated some file so that that newer module loads at boot up you'll need ot change that back as well. what guide did you follow? I can check it out and help you fix it.

---

### Post by WardLoockx on 2008-01-04
> **dannyboy79 said:**
> what does this command entered into a terminal session return?

lsmod

also please post the output of this command.

lspci

that way I can see what wifi chipset your computer has in it to see what module should be loaded. whatever guide you used to install new modules, you can just first remove that module by entering 

sudo modprobe -r modulename

then if you updated some file so that that newer module loads at boot up you'll need ot change that back as well. what guide did you follow? I can check it out and help you fix it.

I removed all the modules using "sudo rmmod mac80211". Normally there are no modules for this card installed. I hoped he took them automaticly if there was not a special module for it. but didn't work.

[http://www.intellinuxwireless.org/?p=iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi)

These are the drivers I try'd to install. Ubuntu kernel uses the 3945 drivers and works fine but I wanted to Play :D

---

### Post by dannyboy79 on 2008-01-04
well it appears as though you configured a totally different kernel if I read the guide correctly. you should still have the old kernel installed and be able to boot to it but you have to edit grub's menu so it boots to the old jkernel and not the one you createdso that it was able to run the new mac80211 module.

to edit grub 's menu, issue this command so that I can see what's in your grub's menu.lst file

gksudo gedit /boot/grub/menu.lst

then copy and paste that whole file here. I can help from there.

also issue this command to see if the old kernel is still installed.

sudo aptitude search linux-image

and paste the output here as well.

---

### Post by WardLoockx on 2008-01-05
> **dannyboy79 said:**
> well it appears as though you configured a totally different kernel if I read the guide correctly. you should still have the old kernel installed and be able to boot to it but you have to edit grub's menu so it boots to the old jkernel and not the one you createdso that it was able to run the new mac80211 module.

to edit grub 's menu, issue this command so that I can see what's in your grub's menu.lst file

gksudo gedit /boot/grub/menu.lst

then copy and paste that whole file here. I can help from there.

also issue this command to see if the old kernel is still installed.

sudo aptitude search linux-image

and paste the output here as well.

**My grub menu file**
[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout         3

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
# kopt=root=UUID=6c5b1bce-8482-4b0c-9449-78f66ec89f1c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=6c5b1bce-8482-4b0c-9449-78f66ec89f1c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=6c5b1bce-8482-4b0c-9449-78f66ec89f1c ro single
initrd          /boot/initrd.img-2.6.22-14-server

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6c5b1bce-8482-4b0c-9449-78f66ec89f1c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6c5b1bce-8482-4b0c-9449-78f66ec89f1c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[/PHP]


**Aptitude searchs**
[PHP]
p   linux-image                                                                         - Generic Linux kernel image.
v   linux-image-2.6                                                                     -
p   linux-image-2.6.22-14-386                                                           - Linux kernel image for version 2.6.22 on i386
i   linux-image-2.6.22-14-generic                                                       - Linux kernel image for version 2.6.22 on x86/x86_64
p   linux-image-2.6.22-14-rt                                                            - Linux kernel image for version 2.6.22 on RT kernel
i A linux-image-2.6.22-14-server                                                        - Linux kernel image for version 2.6.22 on x86/x86_64
p   linux-image-2.6.22-14-ume                                                           - Linux kernel image for version 2.6.22 on Ubuntu Moblie and Embedded
p   linux-image-2.6.22-14-virtual                                                       - Linux kernel image for version 2.6.22 on x86
p   linux-image-2.6.22-14-xen                                                           - Linux kernel image for version 2.6.22 on This kernel can be used for Xen dom0 and domU
p   linux-image-386                                                                     - Linux kernel image on 386.
p   linux-image-debug-2.6.22-14-386                                                     - Linux kernel debug image for version 2.6.22 on i386
p   linux-image-debug-2.6.22-14-generic                                                 - Linux kernel debug image for version 2.6.22 on x86/x86_64
p   linux-image-debug-2.6.22-14-server                                                  - Linux kernel debug image for version 2.6.22 on x86/x86_64
p   linux-image-debug-2.6.22-14-virtual                                                 - Linux kernel debug image for version 2.6.22 on x86
p   linux-image-debug-386                                                               - Linux kernel debug image for 386 kernel image
p   linux-image-debug-generic                                                           - Linux kernel debug image for generic kernel image
p   linux-image-debug-server                                                            - Linux kernel debug image for server kernel image
p   linux-image-debug-ume                                                               - Linux kernel debug image for ume kernel image
i   linux-image-generic                                                                 - Generic Linux kernel image
p   linux-image-rt                                                                      - Linux kernel image on realtime kernel
p   linux-image-server                                                                  - Linux kernel image on Server Equipment.
p   linux-image-ume                                                                     - Linux kernel image on 386 Embedded/Mobile
p   linux-image-virtual                                                                 - Linux kernel image geared towards virtualised hardware
p   linux-image-xen                                                                     - Linux kernel image on Xen

[/PHP]

Hope you are something with this info!

Thanks!

---

### Post by dannyboy79 on 2008-01-05
well it doesn't appear that you did a new kernel and enabled the things they stated you should using menuconfig. I can't say that you did or didn't I suppose but the name isn't different. what happens when you boot to another kernel? like this one: Ubuntu 7.10, kernel 2.6.22-14-generic 

you would do that by hitting the ESC key when grub is loading upon system startup, then you would select the kernel you want to boot and hit enter within the grub menu. when you boot into the new kernel, issue this command

lsmod

and post the output here

---

### Post by WardLoockx on 2008-01-06
> **dannyboy79 said:**
> well it doesn't appear that you did a new kernel and enabled the things they stated you should using menuconfig. I can't say that you did or didn't I suppose but the name isn't different. what happens when you boot to another kernel? like this one: Ubuntu 7.10, kernel 2.6.22-14-generic 

you would do that by hitting the ESC key when grub is loading upon system startup, then you would select the kernel you want to boot and hit enter within the grub menu. when you boot into the new kernel, issue this command

lsmod

and post the output here

Okay when I boot the generic kernel instead I have wireless support :)

Here is the lsmod outpot
[PHP]
Module                  Size  Used by
ipv6                  273892  10
af_packet              24840  2
i915                   25856  2
drm                    83348  3 i915
rfcomm                 42136  4
l2cap                  26240  11 rfcomm
vboxdrv                60208  0
ppdev                  10244  0
acpi_cpufreq           10568  1
cpufreq_conservative     8072  0
cpufreq_userspace       5280  0
cpufreq_stats           7232  0
cpufreq_ondemand        9612  1
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0
button                  8976  0
battery                11012  0
ac                      6148  0
bay                     6912  0
dock                   10656  1 bay
sbs                    19592  0
container               5504  0
video                  18060  0
sbp2                   24072  0
parport_pc             37412  0
lp                     12580  0
parport                37448  3 ppdev,parport_pc,lp
arc4                    2944  2
snd_hda_intel         262552  3
ecb                     4608  2
joydev                 11328  0
blkcipher               7556  1 ecb
snd_pcm_oss            44800  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            35328  0
snd_seq_midi            9728  0
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  3 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41388  0
iwl4965               101480  0
iwlwifi_mac80211      175112  1 iwl4965
sr_mod                 17828  0
snd                    56452  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
cdrom                  37536  1 sr_mod
hci_usb                18332  2
yenta_socket           27532  1
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211                7304  1 iwlwifi_mac80211
bluetooth              57060  7 rfcomm,l2cap,hci_usb
psmouse                39952  0
serio_raw               8068  0
pcspkr                  4224  0
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
intel_agp              25620  1
agpgart                35016  3 drm,intel_agp
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
evdev                  11136  5
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sd_mod                 30336  4
usbhid                 29536  0
hid                    28928  1 usbhid
ata_piix               17540  0
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
ahci                   23300  3
tg3                   110980  0
ata_generic             8452  0
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor
[/PHP]

Can you explain how this comes ? don't understand it :( wich kernel is the default ? Really want to understand what went wrong !

Thanks

---

### Post by dannyboy79 on 2008-01-07
i can't say what went wrong. did you or did you not create a new kernel? if you did and you named it "server", than that's what's wrong, that kernel has things enabled in it which messes with the default wifi modules from working.

if you didn't create or edit the "server" kernel, than I have no idea what you did.

the way to make sure you always boot to the generic kernel is to either change the "0" within your /boot/grub/menu.lst file so that it has this instead, "1" (meaning it will always boot kernel 1, instead of kernel 0. grub kernels start at 0)

or just uninstall that "server" kernel. if you do and also want to reinstall, clear your aptitude cache so it removes that modified kernel and downloads it from teh ubuntu servers again. good luck

---

### Post by WardLoockx on 2008-01-07
> **dannyboy79 said:**
> i can't say what went wrong. did you or did you not create a new kernel? if you did and you named it "server", than that's what's wrong, that kernel has things enabled in it which messes with the default wifi modules from working.

if you didn't create or edit the "server" kernel, than I have no idea what you did.

the way to make sure you always boot to the generic kernel is to either change the "0" within your /boot/grub/menu.lst file so that it has this instead, "1" (meaning it will always boot kernel 1, instead of kernel 0. grub kernels start at 0)

or just uninstall that "server" kernel. if you do and also want to reinstall, clear your aptitude cache so it removes that modified kernel and downloads it from teh ubuntu servers again. good luck

Okay now I boot the generic kernel (changed it in grub). can I see when the kernel is created ? Can you give some more info on how to remove the kernel properly? I now use my generic kernel and it works fine (wlan is ok) so I think I can get rid of that server kernel.

Thanks,
Ward

---

### Post by dannyboy79 on 2008-01-07
well I believe it would just be this command

sudo aptitude remove --purge linux-image-2.6.22-14-server

or you could just use synaptic to remove it. grub should update by itself. one thing to make sure though after you remove that kernel, you might need to re-edit the menu.lst and change it back to 0, so that it would boot the first kernel which should become the generic kernel. good luck

---

