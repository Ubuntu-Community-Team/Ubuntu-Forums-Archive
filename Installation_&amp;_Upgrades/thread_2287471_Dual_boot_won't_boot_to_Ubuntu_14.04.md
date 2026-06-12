---
title: "Dual boot won't boot to Ubuntu 14.04"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by kevin171 on 2015-07-19
I just completed my dual boot setup with Win7 Pro and Ubuntu 14.04.  Initially I had issues getting grub to load but OldFred hooked me up and grub comes up fine now.  I have Ubuntu set as my default boot but I can't get it load load at all.  Windows 7 boots fine but if I select Ubuntu it goes to the purple background and just sits there.  I booted to live CD and installed boot-repair.  I even tried to remove grub and reinstall it but nothing works so far.  I got an output from boot-repair, hopefully someone can tell me what I need to do.  [http://paste.ubuntu.com/11904609/](http://paste.ubuntu.com/11904609/).  Thanks in advance!

Kevin

---

### Post by oldfred on 2015-07-20
If you get grub menu, then you are past what grub does to boot & Boot-Repair fixes.
You are into kernel loading & driver issues.
Often a video issue and you show this:

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770] [1002:68b8]
Subsystem: Hightech Information System Ltd. Device [1787:200b]
Kernel driver in use: radeon

But I have nVidia and do not know much about AMD.

May be best to edit title and see if those that know AMD video issues will respond.

Since you already have radeon driver, not sure if nomodeset still works?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 AMD drivers alternatives
[http://ubuntuforums.org/showthread.php?t=2256824](http://ubuntuforums.org/showthread.php?t=2256824)

   open (Gallium3D) and closed-source (Catalyst) driver
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

