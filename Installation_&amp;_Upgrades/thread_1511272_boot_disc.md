---
title: "boot disc"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by schwarza on 2010-06-16
greetings all

as you guys and gals can see, this is my first post and i am new here.

i imagine this topic would have been discussed before however i am not having much success in locating information to help resolve my issue.

------

i have burned the image to disk using windows. for some reason my usb drive would not display so could not use that method. i burned to dvd-rw.

when i place the disk into the rom drive and try load ubuntu it fails to boot. the boot order is correct and i get the message

booting from cd _

it tries for a short while then skips and launches the windows operating system.

-----

any ideas?

thanks

---

### Post by darkod on 2010-06-16
Sometimes it doesn't work correctly on cd-rw or dvd-rw. Also try burning it very slow, for cd 4x or 8x, for dvd even less, like 2x.

It's also option that the image file got corrupted during download.

---

### Post by schwarza on 2010-06-16
thanks for the speedy reply. i shall start from fresh and report back.

regards

---

### Post by schwarza on 2010-06-16
hi there.

i have re-downloaded, re-burned.. on slowest speed still not booting install disk.

is the USB install file structure the same as on the ROM? if I drag the files from the rom to the USB will that be the same as what Universal USB Installer would do?

regards

---

### Post by C.S.Cameron on 2010-06-16
Did you check the MD5SUM of the iso?

Following is a method of booting the iso directly:

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by schwarza on 2010-06-16
hi

thanks for the reply.

i have looked at the link you gave. thanks for that. 

although... i have no idea what to do with that info. hahahaha

regards

---

### Post by darkod on 2010-06-16
> **schwarza said:**
> hi there.

i have re-downloaded, re-burned.. on slowest speed still not booting install disk.

is the USB install file structure the same as on the ROM? if I drag the files from the rom to the USB will that be the same as what Universal USB Installer would do?

regards

No, it's not the same. Just copying the files doesn't make the usb stick bootable. Otherwise, the file structure is same, but it won't be bootable.

---

### Post by schwarza on 2010-06-16
hi darkod

i sort of guessed it would be different.

going to get a cd-r and dvd-r tomorrow and try again. i hope that fixes the problem...

on a different note, how come the install notes say to have a usb stick with 2gb free but the file size of iso/extracted files are only 672/5mb ?

will report back tomorrow.

---

### Post by darkod on 2010-06-16
> **schwarza said:**
> hi darkod

i sort of guessed it would be different.

going to get a cd-r and dvd-r tomorrow and try again. i hope that fixes the problem...

on a different note, how come the install notes say to have a usb stick with 2gb free but the file size of iso/extracted files are only 672/5mb ?

will report back tomorrow.

1GB is enough. Maybe they meant in case you want to create a space on the stick where you can keep documents instead of them being lost when you shutdown from live mode. Then you need additional space over the 670/680MB.

---

### Post by schwarza on 2010-06-17
install cd doesn't boot from a cd-r or dvd-r either.

i have downloaded and tried this twice with both amd64 and i386

there is currently windows server 2003 installed on the HD i am trying to install ubuntu on.

i am going stir crazy here chaps.

---

### Post by schwarza on 2010-06-17
i have managed to start the install now. thanks for your helps.

i had to reboot about 15 times before it started to install though. no idea why.

i am now at a crossroads that i could do with some advice about.

new thread started for this.

[http://ubuntuforums.org/showthread.php?p=9473628#post9473628](http://ubuntuforums.org/showthread.php?p=9473628#post9473628)

thanks

---

### Post by schwarza on 2010-06-17
Update.

I have now successfully created a working boot disk that passes integrity testing. as a note for the search on here i used the following.

Windows 7 Pro
maxell cd-r
infraRecorder @ 10x

---

