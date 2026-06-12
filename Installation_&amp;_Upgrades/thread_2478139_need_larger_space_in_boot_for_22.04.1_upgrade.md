---
title: "need larger space in /boot for 22.04.1 upgrade"
date: 2022-08-17
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2022-08-17
Friends--

Two desktops need to be upgraded from 18.04.6 lts to 22.04.1 lts. They each have a /boot partition of 472 M. When I upgraded another desktop last week, it stopped me from the upgrade saying I needed a total space in /boot of something like 700 M.

That led me to trying to reallocate lvm luks encrypted space to /boot. That did not go well, and I ended up having to blow it all away and install 22.04.1 from scratch. Don't want to repeat that 4 days of lost time!

So what are my options for increasing the size of the /boot partition?

Here is some info for one of the machines:
```
sda                      8:0    0 232.9G  0 disk  
&#9500;&#9472;sda1                   8:1    0   487M  0 part  /boot
&#9500;&#9472;sda2                   8:2    0     1K  0 part  
&#9492;&#9472;sda5                   8:5    0 232.4G  0 part  
  &#9492;&#9472;sda5_crypt         253:0    0 232.4G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root  253:1    0 224.5G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1
                       253:2    0   7.9G  0 lvm   
      &#9492;&#9472;cryptswap1     253:3    0   7.9G  0 crypt [SWAP]

/dev/sda1                    472M  277M  171M  62% /boot

```

Could I somehow move /boot to a usb drive, then move it back after the upgrade? What other ways might there be (involving low pain)?

Thanks!

---

