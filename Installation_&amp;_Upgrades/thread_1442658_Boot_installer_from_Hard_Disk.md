---
title: "Boot installer from Hard Disk"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by elaich1988 on 2010-03-30
Hi,
I want to install ubuntu 9.10 DVD, I have the iso image, so i try to boot the installer from hard disk by adding this lines to my menu.lst.


```
title Install Ubuntu
kernel (hd0,0)/install-ubuntu/vmlinuz
initrd (hd0,0)/install-ubuntu/initrd.gz
```

i extract the two files (vmlinuz and initrd.gz) from install folder in my DVD 

so when i reboot the system and i choose install ubuntu from grub startup screen, i have this message:
```
error 13: invalid or unsupported executable format
```

I will appreciate your help !! thanks x)

---

### Post by sisco311 on 2010-03-30
[uhelp]community/Installation/FromLinux[/uhelp]

---

### Post by pavilonfi on 2010-03-30
Hello,
I am new to Linux, Ubuntu and this forum :) I tried to install Ubuntu 9.10 with the [community/Installation/FromLinux]("http://help.ubuntu.com/community/Installation/FromLinux") method. I had a WinXP partition and an old faulty Ubuntu 5.10. I used the latter to  create the ISO partition and configure grub. I could boot into the mounted ISO, and after the Live version started I run the installer from there. I created a new ext4 partition for 9.10 and let it install grub2, too. That was my last success :S

After reboot, the grub2 interface shows up without an option to boot into the new system. Only the old Ubuntu and WinXP are in the list (the ISO boot option is missing, too). 

If I boot into the old Ubuntu, I can bring back the grub menu and after reboot I can use the ISO again. From there I tried to update and install grub2 (using chroot, update-grub, grub-install) but the best result I can get is the grub2 interface as it was after the installation (WinXP, old Ubuntu options).

From grub I cannot boot into the new system because of the ext4 filesystem. From grub2 I cannot boot into the new system, because we (me and grub2) cannot find a vmlinuz* on the new partition (I checked it from the Live version, too). 

I hope you understand me :) Can you give me a hint how to proceed? Thx!

ps. I tried to upgrade grub to grub2 under Ubuntu 5.10, but it could not find the package, I don't know whether there is no such package for 5.10 or my 5.10 broke down so much.

---

### Post by sisco311 on 2010-03-30
> **pavilonfi said:**
> 
I hope you understand me :) Can you give me a hint how to proceed? Thx!


Boot the ISO, chroot into Ubuntu 9.10 and upgrade the system:
```
sudo apt-get update
sudo apt-get upgrade
```

Hopefully, the upgraded grub will recognize the new installation. If not, then post the output of:
```
sudo cat /boot/grub/grub.cfg
```
```
sudo blkid
```
and
```
ls -al /boot
```
  
PS: I use this script to chroot:
```
#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="/dev/sda1"

# mount point of the new root partition
MOUNT="/mnt/lucid"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf"

# list of additional devices and their mount pont. 
# device names must be separated by the mount point with a colon:
# i.e. /dev/sda2:/home 
AMOUNT=""

# user name
UNAME="sisco"

############################################################################
# start the chroot environment                                             #
############################################################################

# add user to the list of allowed users to make connections to the X server.
sudo -u $USER xhost SI:localuser:$UNAME

# create the mount point & mount the root partition
mkdir -p $MOUNT
mount $ROOT $MOUNT

# mount the virtual filesystems & resolv.conf to enable the network
for i in $ARGS; do
  mount --bind /$i $MOUNT/$i
done 

# mount additional partitions:
for i in $AMOUNT; do
  mkdir -p ${MOUNT}${i//*:/}
  mount ${i//:*/} ${MOUNT}${i//*:/}
done

# chroot into the linux installation
chroot $MOUNT su - $UNAME 

```edit the variable section before you run it.

---

### Post by pavilonfi on 2010-03-30
Thank you for your reply!

I had do some network configuration (to have this page on the target machine), some work to get into the Live Ubuntu, some google to understand how to create and run a script file but I finished. 

It seems there are some errors in the first step. I changed the values in your script to

ROOT="/dev/sda7"
MOUNT="/mnt/koala"
UNAME="ubuntu"

The output:

ubuntu@ubuntu:~$ sudo ./chroot-script.sh
localuser:ubuntu being added to access control list
mount: mount point /mnt/koala/etc/resolv.conf does not exist
Unknown id: ubuntu

