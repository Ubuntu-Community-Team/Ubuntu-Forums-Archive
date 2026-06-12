---
title: "The installer encountered an error copying files to hard disk:  [Errn5] input/output"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by plabon on 2013-05-25
i am facing a problem while installing ubuntu 13.04..  a error message show:    "The installer encountered an error copying files to the hard disk:   [Errno 5] Input/output error    This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment."     i have tried with usb stik, but still same getting same error. and one point, i installed ubuntu with the same  dvd before in the same pc. when i format ubuntuand tried to reinstall, the problem stared.  what can i do? please help.

---

### Post by claracc on 2013-05-25
When i have encountered this problem, the culprit was the copied iso in the CD.

Try to copy again the iso in other CD/DVD and check the integrity of data copied ( I use k3b to copy to CD and check inategrity)

---

### Post by sudodus on 2013-05-25
Welcome to the Ubuntu Forums :-)


1. Check that the download was OK with ***md5sum*** in a terminal window

```
 md5sum filename.iso
```

Use the real filename of the downloaded iso file instead of 'filename' in the command. You can find the md5sums to check with at this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


2. Check that it will be possible  to write the Ubuntu system to your hard disk drive

- If you already have 4 primary partitions, you need to do something about it.

- If there is not enough empty space on the disk, you need to move / remove some data.

---

### Post by jaj2 on 2013-11-06
Hello, I am biginner, but I'd like to share my experience. I had the same problem. I checked the USB disk (in which ubuntu is installed). The bootable disk was created by unetbootin. It was with error (i checked it out by the option of disk cheeking of the boot menu). Then I created the same disk but by the ubuntu's startupdisk creator. IT went smoothly... without problems)))) 

sometimes it is helpful also swithching the pc off (for cooling) and having a bit rest))))

---

