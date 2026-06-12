---
title: "Possible menu.lst problem after kernel update"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by Col-1023 on 2012-09-23
Today I was offered a kernel update, but while updating the kernel I was asked about menu.lst and offered these suggestions,

1. install the package maintainer's version
2. keep the local version currently installed
3. show the differences between the versions
4. show a side-by-side difference between the versions
5. show a 3-way difference between available versions
6. do a 3-way merge between available versions (experimental)
7. start a new shell to examine the situation

What would you like to do about menu.lst?

I didn't really know what menu.lst was so I chose number 4.

Everything else went fine, and after rebooting there was some graphics ugliness, but eventually everything seemed to work.

A second reboot showed no graphics ugliness.

After some reading, it may have been wiser to choose number 1, since even though I've rebooted, I my system may not be using the latest kernel.

System monitor says 3.2.0-30 generic, whereas the kernel update today was 3.2.0-31 I believe.

Synaptic shows the latest kernel I have installed and marked green is 3.2.0-31.50

Ubuntu is the only os on this machine, so by doing nothing shouldn't the latest kernel be automatically installed, I only started typing or moving the mouse when the passwork screen comes up.

Is this a problem, or nothing to worry about.

Thanks In Advance

---

### Post by Col-1023 on 2012-09-23
I ran uname -r, uname -v and got back 3.2-0.30 and #48

After more searching, My problem might be related to this Bug #1054289


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054289](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054289)

---

### Post by mikewhatever on 2012-09-23
The menu.lst is the old GRUB's config file, and when seeing that message, it's generally safer to select the second option.

Since everything seems to work, I am not sure there is anything to do.

The bug report you've linked to seems unrelated.

---

### Post by Col-1023 on 2012-09-23
Thanks Mike for your reply.

I linked to that bug because while update manager had downloaded the latest kernel, 3.2.0-31.50, this is not currently running on my system, that is it's not been installed.

The kernel on my system is 3.2.0-30.48.


I think something strange did happen with the latest ketnel update, but don't know whether it's a big deal or just a trivial problem that will be fixed soon.

---

### Post by oldfred on 2012-09-23
If you kept an old menu you have to update the menu yourself to include the new kernel.

Whether old grub legacy or grub2.

sudo update-grub

But why do you still have grub legacy? Ubuntu 9.04 was the last to use grub legacy as the standard. Grub2 started with 9.10 and only those who upgraded may have still kept grub legacy. Have you just upgraded from 9.04 or before or had some issue where you thought you needed grub legacy?

---

### Post by Col-1023 on 2012-09-24
Thanks Oldfred for your reply.

I think I did start with ubuntu 9.04 a few years back, then upgraded to 9.10 - 10.04 lts, where I stayed until upgrading to 12.04.1.

I Never upgraded grub to grub2 because I was worried that if anything went wrong the system wouldn't boot, and I need this system working, I also didn't see any advantages in grub2.

So assuming I'm still using grub legacy, if I run "sudo update-grub" will that update my menu.lst file, or is this a command that only works with grub2

---

### Post by grahammechanical on 2012-09-24
The command to update Grub legacy was "sudo update-grub." and it is also the command for Grub 1.99 (also called Grub 2) and for the real Grub 2 that now comes with 12.10.

I have found that kernel updates do not happen at the same time. I see parts of the kernel being downloaded and then in the next update the rest of the parts to the kernel come down. And then the new kernel gets activated in Grub. That could be what is happening here.

When a new kernel is brought in the update manager should run update-grub and the details section should show what kernels it is finding.


Regards.

---

### Post by Col-1023 on 2012-10-15
Sory, been away from this pc for a while.

The sudo upgdte-grub DIDN'T WORK.

It found all the kernels I have installed, including the latest 3.2.32, and it said it had updated menu.lst.

But when I restarted and checked menu.lst it hadn't changed, with the 3.20.30 kernel still the top most kernel.

How can this happen,

Should I run gksudo update-grub

Will that do any harm, or will it fix the problem.

Nautilus says the files were written [modified] today at the times I ran sudo update-grub, so something seems to be wrong.

Any help appreciated.

There were no error messages reported when running sudo update-grub.

I found this in my menu.lst file,

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

These entries were in the defaults, automatic section of menu.lst, should I chantge these settings, and if so how to change them without causing damage.

TIA

---

### Post by darkod on 2012-10-15
Do you see the advantage of grub2 now? :)

