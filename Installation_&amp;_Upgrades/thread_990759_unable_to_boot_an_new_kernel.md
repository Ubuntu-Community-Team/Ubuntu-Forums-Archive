---
title: "unable to boot an new kernel"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2008-11-23
Hi..i am using ubuntu 7.10 distro...in that the preinstalled kernel is "linux-2.6.22-14 generic"...after that i planned to compile an new kernel...so i downloaded from kernel.org....the new kernel which i download is "linux-2.6.22.14"...so i compiled that new kernel an d\tried to install...so that i followed the below steps

#cd /usr/src/linux-2.6.22.14
#make menuconfig
#make
#make modules
#make modules_install
#make install

after this commands i opened this /boot/grub/menu.lst and i added the below lines extra which i given in the block letters...

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ef4f8ec-7dd3-4c02-9f24-c9438e6b8bce ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ef4f8ec-7dd3-4c02-9f24-c9438e6b8bce ro single
initrd /boot/initrd.img-2.6.22-14-generic

title My Custom Kernel
root (hd0,0)
kernel /boot/vmlinuz-2.6.22.14 root=/dev/hda1 ro

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

but now i am unable to boot from new kernel..when i select the new kernel means i am getting the following error

starting up.....
uncompressing linux...ok,booting the kernel
[ 53.987716]kernel panic - not syncing: VFS : unable to mount root fs on unknown -block(0.0)

so i dont know what to do...can any one suggest me what to do and how to do...cause i am new to linux...

---

### Post by cdtech on 2008-11-23
Did you run:
```
update-initramfs -c -k  $(uname -r)
```
"uname -r" being the new kernel you compiled....
Then add the image below your new kernel line:
```
initrd /boot/initrd.img-2.6.22-14
```

Hope this helps.......

---

### Post by shariefbe on 2008-11-23
when i put **update-initramfs -c -k $(linux-2.6.22.14)** i am getting this below error 
 
root@sharief-desktop:/usr/src/linux-2.6.22.14# update-initramfs -c -k $(linux-2.6.22.14)
bash: linux-2.6.22.14: command not found
No arg for -k option
Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]   Specify kernel version or 'all'
 -c             Create a new initramfs
 -u             Update an existing initramfs
 -d             Remove an existing initramfs
 -t             Take over a custom initramfs with this one
 -b             Set alternate boot directory
 -v             Be verbose
 -h             This message

---

### Post by cdtech on 2008-11-23
Don't put your kernel in a variable state (no $ parenth)...

---

### Post by shariefbe on 2008-11-23
sorry i cant understand...variable state means?how to do that command?suggest me

---

### Post by cdtech on 2008-11-23
Like such:
```
sudo update-initramfs -c -k linux-2.6.22.14
```

---

### Post by shariefbe on 2008-11-23
see when i type this comand which you gave in last post..

[B]sharief@sharief-desktop:/usr/src/linux-2.6.22.14$ sudo update-initramfs -c -k linux-2.6.22.14
[sudo] password for sharief:
update-initramfs: Generating /boot/initrd.img-linux-2.6.22.14
Cannot find /lib/modules/linux-2.6.22.14
update-initramfs: failed for /boot/initrd.img-linux-2.6.22.14[/B]

it is telling that cannot find linux-2.6.22.14 but see the below 

[B]sharief@sharief-desktop:/usr/src/linux-2.6.22.14$ cd /
sharief@sharief-desktop:/$ cd /lib/modules/
sharief@sharief-desktop:/lib/modules$ ls
2.6.22.14  2.6.22-14-generic
sharief@sharief-desktop:/lib/modules$[/B]

what to do now?

---

### Post by cdtech on 2008-11-23
When you compiled your kernel you didn't do &#8220;make modules_install&#8221; after compilation.

---

### Post by shariefbe on 2008-11-23
No..i done that steps....i didnt miss that step...see in my first post...i have typed what are all things i done....

---

### Post by shariefbe on 2008-11-23
No..i done that steps....i didnt miss that step...see in my first post...i have typed what are all things i done....

---

### Post by shariefbe on 2008-11-27
For the sake i installed the new kervel version 2.6.26..i will tell the steps which i done here..

step 1)tar -xzvf linux-2.6.26.tar.gz

step 2)cd linux-2.6.26

step 3)make menuconfig
(I didnt do any changes)

step 4)make

step 5)make modules_install

step 6)make install

After i typed this i got the following things

