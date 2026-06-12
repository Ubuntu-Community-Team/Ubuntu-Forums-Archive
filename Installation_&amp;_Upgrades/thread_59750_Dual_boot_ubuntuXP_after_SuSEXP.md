---
title: "Dual boot ubuntu/XP after SuSE/XP"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by KurtB on 2005-08-25
Hi,

I need some help to install a dual boot (Win XP & Ubuntu) on my laptop (Dell inspiron 5150).

Current situation:
I tried a dual boot with SuSE9.3 & WinXP -> SuSE boots really slow & I don't get any KDE or Gnome after I login (root as normal user). I reinstalled it twice & tried system restore twice -> problem remains

So I still have an ubuntu disk,...

Desired situation:
Dual boot with XP & ubuntu, without messing up my windows partition again. So I really need help with choosing the right partition when installing ubuntu (don't know howto) & being sure that after installing I still can boot both OS's

As I tried with SuSE first I think my disk partitions are OK:
19 GB -> NTFS Win XP C:/ -> really need to keep this one
30 GB -> NTFS Data d:/ -> still empty, don't want that partioner from ubuntu messes this one up either
1 GB -> SWAP, done by SuSE
10 GB -> ReiserFS, done by SuSE -> want to install ubuntu here...

My question(s):
- some help with choosing the last partition for my ubuntu-install aswell as ubuntu 'automatically' uses the existing SWAP partition (and doesn't create another one...)
- installing / configuring GRUB so that I can nicely boot win & ubuntu without worries/risks (on laptop, no floppy...)
- I also have a Belkin 54G WIFINIC -> does anyone has experience with this on ubuntu?

thx

---

### Post by matej on 2005-08-25
[QUOTE=KurtB]Hi,
- installing / configuring GRUB so that I can nicely boot win & ubuntu without worries/risks (on laptop, no floppy...)
[/QUOTE]
IMHO this is done automatically during installation

---

