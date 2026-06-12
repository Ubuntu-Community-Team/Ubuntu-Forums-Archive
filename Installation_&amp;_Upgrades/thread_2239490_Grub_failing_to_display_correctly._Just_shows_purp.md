---
title: "Grub failing to display correctly. Just shows purple outline."
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by matthewrhodes227 on 2014-08-14
Hello, I have just installed ubuntu 14.04 on its own on a 128gb m2 sata with my swap and home partition on a seperate 1tb hd. My laptop is a lenovo s540 touch with intel integrated graphics and a  AMD Radeon HD 8670M.

Once I had installed it I had issues with it being in low graphics mode. I was unable to select nomodeset as the grub was not displaying properly. I changed to using gdk instead of lightDM. When I booted in finally the updated graphics drivers reverted to lightDM and now works. 
Grub however is still behaving the same and not displaying properly. 

On my boot drive it is a guid partition table with a 40mb efi partition. I have tried reinstalling grub with no success.

---

### Post by oldfred on 2014-08-14
When you boot is it using Intel or AMD? 

If booting in UEFI mode you may need to use escape key to get grub menu. In BIOS hold shift until menu appears.

This will tell what modes grub supports, but may depend on which video driver you boot with:
 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

Then you can edit grub's gfxmode, if you can boot into your system:
      
 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


      
 gksudo gedit /etc/default/grub

---

### Post by matthewrhodes227 on 2014-08-15
Thanks oldfred. Ok feel it bit silly now. Pressing esc brought up grub I didn't think to do that. I also discoverers that if I used anything other then the open source drivers for my amd video card then unity will hang at login. Apart from that I think I have functioning system.

---