I tried mount to see what happened:

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sda6 on /cdrom type ext3 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda7 on /mnt/koala type ext3 (rw)
/dev on /mnt/koala/dev type none (rw,bind)
/dev/pts on /mnt/koala/dev/pts type none (rw,bind)
/proc on /mnt/koala/proc type none (rw,bind)
/sys on /mnt/koala/sys type none (rw,bind)

I continued with sudo chroot /mnt/koala (seems OK, 'root@ubuntu:/#'), tried sudo apt-get update but it failed probably because of the resolv.conf error ('could not resolve proxy....'). 
I tried sudo mount --bin /etc/resolvconf/ /mnt/koala/etc/resolvconf/ as well, before chroot, I had the same result. I can ping servers by name, but I cannot download the updates. Should I set the proxy somewhere after chroot?

Edit: no,  I cannot ping by name after chroot.

---

### Post by sisco311 on 2010-03-30
> **pavilonfi said:**
> Should I set the proxy somewhere after chroot?


Yeh, but I don't know how. Instead of that, let's try to create a custom grub menu entry for the new Ubuntu installation.

In the chroot environment, edit the /etc/grub.d/40-custom file:
```
nano /etc/grub.d/40-custom
```
and append it with:
```

menuentry "Ubuntu 9.10"{
        recordfail
        insmod ext2
        set root='(hd0,7)'
        linux   /boot/vmlinuz-**<version-number>**-generic root=/dev/sda7 ro quiet splash
        initrd  /boot/initrd.img-**<version-number>**-generic
}

```

replace the **<version-number>** with the actual version of the kernel (run: *ls /boot* to find it out). Save the file and exit (Ctrl+x, y, Enter).

run:
```
update-grub
```

Reboot and see if you can boot in Ubuntu 9.10. If yes, then upgrade your system.

---

### Post by pavilonfi on 2010-03-30
In the meanwhile, after chroot:

root@ubuntu:/# ls -al /boot
total 10736
drwxr-xr-x  3 root root    4096 2010-03-30 03:43 .
drwxr-xr-x 21 root root    4096 2010-03-30 03:43 ..
-rw-r--r--  1 root root  629174 2009-10-16 20:03 abi-2.6.31-14-generic
-rw-r--r--  1 root root  111371 2009-10-16 20:03 config-2.6.31-14-generic
drwxr-xr-x  2 root root    4096 2009-10-28 22:03 grub
-rw-r--r--  1 root root 8404794 2010-03-30 03:43 initrd.img-2.6.31-14-generic
-rw-r--r--  1 root root  128796 2009-10-23 18:11 memtest86+.bin
-rw-r--r--  1 root root 1664737 2009-10-16 20:03 System.map-2.6.31-14-generic
-rw-r--r--  1 root root    1196 2009-10-16 20:06 vmcoreinfo-2.6.31-14-generic

root@ubuntu:/# ls -al /boot/grub/
total 8
drwxr-xr-x 2 root root 4096 2009-10-28 22:03 .
drwxr-xr-x 3 root root 4096 2010-03-30 03:43 ..

-> cat /boot/grub/grub.cfg fails

root@ubuntu:/# sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9828A9FF28A9DC8E" TYPE="ntfs" 
/dev/sda3: LABEL="/" UUID="eb20a8b1-284d-4767-8698-a10861fa130e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="FE9C6D199C6CCDA9" LABEL="M-Zj kM-vtet" TYPE="ntfs" 
/dev/sda6: UUID="91d38e94-a665-4d91-8a01-aa958820e071" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="f72559b0-2cbc-4a9e-87d8-0f12c06a8e79" TYPE="ext3" 
/dev/sda8: UUID="29d80513-cd37-4b0f-98df-5a25f32d9b9c" TYPE="swap" 
/dev/sda9: UUID="e66f252c-24ad-40b0-b1e2-e1a5187d56f8" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap"



Edit:  there is no grub.cfg, no vmlinuz, no ideas. If it helps: to use the Live Ubuntu, I boot into the old 5.10, then: sudo grub, root(hd0,2), setup(hd0), quit grub, reboot.

---

### Post by sisco311 on 2010-03-30
That's kinda odd, it looks like sda9 is the Ubuntu 9.10 partition.

Edit the variables to:
ROOT="/dev/sda9"
MOUNT="/mnt/karmic"
UNAME="root"

The network manager generates the resolv.conf file. So set up the network before you chroot and run the script again.

