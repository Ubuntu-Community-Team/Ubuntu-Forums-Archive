---
title: "Boot problems (incl. GRUB error 17)"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by ro88o on 2007-03-20
Hi,

The other day I went into my BIOS to change some settings however I decided against it in the end and exitted without saving changes. However when my computer rebooted it stopped while trying to load GRUB with Error 17.

I tried fixing this by using the cd from [www.sysresccd.org](www.sysresccd.org), using this I typed "grub" to make a GRUB prompt appear then typed "setup (hd0)".

Now when I reboot my system it no longer even says it's trying to load GRUB.

Does anybody know how I fix this? I just want to be able to load Windows again :S

Tom

---

### Post by confused57 on 2007-03-20
> **ro88o said:**
> Hi,

The other day I went into my BIOS to change some settings however I decided against it in the end and exitted without saving changes. However when my computer rebooted it stopped while trying to load GRUB with Error 17.

I tried fixing this by using the cd from [www.sysresccd.org](www.sysresccd.org), using this I typed "grub" to make a GRUB prompt appear then typed "setup (hd0)".

Now when I reboot my system it no longer even says it's trying to load GRUB.

Does anybody know how I fix this? I just want to be able to load Windows again :S

Tom
You may have better luck reinstalling grub with the Ubuntu live cd(or any Linux live cd):
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by ro88o on 2007-03-29
I've tried the tutorial and re-installed GRUB to my mbr, however when my system tries to boot up I get:
> 
Verifying DMI Pool Data ...........
Boot from CD :
Boot from CD :
Boot from CD :

... and then nothing, it just stops there whereas it used to load GRUB. Any ideas :( ?

Earlier today I tried to do a full install from the liveCD thinking that may fix it but it just froze when trying to detect the current partitions on my hard drives.

---

### Post by phidia on 2007-03-29
Once you are in your install either by doing chroot from the livecd or some other way; try this:> grub
One grub starts you should get the grub prompt i.e > grub>
In grub do > find /boot/grub/stage1
Hopefully you'll get some output from that.
Next do > root (hdX,X)
the "X's" will be replaced by what grub says your root partiton is from the find command. If that provides a filesystem type and no errors  then do:
> setup (hdX,X)
Good luck

---

### Post by ro88o on 2007-03-30
That's what the tutorial tells me to do which I tried and it didn't work.

---

### Post by ro88o on 2007-04-05
Ok I finally fixed it - thought I'd post what I did on here in case it helps anyone in the future...

I decided to just do a clean linux install on my linux partition in the end instead of mucking about trying to fix GRUB.
However the installation was freezing when trying to detect current partitions. To solve this I unplugged my secondary unformatted/unpartitioned SATA drive and tried the install again. This time it ran and I created a fresh linux install which in turn fixed my mbr for me and GRUB now loads again.

---