I suggest you do what you should have done years ago, upgrade to grub2.

You can do that from within ubuntu and there is very little risk involved. Just in case, if things go wrong, you should have a live cd of the version you are running now (12.04 LTS) at hand.

If you have only one hdd, /dev/sda, it means you need grub2 on the MBR of /dev/sda. The commands to remove all grub1 and install grub2 from within the running installation would be like:
```
sudo apt-get remove --purge grub grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

Reboot and you should see the grub2 menu with an option for the latest kernel.

PS. Before trying the above it's wise to check whether you use msdos or gpt table. With gpt grub2 doesn't have enough space on the MBR and needs a small bios_grub partition. You can see your table type among the info in the output of:
sudo parted -l (small L)

---

### Post by Col-1023 on 2012-10-15
Thanks for the info Darkod.

I have 3 x 750 gb drives, but only 1 os [ubuntu] running on sda, so does that change any of the commands above?

I'm just wondering whether changing,

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

to

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true


in my menu.lst file would fix my problem.

Thanks.

---

### Post by darkod on 2012-10-15
As long as you are booting from /dev/sda in bios, no change is needed because the last command will install grub2 to /dev/sda.

As for the grub1 question, I'm not sure since I don't know it that much in detail. If I remember correctly, I think in the menu that popped up you needed to select 1. Maintainer's version and that should keep it up to date.

---

### Post by Col-1023 on 2012-10-15
Just for further info running sudo update-grub gives,

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-3.2.0-32-generic
Found kernel: /vmlinuz-3.2.0-31-generic
Found kernel: /vmlinuz-3.2.0-30-generic
Found kernel: /vmlinuz-2.6.32-42-generic
Found kernel: /vmlinuz-2.6.31-22-generic
Found kernel: /vmlinuz-2.6.31-21-generic
Found kernel: /vmlinuz-2.6.31-20-generic
Found kernel: /vmlinuz-2.6.31-19-generic
Found kernel: /vmlinuz-2.6.31-17-generic
Found kernel: /vmlinuz-2.6.31-16-generic
Found kernel: /vmlinuz-2.6.28-17-generic
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Here is my menu.lst file after running sudo update-grub today, notice how the 3.2.31 and 3.2.32 kernels don't show up in menu.lst.

Any answers as to why this would happen?


```
# menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=f161f9cb-e2c7-4a05-9bb8-4f4b51025df1

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

title        Ubuntu 12.04.1 LTS, kernel 3.2.0-30-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-3.2.0-30-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-3.2.0-30-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 3.2.0-30-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-3.2.0-30-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-3.2.0-30-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.32-42-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.32-42-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.32-42-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.32-42-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.32-42-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.32-42-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-22-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-22-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-22-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.31-22-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-21-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-21-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-21-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.31-21-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-20-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-20-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-20-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.31-20-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-19-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-19-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-19-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.31-19-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-17-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-17-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-17-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.31-17-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-16-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-16-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.31-16-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.31-16-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.28-17-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.28-17-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.28-17-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.28-17-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.28-17-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.27-11-generic
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.27-11-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa quiet splash 
initrd        /initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 12.04.1 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /vmlinuz-2.6.27-11-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro xforcevesa  single
initrd        /initrd.img-2.6.27-11-generic

title        Ubuntu 12.04.1 LTS, memtest86+
uuid        f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Col-1023 on 2012-10-15
Thaks Darkod, I thought that may be the case, unfortunately the question didn't come up abain when I updated the kernels.

Does anyone know how I can change the setting to use maintainer's version.

That was the only time I had ever been asked a question while updating a kernel.

Thanks.

---

### Post by oldfred on 2012-10-15
Please use code tags, highlight like a copy & click the # in edit panel to automatically add them.

Boot-Repair also has a function to purge & reinstall grub2. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


Over the years I have gotten the system maintainers question on various configuration files. It is a real problem as if you say yes you lose all your custom settings. But your settings may not be required in the new version. If you say no, you save your settings but do not get any new settings and the software may not work correctly with old settings. 

I now just backup separately (copy into /home for regular backup of /home) all the system files in /etc or grub or elsewhere not in /home. Then always accept system maintainers version but realize I may have to manually re-edit. But I have my old version to copy from if needed.

---

### Post by Col-1023 on 2012-10-15
Thanks oldfred.

