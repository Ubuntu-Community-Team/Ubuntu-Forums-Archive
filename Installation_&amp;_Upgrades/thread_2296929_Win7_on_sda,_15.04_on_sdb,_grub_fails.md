---
title: "Win7 on sda, 15.04 on sdb, grub fails"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by sorceror171 on 2015-09-29
Dell Optiplex GX620. Two SATA drives; sda is 500GB and has Windows 7, sdb is 35GB, newly-installed, and I put Xubuntu 15.04 64-bit on it. But when I boot from hd, grub puts out an error:

```
error: no such partition <GUID that doesn't exist on this system>
```

Tried booting from CD and manually reinstalling grub - same error. Then used the boot-repair ([http://paste.ubuntu.com/12620871](http://paste.ubuntu.com/12620871)), but the same error.

I find it hard to believe that this is *that* unusual a situation. Is there a BIOS setting I'm missing or something? Or a special grub option? For the moment I used a Hirens boot CD to restore Win7's MBR, so at least Win7 can boot, but this obviously not ideal.

---

### Post by oldfred on 2015-09-29
Are you selecting sdb in BIOS to boot from.
A few systems will not boot from certain types of second drives. Is this a drive caddy in DVD slot or some similar device or just a standard SATA hard drive in the second SATA port?
How much RAM?
With nVidia you will need nomodeset on first boot in grub or until you install the correct nVidia driver. Your card is older so you need a legacy driver for it. Do not install most current.

If BIOS shows sdb and you can boot from it, once grub is working best to also have a Windows boot loader on sda. Then if issues with sdb, you can go into BIOS or one time boot key & directly boot Windows. You can use Boot-Repair's advanced mode to choose Windows and sda to install a Windows like boot loader or use your Windows repairCD/flash drive to repair Windows.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
      
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by sorceror171 on 2015-09-30
> **oldfred said:**
> Are you selecting sdb in BIOS to boot from.

No... should I have to? I'd like to just boot off of sda, and have the grub there either boot Windows on sda or boot Ubuntu off of sdb. If there's some kind of special grub configuration I need for this, I'll do it, but I figured this was a fairly typical configuration.

The drives are both just SATA drives plugged into SATA ports, nothing fancy. The system has 4GB of RAM.

> **oldfred said:**
> With nVidia you will need nomodeset on first boot in grub or until you install the correct nVidia driver. Your card is older so you need a legacy driver for it. Do not install most current.

I'll see about that, but if I can get to the point of a command line I can handle driver installs, but I have to get things to boot first. ;)

---

### Post by oldfred on 2015-09-30
Try booting from sdb with one time boot key. Not sure what Dell uses, but many systems use f10 or f12.
Everything in script shows your UUID as the 88298....
Is that what it is saying does not exist?
If so try Boot-Repair's advanced mode and total uninstall/reinstall of grub.

---

### Post by sorceror171 on 2015-10-02
Finally figured it out. The second SATA drive, sdb, was disabled in the BIOS. It could be seen after booting - from, say, an install CD - but not when grub was running. Once I enabled it in the BIOS, I was able to get a boot menu, and boot both Ubuntu and Windows.

---

