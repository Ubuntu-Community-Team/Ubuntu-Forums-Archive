---
title: "ubuntu mobile and kohjinsha SH8"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Shiruban on 2008-02-17
Hello,

I bought a SH8 kohjinsha 2 days ago and now I am preparing to put it under GNU/linux.
All the other posts talks about installing a feisty or gutsy, it is a solution, but does anyone has ever tried the ubuntu mobile? What is the status? It looks very promising but the installation doesn't look very easy (cf wiki) and only the samsung Q1 seems to be supported at the moment...
Another question is-it possible to run an openoffice under hildon desktop (the desktop use by ubuntu mobile) thekohjinsha has a full keyboard and so allowed some production it will be silly to not use it.

As now it is under vista premium so any linux could run on it, better, but I would like to use it as tablet pc optimally and also as a production pc, not easy...My biggest fear is all the hardware accessories : webcam, wireless, touchpad (should be possible cf other posts) but the "one seg tv tuner"?? For those who doesn't know what oneseg is a kind of mobile tv tuner use a  lot in japan on mobile phone and other mobile device. Nobody seems to care about it but me living in japan I want to use it, so challenge!

I like linux challenge, but for the kohjinsha challenge, especially the use of the ubuntu mobile edition, i would like some advices.

Thanks

---

### Post by punong_bisyonaryo on 2008-03-03
I'm trying out the Image Builder, but it keeps giving me a No such script error.

```
sudo image-creator -c create-project --platform-name mccaslin --project-name "Kohjinsha" --project-path "/home/jeff/Linux\ Stuff/Kohjinsha" --project-description "Kohjinsha SH6"
--------Platform rootstrap creation try: 1 ----------
Executing: debootstrap --arch i386 --variant=buildd --include=squashfs-tools,dosfstools,syslinux,module-init-tools,mtools,gpgv, gutsy /home/jeff/Linux\ Stuff/Kohjinsha http://archive.ubuntu.com/ubuntu/
E: No such script: http://archive.ubuntu.com/ubuntu/
--------Platform rootstrap creation failed result: 1 ----------
--------For try: 1.  Sleeping for 10 seconds... -----------------
--------Platform rootstrap creation try: 2 ----------
Executing: debootstrap --arch i386 --variant=buildd --include=squashfs-tools,dosfstools,syslinux,module-init-tools,mtools,gpgv, gutsy /home/jeff/Linux\ Stuff/Kohjinsha http://archive.ubuntu.com/ubuntu/
E: No such script: http://archive.ubuntu.com/ubuntu/
```

What am I doing wrong?

---

### Post by Shiruban on 2008-03-04
I don't know what is happening. I started to create an image with the gui but it was too long and went to sleep... what about with the gui does it fails the same?

---