first my current menu.lst has hidemenu enabled and only a 3 second time to bring it up, if I upgrade to grub2, will this be changed automatically so I can see the options, and will the time limit be increased, Howmany is set to all, could this be a problem for the upgrade considering I have many kernels in menu.lst.


I've looked at the upgrade page for grub2, and as part of the gui it asks which partitions to put grub in.

I checked gparted, and on my primary ubuntu drive I have 4 or 5 partitions,

/dev/sda1 - /boot

/dev/sda2 - /

/dev/sda3 /extended

   /dev/sda5 - /home

/dev/sda4 - /linux-swap

the boot and grub folders for grub1 are currently in filesystem according to nautilus, so I don't know which partition they're in.

My other 2 data disks are just 1 partition each, ie /dev/sdb1 and /dev/sdc1

If the upgrade fails, which is the best version to use for a usb repair disk, the alternative or desktop cds.

Thanks.

---

### Post by darkod on 2012-10-15
The bootloader always goes to the MBR of the disk which is labeled /dev/sda, without any number in it. The number stands for a partition, and the bootloader is installed on partition only in special situation. The boot process starts from the MBR hence the natural location for the bootloader is there.

If you have only ubuntu, grub2 menu also doesn't show by default which makes sense since there is no other OS to choose. Why slow down the boot with a menu. You can make the menu show by holding Shift during the boot. Also, you can make it show permanently in the grub2 config files.

grub2 is much smarter when old kernels are concerned. It combines them in a single submenu called previous Versions. So you can still fidn them there but the grub2 menu is not very long at the same time. There are only entries for the latest kernel, the other are in Previous Versions which makes the menu much more compact.

In case things go bad, the live cd of 12.04 is the only thing you need to fix it.

PS. Note that if you are using the mentioned boot-repair tool, I think you have to tick an option that you have separate /boot partition, which you do. You wouldn't need that if you install grub2 from your running system since /boot will be already mounted and the OS is aware of it. Persoanlly, since your computer boots fine right now, I would do it from within ubuntu. You use live mode and boot-repair as last resort, usually when you can't even boot.

Your computer is bootable, you only need to remove/purge grub1 and install grub2.

I think boot-repair in live mode gives more options for errors, especially with separate /boot. You're not repairing anything, you are simply switching one bootloader for the other.

---

### Post by Col-1023 on 2012-10-15
Thanks alot for the info Darkod.

---

### Post by oldfred on 2012-10-15
I think Boot-Repair is just running the same purge & reinstall commands Darko gave back in post #9. Just be sure to have working Internet as once old version is  purged you have to download the new version from Ubuntu repository.

I like to have several repair tools in my tool box. So I always have the current version of Ubuntu liveCD, Knoppix, gparted, Boot-Repair, SuperGrub and often others as I just like to try them. I use grub2 to loopmount the ISO and have them all on one flash drive. I used to burn a lot of CDs when upgrading so I had the current repairCD of everything. Flash drive is a lot easier and saves burning a lot of CDs. :)

---

### Post by Col-1023 on 2012-10-15
I read carefuly the ubuntu grub2 upgrading page and ran

sudo apt-get install grub-pc

This ran and gave the option to upgrade to grub2, I selected ok, it then gave me the option the add chainload to menu.lst, I selected yes, the terminal continued without giving me any other options shown in that upgrade guide, such as import data or which partition to put grub on.

Here is the output from terminal, I want to know did everything go ok before I reboot?

TIA

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fgfs-base libproj0 linux-headers-3.2.0-30 mplayer-nogui libutouch-evemu1
  libutouch-geis1 libutouch-frame1 fgfs-scenery-base libapr1 libogdi3.2
  libcoin60 libpar2-0 libsvn1 libdap11 libgdal1-1.7.0 libpostproc-extra-51
  libgnome-desktop-2-17 fgfs-aircraft-base libepsilon0 libswscale-extra-0
  libxerces-c28 fgfs-models-base libopenthreads14 libhdf5-serial-1.8.4
  libgeos-c1 proj-data libfreexl1 hddtemp libspatialite3 proj-bin
  libutouch-grail1 libgeos-3.2.2 linux-headers-3.2.0-30-generic libhdf4-0-alt
  libaprutil1 simgear2.4.0 libopenscenegraph80 libdapclient3 libnetcdf6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  desktop-base
The following packages will be REMOVED:
  grub
The following NEW packages will be installed:
  grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
