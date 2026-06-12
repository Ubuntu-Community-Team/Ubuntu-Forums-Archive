---
title: "how to dual-boot with 2 linux distro's"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by Arc Owner on 2006-03-28
I have been using Gentoo for a while now, and really like it but I also have used ubuntu and want to use it too. I have heard many people talk about dual-booting with linux and XP, but how would you dual-boot with linux and linux? I have heard that Ubuntu detects the other distro by default when installing, and will dual-boot for you,but I just got done installing ubuntu and it did not detect it, and after installing I realized it got rid of my Gentoo install. I don't want it to do that again, so can somebody give me a walkthrough? I really would like to get these 2 things on the same hard drive because I like both distros.

Thanks,
Arc Owner

---

### Post by dermotti on 2006-03-28
If you really did get rid of your Gentoo install, that is why Ubuntu didnt detect it. I have had success with the ubuntu recognizing my Windows XP and my other Linux distro without issue.

---

### Post by Arc Owner on 2006-03-28
no, I think you misunderstood me. I DID NOT get rid of the Gentoo install before the Ubuntu installation. It was the UBUNTU INSTALL which got rid of gentoo. I still had Gentoo when installing ubuntu. Ubuntu did not detect the Gentoo install.

---

### Post by dermotti on 2006-03-28
"Ubuntu" Does not detect anything. You tell it what harddrive you want to install to and it will do it. 

After Ubuntu is installed, **GRUB** detects your os's.

So you deleted Gentoo before grub could detect it.

---

### Post by rplantz on 2006-03-28
[QUOTE=Arc Owner]I really would like to get these 2 things on the same hard drive because I like both distros.[/QUOTE]

If you look here [http://ubuntuforums.org/showthread.php?t=147197](http://ubuntuforums.org/showthread.php?t=147197) you will see that I was even more ambitious. I installed the second distro on another, different type of drive. And, like you, everything I found in my searching was about installing Linux and Windows.

Anyway, I was unsucessful the first time.

I decided to simply format my external drive as another ext3 partition. Then I played with that for a while.

Then I reinstalled the second Linux distro (Dapper in my case). The installer allowed me to repartition this new partition. (Again, I had it on a separate disk.) I don't know if I missed something the first time I installed, or if creating this extra partition before reinstalling was the key.

Anyway, if I were you, I would try the installation again. Make sure that you create the required new partitions **in addition** to the ones you already have for Gentoo.

In my case, the installer detected the other (Breezy) Ubuntu installation and I followed its recommendations. As you will note in the other thread, everything I read on the web recommended against reinstalling grub. But I followed the advice of the Ubuntu installer, and all went well.

In case you're interested, here are the partitions on my disks:
```

$ sudo fdisk -l
Password:

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9354    75135973+  83  Linux
/dev/hdc2            9355        9729     3012187+   5  Extended
/dev/hdc5            9355        9729     3012156   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            9363        9727     2931862+  82  Linux swap / Solaris
/dev/sda3            1217        9362    65432745   83  Linux
/dev/sda4   *        9728       19457    78156225   a5  FreeBSD

Partition table entries are not in disk order

```

Here is the significant entry in my /boot/grub/menu.lst file:
```

# This is for Dapper
title           Ubuntu, kernel 2.6.15-18-amd64-generic Default
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-18-amd64-generic root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-18-amd64-generic
boot

```
If Gentoo is your primary distro, I assume that you will have to find the equivalent file there. Then I think you will have to use
```

root    (hd0,n)

```
where n is the number of the partition (starting from zero) where your Ubuntu installation begins, instead of the
```

root    (hd1,0)

```
that I have. Notice that grub uses a different system to number disks/partitions. It keeps life interesting. :)

---

