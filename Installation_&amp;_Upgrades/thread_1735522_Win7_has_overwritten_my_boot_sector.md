---
title: "Win7 has overwritten my boot sector"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by sjbaugh on 2011-04-21
I have been running a dual boot system with Windows XP and Ubuntu 10.10 64 bit with the dual boot selected by Grub (placed y an Ubuntu install).

Recently I have installed Window 7 Home on a spare disc. My Bios allows me to select which disc to boot.

The Win7 installation has overwritten the boot sector on the WinXP/Ubuntu dic so that it is now not bootable.

I can sse all my Ubuntu files with a Live Linux Disc, so I can get all my files back.

Is there any easy way to re-install Grub or should I just do a clean install of Ubuntu, perhaps to a blank partition?

Thanks,

Steve

---

### Post by oldfred on 2011-04-21
Usually you just have to reinstall grub2's boot loader to the MBR, but which drive are you booting and which has windows & which Ubuntu?

If not sure post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by sjbaugh on 2011-04-21
Thanks,

My original disc had XP on it first. I then used an ubuntu installation to repartition the disc to add itself to the original disc. It may still have had Grub 1 on it, but not sure.

The Windows 7 on on a separate disc with nothing else.

---

### Post by sjbaugh on 2011-04-22
I did what it said in:

```
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
http://ubuntuforums.org/showthread.php?t=1014708
```

It worked perfectly and following a

```
sudo update-grub
```

command it found the windows 7 disc which I can now boot from grub as well. Windows XP is run by selecting Windows 7 from grub and then "Earlier Version of windows" from the Windows 7 boot loader screen.

Thank you very much, I have got my Ubuntu back! (now see what happens with the upgrade to natty next week...)


Steve

---

