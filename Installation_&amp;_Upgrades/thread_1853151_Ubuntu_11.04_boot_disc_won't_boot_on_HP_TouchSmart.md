---
title: "Ubuntu 11.04 boot disc won't boot on HP TouchSmart 610"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by drone13 on 2011-10-01
<strike>I'm trying to install Ubuntu on my new TouchSmart 610. I burned a ubuntu boot disc and put it in the cd rom drive and restarted. I made sure the boot order had the disc first priority but, it just started Windows. Anyone know what's going on?</strike>

EDIT: Solved that problem, boot disc was messed up. I installed Ubuntu and it sorta works. Now the problem is lack of wireless card drivers so I can't install any updates, anyone know how I can find out which driver I need?

---

### Post by LinuxFan999 on 2011-10-01
Do you have any other computers to test the CD on?

---

### Post by drone13 on 2011-10-01
Yeah I just tested the disc on another computer, didn't work either. OH! I just realized I burned it on a 4.7GB DVD. Maybe that has something to do with it...

---

### Post by LinuxFan999 on 2011-10-02
> **drone13 said:**
> Yeah I just tested the disc on another computer, didn't work either. OH! I just realized I burned it on a 4.7GB DVD. Maybe that has something to do with it...
Try burning it to a CD, then try again.

---

### Post by SuporteTecnicoID on 2012-01-04
> **LinuxFan999 said:**
> Try burning it to a CD, then try again.

Este é um erro relacionado aos drivers da placa de video Intel....Éca....!

Ao aparecer o grub precione o **TAB** na linha do boot e adicione o **parametro de boot** no final desta linha: 

resultando em :

**nomodeset** e para ficar menos pior acrescente tambem o parametro **vga=791**

**quiet splash nomodeset vga=791 --**

No **Linux KDu** , eu resolvi assim, por enquanto...!

---

