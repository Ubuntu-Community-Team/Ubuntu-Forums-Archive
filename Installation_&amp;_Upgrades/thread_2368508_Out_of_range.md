---
title: "Out of range"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by aid03 on 2017-08-11
Hello, I've just bought a new PC which came with Ubuntu preinstalled. I've opened it and hit enter on the *Ubuntu line and Ubuntu started loading when all of the sudden, my monitor went black with and the only text displayed on it was "Out of range". I don't know what to do. Please help.

---

### Post by costar on 2017-08-11
probably hdmi cable or exit was burned, try with vga cable or with other hdmi cable.

---

### Post by Bashing-om on 2017-08-11
aid03; Hello - Welcome to the forum.

Brand new ? Never booted before ?
Hard to make a call yet.

What results when you spam the escape key as soon as the firm ware splash screen clears ( 3 second window of opportunity to boot grub) .

We see how far we get and what we need to do .

[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT]

---

### Post by aid03 on 2017-08-11
It opened up grub.




Edit: The first time I opened the pc it went to this menu in which I hit enter on ubuntu

---

### Post by Bashing-om on 2017-08-11
aid03; Well,

The boot loader is there and functioning.
At 'grub' what exactly results when you press enter with a kernel selected to boot ?

[INDENT][INDENT]step through the process
[/INDENT][/INDENT]

---

### Post by aid03 on 2017-08-11
A purple screen with Ubuntu 14.01 and a few lights under it appears after that the screen changes to black and the out of range text appears

---

### Post by QIII on 2017-08-11
Hello!

Could you please give us the manufacturer, model and hardware specifications of the machine?

Cheers!

---

### Post by aid03 on 2017-08-11
This is the pc  [https://altex.ro/sistem-it-myria-style-v31-amd-ryzen-5-1600x-pana-la-4-0ghz-8gb-1tb-nvidia-geforce-gtx-1060-6gb-ubuntu](https://altex.ro/sistem-it-myria-style-v31-amd-ryzen-5-1600x-pana-la-4-0ghz-8gb-1tb-nvidia-geforce-gtx-1060-6gb-ubuntu)

---

### Post by wildmanne39 on 2017-08-11
How to fix out of range problem at boot:

IF IT IS ONLY HAPPENING IN GRUB and you can boot into Ubuntu, which if you wait about a minute and a half or longer I believe it will boot to the desktop, then please do this:
Code:
```
gksudo gedit /etc/default/grub
```
and change this line:

```
#GRUB_GFXMODE=640x480
```

to this:

```
GRUB_GFXMODE=640x480
```

Then save and exit the document.

Then do:
Code:
```
sudo update-grub
```

---