### Post by #&amp;thj^% on 2022-08-17
mine is this on any linux install:
```
df -hT | grep boot
/dev/nvme0n1p1 vfat     1022M  174M  849M  17% /boot

```
This may be a good read: [https://geekdudes.wordpress.com/2021/04/09/ubuntu-20-04-extend-boot-partition/](https://geekdudes.wordpress.com/2021/04/09/ubuntu-20-04-extend-boot-partition/)
I generally follow the Arch Wiki: [https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS](https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS)

---

### Post by dgermann on 2022-08-17
@ 1fallen--

Thanks for getting back to me so quickly!

As near as I can tell, the geekdudes tutorial involves a non luks drive. I did follow the archlinux page in working to resize things, and even so, it went awry, so I am nervous about trying that, again.

I think I got into trouble when I did sudo fdisk /dev/sda. Now I see that archlinux does not seem to use that, but rather parted. It seems I was mainly following [https://help.ubuntu.com/community/ResizeEncryptedPartitions]("https://help.ubuntu.com/community/ResizeEncryptedPartitions").

Have you actually done this? Any pointers on what I may have done wrong?

Any thoughts on just moving the /boot partition to a usb drive?

Thanks, 1fallen!

---

### Post by #&amp;thj^% on 2022-08-17
Truthfully, I've never had to unless it was a fresh/new disk, and I'm installing Arch first.
but yes I have used just this before:
```
sudo cryptsetup resize /dev/mapper/opened-volume

####then resize the file system. E.g. if it is an Ext4 filesystem, you can resize it even if it is mounted with

sudo resize2fs /dev/mapper/opened-volume
```

I did both commands with a mounted file system with no interruption, that does not mean your will go as well though. (AKA Your mileage may vary)
As far as moving it to a USB drive : [https://bbs.archlinux.org/viewtopic.php?id=192858](https://bbs.archlinux.org/viewtopic.php?id=192858)
I just rsync for all my back-ups
Sounds fun though, if no one else pop's in on this I just might set-up a test bed, it might take me a day or two though.
Life is **commanding** my time for short spell.
EDIT: A friend just sent me this, and it looks very doable: [http://e1z.ca/devlog/encrypted_partition_resize.html](http://e1z.ca/devlog/encrypted_partition_resize.html)

---

### Post by ubfan1 on 2022-08-17
First ensure to remove old kernels to reduce the update space requirements.  Might fit if only one, but the update usually brings in another. Consider an hwe kernel on the old system, maybe that would keep the kernels down to only one.  I've used USB on /tmp for tight updates, I suppose /boot would work, ensure you copy the necessary things back to the mount point /boot before trying a reboot.

---

### Post by ubfan1 on 2022-08-17
First ensure to remove old kernels to reduce the update space requirements.

---

### Post by dgermann on 2022-08-17
@1fallen --

Thanks!

The archlinux link gives me confidence that it can be done. I also found [https://askubuntu.com/questions/539504/moving-boot-to-a-usb-key]("https://askubuntu.com/questions/539504/moving-boot-to-a-usb-key") which gives a bit of a tutorial, although it is from several years ago.

The devlog link does look hopeful.

Wish there were a way to test these things out without destroying a well running existing install!

@ubfan1 --

Thanks for jumping in!

Yes, I manually removed all kernels from /boot except for the running one, but it still wanted more space than was available in the partition. (As I recall when I first installed this the size was automatically generated. But I suppose that might have been 4 or so releases back, so maybe the sizes just kept increasing.)

You mention using an hwe kernel. Although I just searched to see what that is, I did not get any good sense of it. I presume it is a smaller kernel, but then it sounds like it somehow loses lts support. Could you tell me a bit more, please?

Your suggestion of mounting a usb drive to /tmp is intriguing. How does that help, and is it a simple:
```
# mount /dev/sdd2 /tmp/usb
```
or something else I'd need to do?

Thank you ubfan1 and 1fallen!

---

### Post by ubfan1 on 2022-08-18
The hwe packages (hardware enablement) like linux-image-generic-hwe-22.04 will allow you to install the latest kernel available for you system.  If the 22.04 hwe is available, it has the 5.15 kernel the 22.04 system uses, so you might be able to upgrade the kernel first, then skip a kernel upgrade on the release upgrade (not sure though).  Might just be a complication though.  For an upgrade of a really small root (5GB), I mounted  external filesystems for /var/cache/apt/archives (for the new package downloads) and /tmp (for a little more working room). I suppose you could make a USB with ext4 or have a directory on another hard disk, copy the existing /boot files there, then mount the USB or dir at /boot, giving you as much space as you need for the upgrade.  Then before rebooting, assuming the completed upgrade is small enough (making the initrd takes up working room), unmount the /boot device, and copy files back to the /boot partition.

---

### Post by yancek on 2022-08-18
487MB seems like it would be more than enough for a boot partition.  Could you post the output of ls /boot?  Posting the output of sudo fdisk -l would be more useful as it shows sectors.  I have never used LVM but if your /boot and lvm partitions are adjacent, you should be able to move the lvm partition to the right but it will be time consuming as it will have to also move all the data.  I believe you can do this with GParted.

As far as booting from a USB, you should be able to do that.  Are you using UEFI?  I would think you would need both an efi and boot partition on the USB and would also need to, copy those files from the internal to the USB.  You would also need to run sudo grub-install with the USB attached and change the grub.cfg file on the efi partition to point to the new /boot partition where the kernels reside.  I don't know that this would do it but you would need to at least do these steps.  I'm not familiar with LVM so...?

---

### Post by dgermann on 2022-08-18
ubfan1 and  yancek--

Thanks for your guidance. I am tied up most of today and will get back to you, probably tomorrow.

Thanks!

---

### Post by dgermann on 2022-08-23
ubfan1 and yancek and all--

Well, I am somewhat stuck.

In upgrading the first computer (actually have 3 to upgrade), I first ran these commands:
```
    • doug@fire:~$ sudo apt-get update
    • doug@fire:~$ sudo apt-get upgrade -y
    • doug@fire:~$ sudo apt-get autoremove -y
    • doug@fire:~$ sudo apt install update-manager-core
```
and then ran the "Software Updater" from the gui. It ran through some downloads and then told me /boot was too small. If I took out all but the running kernel, it would still be too small.

So I decided to try to move /boot to a usb stick. I followed [https://askubuntu.com/questions/539504/moving-boot-to-a-usb-key]("https://askubuntu.com/questions/539504/moving-boot-to-a-usb-key") and all went well till it asked me to mv /boot /boot/old. No go. Ubuntu would not allow /boot to be renamed.

So I played around with trying to get grub to boot it, but got as far as grub> boot and nothing would boot. I was following [https://szymonkrajewski.pl/how-to-boot-system-from-usb-using-grub/]("https://szymonkrajewski.pl/how-to-boot-system-from-usb-using-grub/"). Here are the things I did:
```
grub> ls
grub> set root=(hd3,msdos1)
grub> chainloader / #(here i used tab complete and tried, in turn, all the options available)
grub> boot

```

I am reluctant to try resizing the partitions, because that ended up with having to blow away the drive and reinstall from scratch!

If I could figure out how to get the usb stick to boot, I suspect I can make the current /boot partition go away and make the changes in fstab and other things necessary to make it boot on startup. Or at least complete the upgrade to 20.04 and then to 22.04.

Or perhaps there is a way from a live disk to access the /boot directory of the machine itself, I could do the mv and changes to fstab.

BTW, this computer now shows 1152 packages that can be upgraded--I guess that is because of the aborted upgrade to 20.04. I am afraid that if I update those, the whole system will be broken!

Any ideas what might be a reasonable next step?

Thanks!

---

### Post by ubfan1 on 2022-08-23
Odd the rename failed, maybe you just needed to use sudo mv /boot /boot.old     Works for me.

---

### Post by dgermann on 2022-08-23
ubfan1--

```
root@fire:/# mv /boot /boot.old
mv: cannot move '/boot' to '/boot.old': Device or resource busy
```

is what it does for me. I am not in /boot; what could be causing it to say it's busy?

---

### Post by dgermann on 2022-08-23
ubfan1 and yancek and all--

There was a simple answer to my question, why is /boot busy? I found the way to deal with it here: [https://unix.stackexchange.com/questions/11238/how-to-get-over-device-or-resource-busy]("https://unix.stackexchange.com/questions/11238/how-to-get-over-device-or-resource-busy"). I did this:
```
root@fire:/# umount /boot # Who woulda thunk?
root@fire:/# mv /boot /boot.old
root@fire:/# mkdir /boot
root@fire:/# umount /dev/sdd
root@fire:/# mount /dev/sdd /boot
root@fire:/# blkid /dev/sdd
/dev/sdd: UUID="d31679dc-72d8-441d-9d47-7a71d45ed4c4" TYPE="ext4"
root@fire:/# nano /etc/fstab
        &#9702; #####ddg 20220823:
        &#9702; 
        &#9702; #UUID=c06baf8b-1008-485a-8c98-5c406e5ad497 /boot           ext2    defaults    $
        &#9702; UUID=d31679dc-72d8-441d-9d47-7a71d45ed4c4 /boot           ext2    defaults     $
        &#9702; #####
root@fire:/# update-grub
reboot
```

So now the boot proceeds past mounting the luks drives, and then stops me. Here is the error message I have found:
```
mount: /boot: wrong fs type, bad option, bad superblock on /dev/sdd, missing codepage or helper program, or other error.
```

What are the likely troubleshooting steps I should be doing? Please? Thanks!

---

### Post by ubfan1 on 2022-08-23
Without a partition table on sdd, so you use /dev/sdd instead of /dev/sdd1, I think you need the -oloop option on the mount, and -text4 too so try mount -text4 -oloop /dev/sdd /boot

---

### Post by dgermann on 2022-08-23
ubfan1--

dmesg I think it was that showed me the clue: for some reason my system was expecting ext2 and I had formatted my usb to ext4. So (for completeness for anyone following this) this is what I did:
```
        &#9702; doug@wind:~$ sudo mkdir /media/doug/copy
        &#9702; doug@wind:/media/doug/d31679dc-72d8-441d-9d47-7a71d45ed4c4$ sudo cp -ax . /media/doug/copy/
        &#9702; root@wind:~# fdisk /dev/sdb
            &#9642; d none to delete
            &#9642; n chose all defaults
            &#9642; t 83 linux
            &#9642; w
        &#9702; root@wind:~# mkfs -t ext2 /dev/sdb1
            &#9642; Filesystem UUID: a26eefb0-361e-41ff-924b-cd15214d83d5
            &#9642; Superblock backups stored on blocks: 
            &#9642; 	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632
        &#9702; disk: pull out, push in
        &#9702; root@wind:/media/doug# mount /dev/sdb1 fireroot/
        &#9702; root@wind:/media/doug/copy# cp -ax . /media/doug/fireroot/
        &#9702; root@wind:~# umount /media/doug/fireroot 

```
Then I had some difficulty with editing /etc/fstab under grub> and found that copying by hand I got a couple of digits wrong in the uuid for the new sdd1. Once I got that corrected, I was in!

After that, for good measure I ran
```
update-grub
```

At this moment, the upgrade from 18.06 to 20.04 is proceeding smoothly.

So I will mark this solved.

Thank you for your help. It really helped to be able to talk with you and get some clues from my questions and your nudges! Thanks!

---

