---
title: "Solved: Can't get a clean copy"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by jthoward013 on 2017-08-11
Yes I can't seem the get a clean copy of Ubuntu. I've tried 17.04 16.04.3 and 16.04.1. Ive tried direct from Ubuntu, torrents, and mirror sites. I'm using rufus to make a usb. I try to load it and get a black screen then the kernel loads goes to purple screen for couple minutes the back to black screen with message about something missing. My system mb 990 cpu amd 9590 at 5.2g.

---

### Post by QIII on 2017-08-11
Hello!

"Something about something missing" gives us precious little to work with.

Could you give us the exact message?  Take a picture with your cell phone and post it if you need to.

---

### Post by mastablasta on 2017-08-11
how do you know they are not clean copies? check the md5sum after download if it is the same as on server then your download is good.: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

next. create the USB using some other program (Yumi, Unetbootin, pendrive linux...). for example: [https://www.pendrivelinux.com/](https://www.pendrivelinux.com/)
if you are on windows i can recomend LiLi: [https://www.linuxliveusb.com/](https://www.linuxliveusb.com/)
if you are on Ubutnu you can just use startup disc creator: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
this was we will eliminate program as the cause. if possible you can also switch the USB drive to a known good one.

then boot from it and check the USB for errors. if all is good we can continue.

boot from USB and try nomodeset or other boot option that has to do with graphics. : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also what is your graphics card? AMD 9590 ?

is the System using UEFI or BIOS?

---

### Post by shridhar-kapshikar on 2017-08-11
The program md5sum is designed to verify data integrity using the MD5. An MD5 hash comparison detects changes in files that would cause errors. 
Please refer below link 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As you mentioned, you are using Rufus to make use please ensure below option to be selected while making USB,
-> Partition scheme and target file system type: gparted 
-> Filesystem: FAT32.

please refer below link
[https://rufus.akeo.ie/?locale](https://rufus.akeo.ie/?locale)

---

### Post by jthoward013 on 2017-08-11
Solved. Obviously something wrong with the usb drive although loaded with rufus with check for bad sectors checked and quick format unchecked showed no problems. After downloading 17.04 again and fixing the bluray ( another story altogether ) burned a disc and worked perfect.

---

