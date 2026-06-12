---
title: "okay GRUB gurus"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by clark3rd on 2005-12-02
Here is my challenge.

One of the things I really like about Ubuntu and its installing process is its ability to scan your local discs for other Linux distributions and put corresponding entries in the GRUB menu. I love that. On my system, I have two 80G hard drives. On hda I have Ubuntu installed, and it is my primary distro. I like to install other distros on hdb to play with (I mean evaluate ;^) and really like how Ubuntu detects these when I reinstall Ubuntu, but I've already said that. Now my question to you is, if I change my distro on hdb how do I get Ubuntu to update my GRUB menu accordingly? I don't want to reinstall Ubuntu again to get it to detect my new distro, but can't figure out how to do it otherwise.

Who has the answer?

Thanks in advance.

---

### Post by bwog on 2005-12-02
You dont have to reinstall ubuntu. You can edit /boot/grub/menu.lst from ubuntu to add OSses. You may have to edit device.map as well to add the new disk. Suppose grub gets broken during install, then you can restore grub with the ubuntu cd in rescue mode: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

---

### Post by john_c on 2005-12-02
You can also use the command "update-grub" to have it update the /root/grub/menu.lst file.  I would always make a backup copy of menu.lst first and read the manual entry for this command before using it.
"man update-grub"

It is run with "sudo update-grub" if you wish to use it.


John_c

---

