---
title: "Bootmgr from boot from USB"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by MarkDome on 2012-05-27
Hi Guys and Girls,

Ive a little problem, I've an old laptop with out a screen. So I've an extended screen but I'm not able to enter my bios, I've seriously no idea why. Tried pressing F2, F8 F10 F12 and also 'del' but nothing happened.

So I downloaded PLOP bootmanager and now I can boot from my USB.

I tried 2 ways to make the USB bootable. Its a 1GB usb.
Way 1 was with DISKPART - SELECT DISK 1 - CLEAN - CREATE PARTITION PRIMARY - SELECT PARTITION - ACTIVE - FORMAT FS=NTFS

the second way was with unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Boot ways give the error
'bootmgr onbreekt
Druk Ctrl+Alt+Delete om opnieuw te starten' 
(missing bootmgr, press Ctrl+Alt+Delete to reboot)

What is the problem? Can someone help me
Downloaded Ubuntu-12.04-server-amd64.iso from ubutu.com (download/server)

Please help me out :)
greetz Mark

---

### Post by raja.genupula on 2012-05-27
have you checked the ISO image for any errors ? ? 
[click here]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by MarkDome on 2012-05-28
I tried it and md5 

MacBook-Pro-van-Mark:~ turinhinhurin$ md5 /Users/turinhinhurin/Downloads/ubuntu-12.04-server-amd64.iso 
MD5 (/Users/turinhinhurin/Downloads/ubuntu-12.04-server-amd64.iso) = f2e921788d35bbdf0336d05d228136eb

And that's the same as the hash at 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

So it seems valid

---

### Post by raja.genupula on 2012-05-28
its looking like you havent prepared proper LIVE USB . give a try with formatting USB to FAT . 

unetbootin should have to take care of all the things , try again with that . 

if you have any Ubuntu PC try with startup disk creator .

---

### Post by MarkDome on 2012-05-28
Made it FAT
Now I got some new messages

"verwijder schijven of media. Druk op een toets"
"Remove disks or mediums. Press a key"

If I press a key, the same message appear.
I press a key and after my computer gave a new message

"Reboot and Select prober boot device or Insert Boot Media in selected Boot device and pres a key"

---

### Post by raja.genupula on 2012-05-28
you set boot from Removal disk in BIOS boot priority's .

---

