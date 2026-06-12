---
title: "Ubuntu Minimal Black screen blinking curser after install."
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by aaronmarsh632 on 2016-08-30
Hi,

I'm trying to install Ubuntu Minimal on an old laptop.

I have done about half a dozen installs now but keep getting the same issue. I can get through the entire setup but then once the install is complete, It wont boot there after. I have made sure grub has been installed to the correct drive, and I have removed all other devices. On some occasions it boots Once after the install but then wont boot again.

It only seems to do this with ubuntu minimal, all other operating systems are fine.

Any ideas?

Thanks

EDIT: I forgot to mention, when its on this screen, if you press ctrl+alt & del the ubuntu splash loading screen appears a second before it reboots, so this would indicate ubuntu has tried to boot.

---

### Post by sudodus on 2016-08-30
I have seen what maybe is the same problem, that the text does not appear by itself, but if you enter

***ctrl + alt + F1***

or another of the keys F1 - F6
...

***ctrl + alt + F6***

the text will appear. Will that work for you?

---

### Post by aaronmarsh632 on 2016-08-30
Hi,

Thanks for the reply, I did try f2 with no luck but I found f4 actually works for me.

Is there a way I can stop this and get it to automatically drop to that screen without needing ctrl alt f4?

Thanks

---

### Post by Bucky Ball on 2016-08-30
Did you select a machine profile during the install (i.e. at the tasksel section of the install) or you skipped that, just installed the kernel and are booting to a CLI (login screen, no desktop environment or greeter installed)?

---

### Post by sudodus on 2016-08-30
At least we found a work-around that works for you. I don't know how to solve it. Probably it is caused by a problem with the graphics driver.

- Please specify your graphics chip/card: brand name and model number.

Let us hope someone who knows will read this thread, and tell us how to solve the problem.

---

### Post by grahammechanical on 2016-08-30
> I forgot to mention, when its on this screen, if you press ctrl+alt  & del the ubuntu splash loading screen appears a second before it  reboots, so this would indicate ubuntu has tried to boot.

The splash screen we see when Ubuntu loads is the same screen we see when we shut down Ubuntu. And Crtl+Alt+Del = Reboot.

You have not described how far into the boot process the loading goes. With the Ubuntu mini ISO image if we do not select to install a desktop environment as part of the install all we get is Linux. 

Do you get a Grub boot menu? What happens when you select Ubuntu? Do you get Grub rescue? Do you get a black screen with a flashing white line? Initramfs? Do you get to a Linux command line prompt?

Regards

---

