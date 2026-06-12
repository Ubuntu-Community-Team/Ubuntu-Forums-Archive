---
title: "Installing Ubuntu from flash drive but error says it can't find the CD-ROM"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by penguinboy561 on 2014-09-23
First, I've never tried installing any flavor of Linux  before, so bear with me. I created a bootable flash drive using  Universal USB Installer. I ran the Ubuntu installer, but it quickly  errors out with several error messages:

  ```
[INDENT]Install: invalid user 'ubuntu'
Install: invalid user 'ubuntu'
Using CD-ROM mount point /cdrom/
...
E: Line 1 too long in source list /etc/apt/sources.list.
E: No CD-ROM could be auto-detected or found using the default mount point.
You may try the --cdrom option to set the CD-ROM mount point.
See 'man apt-cdrom' for more information about the CD-ROM auto-detection and mount point.
Use of uninitialized value in concatenation (.) or string at /usr/share/per15/Debconf/Config.pm line 22.
Umount: cant umount /cdrom: Device or resource busy
Umount: cant umount /cdrom: Device or resource busy
Umount: cant umount /cdrom: Device or resource busy
...
Chown: invalid user: 'root:ssl-cert'
pwchk: cannot open /etc/passwd
chown: invalid user: 'root:root'
chmod: cannot access '/etc/passwd': Input/output error
chown: invalid user: 'root:shadow'
usermod: user 'root' does not exist
install: 'invalid user 'ubuntu'
install: 'invalid user 'ubuntu'
[/INDENT]

```
  After that it just stalls indefinitely. There seem to be a number of things going on here, and I have no idea.  It mentions the CD-ROM several times, but I am using a flash drive, not a  CD or DVD. I verified that the CD drive was connected correctly. I even  tried disconnecting it just to take it out of the equation, but it made  no difference. Any assistance would be greatly appreciated.

---

### Post by mastablasta on 2014-09-23
it seems that the image was not done well.

try using unetbootin or Linux live usb or Yumi instead if you are on windows. but first make sure the md5 sum has matches the one on the website as they have to be exactly the same. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by penguinboy561 on 2014-09-27
Thanks, that did it! I downloaded the image again, made sure the md5 sum was correct, and the install went properly.

---

