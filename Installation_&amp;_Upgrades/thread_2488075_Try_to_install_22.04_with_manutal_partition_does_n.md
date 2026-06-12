---
title: "Try to install 22.04 with manutal partition does not work"
date: 2023-06-22
forum: Installation &amp; Upgrades
---

### Post by kessl on 2023-06-22
Hi
I try to install ubuntu 22.04 on a 1 TB nvme ssd with manual partition but when I am done setting up the partitions and press install now I get an error message 30 sec later that it is not able to mount 3rd partition - root, that is the only error message I get. I set the partitions up as follows, maybe you can spot my mistake:
400mb ESP
1GB ext4 - "/boot"
64GB encrpyt - ext4 - "/"
800GB encrypt - ext4 - "/home"
16 GB encrypt - swap

Does anybody sport an error? I dont seem to find a good manual on patitioning. Does /boot maybe need to be bigger? Or ext2? Or is EFI too small?

Thanks
Regards
Dieter

---

### Post by Rubi1200 on 2023-06-22
Hi and welcome to the forums :-)

From a liveUSB run the boot info script (in my signature) and post the results here so we can get a better overview of the situation. Do not try and repair anything, just the link with the script results.

---

### Post by MAFoElffen on 2023-06-22
From the LiveUSB, use "Try" and do this:
```

lsblk -e7 -o name,mountpoint,size,fstype,type

```
Copy  the output. Go back to the thread here, in the post section select "Go  Advanced"... In the post editor menu selct the "#" icon to insert CODE  Tags... Paste the output within those tags.

Do the same for this, copy the whole code and paste it into a terminal command prompt, then press <Enter>
```

nvme_list=$(ls -la /dev/disk/by-id | \
    grep 'nvme' | \
    grep -v 'part' | awk '{print $9}' )

for nvme_disk in ${nvme_list}
do
    sudo sgdisk -p /dev/disk/by-id/$nvme_disk
    echo "..."
done

```
If you are trying to  install manually within LUKS containers... They have to be completely  setup before you go to "Do Something Else" (Manual) in the installer.  Even then, after the installer is through, if it had installed without  error), after the install, you will have to setup the cyptab and  keyfile, before you shut down and reboot the install. Usually, if you are installing using the manual option, using LUKS containers,  you have to prep the disk, setting up those LUKS containers, prior to starting the partitioner, so that the partitioner recognizes those preconfigured containers.

Unfortunately, if you are using the 23.04 ISO... which uses Snap ubuntu-desktop-installer, that will not work. The partioner in that ISO does not recognise pre-configured LUKS, LVM2, ZFS or BTRFS container (correctly). So it will help if you tell us which release of Ubuntu you are trying to install.

What I see  that will cause you problems later, is size of your containers. I would  give your ESP a minimum of 750MB, and when I create /boot partitions, I  usually make them between 1.5GB to 2GB.

---

### Post by MAFoElffen on 2023-06-22
It will not let me edit the previous post... I forgot to say that the LUKS containers also need to be "unlocked" previous to starting up the partitioner...

Sidenote: If you did use the Lunar 23.04 ISO and had this problem, please join this BUG as "Affect's me" and add a comment: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

I know that Bug says "LVM"... But it affects that the partitioner is not filesystem nor volume manager aware, so it does not recognize whether LVM2, LUKS, ZFS and BTRFS volume managers are setup already, which for a lot of us, this is the meat and potatoes of installing other than default installations. 

This is a major to concern to me, and I feel this should be fixed before the next LTS release.

If it did not affect you, please spread the word on this Bug, to get more people joining this Bug. The more people that say they are affected or concerned with this, the more weight will be applied to get this fixed.

If you need help setting up LUKS containers in an other than default install installation, please let us know, so I can point you to previous posts, where I dealt with that, that has instructios on how to do that... That might save you a lot of work, and/or give you ideas on how that is done.

After thought-- What filesystem and/or volume manager will you be using within those LUKS containers?

---

### Post by kessl on 2023-06-23
Well, I tried to install Ubuntu on 2 different PCs and it is the same on  both. If I try to install with encrypted root and separate encrypted  home the installation fails. If I install with an encrypted root only,  no problem.
After quiet some time spent trying to install this  distro, I decided that ubuntu is not for me. Thanks for trying to help  anyways, but this installer is fundamentally broken and I am not looking  for something to make my life harder.

@Rubi: I don't have a problem with booting, I have a problem with installing.
@Mafo:  Trying to install Ubuntu, I don't even have a concole to enter your  command. And I don't really see an option to unlock a luks partitions  after hitting "try to install". That should have been hint enough, "try  to install", all other distros just say "install" and then they do it  instead of trying and failing.

