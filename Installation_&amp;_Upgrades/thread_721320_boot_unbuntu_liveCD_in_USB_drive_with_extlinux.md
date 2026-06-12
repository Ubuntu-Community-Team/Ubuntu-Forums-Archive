---
title: "boot unbuntu liveCD in USB drive with extlinux"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by jamesjames on 2008-03-11
I am trying to copy the contents of ubuntu livecd into a USB drive and install  a bootloader to make a 'liveUSB'. 
Since I want to use ext3 file system, I choose extlinux as the bootloader. What I have done is as followed.

1. copy all the content of livecd iso to the usb drive (say sdb1)
2. install extlinux to root of sdb1
3. cat mbr.bin into sdb1
4.copy the isolinux.cfg to root and rename to extlinux.conf

After that, I assumed the liveUSB should boot. But unforturnately, it stuck in initramfs. 

I tried syslinux as the bootloader in the similiar way, and it is ok. But I still need to use ext3 filesystem.

Anyone tried extlinux to boot liveUSB??  

Thanks a lot.

---

### Post by dbo33 on 2008-03-11
haven't tried it, but try: [http://edoceo.com/liber/ubuntu-live-usb](http://edoceo.com/liber/ubuntu-live-usb)

---

### Post by mick8985 on 2008-03-31
I did this the other week as hardy failed to boot from cd on my friends laptop, basically everything you have done is correct, and what I did. Apart from I believe you need to cat mbr.bin > /dev/sdb rather than sdb1. As the MBR is for the entire drive not just that partition.

---

### Post by carolus on 2008-03-31
When the BIOS provides no option for booting from USB, is there some way to make a boot CD that boots into the USB drive?  So that you don't have to alter the MBR on the primary hard drive?

---

### Post by mick8985 on 2008-03-31
> **carolus said:**
> When the BIOS provides no option for booting from USB, is there some way to make a boot CD that boots into the USB drive?  So that you don't have to alter the MBR on the primary hard drive?

Yes it should be possible. you would install isolinux onto the cd and edit the isolinux.cfg to point to the usb hard drive, problem is it would be as flexible as you probably hope. because the address of the usb hard drive would vary from computer to computer.

---

### Post by wilsonB on 2008-04-03
Yes, I got Ubuntu 8.04 booting off a 1GB Sd without problems in live mode. I'm trying to get persistent mode working to save changes. That part doesn't work to spiffy.. I think persistent still broke in 8.04. Can anyone verify this? Iv'e wasted many hours on this myself.

[http://ubuntuforums.org/showthread.php?p=4645057#post4645057](http://ubuntuforums.org/showthread.php?p=4645057#post4645057)

---

