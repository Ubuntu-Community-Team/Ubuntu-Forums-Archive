---
title: "Computer freezes after install and reboot"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by james71 on 2014-01-18
I just finished installing Ubuntu and when it asks me to restart the computer I do so, and then my display shows Invalid format and so I hit enter on my keyboard a few times and that brought up a Ubuntu screen and shows my login name and then the system freezes. I have a picture of where it gets to and then freezes

[IMG]http://i.imgur.com/3TWvGW5.jpg[/IMG]

---

### Post by mörgæs on 2014-01-18
Hi, welcome to the fora.
Which screen card do you use?

---

### Post by james71 on 2014-01-18
what video card do i use? i'm not sure it's an integrated nvidia card

---

### Post by mörgæs on 2014-01-19
Nvidia cards often need the **nomodeset** boot option. Have you tried that?

---

### Post by VMC on 2014-01-19
Open a terminal (Ctrl+Alt+T), then type this ```
lspci -v|grep VGA
```

example:
```
 $ lspci -v|grep VGA
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [**GeForce 6150SE nForce 430**] (rev a2) (prog-if 00 [VGA controller])
```

---

