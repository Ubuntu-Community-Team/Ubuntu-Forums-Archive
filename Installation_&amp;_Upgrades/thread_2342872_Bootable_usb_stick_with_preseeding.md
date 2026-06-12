---
title: "Bootable usb stick with preseeding"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by captainquirk2 on 2016-11-10
Hi there,

I'm trying to accomplish the following thing : **create a bootable usb stick containing a preseed file** for automatic installation. This file would allow me to
[LIST]
[*]Set **basic configuration values** like keyboard, language, main account
[*]Set **partitioning**
[*]**Install some packages** I always need to kick off a new installation.
[/LIST]


Now, creating a bootable stick can be done with GUI programs like **Unetbootin** or even the built-in **Startup disk creator**, but when the iso file is copied over to the usb drive, nothing can be modified anymore. Is this even the proper way to do things ?

Thanks in advance

CaptainQuirk

---

### Post by C.S.Cameron on 2016-11-10
Welcome to the forums.

Have you looked at **mkusb**?
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Or you could do a modified Ubuntu Full or Persistent install to USB and clone it to disk as required, (see **dd**).

---

### Post by Bucky Ball on 2016-11-11
Welcome. Yes, you may be putting the cart before the horse. Do a persistence install to the USB, boot to it and customise it as you like. You now have your customised Ubuntu on USB. As mentioned previously, you could now clone the USB / partition to a drive partition with dd or something like it.

In other words, you can install Ubuntu on USB. You seem to be under impression you can only create a bootable install media USB with the ISO for installing Ubuntu to another device. You need a persistence install, Ubuntu installed on USB, not a Ubuntu install USB. :)

---

### Post by sudodus on 2016-11-11
Another option is to make an ***OEM installation***. See this link:

[Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

An OEM installed system can be cloned with Clonezilla, or you can make a tarball with the One Button Installer, and install from that tarball to other computers.

---

### Post by C.S.Cameron on 2016-11-11
I think it would be best to unplug the internal hard drive while using OEMI, at least the first time.

---

### Post by captainquirk2 on 2016-11-12
Hi there !

Thank you all for your responses. Reading them I realize that I didn't state my end purpose clearly enough.

I'm using **provisioning scripts** to achieve the two following tasks :


[LIST]
[*]**Install** a new development machine
[*]**Update any machine** I'm working on with the latest modifications I made on another. (typically dev machine at work)
[/LIST]

As I **continuously** let the set of provisioning scripts evolve, I want to put some **build system** in place with an **iso** file as the result. Those provisioning scripts need some **prerequisites**. I would like to find a way, as part of this build procedure, to **modify a base iso image** (I think it can be done through preseeding) so that those prerequisites are met and the provisioning scripts can run right after install.

Transforming the iso file to a bootable drive is just the end of the build procedure.

Could you point me to any resources on this part ?

---

### Post by ubfan1 on 2016-11-12
Here's a set of notes I found on my system (untested by me, unknown source):

#edit an iso
mount -o loop /path/to/iso /mnt/iso" (/mnt/iso must be created if it doesn't exist).
cp -a /mnt/iso /tmp/iso
Make all your changes in /tmp/iso.
Use mkisofs to create the modified ISO from the /tmp/iso directory:
#mkisofs -R -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o <new iso filename> /tmp/iso
mkisofs -o /tmp/new.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -R -V disks .

Of course,  it might be better for you to investigate changing the existing preseeding approach to not rely on having the "ubuntu" link in the root of the ISO.
Without such a link, and if you machines are UEFI, you can just copy all the ISO files to a FAT fs, and modify/add as needed.  On a USB, have an EFI partition as well at the FAT partition holding the files and that is bootable.

---

### Post by oldfred on 2016-11-12
If just a one off, not a large group of systems, it may just be easier to copy /home to new system, install list of exported applications and possibly some other settings/configurations/programs/folders in /etc.
It is more like confirming that your backup of your other system works by restoring to your home system.

I typically install in 10 min, run script that adds some programs and loads the entire list of apps from my exported saved file. I typically do not copy my backup of /home, but have scripts to edit the majority of changes. Fully configured system in about an hour. Probably less if I just copied /home back, but often want to experiment so do not want all the same settings.

---

### Post by captainquirk2 on 2016-11-15
Thanks for your help, first ; this is much appreciated.

@oldfred, unfortunately, copying my workstation's home directory at work on my personal laptop is not something I can do, as you can imagine.

@ubfan1, I tried your solution and the set of commands you give seem to work but the preseeding itself doesn't seem to be taken into account. I've been doing the following things :

```

mount -o loop /path/to/iso /mnt/iso" (/mnt/iso must be created if it doesn't exist).
cp -a /mnt/iso /tmp/iso

```

Then I overwrote the /tmp/iso/isolinux/preseed/ubuntu.seed with the following file, adapted from [https://help.ubuntu.com/lts/installation-guide/example-preseed.txt](https://help.ubuntu.com/lts/installation-guide/example-preseed.txt)
```


#### Contents of the preconfiguration file (for xenial)
### Localization
# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_US

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select fr

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

# Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string ftp
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# To create a normal user account.
d-i passwd/user-fullname string CaptainQuirk
d-i passwd/username string captainquirk
# Normal user's password, either in clear text
d-i passwd/user-password password azerty
d-i passwd/user-password-again password azerty

# The installer will warn about weak passwords. If you are sure you know
# what you're doing and want to override it, uncomment this.
d-i user-setup/allow-password-weak boolean true

# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/Paris

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true

### Partitioning
## Partitioning example
# If the system has free space you can choose to only partition that space.
# This is only honoured if partman-auto/method (below) is not set.
# Alternatives: custom, some_device, some_device_crypto, some_device_lvm.
d-i partman-auto/init_automatically_partition select biggest_free

# Alternatively, you may specify a disk to partition. If the system has only
# one disk the installer will default to using that, but otherwise the device
# name must be given in traditional, non-devfs format (so e.g. /dev/sda
# and not e.g. /dev/discs/disc0/disc).
# In addition, you'll need to specify the method to use.
# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string lvm

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /var, and /tmp partitions
d-i partman-auto/choose_recipe select atomic


# This makes partman automatically partition without confirmation.
d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

### Package selection
tasksel tasksel/first multiselect ubuntu-desktop

# Individual additional packages to install
d-i pkgsel/include curl git chef-solo rvm build-essential
# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
d-i pkgsel/upgrade select full-upgrade

# Language pack selection
d-i pkgsel/language-packs multiselect de, en, fr

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note

# This will prevent the installer from ejecting the CD during the reboot,
# which is useful in some situations.
d-i cdrom-detect/eject boolean false

#### Advanced options
### Running custom commands during the installation
# d-i preseeding is inherently not secure. Nothing in the installer checks
# for attempts at buffer overflows or other exploits of the values of a
# preconfiguration file like this one. Only use preconfiguration files from
# trusted locations! To drive that home, and because it's generally useful,
# here's a way to run any shell command you'd like inside the installer,
# automatically.

# This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system.
d-i preseed/late_command string curl -sSL https://get.rvm.io | bash -s stable --ruby


```

I then ran the command ```
sudo mkisofs -R -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ~/Documents/modified-ubuntu.iso /tmp/iso
```.

I'm attempting to test this iso image with qemu by launching
```
qemu -cdrom ~/Documents/modified-ubuntu.iso -m 2048
```

After an awfully long time, I get the usual prompt "Install or Try live" but nothing remotely automatic I'm afraid. Any idea on what I could have done wrong ?

Thanks in advance !

---

### Post by ubfan1 on 2016-11-15
I'd suggest installing the qemu-kvm package and use kvm instead of qemu for some hardware acceleration -- you should notice a hugh difference in speed.  I have no experience with preseeding, other than being annoyed by it interfering with creating the install media with persistence.

---

