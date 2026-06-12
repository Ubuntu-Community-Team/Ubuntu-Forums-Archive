---
title: "change console keyboard layout"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by cccc on 2011-05-15
hi

If I switch using CTRL-ALT-F1 to the console, then I have other keyboard layout than under Gnome Desktop.
Howto change console keyboard layout?

---

### Post by lechien73 on 2011-05-15
Try switching to the console, and then installing the console-common package, if it's not already installed:

```
sudo apt-get install console-common
```

It will prompt you to change your keyboard layout. To make changes after that, you can type:

```
sudo dpkg-reconfigure console-data
```

---

### Post by cccc on 2011-05-15
Thy a lot, now it works well!

---

### Post by lechien73 on 2011-05-15
Great stuff :) please could you use the **Thread Tools** menu and mark it as [SOLVED]?

Thanks

---

### Post by rocktale on 2011-06-20
Is there a way to make the changes permanent? I use the server edition and after a reboot I am back with the default keymap.

---

### Post by cccc on 2011-06-25
> **rocktale said:**
> Is there a way to make the changes permanent? I use the server edition and after a reboot I am back with the default keymap.

Try to change in /etc/default/keyboard and change as well at the Gnome Login Mask, if you mark an user name, go down and change the keyboard, before login into the Gnome desktop.

---

### Post by pma083 on 2012-04-04
> **lechien73 said:**
> Try switching to the console, and then installing the console-common package, if it's not already installed:

```
sudo apt-get install console-common
```

It will prompt you to change your keyboard layout. To make changes after that, you can type:

```
sudo dpkg-reconfigure console-data
```

Simply Awesome! :)
Thanks.

---