---

### Post by ActionParsnip on 2023-06-23
Does your BIOS not support legacy boot? If it does then you don't need UEFI and then won't need the [COLOR=#E8E6E3]ESP.[/COLOR]

---

### Post by MAFoElffen on 2023-06-23
> **kessl said:**
> @Mafo: Trying to install Ubuntu, I don't even have a concole to enter your command. And I don't really see an option to unlock a luks partitions after hitting "try to install". That should have been hint enough, "try to install", all other distros just say "install" and then they do it instead of trying and failing.
In the installer, Hotkey: <Alt><F2> toggles to a command prompt.

If you reread my posts, I said that the easiest way to install LUKS encrypted partitions is to create then from the command line. Unlock the containers. The start the installer. Not from the installer. 

The default "encrypted" script is for a basic install on LVM2 with an encrypted root. (Not a separate encrypted home)... So info is needed what you tried outside of that, and what you expected what you did, for what to happen.

You still did not tell us which release of Ubuntu you tried to install. That piece of information is very important.

You may think you explained what you did to cause your problem... But the details of that are just not in your post. More info needed.

I install, test, and use various distributions, from RedHat, Fedora, SUSE, Oracle Linux, CentOS Stream, Kaisen, Alpine, Arch, Slackware, Debian, Ubuntu, Mint, PopOS, etc. What I described on how to install within LUKS containers, is fairly universal to all. I do support fro Linux as a whole, not just Ubuntu.

What you just explain, will fail in the way you tried that, for any distro. Except maybe for Kaisen, which has the scripting to add a separated home, and optionally being encrypted.

I think if you understood how the pieces work, you would understand how they fit together, and what needs to happen when, which piece come first, next, etc.

What I would suggest, is:
1. Start with the Ubuntu Desktop 22.04.2 LTS ISO. And stay with an LTS release. Even if you go to another Flavor or even another distro, stay with an LTS release.

2. Whether you stay with Ubuntu, or go somewhere else, when you post to their Forum, don't go there close minded and shut out. Be open-minded. Make it easy for others to help you. If you want help, people on Forums volunteer their time to help other users. We don't get paid. If someone suggests something or requests information on your system, or on what you did, have the courtesy to either answer their questions, or answer why you decline with that.

3. Outside of this Forum, I have been an IT Consultant and have been doing computer support for over 33 years. I charge my customers for my advice. If you don't want free advice, that is just foolish.

Honestly. Sincerely. You will not find another Community like this. The people here do care, are knowledgeable, and they are here to help others. You have not done anything here to try "anything" to help yourself. Have you? It sounds like you came here to complain and lash out. That is on you.

If you had provided some of the information asked for, answered some questions and actually let people help you, you would be on your way to a working system that your have plans for. Instead, you closed doors for yourself. You sound a bit frustrated. I feel that frustration, and am sorry you feel that way.

If that is not what you meant, then I would start over and reword what you want and expect... 

*** I asked you if you needed help in how to do this. I asked if you wanted to see instructions. Do you need help? What specifically is your plan? What did you do that failed? (Try to be specific in the steps you took.)

---

### Post by TheFu on 2023-06-24
I've always found that fixing storage AFTER the default "Use Encryption + LVM" install option is used is the easiest way.   Just be certain to reduce the "root" LV very soon after the base install finishes.  I do it before I install anything else.  They typical Encryption + LVM setup will use LVM so there's only 1 partition that is encrypted.  This creates a single LUKS container for an LVM PV, VG and as many LVs inside the VG as you like. No limits, except for how much storage you use.  

See the attached diagram. That's a simple setup with LVM. See how everything except the UEFI and boot are outside the LUKS container, but the OS and all data are inside it?

I haven't look at 22.04 encryption, so the diagram is what I did for 18.04, but I doubt much has really changed.  Hopefully, they are using GPT now, not MBR partitions, but besides that, should be similar.  Also, if you use LVM, move the swapfile in /swapfile into an LV for swap.

---

### Post by MAFoElffen on 2023-06-27
The is for the OP, kessl and TheFu... TheFu had mentioned that he was interested in doing LUKS with the Keys on a USB FlashDrive. That spun up some interest with me as a challenge.

I haven't created any LUKS machines since 22.04. I decide to spin up some machines with 22.04.2 to see if anything changed, and to be able to give more detailed instructions to the OP. This is a manually installed, LVM2 on LUKS2 recipe:
```

### Encryted LUKS with LVM2
[code]
# Become root
sudo su

# Create an alias variable, as a shortcut to typing it out each time
DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
echo -e "Disk found: $DISK"


# This is a USB for my keyfile
USB=$(ls -l /dev/disk/by-id | awk '/usb/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
echo -e "USB found: $USB"


DEST=/keystore/luks.key
mkdir /keystore
mount $USB-part1 /keystore
openssl genrsa -out $DEST 4096
chmod -v 0400 $DEST
chown root:root $DEST


# Partition the disk 
sgdisk  -n1:1M:+750M -t1:EF00 -c1:EFI  $DISK  # Create EFI partition
sgdisk  -n2:0:+2G    -t2:8300 -c2:BOOT $DISK  # Create Boot partition
sgdisk  -n3:0:+25G   -t3:8309 -c3:ROOT $DISK  # Create Root partition
sgdisk  -n4:0:0      -t4:8309 -c4:HOME $DISK  # Create Home partition

# Display partition table
sgdisk -p $DISK


# Format EFI partition
mkfs.vfat -F 32 -s 1 -n EFI ${DISK}-part1

# Format Boot partition
mkfs.ext4 -L BOOT ${DISK}-part2


# Create LUKS2 container and format for ROOT (part3)
cryptsetup luksFormat --type luks2 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part3

cryptsetup luksAddKey ${DISK}-part3 $DEST

cryptsetup luksConvertKey --key-slot 0 --pbkdf pbkdf2 ${DISK}-part3
cryptsetup luksConvertKey --key-slot 1 --key-file /keystore/luks.key --pbkdf pbkdf2 ${DISK}-part3


cryptsetup luksOpen ${DISK}-part3 luks1

# Create LUKS2 container and format for HOME (part4)
cryptsetup luksFormat --type luks2 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part4

cryptsetup luksAddKey ${DISK}-part4 $DEST

# cryptsetup luksConvertKey --ke***** 0 --pbkdf pbkdf2 ${DISK}-part4
# cryptsetup luksConvertKey --ke***** 1 --key-file /keystore/luks.key --pbkdf pbkdf2 ${DISK}-part4

cryptsetup luksOpen ${DISK}-part4 luks2

# Encrypted LVM root and swap inside LVM lv_root

# Verify that keys are set in the ke*****s
sudo cryptsetup luksDump ${DISK}-part3 
sudo cryptsetup luksDump ${DISK}-part4

# Create LVM2
pvcreate /dev/mapper/luks[2,3]

vgcreate vg_ubuntu /dev/mapper/luks1
vgcreate vg_home /dev/mapper/luks2

lvcreate -L+6G      -n lv_swap vg_ubuntu 
lvcreate -l 80%FREE -n lv_root vg_ubuntu
lvcreate -l 80%FREE -n lv_home vg_home

### 
# Leave that terminal session open...
#
# Start up installer. When it gets to the partition stage, choose "Something else"...
#
# Select /dev/sda1. Change. Use as EFI filesystem.
#
# Select /dev/sda2 (Linux device-mapper (crypt)). Change. Use as ext4, /boot.
#
# Select /dev/mapper/vg_ubuntu-lv_root (Linux device-mapper (crypt)). Change. Use as ext4, format, /.
#
# Select /dev/mapper/vg_home-lv_home. Change. Use as ext4, format, /home.
#
# Select /dev/mapper/vg_ubuntu-lv_swap. Change
#
# Continue Install. At completion, DO NOT REBOOT. Instead choose "Continue # Testing".
#
# Go back to the open terminal session, which you are still root...
###
mkdir -p /target
MapMount=$(ls /dev/mapper/vg_ubuntu-lv_root)
mount $MapMount /target
for DIR in proc sys dev /etc/resolv.conf; do mount --rbind /$DIR /target/$DIR; done
chroot /target
mount -a

## Reset Var's inside chroot
DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
USB=$(ls -l /dev/disk/by-id | awk '/usb/ {print "/dev/disk/by-id/"$9}' | head -n 1 )


blkid | grep 'sda\|sdb' | grep -e 'crypto_LUKS\|SWAP' | awk '{print $1 " " $2 " " $4}' | sort
# copy that output to an editor...


## Add UUID's to crypttab
echo -e "# <name>  <device>     <password>     <options>" >> /etc/crypttab
echo -e "#luks1 UUID=\"$(blkid -s UUID -o value ${DISK}-part3)\" none luks" >> /etc/crypttab
echo -e "luks1 UUID=\"$(blkid -s UUID -o value ${DISK}-part3)\" /keystore/luks.key luks" >> /etc/crypttab 
echo -e "#luks2 UUID=\"$(blkid -s UUID -o value ${DISK}-part4)\" none luks" >> /etc/crypttab
echo -e "luks2 UUID=\"$(blkid -s UUID -o value ${DISK}-part4)\" /keystore/luks.key luks" >> /etc/crypttab

grep . /etc/crypttab


## fstab
mkdir /keystore
echo -e "UUID=$(blkid | awk -F [\ =] '/sda1/ {print $7}') /keystore     vfat  defaults,umask=0077  0 2" >> /etc/fstab
mount /keystore


## Add this line to /etc/default/grub
echo -e "GRUB_ENABLE_CRYPTODISK=y" >> /etc/default/grub
update-grub

sudo nano /etc/cryptsetup-initramfs/conf-hook
## Uncomment and change this line to:
KEYFILE_PATTERN="/keystore/*.key"


### RESCUE (chroot into system from LiveUSB)
sudo su

DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
USB=$(ls -l /dev/disk/by-id | awk '/usb/ {print "/dev/disk/by-id/"$9}' | head -n 1 )

mkdir /keystore
mount ${USB}-part1 /keystore
DEST=/keystore/luks.key

cryptsetup luksOpen ${DISK}-part3 luks1 --key-file $DEST
cryptsetup luksOpen ${DISK}-part4 luks2 --key-file $DEST

pvscan
vgscan
lvscan

mount /dev/mapper/vg_ubuntu-lv_root /mnt
for DIR in proc sys dev /etc/resolv.conf 
do 
    mount --rbind /$DIR /mnt/$DIR 
done
chroot /mnt

mount -a

####


# fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg_root-lv_root /               ext4    errors=remount-ro 0       1
#/dev/mapper/luks1 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=3B24-07E9  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vg_home-lv_home /home           ext4    defaults        0       2
#/dev/mapper/vg_swap-lv_swap none            swap    sw              0       0
/dev/mapper/vg_swap-lv_swap none swap defaults 0 0
UUID=09660ab9-d621-4752-b1f7-fc1e7118979a  /boot       ext4    defaults      0       2
UUID="4987-2A68"    /keystore    vfat    defaults 0 2

## This is to tell intramfs that it is okay to store key-file abstract info in the initramfs files.
nano /etc/cryptsetup-initramfs/conf-hook
# Change this:
KEYFILE_PATTERN="/keystore/*.key"


```
The trick to get it to work with Grub2 and get it to boot was to change the root containers key slot format from PKDF from type argon2id to type pbkdf2...

I once I figured that out, then I can also encrypt furhter the recipe for an encrypted /boot. Further for TheFu's use, you can dd copy the LUKS2 continer headers to partitions on the USB Key, then zero out the header in the containers... Then in the cryttab, tell it where to use the header from... That will make your laptop "useless" without your USB key being plugged in at boot.

@TheFu -- PM me if you want the details of that. Remember me mentioning that if you had access to the LUKS header, that there was way, to decrypt it (with a some work)? That would take that possibility out of the picture. 

I had fun. LOL

---

### Post by TheFu on 2023-06-28
I use yubikeys to unlock my LUKS stuff. It wasn't hard to setup long ago. Since I haven't been traveling internationally in a few years, I haven't setup this stuff recently.

The easy way. Just boot from a small SSD that you keep on a chain around your neck. 2242 SSDs are small and there are USB enclosures for those.  Or use a microSD card. Those are huge these days and some people use them for over a year with a standard Linux install and don't have any issues. A guy in my LUG has been booting MX Linux from small USB flash storage for 5 yrs now. He claims the storage has never failed.  I've had a few flash storage devices fail, but they usually last years.  Been using microSD storage for raspberry pi OSes for at least 5 yrs.  Only had 1 microSD fail (8GB Patriot) and that was after 4 yrs of 24/7 use. I definitely got my value from it. I've been using 32G, 64G and 128G Samsung Endurance PRO microSD for everything the last few years. No failures.  Outside the r-pi use, I really don't re-write that much data to the devices, so wear leveling isn't any issue that I've seen, so far.

Or for travel to places with not-so-nice borders, using a microSD for the entire OS (encrypted storage, of course) is pretty easy. SanDisk says a microSD can go through a laundry cycle unharmed. That opens lots of possibilities for transport.  </spy hat>   Certain "western" countries have laws that allow them to demand unlock keys for storage like we'd expect from dictatorships. I prefer crossing into them through neighbor countries with nice border agreements to avoid the customs search hassle, if possible. I've only been searched in detail when leaving other countries headed home. Sometimes those searches have been rather nasty - I call it molestation - in 1 situation leaving eastern Europe. Only once has a computer been checked and I can't recall anybody really looking at the extra storage I brought for use in cameras. Putting an encrypted OS microSD into a camera bag with 10 other microSDs with assorted "travel photos", wouldn't get a second look.

I don't think all these manual steps are really necessary for my needs.

---

