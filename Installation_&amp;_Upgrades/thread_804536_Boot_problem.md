---
title: "Boot problem"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by xtrait on 2008-05-23
I've an existing XP Home edition installation on my PC. Installation went fairly well until the first boot. I see the following error.

" find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu/lst "

" Error 15: file not found "

I suspect it is about floppy disk. Do I have to have a floppy boot disk for ubuntu? Or do I have to have floppy drive for the installation. Anyway, my BIOS setting for floppy drive is set to "disable".

PLS help! I really really wanna forget Microsoft and its "great" products.

---

### Post by nix2ways on 2008-05-23
Did you install Ubuntu using the default options?
Have you copied the message you quote accurately? 
" find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu/lst " 
If so, the last part should be /menu.lst not /menu/lst.
Boot using the Ubuntu live CD and copy paste your /boot/grub/menu.lst file here.
Error 15 would indicate Grub can't find your kernel image - don't worry about what that means right now. Once we can see the output from your menu.lst we should have a clearer idea what's happening. 
Don't worry too much I'm sure it's 'fixable'.

Did you install using 'wubi'? I've no experience of installing using this method. Maybe someone else has. However, there's a similar thread on Linux Questions 
[http://www.linuxquestions.org/questions/linux-newbie-8/just-installed-linux...-having-problems.-643865/](http://www.linuxquestions.org/questions/linux-newbie-8/just-installed-linux...-having-problems.-643865/)

and my advice agrees 100% with the reply from pixellany (If you you want to install, then take the time to make space on you drive, and do a "clean, native install"--ie not inside Windows or in a virtual machine. This is--IMHO--the only way to really see Linux at its best.)

My advice is install using the 'traditional' method via the live CD. If you want to do that and need to know how to do it, it's very easy, get back and I'll help you get a working dual boot in a very short time.

---

### Post by dstew on 2008-05-23
I agree that installing the regular way is better than installing inside Windows. The Hardy CD gives you the option of installing inside Windows if you *open* it in Windows rather than *boot* it, and I think a lot of new users get confused at this point. If you install inside Windows, it is (I think) the same as [Wubi]("http://wubi-installer.org/"). Maybe some Wubi guru can help, or visit the [Wubi forum]("http://ubuntuforums.org/forumdisplay.php?f=234").

---

### Post by wpshooter on 2008-05-23
> **xtrait said:**
> I've an existing XP Home edition installation on my PC. Installation went fairly well until the first boot. I see the following error.

" find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu/lst "

" Error 15: file not found "

I suspect it is about floppy disk. Do I have to have a floppy boot disk for ubuntu? Or do I have to have floppy drive for the installation. Anyway, my BIOS setting for floppy drive is set to "disable".

PLS help! I really really wanna forget Microsoft and its "great" products.

DOES your machine have a floppy drive ?  Is so, then change the parameter in the BIOS from disable to enable !!!

---

