---
title: "Hewlett-Packard ScanJet 5300C flatbed scanner won't work"
date: 2017-07-07
forum: MINT
---

### Post by Kevin McCready on 2017-07-07
My new version of Mint doesn't work with my scanner.

simple-scan in the terminal opens up a window and when I click "scan" on the menu, the scanner makes a tiny little noise then after a while a message in red says "Failed to scan. Unable to start scan"

```
 scanimage -L
device `avision:libusb:006:004' is a Hewlett-Packard ScanJet 5300C flatbed scanner

sudo sane-find-scanner

found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:001:003
found USB scanner (vendor=0x03f0 [Hewlett Packard], product=0x0701 [Hewlett Packard ScanJet 5300C]) at libusb:006:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
```

I don't know how to read a backend. Hope someone can help. I don't even know what a backend is, but it sounds painful.

My version of Mint is
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18
DISTRIB_CODENAME=sarah
DISTRIB_DESCRIPTION="Linux Mint 18 Sarah"
NAME="Ubuntu"
VERSION="16.04 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial

---

### Post by ajgreeny on 2017-07-07
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by CatKiller on 2017-07-07
This information may well be a decade out of date, but the last time I used SANE with a single-purpose scanner, my user hadn't automatically been put in the group that was able to access the scanner. If *sudo scanimage* works but *scanimage* doesn't then that is probably the problem. I can't remeber off-hand which group it is, but I'm sure you could find out, if that turns out to be the issue.

I didn't need to change any backend options with the scanner I was using at the time, but according to [this page]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD"), [this is the man page]("http://www.sane-project.org/man/sane-avision.5.html") for the backend you should be using.

---

### Post by Kevin McCready on 2017-07-08
Thanks. I think I may have created a problem for myself. I found a group which might be it. But I don't know if the name is correct. The group seems to be called "scanner:x:120:saned" . When I tried to add my account, it didn't seem to work. Because when I listed the groups I'm in, it wasn't listed. Also I'm not sure that myself as a normal user should be in the group called "sudo". If I've mistakenly added myself to the "sudo" group, how do I fix that?

---

### Post by CatKiller on 2017-07-08
I don't think there's anything wrong with your user being in the sudo group. It means that that user is authorised to use sudo to temporarily elevate their privileges to root, which you are. I think you were already in that group; I don't think it's something that you did.

Did scanimage work as root, but not as not-root? If not, then it isn't likely to be a permissions problem at all. As I said, that was the issue for me a long time ago, but it might not be the issue for you.

---

### Post by Kevin McCready on 2017-07-09
Thanks. I'm relieved to hear that. And it makes good sense. Yes, scanimage -L only works as root. I tried to change permissions but I haven't been able to. When I use simplescan from the menu, the scanner still just gives a little burp and then nothing happens.

---

### Post by CatKiller on 2017-07-09
I had a bit of a look at this last night, and the permissions are controlled by udev rules. Unfortunately, these went over my head a bit in the abstract. Back when I was facing this problem it was write access to the parallel port that was required, which had an easily-understood and widely-reported access mechanism.

I've already posted the link to the manpage of the backend you should be using. That links to the manpage of [sane-usb]("http://www.sane-project.org/man/sane-usb.5.html"), which tells you about the necessity of modifying the udev rules to allow non-root access, and provides the locations of README files to show you exactly how to do so.

That should be enough to get you started, but perhaps someone versed in udev rules will happen along to help you the rest of the way.

---

### Post by pdk-knight on 2017-08-07
Linux bigboy 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

simple-scan  failed to scan no scanners available.
'change' shows full details of Ace FlatbedScanner22
Having tried everything to no avail. Reloaded the o/s and simple-scan does not find a scanner when trying to scan.
Unable to report a bug as instructions are totally out of date.
my 16.04 doesn't have apport and the .conf files are blank.
There are a large number of complaints and no real answers.
Peter

---

### Post by pdk-knight on 2017-08-08
try going to [https://www.hamrick.com/download.html](https://www.hamrick.com/download.html)
and download vuescan. The site automatically gave me vux6495.tgz for ubuntu 16.04 64 bit
Peter

---

