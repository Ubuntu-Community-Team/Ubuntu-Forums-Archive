---
title: "Grub won't go away"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by Dugatee on 2014-10-18
Recently I tried Ubuntu and didn't like it, so I uninstalled. Everything went smoothly except for the fact that whenever I boot my computer it boots to GNU Grub command line and I have to type "exit" to continue on my way. Also my computer runs slightly slower and crashes for no apparant reason much too often. I've tried everything that comes up when I google to get rid of this stupid command line including "bootrec /fixmbr" in the windows command prompt. Please help me get rid of this godawful command line and hopefully return my computer back to normal.

---

### Post by Vladlenin5000 on 2014-10-18
Hi, welcome.

You need to boot a Windows installation DVD/USB or a Windows boot repair CD/USB and follow instructions. Windows will happily replace the entry previously needed for dual booting.

```
Also my computer runs slightly slower and crashes for no apparant reason much too often.
```
This has nothing to do with the leftover GRUB. I recommend you proceed with the usual Windows troubleshooting.

---

### Post by fantab on 2014-10-18
If you have Ubuntu DVD/USB then boot with it and 'Try ubuntu'. Open Terminal [ctrl+alt+t], run the following commands and post the output here:
```
sudo parted -l
```

What windows do you have in there, Windows8?
If it is Windows 8 and set up with ESP then returning to normal windows boot is as simple as changing the boot order in UEFI menu to boot Windows first...
You can remove Ubuntu entry completely by installing ***efibootmgr*** in Live ubuntu and run it to remove Ubuntu entry.
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

---

