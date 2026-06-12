---
title: "grub rescue (boot-repair report attached)"
date: 2023-03-08
forum: Installation &amp; Upgrades
---

### Post by yesok2 on 2023-03-08
my partitions and the erase and auto-partition failed.

solution has to be non-bios as i dont have access. so boot-repair tools wont work.


some failed methods:


this failed with windows usb

bootrec /fixboot
bootrec /fixmbr

(access denied :( )


this wasnt tried successfully. Should I try?
Method 2 To Rescue Grub
    Open terminal after booting up into the live desktop.
    Mount the root partition by typing /mnt and boot to /mnt/boot and hit enter. [e.g. sudo grub-install –root-directory=/mnt –boot-directory=/mnt/boot /dev/sda]

You should replace /dev/sda with the correct partition or disk. Now update grub by typing sudo update-grub.  It can take some time, so wait. After a successful update, reboot, and voila problem was solved.


#insmod normal doesnt work as command


third line failed here:
3rd step "" grub-install failed to get cononical path of /cow

sudo apt-get update
sudo apt-get install --reinstall grub-pc
sudo grub-install /dev/sda
sudo update-initramfs -u
sudo update-grub








tried a bunch of things: this failed
```

Once you’ve created your bootable media and inserted it into the PC, boot directly to the live environment. Once loaded up, open a terminal and type the following commands:

    First, we need the drive name and partition number that we’re trying to rescue. Type the following command to see a full list of the partitions on your hard drive:

    $ sudo fdisk -l

    The hard drive and partition will be identified by something like /dev/sda5, but that’s just an example, yours is likely different. Once you know how yours is called, type the following commands (while substituting the hard drive name and partition number where necessary) to mount the partition:

    $ sudo mkdir /mnt/temp
    $ sudo mount /dev/sda5 /mnt/temp

    Next, it’s necessary to chroot into the installed system to reinstall the grub packages. Execute the following commands:

    $ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
    $ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
    $ sudo chroot /mnt/temp

    If your terminal prompt has changed to show the root user (i.e. root@ubuntu:/#) then the chroot was successful. Now it’s time to remove grub; be sure to use purge so all of the grub conf files are also removed. You’ll also be prompted asking if you’re sure that you want to remove grub, use TAB on your keyboard to select ‘Yes’ and continue.

    # apt-get update
    # apt-get purge grub grub-pc grub-common

    Finally, reinstall grub with the following commands:

    # apt-get install grub-common grub-pc
    # update-grub

    That should be it. To wrap up, exit chroot and unmount everything with the commands below. Then, remove your live media and reboot the system.

    # exit
    $ for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
    $ reboot

As long as your terminal didn’t return any errors when following the steps above, you should now be able to boot directly into your Linux system as before.
Conclusion

If grub doesn’t work properly, your computer doesn’t know how to load Linux. There are a few reasons for why grub may fail to find a partition to boot to, with the most common cause being when a user rearranges partitions and the changes fail to sync with grub’s configuration. The steps above work by completely reinstalling grub and all of its configuration files. This will allow your system to find the Linux OS on your hard drive and boot to it.


```

---

### Post by yancek on 2023-03-08
> solution has to be non-bios as i dont have access 

Why not?  Do the function keys to access BIOS not work?  Is this not your computer?

The windows usb failed because you do not have any windows OS installed so it could not possibly work.

BIOS_Boot and EFI partitions are an either/or situation.  You only need one.  If you want an EFI install on your GPT disk (this is the standard method) then you have the EFI partition and do not need the BIOS_Boot partition.  The reverse is also true.  What you show in boot repair is a typical EFI install.  What do you want an EFI or Legacy install?  Your boot repair output shows is booted in Legacy mode.  You must have booted in UEFI mode at some point to get the install as you have Ubuntu showing installed on sda3 and the proper EFI files on sda2..  Did you do multiple installation attempts?  Otherwise I would not expect to also see a BIOS_Grub partition.

>  Mount the root partition by typing /mnt and boot to /mnt/boot and hit enter. 

You would first need to actually mount by using:  sudo mount /dev/sda3 /mnt  Did you do that?

> 3rd step "" grub-install failed to get cononical path of /cow
 

That error is generally seen when trying to install to a drive but don't use the proper commands and the installation is to the DVD/USB.  Chroot wasn't done or wasn't done properly.

I guess the most important thing is what type of install do you want, EFI or Legacy?

---

