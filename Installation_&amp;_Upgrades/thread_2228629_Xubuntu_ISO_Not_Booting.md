---
title: "Xubuntu ISO Not Booting"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by Keil_Miller_Jr on 2014-06-08
I have used all variants of ubuntu in the past and never had an issue. I usually install x or l 'ubuntu on friends older computers to get them up and operational again.

I'm trying to install xubuntu 14.04 on an HP Pavilion a530n 2.0ghz amd64. No matter how I burn the iso onto dvd, it is not bootable and I get a "[COLOR=#545454][FONT=arial]**NTLDR**[/FONT][/COLOR][FONT=arial, sans-serif][SIZE=2][COLOR=#545454] is Missing" error. I downloaded from server as well as torrent.
[/COLOR][/SIZE][/FONT]

[LIST]
[*][FONT=arial, sans-serif][SIZE=2][COLOR=#545454]I burn it in disk utility on my mac 10.9.2 multiple times. The iso isn't even mountable, but it will burn.
[/COLOR][/SIZE][/FONT]
[*][FONT=arial, sans-serif][SIZE=2][COLOR=#545454]I even followed the directions on the [ubuntu webpage]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows") to burn it on a windows xp machine using InfraRecorder.[/COLOR][/SIZE][/FONT]
[/LIST]
[FONT=arial, sans-serif][SIZE=2][COLOR=#545454]
Whats going on here? This is ridiculous. I never had an issue before. I'm just pissing away dvd's. I know the computer will boot a disc if it is bootable because [supergrubdisc]("http://www.supergrubdisk.org") I burned using disc utility will boot.
[/COLOR][/SIZE][/FONT]

---

### Post by LastDino on 2014-06-08
Does it have USB post? If it does, you should give a shot at Live USB method.

---

### Post by Keil_Miller_Jr on 2014-06-08
> **LastDino said:**
> Does it have USB post? If it does, you should give a shot at Live USB method.

It does. However, I'm all out of usb flash drives at the moment. Not trying to spend even more money to fix some one else's computer. Already spend 10$ on single layer dvd's because that windows app wouldn't take my dual layer dvd's, and I live in the country and have to spend money on fuel to go to the store.

---

### Post by pqwoerituytrueiwoq on 2014-06-08
are you sure it is trying to boot the DVD drive?
use the Boot menu available from the system's bios

---

### Post by Keil_Miller_Jr on 2014-06-08
> **pqwoerituytrueiwoq said:**
> are you sure it is trying to boot the DVD drive?
use the Boot menu available from the system's bios

Yes. I changed the bios via f1 to boot the dvd drive first. As I said, the computer will boot supergrubdisc, so I know the issue is likely not with that computer.

---

### Post by LastDino on 2014-06-08
Well, does it have a card reader port or do you've a card reader somewhere and happen to have some 4GB MicroSD card? 2GB would work too but you will need to go with Xubuntu on that one.

---

### Post by Keil_Miller_Jr on 2014-06-08
Well, I went to town and bought a 4gb usb disk since no one has an answer as to why the dvd created from iso doesn't work. Computer bios does not allow USB as a boot option. Booted supergrubdisk. List devices and partitions shows the two hard drive partitions and the supergrubdisk cd. It does not show the usb stick. No idea how I can boot from it if the computer does not recognize usb as a bootable source. I believe I confirmed this by inserting a windows 8.1 usb drive and supergrubdisk did not recognize that as well.

---

### Post by sammiev on 2014-06-08
Backup what ever you have on one of the USB drives you have and try Xubuntu on it. What does it take to write a ISO to a USB. 5 Min with a old and slow machine. Gee

---

### Post by Keil_Miller_Jr on 2014-06-08
> **sammiev said:**
> Backup what ever you have on one of the USB drives you have and try Xubuntu on it. What does it take to write a ISO to a USB. 5 Min with a old and slow machine. Gee

No need for attitude. Old computers like this won't support booting from usb. See [post #7]("http://ubuntuforums.org/showthread.php?t=2228629&p=13044854#post13044854").

I just read [this article]("http://www.linux.com/learn/tutorials/445010-weekend-project-use-the-plop-boot-manager-to-boot-older-computers-from-usb") and will try plop boot manager tomorrow after work. Hopefully it will work. I'd still like to know why the current distro iso will no longer burn bootable if anyone knows. I'm sure I'm not the only one that still uses those archaic things called compact discs.

---

### Post by grumblebum2 on 2014-06-08
Can you boot to the ISO cd/dvd on your pc?

---

### Post by Keil_Miller_Jr on 2014-06-08
Couldn't sleep. For anyone else having similar issues to myself, plop was able to boot from usb. It did not work with the front usb port on the computer. Moved the usb disk to the rear port and it worked.

**Burning Xubuntu iso to bootable dvd issue remains unresolved**, even though it's no longer needed by myself.

---

