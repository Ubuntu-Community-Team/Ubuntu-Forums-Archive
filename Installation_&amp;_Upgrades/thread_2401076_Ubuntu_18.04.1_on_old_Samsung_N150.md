---
title: "Ubuntu 18.04.1 on old Samsung N150"
date: 2018-09-13
forum: Installation &amp; Upgrades
---

### Post by paulfris on 2018-09-13
Hi there,

Since my old Samsung N150 is very very slow on Windows 10 and I want to use it for my Arduino IDE I installed a dual boot (via USB) of Ubuntu 18.04.1
So far so good (yes I know the machine is below the requirements of his install but hey if Windows 10 runs on this old thing I thought Ubuntu wil :-)).

The problem is, that booting Ubuntu in normal mode will show the boot logo (UBUNTU with running dots below) for a few seconds and then the screen freezes.
So I think I will have a Graphics Driver issue ???

When I use the GRUB option of starting in advanced mode Ubuntu starts and I could even install my Arduino IDE but the screen is low res.

Is there a way to tackle this problem and to update or roll back some things?
Truoble shoot ideas?

Or...??

Anybody?

---

### Post by ajgreeny on 2018-09-13
Judging by what I can find about that hardware I suggest you forget about using Ubuntu 18.04 and try Lubuntu 18.04 instead.

It should run a lot better than you describe; I have it running, not fast but usable, on a similarly specified machine.
You can use all the same software and the same repos as Ubuntu but simply has a much lower resource hungry GUI.

---

### Post by paulfris on 2018-09-13
Hey, thanks for the advise.
Any advise how I swap the install of Ubuntu to Lubuntu on the dual boot install I have now?
I need a new GRUB I suppose?

---

### Post by ajgreeny on 2018-09-13
Is there anything on the machine that you need to keep or can you just reinstall, which may be a great deal simpler?

You could install the lubuntu-desktop package and choose Lubuntu at the login screen but that will leave you with a lot of duplicate application types, eg two text editors, two file managers, etc etc.
How annoying that may be is something only you will know.

---

### Post by paulfris on 2018-09-14
OK, I managed by doing: 1) startup in Windows10; 2) deleted the Ubuntu partition; 3)Boot from Lubuntu USB bootable 4)make dual install option Win/LUbuntu.
Worked and works a lot better than Ubuntu on the machine but....
Lubuntu does not have the Arduino IDE in his Software Library.
I downloaded Arduino IDE from the Arduino site (Linux 64 version) and installed it in the Lubuntu terminal (SUDO).
Worked and installed but....
Arduino IDE does not 'see' the serial (USB) ports so no com.
Solved it by making myself (userid) part of the group aout and set permissions (chmod) so Arduino got access to serial ports.
Worked but....I needed a beer!
Done.

Thank you very much for your help on Lubuntu.

---

### Post by ajgreeny on 2018-09-14
Very well done!

I have no beer but here's some popcorn!

:popcorn:

---

### Post by paulfris on 2018-09-14
:P:P:lolflag:

---

