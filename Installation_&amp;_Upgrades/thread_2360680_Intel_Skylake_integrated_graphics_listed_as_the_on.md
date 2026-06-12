---
title: "Intel Skylake integrated graphics listed as the only VGA compatible card"
date: 2017-05-07
forum: Installation &amp; Upgrades
---

### Post by icmv333 on 2017-05-07
[SIZE=3][FONT=arial]Hello. I've recently installed ubuntu 16.04 along with my pre-installed Windows 10 OS. I've applied some driver updates on my Nvidia 940MX graphics card found in additional drivers in system options. Now when I use this command: 

[/FONT][/SIZE]
[SIZE=3]lspci | grep VGA[/SIZE]


[SIZE=3][FONT=arial]I get my intel skylake integrated graphics card as the result. What could be the problem here? Is this something I should worried about or is this a harmless bug?[/FONT][/SIZE]

---

### Post by mörgæs on 2017-05-07
Hi, welcome to the fora.

If you are satisfied with the speed of Intel graphics then you can just carry on. 

If you want to use the Nvidia option as well you could look at [another thread]("https://ubuntuforums.org/showthread.php?t=2360275") about the 940 not working well in 16.04. 17.04 is worth testing, and if that does not help then maybe another distro as suggested.

---

### Post by icmv333 on 2017-05-07
Actually the weird thing is, I've selected my Nvidia graphics card and it's running correctly according to system information but upon using the command in th terminal, ubuntu just shows Intel as the only VGA card compatible. Sorry for not mentioning this information.

---

### Post by mc4man on 2017-05-07
If this is a laptop then I wouldn't find unusual as Intel handles the display, Nvidia, if used, just the rendering. 
Maybe here can explain
[https://askubuntu.com/questions/733183/difference-between-vga-compatible-controller-and-3d-controller](https://askubuntu.com/questions/733183/difference-between-vga-compatible-controller-and-3d-controller)

---

### Post by icmv333 on 2017-05-07
mc4man thanks. That answers my question.

---

### Post by efflandt on 2017-05-07
Your Nvidia card is not listed under VGA when you have hybrid (duel laptop) graphics, see if you see it doing: **lspci | grep 3D**
Otherwise just look through the output of lspci.

---

