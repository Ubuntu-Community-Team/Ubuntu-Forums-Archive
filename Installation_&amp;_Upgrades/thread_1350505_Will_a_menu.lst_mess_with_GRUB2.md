---
title: "Will a menu.lst mess with GRUB2?"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by BoardStupid on 2009-12-09
During the past three updates, I am told that there is no menu.lst on my system (Ubuntu 9.10, clean install) and I'm asked if I would like to create one.

After doing a little research, I am aware that GRUB2 doesn't use the menu.lst anymore so I kept denying the creation of the file. I'm starting to get a little bugged by the repeated failed install of an update so I'm wondering if the next time I'm asked I should just let Update Manager do it's thing.

[[IMG]http://img262.imageshack.us/img262/8413/grub.th.png[/IMG]](http://img262.imageshack.us/i/grub.png/)

I don't want to lock myself out of the pc, so I'll just deny it this time and try any solutions posted at the next update.

---

### Post by Mark_in_Hollywood on 2009-12-09
Read this:

Grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

"No /boot/grub/menu.lst. It has been replaced by /boot/grub/grub.cfg."

it goes on to say that grub.cfg is NOT user editable. 

YOU are warned!

---

### Post by BoardStupid on 2009-12-09
I've read that, which is how I know menu.lst isn't part of GRUB2.

What I'm asking is, since update manager wants to create a menu.lst, will that alter that way GRUB2 works or will it just be ignored during boot

---

### Post by presence1960 on 2009-12-09
> **BoardStupid said:**
> I've read that, which is how I know menu.lst isn't part of GRUB2.

What I'm asking is, since update manager wants to create a menu.lst, will that alter that way GRUB2 works or will it just be ignored during boot

create it so your updates complete. I did the same thing then removed menu.lst.

---

### Post by BoardStupid on 2009-12-09
Thanks. I'm glad I'm not the only one who's come across this.

---

