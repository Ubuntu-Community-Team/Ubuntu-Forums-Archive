---
title: "Not Install GRUB"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by Lamez on 2007-06-28
I am working on my own boot loader, so I do not want to install GRUB, how can I remove it from the installation?

On step 7, the last step, I click advance, and remove where ever GRUB was going to be installed, but then I get a error when the installer is installing saying GRUB cannot be installed, and it exits?

Please Help!

-Thanks

---

### Post by louieb on 2007-06-28
Sounds like you just installed Ubuntu and did not install GRUB. Isn't that what you wanted?
To test your Ubuntu install get the [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")

---

### Post by Lamez on 2007-06-28
No, I do want to install ubuntu, but not install GRUB, but the ubuntu installation forces me to install GRUB, how do I get around this?

---

### Post by louieb on 2007-06-28
Thats what you did  by aborting the Ubuntu install just before GRUB  is installed: Ubuntu is install on your PC but you can't use it until you install GRUB or some other boot loader / manager.

Or as an alternate to install the GRUB pointer in the MBR of the hard drive. You can install the pointer in the boot sector of the Ubuntu Linux / (root) partition.

---

### Post by Lamez on 2007-06-28
So you are saying, if I point GRUB to the root partition it will not pop up?

Or could I install and watch the process, and exit when grub is about to be installed?

They really show have this option if you want GRUB installed or not.

---

### Post by logos34 on 2007-06-28
> They really show have this option if you want GRUB installed or not.

Actually they do.  But it's on the text-mode Alternate Install CD.  You can say 'no' to grub, or even send it to a floppy disc.

Do you have a floppy drive?  On the 'ready to install' screen you could hit 'advanced' and type (fd0) in the bootloader pop up box.  Not sure it will work though.  Or just leave it blank and maybe it will install without putting grub on mbr (did'nt know you could that).  

But then you'd need something like SuperGrub to get into ubuntu in the meantime.

---

### Post by Lamez on 2007-06-28
Well I have my own boot loader, well it really is window's boot loader, but I changed it to also point to Ubuntu and windows.

Thanks I will check that "command" out.

---

