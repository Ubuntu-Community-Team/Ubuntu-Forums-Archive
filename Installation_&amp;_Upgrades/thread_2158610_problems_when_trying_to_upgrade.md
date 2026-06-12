---
title: "problems when trying to upgrade"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by rizos on 2013-06-29
when i try sudo apt-get upgrade i get this message and cant install anything at all.


```
The following packages will be REMOVED:
  linux-image-3.2.0-43-generic-pae
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 113 MB disk space will be freed.


(Reading database ... 202946 files and directories currently installed.)
Removing linux-image-3.2.0-43-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-43-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-48-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-45-generic-pae...
/usr/sbin/extlinux-update: 328: /usr/sbin/extlinux-update: tr: not found
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
Generating grub.cfg ...
/etc/grub.d/10_linux: 35: /etc/grub.d/10_linux: tr: not found
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
/etc/grub.d/10_linux: 1: /etc/grub.d/10_linux: tr: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-43-generic-pae.postrm line 328.
dpkg: error processing linux-image-3.2.0-43-generic-pae (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.2.0-43-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by DeathByDenim on 2013-06-29
It can't find the command "tr"? That's pretty odd. What happens when you type this in the terminal:
```
which tr
```

Also, you can try this to fix apt with this command:
```
sudo apt-get -f install
```
, but it might just spew out the same errors again.

---

### Post by rizos on 2013-06-29
which tr... brings nothing.

and sudo apt-get -f install, brings the same errors over and over.

last thing i was doing before this issue was the ubuntu tewak, janitor tool to removoe old kernel. 


since then no way to fix it.

---

### Post by DeathByDenim on 2013-06-29
Hmm, yeah. "tr" is kind of essential for the post-remove script. "tr" is usually located in /usr/bin. Can you still find it there?

It's part of the coreutils package, so maybe reinstalling that will help. Is it still possible to do
```
apt-get install --reinstall coreutils
```
or will apt-get refuse to do that?

---

### Post by rizos on 2013-06-29
tr is not on /usb/bin folder...

and apt-get install --reinstall coreutils wont work, it does not let me install anything at all.

---

### Post by DeathByDenim on 2013-06-30
You can try downloading the coreutils package manually from [http://packages.ubuntu.com/precise-updates/coreutils](http://packages.ubuntu.com/precise-updates/coreutils) (assuming you were using 12.04 precise, you can select your distribution on the top of the page)
On that page you need to click on either amd64 if you have a 64-bit operating system or i386 otherwise.
Then install it by typing
```
sudo dpkg -i coreutils_8.13-3ubuntu3.2_amd64.deb
```
(or coreutils_8.13-3ubuntu3.2_i386.deb for 32-bit)

It sounds like your system is rather messed up though, so you might want to consider doing a fresh reinstall.

---

### Post by rizos on 2013-06-30
i was trying to make a fresh install and by mistake i did got to install ubuntu deleting all the disk, fortunately i was able to rescue the partition table via testdisk, i had dual windows7/ubuntu 12.04. i can see my files via sudo ecryptfs-recover-private. but there is no way i can copy them into a usb so i can reinstall and get my pc working again (says i dont have the permission to copy such files). i had a partition for windows 7, a partition just for ubuntu OS, another for swap and last one for all my files (music. photos etc etc). i tried to fix the MBR for windows via Boot-repair and got mess some how as i cant bring the windows partiton back. and the regular ubuntu partition wont work, keep telling me something about monitor resolution and cant go any further. so my files are there, i know the partition table is there. how can i bring back the system as it was, so later on i can re-install ubuntu on the partition for the OS. 

any help will be extremely appreciated. 

here is the full out put of partition table via boot repair. [http://paste.ubuntu.com/5815124/](http://paste.ubuntu.com/5815124/)

---

### Post by DeathByDenim on 2013-06-30
Ah, so your files were encrypted then?
Do you use the live-CD to boot your system now?
And then you run sudo ecryptfs-recover-private to get at your files again?
I have never used ecryptfs before, but according to the help, it mounts the encrypted files and makes them accessible in a temporary directory, in the form of /tmp/ecryptfs.XXXXXXXX.
But when you try to copy from there, you get access denied? Did you try copying it to a USB stick using sudo?

---

### Post by rizos on 2013-06-30
*ecrypted files?* **yes**
*use live cd?*** yes**
*ecryptfs-recover-private?* **yes**
i try getting the files with sudo nautilus then going to /tmp/ecryptfs.XXXXXXXX. and i have access to my files, theya re there all of them, but when i copy the files and try to paste them/drag-drop to another folder in another usb it says i dont have the permissions.

is there a way to make the partition come back and be recognized by gparte and ubuntu?.

hope i can get my files back.

---

### Post by DeathByDenim on 2013-07-01
Ah, I see. Maybe the files are only readable for root. In that case you won't be able to copy them using drag-and-drop. Can you try
```
sudo cp -r /tmp/ecryptfs.XXXXXXXX /media/usb
```
where you need to replace /media/usb with the directory where you mounted your usb stick?

---

### Post by rizos on 2013-07-01
cp: cannot create directory `/media/cdrom/ecryptfs.0kyUSFWb': Read-only file system

this is what i get running the command.

---

### Post by rizos on 2013-07-01
cp: cannot create directory `/media/cdrom/ecryptfs.0kyUSFWb': Read-only file system

this is what i get with the command.

---

### Post by DeathByDenim on 2013-07-01
It looks like you are trying to copy your data to a CD? That's indeed not possible. I thought you were trying to copy it to a usb stick. /media/cdrom usually refers to the cd-player.
 When you plug in the USB stick, you can look at the contents, right? What does this command say then:
```
ls -l /media
```
?

---

### Post by rizos on 2013-07-01
total 0
lrwxrwxrwx 1 root root 6 Jul  1 19:44 cdrom -> /cdrom

this is the out put... but also the cdrom is where usb stickis mounted, i try to copy to a usb no doubt.

---

### Post by DeathByDenim on 2013-07-01
Wow, that's weird. Can you create files at /media/cdrom ? It sounds like the problem is not with ecrypt giving unreadable files, but with your destination being read-only.

---

### Post by rizos on 2013-07-01
i cannot!... how can i change the destination read only mode

---

### Post by rizos on 2013-07-01
finally i work it out, sudo su then nautilus surf to media which is a usb stick and then i was able to copy my files, have no idea why the other usb stick was read only. now i think i will have to do a whole new install on my system, this is the odd part gparted wont reconize any partition at all, but when i start up pc it gives me the option to boot into windows 7 or ubutntu, ubuntu is completely broken and it wont load, windows by the other hand loads pretty normal, how can i install ubuntu on the partition designtaed for with out loosing windows 7 partition, gparted shows one 500gb unallocated space and ubuntu live cd only shows delete entire disk option.

---

### Post by DeathByDenim on 2013-07-01
Doesn't the Ubuntu installer show something like this ( [http://blog.gambliser.com/wp-content/uploads/2012/03/install-ubuntu-12-04-3.jpeg](http://blog.gambliser.com/wp-content/uploads/2012/03/install-ubuntu-12-04-3.jpeg) ) though?
If you choose "Something else", I think you should be able to choose the unallocated space.

---

### Post by rizos on 2013-07-03
yes it does then it shows 500 gb of free space, i did manage to get my files back and do a fresh install.

---

