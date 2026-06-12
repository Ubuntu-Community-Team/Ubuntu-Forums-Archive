---
title: "Can't install 11.10 on notebook with 10.04"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by Shellbak3 on 2012-09-27
I couldn't do any upgrade; when I tried I received a verification error.  I decided to do a clean install and downloaded 11.10 iso and tried to burn it to a CD/DVD but my 10.04 doesn't detect the blank disk when I insert it or when it's in the drive on boot.  (Brasero did recognize the drive once).  

I followed instructions to mount it on the fs and it mounted but no dialog appeared so I could start the install.

The drive is there and ready according to: 

```
sudo lshw -C disk
*-disk                  
       description: ATA Disk
       product: ST980811AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.BH
       serial: 5LYAA44B
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a2c90
  *-cdrom
       description: DVD reader
       product: RW/DVD GCC-M10N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


```

I'm really frustrated now and don't have any idea of what to try next.

---

### Post by josephmills on 2012-09-27
Have you thought about giving K3B a shot. I tend to use that more then Brasero, But that is about all the help that I can offer. Good luck and I am sure that someone else will have a great answer for you.

---

### Post by black veils on 2012-09-27
how about making a bootable usb stick instead, does your computer support that?

---

### Post by Shellbak3 on 2012-10-01
I was able to create a USB Stick that's bootable, thanks.

---

