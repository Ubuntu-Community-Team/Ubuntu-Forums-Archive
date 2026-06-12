---
title: "Reinstall boot loader"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by darkjedi8359 on 2005-08-16
Greetings, I have been using ubuntu for a few months now and have had no troubles. I don't have any troubles right now with ubuntu right now other than I just had to reinstall windows xp. Usually I would search for the answer, but how can I get the boot loader reloaded? I remember seeing posts about it in recent searches but I can't remember posts names, and can't get the search feature here to work. Everytime I try I get a blank page.

---

### Post by heimo on 2005-08-16
If it's grub, something like this should do:
[http://www.ubuntuforums.org/showpost.php?p=301715&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=301715&postcount=4")

If it's lilo, boot Live-CD, mount your root partition (just like in post above), change directory to mount point, change root, run lilo.
 ```

sudo mkdir /mnt/hda2
sudo mount /dev/hda2 /mnt/hda2
cd /mnt/hda2/
sudo chroot . 
sudo lilo

```


EDIT: If it's default Hoary install, it's Grub.

---

### Post by darkjedi8359 on 2005-08-16
[QUOTE=heimo]If it's grub, something like this should do:
[http://www.ubuntuforums.org/showpost.php?p=301715&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=301715&postcount=4")

If it's lilo, boot Live-CD, mount your root partition (just like in post above), change directory to mount point, change root, run lilo.
 ```

sudo mkdir /mnt/hda2
sudo mount /dev/hda2 /mnt/hda2
cd /mnt/hda2/
sudo chroot . 
sudo lilo

```


EDIT: If it's default Hoary install, it's Grub.[/QUOTE]
 thanks, I will give that a try :)

---

### Post by darkjedi8359 on 2005-08-16
This is what happens when I try th grub-install,
 ```
ubuntu@ubuntu:~$ sudo grub-install --config-file=/mnt/hdb1/boot/grub/menu.lst /dev/hda
sudo: grub-install: command not found

```

---

### Post by heimo on 2005-08-16
Ok. You could either try /sbin/grub-install or /mnt/hda2/sbin/grub-install (or what-ever the path to the directory where you mounted root is).

---

### Post by darkjedi8359 on 2005-08-16
getting closer,
 ```
ubuntu@ubuntu:~$ sudo /mnt/hdb1/sbin/grub-install --config-file=/mnt/hdb1/boot/grub/menu.lst /dev/hda
Unrecognized option `--config-file=/mnt/hdb1/boot/grub/menu.lst'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help			  print this message and exit
  -v, --version		   print the version information and exit
  --root-directory=DIR	install GRUB images under the directory DIR
						  instead of the root directory
  --grub-shell=FILE	   use FILE as the grub shell
  --no-floppy			 do not probe any floppy drive
  --force-lba			 force GRUB to use LBA mode even for a buggy
						  BIOS
  --recheck			   probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
``` I tried "--grub-shell=FILE" :
 ```
ubuntu@ubuntu:~$ sudo /mnt/hdb1/sbin/grub-install --grub-shell=/mnt/hdb1/boot/grub/menu.lst /dev/hda
//lib/grub/i386-pc/stage1: Not found.
```
I think we are getting closer, was I right in using grub-shell?

---

### Post by heimo on 2005-08-16
I'm not familiar with grub, but maybe you could try this recipe:
  ```
sudo mkdir /mnt/hda2
sudo mount /dev/hda2 /mnt/hda2
cd /mnt/hda2/
sudo chroot . 
sudo grub-install /dev/hda
```
Assumes hda2 is root partition with /boot directory and installing grub to master boot record of hda.

I'm uncertain if this will work.

---

### Post by darkjedi8359 on 2005-08-16
it seems to have worked, thank you for your help :).

---

