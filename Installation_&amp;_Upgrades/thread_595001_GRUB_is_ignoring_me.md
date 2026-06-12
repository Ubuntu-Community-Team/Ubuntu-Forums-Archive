---
title: "GRUB is ignoring me"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by themess on 2007-10-28
I'm dual booting XP Pro and Gutsy Gibbon. I'm a noob and I'm feeling my way around. I changed the boot menu to put XP at the top and then I changed the timeout to 0 so my girlfriend wouldn't get confused. Only now the menu times out so fast that I can't get into Ubuntu. So how do i fix this? I can't change grub because I can get into Ubuntu. Grrrrr, please help me. I'm missing it already.

---

### Post by taurus on 2007-10-28
Install this little app for XP so you can access Ubuntu partitions, ext3, [http://www.fs-driver.org/](http://www.fs-driver.org/).  Then, edit /boot/grub/menu.lst and change the timeout to 5 seconds.  Just tell her not to do a thing after she turns on the computer and it will boot into XP for her.

---

### Post by aidanr on 2007-10-28
Couple of ways to change it, first would be to boot the live cd and change it from there (the ubuntu partition should just be on the live cd desktop) or alternatively install [fs-driver]("http://www.fs-driver.org/") on windows and change it from there, I find 3 seconds to be best.

---

### Post by Pumalite on 2007-10-28
Boot from Live CD, mount your partitions and edit your menu.lst.
If you don't know how to mount partitions, use Knoppix (mounts all your drives/partitions on boot)

---

### Post by themess on 2007-10-28
Right on! Thanks for the quick responses guys.

---

