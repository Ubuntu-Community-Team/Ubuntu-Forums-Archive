---
title: "please help me (again) !"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by esculayd4724 on 2008-02-06
hello,
i just got help about an hour or two ago from somebody on here who fixed my installation cd problem.
so i installed ubuntu, and the computer restarted afer i was told to take it out of the disk drive.
everytime i turn my laptop on, and after the ubuntu bar loads, the screen just turns black, and nothing seems to happen. please help me because i need this working by tomorrow!

thank you.

---

### Post by taurus on 2008-02-06
Sounds like you need to reconfigure your X server again.  Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by esculayd4724 on 2008-02-06
how would i do that?
is tehre  a selection for the recovery mode?
and do i have to press f6 and then type in that code or will a black screen pop up where i have to type something?

---

### Post by taurus on 2008-02-06
When you turn on your machine, you will get a logo of your mobo.  Then, you would see GRUB at which point you have three seconds to press Esc to bring up the menu.  The first entry is highlight which is your Ubuntu.  The second entry is the recovery mode while the third entry is to test your RAM.  Use the down arrow to highlight the second entry and hit Return to boot from it.

---

