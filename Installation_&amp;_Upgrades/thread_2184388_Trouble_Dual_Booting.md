---
title: "Trouble Dual Booting"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by ejiang9 on 2013-10-28
So I've partitioned my Windows 8 drive and allocated 200GB for Ubuntu (13.10) and 10GB for swap. Everything seems to have installed correctly from my USB drive. When Ubuntu tells me to reboot before I can start using it, I do so but am not presented with the option of selecting which OS to boot into. I have tried checking my BIOS to see if it might be there but to no avail. I have tried Boot-repair (which gave me the link: paste.ubuntu.com/6321477) which did not work either. 

By the way, I have a 64-bit machine.

Any ideas?

---

### Post by Bucky Ball on 2013-10-28
Welcome. So you installed the 64bit version? 

Your pastebin link worked fine, BTW. I'm looking at your setup right now. ;)

Put this:

[http://paste.ubuntu.com/6321477/](http://paste.ubuntu.com/6321477/)

... in the address bar of a browser. You don't have grub in sda, you have it in sdb and that is probably the issue. You also have EFI setup which I know nothing about but do know that it needs specific tweaking. You might want to do some research there.

---

### Post by Bucky Ball on 2013-10-28
Welcome. So you installed the 64bit version? 

Your pastebin link worked fine, BTW. I'm looking at your setup right now. ;)

---

### Post by ejiang9 on 2013-10-29
I reinstalled Ubuntu, and this time I paid particular attention to where I installed the bootloader (I installed it in the /sda6, where my Ubuntu partition is); Grub still did not load upon boot, so I boot-repaired again and still no change. (By the way, I knew my paste-bin link worked. I was referring to the boot-repair that didn't work in my prev post)

I'm honestly at a dead end. I've tried holding either shift or esc while at the BIOS screen.

No forum seems to have a solution to this.

---

### Post by Bucky Ball on 2013-10-29
If you're booting into Ubuntu fine (just not getting grub) do this in a terminal:

```
sudo update-grub
```

Try hitting esc/shift (not sure which in your release) on a reboot. If still nothing, try grub on sda1. Do this:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Bucky Ball on 2013-10-29
Do this:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

You want grub on sda1.

---

### Post by fantab on 2013-10-29
I think you are using EasyBCD. Remove it if you want to keep things simple. EasyBCD complicates boot.

To boot Ubuntu in EFI it needs to be installed in EFI mode, and to install it in EFI mode the Ubuntu DVD/USB MUST be booted In EFI. If you boot Ubuntu install disk in UEFI you will see a black screen with options, otherwise you see regular colors.

---

### Post by oldfred on 2013-10-29
Your original install showed Ubuntu as a boot option and you just needed to make it the default.

       BootOrder: [COLOR=#ff0000]0001[/COLOR],0000
Boot0000* Windows Boot Manager
Boot0001* EFI USB Device
BootCurrent: 0001
BootOrder: [COLOR=#ff0000]0002[/COLOR],0001,0000
Boot0000* Windows Boot Manager
Boot0001* EFI USB Device
Boot[COLOR=#ff0000]0002[/COLOR]* ubuntu

Change boot order so 0002 is first. Not sure why script shows several boot orders. One may just be last boot, and another BIOS or secure boot order?

---

### Post by ejiang9 on 2013-10-29
@Bucky Ball
After I've installed Ubuntu and it asks to reboot, I remove the USB I installed from before the BIOS screen and it just boots straight into Windows. I can't boot into Ubuntu at all because grub isn't loading. I tried plugging the USB back in and "Try Without Installing" so I can access terminal. 'sudo update-grub' doesn't solve the problem. Just to clarify: is a LiveCD the USB drive from which I originally installed Ubuntu?

@fantab
I am pretty sure I installed and booted Ubuntu in UEFI. If I am somehow using EasyBCD, I didn't do so on my own volition. 

@oldfred
Where do I go about changing the boot order?

Thanks for all the responses, by the way!

---

### Post by oldfred on 2013-10-29
From UEFI/BIOS you should have boot devices. Back in BIOS days it was just the hardware, but with UEFI it will include all the boot loaders found in the efi partition. 
If secure boot is on, then UEFI only shows secure boot systems as boot options. But with secure boot off, you may get both UEFI and CSM/BIOS boot options.

---

