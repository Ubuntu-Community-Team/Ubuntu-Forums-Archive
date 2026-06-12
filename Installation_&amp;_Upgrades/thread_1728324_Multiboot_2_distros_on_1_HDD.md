---
title: "Multiboot 2 distros on 1 HDD"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by imkqm6 on 2011-04-13
I want to multiboot several Distros for experimental purposes. My main distro is Ubuntu 10.04.
Hard drive is partitioned like such:
 /dev/sda1, grup bios, size = 977 Kib
/dev/sda2, file system ext4, size 1.8 Tib, this is mounted on / 

/dev/sda3 linux swap, 4.3Gib.

My question is can I use Gparted to partition a second space out of sda2, and install another Distro? Do I mount it on / ? and will grub boot see both OS without destroying the kernel of my old distro? I am assuming to partition my hard drive I have to unmount it, but can I do this without using a live cd? So many questions and so little help, because apparently this is an easy thing to do. I am just worried just seems that what I just described is too easy and I will probably destroy everything and have to start over.

---

### Post by malspa on 2011-04-13
I use GParted from a live CD for the partitioning. I think it's best to use a live CD.

Here, the distro that boots the others is Mepis 8. It's using grub-legacy, not grub2, so the situation might be different than yours.

On my first hard drive, sda1 is for Mepis' / (root partition); sda2 is swap; sda3 is for Mepis' /home partition. Those are all "primary" partitions.

sda4 is an "extended" partition, containing "logical" partitions sda5, sda6, etc.

You'll want to know about primary, secondary, and logical partitions, if you don't already.

When I install a new distro, I have to make sure that Mepis' /etc/fstab shows the new distro's partitions, and that I have mount points for them in /mnt. 

And, I have to edit /boot/grub/menu.lst in Mepis so that it'll boot the new distro; I use "chainloading" here. But, again, that's the procedure for grub-legacy.

This is just an overview of how I'm doing it here, mainly so you'll have an idea of some of the terms that you'll need to know about. I'd suggest doing a web search on multi-booting and other terms. Here are links to a couple of Dedoimedo's articles -- these might help:

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Good luck! It does get a lot easier after the first few tries! I've got seven or eight distros installed across two hard drives here.

---

### Post by Dutch70 on 2011-04-13
If you're worried about messing up, back up your hdd with Clonezilla. Don't ask me how...lol.

You'll have to shrink sda2 and create an extended partition. You can only have 4 primary prtns. which will be numbered sda1 thru sda4. You can have about 15 logical partitions inside the extended prtn.

You can use Gparted, you'll have to use a live cd or usb stick AFAIK.
Yes, you mount it on /. Grub will see both after you run "sudo update-grub" without the quotes. It is pretty easy actually.

Have a look at my hard drives. I have a total of 10 OS's.

---

### Post by oldfred on 2011-04-13
Is your first partition bios_grub or an UEFI partition?

If you are using gpt you may need newer distributions. Old grub legacy has not been maintained for years and may not work with gpt. Grub2 works fine with gpt, I have it booting several versions of Ubuntu.

Which ever distribution you install last will install to the MBR and control booting, unless you specify otherwise during the install. Or you can reinstall Ubuntu's grub if you end up installing the other distribution's boot loader.

I recommend smaller system partitions of about 25GB and if multibooting include /home inside the system partition, but only have the mostly hidden user settings in /home. Then put all you data in a data partition that you can access from the other installs. 

Depending on the other installs there can be issues with UID & PIDs or who the user is on the data partition.  Debian based distributions use 1000 as first user, but others use different UIDs.

---

### Post by imkqm6 on 2011-04-13
Alright thanks guys, I think I know enough to try it now. Wish me luck

---

### Post by srs5694 on 2011-04-13
Pay attention to oldfred's comments on GPT. You claimed that your first partition is "grup bios", which I'm guessing is a distortion of GNU Parted or GParted's identification of a drive as having the "bios_grub" flag set. If so, it's almost certainly a GPT disk, which is *not* subject to the primary/extended/logical issues that others have described.

If you're not sure what you've got, please run the following command on your current installation:

```

sudo parted /dev/sda unit s print

```

Post the result here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. That will tell us precisely what sort of partition table you've got.

---

### Post by malspa on 2011-04-14
Is GPT something that one would run into only with newer hard drives? Sorry, this is the first I've heard of that. I'm reading a little about it now.

---

### Post by oldfred on 2011-04-14
srs5694 has posted many times  and has a web site on gpt info.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

MBR(msdos) is the drive formating we have used since hard drives started appearing on IBM compatable PCs. It is getting long in the tooth. It cannot easily support drives over 2TiB. It soon after release had a fix to allow more than 4 primary partitions by using one primary as an extended and putting logicals inside the extended.

Macs & Windows servers with EFI use gpt. Some new motherboards offer both BIOS & UEFI boot managers and with UEFI you need gpt. But only windows 7 64 bit works with UEFI, so few are using UEFI now.

Some (arch linux) suggest all SSDs should use gpt. 

If not booting an older copy of windows you can use gpt. I have it on my 160GB drive with 10.10. and on my 16GB flash with Natty (full install).

---

### Post by srs5694 on 2011-04-14
> **malspa said:**
> Is GPT something that one would run into only with newer hard drives? Sorry, this is the first I've heard of that. I'm reading a little about it now.

GPT is just data on the drive. It can be used on new hard disks or old ones. Just run the command I suggested earlier and post the results to eliminate all confusion; it will clearly identify the partition table type.

---

