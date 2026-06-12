---
title: "Fluxbuntu live CD can't be booted through my machine"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by amitst on 2007-12-24
Since Xubuntu is running too slow on my old desktop (333MHz Celeron 64MB RAM) I decided to try Fluxbuntu on it. However, I noticed that the live CD doesn't boot and the OS from hard disk is booted instead (as if there is no CD in the CDROM). Here are some facts to understand the situation,
- Once booted from hard disk the fluxbuntu CD is recognized and I can read all the files in it
- I have installed Xubuntu using the bootable alternate CDROM on my desktop. So "boot through CD" operation should work for fluxbuntu as well
- I have successfully booted through and installed Fluxbuntu on my other laptop (using the same CD) so there shouldn't be any issue with the CD
- One suspect is that the CD is written using the writer on Laptop. So there might be some issue while recognizing the disk as bootable through the older CDROM drive on my desktop (Celeron).

Any pointers regarding what can be done?

---

### Post by thalamus on 2007-12-24
I am also having a similiar problem. I have used older versions of Ubuntu with no problems or bumps in the road. Now I can't get the live CD to boot for anything.

---

### Post by pointone on 2007-12-24
Verify the integrity of the CD image and the burned CD (MD5 checksum), and try re-burning the disc at the lowest speed possible.

---

### Post by amitst on 2007-12-24
Do you suggest this even if I am able to install Fluxbuntu on my laptop using the same disk? I guess the integrity can be checked through the initial bootup menu. How can I get (verify) the MD5 checksum of a burned CD?

---

### Post by Sef on 2007-12-25
> How can I get (verify) the MD5 checksum of a burned CD?

If you still have the iso, you can check it with what it is supposed to be.  [How to MD5sum.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by amitst on 2007-12-25
Looks like the [https://help.ubuntu.com](https://help.ubuntu.com) site is down. I googled other sites for the procedure, downloaded a new iso and checked the MD5 checksum as follows

```
amit@lap432:/data/iso_downloads$ md5sum fluxbuntu-7.10-installer-i386.iso
477c72d8363a45a3d2aea9936764227d  fluxbuntu-7.10-installer-i386.iso
amit@lap432:/data/iso_downloads$ cat fluxbuntu-7.10-installer-i386.iso.MD5SUM 
477c72d8363a45a3d2aea9936764227d  fluxbuntu-7.10-installer-i386.iso
```

Which is matching. I will write a new CD later with the lowest speed possible and try it out on the home desktop later. I will update this thread in a day or two.

---

### Post by kerry_s on 2007-12-25
> **amitst said:**
> Since Xubuntu is running too slow on my old desktop (333MHz Celeron 64MB RAM) I decided to try Fluxbuntu on it. However, I noticed that the live CD doesn't boot and the OS from hard disk is booted instead (as if there is no CD in the CDROM). Here are some facts to understand the situation,
- Once booted from hard disk the fluxbuntu CD is recognized and I can read all the files in it
- I have installed Xubuntu using the bootable alternate CDROM on my desktop. So "boot through CD" operation should work for fluxbuntu as well
- I have successfully booted through and installed Fluxbuntu on my other laptop (using the same CD) so there shouldn't be any issue with the CD
- One suspect is that the CD is written using the writer on Laptop. So there might be some issue while recognizing the disk as bootable through the older CDROM drive on my desktop (Celeron).

Any pointers regarding what can be done?


with those specs-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by amitst on 2007-12-26
Yes, I usually boot through the DSL and avoid using Xubuntu on my Celeron. However, this has some limitations,
- I use static IP for my network card and DNS host. I have arranged to backup/restore interfaces and resolv.conf files everytime the PC boots up through DSL CD but somehow it is not picking it up and I have to reconfigure or restart the network interface.
- Upgrading to new OS version requirs writing a new CD
- CD drive is engaged and I can't put another CD to listen to music etc. (fortunately I have two CD drives, one read-only and one writer but still it is an issue)
- I am not very sure how to add the vast amount of packages/games available on Ubuntu repositories. For now I have to be content with ehatever is in the DSL CD

It seems that Fluxbuntu is also using Fluxbox (similar to DSL) so it will solve all the above issues. I also would like to stick to the Ubuntu family to reduce the learning curve.

---

### Post by amitst on 2007-12-27
I tried writing a new CD with the lowest speed 4.7x possible through Ubuntu. But still the Celeron can't boot through that CD. :(

Next option will be to write the CD through the Celeron writer. But this mean (possibly) wasting another CD.

---

### Post by amitst on 2007-12-29
At last I burned a new CD using the workaround mentioned in the following link and was able to boot through the new CD on my Celeron. :)

[https://bugs.launchpad.net/fluxbuntu-project/+bug/157724](https://bugs.launchpad.net/fluxbuntu-project/+bug/157724)

The specific steps I followed on my Ubuntu laptop are,
```

mkdir fluxbuntu-7.10RC
mount -t iso9660 -o loop fluxbuntu-7.10-installer-i386.iso fluxbuntu-7.10RC
tar -cvf fluxbuntu-7.10RC.tar fluxbuntu-7.10RC
umount fluxbuntu-7.10RC
rmdir fluxbuntu-7.10RC
tar -xvf fluxbuntu-7.10RC.tar
chmod -R +w fluxbuntu-7.10RC
genisoimage -J -r -o fluxbuntu-7.10RC-remaster.iso \
-b isolinux/isolinux.bin -c isolinux/boot.cat \
-no-emul-boot -boot-load-size 4 -boot-info-table fluxbuntu-7.10RC

```
Now burn the CD using the remastered image

---

### Post by amitst on 2007-12-31
Further to this I installed Fluxbuntu using the rematered CD and it installed successfully. But while booting through hard disk the GRUB gave "Error 18" and was unable to proceed. Upon searching I found that the error comes if BIOS is unable to read the GRUB configuration. It happens when the GRUB config is at a location that is not directly accessible to the BIOS (beyond the maximum address space). I was having a 10GB Win98 partition and then 30 GB / partition. I wasn't sure why GRUB can't reboot (as Xubuntu was able to boot through same parition structure. I am not sure about the "Bootable" flag for each paritition but I think I messed up with that setting while recreating partitions). Anyways so I erased the entire disk and installed fluxbuntu and then it booted through fine.

After installation my serial mouse wasn't detected by the system. I had to change the following content in the /etc/X11/xorg.conf (under Mouse section)

Option "Device" "/dev/ttyS0" (originally something like /dev/mice/)
Option "Protocol" "Microsoft" (originally something like PS2)

And mouse started working. Still I have issues with double click of mouse. Also the Xterm is not loading (other applications are working)

---

