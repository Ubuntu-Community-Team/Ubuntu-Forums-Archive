---
title: "Help with ISO install file to USB"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by jeffdmac on 2012-07-10
Hi Everyone
I'm a new member and I would like some help installing the iso file onto my USB stick.
As I am concerned about security (even on my iMac to my banks internet site), I would like to make a bootable USB so as I can boot an operating system on my iMac just for banking use.
I downloaded the file "ubuntu-12.04-desktop-i386.iso" and in the instructions on this link [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) , the instructions are not clear what you do with an ISO file so I would be grateful if someone can tell me what the correct line commands are  when I use the "Terminal" on my iMac to make the bootable USB.

Jeff...

---

### Post by wilee-nilee on 2012-07-10
Here is a ub loader that is pretty straight forward, if you are going to do banking it is generally suggested to have it be writeable. This way the information input in the user process like going to a bank is not saved

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by hive225 on 2012-09-27
I found this very helpful as well, many thanks!

---

### Post by whiteraven on 2012-09-27
If you use Unetbootin to make a bootable USB, occasionally you'll get a boot error depending on the make of the USB drive. I found a fix if you need it:

Make sure the USB drive is formatted Fat32, empty of all files, then run

mkdosfs -v -I /dev/sdg where sdg is the mount name of your device

Solution was found [**[COLOR="Blue"]here[/COLOR]**]("http://www.linuxquestions.org/questions/linux-newbie-8/boot-error-when-trying-to-boot-from-usb-786172/"), post #7

Hope this helps if it comes to that point.

---

