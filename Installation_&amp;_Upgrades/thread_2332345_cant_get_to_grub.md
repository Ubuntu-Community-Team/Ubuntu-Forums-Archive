---
title: "cant get to grub"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by jpratik on 2016-07-30
im using a sony vaio e series with windows 8 pre installed. i am trying to dual boot.
Secure Boot is disabled and it is set to boot UEFI
[http://paste.ubuntu.com/21574297/](http://paste.ubuntu.com/21574297/)

---

### Post by jpratik on 2016-07-30
[http://paste.ubuntu.com/21583026/](http://paste.ubuntu.com/21583026/)

---

### Post by Bucky Ball on 2016-07-30
And what exactly is happening when you try to boot? You haven't given us much to work with bar the bootinfo ...

What I can say is that you now have two EFI partitions. Did you create one during install by using the 'Something Else' option?

See this at the bottom of your second bootinfo:

> Please do not forget to make your BIOS boot on sda3/EFI/ubuntu/shimx64.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

I could add other possibilities as to what might be going wrong but I'd be guessing as don't know what happening when you boot the machine.

---

### Post by jpratik on 2016-07-30
when i boot to EFI\ubuntu\grubx64.efi or [COLOR=#000000]*shimx64.efi *[/COLOR]i get a blank screen

---

### Post by oldfred on 2016-07-31
One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

But black screen is most often a video driver issues. What video card/chip do you have?
 
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

      
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
 i915.preliminary_hw_support=1 #Skylake some versions of Ubuntu -For linux kernels older than 4.3.x, i915.preliminary_hw_support=1 must be added to your boot parameters for the driver to work on the new Intel Skylake (6th gen.) GPUs. On a fully updated system running kernel 4.3.x and up, this step is unneccesary.

If you do not get grub menu, then press escape Key(perhaps more than once) right after BIOS/UEFI screen. Or if BIOS press and hold shift key.

---

### Post by gordintoronto on 2016-07-31
When you power on and lean on the shift key, still no grub?

---

### Post by jpratik on 2016-08-01
when i power on it shows the vaio logo then goes straight to a blank screen, pressing shift doesn't do anything.

---

### Post by deadflowr on 2016-08-01
I think if set to UEFI then it's the ESC key, instead of the shift key to access  the grub-boot menu.

Oh, yeah.
oldfred mentioned as much at the end of his last post...

---

### Post by jpratik on 2016-08-01
ESC doesn't do anything either

---

### Post by oldfred on 2016-08-01
Sony normally defaults to boot Windows unless  you have done one of the required work arounds already.
So is blank screen really from Windows?
Escape key should work if booting into grub, unless you have fast boot on in UEFI. Then you do not have time to press any keys.

---

