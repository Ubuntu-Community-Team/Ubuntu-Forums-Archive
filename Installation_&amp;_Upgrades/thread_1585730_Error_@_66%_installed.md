---
title: "Error @ 66% installed"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by Brokencar on 2010-09-30
> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.Hello I am new to this forum and this OS. I have searched for this in this forum I couldn't find this problem.  So please bear with me. I recently visited my uncle and he had Ubuntu on his laptop I got to check it out.  I liked it so thought I would put it on old 160G HD. I quit using this hd when it started giving me a missing file error. No big deal, I had a a 40g I wasn't using. So I downloaded " Install Ubuntu 10.04.1 LTS ", and the USB loader [pendrivelinux]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). And every time I install it I get this error you see above @ 66% installed.I have re downloaded the file 3 times (once from a different server), and reformatted the thumb drive every time. Yet every time I get the same error at the same point. I have also tried installing on my 40g hd that is perfect working order. Same result. :confused:    Right now I'm running the desktop off the thumb drive right now with no problems other than speed. 

So any insight would be appreciated. 
Thanks J


Edit to add this log, I think it may be related. 

> Oct  1 02:30:05 ubuntu ubiquity[9378]: progress_loop()
Oct  1 02:31:10 ubuntu kernel: [ 3635.874783] Adding 2240504k swap on /dev/sda5.  Priority:-1 extents:1 across:2240504k 
Oct  1 02:31:11 ubuntu partman: mke2fs 1.41.11 (14-Mar-2010)
Oct  1 02:32:32 ubuntu kernel: [ 3718.002664] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct  1 02:32:38 ubuntu ubiquity[9378]: debconffilter_done: ubiquity.components.partman_commit (current: None)
Oct  1 02:32:40 ubuntu python: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Oct  1 02:32:40 ubuntu python: keeping language packs for: en
Oct  1 02:46:12 ubuntu kernel: [ 4537.500785] SQUASHFS error: zlib_inflate error, data probably corrupt
Oct  1 02:46:12 ubuntu kernel: [ 4537.500807] SQUASHFS error: squashfs_read_data failed to read block 0x599a
Oct  1 02:46:12 ubuntu kernel: [ 4537.500819] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500823] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500871] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500875] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500900] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500905] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500923] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500927] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500942] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500945] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500957] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500961] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500974] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500977] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.500988] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.500992] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:46:12 ubuntu kernel: [ 4537.501007] SQUASHFS error: Unable to read data cache entry [599a]
Oct  1 02:46:12 ubuntu kernel: [ 4537.501010] SQUASHFS error: Unable to read page, block 599a, size 2ddd
Oct  1 02:47:10 ubuntu pulseaudio[2801]: protocol-esound.c: write(): Broken pipe
Oct  1 03:17:01 ubuntu CRON[14137]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


---

### Post by sanderd17 on 2010-10-01
Maybe try with a CD. Pendrive installs are rather new and can cause some problems.

---

### Post by sikander3786 on 2010-10-01
First of all check the MD5SUM of the downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Secondly use some other flash drive if available. And also try an alternative to Pendrivelinux i.e,

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by Brokencar on 2010-10-01
> **sanderd17 said:**
> Maybe try with a CD. Pendrive installs are rather new and can cause some problems.

I would have perfered too, however this machine doesn't have a disk drive. :(
Although I may have to add one for this purpose.

---

### Post by Brokencar on 2010-10-01
> **sikander3786 said:**
> First of all check the MD5SUM of the downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Secondly use some other flash drive if available. And also try an alternative to Pendrivelinux i.e,

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)


I will try that now and post results.

---

