---
title: "crypstetup can't find my encrypted source device after upgrading to linux 6.2.0-26.26"
date: 2023-07-24
forum: Installation &amp; Upgrades
---

### Post by onetefo2 on 2023-07-24
Hey there,
I am having this issue after upgrading to kernel 6.* for the very first time.
If I fallback to kernel 5.19.* my partition is recognized again with no issues.
I have an XPS 9320.
Anyone else experiences issues with FDE and kernel 6? Is this a bug?
Thanks!

---

### Post by #&amp;thj^% on 2023-07-24
Just to be sure have you yet run:
```
update-initramfs -u -k all
```
You should be fine with FDE on kernel6.2

---

### Post by onetefo2 on 2023-07-24
Hi 1fallen, thanks for you quick prompt.
Yes, I tried that. I also updated to > linux-image-6.2.0-26-generic (6.2.0-26.26~22.04.1) today so the whole install process was go through again and still same problem.

---

### Post by MAFoElffen on 2023-07-25
You were a bit unclear on this, and you really did not say so.... No 0ne has asked yet but:

Which ISO did you to install from originally?
Are you do your encryption installation with the default install scripts of LVM2 or ZFS?
Or did you install manually and do either LUKS1 or LUKS2 containers with EXT4, LVM2, ZFS, or BTRFS?
Is it an encrypted on root, with a separate  encrypted boot partition (LUKS1 or LUKS2 boot)?
Or are your doing other LUKS encrypted partitions (Home, Data)?
What are the key formats?
Or are your trying to do ZFS native encryption?

There are some variables that go with those answers, with different  answers for each...

On the whole, I have not seen a problem with the 6.2.x kernels and encryption. ...and I have many test machines installed with different filesystems, file managers, and encryption types in my test lab suite. If on a new install, on a new ISO, then I would like to retest that ISO to report it through the QA ISO tracker.

---

### Post by MAFoElffen on 2023-07-26
For example:
```

root@lunar-lander-01:~# uname -r
6.2.0-26-generic
root@lunar-lander-01:~# lsb_release -d
No LSB modules are available.
Description:    Ubuntu 23.04
root@lunar-lander-01:~# zfs get keylocation | grep -v -e 'none'
NAME                                              PROPERTY     VALUE                                  SOURCE
rpool                                             keylocation  file:///run/keystore/rpool/system.key  local

```
That 'is' the same kernel that you say you are experiencing issues with...

---

### Post by onetefo2 on 2023-07-26
Hi @MAFoElffen, thank you for your willingness to help.
Please find bellow my answers, overall an standard installation from ISO 22.04LTS with the default FDE option from the GUI. I haven't moved a lot from the basics with this system, mostly all of the option that came by default and just keep it updated.

> **MAFoElffen said:**
> You were a bit unclear on this, and you really did not say so.... No 0ne has asked yet but:

Which ISO did you to install from originally?
RE: [Ubuntu 20.04 _Focal_ - Build amd64 LIVE Binary 20200502-05:58]/ focal main

