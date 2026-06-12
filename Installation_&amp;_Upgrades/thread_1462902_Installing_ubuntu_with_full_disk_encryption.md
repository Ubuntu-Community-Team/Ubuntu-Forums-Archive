---
title: "Installing ubuntu with full disk encryption"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by paolinox on 2010-04-26
Hi, I have a problem I'm trying to solve regarding full disk encryption. I'm experimenting with lucid lynx rc, I have kms and plymouth working with very nice graphics and blazingly fast boot time.

I'm currently running an archlinux installation that does exactly this:

- the root filesystem resides on a cryptsetup ( no luks ) encrypted disk without partitions ( yeah I encrypted /dev/sda not /dev/sda1 )
- the boot medium is a usb pendrive with kernel, initramfs and syslinux

What I have made with arch is putting the encrypt hook in the hooks list in /etc/mkinitcpio.conf ( HOOKS="base udev autodetect pata scsi sata usb usbinput encrypt filesystems" ) and modified the encrypt hook script as follows

```

run_hook ()
{
    /sbin/modprobe -a -q dm_crypt >/dev/null 2>&1
    /sbin/modprobe -a -q ext4 >/dev/null 2>&1
    /sbin/modprobe -a -q sha256_generic >/dev/null 2>&1
    /sbin/modprobe -a -q sha512_generic >/dev/null 2>&1
    /sbin/modprobe -a -q aes_x86_64 >/dev/null 2>&1
    /sbin/modprobe -a -q aes_generic >/dev/null 2>&1
    /sbin/modprobe -a -q xts >/dev/null 2>&1
    /sbin/modprobe -a -q dm_mod >/dev/null 2>&1
  
    if [ -e "/sys/class/misc/device-mapper" ]; then
        if [ ! -c "/dev/mapper/control" ]; then
            read dev_t < /sys/class/misc/device-mapper/dev
            /bin/mknod "/dev/mapper/control" c $(/bin/replace "${dev_t}" ':')
        fi

        /sbin/cryptsetup -c aes-xts-essiv:sha256 -h sha512 -s 512 create cryptodisk /dev/sda
        export root="/dev/mapper/cryptodisk"
    fi
}

```

This script runs at some point during the bootstrap and mounts the encrypted disk and inform the system that root is /dev/mapper/cryptodisk. Fairly simple.

I want to do something like this on Ubuntu. I have found two tutorials. The first is [http://www.c3l.de/linux/howto-completly-encrypted-harddisk-including-suspend-to-encrypted-disk-with-ubuntu-6.10-edgy-eft.html](http://www.c3l.de/linux/howto-completly-encrypted-harddisk-including-suspend-to-encrypted-disk-with-ubuntu-6.10-edgy-eft.html)

It says that I must add an entry to /etc/crypttab and then rebuild the initramfs. Very simple and in fact it doesn't work. During the bootstrap the system halts after saying it has executed the scripts in scripts/local-top ( where the cryptoroot script resides ). I suspect the cryptoroot script is not executed at all by the system.

The second tutorial is [https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)

It says I must add an hook file and a script file to /etc/initramfs-tools. I made it, upgraded the initramfs and reboteed. It starts cryptsetup ( that asks for the password ) during the bootstrap sequence.

The only problem is that I cannot type the password because at that point in the bootstrap sequence there's no support for usb keyboard I guess. Also I cannot use quiet and splash options because cryptsetup uses text mode to ask for password ( I want a graphical box like the default box ubuntu shows for luks encrypted filesystems ).

What I don't understand is how hook scripts can be activated/deactivated and how the system selects their correct execution order.

With arch I have this line 

HOOKS="base udev autodetect pata scsi sata usb usbinput encrypt filesystems"

Note the usbinput ( needed to type the password with a usb keyboard ) prior to encrypt. The hooks are executed in the order they're listed. On Ubuntu I guess the PREQS do the trick.

Also how can I say to the system "start the cryptoroot script at boot"?

---

### Post by onyxrev on 2010-05-02
I believe I have a similar issue which I've been documenting here:

[http://ubuntuforums.org/showthread.php?t=1469161&highlight=luks](http://ubuntuforums.org/showthread.php?t=1469161&highlight=luks)

My setup is LUKS but has some similar weirdness regarding the keyboard.

---

