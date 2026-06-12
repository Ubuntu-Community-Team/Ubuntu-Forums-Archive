---
title: "install ubuntu 13.04 lts instead of windows 7 starter; Kernel panic"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by niclas_nielsen on 2013-08-02
Hi i got a little problem, when i'm trying to install ubuntu 13.04 from a bootable usb flash drive, 1 gb.

after it has install the webcam, it says 
[22.854621] LZMA data is corrupt
[22.864186] VFS: cannot open root device "(null)" or unknown-block(0,0): error -6
[22.864299] please append a correct "root"= boot option; here are the available partitions:
[22.864420] Kernel panic - not syncing: VFS: unable to mount root fs in unknown-block(0,0)

pc specs

BIOS: Windows 7 starter edition
Processor: Intel atom CPU N450 @1.66ghz*2
RAM: 1 gb ddr2
Hard drive: 250 hitachi 5200 RPM

Just write for more information.

---

### Post by sudodus on 2013-08-02
Welcome to the Ubuntu Forums :-)

It looks like a netbook. Please tell us the brand name and model plus the graphics chip too :-) It will make it easier to help.

1. Check with md5sum, that the download was good

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Can you run a live session (try without installing)? If not, try if the pendrive works to boot another computer.

3. If still problems, I suggest that you try an older version of Ubuntu, and a flavour with a lighter desktop environment. This would increase the chances to boot without problems with the hardware.

Download and try Xubuntu 12.04 LTS from [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

---

### Post by niclas_nielsen on 2013-08-02
the brand name is Acer Emachine 350-21g25ikk and the grafik chip is [Intel Graphics Media Accelerator (GMA) 3150]("http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-3150.23264.0.html")
my pc can't run in live mode becasue something is wrong with the root, but ill try with the xbuntu instead. 

Thanks.



[http://www.notebookcheck.net/Acer-eMachines-EM350.35871.0.html](http://www.notebookcheck.net/Acer-eMachines-EM350.35871.0.html)

---

### Post by sudodus on 2013-08-02
It is a good idea to try Xubuntu 12.04.2 (not 13.04). Intel graphics should work with the built in drivers.

- But please tell us also if you had problems with the live session or only after installation!

- And what about the partitions on the hard disk drive? Please post the output of the following commands

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
 sudo blkid
```

Try to mount all partitions (using the file browser) and run

```
df
```

---

### Post by niclas_nielsen on 2013-08-02
where shall i write the commands, and i get the same problem, when im trying to do the live session.

---

### Post by sudodus on 2013-08-02
1. In a terminal window (if you get one) or a text screen if no graphical desktop environment.

2. Did you try 12.04 LTS or 13.04? The version 13.04 is not LTS (long time support). Anyway, try with the live session until you get it working before you try installing! I suggest you try with some boot options according to the following link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

And Xubuntu 12.04 LTS is a better alternative as I described earlier.

---

### Post by niclas_nielsen on 2013-08-02
okay ill try the xubuntu instead, i appreciated ur time.. and i don't have a terminal window only in windows, and the command don't work there.

---

### Post by niclas_nielsen on 2013-08-02
after i tried to install the xubuntu it just starts to write (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

What shall i do, can i try to install a older version of xubuntu. or what to do please help...

---

### Post by sudodus on 2013-08-02
12.04 is the oldest of the current Ubuntu desktop versions. Older versions have passed end of life, and receive no security updates. And I think that 12.04 should work in your computer.

1. Did you check the md5sums of the downloaded iso files? The calculated sum must be exactly like the one from Ubuntuhashes.

1. How did you make the USB flash drive (the pendrive) to an install device? What tool did you use? Did it finish without errors?

2. Did you try the pendrive live (try it without installing) in another computer? What's the result?

3. Did you try the pendrive live (try it without installing) in this computer? What happened ? Do not start installing before you have tried it and found that it works!

4. And what about the partitions on the hard disk drive? Please post the output of the following commands

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
 sudo blkid
```

Try to mount all partitions (using the file browser) and run

```
df
```

You might have some problem with the partitions. For example: if you have four primary partitions, it is not possible to create partitions to install Xubuntu. In this case you must delete one partition and probably also shrink another partition to create space logically and physically.

---

### Post by niclas_nielsen on 2013-08-03
1. the md5sums are the exact same as the ubuntuhashes.
2. the program i use to make the pendrive was lili usb creator, download from [http://www.linuxliveusb.com/help/guide/using-lil]("http://www.linuxliveusb.com/help/guide/using-lili") and at the finish there is no error when im trying to create the pen drive
3. i haven't tried the pen drive on another PC jet but soon i will do it.
4. [i]("http://www.linuxliveusb.com/help/guide/using-lili") when im trying to do the live session, i writes the same command as under the install, and i can't get any further.
5. i cant write the commands in the windows terminal, because it dosen't recognize any of them, but i don't know were to write them, if they not work in windows 7 starter.

---

### Post by sudodus on 2013-08-03
Good that you will try the pendrive to boot another computer :-)

I think that you have problems with some driver (for the operating system to cooperate with some hardware), probably the graphics or the wifi chip.

No those commands are made for linux, they do *not* work in a Windows terminal window (DOS-promt). But if you boot with some boot option, for example ***nomodeset*** and/or ***text***, you might succeed to get a text screen, where to write those commands. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

