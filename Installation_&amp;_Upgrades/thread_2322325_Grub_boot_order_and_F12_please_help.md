---
title: "Grub boot order and F12 please help"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by mnduck on 2016-04-27
Lenovo B50 laptop 
Celron (R) N2840 2.16 GHz
4gig Ram
Booting in Legacy Mode
Secure boot Off

After a good deal of work I have both Win8 and Lubuntu running and setup but on start up Grub dies reporting no OS, a  quick poke of F12 and I can start either OS and have access to the various options.

I've run boot-repair and the output is :- [http://paste.ubuntu.com/16079169](http://paste.ubuntu.com/16079169) 

I'm asking for help as I want Grub to offer Windows  1st then Lubuntu 2nd and not to have to use F12 to change the boot order.  The order is important so Win can restart during it's interminable updates. 

Any help wil be much appreciated.


ATB.              aamcle

PS.  I'm not very good on the command line    ...    :(

---

### Post by oldfred on 2016-04-27
While at some point you must have used Legacy mode as you have grub in the protective MBR for BIOS/CSM boot.
But your install now has /EFI/ubuntu for UEFI boot. And /boot/efi being mounted in fstab also required for UEFI boot. Perhaps from the Boot-Repair update.

So you need to boot in UEFI mode and choose the ubuntu entry.

If that does not work, you may need a work around.

No OS sounds more like UEFI/BIOS not finding something.

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side 
      
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) 
    
I thought there were some issues with Atom and newest kernels.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
xenial: invalid opcode when using llvmpipe With Intel video

and if Bay Trail, a boot parameter required:
[http://ubuntuforums.org/showthread.php?t=2314964](http://ubuntuforums.org/showthread.php?t=2314964)

When you get it working I can copy the commands you need to edit grub to default to Windows. Not really difficult, a bit of copy & paste. There is a gui tool to edit grub, but it modifies scripts and can complicate easy changes.

---

### Post by mnduck on 2016-04-28
Going back to UEFI has worked well enough, if left it boots to win 8 so the MS updates should still work  but I can use F12 to get to Lubuntu.


Many Thanks.          Aamcle

---

