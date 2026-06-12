---
title: "problem with grub: the system is not loaded"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by ubunlilluz on 2010-07-02
hi,
i've installed Ubuntu 10.4 on my new pc. This pc has 2 sata hd configured in raid 0 and a third hd pata (set to master)  that comes from my old computer that is with ubuntu 10.4 too.
At beginning i tried to install without the pata hd, but i couldn't install the grub because grub has problem with raid.
With the pata hd added and chosen as the site of the grub the installation ends correctly but when i reboot the system stops on the screen "loading operating system"

If can be usefull to understand my system, the pata hd as i said was the one of my old computer and contains still ubuntu 10.4 directories (/, swap, home) because i haven't formatted therm because the home is full of data i'd want to move on my new pc.

Is there somebody so kind to help me to solve it?
thanks

---

### Post by ronparent on 2010-07-03
As I have told others, each Ubuntu release has had it own quirks with regards to installing on a raid. The 10.04 desktop release does come with dmraid which allows you to access your raid (apparently '/dev/mapper/isw_chibcceegh_Volume0'). The quirks are 1)that gparted run from 10.04 will not work on a raid partition and the partitioning step of the installation will fail 2) that the installer will try to install the grub boot loader to /dev/sda and that if this is one of your raid drives, that will fail.

The workarounds I have used are to:

1) pre-format (ext2, ext3 or ext4, it doesn't matter) the target partition with an earlier version of Ubuntu, either installed or live cd. The catch is that you must have dmraid installed or install it. This can be done to a live cd session if you have internet capability - gparted will not see the raid or its partitions unless the raid drives are activated by dmraid.

To install dmraid in a terminal - Code:

Quote:
> sudo apt-get install dmraid
To activate the raid - Code:

Quote:
> sudo dmraid -ay

You now can start gparted (System>Administration>Gparted or Partition Disks depending on the version your running from) and select an unallocated space to create your target sized as you want it - or resize an existing partition to give you unallocated space in which to create your partition in. You will also have to create a swap partition if there is not already one present. We probably don't have to address it here, but if you already have two or more partitions on this array, you should create additional partitions in an extended partition (you are currently limited to four total primary partitions including an extended partition on any drive). Note the name of this partition. Once your pre-formated partitions is created on the raid you can boot into your 10.04 live cd. 

At this point you pick the desktop icon to start the installation of 10.04. When you reach step 4 of 7 you will pick the option to manually specify the partition you have previously formatted to install to. When step 5 of 8 appears, select your partition and click 'change' at the bottom of the window. In the box select the format from the drop box choices (probably ext3 or ext4, same as what you previously formated). Do NOT check to format. In the next drop down select '/' - the mount point you file system is to be installed to.

2) To hopefully handle the 2nd quirk, at step 8 of 8 you will click on the box labeled 'Advanced'. At this point you should be able to select the top array name (the name representing the entire array, not one of the partitions) from a drop box. After this you have done everything you can do. You can click next and you system will be setup on the chosen partition. I have just run into the problem in Mint where this was not adequate. The installer still tried to install to sda and resulted in a 'fatal failure'. If you need or want to boot from the raid and this happens don't despair - it can still be fixed. Just continue to install without the boot loader. Unfortunately I have consequently learned that this last step is likely to fail! If you don't have another install on your system that can update grub to boot into your new install, you can use the chroot command from a live cd terminal to install grub2 to the raid. Look to this site for guidance: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html) Just be sure to use the raid drive (the entire drive not one of the partitions) as the target for the grub bootloader - in the form of 'grub-install /dev/mapper/<YourRaidDrive>'. Hint look in /dev/mapper/ for the name.

As you can tell, raid in Ubuntu is not for the faint hearted or under informed. It is doable. You will have to do some learning along the way. If you are going to try and stick with it, I or others will be able to help along the way.

---

### Post by ubunlilluz on 2010-07-03
thank you, today i'll try

---

### Post by ubunlilluz on 2010-07-04
oops i've a lapsus (ok i'm getting old)

i've to create 3 partition:

\
swap
home

the \ is a primary one ok i'm sure, but swap and home are primary or extended?
thanks

---

### Post by ronparent on 2010-07-04
It makes little difference. Because of the limitation to 4 primary (including the extended), I generally put them all in extended.

---

### Post by ubunlilluz on 2010-07-05
hi
it worked, yesterday i installed it in the raid 0. I created instead 3 primaries partitions and it worked.
thanks

---

### Post by ronparent on 2010-07-05
Glad to hear it worked out. Just a little curiosity - did yousetup the boot from a raid0.

---

