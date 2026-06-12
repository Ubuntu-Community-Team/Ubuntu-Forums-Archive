---
title: "Unrecognized bootloader version"
date: 2019-06-25
forum: Installation &amp; Upgrades
---

### Post by ralpho00 on 2019-06-25
Hi everyone,

A little info before I go on with my problem: 
I cleaned my ssd before doing any of this. 
I came from windows 10.

I've been trying to install kubuntu. I tried using Kubuntu 19.04 and Kubuntu 18.04.2 LTS, after several failed attempts, I tried elementary OS, but I had the same error.
This error appears after I select kubuntu from the grub.
I don't know what to do from here because this is fairly new to me.

Image of the error: (sorry for the real bad quality
[IMG]https://i.imgur.com/fzqfnIT.jpg[/IMG]
[IMG]https://imgur.com/a/613aDVY[/IMG]

---

### Post by oldfred on 2019-06-25
Please attach screen shots, not post in line.
Easy to attach with Forum's advanced Editor and paperclip icon.

You show nouveau, so nVidia? Which card?
Often other errors are just warnings & can be ignored.

With nVidia you need nomodeset boot parameter to boot live installer & first boot or until you install nVidia driver from Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by ralpho00 on 2019-06-30
Yes, I have an nvidia geforce 960m. I'll try your solution now.

---