sh /home/sharief/Desktop/linux/linux-2.6.26/arch/x86/boot/install.sh 2.6.26 arch/x86/boot/bzImage System.map "/boot"
In order to use the new kernel image you have just installed, you
will need to reboot the machine. First, however, you will need to
either make a bootable floppy diskette, re-run LILO, or have GRUB
installed.

Checking for ELILO...No

GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.26
root@sharief-desktop:/home/sharief/Desktop/linux/linux-2.6.26# 

After that i did

step 7)# cp arch/i386/boot/bzImage /boot/bzImage-2.6.26

step 8)# cp System.map /boot/System.map-2.6.26

step 9)vi /boot/grub/menu.lst

in that i edited as

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ef4f8ec-7dd3-4c02-9f24-c9438e6b8bce ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ef4f8ec-7dd3-4c02-9f24-c9438e6b8bce ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, kernel 2.6.26 ie new one
root (hd0,0)
kernel /boot/vmlinuz-2.6.26 root=UUID=7ef4f8ec-7dd3-4c02-9f24-c9438e6b8bce ro quiet splash

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

when i reboot the system i entered in to new kernel i am getting this error

starting up.....
uncompressing linux...ok,booting the kernel
[ some number]kernel panic : not syncing; VFS; Unable to mount root fs on unknown-block (0,0)

for your kind information the content of /boot is

abi-2.6.22-14-generic memtest86+.bin
bzImage-2.6.26 sarge.bmp
coffee.bmp sid.bmp
config Syatem.map-2.6.26
config-2.6.22.14 System.map
config-2.6.22-14-generic System.map-2.6.22.14
config-2.6.26 System.map-2.6.22-14-generic
config.old System.map-2.6.26
debian.bmp System.map.old
debianlilo.bmp vmlinuz
grub vmlinuz-2.6.22.14
initrd.img-2.6.22-14-generic vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak vmlinuz-2.6.26
initrd.img-linux-2.6.22.14 vmlinuz.old

what to do now?

---

### Post by cdtech on 2008-11-27
You need to make initrd:
```
mkinitrd -o /boot/initrd.img-2.6.26 vmlinuz-2.6.26
```
Then you need to add that to your menu.lst file:
```
title Ubuntu 7.10, kernel 2.6.26 ie new one
root (hd0,0)
kernel /boot/vmlinuz-2.6.26 root=UUID=7ef4f8ec-7dd3-4c02-9f24-c9438e6b8bce ro quiet splash
**initrd /boot/initrd.img-2.6.26**
```

**UPDATE::.**
An initrd image is needed for loading your SCSI module at boot time or if you are compiling the kernel with ext3 support as a module.

---

### Post by shariefbe on 2008-11-27
when i typed the command  **mkinitrd -o /boot/initrd.img-2.6.26 vmlinuz-2.6.26** i am getting the below error...

**bash: mkinitrd: command not found**

---

### Post by cdtech on 2008-11-27
Sorry, try this command:
```
sudo update-initramfs -c -k all
```

---

### Post by shariefbe on 2008-11-27
see what happened....

sharief@sharief-desktop:~$ sudo update-initramfs -c -k all
[sudo] password for sharief:
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
sharief@sharief-desktop:~$ mkinitrd -o /boot/initrd.img-2.6.26 vmlinuz-2.6.26
bash: mkinitrd: command not found
sharief@sharief-desktop:~$

---

### Post by forcumang on 2008-11-27
> **shariefbe said:**
> see what happened....

sharief@sharief-desktop:~$ sudo update-initramfs -c -k all
[sudo] password for sharief:
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
sharief@sharief-desktop:~$ mkinitrd -o /boot/initrd.img-2.6.26 vmlinuz-2.6.26
bash: mkinitrd: command not found
sharief@sharief-desktop:~$

he told you to run 'sudo update-initramfs -c -k all', as a correction to 'mkinitrd ...', using that second command has no reason. your top update worked flawless.

---

### Post by shariefbe on 2008-11-27
yes i done that...yet i didnt get any initrd image for new kernel...

---

### Post by cdtech on 2008-11-27
Try to run it with your kernel version instead of "all" and see what errors if gives you, something is wrong here, it should have givin you the initrd.

---

### Post by shariefbe on 2008-11-27
yes got it cdtech....Thanks a lot...Thank you very much.......regards

---

### Post by cdtech on 2008-11-27
Your welcome.

Good luck....

---

### Post by shariefbe on 2008-11-27
now i got the new kernel compiled...can you tell me how to set time for menu.?cause every time i am pressing escape to enter in kernel m

---

### Post by cdtech on 2008-11-27
I sent it to you.

Good luck........

---