Are you do your encryption installation with the default install scripts of LVM2 or ZFS?
RE: I did the standard LVM and encryption from the "Advanced options" feature like in here [https://linuxconfig.org/wp-content/uploads/2022/05/02-ubuntu-22-04-enable-full-disk-encryption.png](https://linuxconfig.org/wp-content/uploads/2022/05/02-ubuntu-22-04-enable-full-disk-encryption.png)

Or did you install manually and do either LUKS1 or LUKS2 containers with EXT4, LVM2, ZFS, or BTRFS?
RE: No.

Is it an encrypted on root, with a separate  encrypted boot partition (LUKS1 or LUKS2 boot)?
RE: Not entirely clear what this means.
This is the output of
```
sudo lsblk -o NAME,FSTYPE
nvme0n1               
&#9500;&#9472;nvme0n1p1           vfat
&#9500;&#9472;nvme0n1p2           ext4
&#9492;&#9472;nvme0n1p3           crypto_LUKS
  &#9492;&#9472;nvme0n1p3_crypt   LVM2_member
    &#9500;&#9472;vgubuntu-root   ext4
    &#9492;&#9472;vgubuntu-swap_1 swap
```

Or are your doing other LUKS encrypted partitions (Home, Data)?
RE: No.

What are the key formats?
RE: It is a passphrase.
Or are your trying to do ZFS native encryption?
RE: No.

There are some variables that go with those answers, with different  answers for each...

On the whole, I have not seen a problem with the 6.2.x kernels and encryption. ...and I have many test machines installed with different filesystems, file managers, and encryption types in my test lab suite. If on a new install, on a new ISO, then I would like to retest that ISO to report it through the QA ISO tracker.

---

### Post by onetefo2 on 2023-07-26
@MAFoElffen
> That 'is' the same kernel that you say you are experiencing issues with... 				

RE: It is, yes. :-k

---

### Post by #&amp;thj^% on 2023-07-26
I don't think MAFoElffen is having any issues with that kernel.
Can you show us this please:
```
sudo lsblk -o NAME,FSTYPE

```
EDIT: Mine shows:
```
NAME               FSTYPE
sda                
&#9500;&#9472;sda1             zfs_member
&#9492;&#9472;sda2             LVM2_member
  &#9500;&#9472;vglinux-root   ext4
  &#9492;&#9472;vglinux-swap_1 swap
sdb                
&#9500;&#9472;sdb1             btrfs
&#9492;&#9472;sdb2             ext4
sdc                
sdd                
sde                
&#9492;&#9472;sde1             ext4
nvme1n1            
&#9500;&#9472;nvme1n1p1        vfat
&#9500;&#9472;nvme1n1p2        swap
&#9500;&#9472;nvme1n1p3        zfs_member
&#9492;&#9472;nvme1n1p4        zfs_member
nvme0n1            
&#9500;&#9472;nvme0n1p1        vfat
&#9500;&#9472;nvme0n1p2        swap
&#9492;&#9472;nvme0n1p3        ext4

```
This would be nice to view as well:
```
sudo  zfs get keylocation | grep -v -e 'none'

```
You said yes to this "Or are your trying to do ZFS native encryption?
RE: yes.
"

---

### Post by MAFoElffen on 2023-07-26
He did post that results and it showed LVM2 without an ecrypted boot:
> ```

sudo lsblk -o NAME,FSTYPE
nvme0n1               
&#9500;&#9472;nvme0n1p1           vfat
&#9500;&#9472;nvme0n1p2           ext4
&#9492;&#9472;nvme0n1p3           crypto_LUKS
  &#9492;&#9472;nvme0n1p3_crypt   LVM2_member
    &#9500;&#9472;vgubuntu-root   ext4
    &#9492;&#9472;vgubuntu-swap_1 swap

```

---

### Post by MAFoElffen on 2023-07-26
On boot, after the Grub2 Menu, does it go to the splash screen with a Dialog Box near the bottom asking for a passphrase? Or is it just a black screen?

23.04 had and encryption boot process bug where that dialog box does not show in the boot process, and goes to a black screen... If you press the <Down-Arrow>, it then toggles the screen to the messages underneath, where it says:
```

Please unlock disk dm_crypt-0:**

```
Press the <Backspace key to delete the "*" characters, then enter your encryption passphrase, then press <Enter> to continue.

You can get around this once you boot by opening a terminal session, then
```

sudo nano /etc/default/grub

```
Go down to the line that starts with GRUB_CMDLINE_LINUX_DEFAULTED="quiet splash" line and replace the word "quiet" with "---". (3 dashes) Save and Exited, then do
```

sudo update-grub

```
That will displayed the boot messages and you will see that encryption prompt come up...

---

### Post by MAFoElffen on 2023-07-26
The answer to my other question would be revealed by this query
```

sudo cryptsetup luksDump $(sudo blkid | awk '/crypto_LUKS/ {print $1}' | sed 's/://g') | grep 'PBKDF:'
## Which is going to show this output:
#   PBKDF:      argon2id

```

---

### Post by onetefo2 on 2023-07-26
Hi all,
Thank you for your help! The answer to whether I have ZFS native encryption was No. Actually if I try
> $ sudo  zfs get keylocation | grep -v -e 'none'
sudo: zfs: command not found

The second command you are asking is showing
> $ sudo cryptsetup luksDump $(sudo blkid | awk '/crypto_LUKS/ {print $1}' | sed 's/://g') | grep 'PBKDF:'
    PBKDF:      argon2i
    PBKDF:      argon2i
Attached is what it shows when I try to boot on Kernel 6* (cryptsetup: Waiting for encrypted source device), and then it goes into the busybox shell

---

### Post by MAFoElffen on 2023-07-27
What is the results of
```

sudo blkid

```

---

### Post by onetefo2 on 2023-07-27
```

$ sudo blkid
/dev/mapper/nvme0n1p3_crypt: UUID="eceKBK-ePi1-8s0R-ny13-v3oD-NeZd-L6iTPP" TYPE="LVM2_member"
/dev/mapper/vgubuntu-swap_1: UUID="d894c94f-72b0-407d-9e9e-197f71c6ad44" TYPE="swap"
/dev/mapper/vgubuntu-root: LABEL="UBUNTU" UUID="55dff36c-f74e-48d2-a24c-facb96ff2138" BLOCK_SIZE="4096" TYPE="ext4"
/dev/loop1: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/nvme0n1p3: UUID="cf75f74f-b538-4fb6-a740-23a26027431b" TYPE="crypto_LUKS" PARTUUID="c806d696-16e9-4e66-a0a3-13939768bbdf"
/dev/nvme0n1p1: UUID="596C-B2FF" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="9ee29aa0-d85c-4776-9cc3-4ae7dea046d8"
/dev/nvme0n1p2: UUID="09da7d71-778e-4164-9297-06f6e2136481" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="8b291659-bdf7-4569-b7c7-9ebd779de586"
/dev/loop27: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop31: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop30: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"

```

---

### Post by MAFoElffen on 2023-07-28
Here is what I want you to do booted from an Ubuntu LiveUSB, using try, from a terminal session
```

sudo su -
LUKS_VDEV=$(blkid | awk '/crypto_LUKS/ {print $1}' | sed 's/\://g' )
cryptsetup open $LUKS_VDEV

vgchange -a y
LVM_LUKS=$(lvscan | awk '/ACTIVE/ {print $2}' | sed 's/\'//g' )

mount $LVM_LUKS /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
mount /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi || true
mount /dev/sda1 /mnt/boot/efi
chroot /mnt /bin/bash --login
mount -a

update-initramfs -c -k all
update-grub
exit
reboot

```

---

### Post by onetefo2 on 2023-07-29
OK, I have a busy weekend at work but will try create an Ubuntu Live USB and run that code. BTW, is it safe? I have an important presentation next week.
Also, I noticed a couple more of line of text appearing when booting on kernel 6*:
```
Volume grop "vgubuntu" not found
Cannot process volume group vgubuntu
mdadm: No devices listed in conf file were found
```

---

### Post by MAFoElffen on 2023-07-29
It is safe.

I contribute to the boot-repair and boot-info script on encryption, LUKS and ZFS. I do not 'need' to advise you on how to do this. You have no backups of it. If you do not want to try it, you could always just install fresh.

If you have any worries, what you can do is make a full disk image of it for the just-in-cases, which is something I advise to everyone before attempting a repair of any sort.

EDIT: That last line will just rebuild the initramfs image without any other changes. It will not try to reinstall the boot-loader. That is not the problem you are showing. What you showed is that your system cannot find the LUKS container, that your root LVM container is in, which your root filesystem is in... Which by your previous output is there. After that, well... Not much else to tell you. If that fails, You are pretty much "locked out". Everything I told you "should" work.

---

### Post by onetefo2 on 2023-08-12
Thank you so very much for your help, @[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547"). I just wanted to get a sense of the acceptable level of risk to decide whether would be the best time to try it based on my necessities with this laptop for work.
Happily, the problem was solved with the last update so there is no need to further changes.
Once again, thank you and all for your valuable contribution and support. Very much appreciated!

---

### Post by MAFoElffen on 2023-08-12
You are very welcome... This is what I do for encrypted volumes.

I do backups. I think this experience is a wake up call showing you what you may lose if not prepared, and how that means to you. Only you can decide what your own "acceptance of risk" is to you. Agreed?

I setup multiple key--slot passphrases... More than just one. For one of the key--slot's, I setup a keyfile, which I keep on a USB flash drive. The I also backup the LUKS header and save that to that USB Flash drive.

That way, if something goes wrong, I have more than one option opened up to me.

---

### Post by onetefo2 on 2023-08-12
Thanks - I do backups of all my data on my own Nextcloud server but I am always hesitating whether routinely backup the disk image to safeguard OS config or start from scratch if something goes wrong :-s

---

