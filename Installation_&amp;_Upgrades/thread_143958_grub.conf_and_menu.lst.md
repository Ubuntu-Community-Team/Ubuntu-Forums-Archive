---
title: "grub.conf and menu.lst"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2006-03-13
Hi Folks,


I have a few question on these two files...


(1) Does anyone know if both of these files get read when booting with GRUB?

(2) Does GRUB just read one of the files if both are present, and is one the default choice over the other when both are available?


Thanks in advance,
DAVE

---

### Post by Xian on 2006-03-13
It depends on the distro. AFAIK, Fedora uses grub.conf over menu.lst and Gentoo symlinks menu.lst to grub.conf. I thought that Ubuntu didn't use grub.conf at all, which makes me wonder how you found this on your system ??

---

### Post by DaBruGo on 2006-03-14
[QUOTE=Xian]It depends on the distro. AFAIK, Fedora uses grub.conf over menu.lst and Gentoo symlinks menu.lst to grub.conf. I thought that Ubuntu didn't use grub.conf at all, which makes me wonder how you found this on your system ??[/QUOTE]

Xian,

Thanks for your reply. I didn't actually know if both files were included in Ubuntu or not. I was just wondering (if they both were included in Ubuntu) just how the bootup process worked with these two files and if one took priority over the other or if they were inter-related somehow.

But your  answer helped me understand a little better, because some of the resource material I was reading about GRUB was geared toward redhat and it mentioned grub.conf almost always. I haven't read that much on Gentoo yet, but your symlink info shed some insight to how they setup GRUB as well.

What got me to post the question was [another thread]("http://ubuntuforums.org/showthread.php?t=143952") I started in relation to using the LABEL option on the kernel line in the menu.lst file for GRUB.  I was thinking about using the LABEL option so that I could bootup an external drive on whatever PC I wanted to connect it to, without all the (hdx) config headaches in menu.lst.



I really appreciated you taking the time to reply,
DAVE

---

