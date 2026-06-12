---
title: "xubuntu ISO corrupted?"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by geoffm on 2010-08-05
I want to try xubuntu because I am tired of the countless bugs and of waiting 3 minutes for gnome to load every time I boot.

I burned xubuntu-10.04-desktop-i386.iso on a DVD; the computer won't boot from it. I tried putting the installation on a flash drive using USB-creator and unetbootin:
when I made the flash drive using usb-creator, the program says "checksums do not match. retry?" then I say yes and it doesn't give the error message again.
when I boot from the USB, the installation loads until I am asked to choose a language. I choose english and then I get a black screen with
Uncompression error
--System halted


I downloaded the iso twice from different mirrors. I checked the sum using jacksum and the sum corresponds to the one provided in the SHA1SUMS file on the server. I also tried downloading if from the torrent. All give the same result.

What could be the problem?

---

### Post by stlsaint on 2010-08-05
Thats crazy that all those didnt work. Try the program: unetbootin

---

### Post by snowpine on 2010-08-05
If you are using Ubuntu now, all you need to do is:

```
sudo apt-get install xubuntu-desktop
```

Now you have Xubuntu. Log out and choose Sessions->Xfce from the login screen.

---

### Post by geoffm on 2010-08-05
unetbootin' didn't work either.
I didn't want to install xubuntu-desktop, I already did that last year and it screwed up quite a few things. besides, my system is bloated with too many things installed and I need to do a fresh install, that's the whole point in trying to get a faster boot.

I solved the problem using another USB drive created from another computer.

---

