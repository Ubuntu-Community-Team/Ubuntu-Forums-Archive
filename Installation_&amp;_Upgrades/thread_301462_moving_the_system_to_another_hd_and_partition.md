---
title: "moving the system to another hd and partition"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by akraix on 2006-11-17
Hi, 

i am trying to move an ubuntu installation from one partition to another. it is an upgraded edgy eft. i hope this fits into this category, else please feel free to move the thread. 

this is what i did for the complete system: 

tar cpf - /old/hd/mountpoint | (cd /mnt/new/partition ; tar xpf - )

after that i did a chroot into this newly created old root system.

once this has been finished i edited /etc/fstab. here i the uuids, after doing some research i found what they are etc. vol_id -u <partition> does not work (i tried due to my curiousity) and i am perfectly happy with the old approach, so i substituted the uuids for devicenames again. 

after that i substituted the uuids in grub's menu.lst as well and adjusted it to the new partition scheme.

when i tried to run grub grub-install /dev/hda i ran into problems: 

```
/sbin/grub-install: 404: sort: not found
/sbin/grub-install: 404: uniq: not found
/dev/hda: Not found or not a block device.

```

then i found 

```
 sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda 
```
but that does not do anything here, 
/dev/hda: No such file or directory

sfdisk: Fatal error: cannot find /dev/hda
/dev/hda: No such file or directory

sfdisk: cannot open /dev/hda for reading
[/code]

i am not really sure what this is for, though. as i don't have anything i can lose on this new hd i tried it, hoping it won't ```
rm -rf /
``` ;-).

and now i found the real problem: 

```
ls: /dev/hd*: No such file or directory
```

there are no device files for hd*! 

i do have a quick running install of ubuntu on another partition. could i somewhat take those /dev/hda* over to the system i really want to use? 

is there anything else i need to do after that? 

any help is appreciated, 

akraix

---

### Post by swamytk on 2006-11-17
Before chrooting, mount the devfs (/dev) in new root's dev directory as shown below:
mount -t devfs devfs /mnt/new/partition/dev

---

### Post by akraix on 2006-11-17
hi, 

thanks for the suggestion. 
should be great, unfortunately ... 
```
mount -t devfs devfs /mnt/hda2/dev/
mount: unknown filesystem type 'devfs'
```
akraix

---

### Post by yota on 2006-11-17
Hi,

device filesystem support has been removed from the kernel, by the way I suppose you don't need to chroot at all:
> 
root@linbook:/home/yota# grub-install -h
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

just tell grub to install itself in the correct --root-directory and you're done!

If you want to chroot anyway you can bind (do this before the chroot) the chroot dev to the real system dev:
```

mount --bind /dev /mnt/hda2/dev/

```

Hope this helps

---

### Post by hal10000 on 2006-11-17
instead of mounting devfs filesystem you can try to mount udev:> sudo mount -t tmpfs udev /mnt/hda2/dev
sudo mkdir /mnt/hda2/dev/pts
sudo mkdir /mnt/hda2/dev/shm
sudo mount -t devpts devpts /mnt/hda2/dev/pts
sudo mount -t tmpfs devshm /mnt/hda2/dev/shm

and don't forget to mount /proc:

sudo mount -t proc proc /mnt/hda2/proc
sudo mount -t binfmt_misc binfmt_misc /mnt/hda2/proc/sys/fs/binfmt_misc

(maybe you can omit the last step)
I guess the most relevant thing is to use udev instead of devfs.
After doing that you can chroot and do the things you like.

---

### Post by akraix on 2006-11-17
ok, got it up and running again now. 
thanks to everyone involved! 

another solution would have been in this case to edit the temporary system's menu.lst to include the transferred system and then boot into that. this might work for some people reading this. anyway, i got it quite the way i wanted in order to learn. 

akraix

---