the 40-custom file should look like:
```

...
menuentry "Ubuntu 9.10"{
        recordfail
        insmod ext2
        set root='(hd0,9)'
        linux   /boot/vmlinuz-<version-number>-generic root=/dev/sda9 ro quiet splash
        initrd  /boot/initrd.img-<version-number>-generic
}
```

---

### Post by pavilonfi on 2010-03-30
In fact, both sda7 and sda9 are (should be) Ubuntu 9.10, sda7 is a second try on ext3. I checked both for /boot/grub/* and /boot/vmlinuz*. Nothing.


ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda8 swap swap defaults 0 0

---

### Post by pavilonfi on 2010-03-30
I changed the variables (sda9, root, karmic) , rerun the script, same error with resolv.conf, but the chroot command is now successful in the script. I don't know how to setup the network (I'm using it now). Before chroot, I can resolve names to IPs from terminal, after chroot I cannot. Thank you for your efforts!

---

### Post by sisco311 on 2010-03-30
> **pavilonfi said:**
> In fact, both sda7 and sda9 are (should be) Ubuntu 9.10, sda7 is a second try on ext3. I checked both for /boot/grub/* and /boot/vmlinuz*. Nothing.


Did the installation complete without errors? It looks like that the kernel and grub are not installed & the fstab is not configured properly.

EDIT: when you run the ls commands, you are in the chroot, right?

Never tried the LiveCD ISO, but the Alternate CD ISO always worked for me without any problems.

---

### Post by pavilonfi on 2010-03-30
I think there were no errors during the install. At the end, I had the choice to continue trying Live or restart machine. Telling the truth, there was a warning at the beginning: if I have my installer on the target drive I will not be able to create partitions. But since I already had the partitions I ignored that. And I had to umount  /cdrom before the last step of the installer wizard (I read that in a forum after I got an error for the first time). 

I think I start from scratch tomorrow. Can you tell me a 'best practice', if I have this configuration (broken old Ubuntu, Live CD partition, WinXP etc) and I want to install from the Alternate CD and I want keep at least the WinXP part untouched?

Edit: yes, I was in chroot when listing the directories.

---

### Post by elaich1988 on 2010-03-31
Hi,
I followed the instructions in here [https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") 
I have the iso image for ubuntu dvd so i created a 5 GB new ext3 partition ("/dev/sda3") i mounted it:
```
mount -t ext3 /dev/sda3 /media/dvd
```
after that i copied the iso :
```
cp /home/ubuntu-9.10-dvd-i386.iso /media/dvd
```
i downloaded the initrd.gz and vmlinuz files from [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/]("http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/")
and copied them to /media/dvd 
then i unmount the partition :
```
umount /media/dvd
```

so i added this lines to my menu.lst:

```
title install ubuntu
root (hd0,2)
kernel          /vmlinuz root=/dev/ram ramdisk_size=1048576 rw
initrd          /initrd.gz
```
i saved, and reboot.

the installation begins and stops in ("Scan hard drives for an installer ISO image") step:

```
While one or more possible ISO images were found, they did not look like valid installer ISO images.

You'll have to use an alternative installation method, or try again after you've fixed the ISO image
```

i don't know what i have to do .. can anybody help me pllzz :p

---

### Post by sisco311 on 2010-03-31
@elaich1988

If you use that method, then you need the Alternate ISO image. Download it via bittorent, it's much faster than the direct download:  [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

Oh, and you don't need a separate partition, just copy the ISO, vmlinuz & initrd.gz to the root of your current installation.

The Alternate ISO uses a text based installer, it's easier to create the partition(s) you need for the new installation with GParted.

EDIT: Just tested it. It looks like you _must_ create the partition(s) for Ubuntu 9.10 before you boot the installer.

When the installer asks you if you want to unmount the mounted partitions, select NO. At the partitioning screen select Manual partitioning & select the root, swap... partitions.

---

### Post by elaich1988 on 2010-03-31
the installation success with the alternative iso, but the results are not very good.

i had mandriva 2010 in my disk, now when the installation is finihsed, in my grub screen i can see my mandriva but if i choose it, or any other entry like "install ubuntu" i have this error:
```
error: You need to load the kernel first.
```

and when i choose ubuntu, i have only a text environment, :/

what can i do ? pleaze

---

### Post by sisco311 on 2010-03-31
Use Grub2's CLI to boot Mandriva:
[uhelp]community/Grub2#Command%20Line%20&%20Rescue%20Mode[/uhelp]
Reinstall Mandriva's Grub & create an entry for Ubuntu.

At some point of the installation you are prompted to install additional packages. Did you select ubuntu-desktop? Can you start the GUI with the *startx* command?

---

