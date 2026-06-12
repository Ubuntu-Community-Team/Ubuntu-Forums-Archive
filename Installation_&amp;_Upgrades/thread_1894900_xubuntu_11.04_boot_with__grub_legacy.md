---
title: "xubuntu 11.04 boot with  grub legacy"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by francois.e on 2011-12-13
I like the accessibility of changes provided by grub 0.98. What would be the menu.lst entry to call ubuntu 10.04 version under grub 0.98?

---

### Post by dandnsmith on 2011-12-14
You want something like:
```
title  Ubuntu 10.04LTS
        kernel /vmlinuz-2.6.32-21-generic root=/dev/sda8 ro quiet
        initrd /initrd.img-2.6.32-21-generic

```
suitably adjusted to meet local circumstances.

I too felt the need for this method, as I found I couldn't do the equivalent of hide and unhide in the newer grub, and cannot see a way to perform the same setup as a result.

---

### Post by francois.e on 2011-12-19
I will implement xubuntu 10.04 side by side with grub 0.98 as soon as I get enough time. And I will come back to report.

Thanks a lot Derek. :D

---

### Post by oldfred on 2011-12-20
Make sure you are using a newer grub legacy that has ext4 support. You also need a root command.

title    Most Current Ubuntu on sdc5
root    (hd2,4)
kernel   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

If you want the full path and kernel use dandnsmith's entry but include a root  line also.

I like grub2 once I understood it. I find I can edit 40_custom just like editing menu.lst and it avoids the issues of whether the edits in menu.lst are inside or outside the auto magic area.
It separates the updateable part form the auto part, also separates the parameters from the editable menu and exposes all the scripts for updating. At first I thought the separation was a problem but find it avoids many issues as those editing menu.lst did not understand all the parts of menu.lst and put entries in the incorrect places and wondered why they disappeared on updates.  Grub2's os-prober is worth its weight in gold. Grub legacy often had touble getting a Windows boot entry correct.

---

### Post by francois.e on 2011-12-29
> **dandnsmith said:**
> You want something like:
```
title  Ubuntu 10.04LTS
        kernel /vmlinuz-2.6.32-21-generic root=/dev/sda8 ro quiet
        initrd /initrd.img-2.6.32-21-generic

```suitably adjusted to meet local circumstances.

I too felt the need for this method, as I found I couldn't do the equivalent of hide and unhide in the newer grub, and cannot see a way to perform the same setup as a result.

I have tried:

title  xubuntu 10.04
       kernel (hd0,5)/boot/vmlinuz-3.1.0-1-486 root=/dev/sda6 ro quiet
       initrd=(hd0,5)/boot/initrd.img-3.1.0-1-486  

and

title  xubuntu 10.04
       kernel (hd0,5)/boot/vmlinuz-3.1.0-1-486 root=/dev/sda6 ro quiet
       initrd=(hd0,5)/boot/initrd.img-3.1.0-1-486
boot

This is not working

---

### Post by oldfred on 2011-12-29
Are you booting 11.04 not 10.04 as kernel 3.1 is for 11.04 unless you complied your own kernel?

You need a set root line. I do not think just the (hd0,5) at the beginning of the line work.

title  xubuntu 10.04
root (hd0,5)
       kernel (hd0,5)/boot/vmlinuz-3.1.0-1-486 root=/dev/sda6 ro quiet
       initrd (hd0,5)/boot/initrd.img-3.1.0-1-486  

or this which uses the link to the most current kernel:

title    Most Current Ubuntu on sda6
root    (hd0,5)
kernel   /vmlinuz root=/dev/sda6 ro quiet splash
initrd  /initrd.img

---

### Post by francois.e on 2011-12-29
You are right I am on 11.04, and I did not compiled my own kernel. I have tried:

title  xubuntu 11.04
       root (hd0,5)
       kernel (hd0,5)/boot/vmlinuz-3.1.0-1-486 root=/dev/sda6 ro quiet
       initrd=(hd0,5)/boot/initrd.img-3.1.0-1-486
boot

which does not work, file not found, error 15.

---

### Post by oldfred on 2011-12-29
Error 15 is often a conflict between grub2 and grub. You may have to fully uninstall grub & grub2 and reinstall grub from a chroot. Make sure the internet connection is working before deleting grub.

Uninstall grub2
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Sometimes this will get you working.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And sometimes this will bypass grub and boot, then you can fix grub from inside your install without the chroot.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by Quackers on 2011-12-29
You also missed out the " = " in the second line ```
root=(hd0,5)
```
not
```
root (hd0,5)
```

EDIT  Actually I don't know which is correct. Oldfred's first set of commands does not include the =, but his second does :-)
Oldfred, help! :-)

---

### Post by oldfred on 2011-12-29
Mixing up grub2 which uses set root = and grub legacy which uses root, uuid, or rootnoverify (on chainloads) and does not have an equals. Sorry, been a while since grub legacy.

Unless you have files in non-standard locations or these are not the kernels you have.

title  xubuntu 11.04
       root (hd0,5)
       kernel /boot/vmlinuz-3.1.0-1-486 root=/dev/sda6 ro quiet
       initrd /boot/initrd.img-3.1.0-1-486

Maybe just best to run this so we know exactly what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by francois.e on 2011-12-31
Being abroad for the Christmas holiday, and with another linux box a MSI340x laptop, I installed XUBUNTU on sda8. Finally, all the following entries work:

title 4 xubuntu 11.04
kernel (hd0,7)/boot/vmlinuz-2.6.38-8-generic root=/dev/sda8 ro quiet
initrd (hd0,7)/boot/initrd.img-2.6.38-8-generic
boot

title 3 xubuntu 11.04
root (hd0,7)
kernel (hd0,7)/boot/vmlinuz-2.6.38-8-generic root=/dev/sda8 ro quiet
initrd (hd0,7)/boot/initrd.img-2.6.38-8-generic

title 1 Most Current Ubuntu on sda8
root (hd0,7)
kernel /vmlinuz root=/dev/sda8 ro quiet splash
initrd /initrd.img

title 2 xubuntu 11.04
root (hd0,7)
kernel /boot/vmlinuz-2.6.38-8-generic root=/dev/sda8 rw quiet
initrd /boot/initrd.img-2.6.38-8-generic


Thanks to you all.

---

### Post by oldfred on 2011-12-31
Glad you got it working and thanks for posting answers, so others may find them. Edited main title so it is closer to what solution is.

Please post as solved as that also helps those searching to find best answers.

---

### Post by francois.e on 2011-12-31
Thanks a lot Oldfred, your patience and resolution is quite appreciated.:)

---

