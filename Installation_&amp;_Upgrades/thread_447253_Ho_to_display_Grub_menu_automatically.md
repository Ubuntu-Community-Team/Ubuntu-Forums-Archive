---
title: "Ho to display Grub menu automatically"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-05-17
After reading a lot I finally got my dual boot. Kubuntu on IDE and XP Pro on SATA.
Everything booting up perfect except that grub does not show automatically, I get the option to press ESC to load the grub menu and a countdown.

How do I display grub menu automatically so I can always have the option to boot to different OS ??

BTW - thanks to Bulldog to his dual boot postings......great..!!

.

---

### Post by jglen490 on 2007-05-17
You can edit the GRUB Menu at /boot/grub/menu.lst using vi or kate.

There should be an entry near the top of the file that is someting like:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

Place # in front of the the "hiddenmenu" line and save the file.

---

### Post by geek2330 on 2007-05-17
Cool, thanks for the quick reply....:guitar:

---

