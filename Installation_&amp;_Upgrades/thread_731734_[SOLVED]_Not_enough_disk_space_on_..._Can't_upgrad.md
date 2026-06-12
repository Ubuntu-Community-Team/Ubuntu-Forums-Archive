---
title: "[SOLVED] Not enough disk space on /... Can't upgrade to 8.04 Beta"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by LinuX-M@n1@k on 2008-03-22
After the `sudo apt-get clean` command and emptying my trash, I dont have enough space yet:
```
root@ubuntu:/# df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             4.6G  3.9G  531M  89% /
root@ubuntu:/# 
```
What can I remove ? Thanks.

---

### Post by fela on 2008-03-22
you can remove any data that you don't need that's in your home directory, and any apps that you installed but now don't need anymore. I don't know how you can live with a 4.9GB hdd! (or is it wubi virtual partition?) :guitar:

---

### Post by schiznik on 2008-03-22
I expect there are a load of temporary files you can remove. du (from the command line) may be useful, although there are some gui programs you can use (xdu and gtkdiskfree spring to mind) to see where your space is used.

5G is a bit on the small side these days.. I have more that that on a usb key :-P (which also happens to run ubuntu :))

---

### Post by LinuX-M@n1@k on 2008-03-22
My hdd is 80GB ( / - 5GB ; /home - 35GB ; /media/sda1 - 40GB )
I'm going to remove gnome ( since I use fluxbox I don't need gnome )

Edit: > I'm going to remove gnome ( since I use fluxbox I don't need gnome )
This was a BAD move !!!
```
sudo apt-get remove gnome-*
```
This removed ubutnu-desktop too and now the update-manager ( which also was removed xD (I installed it again) ) couldn't recognize my Ubuntu and now (AGAIN) I'm installing ubuntu-desktop which also needs 400MB packages ( including some gnome-* ) and now I'm wondering:
"What the @#$% am I trying to do with my ubuntu ?!?! xDD Why do I want to upgrade to the newest gnome and other stuff, since I'm not going to use them.."
Well, when I think about it, I want to upgrade to the newest kernel and I believe that there's an easier way.
EDIT: I'm so stupid... this thread is useless... I'm with kernel 2.6.22-14-generic. Isn't it the newest ?

---

### Post by zvacet on 2008-03-22
You can do several things

1. remove files which you don´t need anymore

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

2.download [Geparted live Cd](http://gparted.sourceforge.net/) and with it shrink your home partition and add free space to the root(let root be ~10GB)

Yes,you have latest kernel.

---

