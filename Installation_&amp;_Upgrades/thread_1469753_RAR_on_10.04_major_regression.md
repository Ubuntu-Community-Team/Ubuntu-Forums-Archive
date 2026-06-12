---
title: "RAR on 10.04 major regression"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by kakyoism on 2010-05-02
Just found that my rar on 10.04 cannot unrar packages that include files of multibyte filenames (e.g., Asian languages). The error looks like this:

```
Cannot create /media/USB-WORK/hardy/kakyo/Music/1/21 ÂÒ¤ì´ò¤Á r£¨×î½K¥Ç¥â£©.mp3
Invalid or incomplete multibyte or wide character
```

But it did work on 8.04.
My language support was correctly installed and these files can be unrared on Windows.

Help!

---

### Post by kakyoism on 2010-05-02
bump, please help. 
Lots of data are in those rars...

---

### Post by kostkon on 2010-05-02
Are you using [*unrar*]("http://packages.ubuntu.com/lucid/unrar") or [*unrar-free*]("http://packages.ubuntu.com/lucid/unrar-free") or [*p7zip-rar*]("http://packages.ubuntu.com/lucid/p7zip-rar")?

If you are using unrar-free for example, remove it and install unrar instead.

---

### Post by kakyoism on 2010-05-02
unrar

---

### Post by kakyoism on 2010-05-02
Wait a second.

I just found that it's the problem of the destination drive I wanted to unrar my files to. It was an NTFS. After copying stuff to my EXT4 local drive, the unrar seems to work correctly now.

So it looks like there is some locale compatibility issue with NTFS drive, huh?

Anyone knows?

---

### Post by dragomang87 on 2010-11-09
do you have the "utf8" option in your fstab line for this NTFS partition?

---

### Post by kakyoism on 2010-11-09
No I didn't even put the drive in my fstab, just let it automount.

---

