---
title: "grub-again"
date: 2004-12-02
forum: Installation &amp; Upgrades
---

### Post by in_omaha on 2004-12-02
Ok, here's the deal. I have XP Pro on my 120gb C drive and just installed Ubuntu on my 60gb D drive. Everything installed fine until I got to grub. If I install it to the MBR, it just hangs and show Grub.. I tried to install it to a floppy by typing /dev/fd0 when it asked where to put it the second time, but it told me it failed. I continued without installing a boot loader. Can someone please tell me how to get this working. It seems to be a grub problem, as it has happened with other distro's.

Thanks in advance.

---

### Post by risager on 2004-12-03
Hi,

I had the same problem, and I have not been able to solve it  : ](*,) . 
But you will be able to find some suggestions on what to do at the following FAQ

[My system froze at GRUB](http://ubuntuforums.org/showthread.php?t=2689)

---

### Post by Mr Fancypants on 2004-12-04
I had a similar problem when tryign to set up dual booting system from a drive w/ XP already installed and putting Ubuntu on a different drive. With XP on the IDE primary and Ubuntu on IDE secondary the Grub install failed. However, when I switched swapped the drives' IDE status (primary/secondary) Grub installed just fine.

The next problem is, NOW you've a drive on secondary where XP thinks it's on primary. You have to modify the grub configuration (e.g. the menu.lst file) for your XP install using something like the following (from [here](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)):

```
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot
```

The map command essentially fools windows into thinking the primary/secondary are reversed from reality. 

 Hope that helps.

-Jerod

---

### Post by wallijonn on 2004-12-05
If you have two disk drives with WXP on the first one and Ubuntu on the second one, GRUB will always install to the first HD.

If you have two disk drives wirh Ubuntu on the first one and WXp on the second one, GRUB will always install on the first HD.

If you have disconnected the WXP drive and installed Ubuntu on the second drive, then it is easy enough to go into your BIOS and select HDA1 (the second drive) as the boot priority first boot disk and it will boot fine. If you select HDA0 (the first drive) it will boot into WXP.

If you boot into the second drive through the BIOS you can then create a boot floppy for Ubuntu. See the HOWTO section where I describe how to do it.

Personally, I would not bother with GRUB installing to the MBR. The easier thing might be to install it to HDA1 (the second disk, 60GB) root then setting the bootable flag. Then you can modify WXP's boot loader to point to Ubuntu.

---

### Post by cabu on 2004-12-05
[QUOTE=wallijonn]If you have two disk drives with WXP on the first one and Ubuntu on the second one, GRUB will always install to the first HD.

If you have two disk drives wirh Ubuntu on the first one and WXp on the second one, GRUB will always install on the first HD.

If you have disconnected the WXP drive and installed Ubuntu on the second drive, then it is easy enough to go into your BIOS and select HDA1 (the second drive) as the boot priority first boot disk and it will boot fine. If you select HDA0 (the first drive) it will boot into WXP.

If you boot into the second drive through the BIOS you can then create a boot floppy for Ubuntu. See the HOWTO section where I describe how to do it.

Personally, I would not bother with GRUB installing to the MBR. The easier thing might be to install it to HDA1 (the second disk, 60GB) root then setting the bootable flag. Then you can modify WXP's boot loader to point to Ubuntu.[/QUOTE]

If I'm not mistaken, hda1 would be the first primary partition on the 1st disk (the 120GB disk). The 60GB disk would be hdb, hdc, or hdd.

---

