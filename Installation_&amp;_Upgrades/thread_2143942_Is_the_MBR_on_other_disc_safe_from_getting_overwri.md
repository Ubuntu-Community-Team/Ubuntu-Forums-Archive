---
title: "Is the MBR on other disc safe from getting overwritten?"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by Spinybuntu on 2013-05-10
Hi 

I'm not exactly new but not found an answer searching for this anywhere:

**System**
[LIST]
[*]Multiple physical hard drives
[*]Windows installed on one
[*]Ubuntu installed on another
[*]Switch OS by reboot and selecting drive in BIOS
[/LIST]

My question is that if I run the Ubuntu setup and do a fresh install to a non windows drive, is it possible that the grub installation will mess with the boot record on the Windows drive?

I've always guarded against this in the past by unplugging everything apart from the drive I'm installing Ubuntu onto, but I don't know if I'm being too paranoid?

Does anyone know?

Many thanks.

Spiny

---

### Post by prodigy_ on 2013-05-10
> **Spinybuntu said:**
> I've always guarded against this in the past by unplugging everything apart from the drive I'm installing Ubuntu onto
And that's the wisest thing to do especially if you don't have a backup. You can always select default boot device in BIOS and Windows can be added to Grub menu with ```
sudo update-grub
```
Why take any risks if you don't have to?

---

### Post by Spinybuntu on 2013-05-10
Great, thanks I'll keep playing it safe :)

---

### Post by Bashing-om on 2013-05-10
prodigy_; Hi ! Welcome to the forum.

Unplugging all other drives will preclude any adverse affects but if one pays close attention to the install process (implies familiarity), it is not necessary to unplug the drives. Distractions can always be a cause of havoc !

The last install I did was of version 12.04 and the last screen gave a synopsis of what the installer was going to do. At this time there was an option to select where grub was to be installed --- if one did not want the installers' default install position. 

Nothing is touched on that disk to that time, until you accept the installers' synopsis. One can always "go back" and change a preference; however, Once accepted, it is all over with except the crying ! 

Pay attention and check and check again and double check what you have directed the installer to perform and what the installer is going to do.
[INDENT=2]
That's my story

[/INDENT]

---

### Post by grahammechanical on 2013-05-10
Nothing is ever safe when the user switches on and starts tapping away at the keyboard. Keep a note of the drives you have and what each is for and their Linux designations, such as sda; sdb; etc. The installer will give you an option to select where to install Grub. Just make sure it is going on your designated Ubuntu hard drive and not your Windows drive.

This is a bit old but notice the image called 7-C

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

Do you see the panel called Device for bootloader installation? Make sure that is pointing to the sd that is the Ubuntu drive.

Regards.

---

### Post by oldfred on 2013-05-10
You only get the option on which drive to install grub2's boot loader if you choose the Something Else or manual install. And you have to use combo box to choose another drive. Otherwise it defaults to sda. I have clicked thru too fast and installed to sda.

And all the auto install options default to sda. 

Or still safest to disconnect drive if not sure or not sure how to repair when you install to wrong place.

---

### Post by darkod on 2013-05-10
We all have our preferences and our way of thinking. Personally I don't support installing an OS with hardware unplugged since you need to see if it will be giving you issues with anything. In some (rare) cases you can be surprised after you plug hardware back and wonder what happened.

I have found ubuntu very precise to specify a destination for installation, using the manual install of course. Including for the bootloader. Compare that with windows which never asks you where to install a bootloader, but still many people think reinstalling ubuntu is more dangerous...

If it makes you happy, keep disconnecting disks. It's your choice.

---

### Post by Spinybuntu on 2013-05-12
> **grahammechanical said:**
> 

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

Do you see the panel called Device for bootloader installation? 

Regards.


Ah yes, I did in the end, as I'd done an advanced install & put /home on a separate partition. By which time I was obviously already in the install with my other drives unplugged.

Good one to remember for next time.

Thanks all.

---

