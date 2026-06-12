---
title: "strange thing at grub begs question: recover  ZFS with new install; possible?"
date: 2023-07-08
forum: Installation &amp; Upgrades
---

### Post by gbp00 on 2023-07-08
Installing new GPU from grub
Removed old drivers and cuda
$ sudo apt-get update
$ sudo apt-get dist-upgrade

After some time ends on and endless loop on this screen

[https://anonfiles.com/gfLcVf0azf/IMG_20230707_175046_931_jpg](https://anonfiles.com/gfLcVf0azf/IMG_20230707_175046_931_jpg)

Which is related to the dist-upgrade screenshot 
https://anonfiles.com/a1V6V30bz6/IMG_20230707_154519_545_jpg

Now when it boots to crypsetup and press ESC to get to grub, it runs the setup commands  (last screen shown)

[https://anonfiles.com/S6K6V209z7/IMG_20230707_170638_233_jpg](https://anonfiles.com/S6K6V209z7/IMG_20230707_170638_233_jpg)

, then "Oh No! Something has gone wrong and the system can't recover"

So I've lost grub access so can't install new driver, so asking if its possible to recover ZFS data... Without grub? Or can you debug this so driver can be installed?

 And not could you walk me through the ZFS recovery process on a new install? 

I am unskilled at Linux.

Thanks for your time :-)

---

### Post by MAFoElffen on 2023-07-08
Yes, it is possible. It is also possible to fix.

First, let me make some comments. When you do an update/upgrade process, if during the update the APT cache process, if you see errors where it cannot connect to something, as it did in the second screenshot ([https://cdn-150.anonfiles.com/a1V6V30bz6/5f01497f-1688846892/IMG_20230707_154519_545.jpg](https://cdn-150.anonfiles.com/a1V6V30bz6/5f01497f-1688846892/IMG_20230707_154519_545.jpg))... Then there is a problem where you should not go on with the upgrade process, until you correct that That is where you broke things in that process.

Boot from an Ubuntu Desktop LiveUSB install media. I noticed you have nVidia (your screen shots). Is that right? If so, the at the Grub2 Boot menu. press the <E> key, then <Arrow_Down> until you get to the line taht starts with :linux". <Arrow_Right> until you get to the words "quiet splash". Replace the word "quiet" with "---" (3 dashes). Then <Arrow-Right until after the word "splash", and add the word "nomodeset". Then press keys <Cntrl><X> to continue booting.

After it boots, Select "Try". Open a browser (FireFox) and get back to this post, so you can cut and paste commands from this post, into a graphical terminal window.

Select "Activities". Start typing "Terminal". Open a Graphical Terminal.

The following will be commands you enter
```

sudo su
apt update
LUKS_DEV="/dev/$(lsblk -e 7 -o name,fstype | grep 'crypto_LUKS' | cut -b 7- | awk '{print $1}' )"
apt install -y cryptsetup zfs-initramfs zfsutils-linux
cryptsetup open $LUKS_DEV luks1

```
Enter in your passphrase to unlock your encrpted LUKS volume.
```

zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool
zfs load-key -a
UUID=$(zfs list | grep -m 1 'rpool/ROOT/ubuntu_' | cut -b 19-24 )
zfs mount rpool/ROOT/ubuntu_$UUID
zfs mount bpool/BOOT/ubuntu_$UUID
zfs mount -a
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount -t tmpfs tmpfs /mnt/run
mkdir /mnt/run/lock
chroot /mnt /bin/bash --login
mount -a

apt update

```
You will be chrooted into the system...

Have to go to work. Will finsh these instruction when I get home.

---

### Post by gbp00 on 2023-07-08
Thanks for detailed response!

I tried the e key and down arrow, didn't stop failed boot.

Previously did:
Sudo apt autoremove cuda
Sudo apt autoremove nvidia-driver-xxx

I think that is all the drivers I have, so not sure why nvidia causing errors.

I'm using a legacy nvidia card in the PC now. Was keeping it in while I install new driver for AMD card.

 There's a  non-zero chance there's still a legacy driver, I cannot recall.

Hope to hear a follow up. Thanks!

---

### Post by MAFoElffen on 2023-07-09
Are you saying that it does not boot to a LiveUSB Install Flash drive? Or is that boot without it?

Because looking at the screen shots again tonight, it looks like it tries to boot, but that is stops at the boot status messages, at a point, right before the splash would start, right before the graphical login screen... It that right?

If so, at the point, what happnes if you press <Cntrl><Alt<F4>? Does it toggle to a vtty4 console screen, at the Console login?

Yo said a tempary NVidia GPU. Do you know the model?

---

### Post by gbp00 on 2023-07-10
OK I had mistaken a "tty terminal" for grub2. Now I have followed instructions, awaiting the continuation. 

Can I now run these commands for new GPU install?
amdgpu-install.readthedocs.io/en/latest

Thanks

---

### Post by MAFoElffen on 2023-07-10
Will answer this when I get home from work. On break, on my phone. In the meantime, the Kernel's open source module or the proprietary binary?

---

### Post by MAFoElffen on 2023-07-11
At home... So it sounds like it boots to a point where you can, at least get to a command prompt at a TTY without having to boot from a LiveUSB. It sounds like the prblem you are having is with your graphics driver.

From the command line, 
```

grep -m 1 'name' /proc/cpuinfo

```
Post the results within CODE Tags.

Then do
```

sudo modprobe amdgpu
sudo echo "amdgpu" >> /etc/module-load.d/modules.conf
sudo update-initramfs -u

```
start an editor to edit the Grub defaults file: 
```

sudo nano /etc/default/grub

```
Make these changes
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]--- [/COLOR]splash[COLOR=#ff0000] video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1[/COLOR]"
GRUB_CMDLINE_LINUX=""

```
Save and Exit: <Cntrl><O>, <Enter>, <Cntrl><X>.

Update Grub to pick up the changes
```

sudo update-grub

```
Reboot to test.

---

### Post by #&amp;thj^% on 2023-07-11
> **MAFoElffen said:**
> 
start an editor to edit the Grub defaults file: 
```

sudo nano /etc/default/[COLOR="#FF0000"]com[/COLOR]

```

Should that code read as "sudo nano /etc/default/grub"

---

### Post by MAFoElffen on 2023-07-11
> **1fallen said:**
> Should that code read as "sudo nano /etc/default/grub"
Yes. LOL. Corrected in previous post...

Need to PM you today...

---

### Post by #&amp;thj^% on 2023-07-11
> **MAFoElffen said:**
> 
Need to PM you today...
I'll be around on and off today.....working from home.

---

### Post by gbp00 on 2023-07-12
Have to reboot multiple times to get past the "F1 to continue, F2 setup utility, F5 diagnostics" screen on liveUSB for both GPU. 

New GPU has no signal with the splash edit / safe graphics splash edit / safe graphics 

Legacy works fine to boot liveusb

So that would change "amdgpu.noretry=0 amdgpu.dc=1"?

I'll await further instruction. 

"Kernel's open source module or the proprietary binary? " -- the latter or whichevers better.

Still unsure whether I can follow amd GPU  instructions after chrooting with legacy nvidia. 

Nvidia-driver-315 for legacy. 

Getting this error on
cryptsetup open $LUKS_DEV luks1
"Device /dev/ not compatible"


model name	: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz


Probably redundant, but:

ubuntu@ubuntu:~$ sudo modprobe amdgpu 
modprobe: ERROR: could not insert 'amdgpu': Invalid argument


&#128580;

---

### Post by gbp00 on 2023-07-13
Main problem is this

Getting this error on
cryptsetup open $LUKS_DEV luks1
"Device /dev/ not compatible"

---

### Post by MAFoElffen on 2023-07-13
Back up to square one...

When it boots one it's own (without trying to boot from a LiveUSB), it gets to this screen right? [https://cdn-150.anonfiles.com/gfLcVf0azf/4d3aec5c-1689273802/IMG_20230707_175046_931.jpg](https://cdn-150.anonfiles.com/gfLcVf0azf/4d3aec5c-1689273802/IMG_20230707_175046_931.jpg)

Please confirm or deny.

That is "past" the decryption process. That is just with having a problem starting the graphics layer. That is in the system, without the graphic drivers loaded...

Do you ever see the Grub2 menu?

---

### Post by gbp00 on 2023-07-15
Yes I can get to grub menu from normal boot. Sorry for confusion.

---

### Post by MAFoElffen on 2023-07-15
Now we are on the same picture of where it is at, and what it should be able to do.

At the Grub Boot Menu, press the <E> key. That will put grub into an edit mode, at the menu item that was highligted at the time.

Then cursor down with <Arrow-Down> to the line that starts with the word 'linux'. <Arrow-Right> to the words "quite splash".

Replace those words, with "--- 3". Then press the <Cntrl><X>  keys to continue booting.

That should get you to a Console, at a Login prompt...

This is where we can remove any graphics drivers that are casuing this, and install the graphics drivers you need...

Which is up to you. I am confused by what you did and where your goal is. Meaning, you said you wanted to do AMD Graphics, but those problems occurred, and you installed an old nVidia GPU... So is that card just temporary until you get the system up and reonstall the nVidia Card? Or just to the nVidia Card? Or have both going? 

Further meaning, it will boot, but you need to guide where you need to go from there.

---

### Post by gbp00 on 2023-07-18
I don't appear to have internet access at grub that isn't for Ubuntu updates? Usually have a killswitch on VPN, wasn't aware it was active between restarts (assuming that is the problem) & can't activate it through grub. Could you show how to access a .deb file downloaded to USB please, to install driver. 

Thank you!

---

### Post by MAFoElffen on 2023-07-18
Where you able to do anything from the instructions in Post #15? If so, then it would have booted to a command line console with your internet working, where you could remove the nVidia drivers and installed your amdgpu drivers... And at that kind of boot, since it was setup already with that, all your VPN drivers and such are already there right?

But I also asked in that post if that was what you wanted to do. You said that was your first goal, to install amdgpu drivers. But in the meanwhile, you insytalled nVidia GPU. So if is jumping around and I do not know what the current state is, to get you going.

So clarify what state it is in and where you need to go.

---

### Post by gbp00 on 2023-07-19
Yes still trying AMD GPU install. I can boot to grub but it won't ping websites from grub. So USB would be easy fix.

Install amd deb from USB I'm thinking. 
Please would you help with this?

---

### Post by MAFoElffen on 2023-07-19
I don't think you understand... I explain what to do, but you do not understand the instructions and what they give you to work with. I think you need an explanation of the process.

Your machine presently is booting, but without the graphics layer. So not to a point where you can do any changes. Getting to the grub menu, and into an edit mode of that menu, gives you the ability to edit the Linux 'boot line', to add parameters that will allow you to boot into a console, text-only mode, with a BASH prompt... That is the instructions I gave you, to be able to boot, where it will got from the first screen attached, to the last screen attached...

From that login prompt, I would log in with my username and password, then proceed to make the changes you need to do...

---

### Post by gbp00 on 2023-07-21
I think I did follow instructions and was able to login and unlock ZFS. The network issue remains. Even turning kill switch off doesn't allow to ping a website. Clearly this is uncommon issue. Nothing has changed with network setup 

Please will you provide USB instructions to install .deb. Thank you.

https://anonfiles.com/db5asa3az1/_20230720_153202_JPG

https://anonfiles.com/ed58sf36z4/_20230720_153039_JPG

---

### Post by MAFoElffen on 2023-07-21
What the Heck?

You said you see the Grub menu right?

At the Grub Menu, select the "Advanced Options"... Arrow to an older kernel with "recovery" options. Press the <E> key. It should be similar to this:
```

linux   "/BOOT/ubuntu_5ylu87lu87@/vmlinuz-5.15.0-53-generic" root=ZFS="rpool/ROOT/ubuntu_5ylu87" ro recovery nomodeset dis_ucode_ldr

```
Press keys <Cntrl><X> to boot.

Select "network" to enable networking and mounting the filesystem. Select "root" to drop to a root prompt...

First off... You said you wanted amdgpu instead of nVidia, yet your output messages shown in the pictures show not just nvidia drivers, but also Cuda drivers?

Remove and purge them
```

apt remove --purge nvidia-*

```
Next, get where your sysfs stores cstate information, so we can use the correct grub boot parameter

Next, edit your /etc/default/grub file
```

nano /etc/default/grub

```
Then change "hidden" to "menu" and the timeout time from "0" to "3". add "intel_idle.max_cstate=4" to the boot parameters after "quiet boot". Save and exit, then run 
```

update-grub

```
Then do this
```

sudo modprobe amdgpu
sudo echo "amdgpu" >> /etc/module-load.d/modules.conf
sudo update-initramfs -c -k all

```
Then reboot

Note: If you cannot get into your system through trying to boot through the rescue option... This morning I tried my old instructions for chroot'ing into Ubuntu ZFS encrypted (installed via the default install script) and it didn't work as it did before. I had to break in and change my old instructions... I will post those in the next post for how to do that now.

---

### Post by MAFoElffen on 2023-07-21
Here is my new amended instructions:
```

sudo su -

zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool

cryptsetup open /dev/zvol/rpool/keystore zfskey
# Enter passphrase for /dev/zvol/rpool/keystore: 


lsblk -e7 -o name,label,size,fstype
NAME     LABEL                   SIZE FSTYPE
sr0      Ubuntu 22.04 LTS amd64  3.4G iso9660
zd0                              500M crypto_LUKS
&#9492;&#9472;zfskey keystore-rpool          484M ext4
vda                               30G 
&#9500;&#9472;vda1                           512M vfat
&#9500;&#9472;vda2                           1.4G crypto_LUKS
&#9500;&#9472;vda3   bpool                   1.5G zfs_member
&#9492;&#9472;vda4   rpool                  26.7G zfs_member


ls /dev/mapper
# control  zfskey

mount /dev/mapper/zfskey /media
ls /media
# lost+found  system.key

cat /media/system.key | zfs load-key -L prompt rpool
# <No ouput indicates that it unlocked without an error>


zfs mount $(zfs list | awk '/rpool\/ROOT\/ubuntu_...... / {print $1}' )
zfs mount $(zfs list | awk '/bpool\/BOOT\/ubuntu_...... / {print $1}' )
zfs mount -a


zfs list
#NAME                                               USED  AVAIL     REFER  MOUNTPOINT
#bpool                                              270M  1010M       96K  /mnt/boot
#bpool/BOOT                                         269M  1010M       96K  none
#bpool/BOOT/ubuntu_5ylu87                           269M  1010M      269M  /mnt/boot
#rpool                                             9.65G  16.0G      192K  /mnt
#rpool/ROOT                                        9.00G  16.0G      192K  none
#rpool/ROOT/ubuntu_5ylu87                          9.00G  16.0G     5.35G  /mnt
#rpool/ROOT/ubuntu_5ylu87/srv                       192K  16.0G      192K  /mnt/srv
#rpool/ROOT/ubuntu_5ylu87/usr                       580K  16.0G      192K  /mnt/usr
#rpool/ROOT/ubuntu_5ylu87/usr/local                 388K  16.0G      388K  /mnt/usr/local
#rpool/ROOT/ubuntu_5ylu87/var                      3.65G  16.0G      192K  /mnt/var
#rpool/ROOT/ubuntu_5ylu87/var/games                 192K  16.0G      192K  /mnt/var/games
#rpool/ROOT/ubuntu_5ylu87/var/lib                  3.64G  16.0G     3.48G  /mnt/var/lib
#rpool/ROOT/ubuntu_5ylu87/var/lib/AccountsService   212K  16.0G      212K  /mnt/var/lib/#AccountsService
#rpool/ROOT/ubuntu_5ylu87/var/lib/NetworkManager    260K  16.0G      260K  /mnt/var/lib/NetworkManager
#rpool/ROOT/ubuntu_5ylu87/var/lib/apt              98.2M  16.0G     98.2M  /mnt/var/lib/apt
#rpool/ROOT/ubuntu_5ylu87/var/lib/dpkg             61.3M  16.0G     61.3M  /mnt/var/lib/dpkg
#rpool/ROOT/ubuntu_5ylu87/var/log                  10.4M  16.0G     10.4M  /mnt/var/log
#rpool/ROOT/ubuntu_5ylu87/var/mail                  192K  16.0G      192K  /mnt/var/mail
#rpool/ROOT/ubuntu_5ylu87/var/snap                 2.64M  16.0G     2.64M  /mnt/var/snap
#rpool/ROOT/ubuntu_5ylu87/var/spool                 276K  16.0G      276K  /mnt/var/spool
#rpool/ROOT/ubuntu_5ylu87/var/www                   192K  16.0G      192K  /mnt/var/www
#rpool/USERDATA                                     142M  16.0G      192K  /mnt
#rpool/USERDATA/mikeferreira_hsfoy4                 142M  16.0G      142M  /mnt/home/mikeferreira
#rpool/USERDATA/root_hsfoy4                         360K  16.0G      360K  /mnt/root
#rpool/keystore                                     518M  16.5G     63.4M  -

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run

cd /mnt
chroot /mnt /bin/bash --login
mount -a

```
That , in a line after "#", is either sample output or added notes...

---

### Post by gbp00 on 2023-07-23
OK excellent! The grub edit didn't fix the broken boot but the liveUSB chroot worked. Obligatory naive question: what're the next steps from here? 

Can I install AMD .deb after mount -a, or is this for transfering files to new install?

Thank you for your patience.

---

### Post by MAFoElffen on 2023-07-23
The amdgpu driver is inside the kernel...

Look at Post #21. The instructions there will uninstall the nVidia drivers ad load the amdgpu module to the kernel.

---

