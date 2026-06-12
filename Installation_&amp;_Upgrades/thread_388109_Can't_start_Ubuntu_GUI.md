---
title: "Can't start Ubuntu GUI"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by bt86bt on 2007-03-19
Hi.

Have just installed Ubuntu with the alternative cd (low memory install) and then booted it with the "ultimate boot cd" and manually booted it with grub like this:

root hd(0,0)
kernel /vmlinuz root=/dev/hda1
initrd /boot/initrd.img-2.6.17-10-generic
voot

After that I see alot of text flashing by, no errors what I can see. Then it does not start the gui gnome but just leave me in a terminal. Now I wonder how I start gnome couse there are some stuff I need to do in the gui before I can get internet to work on it.

It looks like this: [http://img233.imageshack.us/img233/1866/dsc00252ch1.jpg](http://img233.imageshack.us/img233/1866/dsc00252ch1.jpg)

Also when I write something with sudo I get "Can't mkdir /var/run/sudo: Read-only file system".

Please help me.

---

### Post by Kateikyoushi on 2007-03-19
Seems to me like a broken install. Could you show the content of / ?
> ls /

---

### Post by nsleiman on 2007-03-19
> **bt86bt said:**
> Hi.

Have just installed Ubuntu with the alternative cd (low memory install) and then booted it with the "ultimate boot cd" and manually booted it with grub like this:

root hd(0,0)
kernel /vmlinuz root=/dev/hda1
initrd /boot/initrd.img-2.6.17-10-generic
voot

After that I see alot of text flashing by, no errors what I can see. Then it does not start the gui gnome but just leave me in a terminal. Now I wonder how I start gnome couse there are some stuff I need to do in the gui before I can get internet to work on it.

It looks like this: [http://www.btcreations.net/images/DSC00252.JPG](http://www.btcreations.net/images/DSC00252.JPG)

Also when I write something with sudo I get "Can't mkdir /var/run/sudo: Read-only file system".

Please help me.

is it voot or root ?

i can remeber having such a problem, it was related to the "ro" (read only) patern i removed it and it worked after.

---

### Post by bt86bt on 2007-03-19
> **Kateikyoushi said:**
> Seems to me like a broken install. Could you show the content of / ?

Here you go: [http://img477.imageshack.us/img477/8303/dsc00253xt4.jpg](http://img477.imageshack.us/img477/8303/dsc00253xt4.jpg)
And you might be right, it froze on "unmounting file system" at the end of the instalation but ther might be some final step that I missed because of that...

> **nsleiman said:**
> is it voot or root ?

i can remeber having such a problem, it was related to the "ro" (read only) patern i removed it and it worked after.
I meant "boot".

Hmm how do I remove the "ro" patern?

---

### Post by 50words on 2007-05-03
I'm having a similar problem, and I'm stuck on read only, so I can't do anything. Little help?

---

