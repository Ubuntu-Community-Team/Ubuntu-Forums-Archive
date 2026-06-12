---
title: "Problem Creating USB flash drive"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by crazygeo on 2010-07-28
Go gently - this is my first foray into the world of Ubuntu ...

I'm getting 'File is broken' messages while trying to set up Ubuntu 10.04 on 4GB flash drive.

Following instructions on [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download),
I downloaded Ubuntu Desktop Edition - 32bit version. It shows up as:
ubuntu-10.04-desktop-i386.iso    size on disk 542 MB (568,475,648 bytes)

I downloaded and ran the Universal USB Installer. It shows up as:
Universal-USB-Installer-v1.7.4.exe    size on disk 816 KB (835,584 bytes)

I get 56 7-zip Diagnostic messages. A small sample shows:
0    C:\Documents and Settings\My Downloads\ubuntu-10.04-desktop-i386.iso
1    Data error in '.disk\casper-uuid-generic'. File is broken
...
5    Data error in 'casper\filessystem.squashfs'. File is broken
...
55    Data error in 'preseed\ubuntu.seed'. File is broken

Should I download the iso file again, or have I missed something in the install?

I'm running Windows XP sp3 on an IBM T60 Thinkpad

Thanks.

---

### Post by bobpress on 2010-07-28
You may need to download again.  The size of the iso seems off, should be about 699M.

---

### Post by crazygeo on 2010-07-29
bobpress,

Thanks for the suggestion - you were correct.

I should have looked at the filesize of the download and made sure it was close to the 699.

Downloaded again and got the complete file - setup was fast and successful.

Thanks again for taking the time to help.

---

### Post by CharlesA on 2010-07-29
Glad it was something simple.

Don't forget the mark the thread as solved. Thread tools > mark as solved.

---

### Post by lestat60628 on 2012-01-17
Hi, I am new to linux also and in creating the usb flash drive I have been getting the 7-zip:diagonistic message
0 c:\users\#name#\downloads\ubuntu10.04.3desktop-i386.iso
1 data error in 'casper\filesystem.1386.iso-squashfs'. file is broken

I downloaded from the site and the iso is 688 - 686mb.  I have windows7-64 what am I doing wrong?

---