0 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
Need to get 1,105 kB of archives.
After this operation, 396 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.iinet.net.au/pub/ubuntu/ precise-updates/main grub2-common amd64 1.99-21ubuntu3.4 [94.2 kB]
Get:2 http://ftp.iinet.net.au/pub/ubuntu/ precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.4 [867 kB]
Get:3 http://ftp.iinet.net.au/pub/ubuntu/ precise-updates/main grub-pc amd64 1.99-21ubuntu3.4 [140 kB]
Get:4 http://ftp.iinet.net.au/pub/ubuntu/ precise/main grub-gfxpayload-lists amd64 0.6 [3,506 B]
Fetched 1,105 kB in 1s (811 kB/s)                  
Preconfiguring packages ...
(Reading database ... 406525 files and directories currently installed.)
Removing grub ...
Processing triggers for man-db ...
Selecting previously unselected package grub2-common.
(Reading database ... 406480 files and directories currently installed.)
Unpacking grub2-common (from .../grub2-common_1.99-21ubuntu3.4_amd64.deb) ...
Selecting previously unselected package grub-pc-bin.
Unpacking grub-pc-bin (from .../grub-pc-bin_1.99-21ubuntu3.4_amd64.deb) ...
Selecting previously unselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.99-21ubuntu3.4_amd64.deb) ...
Selecting previously unselected package grub-gfxpayload-lists.
Unpacking grub-gfxpayload-lists (from .../grub-gfxpayload-lists_0.6_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up grub2-common (1.99-21ubuntu3.4) ...
Setting up grub-pc-bin (1.99-21ubuntu3.4) ...
Setting up grub-pc (1.99-21ubuntu3.4) ...

Creating config file /etc/default/grub with new version
Generating core.img
Saving menu.lst backup in /boot/grub/menu.lst_backup_by_grub2_postinst
Running update-grub Legacy to hook our core.img in it
    Searching for GRUB installation directory ... found: /boot/grub
    Searching for default file ... found: /boot/grub/default
    Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
    Searching for splash image ... none found, skipping ...
    Found GRUB 2: /grub/core.img
    Found kernel: /vmlinuz-3.2.0-32-generic
    Found kernel: /vmlinuz-3.2.0-31-generic
    Found kernel: /vmlinuz-3.2.0-30-generic
    Found kernel: /vmlinuz-2.6.32-42-generic
    Found kernel: /vmlinuz-2.6.31-22-generic
    Found kernel: /vmlinuz-2.6.31-21-generic
    Found kernel: /vmlinuz-2.6.31-20-generic
    Found kernel: /vmlinuz-2.6.31-19-generic
    Found kernel: /vmlinuz-2.6.31-17-generic
    Found kernel: /vmlinuz-2.6.31-16-generic
    Found kernel: /vmlinuz-2.6.28-17-generic
    Found kernel: /vmlinuz-2.6.27-11-generic
    Found kernel: /memtest86+.bin
    Updating /boot/grub/menu.lst ... done
    
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-2.6.32-42-generic
Found initrd image: /boot/initrd.img-2.6.32-42-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.28-17-generic
Found initrd image: /boot/initrd.img-2.6.28-17-generic
Found linux image: /boot/vmlinuz-2.6.27-11-generic
Found initrd image: /boot/initrd.img-2.6.27-11-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up grub-gfxpayload-lists (0.6) ...
david@liberator:~$ 

```

---

### Post by darkod on 2012-10-15
Yes and no, but if I start writing more you will get confused. So I will just say Yes.

Reboot and it should work.

---

### Post by Col-1023 on 2012-10-15
OK, I rebooted, got no menue, but that's supposed to be normal, logged in ok, and after typing uname -r, uname -v, it seems I'm running kernel,

3.2.0.32 #51.

Which should be the latest kernel, so it seems everything went ok, touch wood.

The Upgrade page says to make the change perminent in the MBR I need to do,

sudo upgrade-from-grub-legacy

Is this still the case?

Thanks to everyone for your help, nuch appreciated.

---

### Post by darkod on 2012-10-15
Yes, I think it's still necessary.

If you first purged grub1 and then installed grub2 this step wouldn't have been needed. I hope it won't leave sort of hybrid grub1/grub2 setup.

The upgrade-from-grub-legacy should take care for that not to happen and clean up any files of grub1, including menu.lst.

---

### Post by Col-1023 on 2012-10-15
Thanks Darkod for your help, I'll run the system like this for a while and see how a few kernel updates go before making the final upgrade.

Touch wood everything continues to work well.

---

