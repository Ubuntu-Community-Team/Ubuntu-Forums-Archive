---
title: "create recovery boot option"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by cjohnpritchard on 2016-03-30
Hi all,

I am setting up a PC using the OEM installer for a customer.

I want to add a boot option, which on selection would boot using a separate partition to do a "factoy reset" where they would be back to the initial end-user configuration.

is there any facility for this? has this been done (I tried googling but didn't find anything similar)?

If not then does anyone have any pointers in the right direction?

many thanks

---

### Post by oldfred on 2016-03-30
I use grub2's loopmount to directly boot the ISO. But have had issues with unmounting /device/ISO which even when installing from sdb to sda is mounted on sda.

But saved this as Dell seems to do something similar as a recovery on its Linux installed systems.
 Dell with Ubuntu pre-installed loopmount ISO for recovery (see pastebin)
[http://askubuntu.com/questions/739763/grub2-issue-ubuntu-will-not-boot-unless-i-type-exit-from-grub-menu](http://askubuntu.com/questions/739763/grub2-issue-ubuntu-will-not-boot-unless-i-type-exit-from-grub-menu) 

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

Pastebins seem to have a limited life. So posting Dell ISO recovery boot stanza.

```
### BEGIN /etc/grub.d/99_dell_recovery ###
menuentry "Restore Ubuntu 14.04 to factory state" {
        search --no-floppy --hint '(hd0,msdos3)' --set --fs-uuid 30E1-4FA3
        set uuid_options="uuid=30E1-4FA3"
        if [ -s /factory/common.cfg ]; then
            source /factory/common.cfg
        else
            set options="boot=casper automatic-ubiquity noprompt quiet splash"
        fi
        #Support starting from a loopback mount (Only support ubuntu.iso for filename)
        if [ -f /ubuntu.iso ]; then
            loopback loop /ubuntu.iso
            set root=(loop)
            set options="$options iso-scan/filename=/ubuntu.iso"
        fi
        if [ -n "${lang}" ]; then
            set options="$options locale=$lang"
        fi

        linux   /casper/vmlinuz.efi dell-recovery/recovery_type=hdd $uuid_options $options 
	initrd	/casper/initrd.lz
}
### END /etc/grub.d/99_dell_recovery ###
```

---

### Post by cjohnpritchard on 2016-03-30
i'm guessing the ubuntu.iso is an unnatended install image then?

I'll have a play with it this evening

---

### Post by oldfred on 2016-03-30
I would think it cannot be totally unattended, but I have never tried to create an ISO.
Probably like an OEM install, but then user later has to add name & password?

 OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
Perform end-user configuration after initial OEM installation 
 sudo apt-get install oem-config-gtk

---

### Post by yancek on 2016-03-30
A factory reset such as used in a windows recovery partition is a pretty extreme measure used when all else fails.  It is basically the same as a new install as any new software that you have installed as well as any data on the system partition is also gone.  If you have personal data on a separate partition you will, or at least should still have that.  You can easily put an Ubuntu iso on a separate partition and boot it to install to another (the original) partition.  The problem is that if your install is bad and you can't boot, it's useless.  The same with windows and a recovery partition, if your bootloader is messed up it is also useless, you won't be able to access it.  The process of running the recovery partition will probably take as long as a new install of Ubuntu.

---

### Post by oldfred on 2016-03-31
to Yancek point that is why with two drives I have a full install with boot files on second drive.
And then also have flash drives with full install and/or ISO files to boot system or boot repair ISO.

I always thought it was belt and suspenders, but answer on Jeopardy (TV quiz show) was Belt & Braces.  Or I like to have multiple ways to boot system, just in case.

Might be easier just to provide flash drive with full boot capability.

---

