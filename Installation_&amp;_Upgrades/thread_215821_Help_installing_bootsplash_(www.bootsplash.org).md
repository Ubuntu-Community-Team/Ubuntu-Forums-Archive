---
title: "Help installing bootsplash (www.bootsplash.org)"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by linuxnewbie946 on 2006-07-14
I have just compiled a kernel (2.6.17.4) from kernel.org and patched it with bootsplash. I edited xconfig to match everything from this guide [http://www.ubuntuforums.org/archive/index.php/t-177785.html]("http://www.ubuntuforums.org/archive/index.php/t-177785.html") but there is no bootsplash, just the regular kubuntu logo. Whats the problem?

---

### Post by linuxnewbie946 on 2006-07-15
I never found the answer for the bootsplash problem, but I did find Splashy ([http://splashy.alioth.debian.org/wiki/doku.php]("http://splashy.alioth.debian.org/wiki/doku.php")).
Splashy is a next generation boot splashing system for Linux systems. Unlike other splashig systems, it needs no patches to the kernel and it’s installed like a normal package. Make your boot process eye-candy with Splashy!

Some of Splashy’s most noticable features include:

    *
      Require zero kernel patches/full functionality in user-space
    *
      Boot/halt/reboot/runlevel-switch support
    *
      Progressbar support (with optional border)
    *
      Verbose mode (with F2/ESC keys)
    *
      Configuration file in XML
    *
      Cope with any video-mode resolution/size
    *
      Cope with 8, 16, and 24 bit framebuffers
    *
      Alpha channel (transparency) support
    *
      Video mode detection
    *
      Initramfs support
    *
      TrueType2 fonts support
    *
      Lots of image/animation file formats supported: jpg, png, gif, mpg, swf
    *
      Low dependencies and code in C to best perform
    *
      Full LSB support
    *
      Multiple themes support
    *
      Really easy to create new themes
    *
      X detection on exit
    *
      Smooth progressbar movement
    *
      Animations support
    *
      Fade in/out effects
    *
      Totally configurable

It is easier to install than bootsplash because you don't have to patch the kernel! It gives the same resolution as bootsplash and is themeable! Try it!

---

