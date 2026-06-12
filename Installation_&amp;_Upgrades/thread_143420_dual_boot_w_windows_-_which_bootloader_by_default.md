---
title: "dual boot w/ windows - which bootloader by default?"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by sfl on 2006-03-12
I read these instructions on windows dualboot with ubuntu:
[https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29)

Does ubuntu install it's own bootloader to boot either of the OS or does it simply add an entry to the list of OS that the windows bootloader can load? If a bootloader is installed can someone point me in the right direction for information on removing the bootloader (if I choose to go back to a single OS system)?

Thanks much,

Sacha

---

### Post by Klaidas on 2006-03-12
It's GRUB. ([https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29](https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29))
For removing it, insert you Windows XP (if that's you other OS) CD, go to recovery console and do
```
fixmbr
``` if I remember correctly :)

---

### Post by sfl on 2006-03-12
Thanks much for the quick reply klaidas. Very much appreciated. Off I got to try out Ubuntu... : )

---

### Post by Klaidas on 2006-03-12
Good luck! :)

---

### Post by uscfan on 2006-03-12
Been a while since I have used linux. I know you all are gonna wonder why the hell I am still using windows but here goes...

I know that using fixmbr will format the mbr and make windows the default os again, but I remember with early 2.6kernel distros installing a 2.6 based distro would corrupt the windows partitions. Is this still true?

---

