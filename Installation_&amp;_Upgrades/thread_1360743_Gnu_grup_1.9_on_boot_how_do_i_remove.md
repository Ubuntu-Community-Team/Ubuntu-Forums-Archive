---
title: "Gnu grup 1.9 on boot how do i remove"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Cabbage1 on 2009-12-21
i have recently just installed ubuntu. After a lot of trouble i finally got my wireless working.
I used the update manager and just updated everything. Then it said i had to reboot so i did. The next time i booted it came up with gnu grup 1.97 beta..... and i cant choose to boot to ubuntu.

I want to remove this "gnu grup" and just be able to boot in ubuntu.

Any help appreciated thanks :)

---

### Post by darkod on 2009-12-21
GNU Grub is the grub bootloader that loads ubuntu. If you get rid of it you have no way to boot ubuntu. Obviously something went wrong during the updates.
You can try reinstalling grub2 (the official version number is 1.97, what you have). Boot with the 9.10 ubuntu cd, Try Ubuntu option. Follow the instructions here for grub for 9.10:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Cabbage1 on 2009-12-21
> **darkod said:**
> GNU Grub is the grub bootloader that loads ubuntu. If you get rid of it you have no way to boot ubuntu. Obviously something went wrong during the updates.
You can try reinstalling grub2 (the official version number is 1.97, what you have). Boot with the 9.10 ubuntu cd, Try Ubuntu option. Follow the instructions here for grub for 9.10:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

yeh i dont have the ubuntu cd though, is there any other way?

i found this [http://ubuntuforums.org/showthread.php?t=1321107](http://ubuntuforums.org/showthread.php?t=1321107) but dont really understand what to do :confused:

---

### Post by darkod on 2009-12-21
> **Cabbage1 said:**
> yeh i dont have the ubuntu cd though, is there any other way?

i found this [http://ubuntuforums.org/showthread.php?t=1321107](http://ubuntuforums.org/showthread.php?t=1321107) but dont really understand what to do :confused:

That is if you have wubi installed, not ubuntu. Wubi is installed inside windows and you first get the windows bootloader. It's sort of virtual ubuntu.
If you have full ubuntu then I don't know any other way except with the cd. You can download an image for free anytime.

---

### Post by Cabbage1 on 2009-12-21
> **darkod said:**
> That is if you have wubi installed, not ubuntu. Wubi is installed inside windows and you first get the windows bootloader. It's sort of virtual ubuntu.
If you have full ubuntu then I don't know any other way except with the cd. You can download an image for free anytime.

ive tried to boot from cd before but it never recognizes the cd

Edit: actually I just realised i didnt burn the cd correctly, ill try tommorow and see if I can find a disk to burn. Thanks for your help I really appreciate it.

---

