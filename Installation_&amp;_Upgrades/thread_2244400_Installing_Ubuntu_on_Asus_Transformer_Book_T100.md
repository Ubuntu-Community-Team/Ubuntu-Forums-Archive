---
title: "Installing Ubuntu on Asus Transformer Book T100"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by J0nDaFr3aK on 2014-09-16
Hello everyone,
I recently bought an Asus TB T100. At University, the lab pcs have Ubuntu on it, which is going to be used for tests too.
I read that installing Ubuntu 13.04 on this machine is kind of a problem. Too many incompatibility issues...

Does anyone know if this has been fixed with Ubuntu 14.04.1?

At the moment I have a genuine copy of Windows 8.1 installed on it.

Thanks everyone.

---

### Post by fantab on 2014-09-16
> I read that installing Ubuntu 13.04 on this machine is kind of a problem. Too many incompatibility issues...

Does anyone know if this has been fixed with Ubuntu 14.04.1?


What kind of incompatiblity are we talking about?

I suggest you go through this wiki... [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by J0nDaFr3aK on 2014-09-17
> **fantab said:**
> What kind of incompatiblity are we talking about?

I suggest you go through this wiki... [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Hi, thanks for the reply.

I'll definitely take a look at the link you provided, as soon as I have the chance.

As for the incompatibility issues, I referred to [this]("http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/"). There are issues mainly with the backlight sensor and the wifi card.

Plus I created a bootable ubuntu live usb pendrive, but, though I change the boot priority settings in the bios, the pc just ignores the usb stick and starts Windows. but i'll follow the guide you provided and see what happens...

---

### Post by fantab on 2014-09-17
With windows8 you need to disable hibernation or 'Fast startup' as MS likes to call it now. As long as its hibernating it won't boot anything else...

---

### Post by J0nDaFr3aK on 2014-09-18
I see. I'll give it a try. Hope it works. thank you

---

### Post by J0nDaFr3aK on 2014-09-20
Ok, I got the t100 to at least display the linux bootloader from the usb stick (created a bootable usb stick with 64-bit ubuntu 14.04 with rufus and added the bootia32.efi (i could only find one for ubuntu 13.04) file to the efi/boot directory). though, that's all. the screen is blank and ubuntu won't load after i select "try ubuntu without installing".

any ideas?

---

### Post by ubfan1 on 2014-09-20
Have you taken a look at [http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)  ?

---

### Post by J0nDaFr3aK on 2014-09-21
yep, i have... nothing really happens. Same as before, the screen stays blank after i highlight "try ubuntu" and then hit enter (both directly and after modifying some parameters, as suggested in the link you provided)

thanks anyway.

---

