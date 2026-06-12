---
title: "do-release-upgrade but no nV idia graphics"
date: 2022-04-28
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-04-28
Have unity desktop on DELL Vostro 3500.  but no graphics.  lspci | grep VGA gives 

NVIDIA Corporation GT218M [GeForce 310M]

John

---

### Post by scubascooby on 2022-05-01
I think I may be having a similar problem.

Initially I could only login via console F2 and then startx, I thought it was a grub issue but I have now found it will start normally via VGA.

NVIDIA Corporation G96GL [Quadro FX 380] (rev a1)

---

### Post by SeijiSensei on 2022-05-01
Have you run the Driver Manager?

---

### Post by scubascooby on 2022-05-01
I don't know what that is. I've never had to run it before.

Where do I find it ?

---

### Post by scubascooby on 2022-05-01
I have just tried:

apt search nvidia-driver 

but it doesn't list anything for my 380 or cigtoxdc's 310

---

### Post by cigtoxdoc on 2022-05-02
After Iog in, 4 lines of type appear momentarily in top left hand corner of the screen saying that nouveau couldn't load firmware and three othe lines of what appear to be errors.  How do I get to see what they are?

Thank you,

John

---

### Post by scubascooby on 2022-05-03
The error I saw on the F2 console was:

nouveau 0000: 01: 00: init failed, -2
nouveau 0000: 01: 00.0: bsp: init failed, -2

---

### Post by cigtoxdoc on 2022-05-03
Thank you.  When do I press F2 to get the nouveau and nvidia errors?

---

### Post by scubascooby on 2022-05-03
When mine gets to the black screen I use Ctr-lAlt-F2 or Ctrl-Alt-F3 to open a console. 

I then login and can use startx to open the normal gui desktop.

---

